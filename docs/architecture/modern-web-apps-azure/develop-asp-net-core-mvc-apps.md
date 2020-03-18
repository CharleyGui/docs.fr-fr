---
title: Développement d’applications ASP.NET Core MVC
description: Architecturer des applications web modernes avec ASP.NET Core et Azure | Développement d’applications ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: a18b4dfc60c7d3971136f73f333b7225735710b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503946"
---
# <a name="develop-aspnet-core-mvc-apps"></a>Développer des applications ASP.NET Core MVC

> « Réussir du premier coup n’est pas le plus important. Ce qui compte, c’est le résultat final. »  
> _– Andrew Hunt et David Thomas_

ASP.NET Core est un framework open source multiplateforme qui permet de générer des applications web modernes optimisées pour le cloud. Légères et modulaires, les applications ASP.NET Core intègrent la prise en charge de l’injection de dépendances, améliorant ainsi la testabilité et la maintenabilité. Associé à MVC, qui prend en charge la génération d’API web modernes et d’applications basées sur les vues, ASP.NET Core est un framework puissant qui permet de générer des applications web d’entreprise.

## <a name="mvc-and-razor-pages"></a>MVC et pages Razor

ASP.NET Core MVC offre de nombreuses fonctionnalités qui sont utiles pour la création d’applications et d’API basées sur le web. Le terme MVC signifie « Model-View-Controller », un modèle d’interface utilisateur qui sépare en plusieurs parties les responsabilités relatives au fait de répondre aux demandes des utilisateurs. En plus de suivre ce modèle, vous pouvez également implémenter des fonctionnalités dans vos applications ASP.NET Core sous la forme de pages Razor. Les pages Razor sont intégrées à ASP.NET Core MVC, et utilisent les mêmes fonctionnalités pour le routage, la liaison de modèle, etc. Cependant, au lieu d’avoir des dossiers et des fichiers distincts pour les contrôleurs, les vues, etc. et d’utiliser le routage basé sur l’attribut, les pages Razor sont placées dans un seul dossier («/Pages»»), l’itinéraire en fonction de leur emplacement relatif dans ce dossier, et de traiter les demandes avec des gestionnaires au lieu d’actions de contrôleur.

Lorsque vous créez une nouvelle application ASP.NET Core, vous devez avoir un plan à l’esprit pour le type d’application que vous souhaitez générer. Dans Visual Studio, vous effectuez votre choix parmi plusieurs modèles. Les trois modèles de projet les plus courants sont API web, Application web et Application web (Model-View-Controller). Vous pouvez prendre cette décision seulement lorsque vous créez un projet, mais ce n’est pas une décision irrévocable. Le projet API web utilise des contrôleurs Model-View-Controller standard : il ne dispose pas de vues par défaut. De même, le modèle Application web par défaut utilise les pages Razor et ne dispose donc également pas d’un dossier de vues. Vous pouvez ajouter un dossier de vues à ces projets plus tard, pour prendre en charge le comportement basé sur les vues. Les projets API web et Model-View-Controller n’incluent pas de dossier de pages par défaut, mais vous pouvez en ajouter un plus tard pour prendre en charge le comportement basé sur les pages Razor. Vous pouvez considérer ces trois modèles comme prenant en charge trois différents types d’interactions utilisateur par défaut : données (API web), basées sur les pages et basées sur les vues. Toutefois, vous pouvez mélanger et traiter plusieurs ou tous les types d’interactions dans un seul projet si vous le souhaitez.

### <a name="why-razor-pages"></a>Pourquoi utiliser les pages Razor ?

Les pages Razor représentent l’approche par défaut pour les nouvelles applications web dans Visual Studio. Les pages Razor favorisent la création de fonctionnalités d’application basées sur les pages, comme les formulaires non monopages. En utilisant des contrôleurs et des vues, il était courant que des applications possèdent des contrôleurs de très grande taille qui fonctionnaient avec de nombreuses dépendances et modèles de vue différents et retournaient de nombreuses vues différentes. Il en est résulté une plus grande complexité et a souvent donné lieu à des contrôleurs qui n’ont pas suivi efficacement le principe de responsabilité unique ou les principes ouverts/fermés. Les pages Razor résolvent ce problème en encapsulant la logique côté serveur pour une « page » logique donnée dans une application web avec son balisage Razor. Une page Razor qui n’a pas de logique côté serveur peut être simplement constituée d’un fichier Razor (par exemple, « Index.cshtml »). Toutefois, la plupart des pages Razor non triviales ont une classe de modèle de page associée, qui, par convention, porte le même nom que le fichier Razor avec une extension « .cs » (par exemple, « Index.cshtml.cs »).

Le modèle de page d’une page Razor combine les responsabilités d’un contrôleur MVC et d’un objet viewmodel. Au lieu de traiter les demandes avec les méthodes d’action de contrôleur, les gestionnaires de modèle de page comme « OnGet() » sont exécutés, effectuant le rendu par défaut de leur page associée. Les pages Razor simplifient le processus de création des pages individuelles dans une application ASP.NET Core, tout en fournissant toutes les fonctionnalités architecturales d’ASP.NET Core MVC. Elles constituent un choix par défaut judicieux pour de nouvelles fonctionnalités basées sur les pages.

### <a name="when-to-use-mvc"></a>Quand utiliser MVC ?

Si vous créez des API web, il est plus judicieux d’utiliser le modèle MVC que les pages Razor. Si votre projet n’expose que les paramètres de l’API Web, vous devriez idéalement commencer à partir du modèle de projet Web API. Dans le cas contraire, il est facile d’ajouter des contrôleurs et des paramètres D’API associés à n’importe quelle application ASP.NET Core. Utilisez l’approche MVC basée sur l’vue si vous migrez une application existante à partir de ASP.NET MVC 5 ou plus tôt à ASP.NET Core MVC et vous souhaitez le faire avec le moins d’effort. Une fois que vous avez effectué la migration initiale, vous pouvez évaluer l’intérêt à adopter les pages Razor pour les nouvelles fonctionnalités ou même en tant que migration complète.

Que vous choisissiez de créer votre application Web à l’aide de Pages Razor ou de vues MVC, votre application aura des performances similaires et comprendra un support pour l’injection de dépendance, des filtres, la liaison de modèle, la validation, et ainsi de suite.

## <a name="mapping-requests-to-responses"></a>Mappage des requêtes aux réponses

À la base, les applications ASP.NET Core mappent les requêtes entrantes à des réponses sortantes. À bas niveau, cette opération est effectuée par un intergiciel (middleware). D’ailleurs, certains microservices et applications ASP.NET Core simples sont uniquement constitués de middlewares personnalisés. ASP.NET Core MVC vous permet de travailler à un niveau plus élevé et de réfléchir en termes _de routes_, _de contrôleurs_ et _d’actions_. Chaque requête entrante est comparée à la table de routage de l’application. Si une route correspondante est trouvée, la méthode d’action associée (appartenant à un contrôleur) est appelée pour traiter la requête. Si aucune route correspondante n’est trouvée, un gestionnaire d’erreurs (qui, dans ce cas, retourne un résultat NotFound) est appelé.

Les applications ASP.NET Core MVC peuvent utiliser des routes conventionnelles, des routes par attributs ou les deux. Les routes conventionnelles sont définies dans le code. Elles spécifient des _conventions_ de routage à l’aide d’une syntaxe semblable à celle de l’exemple ci-dessous :

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Dans cet exemple, une route nommée « default » a été ajoutée à la table de routage. Il définit un modèle d’itinéraire avec les placeholders pour _le contrôleur,_ _l’action,_ et _id_. Le contrôleur et les détenteurs de places d’action ont spécifié par défaut («Home» et «Index», respectivement), et le placeholder id est facultatif (en vertu d’un «?" appliqué à elle). Selon la convention définie ici, la première partie d’une requête doit correspondre au nom du contrôleur, la deuxième partie à l’action et la troisième partie, s’il y a lieu, à un paramètre id. Les routes conventionnelles sont généralement définies dans un seul emplacement pour l’application, par exemple dans la méthode Configure de la classe Startup.

Les routes par attributs ne sont pas spécifiées globalement. Au lieu de cela, elles sont appliquées directement aux contrôleurs et aux actions. L’avantage, c’est que ces routes sont plus facilement détectables quand vous examinez une méthode particulière. Mais cela signifie aussi que les informations de routage ne sont pas conservées au même endroit dans l’application. Avec les routes par attributs, vous pouvez facilement spécifier plusieurs routes pour une action donnée, mais aussi combiner des routes entre les contrôleurs et les actions. Par exemple :

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

Vous pouvez spécifier des routes [HttpGet] et des attributs similaires, ce qui vous évite de devoir ajouter des attributs [Route] distincts. Les routes par attributs peuvent également utiliser des jetons pour réduire la nécessité de répéter les noms de contrôleurs ou d’actions, comme indiqué ci-dessous :

```csharp
[Route("[controller]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

Les pages Razor n’utilisent pas le routage par attributs. Vous pouvez spécifier des informations de modèle de route supplémentaires pour une page Razor dans le cadre de sa directive `@page` :

```csharp
@page "{id:int}"
```

Dans l’exemple précédent, la page en question correspondrait à une route avec un paramètre `id` entier. Par exemple, la page *Products.cshtml* située à la racine de `/Pages` aurait cette route :

```csharp
"/Products/123"
```

Après la mise en correspondance d’une requête donnée avec une route, mais avant l’appel de la méthode d’action, ASP.NET Core MV procède à la [liaison de données](/aspnet/core/mvc/models/model-binding) et à la [validation du modèle](/aspnet/core/mvc/models/validation) sur la requête. La liaison de données convertit les données HTTP entrantes en types .NET (spécifiés comme paramètres de la méthode d’action à appeler). Par exemple, si la méthode d’action attend un paramètre id de type int, la liaison de données tente de fournir ce paramètre à partir d’une valeur fournie dans le cadre de la requête. Pour ce faire, la liaison de données recherche des valeurs dans un formulaire publié, dans la route elle-même et dans la chaîne de requête. Si une valeur id est trouvée, elle est convertie en entier avant d’être passée à la méthode d’action.

La validation du modèle se produit après la liaison de données, mais avant l’appel de la méthode d’action. À l’aide d’attributs facultatifs sur le type de modèle, la validation du modèle peut contribuer à assurer la conformité de l’objet modèle fourni à certaines exigences en matière de données. Certaines valeurs peuvent être spécifiées au besoin, ou limitées à une certaine longueur ou à une certaine plage numérique, etc. Si les attributs de validation sont spécifiés mais que le modèle n’est pas conforme à leurs exigences, la propriété ModelState.IsValid sera fausse, et l’ensemble des règles de validation défaillantes sera disponible pour envoyer au client qui fait la demande.

Si vous utilisez la validation du modèle, veillez à toujours vérifier que le modèle est valide avant d’exécuter des commandes de modification de l’état, et ce pour garantir que votre application n’est pas endommagée par des données non valides. Vous pouvez utiliser un [filtre](/aspnet/core/mvc/controllers/filters) pour ne pas avoir à ajouter du code dans chaque action. Les filtres ASP.NET Core MVC offrent un moyen d’intercepter des groupes de requêtes, ce qui permet d’appliquer des stratégies courantes et des problèmes transversaux de manière ciblée. Des filtres peuvent être appliqués à des actions individuelles, à des contrôleurs entiers ou à une application de manière globale.

Pour les API web, ASP.NET Core MVC prend en charge la [_négociation de contenu_](/aspnet/core/mvc/models/formatting), qui autorise les requêtes à spécifier le format des réponses. En fonction des en-têtes fournis dans la requête, les actions retournant des données appliquent à la réponse le format XML ou JSON ou un autre format pris en charge. Cette fonctionnalité permet à la même API d’être utilisée par plusieurs clients avec des exigences différentes en matière de format des données.

Les projets API web doivent envisager d’utiliser l’attribut `[ApiController]`, qui peut être appliqué à des contrôleurs individuels, à une classe de contrôleur de base ou à la totalité de l’assembly. Cet attribut ajoute la vérification automatique de la validation du modèle et toute action dotée d’un modèle non valide retourne une réponse BadRequest contenant les détails des erreurs de validation. Cet attribut exige également que toutes les actions aient une route d’attribut, au lieu d’utiliser une route conventionnelle, et retourne des informations ProblemDetails plus détaillées en réponse aux erreurs.

> ### <a name="references--mapping-requests-to-responses"></a>Références – Mappage des requêtes aux réponses
>
> - **Routage vers les actions de contrôleur**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Liaison de modèle**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding>
> - **Validation du modèle**
 > <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filtres**
 > <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **Attribut ApiController**
 > <https://docs.microsoft.com/aspnet/core/web-api/>

## <a name="working-with-dependencies"></a>Utilisation de dépendances

ASP.NET Core intègre la prise en charge d’une technique appelée « [injection de dépendances](/aspnet/core/fundamentals/dependency-injection) » qu’il utilise en interne. L’injection de dépendances est une technique qui autorise un couplage faible entre les différentes parties d’une application. Un couplage faible est un objectif souhaitable dans la mesure où il facilite l’isolation des parties d’une application à des fins de test ou de remplacement. Il réduit aussi le risque qu’un changement apporté à une partie de l’application ait un impact inattendu à un autre endroit de l’application. Basée sur le principe d’inversion de dépendances, l’injection de dépendances joue souvent un rôle clé dans la réalisation du principe ouvert/fermé. Quand vous évaluez le fonctionnement de votre application avec ses dépendances, prenez garde au « code smell » [Static Cling](https://deviq.com/static-cling/) (adhésion statique), et n’oubliez pas l’aphorisme « [New is Glue](https://ardalis.com/new-is-glue) » (couplage du code résultant de l’utilisation du mot clé new).

Le phénomène de « static cling » se produit quand vos classes appellent des méthodes statiques ou accèdent à des propriétés statiques qui ont des effets secondaires ou des dépendances sur l’infrastructure. Par exemple, si vous avez une méthode qui appelle une méthode statique qui à son tour écrit dans une base de données, votre méthode est alors étroitement couplée à la base de données. Tout problème interrompant cet appel de base de données arrête donc votre méthode. Les procédures à mettre en œuvre pour tester ces méthodes sont notoirement difficiles, car elles nécessitent des bibliothèques de simulation commerciale pour simuler les appels statiques ou la mise en place d’une base de données de test. Les appels statiques qui ne dépendent pas de l’infrastructure, en particulier ceux sans état, ne posent pas de problèmes et n’ont aucun impact sur le couplage ou la testabilité (au-delà du couplage du code à l’appel statique proprement dit).

Si les développeurs ont conscience des risques associés au « static cling » et à l’état global, bon nombre continuent de coupler étroitement leur code à des implémentations spécifiques par le biais d’instanciations directes. « New is Glue » est destiné à être un rappel de ce couplage, mais ne vise pas à condamner l’utilisation du mot clé `new`. Comme pour les appels de méthode statique, les nouvelles instances de types qui n’ont aucune dépendance externe n’entraînent généralement pas un couplage étroit du code aux détails d’implémentation et ne compliquent pas les tests. Mais chaque fois qu’une classe est instanciée, prenez un instant pour déterminer s’il convient de coder en dur cette instance spécifique à cet emplacement particulier ou s’il serait préférable de demander cette instance en tant que dépendance.

### <a name="declare-your-dependencies"></a>Déclarer vos dépendances

ASP.NET Core repose sur le fait que les méthodes et les classes déclarent leurs dépendances, celles-ci étant passées en tant qu’arguments. Les applications ASP.NET sont généralement configurées dans une classe Startup qui est elle-même configurée pour prendre en charge l’injection de dépendances à plusieurs points. Si votre classe Startup a un constructeur, elle peut demander des dépendances par le biais du constructeur, comme ceci :

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
            .SetBasePath(env.ContentRootPath)
            .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
            .AddJsonFile($"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

La classe Startup est intéressante dans la mesure où elle n’exige aucun type explicite. Elle n’hérite pas d’une classe de base Startup spéciale et n’implémente aucune interface particulière. Vous pouvez lui donner ou non un constructeur, et vous pouvez spécifier sur celui-ci autant de paramètres que vous le souhaitez. Quand l’hôte web que vous avez configuré pour votre application démarre, il appelle la classe Startup que vous avez spécifiée et utilise l’injection de dépendances pour remplir toutes les dépendances dont a besoin la classe Startup. Bien entendu, si vous demandez des paramètres qui ne sont pas configurés dans le conteneur de services utilisé par ASP.NET Core, une exception est générée. Mais tant que vous utilisez des dépendances connues du conteneur, vous pouvez demander ce que vous voulez.

L’injection de dépendances est intégrée à vos applications ASP.NET Core dès le départ, quand vous créez l’instance Startup. Mais la classe Startup va plus loin. Vous pouvez également demander des dépendances dans la méthode Configure :

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

La méthode ConfigureServices constitue l’exception à la règle puisqu’elle accepte un seul paramètre de type IServiceCollection. Elle n’a pas vraiment besoin de prendre en charge l’injection de dépendances, étant donné que, d’une part, elle est chargée d’ajouter des objets au conteneur de services et que, d’autre part, elle a accès à tous les services actuellement configurés par le biais du paramètre IServiceCollection. Vous pouvez donc utiliser les dépendances définies dans la collection de services ASP.NET Core dans chaque partie de la classe Startup : soit en demandant le service nécessaire comme paramètre, soit en utilisant le paramètre IServiceCollection dans ConfigureServices.

> [!NOTE]
> Si vous devez vous assurer que certains services sont disponibles pour votre classe Startup, vous pouvez les configurer à l’aide d’un IWebHostBuilder et de sa méthode ConfigureServices à l’intérieur de l’appel CreateDefaultBuilder.

La classe Startup est un modèle à suivre pour structurer d’autres parties de votre application ASP.NET Core, des contrôleurs aux middlewares en passant par les filtres et vos propres services. Dans chaque cas, vous devez respecter le [principe des dépendances explicites](https://deviq.com/explicit-dependencies-principle/), c’est-à-dire que vous devez demander vos dépendances au lieu de les créer directement et tirer parti de l’injection de dépendances dans toute votre application. L’endroit où vous instanciez directement des implémentations et la façon dont vous procédez doivent faire l’objet d’un examen attentif, surtout en ce qui concerne les services et objets qui utilisent l’infrastructure ou qui ont des effets secondaires. Utilisez des abstractions définies dans le noyau de votre l’application et passées en tant qu’arguments plutôt que de coder en dur des références à des types d’implémentation spécifiques.

## <a name="structuring-the-application"></a>Structuration de l’application

Les applications monolithiques ont généralement un point d’entrée unique. Dans le cas d’une application web ASP.NET Core, le point d’entrée est le projet web ASP.NET Core. Toutefois, cela ne veut pas dire que la solution doit se composer d’un projet unique. Il est utile de diviser l’application en plusieurs couches pour honorer la « séparation des préoccupations ». Une fois l’application divisée en couches, il est recommandé d’aller au-delà des dossiers pour séparer les projets et ainsi améliorer l’encapsulation. Pour atteindre ces objectifs avec une application ASP.NET Core, la meilleure approche consiste à utiliser une variante de l’architecture propre (« Clean Architecture ») décrite dans le chapitre 5. Selon cette approche, la solution de l’application est constituée de bibliothèques distinctes (UI, Infrastructure et ApplicationCore).

Des projets de test distincts sont également inclus (les tests sont décrits dans le chapitre 9).

Le modèle objet et les interfaces de l’application doivent être placés dans le projet ApplicationCore. Ce projet, dont le nombre de dépendances est réduit au minimum, est référencé par les autres projets dans la solution. Les entités métier qui doivent être persistantes sont définies dans le projet ApplicationCore, de même que les services qui ne dépendent pas directement de l’infrastructure.

Les détails de l’implémentation, notamment la façon dont la persistance est effectuée ou la manière dont les notifications peuvent être envoyées à un utilisateur, sont conservés dans le projet Infrastructure. Ce projet référence des packages spécifiques à l’implémentation comme Entity Framework Core, mais il ne doit pas exposer de détails sur ces implémentations en dehors du projet. Les référentiels et services d’infrastructure doivent implémenter les interfaces définies dans le projet ApplicationCore, et ses implémentations de persistance sont responsables de la récupération et du stockage des entités définies dans ApplicationCore.

Le projet d’interface utilisateur ASP.NET Core est responsable des problèmes d’interface utilisateur, mais il ne doit inclure ni logique métier ni détails d’infrastructure. En fait, dans l’idéal, il ne doit pas même pas dépendre du projet Infrastructure, et ce pour éviter qu’une dépendance entre les deux projets ne soit introduite accidentellement. Pour y parvenir, vous pouvez utiliser un conteneur d’injection de dépendances tiers comme Autofac. Celui-ci vous permet de définir des règles d’injection de dépendances dans les classes Module de chaque projet.

Une autre approche pour découpler l’application des détails d’implémentation consiste à configurer l’application de manière à ce qu’elle appelle des microservices (ceux-ci étant éventuellement déployés dans des conteneurs Docker individuels). Si les résultats en matière de séparation des préoccupations et de découplage sont encore meilleurs que ceux obtenus par l’injection de dépendances entre deux projets, le niveau de complexité est plus élevé.

### <a name="feature-organization"></a>Organisation par fonctionnalité

Par défaut, les applications ASP.NET Core organisent leur structure de dossiers de manière à inclure Controllers et Views, et couramment ViewModels. Le code côté client utilisé pour prendre en charge ces structures côté serveur est généralement stocké séparément dans le dossier wwwroot. Toutefois, cette organisation peut poser des problèmes pour les applications volumineuses dans la mesure où le développement d’une fonctionnalité donnée nécessite souvent de passer d’un dossier à un autre. Le niveau de complexité croît à mesure que le nombre de fichiers et de sous-dossiers dans chaque dossier augmente, occasionnant de nombreuses opérations de défilement dans l’Explorateur de solutions. Une solution à ce problème consiste à organiser le code de l’application par _fonctionnalité_ plutôt que par type de fichier. Ce style organisationnel est généralement appelé dossiers de fonctionnalités ou [tranches de fonctionnalité (voir](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc) aussi: Tranches [verticales](https://deviq.com/vertical-slices/)).

À cet effet, ASP.NET Core MVC prend en charge Areas. Les zones vous permettent de créer des jeux distincts de dossiers Controllers et Views (ainsi que tout modèle associé) dans chaque dossier Area. La Figure 7-1 montre un exemple de structure de dossiers avec Areas.

![Organisation de la zone d’échantillonnage](./media/image7-1.png)

**Figure 7-1**. Organisation de la zone d’échantillonnage

Quand vous utilisez Areas, vous devez utiliser des attributs pour décorer vos contrôleurs avec le nom de la zone à laquelle ils appartiennent :

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Vous devez également ajouter la prise en charge des zones à vos routes :

```csharp
app.UseEndpoints(endpoints =>
{
    endpoints.MapControllerRoute(name: "areaRoute", pattern: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
});
```

Outre la prise en charge intégrée d’Areas, vous pouvez utiliser votre propre structure de dossiers et des conventions à la place des attributs et des routes personnalisées. Vous pouvez ainsi avoir des dossiers de fonctionnalités sans dossiers distincts pour Views, Controllers, etc. La hiérarchie est donc plus plate, ce qui permet d’avoir tous les fichiers associés pour chaque fonctionnalité au même endroit.

ASP.NET Core utilise des types de convention intégrés pour contrôler son comportement. Vous pouvez modifier ou remplacer ces conventions. Par exemple, vous pouvez créer une convention qui obtient automatiquement le nom de la fonctionnalité pour un contrôleur donné en fonction de son espace de noms (qui correspond généralement au dossier dans lequel se trouve le contrôleur) :

```csharp
public class FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

Vous pouvez ensuite spécifier cette convention comme option quand vous ajoutez la prise en charge de MVC à votre application dans ConfigureServices :

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

ASP.NET Core MVC utilise également une convention pour localiser les vues. Vous pouvez la remplacer par une convention personnalisée de manière à ce que les vues soient établies dans les dossiers de fonctionnalité (en utilisant le nom de fonctionnalité fourni par FeatureConvention ci-dessus). Vous pouvez en savoir plus sur cette approche et télécharger un échantillon de travail de l’article MSDN Magazine, [Feature Slices for ASP.NET Core MVC](https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc).

### <a name="cross-cutting-concerns"></a>Problèmes transversaux

À mesure que les applications évoluent, il est important d’isoler les problèmes transversaux pour éliminer les doublons et assurer la cohérence. L’authentification, les règles de validation de modèle, la mise en cache de la sortie et la gestion des erreurs sont quelques exemples de problèmes transversaux. Les [filtres](/aspnet/core/mvc/controllers/filters) ASP.NET Core MVC vous permettent d’exécuter du code avant ou après certaines étapes du pipeline de traitement de requête. Par exemple, un filtre peut s’exécuter avant et après la liaison de données, avant et après une action, ou avant et après le résultat d’une action. Vous pouvez également utiliser un filtre d’autorisation pour contrôler l’accès au reste du pipeline. La Figure 7-2 montre le flux d’exécution de la requête à travers des filtres, s’ils sont configurés.

![La requête est traitée à travers les filtres d’autorisations, les filtres de ressources, la liaison de modèle, les filtres d’actions, l’exécution d’actions et la conversion des résultats d’actions, les filtres d’exceptions, les filtres de résultats et l’exécution de résultats. En sortie, la requête est traitée seulement par les filtres de résultats et les filtres de ressources avant de devenir une réponse envoyée au client.](./media/image7-2.png)

**Figure 7-2**. Demander l’exécution par filtres et demander le pipeline.

Les filtres sont généralement implémentés en tant qu’attributs, ce qui vous permet de les appliquer à des contrôleurs ou à des actions (voire globalement). Si vous les ajoutez de cette manière, les filtres spécifiés au niveau de l’action remplacent ou développent les filtres spécifiés au niveau du contrôleur, qui à leur tour remplacent les filtres globaux. Par exemple, l’attribut \[Route\] peut être utilisé pour générer des routes entre des contrôleurs et des actions. De même, l’autorisation peut être configurée au niveau du contrôleur, puis remplacée par des actions individuelles, comme dans l’exemple suivant :

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous] // overrides the Authorize attribute
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

La première méthode, Login, utilise le filtre AllowAnonymous (attribut) pour remplacer le filtre Authorize défini au niveau du contrôleur. L’action ForgotPassword (et toute autre action dans la classe sans attribut AllowAnonymous) nécessite une requête authentifiée.

Vous pouvez utiliser des filtres pour éliminer les doublons sous la forme de stratégies de gestion des erreurs pour les API. Ainsi, une stratégie d’API standard retourne une réponse NotFound aux requêtes référençant des clés qui n’existent pas et une réponse BadRequest en cas d’échec de la validation du modèle. L’exemple suivant illustre ces deux stratégies en action :

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Veillez à ce que vos méthodes d’action ne soient pas encombrées de code conditionnel comme celui-ci. Au lieu de cela, tirez (pull) les stratégies dans des filtres applicables au cas par cas. Dans cet exemple, la vérification de validation du modèle, qui doit se produire chaque fois qu’une commande est envoyée à l’API, peut être remplacée par l’attribut suivant :

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

Vous pouvez ajouter `ValidateModelAttribute` à votre projet en tant que dépendance NuGet en incluant le package [Ardalis.ValidateModel](https://www.nuget.org/packages/Ardalis.ValidateModel). Pour les API, vous pouvez utiliser l’attribut `ApiController` pour appliquer ce comportement sans avoir besoin d’un filtre `ValidateModel` distinct.

De même, vous pouvez utiliser un filtre pour vérifier si un enregistrement existe et retourner une erreur 404 avant l’exécution de l’action, éliminant ainsi la nécessité d’effectuer ces vérifications dans l’action. Après avoir retiré les conventions communes et organisé votre solution de manière à séparer le code d’infrastructure et la logique métier de votre interface utilisateur, vos méthodes d’action MVC doivent être extrêmement légères :

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Vous pouvez en savoir plus sur la mise en œuvre de filtres et télécharger un échantillon de travail de l’article msDN Magazine, [Real-World ASP.NET Core MVC Filters](https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters).

> ### <a name="references--structuring-applications"></a>Références – Structuration des applications
>
> - **Les zones (areas)**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN Magazine – Feature Slices for ASP.NET Core MVC**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/september/asp-net-core-feature-slices-for-asp-net-core-mvc>
> - **Filtres**  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN Magazine - Real World ASP.NET Core MVC Filters**  
>   <https://docs.microsoft.com/archive/msdn-magazine/2016/august/asp-net-core-real-world-asp-net-core-mvc-filters>

## <a name="security"></a>Sécurité

La sécurisation des applications web est un vaste sujet qui suscite de nombreuses questions. Au niveau de sécurité le plus élémentaire, vous devez savoir d’où provient une requête donnée et vérifier qu’elle a uniquement accès aux ressources appropriées. L’authentification est le processus qui consiste à comparer les informations d’identification fournies avec une requête à celles contenues dans un magasin de données approuvé pour savoir si la requête doit être traitée comme provenant d’une entité connue. L’autorisation est le processus qui consiste à limiter l’accès à certaines ressources en fonction de l’identité de l’utilisateur. Les écoutes clandestines effectuées par des tiers constituent un problème de sécurité. Pour protéger les requêtes, vous devez au moins [vérifier que votre application utilise le protocole SSL](/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Authentication

ASP.NET Core Identity est un système d’abonnement que vous pouvez utiliser pour prendre en charge la fonctionnalité de connexion pour votre application. Il prend en charge les comptes d’utilisateurs locaux et les fournisseurs de connexion externes : compte Microsoft, Twitter, Facebook, Google, etc. Outre ASP.NET Core Identity, votre application peut utiliser l’authentification Windows ou un fournisseur d’identité tiers comme [Identity Server](https://github.com/IdentityServer/IdentityServer4).

ASP.NET Core Identity est inclus dans les nouveaux modèles de projet si l’option Comptes d’utilisateur individuels est sélectionnée. Ce modèle inclut la prise en charge de l’inscription, de la connexion, des connexions externes et des mots de passe oubliés, ainsi que d’autres fonctionnalités.

![Sélectionnez des comptes utilisateur individuels pour avoir l’identité préconfigurée](./media/image7-3.png)

**Figure 7-3**. Sélectionnez des comptes utilisateur individuels pour avoir l’identité préconfigurée.

La prise en charge d’Identity est configurée dans Startup, à la fois dans ConfigureServices et dans Configure :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseEndpoints(endpoints =>
    {
        endpoints.MapControllerRoute(name: "default", pattern: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

UseIdentity doit impérativement apparaître avant UseMvc dans la méthode Configure. Quand vous configurez Identity dans ConfigureServices, notez l’existence d’un appel à AddDefaultTokenProviders. Cet appel n’a rien à voir avec les jetons qui peuvent être utilisés pour sécuriser les communications web. En fait, il fait référence aux fournisseurs qui créent des invites pouvant être envoyées aux utilisateurs par SMS ou e-mail pour qu’ils puissent confirmer leur identité.

Pour découvrir plus en détail [la configuration de l’authentification à deux facteurs](/aspnet/core/security/authentication/2fa) et [l’activation des fournisseurs de connexion externes](/aspnet/core/security/authentication/social/), consultez la documentation officielle d’ASP.NET Core.

### <a name="authorization"></a>Autorisation

La forme d’autorisation la plus simple consiste à restreindre l’accès aux utilisateurs anonymes. Pour cela, il vous suffit d’appliquer l’attribut \[Authorize\] à certains contrôleurs ou à certaines actions. Si des rôles sont utilisés, l’attribut peut être étendu de manière à restreindre l’accès aux utilisateurs appartenant à certains rôles, comme indiqué ici :

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

Dans ce cas, les utilisateurs qui appartiennent au rôle HRManager et/ou au rôle Finance ont accès à SalaryController. Pour exiger l’appartenance d’un utilisateur à plusieurs rôles (et non à un seul), vous pouvez appliquer l’attribut plusieurs fois en spécifiant un rôle obligatoire pour chaque instance.

Le fait de spécifier certains ensembles de rôles comme chaînes dans plusieurs contrôleurs et actions peut aboutir à des répétitions indésirables. Vous pouvez configurer des stratégies d’autorisation qui encapsulent des règles d’autorisation, puis spécifier la stratégie à la place de rôles individuels au moment de l’application de l’attribut \[Authorize\] :

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

En utilisant les stratégies de cette façon, vous pouvez séparer les types d’actions faisant l’objet de restrictions des rôles ou des règles spécifiques associés. Par la suite, si vous créez un rôle qui doit accéder à certaines ressources, vous pouvez simplement mettre à jour une stratégie plutôt que de mettre à jour chaque liste de rôles sur chaque attribut \[Authorize\].

#### <a name="claims"></a>Revendications

Les revendications sont des paires nom/valeur qui représentent les propriétés d’un utilisateur authentifié. Par exemple, vous pouvez stocker le matricule d’employé des utilisateurs comme revendication. Vous pouvez ensuite utiliser les revendications dans le cadre de stratégies d’autorisation. Vous pouvez créer une stratégie nommée « EmployeeOnly » qui exige l’existence d’une revendication appelée « EmployeeNumber », comme le montre l’exemple suivant :

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

Cette stratégie peut ensuite être utilisée avec l’attribut \[Authorize\] pour protéger un contrôleur et/ou une action quelconque, comme décrit ci-dessus.

#### <a name="securing-web-apis"></a>Sécurisation des API web

La plupart des API web doivent implémenter un système d’authentification par jeton. Sans état, l’authentification par jeton est conçue pour être scalable. Dans un système d’authentification par jeton, le client doit d’abord s’authentifier auprès du fournisseur d’authentification. En cas de réussite, le client reçoit un jeton qui est simplement une chaîne de caractères significative sur le plan du chiffrement. Quand le client doit par la suite émettre une requête à une API, il ajoute ce jeton comme en-tête de la requête. Le serveur valide alors le jeton trouvé dans l’en-tête de la requête avant de finaliser la requête. La Figure 7-4 illustre ce processus.

![TokenAuth](./media/image7-4.png)

**Figure 7-4.** Authentification par jeton pour les API web.

Vous pouvez créer votre propre service d’authentification, vous intégrer avec Azure AD et OAuth, ou implémenter un service à l’aide d’un outil open-source comme [IdentityServer](https://github.com/IdentityServer).

#### <a name="custom-security"></a>Sécurité personnalisée

Soyez particulièrement vigilant quant au « développement de votre propre » implémentation du chiffrement, de l’appartenance de l’utilisateur et du système de génération de jetons. Il existe de nombreuses alternatives commerciales et open source, qui présenteront certainement une meilleure sécurité qu’une implémentation personnalisée.

> ### <a name="references--security"></a>Références – Sécurité
>
> - **Vue d’ensemble des documents de sécurité**  
>   https://docs.microsoft.com/aspnet/core/security/
> - **Application de SSL dans une application ASP.NET Core**  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Présentation d’Identity**  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Présentation de l’autorisation**  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Authentification et autorisation pour API Apps dans Azure App Service**  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>
> - **IdentityServer**  
>   <https://github.com/IdentityServer>

## <a name="client-communication"></a>Communication avec les clients

Outre le fait de prendre en charge les pages et de répondre aux requêtes de données par le biais d’API web, les applications ASP.NET Core peuvent communiquer directement avec des clients connectés. Cette communication sortante peut faire appel à diverses technologies de transport, la plus courante étant WebSocket. ASP.NET Core SignalR est une bibliothèque qui facilite l’ajout à vos applications d’une fonctionnalité de communication en temps réel du serveur aux clients. SignalR prend en charge plusieurs technologies de transport, notamment WebSockets, et soustrait une grande partie des détails d’implémentation à la vue du développeur.

Qu’elle utilise WebSocket directement ou d’autres techniques, la communication en temps réel avec les clients est utile dans divers scénarios d’application. Voici quelques exemples :

- Applications de conversation en direct

- Applications de monitoring

- Mises à jour de la progression de travaux

- Notifications

- Applications de formulaires interactifs

L’intégration de la communication avec les clients dans vos applications fait généralement appel à deux composants :

- Gestionnaire de connexions côté serveur (SignalR Hub, WebSocketManager WebSocketHandler)

- Bibliothèque côté client

Les clients ne sont pas limités aux navigateurs : les applications mobiles, les applications console et d’autres applications natives peuvent aussi communiquer à l’aide de SignalR/WebSockets. Le programme élémentaire suivant transmet tout le contenu envoyé à une application de conversation à la console, dans le cadre d’un exemple d’application WebSocketManager :

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>
        {
            Console.WriteLine($"{arguments[0]} said: {arguments[1]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }

    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }

    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
}
```

Réfléchissez à la manière dont vos applications communiquent directement avec les applications clientes, et déterminez si la communication en temps réel peut améliorer l’expérience des utilisateurs de votre application.

> ### <a name="references--client-communication"></a>Références – Communication avec les clients
>
> - **ASP.NET Core SignalR**  
>   <https://github.com/dotnet/aspnetcore/tree/master/src/SignalR>
> - **WebSocket Manager**  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Utiliser la conception pilotée par le domaine ou non ?

La conception pilotée par le domaine (DDD, Domain-Driven Design) est une méthode agile de création de logiciels qui met l’accent sur le _domaine métier_. DDD insiste lourdement sur la communication et l’interaction avec un ou plusieurs experts du domaine métier capables de montrer aux développeurs ce qu’est le « monde réel ». Par exemple, si vous créez un système qui gère des transactions boursières, votre expert dans le domaine métier peut-être un courtier expérimenté. DDD est conçue pour résoudre des problèmes volumineux et complexes. En raison des investissements nécessaires en termes d’analyse et de modélisation du domaine, elle ne convient donc pas aux applications relativement simples et de petite taille.

Quand vous suivez une approche DDD pour développer des logiciels, les membres de votre équipe, y compris les contributeurs et les parties prenantes qui ne sont pas impliqués dans la partie technique, doivent développer un _langage omniprésent_ pour l’espace du problème. Autrement dit, vous devez employer la même terminologie pour le concept du monde réel à modéliser, son équivalent logiciel et toute structure permettant de rendre le concept persistant (comme des tables de base de données). Les concepts décrits dans le langage omniprésent doivent donc former la base de votre _modèle de domaine_.

Votre modèle de domaine se compose d’objets qui interagissent entre eux pour représenter le comportement du système. Ces objets peuvent appartenir aux catégories suivantes :

- [Entités](https://deviq.com/entity/) : les entités représentent des objets avec un thread d’identité. Elles sont généralement stockées de manière persistante avec une clé qui permet de les récupérer ultérieurement.

- [Agrégats](https://deviq.com/aggregate-pattern/) : les agrégats représentent des groupes d’objets qui doivent être rendus persistants en tant qu’unité.

- [Objets de valeur](https://deviq.com/value-object/) : les objets de valeur représentent des concepts qu’il est possible de comparer en fonction de la somme des valeurs de leurs propriétés. C’est le cas par exemple d’un DateRange comprenant une date de début et une date de fin.

- [Événements de domaine](https://martinfowler.com/eaaDev/DomainEvent.html) : ces événements se produisent au sein du système et présentent un intérêt pour d’autres parties du système.

Un modèle de domaine DDD doit encapsuler un comportement complexe dans le modèle. En particulier, les entités ne doivent pas simplement être des collections de propriétés. Si un modèle de domaine n’encapsule pas le comportement et qu’il représente simplement l’état du système, il est qualifié de « [modèle anémique](https://deviq.com/anemic-model/) ». Ce type de modèle n’est pas souhaitable dans DDD.

Outre ces types de modèles, DDD emploie généralement une variété de patrons :

- [Référentiel](https://deviq.com/repository-pattern/) : abstraction des détails de la persistance.

- [Fabrique](https://en.wikipedia.org/wiki/Factory_method_pattern) : encapsulation de la création d’objets complexes.

- Événements de domaine : découplage du comportement dépendant du comportement déclencheur.

- [Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/) : encapsulation de comportements complexes et/ou des détails d’implémentation de l’infrastructure.

- [Commande](https://en.wikipedia.org/wiki/Command_pattern) : découplage de l’émission et de l’exécution de commandes.

- [Spécification](https://deviq.com/specification-pattern/) : encapsulation des détails des requêtes.

DDD recommande également l’utilisation de l’architecture propre traitée précédemment. Celle-ci offre un couplage faible, l’encapsulation et la possibilité de vérifier facilement le code à l’aide de tests unitaires.

### <a name="when-should-you-apply-ddd"></a>Quand recourir à DDD ?

DDD est bien adapté aux grandes applications avec une complexité commerciale importante (pas seulement technique). La complexité de l’application est telle qu’elle nécessite les connaissances d’experts du domaine. Le modèle de domaine doit exhiber des comportements significatifs. Il doit notamment représenter les règles et les interactions de l’entreprise, et ne doit pas se limiter au stockage et à la récupération de l’état actuel de plusieurs enregistrements en provenance de magasins de données.

### <a name="when-shouldnt-you-apply-ddd"></a>Quand ne pas recourir à DDD ?

DDD nécessite des investissements dans les domaines de la modélisation, de l’architecture et des communications qui peuvent ne pas être justifiés pour des applications de petite taille ou celles offrant des fonctionnalités limitées : création, lecture, mise à jour et suppression (CRUD, Create/Read/Update/Delete). Si vous choisissez de développer votre application selon la méthode DDD, mais que vous réalisez que votre domaine a un modèle anémique sans comportement, il vous faudra peut-être repenser votre approche. Soit DDD n’est pas adapté à votre application, soit vous avez besoin d’aide pour refactoriser votre application et encapsuler la logique métier dans le modèle de domaine plutôt que dans votre base de données ou l’interface utilisateur.

Une approche hybride consiste à utiliser DDD pour les zones transactionnelles ou plus complexes de l’application, mais pas pour les parties plus simples (CRUD ou en lecture seule). Par exemple, vous n’avez pas besoin des contraintes d’un agrégat si vous interrogez des données pour afficher un rapport ou visualiser les données d’un tableau de bord. Il est parfaitement acceptable d’avoir un modèle de lecture distinct et plus simple pour de telles exigences.

> ### <a name="references--domain-driven-design"></a>Références – DDD
>
> - **DDD en langage clair (réponse StackOverflow)**  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Déploiement

Le processus de déploiement de votre application ASP.NET Core, quel que soit l’endroit où elle sera hébergée, comprend plusieurs étapes. La première étape consiste à publier l’application, qui peut être faite à l’aide de la `dotnet publish` commande CLI. Cette commande compile l’application et place tous les fichiers nécessaires à l’exécution de l’application dans un dossier désigné. Si vous déployez votre application à partir de Visual Studio, cette étape est automatique. Le dossier publish contient les fichiers .exe et .dll pour l’application et ses dépendances. Une application autonome inclut également une version du runtime .NET. Les applications ASP.NET Core comprennent aussi les fichiers de configuration, les ressources du client statiques et les vues MVC.

Les applications ASP.NET Core sont des applications console qui doivent être démarrées au moment du démarrage du serveur et redémarrés en cas de blocage de l’application (ou du serveur). Un gestionnaire de processus peut être utilisé pour automatiser ce processus. Les gestionnaires de processus les plus courants pour ASP.NET Core sont Nginx et Apache sur Linux et IIS ou Windows Service sur Windows.

En plus d’un gestionnaire de processus, ASP.NET applications Core peuvent utiliser un serveur proxy inversé. Un serveur proxy inverse reçoit des requêtes HTTP à partir d’Internet et les transfère à Kestrel après une gestion préliminaire. Les serveurs proxy inversés fournissent une couche de sécurité pour l’application. Kestrel ne prend pas non plus en charge l’hébergement de plusieurs applications sur le même port. Il est donc impossible d’utiliser certaines techniques comme les en-têtes d’hôte avec Kestrel pour héberger plusieurs applications sur le même port et la même adresse IP.

![Kestrel à Internet](./media/image7-5.png)

**Figure 7-5**. ASP.NET hébergée à Kestrel derrière un serveur proxy inversé

Un proxy inverse peut également être utile pour sécuriser plusieurs applications avec SSL/HTTPS. Dans ce cas, SSL ne doit être configuré que sur le proxy inverse. Les communications entre le serveur proxy inverse et Kestrel peuvent avoir lieu sur TTP, comme indiqué dans la Figure 7-6.

![ASP.NET hébergés derrière un serveur proxy inversé sécurisé par HTTPS](./media/image7-6.png)

**Figure 7-6**. ASP.NET hébergés derrière un serveur proxy inversé sécurisé par HTTPS

Une approche de plus en plus répandue consiste à héberger votre application ASP.NET Core dans un conteneur Docker que vous pouvez ensuite héberger localement ou déployer sur Azure pour l’héberger dans le cloud. Le conteneur Docker contient le code de votre application, exécuté sur Kestrel, et est déployé derrière un serveur proxy inverse, comme indiqué ci-dessus.

Si vous hébergez votre application sur Azure, vous pouvez utiliser Microsoft Azure Application Gateway comme appliance virtuelle dédiée pour fournir plusieurs services. Outre son rôle de proxy inverse pour des applications individuelles, Application Gateway offre également les fonctionnalités suivantes :

- Équilibrage de charge HTTP

- Déchargement SSL (SSL uniquement à Internet)

- SSL de bout en bout

- Routage multisite (consolidation de 20 sites au maximum sur une seule passerelle d’application)

- Pare-feu d’application web

- Prise en charge de WebSocket

- Diagnostics avancés

_En savoir plus sur les options de déploiement Azure dans [le chapitre 10](development-process-for-azure.md)._

> ### <a name="references--deployment"></a>Références – Déploiement
>
> - **Vue d’ensemble de l’hébergement et du déploiement**  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Quand utiliser Kestrel avec un proxy inverse**  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Héberger des applications ASP.NET Core dans Docker**  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Présentation d’Azure Application Gateway**  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
>[Suivant précédent](common-client-side-web-technologies.md)
>[Next](work-with-data-in-asp-net-core-apps.md)
