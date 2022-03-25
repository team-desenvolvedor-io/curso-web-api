## No ASP.NET 6 existem algumas mudanças na maneira de criar e configurar a API, caso seja esta a versão que está utilizando siga as instruções com atenção:

### Novo projeto via console

#### A criação do projeto via console permanece igual conforme a aula em vídeo, segue uma série de comandos interessantes para conhecer:

> Listando todos os templates disponíveis

```
dotnet new --list
```
> Resultado

```
These templates matched your input:

Template Name                                 Short Name           Language    Tags
--------------------------------------------  -------------------  ----------  -------------------------------------
ASP.NET Core Empty                            web                  [C#],F#     Web/Empty
ASP.NET Core gRPC Service                     grpc                 [C#]        Web/gRPC
ASP.NET Core Web API                          webapi               [C#],F#     Web/WebAPI
ASP.NET Core Web App                          razor,webapp         [C#]        Web/MVC/Razor Pages
ASP.NET Core Web App (Model-View-Controller)  mvc                  [C#],F#     Web/MVC
ASP.NET Core with Angular                     angular              [C#]        Web/MVC/SPA
ASP.NET Core with React.js                    react                [C#]        Web/MVC/SPA
ASP.NET Core with React.js and Redux          reactredux           [C#]        Web/MVC/SPA
Blazor Server App                             blazorserver         [C#]        Web/Blazor
Blazor WebAssembly App                        blazorwasm           [C#]        Web/Blazor/WebAssembly/PWA
Class Library                                 classlib             [C#],F#,VB  Common/Library
Console App                                   console              [C#],F#,VB  Common/Console
dotnet gitignore file                         gitignore                        Config
Dotnet local tool manifest file               tool-manifest                    Config
EditorConfig file                             editorconfig                     Config
global.json file                              globaljson                       Config
MSTest Test Project                           mstest               [C#],F#,VB  Test/MSTest
MVC ViewImports                               viewimports          [C#]        Web/ASP.NET
MVC ViewStart                                 viewstart            [C#]        Web/ASP.NET
NuGet Config                                  nugetconfig                      Config
NUnit 3 Test Item                             nunit-test           [C#],F#,VB  Test/NUnit
NUnit 3 Test Project                          nunit                [C#],F#,VB  Test/NUnit
Protocol Buffer File                          proto                            Web/gRPC
Razor Class Library                           razorclasslib        [C#]        Web/Razor/Library/Razor Class Library
Razor Component                               razorcomponent       [C#]        Web/ASP.NET
Razor Page                                    page                 [C#]        Web/ASP.NET
Solution File                                 sln                              Solution
Web Config                                    webconfig                        Config
Windows Forms App                             winforms             [C#],VB     Common/WinForms
Windows Forms Class Library                   winformslib          [C#],VB     Common/WinForms
Windows Forms Control Library                 winformscontrollib   [C#],VB     Common/WinForms
Worker Service                                worker               [C#],F#     Common/Worker/Web
WPF Application                               wpf                  [C#],VB     Common/WPF
WPF Class library                             wpflib               [C#],VB     Common/WPF
WPF Custom Control Library                    wpfcustomcontrollib  [C#],VB     Common/WPF
WPF User Control Library                      wpfusercontrollib    [C#],VB     Common/WPF
xUnit Test Project                            xunit                [C#],F#,VB  Test/xUnit
```

#### O nome do template que utilizaremos é o "webapi".

> Listando todas as opções de criação de um projeto API, escolha se utilizará HTTPS, versão do .NET, Autenticação e diversas opções

```
dotnet new webapi -h
```

> Resultado

```
Description: A project template for creating an ASP.NET Core application with an example Controller for a RESTful HTTP service. This template can also be used for ASP.NET Core MVC Views and Controllers.
Options:

  -au|--auth                   The type of authentication to use

                                   None             - No authentication

                                   IndividualB2C    - Individual authentication with Azure AD B2C

                                   SingleOrg        - Organizational authentication for a single tenant

                                   Windows          - Windows authentication

                               Default: None


  --aad-b2c-instance           The Azure Active Directory B2C instance to connect to (use with IndividualB2C auth).

                               string - Optional

                               Default: https://qualified.domain.name.b2clogin.com/


  -ssp|--susi-policy-id        The sign-in and sign-up policy ID for this project (use with IndividualB2C auth).

                               string - Optional

                               Default: b2c_1_susi


  --aad-instance               The Azure Active Directory instance to connect to (use with SingleOrg auth).

                               string - Optional

                               Default: https://login.microsoftonline.com/


  --client-id                  The Client ID for this project (use with SingleOrg or IndividualB2C auth).

                               string - Optional

                               Default: 11111111-1111-1111-11111111111111111


  --domain                     The domain for the directory tenant (use with SingleOrg or IndividualB2C auth).

                               string - Optional

                               Default: qualified.domain.name


  --default-scope              The API scope the client needs to request to provision an access token. (use with IndividualB2C, SingleOrg).

                               string - Optional

                               Default: access_as_user


  --tenant-id                  The TenantId ID of the directory to connect to (use with SingleOrg auth).

                               string - Optional

                               Default: 22222222-2222-2222-2222-222222222222


  -r|--org-read-access         Whether or not to allow this application read access to the directory (only applies to SingleOrg auth).

                               bool - Optional

                               Default: false


  --exclude-launch-settings    Whether to exclude launchSettings.json in the generated template.

                               bool - Optional

                               Default: false


  --no-https                   Whether to turn off HTTPS. This option only applies if Individual, IndividualB2C, SingleOrg, or MultiOrg aren't used for --auth.
                               bool - Optional

                               Default: false


  -uld|--use-local-db          Whether to use LocalDB instead of SQLite. This option only applies if --auth Individual or --auth IndividualB2C is specified.
                               bool - Optional

                               Default: false


  -minimal|--use-minimal-apis  Whether to use minimal APIs instead of controllers.

                               bool - Optional

                               Default: false


  -f|--framework               The target framework for the project.

                                   net6.0           - Target net6.0

                                   net5.0           - Target net5.0

                                   netcoreapp3.1    - Target netcoreapp3.1

                                   netcoreapp3.0    - Target netcoreapp3.0

                                   netcoreapp2.1    - Target netcoreapp2.1

                               Default: net6.0


  --no-restore                 If specified, skips the automatic restore of the project on create.

                               bool - Optional

                               Default: false


  --called-api-url             URL of the API to call from the web app. This option only applies if --auth SingleOrg or --auth IndividualB2C is specified.
                               string - Optional

                               Default: https://graph.microsoft.com/v1.0


  --calls-graph                Specifies if the web app calls Microsoft Graph. This option only applies if --auth SingleOrg is specified.

                               bool - Optional

                               Default: false


  --called-api-scopes          Scopes to request to call the API from the web app. This option only applies if --auth SingleOrg or --auth IndividualB2C is specified.
                               string - Optional

                               Default: user.read


  --no-openapi                 Disable OpenAPI (Swagger) support

                               bool - Optional

                               Default: false



To see help for other template languages (F#), use --language option:
   dotnet new webapi -h --language F#
```

#### Criação do projeto

> Execute o comando a seguir e utilize o parametro -n para definir um nome de sua escolha

```
dotnet new webapi -n MinhaAPI
```

---

### Visual Studio Code

#### Execute o mesmo comando acima e ao finalizar a criação abra via VS Code com os comando a seguir

> Acesse o diretório da aplicação criada (ex: MinhaAPI)

```
cd MinhaAPI
```

> Execute o comando para chamar o VS Code dentro daquele diretório. O ponto após o espaço significa que o diretório de referência é onde o comando está sendo executado.

```
code .
```

---

### Utilizando Visual Studio 2019 ou 2022 siga os passos:

#### Criação do projeto:

![image](https://user-images.githubusercontent.com/5068797/158006937-05f1a481-746f-48e8-9fae-8d9394bc86e4.png)

#### Procure por API para facilitar a pesquisa do template correto, na sequencia **selecione a opção ASP.NET Core Web API**

> Atenção ao escolher com suporte a C# verifique que o ícone possui o simbolo C#

![image](https://user-images.githubusercontent.com/5068797/160076867-332f92a5-14fa-465f-827f-c7cd7db9f641.png)

#### Defina o nome do seu projeto:

![image](https://user-images.githubusercontent.com/5068797/160077332-f17265c5-c85f-497d-b029-80c246efed9e.png)

Escolha a versão do .NET, por razões de estudos sempre utilize a última versão.

![image](https://user-images.githubusercontent.com/5068797/160077838-1eb60a43-5054-4ee1-8f7f-e7666b149311.png)

- [ ] Authentication Type - None, pois iremos adicionar manualmente
- [x] Configure for HTTPS - Para gerar com suporte a SSL
- [ ] Enable Docker - Não precisaremos neste momento
- [x] Use Controllers - Não utilizaremos Minimal API (conheça mais sobre minimal API's [neste vídeo](https://www.youtube.com/watch?v=aXayqUfSNvw))
- [x] Enable OpenAPI support - Para ativar suporte ao Swagger (documentação REST)

#### O projeto será criado, observe a estrutura de projeto WebAPI do ASP.NET 6

![image](https://user-images.githubusercontent.com/5068797/160078936-baa253fb-7d49-4827-a945-38c8424029e0.png)

## Mudanças na WebAPI no ASP.NET 6

### Por uma questão de compatibilização com o padrão de código escrito em C# até o momento é recomendável desativar o suporte a validação de Nullable Types do CSPROJ (clique 2x no projeto para abrir):

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>net6.0</TargetFramework>
    <Nullable>enable</Nullable>
    <ImplicitUsings>enable</ImplicitUsings>
    <UserSecretsId>aspnet-AppMvcBasica-E371D4CD-D91B-418D-B969-E35920E572C4</UserSecretsId>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.Diagnostics.EntityFrameworkCore" Version="6.0.3" />
    <PackageReference Include="Microsoft.AspNetCore.Identity.EntityFrameworkCore" Version="6.0.3" />
    <PackageReference Include="Microsoft.AspNetCore.Identity.UI" Version="6.0.3" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="6.0.3" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="6.0.3" />
  </ItemGroup>

</Project>
```

#### É importante remover esta chave em todos os projetos que forem criados caso não queira tratar cada propriedade do seu código como Nullable

```xml
<Nullable>enable</Nullable>
```

---

### A grande e notável mudança é a saída da classe Startup.cs, toda sua responsabilidade foi levada para a classe Program.cs (que já existia desde sempre). Não é mais necessário ter uma classe startup, mas caso você queira manter a sua num projeto ASP.NET 6 ainda é possível, siga este tutorial [no Youtube](https://www.youtube.com/watch?v=VgjHQvprRy0)

#### Preste atenção aos comentários na classe Program.cs abaixo, é importante entender algumas responsabilidades:

```csharp
// O builder é responsável por fornecer os métodos de controle
// dos serviços e demais funcionalidades na configuração da App
var builder = WebApplication.CreateBuilder(args);

// Daqui para baixo é conteúdo que vinha dentro do método  ConfigureServices() na antiga Startup.cs
// Nesta area adicionamos serviços ao pipeline

// Essa é a nova forma atual de adicionar suporte a API
builder.Services.AddControllers();

// Adicionando suporte de geradores de metadados (para documentação)
builder.Services.AddEndpointsApiExplorer();

// Adicionando suporte a documentação OpenAPI
builder.Services.AddSwaggerGen();

// Essa linha precisa sempre ficar por último na configuração dos serviços
var app = builder.Build();

// Daqui para baixo é conteúdo que vinha dentro do método Configure() na antiga Startup.cs
// Aqui se configura comportamentos do request dentro do pipeline
if (app.Environment.IsDevelopment())
{
    // Chamando o uso do Swagger quando for modo desenvolvimento
    app.UseSwagger();
    app.UseSwaggerUI();
}

// Força o redirecionamento HTTPS
app.UseHttpsRedirection();

// Implementa o uso de validação de autorização
app.UseAuthorization();

// Mapeia todas as controllers para criar uma coleção de rotas
app.MapControllers();

// Essa linha precisa sempre ficar por último na configuração do request pipeline
app.Run();
```
---

### Diferente do exibido na aula em vídeo, a controller criada no começo do projeto é diferente:

```csharp
using Microsoft.AspNetCore.Mvc;

namespace MinhaAPI.Controllers
{
    // Para uma controller responder como API precisa ter esse atributo
    [ApiController]
    
    // Rota - No caso de uso de [controller] a rota será o nome da controller ex:
    // https://localhost:5001/WeatherForecast
    [Route("[controller]")]
    public class WeatherForecastController : ControllerBase // <<< Repare na Herança da controller base, é uma classe controller mais simples do que a do MVC    
    {
        private static readonly string[] Summaries = new[]
        {
          "Freezing", "Bracing", "Chilly", "Cool", "Mild", "Warm", "Balmy", "Hot", "Sweltering", "Scorching"
        };

        // Declaração do Logger do ASPNET
        private readonly ILogger<WeatherForecastController> _logger;
        
        // DI do logger 
        public WeatherForecastController(ILogger<WeatherForecastController> logger)
        {
            _logger = logger;
        }

        // Action (verbo GET)
        // Irá retornar uma coleção (fake) de previsão do tempo
        // GET - https://localhost:5001/WeatherForecast/
        [HttpGet(Name = "GetWeatherForecast")]
        public IEnumerable<WeatherForecast> Get()
        {
            return Enumerable.Range(1, 5).Select(index => new WeatherForecast
            {
                Date = DateTime.Now.AddDays(index),
                TemperatureC = Random.Shared.Next(-20, 55),
                Summary = Summaries[Random.Shared.Next(Summaries.Length)]
            })
            .ToArray();
        }
    }
}
```
--- 

### O arquivo launchSettings.json já vem preparado para HTTP e HTTPS assim como rodar o projeto via IISExpress ou Kestrel


#### Entendendo estas sutis mudanças você não terá problemas em estudar utilizando o ASP.NET 6 em seu projeto.

#### Em caso de dúvidas baixe o nosso projeto em .NET 6 e compare com o seu código [Projetos para Donwload](https://desenvolvedor.io/curso/dominando-o-asp-net-mvc-core/links-materiais) 
