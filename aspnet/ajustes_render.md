<h1>Ajustes no Projeto Blog Pessoal - Render</h1>



<h2>👣 Passo 01- Atualizar a Classe Program</h2>



Vamos atualizar Classe **Program**, para habilitar a compatibilidade com o tipo de dado **DateTimeOffset** no Banco de dados **PostgreSQL**:

1. Abra a Classe **Program**, localizada na pasta raís do projeto.
2. Localize a linha abaixo:

<div align="center"><img src="https://i.imgur.com/KLrhx6q.png" title="source: imgur.com" /></div>

3. Logo abaixo desta linha, insira a linha abaixo:

```c#
 AppContext.SetSwitch("Npgsql.EnableLegacyTimestampBehavior", true);
```

Esta linha habilita a compatibilidade com o tipo de dado **DateTimeOffset** no Banco de dados **PostgreSQL**.

4. O código completo da Classe Program, você confere abaixo:

```c#

using blogpessoal.Configuration;
using blogpessoal.Data;
using blogpessoal.Model;
using blogpessoal.Security;
using blogpessoal.Security.Implements;
using blogpessoal.Service;
using blogpessoal.Service.Implements;
using blogpessoal.Validator;
using FluentValidation;
using MicroElements.Swashbuckle.FluentValidation.AspNetCore;
using Microsoft.AspNetCore.Authentication.JwtBearer;
using Microsoft.EntityFrameworkCore;
using Microsoft.IdentityModel.Tokens;
using Microsoft.OpenApi.Models;
using System.Text;

namespace blogpessoal
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var builder = WebApplication.CreateBuilder(args);

            // Add services to the container.

            builder.Services.AddControllers()
                .AddNewtonsoftJson(options =>
                {
                    options.SerializerSettings.ReferenceLoopHandling = Newtonsoft.Json.ReferenceLoopHandling.Ignore;
                    options.SerializerSettings.NullValueHandling = Newtonsoft.Json.NullValueHandling.Ignore;
                });

            // Conexão com o Banco de dados
            if (builder.Configuration["Environment:Start"] == "PROD")
            {
                // Conexão com o PostgresSQL - Nuvem

                builder.Configuration
                    .SetBasePath(Directory.GetCurrentDirectory())
                    .AddJsonFile("secrets.json");
                
                var connectionString = builder.Configuration
               .GetConnectionString("ProdConnection");

                builder.Services.AddDbContext<AppDbContext>(options =>
                    options.UseNpgsql(connectionString)
                );
            }
            else 
            {
                // Conexão com o SQL Server - Localhost
                var connectionString = builder.Configuration
                .GetConnectionString("DefaultConnection");

                builder.Services.AddDbContext<AppDbContext>(options =>
                    options.UseSqlServer(connectionString)
                );
            }
            

            // Registrar a Validação das Entidades
            builder.Services.AddTransient<IValidator<Postagem>, PostagemValidator>();
            builder.Services.AddTransient<IValidator<Tema>, TemaValidator>();
            builder.Services.AddTransient<IValidator<User>, UserValidator>();

            // Registrar as Classes de Serviço (Service)
            builder.Services.AddScoped<IPostagemService, PostagemService>();
            builder.Services.AddScoped<ITemaService, TemaService>();
            builder.Services.AddScoped<IUserService, UserService>();
            builder.Services.AddScoped<IAuthService, AuthService>();

            // Validação do Token
            builder.Services.AddAuthentication(options =>
            {
                options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
                options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;
            }).AddJwtBearer(options =>
            {
                var key = Encoding.UTF8.GetBytes(Settings.Secret);
                options.SaveToken = true;
                options.TokenValidationParameters = new TokenValidationParameters
                {
                    ValidateIssuer = false,
                    ValidateAudience = false,
                    ValidateLifetime = true,
                    ValidateIssuerSigningKey = true,
                    IssuerSigningKey = new SymmetricSecurityKey(key)
                };
            });

            // Learn more about configuring Swagger/OpenAPI at https://aka.ms/aspnetcore/swashbuckle
            builder.Services.AddEndpointsApiExplorer();

            // Configuração do Swagger
            builder.Services.AddSwaggerGen(options =>
            {
                // Informações do Projeto e da Pessoa Desenvolvedora
                options.SwaggerDoc("v1", new OpenApiInfo
                {
                    Version = "v1",
                    Title = "Projeto Blog Pessoal",
                    Description = "Projeto Blog Pessoal - ASP.NET Core 7.0",
                    Contact = new OpenApiContact
                    {
                        Name = "Rafael Queiróz",
                        Email = "rafaelproinfo@gmail.com",
                        Url = new Uri("https://github.com/rafaelq80")
                    },
                    License = new OpenApiLicense
                    {
                        Name = "Github",
                        Url = new Uri("https://github.com/rafaelq80")
                    }
                });

                // Configuração de Segurança no Swagger
                options.AddSecurityDefinition("JWT", new OpenApiSecurityScheme
                {
                    In = ParameterLocation.Header,
                    Description = "Digite um Token JWT válido",
                    Name = "Authorization",
                    Type = SecuritySchemeType.Http,
                    BearerFormat = "JWT",
                    Scheme = "Bearer"

                });

                // Adicionar a indicação de endpoint protegido no Swagger
                options.OperationFilter<AuthResponsesOperationFilter>();

            });

            // Adicionar o Fluent Validation no Swagger
            builder.Services.AddFluentValidationRulesToSwagger();

            // Configuração do CORS
            builder.Services.AddCors(options =>
            {
                options.AddPolicy(name: "MyPolicy",
                    policy =>
                    {
                        policy.AllowAnyOrigin()
                                .AllowAnyMethod()
                                .AllowAnyHeader();
                    });
            });

            var app = builder.Build();

            // habilita a compatibilidade com o tipo de dado DateTimeOffset no Banco de dados PostgreSQL
            AppContext.SetSwitch("Npgsql.EnableLegacyTimestampBehavior", true);

            // Criar o Banco de dados e as Tabelas

            using (var scope = app.Services.CreateAsyncScope())
            {
                var dbContext = scope.ServiceProvider.GetRequiredService<AppDbContext>();
                dbContext.Database.EnsureCreated();
                
            }

            // Swagger Como Página Inicial - Localhost

                app.UseSwagger();
                app.UseSwaggerUI();

            // Swagger Como Página Inicial - Nuvem

            if (app.Environment.IsProduction())
            {
                app.UseSwaggerUI( options =>
                {
                    options.SwaggerEndpoint("/swagger/v1/swagger.json", "Blog Pessoal - v1");
                    options.RoutePrefix = string.Empty;
                });
            }
                    

            // Inicializa o CORS
            app.UseCors("MyPolicy");

            // Autenticação do Usuário
            app.UseAuthentication();

            // Autorização do Usuário
            app.UseAuthorization();

            // Inicialização das Classes Controladoras
            app.MapControllers();

            app.Run();
        }
    }
}
```

<br />

<h2>👣 Passo 02- Atualizar a Classe AppDbContext</h2>



Vamos atualizar Classe **AppDbContext**, voltando ao estado inicial do ajuste da **data**, no Método **SaveChangesAsync()**:

Veja o código completo da Classe **AppDbContext**:

```c#
using blogpessoal.Model;
using Microsoft.EntityFrameworkCore;
using System.Threading;

namespace blogpessoal.Data
{
    public class AppDbContext: DbContext
    {
        public AppDbContext(DbContextOptions<AppDbContext> options) : base(options) { }

        protected override void OnModelCreating(ModelBuilder modelBuilder)
        {
            modelBuilder.Entity<Postagem>().ToTable("tb_postagens");
            modelBuilder.Entity<Tema>().ToTable("tb_temas");
            modelBuilder.Entity<User>().ToTable("tb_usuarios");

            modelBuilder.Entity<Postagem>()
                .HasOne(p => p.Tema)
                .WithMany(t => t.Postagem)
                .HasForeignKey("TemaId")
                .OnDelete(DeleteBehavior.Cascade);

             modelBuilder.Entity<Postagem>()
                .HasOne(p => p.Usuario)
                .WithMany(u => u.Postagem)
                .HasForeignKey("UsuarioId")
                .OnDelete(DeleteBehavior.Cascade);

        }

        // Registrar DbSet - Objeto responsável por manipular a Tabela

        public DbSet<Postagem> Postagens { get; set; } = null!;
        public DbSet<Tema> Temas { get; set; } = null!;
        public DbSet<User> Users { get; set; } = null!;

        public override Task<int> SaveChangesAsync(CancellationToken cancellationToken = default)
        {

            var insertedEntries = this.ChangeTracker.Entries()
                                   .Where(x => x.State == EntityState.Added)
                                   .Select(x => x.Entity);

            foreach (var insertedEntry in insertedEntries)
            {
                //Se uma propriedade da Classe Auditable estiver sendo criada. 
                if (insertedEntry is Auditable auditableEntity)
                {
                    //auditableEntity.Data = DateTimeOffset.Now;
                    auditableEntity.Data = new DateTimeOffset(DateTime.Now, new TimeSpan(-3,0,0));
                }
            }

            var modifiedEntries = ChangeTracker.Entries()
                       .Where(x => x.State == EntityState.Modified)
                       .Select(x => x.Entity);

            foreach (var modifiedEntry in modifiedEntries)
            {
                //Se uma propriedade da Classe Auditable estiver sendo atualizada.  
                if (modifiedEntry is Auditable auditableEntity)
                {
                    //auditableEntity.Data = DateTimeOffset.Now;
                    auditableEntity.Data = new DateTimeOffset(DateTime.Now, new TimeSpan(-3, 0, 0));
                }
            }

            return base.SaveChangesAsync(cancellationToken);
        }

    }
}

```

<br />

<h2>👣 Passo 03- Atualizar a Classe PostagemService</h2>



Vamos atualizar a Classe **PostagemService**:

**Método GetAll()**

```c#
public async Task<IEnumerable<Postagem>> GetAll()
{
    return await _context.Postagens
        .AsNoTracking()
        .Include(p => p.Tema)
        .Include(p => p.Usuario)
        .ToListAsync();
}
```

Acrescente o Método **.AsNoTracking()** para não exibir os dados das postagens nas entidades **Tema** e **Usuario**, no Método GetAll(). 

**Método GetByTitulo(string titulo)**

```c#
public async Task<IEnumerable<Postagem>> GetByTitulo(string titulo)
{
    var Postagem = await _context.Postagens
        .AsNoTracking()
        .Include(p => p.Tema)
        .Include(p => p.Usuario)
        .Where(p => p.Titulo.ToUpper()
             .Contains(titulo.ToUpper())
        )
        .ToListAsync();
    
    return Postagem;
}
```

Acrescente o Método **.AsNoTracking()** para não exibir os dados das postagens nas entidades **Tema** e **Usuario**, no Método GetByTitulo(). 

Acrescente o Método **ToUpper()** no Atributo e na Variável para manter a consulta Case Insentive (Ignorar Maiúsculas e Minúsculas) . O PostgresSQL do Render não está no formato Case Insensitive. 

<br />

<h2>👣 Passo 04- Atualizar a Classe TemaService</h2>



Vamos atualizar a Classe **TemaService**:

**Método GetByDescricao(string descricao)**

```c#
public async Task<IEnumerable<Tema>> GetByDescricao(string descricao)
{
    var Tema = await _context.Temas
        .Include(t => t.Postagem)
        .Where(T => T.Descricao.ToUpper()
             .Contains(descricao.ToUpper())
        )
        .ToListAsync();
    
    return Tema;
}
```

Acrescente o Método **ToUpper()** no Atributo e na Variável para manter a consulta Case Insentive (Ignorar Maiúsculas e Minúsculas) . O PostgresSQL do Render não está no formato Case Insensitive. 

Ao final, atualize o repositório no Github e aguarde o deploy ser finalizado.

<br />

<h2>👣 Passo 05 - Configurar o Fuso Horário do Servidor</h2>



Vamos configurar o fuso horário do servidor, para que o horário de criação e atualização da postagem seja persistido corretamente:

1. Na barra de menu lateral do WebService, clique na opção **Environment**:

<div align="center"><img src="https://i.imgur.com/WroFgOo.png" title="source: imgur.com" /></div>

2. Na sequência clique no botão **Add Environment Variable**:

<div align="center"><img src="https://i.imgur.com/OTgpqQg.png" title="source: imgur.com" /></div>

3. Na tela **Environment Variables**, crie uma variável chamada **TZ** e insira o valor **America/Sao_Paulo**, como mostra a imagem abaixo:

<div align="center"><img src="https://i.imgur.com/RBPZKtM.png" title="source: imgur.com" /></div>

4. Clique no botão **Save Changes** para concluir a configuração. 
5. O Deploy da aplicação será refeito. Aguarde a conclusão e inicie os testes da aplicação no próximo passo.

<br />
