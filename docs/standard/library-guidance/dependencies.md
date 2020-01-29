---
title: Dépendances et bibliothèques .NET
description: Meilleures pratiques suggérées pour la gestion des dépendances NuGet dans les bibliothèques .NET.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731478"
---
# <a name="dependencies"></a>Dépendances

Le principal moyen d’ajouter des dépendances à une bibliothèque .NET est de référencer des packages NuGet. Les références de packages NuGet vous permettent de réutiliser rapidement des fonctionnalités déjà écrites et d’en tirer parti , mais elles sont une source courante de friction pour les développeurs .NET. La gestion correcte des dépendances est importante pour empêcher des modifications dans d’autres bibliothèques .NET d’arrêter votre bibliothèque .NET et vice versa !

## <a name="diamond-dependencies"></a>Dépendances en losange

Il est courant qu’un projet .NET ait plusieurs versions d’un package dans son arborescence des dépendances. Par exemple, une application dépend de deux packages NuGet dont chacun dépend de différentes versions du même package. Il y a désormais une dépendance en losange dans le graphique de dépendance de l’application.

![Dépendance Diamond](./media/dependencies/diamond-dependency.png "Dépendance Diamond")

Lors du build, NuGet analyse tous les packages dont dépend un projet, y compris les dépendances de dépendances. Lorsque plusieurs versions d’un package sont détectées, les règles sont évaluées pour en choisir une. L’unification des packages est nécessaire, car l’exécution côte à côte des versions d’un assembly dans la même application est problématique dans .NET.

La plupart des dépendances en losange sont facilement résolues ; toutefois, elles peuvent créer des problèmes dans certaines circonstances :

1. **Les conflits de références de packages NuGet** empêchent la résolution d’une version pendant la restauration du package.
2. **Des modifications importantes entre les versions** provoquent des bogues et des exceptions lors de l’exécution.
3. **Un nom fort est attribué à l’assembly de package**, la version d’assembly est modifiée et l’application exécutée sur .NET Framework. Des redirection des liaisons d'assembly sont requises.

Il n’est pas possible de savoir quels packages seront utilisées en même temps que le vôtre. Un bon moyen de réduire la probabilité d’une dépendance en losange avec arrêt de votre bibliothèque consiste à limiter le nombre de packages dont vous dépendez.

✔️ Examinez votre bibliothèque .NET pour rechercher les dépendances inutiles.

## <a name="nuget-dependency-version-ranges"></a>Plages de versions de dépendances de NuGet

Une référence de package spécifie la plage de packages valides autorisés. Généralement, la version de référence de package dans le fichier projet est la version minimale et il n’y a pas de maximum.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Les règles que NuGet utilise lors de la résolution des dépendances sont [complexes](/nuget/consume-packages/dependency-resolution), mais il recherche toujours la version la plus ancienne applicable. NuGet préfère la version la plus ancienne applicable à la plus récente disponible, car la plus ancienne aura moins de problèmes de compatibilité.

En raison de la règle de la version la plus ancienne applicable de NuGet, il n’est pas nécessaire de placer une version supérieure ou une plage exacte sur les références de package pour éviter d’obtenir la dernière version. NuGet essaie déjà de trouver de la version la plus ancienne et la plus compatible pour vous.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Des limites de versions supérieures entraîneront l’échec de NuGet en cas de conflit. Par exemple, une bibliothèque accepte exactement 1.0, tandis qu’une autre bibliothèque requiert 2.0 ou une version ultérieure. Alors que les modifications importantes peuvent avoir été introduites dans la version 2.0, une dépendance de version stricte ou supérieure d’une limite garantit une erreur.

![Conflit de dépendances Diamond](./media/dependencies/diamond-dependency-conflict.png "Conflit de dépendances Diamond")

❌ n’avez pas de références de package NuGet sans version minimale.

❌ éviter les références de package NuGet qui demandent une version exacte.

❌ éviter les références de package NuGet avec une limite supérieure de version.

## <a name="nuget-shared-source-packages"></a>Packages NuGet à code source partagé

Une manière de réduire les dépendances externes de packages NuGet externes consiste à référencer les packages à code source partagé. Un package à code source partagé contient des [fichiers de code source](/nuget/reference/nuspec#including-content-files) qui sont inclus dans un projet référencé. Comme vous incluez uniquement des fichiers de code source compilés avec le reste de votre projet, il n’y a aucune dépendance externe ni risque de conflit.

Les packages à code source partagée sont l’idéal pour inclure de petits éléments de fonctionnalité. Par exemple, un package à source partagée de méthodes d’assistance pour les appels HTTP.

![Package source partagé](./media/dependencies/shared-source-package.png "Package source partagé")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Projet source partagé](./media/dependencies/shared-source-project.png "Projet source partagé")

Les packages à code source partagé ont certaines limitations. Ils ne peuvent être référencés que par `PackageReference`, ce qui exclut les projets `packages.config` plus anciens. Par ailleurs, les packages à code source partagé ne peuvent être utilisés que par des projets ayant le même type de langage. En raison de ces limitations, les packages à code source partagé sont très bien adaptés au partage d’une fonctionnalité au sein d’un projet open source.

✔️ envisagez de faire référence à des packages source partagés pour de petites parties de fonctionnalités internes.

✔️ envisagez de faire de votre package un package source partagé s’il fournit de petits éléments de fonctionnalité internes.

✔️ FAITES référence à des packages source partagés avec `PrivateAssets="All"`.

> Ce paramètre indique à NuGet que le package ne doit être utilisée que lors du développement et ne doit pas être exposé en tant que dépendance publique.

❌ n’avez pas de types de packages sources partagés dans votre API publique.

> Les types à code source partagé sont compilés dans l’assembly de référencement et ne peuvent pas être échangés au-delà des limites de l’assembly. Par exemple, un type de `IRepository` à code source partagé dans un projet est un type distinct du même `IRepository` à code source partagé dans un autre projet. Les types de packages à code source partagé doivent avoir une visibilité `internal`.

❌ ne publiez pas de packages source partagés sur NuGet.org.

> Les packages à code source partagé contiennent du code source et ne peuvent être utilisés que par des projets ayant le même type de langage. Par exemple, un package à code source partagé C# ne peut pas être utilisé par une application F#.
>
> Publier des packages à code source partagé sur un [flux local ou MyGet](./publish-nuget-package.md) pour les utiliser en interne au sein de votre projet.

>[!div class="step-by-step"]
>[Précédent](nuget.md)
>[Suivant](sourcelink.md)
