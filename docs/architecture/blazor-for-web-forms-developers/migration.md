---
title: Migrer de ASP.NET formulaires Web à Blazor
description: Apprenez à aborder la migration d’une application Web Forms ASP.NET existante à Blazor.
author: twsouthwick
ms.author: tasou
ms.date: 09/19/2019
ms.openlocfilehash: 0a10a9a3d5ab32e16cb59a68da57116e20c53e49
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134088"
---
# <a name="migrate-from-aspnet-web-forms-to-blazor"></a>Migrer de ASP.NET formulaires Web à Blazor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

La migration d’une base de code de ASP.NET Web Forms à Blazor est une tâche qui prend beaucoup de temps et nécessite une planification. Ce chapitre décrit le processus. Quelque chose qui peut faciliter la transition est de s’assurer que l’application adhère à une architecture de *niveau N,* dans lequel le modèle d’application (dans ce cas, Web Forms) est séparé de la logique métier. Cette séparation logique des couches indique clairement ce qui doit passer à .NET Core et Blazor.

Pour cet exemple, l’application eShop disponible sur [GitHub](https://github.com/dotnet-architecture/eShopOnBlazor) est utilisée. eShop est un service de catalogue qui fournit des capacités CRUD via l’entrée et la validation du formulaire.

Pourquoi une application de travail devrait-elle être migrée vers Blazor ? Plusieurs fois, il n’y a pas besoin. ASP.NET formulaires Web continueront d’être soutenus pendant de nombreuses années. Cependant, bon nombre des fonctionnalités que Blazor fournit ne sont prises en charge que sur une application migrée. Ces caractéristiques comprennent :

- Amélioration du rendement dans le cadre, comme`Span<T>`
- Capacité à fonctionner comme WebAssembly
- Support multiplateforme pour Linux et macOS
- Déploiement App-local ou déploiement de cadres partagés sans impact sur d’autres applications

Si ces nouvelles fonctionnalités ou d’autres sont assez convaincantes, il peut y avoir de la valeur dans la migration de l’application. La migration peut prendre différentes formes; il peut s’agir de l’application entière, ou seulement de certains paramètres qui nécessitent les modifications. La décision de migrer est finalement basée sur les problèmes d’affaires à résoudre par le développeur.

## <a name="server-side-versus-client-side-hosting"></a>Serveur-côté contre l’hébergement côté client

Comme décrit dans le chapitre [des modèles d’hébergement,](hosting-models.md) une application Blazor peut être hébergée de deux façons différentes : côté serveur et côté client. Le modèle côté serveur utilise ASP.NET connexions Core SignalR pour gérer les mises à jour DOM tout en exécutant n’importe quel code réel sur le serveur. Le modèle côté client fonctionne sous forme de WebAssembly dans un navigateur et ne nécessite aucune connexion serveur. Il existe un certain nombre de différences qui peuvent affecter qui est le mieux pour une application spécifique:

- En cours d’exécution comme WebAssembly est encore en développement et peut ne pas prendre en charge toutes les fonctionnalités (comme le threading) à l’heure actuelle
- La communication bavarde entre le client et le serveur peut causer des problèmes de latence en mode serveur
- L’accès aux bases de données et aux services internes ou protégés nécessite un service distinct avec un hébergement côté client

Au moment d’écrire ces lignes, le modèle côté serveur ressemble plus étroitement aux formulaires Web. La plupart de ce chapitre se concentre sur le modèle d’hébergement côté serveur, car il est prêt à la production.

## <a name="create-a-new-project"></a>Création d'un projet

Cette première étape migratoire consiste à créer un nouveau projet. Ce type de projet est basé sur les projets de style SDK de .NET Core et simplifie une grande partie de la plaque chauffante qui a été utilisée dans les formats de projet précédents. Pour plus de détails, veuillez consulter le chapitre sur [la structure du projet](project-structure.md).

Une fois le projet créé, installez les bibliothèques qui ont été utilisées dans le projet précédent. Dans d’anciens projets Web Forms, vous avez peut-être utilisé le fichier *packages.config* pour énumérer les paquets NuGet requis. Dans le nouveau projet de style SDK, *packages.config* a été remplacé par `<PackageReference>` des éléments dans le dossier du projet. Un avantage à cette approche est que toutes les dépendances sont installées de façon transitive. Vous n’énumérez que les dépendances de haut niveau qui vous tiennent à cœ place.

Bon nombre des dépendances que vous utilisez sont disponibles pour .NET Core, y compris Entity Framework 6 et log4net. S’il n’y a pas de version standard .NET ou .NET disponible, la version cadre .NET peut souvent être utilisée. Votre kilométrage peut varier. Toute API utilisée qui n’est pas disponible en .NET Core provoque une erreur de temps d’exécution. Visual Studio vous informe de ces paquets. Une icône jaune apparaît sur le nœud **Références** du projet dans **Solution Explorer**.

Dans le projet eShop basé à Blazor, vous pouvez voir les paquets qui sont installés. Auparavant, le fichier *packages.config* énumérait tous les paquets utilisés dans le projet, ce qui a donné lieu à un fichier de près de 50 lignes de long. Un extrait de *packages.config* est :

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

L’élément `<packages>` comprend toutes les dépendances nécessaires. Il est difficile d’identifier lequel de ces paquets sont inclus parce que vous en avez besoin. Certains `<package>` éléments sont énumérés simplement pour satisfaire les besoins des dépendances dont vous avez besoin.

Le projet Blazor répertorie les `<ItemGroup>` dépendances dont vous avez besoin dans un élément du dossier du projet :

```xml
<ItemGroup>
    <PackageReference Include="Autofac" Version="4.9.3" />
    <PackageReference Include="EntityFramework" Version="6.3.0-preview9-19423-04" />
    <PackageReference Include="log4net" Version="2.0.8" />
</ItemGroup>
```

Un paquet NuGet qui simplifie la vie des développeurs Web Forms est le [Pack de Compatibilité Windows](../../core/porting/windows-compat-pack.md). Bien que .NET Core est multi-plateforme, certaines fonctionnalités ne sont disponibles que sur Windows. Les fonctionnalités spécifiques à Windows sont mises à disposition en installant le pack de compatibilité. Les services d’annuaire, de l’IMC et des services d’annuaire, en sont des exemples. Le paquet ajoute environ 20.000 API et active de nombreux services avec lesquels vous pouvez déjà être familier. Le projet eShop ne nécessite pas le pack de compatibilité; mais si vos projets utilisent des fonctionnalités spécifiques à Windows, le paquet facilite les efforts de migration.

## <a name="enable-startup-process"></a>Activer le processus de démarrage

Le processus de démarrage de Blazor a changé de Web Forms et suit une configuration similaire pour d’autres services ASP.NET Core. Lorsqu’ils sont hébergés côté serveur, les composants Blazor sont exécutés dans le cadre d’une application standard ASP.NET Core. Lorsqu’ils sont hébergés dans le navigateur avec WebAssembly, les composants Blazor utilisent un modèle d’hébergement similaire. La différence est que les composants sont exécutés comme un service distinct de l’un des processus backend. Quoi qu’il en soit, la startup est similaire.

Le *fichier Global.asax.cs* est la page de démarrage par défaut pour les projets Web Forms. Dans le projet eShop, ce fichier configure le conteneur Inversion of Control (IoC) et gère les différents événements du cycle de vie de l’application ou de la demande. Certains de ces événements sont traités avec `Application_BeginRequest`middleware (comme ). D’autres événements nécessitent la suppression de services spécifiques par injection de dépendance (DI).

À titre d’exemple, le *fichier Global.asax.cs* pour eShop, contient le code suivant :

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
    /// http://docs.autofac.org/en/latest/integration/webforms.html
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

Le fichier précédent `Startup` devient la classe dans Le serveur-côté Blazor:

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

Un changement important que vous pouvez remarquer à partir de formulaires Web est la proéminence de DI. DI a été un principe directeur dans la conception ASP.NET Core. Il soutient la personnalisation de presque tous les aspects du cadre ASP.NET Core. Il y a même un fournisseur de services intégré qui peut être utilisé pour de nombreux scénarios. Si une personnalisation plus grande est nécessaire, elle peut être soutenue par les nombreux projets communautaires. Par exemple, vous pouvez reporter votre investissement de bibliothèque DI tiers.

Dans l’application eShop originale, il y a une certaine configuration pour la gestion de session. Étant donné que Blazor utilise ASP.NET Core SignalR pour la communication, l’état de session n’est pas pris en charge car les connexions peuvent se produire indépendamment d’un contexte HTTP. Une application qui utilise l’état de session nécessite un backchitecting avant de fonctionner comme une application Blazor.

Pour plus d’informations sur le démarrage de l’application, voir [App startup](app-startup.md).

## <a name="migrate-http-modules-and-handlers-to-middleware"></a>Migrer les modules et les gestionnaires HTTP vers middleware

Les modules ET les gestionnaires HTTP sont des modèles courants dans les formulaires Web pour contrôler le pipeline de demande HTTP. Classes qui `IHttpModule` `IHttpHandler` mettent en œuvre ou pourraient être enregistrées et traitent les demandes entrantes. Web Forms configure des modules et des gestionnaires dans le fichier *web.config.* Web Forms est également fortement basé sur la gestion des événements du cycle de vie de l’application. ASP.NET Core utilise plutôt middleware. Middleware est enregistré `Configure` dans `Startup` la méthode de la classe. L’ordre d’exécution De Middleware est déterminé par l’ordre d’enregistrement.

Dans la section [Processus de démarrage Enable,](#enable-startup-process) un événement `Application_BeginRequest` de cycle de vie a été soulevé par Web Forms comme méthode. Cet événement n’est pas disponible dans ASP.NET Core. Une façon d’atteindre ce comportement est de mettre en œuvre middleware comme on le voit dans *l’exemple de* fichier Startup.cs. Ce middleware fait la même logique, puis transfère le contrôle au prochain gestionnaire dans le pipeline middleware.

Pour plus d’informations sur les modules et les gestionnaires de migration, voir [les gestionnaires et modules Migrate HTTP pour ASP.NET Core middleware](/aspnet/core/migration/http-modules).

## <a name="migrate-static-files"></a>Migrer les fichiers statiques

Pour servir des fichiers statiques (par exemple, HTML, CSS, images et JavaScript), les fichiers doivent être exposés par middleware. L’appel de la `UseStaticFiles` méthode permet de servir des fichiers statiques à partir du chemin de racine web. Le répertoire par défaut de racine web est *wwwroot*, mais il peut être personnalisé. Comme inclus `Configure` dans la méthode `Startup` de la classe eShop:

```csharp
public void Configure(IApplicationBuilder app)
{
    ...

    app.UseStaticFiles();

    ...
}
```

Le projet eShop permet un accès statique de base aux fichiers. De nombreuses personnalisations sont disponibles pour l’accès statique aux fichiers. Pour obtenir des informations sur l’activation de fichiers par défaut ou d’un navigateur de fichiers, consultez [les fichiers statiques dans ASP.NET Core](/aspnet/core/fundamentals/static-files).

## <a name="migrate-runtime-bundling-and-minification-setup"></a>Migrer le regroupement et la minification de l’exécution

Le regroupement et la minification sont des techniques d’optimisation des performances pour réduire le nombre et la taille des demandes de serveur pour récupérer certains types de fichiers. JavaScript et CSS subissent souvent une forme quelconque de regroupement ou de minification avant d’être envoyés au client. Dans ASP.NET formulaires Web, ces optimisations sont traitées au moment de l’exécution. Les conventions d’optimisation sont *définies App_Start/BundleConfig.cs.* Dans ASP.NET Core, une approche plus déclarative est adoptée. Un fichier répertorie les fichiers à minifier, ainsi que des paramètres de minification spécifiques.

Pour plus d’informations sur le regroupement et la minification, voir [Bundle et minifier les actifs statiques dans ASP.NET Core](/aspnet/core/client-side/bundling-and-minification).

## <a name="migrate-aspx-pages"></a>Migrer les pages ASPX

Une page d’une application Web Forms est un fichier avec l’extension *.aspx.* Une page Web Forms peut souvent être cartographiée sur un composant de Blazor. Un composant Blazor est rédigé dans un fichier avec l’extension *.razor.* Pour le projet eShop, cinq pages sont converties en une page Razor.

Par exemple, la vue des détails est composée de trois fichiers dans le projet Web Forms: *Details.aspx*, *Details.aspx.cs*, et *Details.aspx.designer.cs*. Lors de la conversion à Blazor, le code-derrière et le balisage sont combinés en *Details.razor*. La compilation Razor (équivalente à ce qu’il y a dans les fichiers *.designer.cs)* est stockée dans le répertoire *obj* et ne sont pas, par défaut, visible dans **Solution Explorer**. La page Formulaires Web se compose de la balisage suivante :

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

Le code de balisage précédent comprend le code suivant :

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

Lorsqu’elle est convertie en Blazor, la page Web Forms se traduit par le code suivant :

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

Notez que le code et le balisage sont dans le même fichier. Tous les services requis `@inject` sont rendus accessibles avec l’attribut. Selon `@page` la directive, cette page peut `Catalog/Details/{id}` être consultée à l’itinéraire. La valeur du propriétaire `{id}` de la place de l’itinéraire a été limitée à un intégriste. Tel que décrit dans la section [de routage,](pages-routing-layouts.md) contrairement aux formulaires Web, un composant Razor indique explicitement son itinéraire et tous les paramètres qui sont inclus. De nombreux contrôles sur les formulaires Web peuvent ne pas avoir de contreparties exactes à Blazor. Il ya souvent un extrait HTML équivalent qui servira le même but. Par exemple, `<asp:Label />` le contrôle peut `<label>` être remplacé par un élément HTML.

### <a name="model-validation-in-blazor"></a>Validation du modèle à Blazor

Si votre code Formulaires Web inclut la validation, vous pouvez transférer une grande partie de ce que vous avez avec peu ou pas de modifications. Un avantage à courir dans Blazor est que la même logique de validation peut être exécutée sans avoir besoin de JavaScript personnalisé. Les annotations de données permettent une validation facile du modèle.

Par exemple, la page *Create.aspx* a un formulaire de saisie de données avec validation. Un exemple d’extrait ressemblerait à ceci :

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

Dans Blazor, la majoration équivalente est fournie dans un fichier *Create.razor* :

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

Le `EditForm` contexte comprend un support de validation et peut être enroulé autour de l’entrée. Les annotations de données sont un moyen commun d’ajouter la validation. Un tel support de `DataAnnotationsValidator` validation peut être ajouté via le composant. Pour plus d’informations sur ce mécanisme, voir [ASP.NET formulaires Core Blazor et la validation](/aspnet/core/blazor/forms-validation).

## <a name="migrate-built-in-web-forms-controls"></a>Migrer les commandes intégrées des formulaires Web

*Ce contenu est à venir.*

## <a name="migrate-configuration"></a>Migrer une configuration

Dans un projet Web Forms, les données de configuration sont le plus souvent stockées dans le fichier *web.config.* Les données de configuration `ConfigurationManager`sont accessibles avec . Les services étaient souvent nécessaires pour analyser les objets. Avec .NET Framework 4.7.2, la composition `ConfigurationBuilders`a été ajoutée à la configuration via . Ces constructeurs ont permis aux développeurs d’ajouter diverses sources de configuration qui ont ensuite été composées au moment de l’exécution pour récupérer les valeurs nécessaires.

ASP.NET Core a introduit un système de configuration flexible qui vous permet de définir la source de configuration ou les sources utilisées par votre application et votre déploiement. L’infrastructure `ConfigurationBuilder` que vous utilisez peut-être dans votre application Web Forms a été calquée sur les concepts utilisés dans le système de configuration ASP.NET Core.

L’extrait suivant montre comment le projet Web Forms eShop utilise *web.config* pour stocker les valeurs de configuration :

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

Il est courant que les secrets, tels que les chaînes de connexion de base de données, soient stockés dans le *web.config*. Les secrets sont inévitablement persistants dans des endroits non sécurisés, tels que le contrôle des sources. Avec Blazor sur ASP.NET Core, la configuration XML précédente est remplacée par le JSON suivant :

```json
{
  "ConnectionStrings": {
    "CatalogDBContext": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb; Integrated Security=True; MultipleActiveResultSets=True;"
  },
  "UseMockData": true,
  "UseCustomizationData": false
}
```

JSON est le format de configuration par défaut; cependant, ASP.NET Core prend en charge de nombreux autres formats, y compris XML. Il existe également plusieurs formats soutenus par la communauté.

Le constructeur de la classe du `Startup` projet Blazor accepte une instance par le biais d’une `IConfiguration` technique DI connue sous le nom d’injection de constructeurs :

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

Par défaut, variables de l’environnement, fichiers JSON *(appsettings.json* et *appsettings. Les*options de ligne de commande et d’environnement sont enregistrées comme sources de configuration valides dans l’objet de configuration. Les sources de configuration `Configuration[key]`peuvent être consultées via . Une technique plus avancée consiste à lier les données de configuration aux objets utilisant le modèle d’options. Pour plus d’informations sur la configuration et le modèle d’options, voir [Configuration dans ASP.NET modèle de base](/aspnet/core/fundamentals/configuration/) et [d’options dans ASP.NET Core](/aspnet/core/fundamentals/configuration/options), respectivement.

## <a name="migrate-data-access"></a>Migrer l’accès aux données

L’accès aux données est un aspect important de toute application. Le projet eShop stocke les informations de catalogue dans une base de données et récupère les données avec Entity Framework (EF) 6. Étant donné que EF 6 est pris en charge dans .NET Core 3.0, le projet peut continuer à l’utiliser.

Les changements suivants liés à l’EF étaient nécessaires pour eShop :

- Dans .NET Framework, l’objet `DbContext` accepte une chaîne du nom de *formulaire-ConnectionString* et utilise la chaîne de connexion à partir de `ConfigurationManager.AppSettings[ConnectionString]` se connecter. Dans .NET Core, ce n’est pas pris en charge. La chaîne de connexion doit être fournie.
- La base de données a été consultée de façon synchrone. Bien que cela fonctionne, l’évolutivité peut en souffrir. Cette logique doit être déplacée à un modèle asynchrone.

Bien qu’il n’y ait pas le même support natif pour la liaison de dataset, Blazor fournit la flexibilité et la puissance avec son support C dans une page Razor. Par exemple, vous pouvez effectuer des calculs et afficher le résultat. Pour plus d’informations sur les modèles de données dans Blazor, consultez le chapitre [d’accès aux données.](data.md)

## <a name="architectural-changes"></a>Changements architecturaux

Enfin, il y a quelques différences architecturales importantes à considérer lors de la migration vers Blazor. Bon nombre de ces modifications s’appliquent à tout ce qui est basé sur .NET Core ou ASP.NET Core.

Parce que Blazor est construit sur .NET Core, il ya des considérations à assurer le soutien sur .NET Core. Voici quelques-uns des principaux changements:

- AppDomains multiples
- Communication à distance
- Sécurité d'accès du code
- Transparence de la sécurité

Pour plus d’informations sur les techniques pour identifier les changements nécessaires pour soutenir l’exécution sur .NET Core, voir [Port votre code de .NET Framework à .NET Core](/dotnet/core/porting).

ASP.NET Core est une version réinventée de ASP.NET et a quelques changements qui peuvent ne pas sembler évidents au départ. Les principaux changements sont les :

- Pas de contexte de synchronisation, ce `HttpContext.Current` `Thread.CurrentPrincipal`qui signifie qu’il n’y a pas, ou d’autres accesseurs statiques
- Pas de copie d’ombre
- Pas de file d’attente de demande

De nombreuses opérations dans ASP.NET Core sont asynchrones, ce qui permet un déchargement plus facile des tâches I/O-bound. Il est important de ne `Task.Wait()` `Task.GetResult()`jamais bloquer en utilisant ou , qui peut rapidement épuiser les ressources de piscine de fil.

## <a name="migration-conclusion"></a>Conclusion migratoire

À ce stade, vous avez vu de nombreux exemples de ce qu’il faut pour déplacer un projet Web Forms à Blazor. Pour un exemple complet, voir le projet [eShopOnBlazor.](https://github.com/dotnet-architecture/eShopOnBlazor)

>[!div class="step-by-step"]
>[Précédent](security-authentication-authorization.md)
