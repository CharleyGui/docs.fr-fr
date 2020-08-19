---
title: Migrer de ASP.NET Web Forms vers Blazor
description: Découvrez comment aborder la migration d’une application Web Forms ASP.NET existante vers Blazor .
author: twsouthwick
ms.author: tasou
no-loc:
- Blazor
- WebAssembly
ms.date: 09/19/2019
ms.openlocfilehash: ba6dbfdf9a4fa9973dfe84cf5d58f1300f5d0cb4
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557540"
---
# <a name="migrate-from-aspnet-web-forms-to-no-locblazor"></a>Migrer de ASP.NET Web Forms vers Blazor

La migration d’une base de code à partir de ASP.NET Web Forms vers Blazor est une tâche longue qui nécessite une planification. Ce chapitre décrit le processus. Une opération qui peut faciliter la transition consiste à s’assurer que l’application adhère à une architecture *multiniveau* , dans laquelle le modèle d’application (dans ce cas, Web Forms) est séparé de la logique métier. Cette séparation logique des couches permet de clarifier ce qui doit être déplacé vers .NET Core et Blazor .

Pour cet exemple, l’application eShop disponible sur [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) est utilisée. eShop est un service de catalogue qui fournit des fonctionnalités CRUD via la saisie et la validation de formulaire.

Pourquoi une application de travail doit-elle être migrée vers Blazor ? Bien souvent, il n’y a aucun besoin. ASP.NET Web Forms sera toujours pris en charge depuis de nombreuses années. Toutefois, la plupart des fonctionnalités Blazor fournies par ne sont prises en charge que sur une application migrée. Ces fonctionnalités sont les suivantes :

- Améliorations des performances dans l’infrastructure, telles que `Span<T>`
- Possibilité de s’exécuter en tant que WebAssembly
- Prise en charge multiplateforme pour Linux et macOS
- Déploiement local de l’application ou déploiement d’infrastructure partagée sans impact sur les autres applications

Si ces nouvelles fonctionnalités ou d’autres sont suffisamment intéressantes, il peut y avoir une valeur pour la migration de l’application. La migration peut prendre différentes formes. Il peut s’agir de l’application entière, ou uniquement de certains points de terminaison qui requièrent des modifications. La décision de migrer est en fin de compte sur les problèmes d’entreprise à résoudre par le développeur.

## <a name="server-side-versus-client-side-hosting"></a>Côté serveur et hébergement côté client

Comme décrit dans le chapitre [modèles d’hébergement](hosting-models.md) , une Blazor application peut être hébergée de deux façons différentes : côté serveur et côté client. Le modèle côté serveur utilise des connexions ASP.NET Core Signalr pour gérer les mises à jour du modèle DOM tout en exécutant du code réel sur le serveur. Le modèle côté client s’exécute comme WebAssembly dans un navigateur et ne nécessite pas de connexion au serveur. Il existe un certain nombre de différences qui peuvent affecter la meilleure solution pour une application spécifique :

- L’exécution de en tant que WebAssembly est toujours en cours de développement et peut ne pas prendre en charge toutes les fonctionnalités (telles que le Threading) à l’heure actuelle.
- Une communication bavard entre le client et le serveur peut entraîner des problèmes de latence en mode côté serveur
- L’accès aux bases de données et aux services internes ou protégés requiert un service distinct avec l’hébergement côté client

Au moment de l’écriture, le modèle côté serveur ressemble davantage à Web Forms. La majeure partie de ce chapitre se concentre sur le modèle d’hébergement côté serveur, car il est prêt pour la production.

## <a name="create-a-new-project"></a>Créer un projet

Cette étape de migration initiale consiste à créer un nouveau projet. Ce type de projet est basé sur les projets de style SDK de .NET Core et simplifie la plupart des modèles utilisés dans les formats de projet précédents. Pour plus d’informations, consultez le chapitre sur la [structure de projet](project-structure.md).

Une fois le projet créé, installez les bibliothèques qui ont été utilisées dans le projet précédent. Dans les projets de Web Forms plus anciens, vous avez peut-être utilisé le fichier *packages.config* pour répertorier les packages NuGet requis. Dans le nouveau projet de type SDK, *packages.config* a été remplacé par des `<PackageReference>` éléments dans le fichier projet. L’avantage de cette approche est que toutes les dépendances sont installées de manière transitive. Vous répertoriez uniquement les dépendances de niveau supérieur qui vous intéressent.

La plupart des dépendances que vous utilisez sont disponibles pour .NET Core, y compris Entity Framework 6 et log4net. Si aucune version de .NET Core ou de .NET Standard n’est disponible, la version .NET Framework peut souvent être utilisée. Votre kilométrage peut varier. Toute API utilisée qui n’est pas disponible dans .NET Core provoque une erreur d’exécution. Visual Studio vous avertit de ces packages. Une icône jaune apparaît sur le nœud **références** du projet dans **Explorateur de solutions**.

Dans le Blazor projet eShop basé sur, vous pouvez voir les packages qui sont installés. Précédemment, le fichier *packages.config* répertorie chaque package utilisé dans le projet, ce qui a pour résultat un fichier d’une longueur de 50 lignes. Un extrait de *packages.config* est :

```xml
<?xml version="1.0" encoding="utf-8"?>
<packages>
  ...
  <package id="Microsoft.ApplicationInsights.Agent.Intercept" version="2.4.0" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.DependencyCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.PerfCounterCollector" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.Web" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.ApplicationInsights.WindowsServer.TelemetryChannel" version="2.9.1" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.FriendlyUrls.Core" version="1.0.2" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.MSAjax" version="5.0.0" targetFramework="net472" />
  <package id="Microsoft.AspNet.ScriptManager.WebForms" version="5.0.0" targetFramework="net472" />
  ...
  <package id="System.Memory" version="4.5.1" targetFramework="net472" />
  <package id="System.Numerics.Vectors" version="4.4.0" targetFramework="net472" />
  <package id="System.Runtime.CompilerServices.Unsafe" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Channels" version="4.5.0" targetFramework="net472" />
  <package id="System.Threading.Tasks.Extensions" version="4.5.1" targetFramework="net472" />
  <package id="WebGrease" version="1.6.0" targetFramework="net472" />
</packages>
```

L' `<packages>` élément comprend toutes les dépendances nécessaires. Il est difficile d’identifier les packages qui sont inclus, car vous en avez besoin. Certains `<package>` éléments sont répertoriés simplement pour répondre aux besoins des dépendances dont vous avez besoin.

Le Blazor projet répertorie les dépendances dont vous avez besoin dans un `<ItemGroup>` élément du fichier projet :

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Un package NuGet qui simplifie la vie des développeurs Web Forms est le [Pack de compatibilité Windows](../../core/porting/windows-compat-pack.md). Bien que .NET Core soit multiplateforme, certaines fonctionnalités sont uniquement disponibles sur Windows. Les fonctionnalités spécifiques à Windows sont mises à disposition en installant le Pack de compatibilité. Le registre, WMI et les services d’annuaire sont des exemples de ces fonctionnalités. Le package ajoute environ 20 000 API et active de nombreux services que vous connaissez peut-être déjà. Le projet eShop ne nécessite pas le Pack de compatibilité. Toutefois, si vos projets utilisent des fonctionnalités propres à Windows, le package facilite les efforts de migration.

## <a name="enable-startup-process"></a>Activer le processus de démarrage

Le processus de démarrage de Blazor a été modifié à partir de Web Forms et suit une configuration similaire pour d’autres services ASP.net core. Lorsqu’ils sont hébergés côté serveur, les Blazor composants sont exécutés dans le cadre d’une application ASP.net Core normale. Lorsqu’ils sont hébergés dans le navigateur avec WebAssembly , les Blazor composants utilisent un modèle d’hébergement similaire. La différence réside dans le fait que les composants sont exécutés en tant que service distinct à partir de l’un des processus principaux. Dans les deux cas, le démarrage est similaire.

Le fichier *global.asax.cs* est la page de démarrage par défaut pour les projets Web Forms. Dans le projet eShop, ce fichier configure le conteneur d’inversion de contrôle (IoC, inversion of Control) et gère les différents événements de cycle de vie de l’application ou de la demande. Certains de ces événements sont gérés avec l’intergiciel (par exemple, `Application_BeginRequest` ). D’autres événements requièrent la substitution de services spécifiques par le biais de l’injection de dépendances (DI).

Par exemple, le fichier *global.asax.cs* pour eShop contient le code suivant :

```csharp
public class Global : HttpApplication, IContainerProviderAccessor
{
    private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

    static IContainerProvider _containerProvider;
    IContainer container;

    public IContainerProvider ContainerProvider
    {
        get { return _containerProvider; }
    }

    protected void Application_Start(object sender, EventArgs e)
    {
        // Code that runs on app startup
        RouteConfig.RegisterRoutes(RouteTable.Routes);
        BundleConfig.RegisterBundles(BundleTable.Bundles);
        ConfigureContainer();
        ConfigDataBase();
    }

    /// <summary>
    /// Track the machine name and the start time for the session inside the current session
    /// </summary>
    protected void Session_Start(Object sender, EventArgs e)
    {
        HttpContext.Current.Session["MachineName"] = Environment.MachineName;
        HttpContext.Current.Session["SessionStartTime"] = DateTime.Now;
    }

    /// <summary>
    /// https://autofaccn.readthedocs.io/en/latest/integration/webforms.html
    /// </summary>
    private void ConfigureContainer()
    {
        var builder = new ContainerBuilder();
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);
        builder.RegisterModule(new ApplicationModule(mockData));
        container = builder.Build();
        _containerProvider = new ContainerProvider(container);
    }

    private void ConfigDataBase()
    {
        var mockData = bool.Parse(ConfigurationManager.AppSettings["UseMockData"]);

        if (!mockData)
        {
            Database.SetInitializer<CatalogDBContext>(container.Resolve<CatalogDBInitializer>());
        }
    }

    protected void Application_BeginRequest(object sender, EventArgs e)
    {
        //set the property to our new object
        LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper();

        LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo();

        _log.Debug("Application_BeginRequest");
    }
}
```

Le fichier précédent devient la `Startup` classe côté serveur Blazor :

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    public IConfiguration Configuration { get; }

    public IWebHostEnvironment Env { get; }

    // This method gets called by the runtime. Use this method to add services to the container.
    // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddRazorPages();
        services.AddServerSideBlazor();

        if (Configuration.GetValue<bool>("UseMockData"))
        {
            services.AddSingleton<ICatalogService, CatalogServiceMock>();
        }
        else
        {
            services.AddScoped<ICatalogService, CatalogService>();
            services.AddScoped<IDatabaseInitializer<CatalogDBContext>, CatalogDBInitializer>();
            services.AddSingleton<CatalogItemHiLoGenerator>();
            services.AddScoped(_ => new CatalogDBContext(Configuration.GetConnectionString("CatalogDBContext")));
        }
    }

    // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
    public void Configure(IApplicationBuilder app, ILoggerFactory loggerFactory)
    {
        loggerFactory.AddLog4Net("log4Net.xml");

        if (Env.IsDevelopment())
        {
            app.UseDeveloperExceptionPage();
        }
        else
        {
            app.UseExceptionHandler("/Home/Error");
        }

        // Middleware for Application_BeginRequest
        app.Use((ctx, next) =>
        {
            LogicalThreadContext.Properties["activityid"] = new ActivityIdHelper(ctx);
            LogicalThreadContext.Properties["requestinfo"] = new WebRequestInfo(ctx);
            return next();
        });

        app.UseStaticFiles();

        app.UseRouting();

        app.UseEndpoints(endpoints =>
        {
            endpoints.MapBlazorHub();
            endpoints.MapFallbackToPage("/_Host");
        });

        ConfigDataBase(app);
    }

    private void ConfigDataBase(IApplicationBuilder app)
    {
        using (var scope = app.ApplicationServices.CreateScope())
        {
            var initializer = scope.ServiceProvider.GetService<IDatabaseInitializer<CatalogDBContext>>();

            if (initializer != null)
            {
                Database.SetInitializer(initializer);
            }
        }
    }
}
```

L’une des modifications importantes que vous pouvez remarquer à partir de Web Forms est l’importance de DI. DI est un principe de GUID dans la conception de la ASP.NET Core. Il prend en charge la personnalisation de presque tous les aspects de l’infrastructure ASP.NET Core. Il existe même un fournisseur de services intégré qui peut être utilisé pour de nombreux scénarios. Si une personnalisation supplémentaire est nécessaire, elle peut être prise en charge par les nombreux projets de la communauté. Par exemple, vous pouvez transférer votre investissement de bibliothèque DI tiers.

Dans l’application eShop d’origine, il existe une certaine configuration pour la gestion des sessions. Étant donné que Blazor l’utilisation côté serveur ASP.net Core signalr pour la communication, l’état de session n’est pas pris en charge, car les connexions peuvent se produire indépendamment d’un contexte http. Une application qui utilise l’état de session doit être remaniée avant d’être exécutée en tant qu' Blazor application.

Pour plus d’informations sur le démarrage de l’application, consultez démarrage de l' [application](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>Migrer des modules et gestionnaires HTTP vers des intergiciels (middleware)

Les modules et gestionnaires HTTP sont des modèles courants dans Web Forms pour contrôler le pipeline de requête HTTP. Les classes qui implémentent `IHttpModule` ou `IHttpHandler` peuvent être inscrites et traiter les demandes entrantes. Web Forms configure des modules et des gestionnaires dans le fichier *web.config* . Web Forms est également fortement basé sur la gestion des événements du cycle de vie des applications. ASP.NET Core utilise à la place intergiciel. L’intergiciel est inscrit dans la `Configure` méthode de la `Startup` classe. L’ordre d’exécution des intergiciels est déterminé par l’ordre d’enregistrement.

Dans la section [activer le processus de démarrage](#enable-startup-process) , un événement de cycle de vie a été déclenché par Web Forms comme `Application_BeginRequest` méthode. Cet événement n’est pas disponible dans ASP.NET Core. Pour ce faire, il est possible d’implémenter un intergiciel (middleware) comme indiqué dans l’exemple de fichier *Startup.cs* . Cet intergiciel (middleware) fait la même logique, puis transfère le contrôle au gestionnaire suivant dans le pipeline d’intergiciel (middleware).

Pour plus d’informations sur la migration des modules et des gestionnaires, consultez [migrer des modules et des gestionnaires HTTP vers ASP.net Core intergiciel](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Migrer des fichiers statiques

Pour servir des fichiers statiques (par exemple, HTML, CSS, images et JavaScript), les fichiers doivent être exposés par un intergiciel (middleware). L’appel `UseStaticFiles` de la méthode permet le service des fichiers statiques à partir du chemin d’accès racine Web. Le répertoire racine Web par défaut est *wwwroot*, mais il peut être personnalisé. Comme inclus dans la `Configure` classe de eShop `Startup` :

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

Le projet eShop active l’accès aux fichiers statiques de base. De nombreuses personnalisations sont disponibles pour l’accès aux fichiers statiques. Pour plus d’informations sur l’activation des fichiers par défaut ou d’un Explorateur de fichiers, consultez [fichiers statiques dans ASP.net Core](/aspnet/core/fundamentals/static-files).

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Migrer le regroupement et la minimisation du Runtime

Le regroupement et la minimisation sont des techniques d’optimisation des performances pour réduire le nombre et la taille des demandes de serveur pour récupérer certains types de fichiers. JavaScript et CSS subissent souvent une certaine forme de regroupement ou de minimisation avant d’être envoyés au client. Dans ASP.NET Web Forms, ces optimisations sont gérées au moment de l’exécution. Les conventions d’optimisation sont définies comme un fichier *App_Start/bundleconfig.cs* . Dans ASP.NET Core, une approche plus déclarative est adoptée. Un fichier répertorie les fichiers à minimisésr, ainsi que les paramètres de minimisation spécifiques.

Pour plus d’informations sur le regroupement et la minimisation, consultez [regrouper et réduire des ressources statiques dans ASP.net Core](/aspnet/core/client-side/bundling-and-minification).

## <a name="migrate-aspx-pages"></a>Migrer des pages ASPX

Une page dans une application Web Forms est un fichier avec l’extension *. aspx* . Une page de Web Forms peut souvent être mappée à un composant dans Blazor . Un Blazor composant est créé dans un fichier avec l’extension *. Razor* . Pour le projet eShop, cinq pages sont converties en page Razor.

Par exemple, la vue Détails comprend trois fichiers dans le projet Web Forms : *Details. aspx*, *Details.aspx.cs*et *Details.aspx.Designer.cs*. Lors de la conversion en Blazor , le code-behind et le balisage sont combinés dans *Details. Razor*. La compilation Razor (équivalente aux fichiers *. Designer.cs* ) est stockée dans le répertoire *obj* et n’est pas, par défaut, visible dans **Explorateur de solutions**. La page Web Forms se compose du balisage suivant :

```aspx-csharp
<%@ Page Title="Details" Language="C#" MasterPageFile="~/Site.Master" AutoEventWireup="true" CodeBehind="Details.aspx.cs" Inherits="eShopLegacyWebForms.Catalog.Details" %>

<asp:Content ID="Details" ContentPlaceHolderID="MainContent" runat="server">
    <h2 class="esh-body-title">Details</h2>

    <div class="container">
        <div class="row">
            <asp:Image runat="server" CssClass="col-md-6 esh-picture" ImageUrl='<%#"/Pics/" + product.PictureFileName%>' />
            <dl class="col-md-6 dl-horizontal">
                <dt>Name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Name%>' />
                </dd>

                <dt>Description
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.Description%>' />
                </dd>

                <dt>Brand
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogBrand.Brand%>' />
                </dd>

                <dt>Type
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.CatalogType.Type%>' />
                </dd>
                <dt>Price
                </dt>

                <dd>
                    <asp:Label CssClass="esh-price" runat="server" Text='<%#product.Price%>' />
                </dd>

                <dt>Picture name
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.PictureFileName%>' />
                </dd>

                <dt>Stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.AvailableStock%>' />
                </dd>

                <dt>Restock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.RestockThreshold%>' />
                </dd>

                <dt>Max stock
                </dt>

                <dd>
                    <asp:Label runat="server" Text='<%#product.MaxStockThreshold%>' />
                </dd>

            </dl>
        </div>

        <div class="form-actions no-color esh-link-list">
            <a runat="server" href='<%# GetRouteUrl("EditProductRoute", new {id =product.Id}) %>' class="esh-link-item">Edit
            </a>
            |
            <a runat="server" href="~" class="esh-link-item">Back to list
            </a>
        </div>

    </div>
</asp:Content>
```

Le code-behind du balisage précédent comprend le code suivant :

```csharp
using eShopLegacyWebForms.Models;
using eShopLegacyWebForms.Services;
using log4net;
using System;
using System.Web.UI;

namespace eShopLegacyWebForms.Catalog
{
    public partial class Details : System.Web.UI.Page
    {
        private static readonly ILog _log = LogManager.GetLogger(System.Reflection.MethodBase.GetCurrentMethod().DeclaringType);

        protected CatalogItem product;

        public ICatalogService CatalogService { get; set; }

        protected void Page_Load(object sender, EventArgs e)
        {
            var productId = Convert.ToInt32(Page.RouteData.Values["id"]);
            _log.Info($"Now loading... /Catalog/Details.aspx?id={productId}");
            product = CatalogService.FindCatalogItem(productId);

            this.DataBind();
        }
    }
}
```

En cas de conversion en Blazor , la page Web Forms se traduit par le code suivant :

```razor
@page "/Catalog/Details/{id:int}"
@inject ICatalogService CatalogService
@inject ILogger<Details> Logger

<h2 class="esh-body-title">Details</h2>

<div class="container">
    <div class="row">
        <img class="col-md-6 esh-picture" src="@($"/Pics/{_item.PictureFileName}")">

        <dl class="col-md-6 dl-horizontal">
            <dt>
                Name
            </dt>

            <dd>
                @_item.Name
            </dd>

            <dt>
                Description
            </dt>

            <dd>
                @_item.Description
            </dd>

            <dt>
                Brand
            </dt>

            <dd>
                @_item.CatalogBrand.Brand
            </dd>

            <dt>
                Type
            </dt>

            <dd>
                @_item.CatalogType.Type
            </dd>
            <dt>
                Price
            </dt>

            <dd>
                @_item.Price
            </dd>

            <dt>
                Picture name
            </dt>

            <dd>
                @_item.PictureFileName
            </dd>

            <dt>
                Stock
            </dt>

            <dd>
                @_item.AvailableStock
            </dd>

            <dt>
                Restock
            </dt>

            <dd>
                @_item.RestockThreshold
            </dd>

            <dt>
                Max stock
            </dt>

            <dd>
                @_item.MaxStockThreshold
            </dd>

        </dl>
    </div>

    <div class="form-actions no-color esh-link-list">
        <a href="@($"/Catalog/Edit/{_item.Id}")" class="esh-link-item">
            Edit
        </a>
        |
        <a href="/" class="esh-link-item">
            Back to list
        </a>
    </div>

</div>

@code {
    private CatalogItem _item;

    [Parameter]
    public int Id { get; set; }

    protected override void OnInitialized()
    {
        Logger.LogInformation("Now loading... /Catalog/Details/{Id}", Id);

        _item = CatalogService.FindCatalogItem(Id);
    }
}
```

Notez que le code et le balisage se trouvent dans le même fichier. Tous les services requis sont rendus accessibles avec l' `@inject` attribut. Pour la `@page` directive, cette page est accessible au niveau de l' `Catalog/Details/{id}` itinéraire. La valeur de l’espace réservé de l’itinéraire `{id}` a été restreinte à un entier. Comme décrit dans la section [routage](pages-routing-layouts.md) , contrairement à Web Forms, un composant Razor indique explicitement son itinéraire et tous les paramètres qui sont inclus. De nombreux contrôles de Web Forms peuvent ne pas avoir des équivalents exacts dans Blazor . Il existe souvent un extrait de code HTML équivalent qui servira le même objectif. Par exemple, le `<asp:Label />` contrôle peut être remplacé par un `<label>` élément HTML.

### <a name="model-validation-in-no-locblazor"></a>Validation de modèle dans Blazor

Si votre code Web Forms comprend une validation, vous pouvez transférer une grande partie de ce que vous avez avec des modifications minimes. L’un des avantages de l’exécution de dans Blazor est que la même logique de validation peut être exécutée sans avoir besoin de JavaScript personnalisé. Les annotations de données facilitent la validation du modèle.

Par exemple, la page *Create. aspx* possède un formulaire de saisie de données avec validation. Voici un exemple d’extrait de code :

```aspx
<div class="form-group">
    <label class="control-label col-md-2">Name</label>
    <div class="col-md-3">
        <asp:TextBox ID="Name" runat="server" CssClass="form-control"></asp:TextBox>
        <asp:RequiredFieldValidator runat="server" ControlToValidate="Name" Display="Dynamic"
            CssClass="field-validation-valid text-danger" ErrorMessage="The Name field is required." />
    </div>
</div>
```

Dans Blazor , le balisage équivalent est fourni dans un fichier *Create. Razor* :

```razor
<EditForm Model="_item" OnValidSubmit="@...">
    <DataAnnotationsValidator />

    <div class="form-group">
        <label class="control-label col-md-2">Name</label>
        <div class="col-md-3">
            <InputText class="form-control" @bind-Value="_item.Name" />
            <ValidationMessage For="(() => _item.Name)" />
        </div>
    </div>

    ...
</EditForm>
```

Le `EditForm` contexte comprend la prise en charge de la validation et peut être encapsulé autour de l’entrée. Les annotations de données sont une méthode courante pour ajouter une validation. Une telle prise en charge de la validation peut être ajoutée via le `DataAnnotationsValidator` composant. Pour plus d’informations sur ce mécanisme, consultez [ASP.net Core Blazor Forms and validation](/aspnet/core/blazor/forms-validation).

## <a name="migrate-configuration"></a>Migrer une configuration

Dans un projet Web Forms, les données de configuration sont le plus souvent stockées dans le fichier *web.config* . Les données de configuration sont accessibles à l’aide de `ConfigurationManager` . Les services étaient souvent requis pour analyser des objets. Avec .NET Framework 4.7.2, la composabilité a été ajoutée à la configuration via `ConfigurationBuilders` . Ces générateurs permettaient aux développeurs d’ajouter différentes sources pour la configuration qui était ensuite composée au moment de l’exécution pour récupérer les valeurs nécessaires.

ASP.NET Core a introduit un système de configuration flexible qui vous permet de définir la ou les sources de configuration utilisées par votre application et votre déploiement. L' `ConfigurationBuilder` infrastructure que vous utilisez peut-être dans votre application Web Forms a été modélisée après les concepts utilisés dans le système de configuration ASP.net core.

L’extrait de code suivant montre comment le projet Web Forms eShop utilise *web.config* pour stocker les valeurs de configuration :

```xml
<configuration>
  <configSections>
    <section name="entityFramework" type="System.Data.Entity.Internal.ConfigFile.EntityFrameworkSection, EntityFramework, Version=6.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" requirePermission="false" />
  </configSections>
  <connectionStrings>
    <add name="CatalogDBContext" connectionString="Data Source=(localdb)\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;" providerName="System.Data.SqlClient" />
  </connectionStrings>
  <appSettings>
    <add key="UseMockData" value="true" />
    <add key="UseCustomizationData" value="false" />
  </appSettings>
</configuration>
```

Il est courant que les secrets, tels que les chaînes de connexion de base de données, soient stockés dans le *web.config*. Les secrets sont inévitablement conservés dans des emplacements non sécurisés, tels que le contrôle de code source. Avec Blazor sur ASP.net Core, la configuration XML précédente est remplacée par le code JSON suivant :

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON est le format de configuration par défaut ; Toutefois, ASP.NET Core prend en charge de nombreux autres formats, y compris XML. Il existe également plusieurs formats pris en charge par la communauté.

Le constructeur dans la Blazor classe du projet `Startup` accepte une `IConfiguration` instance par le biais d’une technique di appelée injection de constructeur :

```csharp
public class Startup
{
    public Startup(IConfiguration configuration, IWebHostEnvironment env)
    {
        Configuration = configuration;
        Env = env;
    }

    ...
}
```

Par défaut, les variables d’environnement, les fichiers JSON (*appsettings.jssur* et *appSettings. { Environment}. JSON*), et les options de ligne de commande sont inscrites en tant que sources de configuration valides dans l’objet de configuration. Vous pouvez accéder aux sources de configuration via `Configuration[key]` . Une technique plus avancée consiste à lier les données de configuration aux objets à l’aide du modèle d’options. Pour plus d’informations sur la configuration et le modèle d’options, consultez [configuration in ASP.net Core](/aspnet/core/fundamentals/configuration/) and [options pattern in ASP.net Core](/aspnet/core/fundamentals/configuration/options), respectivement.

## <a name="migrate-data-access"></a>Migrer l’accès aux données

L’accès aux données est un aspect important de toute application. Le projet eShop stocke les informations de catalogue dans une base de données et récupère les données avec Entity Framework (EF) 6. Comme EF 6 est pris en charge dans .NET Core 3,0, le projet peut continuer à l’utiliser.

Les modifications suivantes liées à EF étaient nécessaires à eShop :

- Dans .NET Framework, l' `DbContext` objet accepte une chaîne sous la forme *nom = ConnectionString* et utilise la chaîne de connexion de `ConfigurationManager.AppSettings[ConnectionString]` pour se connecter. Dans .NET Core, cela n’est pas pris en charge. La chaîne de connexion doit être fournie.
- L’accès à la base de données a été effectué de façon synchrone. Bien que cela fonctionne, l’évolutivité peut en pâtir. Cette logique doit être déplacée vers un modèle asynchrone.

Bien qu’il n’y ait pas la même prise en charge native pour la liaison de jeu de données, Blazor offre la flexibilité et la puissance avec sa prise en charge C# dans une page Razor. Par exemple, vous pouvez effectuer des calculs et afficher le résultat. Pour plus d’informations sur les modèles de données dans Blazor , consultez le chapitre relatif [à l’accès aux données](data.md) .

## <a name="architectural-changes"></a>Modifications architecturales

Enfin, il existe quelques différences architecturales importantes à prendre en compte lors de la migration vers Blazor . La plupart de ces modifications sont applicables à tout ce qui est basé sur .NET Core ou ASP.NET Core.

Étant donné que Blazor repose sur .net Core, il existe des éléments à prendre en compte pour garantir la prise en charge de .net core. Parmi les principales modifications, citons la suppression des fonctionnalités suivantes :

- AppDomains multiples
- Communication à distance
- Sécurité d'accès du code
- Transparence de la sécurité

Pour plus d’informations sur les techniques permettant d’identifier les modifications nécessaires à la prise en charge de l’exécution sur .NET Core, consultez [porter votre code d' .NET Framework vers .net Core](/dotnet/core/porting).

ASP.NET Core est une version repensée de ASP.NET et contient des modifications qui peuvent ne pas paraître évidentes. Les principales modifications sont les suivantes :

- Aucun contexte de synchronisation, ce qui signifie qu’il n’y a aucun `HttpContext.Current` , `Thread.CurrentPrincipal` ou d’autres accesseurs statiques
- Pas de clichés instantanés
- Aucune file d’attente de demandes

De nombreuses opérations dans ASP.NET Core sont asynchrones, ce qui permet de faciliter le chargement des tâches liées aux e/s. Il est important de ne jamais bloquer à l’aide de `Task.Wait()` ou de `Task.GetResult()` , ce qui peut épuiser rapidement les ressources du pool de threads.

## <a name="migration-conclusion"></a>Conclusion de la migration

À ce stade, vous avez vu de nombreux exemples de ce qu’il faut pour déplacer un projet Web Forms vers Blazor . Pour obtenir un exemple complet, consultez le projet [eShopOn Blazor ](https://github.com/dotnet-architecture/eShopOnBlazor) .

>[!div class="step-by-step"]
>[Précédent](security-authentication-authorization.md)
