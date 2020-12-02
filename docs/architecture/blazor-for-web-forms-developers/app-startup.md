---
title: Démarrage des applications
description: Découvrez comment définir la logique de démarrage de votre application.
author: csharpfritz
ms.author: jefritz
ms.date: 11/20/2020
ms.openlocfilehash: d812079f84f67409334d07c4c10c5577446503be
ms.sourcegitcommit: 2f485e721f7f34b87856a51181b5b56624b31fd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "96509700"
---
# <a name="app-startup"></a>Démarrage des applications

Les applications écrites pour ASP.NET ont généralement un `global.asax.cs` fichier qui définit l' `Application_Start` événement qui contrôle quels services sont configurés et mis à disposition pour le rendu HTML et le traitement .net. Ce chapitre explique en quoi les choses sont légèrement différentes avec ASP.NET Core et le serveur éblouissant.

## <a name="application_start-and-web-forms"></a>Application_Start et Web Forms

La méthode Web Forms par défaut `Application_Start` a cessé de s’adapter à plusieurs années pour gérer de nombreuses tâches de configuration.  Un nouveau projet Web Forms avec le modèle par défaut dans Visual Studio 2019 contient désormais la logique de configuration suivante :

- `RouteConfig` -Routage des URL de l’application
- `BundleConfig` -CSS et regroupement JavaScript et minimisation

Chacun de ces fichiers se trouve dans le `App_Start` dossier et ne s’exécute qu’une seule fois au démarrage de notre application.  `RouteConfig` dans le modèle de projet par défaut, ajoute le `FriendlyUrlSettings` pour les Web Forms afin d’autoriser les URL d’application à omettre l' `.ASPX` extension de fichier.  Le modèle par défaut contient également une directive qui fournit des codes d’état de redirection HTTP permanents (HTTP 301) pour les `.ASPX` pages vers l’URL conviviale avec le nom de fichier qui omet l’extension.

Avec ASP.NET Core et éblouissant, ces méthodes sont soit simplifiées et consolidées dans la `Startup` classe, soit supprimées en faveur des technologies Web courantes.

## <a name="blazor-server-startup-structure"></a>Structure de démarrage du serveur éblouissant

Les applications serveur éblouissantes résident sur une version ASP.NET Core 3,0 ou ultérieure.  ASP.NET Core applications Web sont configurées à l’aide d’une paire de méthodes dans la `Startup.cs` classe sur le dossier racine de l’application.  Le contenu par défaut de la classe Startup est indiqué ci-dessous

```csharp
public class Startup
{
  public Startup(IConfiguration configuration)
  {
    Configuration = configuration;
  }

  public IConfiguration Configuration { get; }

  // This method gets called by the runtime. Use this method to add services to the container.
  // For more information on how to configure your application, visit https://go.microsoft.com/fwlink/?LinkID=398940
  public void ConfigureServices(IServiceCollection services)
  {
    services.AddRazorPages();
    services.AddServerSideBlazor();
    services.AddSingleton<WeatherForecastService>();
  }

  // This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
  public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
  {
    if (env.IsDevelopment())
    {
      app.UseDeveloperExceptionPage();
    }
    else
    {
      app.UseExceptionHandler("/Error");
      // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
      app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
      endpoints.MapBlazorHub();
      endpoints.MapFallbackToPage("/_Host");
   });
  }
 }
```

À l’instar du reste de ASP.NET Core, la classe Startup est créée avec des principes d’injection de dépendances.  Le `IConfiguration` est fourni au constructeur et est inclus dans une propriété publique pour un accès ultérieur pendant la configuration.

La `ConfigureServices` méthode introduite dans ASP.net Core permet de configurer les différents services d’infrastructure ASP.net Core pour le conteneur d’injection de dépendances intégré du Framework.  Les différentes `services.Add*` méthodes ajoutent des services qui activent des fonctionnalités telles que l’authentification, les pages Razor, le routage de contrôleur MVC, signalr et les interactions de serveurs éblouissantes entre autres.  Cette méthode n’était pas nécessaire dans Web Forms, car l’analyse et la gestion des fichiers ASPX, ASCX, ASHX et ASMX étaient définies en référençant ASP.NET dans le fichier de configuration web.config.  Vous trouverez plus d’informations sur l’injection de dépendances dans ASP.NET Core dans la [documentation en ligne](/aspnet/core/fundamentals/dependency-injection).

La `Configure` méthode introduit le concept de pipeline HTTP pour ASP.net core.  Dans cette méthode, nous déclarons de haut en bas l' [intergiciel](middleware.md) qui gère chaque demande envoyée à notre application. La plupart de ces fonctionnalités dans la configuration par défaut ont été disséminées dans les fichiers de configuration Web Forms et sont maintenant dans un emplacement unique pour faciliter la référence.

Ne correspond plus à la configuration de la page d’erreurs personnalisée placée dans un `web.config` fichier, mais elle est désormais configurée pour toujours s’afficher si l’environnement de l’application n’est pas étiqueté `Development` .  En outre, les applications ASP.NET Core sont désormais configurées pour traiter les pages sécurisées avec TLS par défaut avec l' `UseHttpsRedirection` appel de méthode.

Ensuite, une méthode de configuration inattendue est présentée à `UseStaticFiles` .  Dans ASP.NET Core, la prise en charge des demandes de fichiers statiques (tels que les fichiers JavaScript, CSS et image) doit être explicitement activée, et seuls les fichiers du dossier *wwwroot* de l’application sont adressables par défaut.

La ligne suivante est la première qui réplique l’une des options de configuration à partir de Web Forms : `UseRouting` .  Cette méthode ajoute le routeur ASP.NET Core au pipeline et peut être configurée ici ou dans les fichiers individuels sur lesquels le routage peut être envisagé.  Vous trouverez plus d’informations sur la configuration du routage dans la [section routage](pages-routing-layouts.md).

La dernière instruction de cette méthode définit les points de terminaison sur lesquels ASP.NET Core écoute.  Ces itinéraires sont les emplacements accessibles sur le Web auxquels vous pouvez accéder sur le serveur Web et qui reçoivent du contenu géré par .NET et qui vous sont renvoyés.  La première entrée `MapBlazorHub` configure un concentrateur signalr à utiliser pour fournir la connexion permanente et en temps réel au serveur sur lequel l’État et le rendu des composants éblouissants sont gérés.  L' `MapFallbackToPage` appel de méthode indique l’emplacement accessible via le Web de la page qui démarre l’application éblouissante et configure l’application pour gérer les demandes de liaison profonde du côté client.  Vous verrez cette fonctionnalité au travail si vous ouvrez un navigateur et accédez directement à l’itinéraire géré par éblouissant dans votre application, par exemple `/counter` dans le modèle de projet par défaut. La requête est gérée par la page de secours *_Host. cshtml* , qui exécute ensuite le routeur éblouissant et affiche la page de compteur.

## <a name="upgrading-the-bundleconfig-process"></a>Mise à niveau du processus BundleConfig

Les technologies de regroupement des ressources, telles que les feuilles de style CSS et les fichiers JavaScript, ont considérablement évolué, avec d’autres technologies fournissant des outils et des techniques en constante évolution pour la gestion de ces ressources.  À cette fin, nous vous recommandons d’utiliser un outil de ligne de commande de nœud tel que grunt/Gulp/WebPack pour empaqueter vos ressources statiques.

Les outils en ligne de commande Grunt, Gulp et WebPack et leurs configurations associées peuvent être ajoutés à votre application et ASP.NET Core ignore ces fichiers pendant le processus de génération de l’application.  Vous pouvez ajouter un appel pour exécuter leurs tâches en ajoutant un à `Target` l’intérieur de votre fichier projet avec une syntaxe similaire à celle qui déclencherait un script Gulp et la `min` cible à l’intérieur de ce script.

```xml
<Target Name="MyPreCompileTarget" BeforeTargets="Build">
  <Exec Command="gulp min" />
</Target>
```

Vous trouverez plus de détails sur les stratégies de gestion de vos fichiers CSS et JavaScript dans le [Bundle et les ressources statiques réduire dans ASP.net Core](/aspnet/core/client-side/bundling-and-minification) documentation.

>[!div class="step-by-step"]
>[Précédent](project-structure.md) 
> [Suivant](components.md)
