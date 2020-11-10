---
title: Déplacer du .NET Framework à .NET Core
description: Présentation du processus de portage et d’outils qui peuvent s’avérer utiles lors du portage d’un projet .NET Framework vers .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 7719742294c04aadbfd2e5f223040d3b5b485b5b
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439740"
---
# <a name="overview-of-porting-from-net-framework-to-net-core"></a>Vue d’ensemble du Portage à partir de .NET Framework vers .NET Core

Vous pouvez avoir du code qui s’exécute actuellement sur le .NET Framework que vous souhaitez porter vers .NET Core. Cet article fournit :

* Vue d’ensemble du processus de Portage.
* Liste des outils que vous pouvez trouver utiles lorsque vous portez votre code vers .NET Core.

## <a name="overview-of-the-porting-process"></a>Vue d’ensemble du processus de portage

Le portage vers .NET Core (ou .NET Standard) à partir de .NET Framework pour de nombreux projets est relativement simple. Un certain nombre de modifications sont nécessaires, mais beaucoup d’entre elles suivent les modèles décrits ci-dessous. Les projets dans lesquels le modèle d’application est disponible dans .NET Core (tels que les bibliothèques, les applications console et les applications de bureau) requièrent généralement peu de modifications. Les projets qui requièrent un nouveau modèle d’application, tels que le passage à des ASP.NET Core à partir de ASP.NET, nécessitent un peu plus de travail, mais de nombreux modèles ont des analogies qui peuvent être utilisées lors de la conversion. Ce document doit vous aider à identifier les principales stratégies qui ont été utilisées par les utilisateurs pour convertir leurs bases de code en cibles .NET Standard ou .NET Core, et traitera la conversion à deux niveaux : à l’ensemble de la solution et spécifique au projet. Consultez les liens en bas pour obtenir des instructions sur les conversions spécifiques du modèle d’application.

Nous vous recommandons d’utiliser le processus suivant lors du Portage de votre projet vers .NET Core. Chacune de ces étapes introduit des emplacements potentiels pour les changements de comportement. Veillez donc à tester correctement votre bibliothèque ou votre application avant de passer aux étapes ultérieures. La première étape consiste à préparer votre projet pour un basculement vers .NET Standard ou .NET Core. Si vous avez des tests unitaires, il est préférable de les convertir d’abord afin de pouvoir continuer à tester les modifications dans le produit sur lequel vous travaillez. Étant donné que le portage vers .NET Core est une modification significative de votre code base, il est fortement recommandé de porter vos projets de test afin que vous puissiez exécuter des tests au fur et à mesure que vous portez votre code. MSTest, xUnit et NUnit fonctionnent tous sur .NET Core.

## <a name="getting-started"></a>Prise en main

Les outils suivants seront utilisés tout au long du processus :

- Visual Studio 2019
- Télécharger l' [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md)
- _Facultatif_ Installer [dotnet try-Convert](https://github.com/dotnet/try-convert)

## <a name="porting-a-solution"></a>Portage d’une solution

En présence de plusieurs projets dans une solution, le portage peut paraître plus compliqué, car vous devez traiter les projets dans un ordre spécifique. Le processus de conversion doit être une approche ascendante, dans laquelle les projets sans dépendances sur d’autres projets de la solution sont convertis en premier et continuent jusqu’à l’ensemble de la solution.

Pour identifier les projets de commande à migrer, vous pouvez utiliser les outils suivants :

- Les [diagrammes de dépendance dans Visual Studio](/visualstudio/modeling/create-layer-diagrams-from-your-code) peuvent créer un graphique orienté du code dans une solution.
- Exécutez `msbuild _SolutionPath_ /t:GenerateRestoreGraphFile /p:RestoreGraphOutputPath=graph.dg.json` pour générer un document JSON qui comprend la liste des références de projet.
- Exécutez l' [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) avec le `-r DGML` commutateur pour récupérer un diagramme de dépendance des assemblys. Vous pourrez trouver plus d’informations [ici](../../standard/analyzers/portability-analyzer.md#solution-wide-view).

Une fois que vous avez des informations sur les dépendances, vous pouvez utiliser ces informations pour démarrer à partir des nœuds terminaux et travailler dans l’arborescence des dépendances en appliquant les étapes de la section suivante.

## <a name="per-project-steps"></a>Par étape de projet

Nous vous recommandons d’utiliser le processus suivant lors du Portage de votre projet vers .NET Core :

1. Convertissez toutes vos `packages.config` dépendances au format [PackageReference](/nuget/consume-packages/package-references-in-project-files) avec l' [outil de conversion dans Visual Studio](/nuget/consume-packages/migrate-packages-config-to-package-reference).

   Cette étape implique la conversion de vos dépendances à partir du `packages.config` format hérité. `packages.config` ne fonctionne pas sur .NET Core, cette conversion est donc nécessaire si vous avez des dépendances de package. Elle nécessite également uniquement les dépendances que vous utilisez directement dans un projet, ce qui facilite les étapes ultérieures en réduisant le nombre de dépendances que vous devez gérer.

1. Convertissez votre fichier projet vers la nouvelle structure de fichiers de style SDK. Vous pouvez créer des projets pour .NET Core et copier des fichiers sources, ou essayer de convertir votre fichier projet existant à l’aide d’un outil.

   .NET Core utilise un [format de fichier projet](../tools/csproj.md) simplifié (et différent) que .NET Framework. Vous devez convertir vos fichiers projet dans ce format pour continuer. Ce style de projet vous permet également de cibler .NET Framework, à ce stade, vous souhaitez toujours cibler.

   Vous pouvez tenter de porter des solutions plus petites ou des projets individuels en une seule opération au format de fichier projet .NET Core à l’aide de l’outil [dotnet try-Convert](https://github.com/dotnet/try-convert) . `dotnet try-convert` n’a pas la garantie de fonctionner pour tous vos projets et peut entraîner des modifications subtiles du comportement dont vous dépendez. Utilisez-le comme _point de départ_ pour automatiser les éléments de base qui peuvent être automatisés. Il ne s’agit pas d’une solution garantie pour la migration d’un projet, car il existe de nombreuses différences dans les cibles utilisées par les projets de style du kit de développement logiciel (SDK) par rapport aux anciens fichiers de projet.

1. Reciblez tous les projets que vous souhaitez porter vers la cible .NET Framework 4.7.2 ou une version ultérieure.

   Cette étape garantit que vous pouvez utiliser des API alternatives pour des cibles spécifiques au .NET Framework si .NET Core ne prend en charge une API particulière.

1. Mettez à jour toutes les dépendances avec la version la plus récente. Les projets utilisent peut-être des versions antérieures de bibliothèques qui n’ont peut-être pas pris en charge .NET Standard. Toutefois, les versions ultérieures peuvent la prendre en charge avec un commutateur simple. Cela peut nécessiter des modifications de code en cas de modifications avec rupture dans les bibliothèques.

1. Utilisez l' [Analyseur de portabilité .net](../../standard/analyzers/portability-analyzer.md) pour analyser vos assemblys et voir s’ils sont portables vers .net core.

   L’outil de l’analyseur de portabilité .NET analyse vos assemblys compilés et génère un rapport. Ce rapport affiche un résumé de la portabilité de haut niveau et une répartition de chaque API que vous utilisez et qui n’est pas disponible sur .NET Core. Quand vous utilisez l’outil, soumettez uniquement le projet individuel que vous convertissez pour vous concentrer sur les modifications d’API qui sont potentiellement nécessaires. La plupart des API ont une disponibilité équivalente dans .NET Core, à partir de laquelle vous souhaitez basculer.

   Lors de la lecture des rapports générés par l’analyseur, les informations importantes sont les API réelles qui sont utilisées et pas nécessairement le pourcentage de prise en charge de la plateforme cible. De nombreuses API ont des options équivalentes dans .NET Standard/Core, et par conséquent, il est important de comprendre les scénarios dont votre bibliothèque ou votre application a besoin pour déterminer l’implication de la portabilité.

   Dans certains cas, les API ne sont pas équivalentes et vous devez effectuer certaines directives de préprocesseur du compilateur (autrement dit, `#if NET45` ) pour ajouter des plateformes au cas particulier. À ce stade, votre projet sera toujours ciblé .NET Framework. Pour chacun de ces cas ciblés, il est recommandé d’utiliser des conditions bien connues qui peuvent être comprises comme un scénario.  Par exemple, la prise en charge d’AppDomain dans .NET Core est limitée, mais pour le scénario de chargement et de déchargement des assemblys, il existe une nouvelle API qui n’est pas disponible dans .NET Core. Voici un moyen courant de gérer cela dans le code :

   ```csharp
   #if FEATURE_APPDOMAIN_LOADING
   // Code that uses appdomains
   #elif FEATURE_ASSEMBLY_LOAD_CONTEXT
   // Code that uses assembly load context
   #else
   #error Unsupported platform
   #endif
   ```

1. Installez l' [analyseur d’API .net](../../standard/analyzers/api-analyzer.md) dans vos projets pour identifier les API qui lèvent <xref:System.PlatformNotSupportedException> sur certaines plateformes et d’autres problèmes de compatibilité potentiels.

   Cet outil est similaire à l’analyseur de portabilité, mais au lieu d’analyser si le code peut être généré sur .NET Core, il analyse si vous utilisez une API d’une manière qui lève une <xref:System.PlatformNotSupportedException> au moment de l’exécution. Bien que cela ne soit pas courant si vous passez de .NET Framework 4.7.2 ou une version ultérieure, il est préférable de vérifier. Pour plus d’informations sur les API qui lèvent des exceptions sur .NET Core, consultez [API qui lèvent toujours des exceptions sur .net Core](../compatibility/unsupported-apis.md).

1. À ce stade, vous pouvez basculer vers le ciblage de .NET Core (généralement pour les applications) ou .NET Standard (pour les bibliothèques).

   Le choix entre .NET Core et .NET Standard dépend en grande partie de l’emplacement où le projet sera exécuté. S’il s’agit d’une bibliothèque qui sera consommée par d’autres applications ou distribuée via NuGet, la préférence consiste généralement à cibler .NET Standard. Toutefois, il peut y avoir des API qui sont uniquement disponibles sur .NET Core pour des raisons de performances ou pour d’autres raisons. Si c’est le cas, .NET Core doit être ciblé avec une .NET Standard Build potentiellement disponible, avec des performances ou des fonctionnalités réduites. En ciblant .NET Standard, le projet est prêt à s’exécuter sur de nouvelles plateformes (par exemple, webassembly). Si le projet a des dépendances sur des infrastructures d’application spécifiques (telles que ASP.NET Core), la cible sera limitée par les dépendances prises en charge par les dépendances.

   S’il n’existe aucune directive de préprocesseur pour le code de compilation conditionnelle pour .NET Framework ou .NET Standard, il s’agit simplement de rechercher les éléments suivants dans le fichier projet :

   ```xml
   <TargetFramework>net472</TargetFramework>
   ```

   et basculez vers le Framework souhaité. Pour .NET Core 3,1, il s’agit de :

   ```xml
   <TargetFramework>netcoreapp3.1</TargetFramework>
   ```

   Toutefois, s’il s’agit d’une bibliothèque pour laquelle vous souhaitez continuer à prendre en charge des builds spécifiques à .NET Framework, vous pouvez utiliser [plusieurs cibles](../../standard/library-guidance/cross-platform-targeting.md) en les remplaçant par les éléments suivants :

   ```xml
   <TargetFrameworks>net472;netstandard2.0</TargetFrameworks>
   ```

   Si vous utilisez des API spécifiques à Windows (telles que l’accès au registre), installez le [Pack de compatibilité Windows](./windows-compat-pack.md).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Analyser les dépendances](third-party-deps.md) 
>  [Empaqueter un package NuGet](../deploying/creating-nuget-packages.md)

## <a name="see-also"></a>Voir aussi

- [Migration de ASP.NET vers ASP.NET Core](/aspnet/core/migration/proper-to-2x)
- [Migrer des applications WPF vers .NET Core](/dotnet/desktop/wpf/migration/convert-project-from-net-framework)
- [Migrer des applications Windows Forms .NET Framework vers .NET](/dotnet/desktop/winforms/migration/?view=netdesktop-5.0&preserve-view=true)
