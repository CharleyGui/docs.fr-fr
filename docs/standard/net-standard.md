---
title: .NET Standard
description: Découvrez .NET Standard, ses versions et les implémentations de .NET qui le prennent en charge.
ms.date: 02/13/2020
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: 00b40b771a8608bad7e3f992e3c99367ff6bb131
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452589"
---
# <a name="net-standard"></a>.NET Standard

[.NET standard](https://github.com/dotnet/standard) est une spécification formelle des API .net qui sont destinées à être disponibles sur toutes les implémentations de .net. La motivation derrière .NET Standard consiste à établir une meilleure uniformité dans l’écosystème .NET. L' [ecma 335](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) continue à établir l’uniformité du comportement de l’implémentation de .net, tandis que l’ECMA 335 spécifie un petit ensemble de bibliothèques standard, la spécification .NET standard englobe une plus large gamme d’API .net.

.NET Standard permet les scénarios clés suivants :

- Définit un ensemble uniforme d’API de bibliothèque de classes de base pour toutes les implémentations de .NET à implémenter, indépendamment de la charge de travail.
- Permet aux développeurs de générer des bibliothèques portables utilisables sur toutes les implémentations de .NET, à l’aide de ce même ensemble d’API.
- Réduit ou même élimine une compilation conditionnelle de source partagée résultant des API .NET, uniquement pour les API de système d’exploitation.

Les différentes implémentations de .NET ciblent des versions spécifiques de .NET Standard. Chaque version de l’implémentation de .NET publie la version la plus récente de .NET Standard qu’elle prend en charge, une instruction qui signifie qu’elle prend également en charge les versions précédentes. Par exemple, .NET Framework 4,6 implémente .NET Standard 1,3, ce qui signifie qu’il expose toutes les API définies dans les versions de .NET Standard 1,0 à 1,3. De même, .NET Framework 4.6.1 implémente .NET Standard 1,4, tandis que .NET Core 1,0 implémente .NET Standard 1,6.

## <a name="net-implementation-support"></a>Prise en charge des implémentations de .NET

Le tableau suivant liste les versions **minimales** des plateformes qui prennent en charge chaque version de .NET Standard. Cela signifie que les versions ultérieures d’une plateforme listée prennent également en charge la version correspondante de .NET Standard. Par exemple, .NET Core 2.2 prend en charge .NET Standard 2.0 et les versions antérieures.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Pour trouver la version la plus élevée de .NET Standard que vous pouvez cibler, procédez comme suit :

1. Recherchez la ligne indiquant l’implémentation de .NET sur laquelle vous voulez exécuter.
2. Recherchez la colonne de cette ligne qui indique votre version, en allant de droite à gauche.
3. L’en-tête de colonne indique la version .NET Standard que votre cible prend en charge. Vous pouvez également cibler une version .NET Standard antérieure. Les versions .NET Standard ultérieures prendront également en charge votre implémentation.
4. Répétez ce processus pour chaque plateforme que vous voulez cibler. Si vous avez plusieurs plateformes cibles, vous devez choisir la version la moins élevée parmi elles. Par exemple, si vous voulez exécuter sur le .NET Framework 4.5 et .NET Core 1.0, la version .NET Standard le plus élevée que vous pouvez utiliser est .NET Standard 1.1.

### <a name="which-net-standard-version-to-target"></a>Version de .NET Standard à cibler

Lors du choix d’une version de .NET Standard, vous devez envisager ce compromis :

- Plus la version est élevée, plus nombreuses sont les API disponibles.
- Moins la version est élevée, plus nombreuses sont les plateformes qui l’implémentent.

D’une façon générale, nous vous recommandons de cibler la version *la moins élevée* possible de .NET Standard. Par conséquent, après avoir trouvé la version de .NET Standard la plus élevée que vous pouvez cibler, procédez comme suit :

1. Ciblez la version moins élevée suivante de .NET Standard et générez votre projet.
2. Si votre projet est généré correctement, répétez l’étape 1. Dans le cas contraire, reciblez-le sur la version plus élevée suivante : c’est cette version que vous devez utiliser.

Le ciblage de versions inférieures de .NET Standard génère cependant un certain nombre de dépendances de support. Si votre projet cible .NET Standard 1.x, nous vous recommandons de cibler *également* .NET Standard 2.0. Ceci simplifie le graphique de dépendance pour les utilisateurs de votre bibliothèque qui exécutent des infrastructures compatibles .NET Standard 2.0 et réduit le nombre de packages qu’ils doivent télécharger.

### <a name="net-standard-versioning-rules"></a>Règles de contrôle de version de .NET standard

Il existe deux règles principales de contrôle de version :

- Additive : les versions de .NET Standard sont des cercles logiquement concentriques : les versions plus élevées intègrent toutes les API des versions précédentes. Il n’y a pas de ruptures entre les versions.
- Immuable : une fois livrées, les versions de .NET Standard sont figées. Les nouvelles API sont disponibles d’abord dans les implémentations de .NET spécifiques, comme .NET Core. Si le comité de révision de .NET Standard estime que les nouvelles API doivent être disponibles pour les implémentations de .NET, elles sont ajoutées dans une nouvelle version de .NET Standard.

## <a name="specification"></a>Caractéristique

La spécification de .NET Standard est un ensemble d’API normalisé. La spécification est gérée par les entités chargées de l’implémentation de .NET, en particulier Microsoft (inclut .NET Framework, .NET Core et Mono) et Unity. Un processus de commentaires publics est utilisé dans le cadre de l’établissement des nouvelles versions de .NET Standard via [GitHub](https://github.com/dotnet/standard).

### <a name="official-artifacts"></a>Artefacts officiels

La spécification officielle est un ensemble de fichiers .cs qui définissent les API qui font partie de la norme. Le [répertoire ref](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) dans le [dépôt dotnet/standard](https://github.com/dotnet/standard) définit les API .NET Standard.

Le métapackage [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) ([source](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) décrit l’ensemble des bibliothèques qui définissent (en partie) une ou plusieurs versions de .NET Standard.

Un composant donné, comme `System.Runtime`, décrit :

- Une partie de .NET Standard (seulement son étendue).
- Plusieurs versions de .NET Standard, pour cette étendue.

Des artefacts dérivés sont fournis pour une lecture plus pratique et pour activer certains scénarios de développement (par exemple, utilisation d’un compilateur).

- [Liste des API au format Markdown](https://github.com/dotnet/standard/tree/master/docs/versions)
- Assemblys de référence, distribués comme [packages NuGet](../core/packages.md) et référencés par le métapackage [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/).

### <a name="package-representation"></a>Représentation des packages

Les assemblys de référence de .NET Standard sont distribués principalement via les [packages NuGet](../core/packages.md). Les implémentations sont fournies de façons différentes, en fonction de l’implémentation de .NET.

Les packages NuGet ciblent un ou plusieurs [frameworks](frameworks.md). Les packages .NET Standard ciblent le framework «.NET Standard ». Vous pouvez cibler le .NET Standard Framework à l’aide de la `netstandard` [compact TFM](frameworks.md) (par exemple, `netstandard1.4`). Les bibliothèques destinées à s’exécuter sur plusieurs runtimes doivent cibler ce framework. Pour l’ensemble d’API le plus large, ciblez `netstandard2.0`, car le nombre d’API disponibles a plus que doublé entre .NET Standard 1.6 et 2.0.

Le métapackage [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) référence l’ensemble complet des packages NuGet qui définissent .NET Standard.  La méthode la plus courante pour cibler `netstandard` consiste à référencer ce métapackage. Il décrit et donne accès à la quarantaine de bibliothèques .NET et les API associées qui définissent .NET Standard. Vous pouvez référencer d’autres packages qui ciblent `netstandard` pour avoir accès à d’autres API.

### <a name="versioning"></a>Contrôle de version

La spécification n’est pas singulière, mais représente un ensemble d’API dont la croissance est incrémentielle et les versions linéaires. La première version de la norme établit un ensemble d’API de référence. Les versions ultérieures ajoutent des API et héritent des API définies par les versions précédentes. Il n’existe aucune disposition établie pour supprimer des API de la norme.

.NET Standard n’est spécifique à aucune implémentation de .NET et ne correspond pas au schéma de contrôle de version de ces runtimes.

Les API ajoutées à une implémentation (par exemple, .NET Framework, .NET Core et Mono) peuvent être considérées comme des candidats à ajouter à la spécification, en particulier si elles sont jugées fondamentales. Des [versions de .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md) sont créées en fonction des versions Release des implémentations de .NET, ce qui vous permet de cibler les nouvelles API à partir d’une bibliothèque de classes portable .NET Standard. Les mécanismes du contrôle de version sont décrits plus en détail dans [Gestion de version .NET Core](../core/versions/index.md).

Le contrôle de version de .NET Standard est important pour son utilisation. Pour une version donnée de .NET Standard, vous pouvez utiliser des bibliothèques qui ciblent cette même version ou une version moins élevée. L’approche suivante décrit le flux de travail de l’utilisation des bibliothèques de classes portables .NET Standard, propre au ciblage de .NET Standard.

- Sélectionnez une version de .NET Standard à utiliser pour votre bibliothèque de classes portable.
- Utilisez des bibliothèques qui dépendent de la même version de .NET Standard ou d’une version inférieure.
- Si vous trouvez une bibliothèque qui dépend d’une version plus élevée de .NET Standard, vous devez adopter cette même version ou décider de ne pas utiliser cette bibliothèque.

## <a name="targeting-net-standard"></a>Ciblage de .NET Standard

Vous pouvez [créer des bibliothèques .NET Standard](../core/tutorials/libraries.md) en combinant le framework `netstandard` et le métapackage NETStandard.Library. Vous pouvez voir des exemples de [ciblage de .NET Standard avec les outils .NET Core](../core/packages.md).

## <a name="net-framework-compatibility-mode"></a>Mode de compatibilité du .NET Framework

Le mode de compatibilité du .NET Framework a été introduit dans .NET Standard 2.0. Ce mode de compatibilité permet aux projets .NET Standard de référencer des bibliothèques .NET Framework comme si elles étaient compilées pour .NET Standard. Le référencement de bibliothèques .NET Framework ne fonctionne pas pour tous les projets, par exemple pour les bibliothèques qui utilisent des API WPF (Windows Presentation Foundation).

Pour plus d’informations, consultez [Mode de compatibilité du .NET Framework](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Bibliothèques .NET Standard et Visual Studio

Pour générer des bibliothèques .NET Standard dans Visual Studio, vérifiez que [Visual Studio 2017 version 15.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) ou ultérieur est installé sur Windows, ou que [Visual Studio pour Mac version 7.1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ou ultérieur est installé sur macOS.

Si vous devez seulement utiliser les bibliothèques .NET Standard 2.0 dans vos projets, vous pouvez également le faire dans Visual Studio 2015. Cependant, le client NuGet 3.6 ou ultérieur doit être installé. Vous pouvez télécharger le client NuGet pour Visual Studio 2015 à partir de la page [Téléchargements NuGet](https://www.nuget.org/downloads).

## <a name="comparison-to-portable-class-libraries"></a>Comparaison avec les bibliothèques de classes portables

.NET Standard remplace les [bibliothèques de classes portables](./cross-platform/cross-platform-development-with-the-portable-class-library.md). .NET Standard améliore l’expérience de création des bibliothèques portables en organisant une bibliothèque de classes de base, établissant ainsi une meilleure uniformité entre les implémentations de .NET. Une bibliothèque qui cible .NET Standard est une bibliothèque de classes portable ou une « bibliothèque de classes portable .NET Standard ». Les bibliothèques de classes portables existantes sont basées sur un profil.

.NET Standard et les profils de bibliothèque de classes portable ont été créés pour des raisons similaires, mais diffèrent de façon significative.

Points communs :

- Définit les API qui peuvent être utilisées pour le partage de code binaire.

Différences :

- .NET Standard est un ensemble organisé d’API, tandis que les profils de bibliothèque de classes portable sont définis par des intersections de plateformes existantes.
- .NET Standard a des versions linéaires, contrairement aux profils de bibliothèque de classes portable.
- Les profils de bibliothèque de classes portable représentent les plateformes Microsoft, alors que .NET Standard est indépendant de la plateforme.

### <a name="pcl-compatibility"></a>Compatibilité des bibliothèques de classes portables

.NET Standard est compatible avec un sous-ensemble de profils de bibliothèque de classes portable. Les versions 1.0, 1.1 et 1.2 de .NET Standard se recouvrent chacune avec un ensemble de profils de bibliothèque de classes portable. Ce chevauchement a été créé pour deux raisons :

- Permettre aux bibliothèques de classes portables .NET Standard de référencer les bibliothèques de classes portables basées sur un profil.
- Permettre aux bibliothèques de classes portables basées sur un profil d’être packagées comme des bibliothèques de classes portables .NET Standard.

La compatibilité des bibliothèques de classes portables est fournie par le package NuGet [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility). Cette dépendance est nécessaire quand vous référencez des packages NuGet qui contiennent des bibliothèques de classes portables basées sur un profil.

Les bibliothèques de classes portables basées sur un profil packagées en `netstandard` sont plus faciles à utiliser que les bibliothèques de classes portables basées sur un profil packagées de manière habituelle. Les packages `netstandard` sont compatibles avec les utilisateurs existants.

Voici l’ensemble des profils de bibliothèques de classes portables qui sont compatibles avec .NET Standard :

| Profil de bibliothèque de classes portable | .NET Standard | Plateformes de bibliothèque de classes portable
|:-----------:|:-------------:|------------------------------------------------------------------------------
| Profile7    | 1.1           | .NET Framework 4.5, Windows 8
| Profile31   | 1.0           | Windows 8.1, Windows Phone Silverlight 8.1
| Profile32   | 1.2           | Windows 8.1, Windows Phone 8.1
| Profile44   | 1.2           | .NET Framework 4.5.1, Windows 8.1
| Profile49   | 1.0           | .NET Framework 4.5, Windows Phone Silverlight 8
| Profile78   | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone Silverlight 8
| Profile84   | 1.0           | Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile111  | 1.1           | .NET Framework 4.5, Windows 8, Windows Phone 8.1
| Profile151  | 1.2           | .NET Framework 4.5.1, Windows 8.1, Windows Phone 8.1
| Profile157  | 1.0           | Windows 8.1, Windows Phone 8.1, Windows Phone Silverlight 8.1
| Profile259  | 1.0           | .NET Framework 4.5, Windows 8, Windows Phone 8.1, Windows Phone Silverlight 8

## <a name="see-also"></a>Voir aussi

- [Versions de .NET Standard](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [Créer une bibliothèque de .NET Standard](../core/tutorials/library-with-visual-studio.md)
- [Ciblage multiplateforme](./library-guidance/cross-platform-targeting.md)
