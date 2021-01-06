---
title: Présentation et présentation de .NET
description: Découvrez .NET, une plateforme de développement Open source gratuite pour créer de nombreux types d’applications.
author: tdykstra
ms.date: 11/16/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 0adc348c1fc340fe481d9987cdbe28c6cf8b065d
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938674"
---
# <a name="introduction-to-net"></a>Introduction à .NET

.NET est une plateforme de développement Open source gratuite pour la création de nombreux types d’applications, telles que :

* [Applications Web, API Web et microservices](/aspnet/core/introduction-to-aspnet-core#recommended-learning-path)
* [Fonctions sans serveur dans le Cloud](/azure/azure-functions/functions-create-first-function-vs-code?pivots=programming-language-csharp)
* [Applications cloud natives](../architecture/cloud-native/index.md)
* [Applications mobiles](https://dotnet.microsoft.com/learn/xamarin/hello-world-tutorial/intro)
* Applications de bureau
  * [WPF Windows](/dotnet/desktop/wpf/)
  * [Windows Forms](/dotnet/desktop/winforms/)
  * [Plateforme Windows universelle (UWP)](/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
* [Joueur](https://dotnet.microsoft.com/apps/games)
* [Internet des objets (IoT)](/dotnet/iot)
* [Machine Learning](../machine-learning/index.yml)
* [Applications de console](tutorials/with-visual-studio-code.md)
* [Services Windows](/aspnet/core/host-and-deploy/windows-service)

Partager des fonctionnalités entre différentes applications et types d’applications à l’aide de [bibliothèques de classes](../standard/class-libraries.md).

Avec .NET, les fichiers de votre code et de vos projets sont les mêmes, quel que soit le type d’application que vous créez. Vous avez accès aux mêmes fonctionnalités de Runtime, d’API et de langage avec chaque application.

## <a name="cross-platform"></a>Multiplateforme

Vous pouvez créer des applications .NET pour de nombreux systèmes d’exploitation, notamment :

* Windows
* macOS
* Linux
* Android
* iOS
* tvOS
* watchOS

Les architectures de processeur prises en charge sont les suivantes :

* x64
* x86
* ARM32
* ARM64

.NET vous permet d’utiliser des fonctionnalités propres à la plateforme, telles que les API du système d’exploitation. Les exemples sont Windows Forms et WPF sur Windows, ainsi que les liaisons natives à chaque plateforme mobile à partir de Xamarin.

Pour plus d’informations, consultez [stratégie de cycle de vie du système d’exploitation](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md) et [catalogue RID .net](rid-catalog.md)pris en charge.

## <a name="open-source"></a>Open source

.NET est open source et utilise [des licences mit et Apache 2](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT). .NET est un projet de [.net Foundation](https://dotnetfoundation.org/).

Pour plus d’informations, consultez la [liste des dépôts de projet sur GitHub.com](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).

## <a name="support"></a>Support

.NET est pris en charge par Microsoft sur Windows, macOS et Linux. Il est régulièrement mis à jour pour la sécurité et la qualité, le deuxième mardi de chaque mois.

Les distributions binaires .NET de Microsoft sont générées et testées sur des serveurs gérés par Microsoft dans Azure et suivent les pratiques d’ingénierie et de sécurité de Microsoft.

[Red Hat prend en charge .net](https://developers.redhat.com/topics/dotnet/) sur Red Hat Enterprise Linux (RHEL). Red Hat et Microsoft collaborent pour s’assurer que .NET Core fonctionne correctement sur RHEL.

[Tizen prend en charge .net](https://developer.tizen.org/development/training/.net-application) sur les plateformes Tizen.

Pour plus d’informations, consultez [Releases and support for .net Core and .net 5](releases-and-support.md).

## <a name="tools-and-productivity"></a>Outils et productivité

.NET vous offre le choix entre les langages, les environnements de développement intégré (IDE) et d’autres outils.

### <a name="programming-languages"></a>Langages de programmation

.NET prend en charge trois langages de programmation :

* [C#](../csharp/index.yml)

  C# (prononcé « voir Sharp ») est un langage de programmation moderne, orienté objet et de type sécurisé. C# prend sa source dans la famille de langages C et sera immédiatement reconnaissable aux programmeurs en C, C++, Java et JavaScript.

* [F#](../fsharp/index.yml)

  Le langage F # prend en charge les modèles de programmation fonctionnel, orienté objet et impératif.

* [Visual Basic](../visual-basic/index.yml)

  Dans les langages .NET, la syntaxe de Visual Basic est la plus proche du langage humain ordinaire, ce qui peut faciliter son apprentissage. Contrairement à C# et F #, pour lesquels Microsoft développe activement de nouvelles fonctionnalités, le langage de Visual Basic est stable. Visual Basic n’est pas pris en charge pour les applications Web, mais il est pris en charge pour les API Web.

Voici quelques-unes des fonctionnalités prises en charge par les langages .NET :

* [Cohérence des types](../standard/base-types/common-type-system.md)
* Inférence de type- [C#](../csharp/programming-guide/types/index.md#specifying-types-in-variable-declarations), [F #](../fsharp/language-reference/type-inference.md), [Visual Basic](../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
* [Types génériques](../standard/generics.md)
* [Délégués](../standard/delegates-lambdas.md)
* [Lambdas](../standard/delegates-lambdas.md)
* [Événements](../standard/events/index.md)
* [Exceptions](../standard/exceptions/index.md)
* [Attributs](../standard/attributes/index.md)
* [Code asynchrone](../standard/async.md)
* [Programmation parallèle](../standard/parallel-programming/index.md)
* [Analyseurs de code](../fundamentals/code-analysis/overview.md)

### <a name="ides"></a>IDE

Les environnements de développement intégrés pour .NET incluent :

* [Visual Studio](https://visualstudio.microsoft.com/vs/)

  S’exécute sur Windows uniquement. A des fonctionnalités intégrées étendues conçues pour fonctionner avec .NET. L’édition Community est gratuite pour les étudiants, les contributeurs Open source et les individus.

* [Visual Studio Code](https://code.visualstudio.com/)

  S’exécute sur Windows, macOS et Linux. Gratuit et open source. Les extensions sont disponibles pour l’utilisation des langages .NET.

* [Visual Studio pour Mac](https://visualstudio.microsoft.com/vs/mac/)

  S’exécute sur macOS uniquement. Pour le développement d’applications et de jeux .NET pour iOS, Android et Web.

* [GitHub Codespaces](https://github.com/features/codespaces)

  Un environnement de Visual Studio Code en ligne, actuellement en version bêta.

### <a name="sdk-and-runtimes"></a>SDK et runtimes

Le [Kit de développement logiciel (SDK) .net](sdk.md) est un ensemble de bibliothèques et d’outils permettant de développer et d’exécuter des applications .net.

Lorsque vous [Téléchargez .net](https://dotnet.microsoft.com/download/dotnet-core/), vous pouvez choisir le kit de développement logiciel (SDK) ou un *Runtime*, tel que le Runtime .net ou le runtime ASP.net core. Installez un Runtime sur un ordinateur que vous souhaitez préparer pour l’exécution des applications .NET. Installez le kit de développement logiciel (SDK) sur un ordinateur que vous souhaitez utiliser pour le développement. Lorsque vous téléchargez le kit de développement logiciel (SDK), vous en recevez automatiquement les runtimes.

Le téléchargement du kit de développement logiciel (SDK) comprend les composants suivants :

* [Interface CLI .net](tools/index.md). Outils en ligne de commande que vous pouvez utiliser pour le développement local et les scripts d’intégration continue.
* `dotnet` [Pilote](tools/index.md#driver). Commande CLI qui exécute des applications dépendantes du Framework.
* Compilateurs de langage de programmation [Roslyn](https://github.com/dotnet/roslyn) et [F #](https://github.com/microsoft/visualfsharp) .
* Moteur de génération [MSBuild](/visualstudio/msbuild/msbuild) .
* Le [Runtime .net](#clr). Fournit un système de type, un chargement d’assembly, un récupérateur de mémoire, une interopérabilité native et d’autres services de base.
* [Bibliothèques Runtime](#runtime-libraries). Fournit des types de données primitifs et des utilitaires fondamentaux.
* Runtime ASP.NET Core. Fournit des services de base pour les applications connectées à Internet, telles que les applications Web, les applications IoT et les backends mobiles.
* Le runtime Desktop. Fournit des services de base pour les applications de bureau Windows, y compris Windows Forms et WPF.

Le téléchargement du runtime comprend les composants suivants :

* Éventuellement, le bureau ou le runtime ASP.NET Core.
* Le [Runtime .net](#clr). Fournit un système de type, un chargement d’assembly, un récupérateur de mémoire, une interopérabilité native et d’autres services de base.
* [Bibliothèques Runtime](#runtime-libraries). Fournit des types de données primitifs et des utilitaires fondamentaux.
* `dotnet` [Pilote](tools/index.md#driver). Commande CLI qui exécute des applications dépendantes du Framework.

Pour plus d’informations, consultez les ressources suivantes :

* [Vue d’ensemble du SDK .NET](sdk.md)
* [Vue d’ensemble de l’interface CLI .NET](tools/index.md)
* [Commande dotnet](tools/dotnet.md)

### <a name="project-system-and-msbuild"></a>Système de projet et MSBuild

Une application .NET est générée à partir du code source à l’aide de [MSBuild](/visualstudio/msbuild/msbuild). Un fichier projet (*. csproj*, *. fsproj* ou *. vbproj*) spécifie des [cibles](/visualstudio/msbuild/msbuild-targets) et des [tâches](/visualstudio/msbuild/msbuild-tasks) associées qui sont responsables de la compilation, de l’empaquetage et de la publication du code. Il existe des identificateurs de kit de développement logiciel (SDK) qui font référence aux collections standard de cibles et de tâches. L’utilisation de ces identificateurs permet de réduire la taille des fichiers projet et de les utiliser facilement. Par exemple, voici un fichier projet pour une application console :

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

Et voici un exemple pour une application Web :

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>
    <TargetFramework>net5.0</TargetFramework>
  </PropertyGroup>
</Project>
```

Dans ces exemples, l' `Sdk` attribut de l' `Project` élément spécifie un ensemble de cibles et de tâches MSBuild qui génèrent le projet.  L' `TargetFramework` élément spécifie la version .net dont dépend l’application. Vous pouvez modifier le fichier projet pour ajouter des cibles et des tâches spécifiques au projet.

Pour plus d’informations, consultez [vue d’ensemble du kit de développement logiciel (SDK) de projet .net](project-sdk/overview.md) et [frameworks cibles](../standard/frameworks.md).

### <a name="cicd"></a>CI/CD

MSBuild et l’interface CLI .NET peuvent être utilisés avec différents environnements et outils d’intégration continue, tels que :

* [Actions GitHub](https://github.com/features/actions)
* [Azure DevOps](/azure/devops/user-guide/what-is-azure-devops)
* [GÂTEAUX](https://cakebuild.net/)
* [CONTREFAIT](https://fake.build/)

Pour plus d’informations, consultez [utilisation du kit de développement logiciel (SDK) et des outils .net dans l’intégration continue (ci)](tools/using-ci-with-cli.md) .

### <a name="nuget"></a>NuGet

[NuGet](/nuget/what-is-nuget) est un gestionnaire de package open source conçu pour .net. Un package NuGet est un fichier *. zip* avec l' `.nupkg` extension qui contient le code compilé (dll), les autres fichiers associés à ce code et un manifeste descriptif qui inclut des informations telles que le numéro de version du package. Les développeurs disposant de code pour partager des packages de création et les publier sur [NuGet.org](https://nuget.org) ou sur un hôte privé. Les développeurs qui souhaitent utiliser du code partagé ajoutent un package à leur projet et peuvent ensuite appeler l’API exposée par le package dans le code de leur projet.

Pour plus d’informations, consultez [la documentation NuGet](/nuget/).

### <a name="net-interactive"></a>.NET interactif

.NET interactive est un groupe d’outils CLI et d’API qui permettent aux utilisateurs de créer des expériences interactives sur le Web, la démarque et les blocs-notes.

Pour plus d’informations, consultez les ressources suivantes :

* [Didacticiel de In-Browser .NET](https://dotnet.microsoft.com/learn/dotnet/in-browser-tutorial/1)
* [Utilisation de blocs-notes .NET avec Jupyter sur votre ordinateur](https://github.com/dotnet/interactive/blob/main/docs/NotebooksLocalExperience.md)
* [Documentation interactive .NET](https://github.com/dotnet/interactive/blob/main/docs/README.md)

## <a name="execution-models"></a>Modèles d’exécution

Les applications .NET exécutent du [code managé](../standard/managed-code.md) dans un environnement d’exécution connu sous le nom de Common Language Runtime (CLR).

### <a name="clr"></a>CLR

Le [CLR](../standard/clr.md) .net est un Runtime multiplateforme qui prend en charge Windows, MacOS et Linux. Le CLR gère l’allocation et la gestion de la mémoire. Le CLR est également un ordinateur virtuel qui exécute des applications, mais génère et compile également du code à l’aide d’un compilateur juste-à-temps (JIT).

Pour plus d’informations, consultez [vue d’ensemble du CLR (Common Language Runtime)](../standard/clr.md).

### <a name="jit-compiler-and-il"></a>Compilateur JIT et IL

Les langages .NET de haut niveau, tels que C#, se compilent en un jeu d’instructions indépendant du matériel, qui est appelé Langage intermédiaire (IL). Quand une application s’exécute, le compilateur JIT traduit le langage intermédiaire en code machine compréhensible par le processeur. La compilation JIT se produit sur l’ordinateur sur lequel le code va s’exécuter.

Dans la mesure où la compilation JIT se produit pendant l’exécution de l’application, la durée de compilation fait partie du temps d’exécution. Par conséquent, les compilateurs JIT doivent équilibrer le temps passé à optimiser le code par rapport aux économies que le code résultant peut produire. Toutefois, un compilateur JIT connaît le matériel réel et peut permettre aux développeurs d’avoir à fournir des implémentations différentes pour différentes plateformes.

Le compilateur JIT .NET peut effectuer une *compilation hiérarchisée*, ce qui signifie qu’il peut recompiler des méthodes individuelles au moment de l’exécution. Cette fonctionnalité permet au service informatique de se compiler rapidement, tout en étant en mesure de générer une version hautement optimisée du code pour les méthodes fréquemment utilisées.

Pour plus d’informations, consultez [processus d’exécution managée](../standard/managed-execution-process.md) et [compilation à plusieurs niveaux](whats-new/dotnet-core-3-0.md#tiered-compilation).

### <a name="aot-compiler"></a>Compilateur AOA

L’expérience par défaut pour la plupart des charges de travail .NET est le compilateur JIT, mais .NET offre deux formes de compilation de l’AOA (avance à temps) :

* Certains scénarios nécessitent une compilation AOA de 100%. [IOS](/xamarin/ios/)en est un exemple.
* Dans d’autres scénarios, la majeure partie du code d’une application est compilée par l’AOA, mais certaines sont compilées juste-à-temps. Certains modèles de code ne sont pas compatibles avec l’AOA (comme les génériques). L’option de publication [prête à l’emploi](whats-new/dotnet-core-3-0.md#readytorun-images) est un exemple de cette forme de compilation AOA. Cette forme d’AOA offre les avantages de l’AOA sans ses inconvénients.

### <a name="automatic-memory-management"></a>Gestion automatique de la mémoire

Le *garbage collector* (GC) gère l’allocation et la libération de mémoire pour les applications. Chaque fois que votre code crée un nouvel objet, le CLR alloue de la mémoire pour l’objet à partir du [tas managé](../standard/garbage-collection/fundamentals.md#the-managed-heap). Aussi longtemps que de l'espace d'adressage est disponible dans le tas managé, le Runtime continue à allouer de l'espace pour de nouveaux objets. Lorsque l’espace d’adressage libre est insuffisant, le garbage collector recherche les objets du tas managé qui ne sont plus utilisés par l’application. Il récupère ensuite cette mémoire.

Le GC est l’un des services CLR qui permettent de garantir la sécurité de la *mémoire*. Un programme est sûr du point de vue de la mémoire s’il accède uniquement à la mémoire allouée. Par exemple, le runtime garantit qu’une application n’accède pas à la mémoire non allouée au-delà des limites d’un tableau.

Pour plus d’informations, consultez [gestion automatique](../standard/automatic-memory-management.md) de la mémoire et [notions de base des garbage collection](../standard/garbage-collection/fundamentals.md).

### <a name="working-with-unmanaged-resources"></a>Utilisation des ressources non managées

Parfois, le code doit référencer des *ressources non managées*. Les ressources non managées sont des ressources qui ne sont pas automatiquement gérées par le runtime .NET. Par exemple, un handle de fichier est une ressource non managée. Un objet <xref:System.IO.FileStream> est un objet managé, mais il fait référence à un handle de fichier qui ne l’est pas. Lorsque vous avez terminé d’utiliser l' <xref:System.IO.FileStream> , vous devez libérer explicitement le descripteur de fichier.

Dans .NET, les objets qui font référence à des ressources non managées implémentent l’interface <xref:System.IDisposable>. Quand vous avez fini d’utiliser l’objet, vous appelez la méthode <xref:System.IDisposable.Dispose> de l’objet qui est chargée de libérer les ressources non managées. Les langages .NET fournissent une `using` instruction pratique ([C#](../csharp/language-reference/keywords/using.md), [F #](../fsharp/language-reference/resource-management-the-use-keyword.md), [VB](../visual-basic/language-reference/statements/using-statement.md)) qui garantit que la `Dispose` méthode est appelée.

Pour plus d’informations, consultez [nettoyage des ressources non managées](../standard/garbage-collection/unmanaged.md).

## <a name="deployment-models"></a>Modèles de déploiement

Les applications .NET peuvent être publiées dans deux modes différents :

* La publication d’une application comme *autonome* produit un fichier exécutable qui comprend le [Runtime](#sdk-and-runtimes) .net et les [bibliothèques](#runtime-libraries), ainsi que l’application et ses dépendances. Les utilisateurs de l’application peuvent l’exécuter sur un ordinateur sur lequel le Runtime .NET n’est pas installé. Les applications autonomes sont spécifiques à la plateforme et peuvent éventuellement être publiées à l’aide d’une forme de [compilation AOA](#aot-compiler).

* La publication d’une application en tant que *dépendant du Framework* produit un fichier exécutable et des fichiers binaires (fichiers *. dll* ) qui incluent uniquement l’application elle-même et ses dépendances. Les utilisateurs de l’application doivent installer séparément le [Runtime](#sdk-and-runtimes).net. Le fichier exécutable est spécifique à la plateforme, mais les fichiers *. dll* des applications dépendantes du Framework sont multiplateformes.

  Vous pouvez installer plusieurs versions du runtime côte à côte pour exécuter des applications dépendantes du Framework qui ciblent différentes versions du Runtime. Pour plus d’informations, consultez [frameworks cibles](../standard/frameworks.md).

Les exécutables sont générés pour des plateformes cibles spécifiques, que vous spécifiez avec un [identificateur de Runtime (RID)](rid-catalog.md).

Pour plus d’informations, consultez [vue d’ensemble de la publication d’applications .net](deploying/index.md) et [Présentation de .net et de l’arrimeur](docker/introduction.md).

## <a name="runtime-libraries"></a>Bibliothèques Runtime

.NET possède un ensemble standard de bibliothèques de classes, connu sous le nom de [bibliothèques Runtime](../standard/glossary.md#runtime), de [bibliothèques d’infrastructure](../standard/glossary.md#framework-libraries)ou de la [bibliothèque de classes de base (BCL)](../standard/glossary.md#bcl). Ces bibliothèques fournissent des implémentations pour de nombreux types et fonctionnalités d’utilitaire à usage général et spécifiques à la charge de travail.

Voici quelques exemples de types définis dans les bibliothèques Runtime .NET :

* Types primitifs, tels que <xref:System.Boolean?displayProperty=nameWithType> et <xref:System.Int32?displayProperty=nameWithType> .
* Collections, comme <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> et <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
* Types de données, tels que <xref:System.Data.DataSet?displayProperty=nameWithType> et <xref:System.Data.DataTable?displayProperty=nameWithType> .
* Types d’utilitaire réseau, tels que <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> .
* Types d’utilitaire d' [e/s de fichier et de flux](../standard/io/index.md) , tels que <xref:System.IO.FileStream?displayProperty=nameWithType> et <xref:System.IO.TextWriter?displayProperty=nameWithType> .
* Types d’utilitaire de [sérialisation](../standard/serialization/index.md) , tels que <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> et <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> .
* Types hautes performances, tels que les <xref:System.Span%601?displayProperty=nameWithType> <xref:System.Numerics.Vector?displayProperty=nameWithType> [pipelines](../standard/io/pipelines.md), et.

Pour plus d’informations, consultez la [vue d’ensemble des bibliothèques Runtime](../standard/runtime-libraries-overview.md). Le code source des bibliothèques se trouve dans [le référentiel GitHub dotnet/Runtime](https://github.com/dotnet/runtime/tree/master/src/libraries).

### <a name="extensions-to-the-runtime-libraries"></a>Extensions des bibliothèques Runtime

Les bibliothèques pour certaines fonctionnalités d’application couramment utilisées ne sont pas incluses dans les bibliothèques Runtime, mais sont disponibles dans les packages NuGet, comme suit :

| Package NuGet | Documentation |
|---------|---------|
| [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) | [Gestion de la durée de vie des applications (hôte générique)](extensions/generic-host.md) |
| [Microsoft. extensions. DependencyInjection](https://www.nuget.org/packages/Microsoft.Extensions.DependencyInjection) | [Injection de dépendances (DI)](extensions/dependency-injection.md)
| [Microsoft.Extensions.Configuration](https://www.nuget.org/packages/Microsoft.Extensions.Configuration) | [Configuration](extensions/configuration.md) |
| [Microsoft.Extensions.Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) | [Journalisation](extensions/logging.md) |
| [Microsoft. extensions. options](https://www.nuget.org/packages/Microsoft.Extensions.Options) | [Modèle d’options](extensions/options.md) |

Pour plus d’informations, consultez le [référentiel dotnet/extensions sur GitHub](https://github.com/dotnet/extensions).

## <a name="data-access"></a>Accès aux données

.NET fournit un mappeur objet/relationnel (ORM) et un moyen d’écrire des requêtes SQL dans le code.

### <a name="entity-framework-core"></a>Entity Framework Core

Entity Framework (EF) Core est une technologie d’accès aux données [Open source](https://github.com/aspnet/EntityFrameworkCore) et multiplateforme qui peut servir d’ORM. EF Core vous permet d’utiliser une base de données en faisant référence à des objets .NET dans le code. Elle réduit la quantité de code d’accès aux données que vous auriez besoin d’écrire et de tester. EF Core prend en charge de nombreux moteurs de base de données.

Pour plus d’informations, consultez [Entity Framework Core](/ef/core/) et [fournisseurs de bases de données](/ef/core/providers/).

### <a name="linq"></a>LINQ

LINQ (Language-Integrated Query) vous permet d’écrire du code déclaratif pour l’exploitation des données. Les données peuvent se présenter sous plusieurs formes (comme des objets en mémoire, une base de données SQL ou un document XML), mais le code LINQ que vous écrivez ne diffère généralement pas d’une source de données à l’autre.

Pour plus d’informations, consultez [vue d’ensemble de LINQ (Language Integrated Query)](../standard/linq/index.md).

## <a name="net-terminology"></a>Terminologie .NET

Pour comprendre la documentation .NET, il peut être utile de savoir comment l’utilisation de certains termes a changé au fil du temps.

### <a name="net-core-and-net-5"></a>.NET Core et .NET 5

Dans 2002, Microsoft a publié [.NET Framework](../framework/get-started/overview.md), une plateforme de développement pour la création d’applications Windows. Aujourd’hui .NET Framework est à la version 4,8 et est toujours [pris en charge par Microsoft](https://dotnet.microsoft.com/platform/support/policy/dotnet-framework).

Dans 2014, Microsoft a commencé à écrire un successeur interplateforme et open source pour .NET Framework. Cette nouvelle implémentation de .NET était nommée .NET Core jusqu’à ce qu’elle atteigne la version 3,1. La version suivante après .NET Core 3,1 est .NET 5,0, qui est actuellement en préversion. Le numéro de version 4 a été ignoré pour éviter toute confusion entre cette implémentation de .NET et .NET Framework 4,8. Le nom « Core » a été supprimé pour préciser qu’il s’agit désormais de l’implémentation principale de .NET.

Cet article concerne .NET 5, mais une grande partie de la documentation pour .NET 5 a toujours des références à « .NET Core » ou à « .NET Framework ». En outre, « Core » reste dans les noms [ASP.net Core](/aspnet/core/) et [Entity Framework Core](/ef/core/).

La documentation fait également référence à .NET Standard. [.NET standard](../standard/net-standard.md) est une spécification d’API qui vous permet de développer des bibliothèques de classes pour plusieurs implémentations de .net.

Pour plus d’informations, consultez composants de l' [architecture .net](../standard/components.md).

### <a name="overloaded-terms"></a>Termes surchargés

Une partie de la terminologie pour .NET peut être déroutante, car le même mot est utilisé de différentes façons dans différents contextes. Voici quelques-unes des instances les plus importantes :

* **runtime**

  |Context  |signification de « Runtime » |
  |---------|---------|
  | [CLR (Common Language Runtime)](#clr)| Environnement d’exécution d’un programme managé. Le système d’exploitation fait partie de l’environnement d’exécution, mais ne fait pas partie du Runtime .NET. |
  | [.NET Runtime sur la page de téléchargement de .NET](https://dotnet.microsoft.com/download/dotnet-core) | Les bibliothèques [CLR](#clr) et [Runtime](#runtime-libraries), qui fournissent ensemble la prise en charge de l’exécution des applications [dépendantes du Framework](#deployment-models) . La page offre également des options d’exécution pour ASP.NET Core les applications serveur et les applications de bureau Windows. |
  | [Identificateur du Runtime (RID)](rid-catalog.md) | La plateforme du système d’exploitation et l’architecture du processeur sur laquelle s’exécute une application .NET. Par exemple : Windows x64, Linux x64. |

* **Framework**

  |Context  | signification de « Framework » |
  |---------|---------------------|
  | .NET Framework | Implémentation originale de Windows de .NET. « Framework » est en majuscules. |
  | version cible de .NET Framework | Ensemble d’API sur lequel repose une bibliothèque ou une application .NET. Exemples : .NET Core 3,1, .NET Standard 2,0 |
  | Moniker du Framework cible  | Un TFM est un format de jeton standardisé pour la spécification de la version cible de .NET Framework d’une application ou d’une bibliothèque .NET. Exemple : `net462` pour .NET Framework 4.6.2. |
  | application dépendante du Framework | Application qui peut s’exécuter uniquement sur un ordinateur sur lequel vous avez installé le runtime à partir de la [page de téléchargement de .net](https://dotnet.microsoft.com/download/dotnet-core). « Framework » dans cette utilisation est la même chose que le « runtime » que vous téléchargez à partir de la page de téléchargement de .NET. |
  | bibliothèques d’infrastructure | Parfois utilisé comme synonyme pour les [bibliothèques Runtime](#runtime-libraries). |

* **Kit SDK**

  |Context  | Signification du kit de développement logiciel (SDK) |
  |---------|---------------|
  | [SDK sur la page de téléchargement de .NET](#sdk-and-runtimes)  | Collection d’outils et de bibliothèques que vous téléchargez et installez pour développer et exécuter des applications .NET. Comprend l’interface CLI, MSBuild, le Runtime .NET et d’autres composants.|
  | [Projet de type SDK](#project-system-and-msbuild) | Ensemble de cibles et de tâches MSBuild qui spécifie comment générer un projet pour un type d’application particulier. Dans ce sens, le kit de développement logiciel (SDK) est spécifié à l’aide `Sdk` de l’attribut de l' `Project` élément dans un fichier projet. |

* **platform**

  |Context  | signification de la « plateforme » |
  |---------|--------------------|
  | multiplateforme | Dans ce terme, « plateforme » désigne un système d’exploitation et le matériel sur lequel il s’exécute, comme Windows, macOS, Linux, iOS et Android. |
  | Plateforme .NET | L’utilisation varie. La référence peut correspondre à une implémentation de .NET (telle que .NET Framework ou .NET 5) ou à un concept d’architecture de .NET, y compris toutes les implémentations. |

Pour plus d’informations sur la terminologie .NET, consultez le [Glossaire .net](../standard/glossary.md).

## <a name="advanced-scenarios"></a>Scénarios avancés

Les sections suivantes expliquent certaines fonctionnalités de .NET qui sont utiles dans les scénarios avancés.

### <a name="native-interop"></a>Interopérabilité native

Chaque système d’exploitation inclut une interface de programmation d’application (API) qui fournit des services système. .NET offre plusieurs moyens d’appeler ces API.

Le principal moyen d’interagir avec les API natives consiste à utiliser « appel de code non managé » ou P/Invoke pour l’instant. P/Invoke est pris en charge sur les plateformes Linux et Windows. Un mode d’interopérabilité Windows uniquement est connu sous le nom de « COM Interop », qui fonctionne avec les [composants com](/cpp/atl/introduction-to-com) dans du code managé. Il est basé sur l’infrastructure de P/Invoke, mais fonctionne légèrement différemment.

Pour plus d’informations, consultez [interopérabilité native](../standard/native-interop/index.md).

### <a name="unsafe-code"></a>Code unsafe

En fonction de la prise en charge du langage, le CLR vous permet d’accéder à la mémoire native et d’effectuer une opération arithmétique de pointeur par le biais de code `unsafe`. Ces opérations sont nécessaires pour certains algorithmes et pour l’interopérabilité du système. Bien que puissant, l’utilisation de code unsafe est déconseillée à moins qu’il soit nécessaire d’interagir avec les API système ou d’implémenter l’algorithme le plus efficace. Le code unsafe peut ne pas s’exécuter de la même façon dans différents environnements et perd les avantages d’un récupérateur de mémoire et de la cohérence des types. Nous vous recommandons de restreindre et centraliser le code unsafe autant que possible et de tester ce code de manière approfondie.

Pour plus d’informations, consultez [pointeurs et code unsafe](../csharp/programming-guide/unsafe-code-pointers/index.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Choisir un didacticiel .NET](tutorials/index.md)

> [!div class="nextstepaction"]
> [Essayez .NET dans votre navigateur](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)

> [!div class="nextstepaction"]
> [Visite guidée de C #](../csharp/tour-of-csharp/index.md)

> [!div class="nextstepaction"]
> [Visite guidée de F #](../fsharp/tour.md)
