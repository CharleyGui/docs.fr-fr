---
title: .NET Standard
description: En savoir plus sur .NET Standard, ses versions et les implémentations de .NET qui la prennent en charge.
ms.date: 10/05/2020
ms.technology: dotnet-standard
ms.custom: updateeachrelease
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
ms.openlocfilehash: a4a59fea3ab1a6bc93a12e3f0aa13dea726d8121
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050393"
---
# <a name="net-standard"></a>.NET Standard

[.NET standard](https://github.com/dotnet/standard) est une spécification formelle des API .net qui sont disponibles sur plusieurs implémentations de .net. La motivation derrière .NET Standard consistait à établir une meilleure uniformité dans l’écosystème .NET. Toutefois, .NET 5 adopte une approche différente pour établir l’uniformité, et cette nouvelle approche élimine la nécessité de .NET Standard dans de nombreux scénarios. Pour plus d’informations, consultez [.net 5 et .NET standard](#net-5-and-net-standard) plus loin dans cet article.

## <a name="net-implementation-support"></a>Prise en charge des implémentations de .NET

Les différentes implémentations de .NET ciblent des versions spécifiques de .NET Standard. Chaque version de l’implémentation de .NET publie la version la plus récente de .NET Standard qu’elle prend en charge, une instruction qui signifie qu’elle prend également en charge les versions précédentes. Par exemple, .NET Framework 4,6 implémente .NET Standard 1,3, ce qui signifie qu’il expose toutes les API définies dans les versions de .NET Standard 1,0 à 1,3. De même, .NET Framework 4.6.1 implémente .NET Standard 1,4, tandis que .NET 5,0 implémente .NET Standard 2,1.

Le tableau suivant répertorie les versions d’implémentation **minimales** qui prennent en charge chaque .NET standard version. Cela signifie que les versions ultérieures d’une implémentation indiquée prennent également en charge la version de .NET Standard correspondante. Par exemple, .NET Core 2,1 et versions ultérieures prennent en charge .NET Standard 2,0 et versions antérieures.

[!INCLUDE [net-standard-table](../../includes/net-standard-table.md)]

Pour trouver la version la plus élevée de .NET Standard que vous pouvez cibler, procédez comme suit :

1. Recherchez la ligne indiquant l’implémentation de .NET sur laquelle vous voulez exécuter.
1. Recherchez la colonne de cette ligne qui indique votre version, en allant de droite à gauche.
1. L’en-tête de colonne indique la version .NET Standard que votre cible prend en charge. Vous pouvez également cibler une version .NET Standard antérieure. Les versions .NET Standard ultérieures prendront également en charge votre implémentation.
1. Répétez ce processus pour chaque plateforme que vous voulez cibler. Si vous avez plusieurs plateformes cibles, vous devez choisir la version la moins élevée parmi elles. Par exemple, si vous souhaitez exécuter sur .NET Framework 4,8 et .NET 5,0, la version de .NET Standard la plus élevée que vous pouvez utiliser est .NET Standard 2,0.

### <a name="which-net-standard-version-to-target"></a>Version de .NET Standard à cibler

Lors du choix d’une version de .NET Standard à cibler, tenez compte de ce compromis :

- Plus la version est élevée, plus les API sont disponibles pour le code de votre bibliothèque.
- Plus la version est basse, plus les applications et les bibliothèques peuvent utiliser votre bibliothèque.

Nous vous recommandons de cibler la version la *plus basse* de .NET standard possible. Par conséquent, après avoir trouvé la version de .NET Standard la plus élevée que vous pouvez cibler, procédez comme suit :

1. Ciblez la version moins élevée suivante de .NET Standard et générez votre projet.
2. Si votre projet est généré correctement, répétez l’étape 1. Dans le cas contraire, reciblez-le sur la version plus élevée suivante : c’est cette version que vous devez utiliser.

Le ciblage de versions inférieures de .NET Standard génère cependant un certain nombre de dépendances de support. Si votre projet cible .NET Standard 1.x, nous vous recommandons de cibler *également* .NET Standard 2.0. Cela simplifie le graphique de dépendance pour les utilisateurs de votre bibliothèque qui s’exécutent sur des implémentations compatibles .NET Standard 2,0 et réduit le nombre de packages qu’ils doivent télécharger.

### <a name="net-standard-versioning-rules"></a>Règles de contrôle de version de .NET standard

Il existe deux règles principales de contrôle de version :

- Additive : les versions de .NET Standard sont des cercles logiquement concentriques : les versions plus élevées intègrent toutes les API des versions précédentes. Il n’y a pas de ruptures entre les versions.
- Immuable : une fois livrées, les versions de .NET Standard sont figées.

Il n’y aura pas de nouvelles versions de .NET Standard après 2,1. Pour plus d’informations, consultez [.net 5 et .NET standard](#net-5-and-net-standard) plus loin dans cet article.

## <a name="specification"></a>Caractéristique

La spécification de .NET Standard est un ensemble d’API normalisé. La spécification est gérée par les entités chargées de l’implémentation de .NET, en particulier Microsoft (inclut .NET Framework, .NET Core et Mono) et Unity.

### <a name="official-artifacts"></a>Artefacts officiels

La spécification officielle est un ensemble de fichiers *. cs* qui définissent les API qui font partie de la norme. Le [répertoire ref](https://github.com/dotnet/standard/tree/master/src/netstandard/ref) dans le [dépôt dotnet/standard](https://github.com/dotnet/standard) définit les API .NET Standard.

Le métapackage [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) ([source](https://github.com/dotnet/standard/blob/master/src/netstandard/pkg/NETStandard.Library.dependencies.props)) décrit l’ensemble des bibliothèques qui définissent (en partie) une ou plusieurs versions de .NET Standard.

Un composant donné, comme `System.Runtime`, décrit :

- Une partie de .NET Standard (seulement son étendue).
- Plusieurs versions de .NET Standard, pour cette étendue.

Des artefacts dérivés sont fournis pour une lecture plus pratique et pour activer certains scénarios de développement (par exemple, utilisation d’un compilateur).

- [Liste des API au format Markdown](https://github.com/dotnet/standard/tree/master/docs/versions)
- Assemblys de référence, distribués comme packages NuGet et référencés par le métapackage [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/).

### <a name="package-representation"></a>Représentation des packages

Les assemblys de référence de .NET Standard sont distribués principalement via les packages NuGet. Les implémentations sont fournies de façons différentes, en fonction de l’implémentation de .NET.

Les packages NuGet ciblent un ou plusieurs [frameworks](frameworks.md). Les packages .NET Standard ciblent le framework «.NET Standard ». Vous pouvez cibler le .NET Framework Standard avec le  [Moniker de framework cible compact](frameworks.md)`netstandard` (par exemple `netstandard1.4`). Les bibliothèques destinées à s’exécuter sur plusieurs implémentations de .NET doivent cibler ce Framework. Pour l’ensemble d’API le plus large, ciblez `netstandard2.0`, car le nombre d’API disponibles a plus que doublé entre .NET Standard 1.6 et 2.0.

Le sous- [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library/) package fait référence à l’ensemble complet des packages NuGet qui définissent .NET standard.  La méthode la plus courante pour cibler `netstandard` consiste à référencer ce métapackage. Il décrit et donne accès à la quarantaine de bibliothèques .NET et les API associées qui définissent .NET Standard. Vous pouvez référencer d’autres packages qui ciblent `netstandard` pour avoir accès à d’autres API.

### <a name="versioning"></a>Gestion de version

La spécification n’est pas singulière, mais un ensemble d’API avec version linéaire. La première version de la norme établit un ensemble d’API de référence. Les versions ultérieures ajoutent des API et héritent des API définies par les versions précédentes. Il n’existe aucune disposition établie pour supprimer des API de la norme.

.NET Standard n’est pas spécifique à une implémentation .NET et ne correspond pas au schéma de contrôle de version de ces implémentations.

Comme indiqué précédemment, il n’y aura pas de nouvelles versions de .NET Standard après 2,1.

## <a name="target-net-standard"></a>.NET Standard cible

Vous pouvez [créer des bibliothèques de .NET standard](../core/tutorials/libraries.md) à l’aide d’une combinaison de l' `netstandard` infrastructure et du `NETStandard.Library` produit.

## <a name="net-framework-compatibility-mode"></a>Mode de compatibilité du .NET Framework

Le mode de compatibilité du .NET Framework a été introduit dans .NET Standard 2.0. Ce mode de compatibilité permet aux projets .NET Standard de référencer des bibliothèques .NET Framework comme si elles étaient compilées pour .NET Standard. Le référencement de bibliothèques .NET Framework ne fonctionne pas pour tous les projets, par exemple pour les bibliothèques qui utilisent des API WPF (Windows Presentation Foundation).

Pour plus d’informations, consultez [Mode de compatibilité du .NET Framework](../core/porting/third-party-deps.md#net-framework-compatibility-mode).

## <a name="net-standard-libraries-and-visual-studio"></a>Bibliothèques .NET Standard et Visual Studio

Pour générer des bibliothèques .NET Standard dans Visual Studio, vérifiez que vous avez installé [Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) ou visual studio 2017 version 15,3 ou ultérieure sur Windows, ou [Visual Studio pour Mac version 7,1](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) ou ultérieure installée sur MacOS.

Si vous devez seulement utiliser les bibliothèques .NET Standard 2.0 dans vos projets, vous pouvez également le faire dans Visual Studio 2015. Cependant, le client NuGet 3.6 ou ultérieur doit être installé. Vous pouvez télécharger le client NuGet pour Visual Studio 2015 à partir de la page [Téléchargements NuGet](https://www.nuget.org/downloads).

## <a name="net-5-and-net-standard"></a>.NET 5 et .NET Standard

.NET 5 est l’implémentation de .NET que Microsoft développe activement. Il s’agit d’un produit unique avec un ensemble uniforme de fonctionnalités et d’API qui peuvent être utilisées pour les applications de bureau Windows et les applications de console multiplateforme, les services Cloud et les sites Web. Le [TFM](frameworks.md) .net 5,0 reflète ce large éventail de scénarios :

* `net5.0`

  Ce TFM est destiné au code qui s’exécute partout. À quelques exceptions près, il n’y a que des technologies qui fonctionnent sur plusieurs plateformes. Pour le code .NET 5, `net5.0` remplace `netcoreapp` et `netstandard` TFM.

* `net5.0-windows`

  Il s’agit d’un exemple de [TFM spécifiques au système d’exploitation](frameworks.md#net-5-os-specific-tfms) qui ajoutent des fonctionnalités spécifiques au système d’exploitation à tout ce qui `net5.0` fait référence à.

### <a name="when-to-target-net50-vs-netstandard"></a>Quand cibler .net 5.0 ou netstandard

Pour le code existant qui cible `netstandard` , il n’est pas nécessaire de changer le TFM en `net5.0` . .NET 5,0 implémente .NET Standard 2,1 et versions antérieures. La seule raison de recibler de .NET Standard vers .NET 5,0 est d’accéder à d’autres fonctionnalités du runtime, à des fonctionnalités de langage ou à des API. Par exemple, pour pouvoir utiliser C# 9, vous devez cibler .NET 5,0. Vous pouvez utiliser le .NET 5,0 et le .NET Standard pour accéder à des fonctionnalités plus récentes tout en gardant votre bibliothèque à la disposition d’autres implémentations .NET.

Voici quelques recommandations pour le nouveau code pour .NET 5 :

* Composants de l’application

  Si vous utilisez des bibliothèques pour décomposer une application en plusieurs composants, nous vous recommandons de `net5.x` cibler `5.x` l’emplacement de la première version de .net 5 que votre application peut cibler. Par souci de simplicité, il est préférable de conserver tous les projets qui composent votre application sur la même version de .NET. Vous pouvez ensuite supposer les mêmes fonctionnalités BCL partout.

* Bibliothèques réutilisables

  Si vous créez des bibliothèques réutilisables que vous envisagez de fournir sur NuGet, envisagez le compromis entre la portée et l’ensemble de fonctionnalités disponible. .NET Standard 2,0 est la dernière version prise en charge par .NET Framework, elle offre une bonne portée avec un ensemble de fonctionnalités assez volumineux. Nous vous déconseillons de cibler .NET Standard 1. x, car vous limitez le jeu de fonctionnalités disponibles pour une augmentation minimale de la portée.

  Si vous n’avez pas besoin de prendre en charge .NET Framework, vous pouvez utiliser .NET Standard 2,1 ou .NET 5. Nous vous recommandons d’ignorer .NET Standard 2,1 et de passer directement à .NET 5. Les bibliothèques les plus largement utilisées finissent par le multi-ciblage pour les .NET Standard 2,0 et .NET 5. La prise en charge de .NET Standard 2,0 vous donne la plus grande portée, tandis que la prise en charge de .NET 5 vous permet de tirer parti des dernières fonctionnalités de plateforme pour les clients qui sont déjà sur .NET 5.

### <a name="net-standard-problems"></a>.NET Standard les problèmes

Voici quelques problèmes avec .NET Standard qui expliquent pourquoi .NET 5 est la meilleure façon de partager du code entre les plateformes et les charges de travail :

- Lenteur pour ajouter de nouvelles API

  .NET Standard a été créé en tant qu’ensemble d’API que toutes les implémentations .NET doivent prendre en charge, de sorte qu’il y a eu un processus de révision pour les propositions visant à ajouter de nouvelles API. L’objectif était de normaliser uniquement les API qui pouvaient être implémentées dans toutes les plateformes .NET actuelles et futures. Par conséquent, si une fonctionnalité a manqué une version particulière, vous devrez peut-être attendre quelques années avant qu’elle ait été ajoutée à une version de la norme. Ensuite, vous attendez encore plus longtemps que la nouvelle version de .NET Standard soit largement prise en charge.

  **Solution dans .net 5 :** Quand une fonctionnalité est implémentée, elle est déjà disponible pour chaque application et bibliothèque .NET 5, car la base de code est partagée. Et étant donné qu’il n’y a aucune différence entre la spécification de l’API et son implémentation, vous pouvez tirer parti des nouvelles fonctionnalités bien plus rapidement qu’avec .NET Standard.

- Contrôle de version complexe

  La séparation de la spécification de l’API de ses implémentations entraîne un mappage complexe entre les versions de spécification d’API et les versions d’implémentation. Cette complexité est évidente dans le tableau présenté plus haut dans cet article, ainsi que les instructions relatives à son interprétation.

  **Solution dans .net 5 :** Il n’existe aucune séparation entre une spécification de l’API .NET 5. x et son implémentation. Le résultat est un schéma TFM simplifié. Il y a un préfixe TFM pour toutes les charges de travail : `net5.0` est utilisé pour les bibliothèques, les applications console et les applications Web. La seule variation est un [suffixe qui spécifie des API spécifiques](frameworks.md#net-5-os-specific-tfms) à la plateforme pour une plateforme particulière, par exemple `net5.0-windows` . Grâce à cette Convention d’affectation de noms TFM, vous pouvez facilement savoir si une application donnée peut utiliser une bibliothèque donnée. Aucune table équivalente de numéro de version, comme celle de .NET Standard est nécessaire.

- Exceptions non prises en charge par la plateforme au moment de l’exécution

  .NET Standard expose des API spécifiques à la plateforme. Votre code peut se compiler sans erreur et sembler portable sur n’importe quelle plateforme, même s’il n’est pas portable. Lorsqu’il s’exécute sur une plateforme qui n’a pas d’implémentation pour une API donnée, vous recevez des erreurs d’exécution.

  **Solution dans .net 5 :** Le kit de développement logiciel (SDK) .NET 5 comprend des analyseurs de code activés par défaut. L’analyseur de compatibilité de plateforme détecte l’utilisation non intentionnelle d’API qui ne sont pas prises en charge sur les plateformes que vous avez l’intention d’exécuter. Pour plus d’informations, consultez [Platform Compatibility Analyzer](analyzers/platform-compat-analyzer.md).

### <a name="net-standard-not-deprecated"></a>.NET Standard pas dépréciée

.NET Standard est toujours nécessaire pour les bibliothèques qui peuvent être utilisées par plusieurs implémentations de .NET. Nous vous recommandons de cibler .NET Standard dans les scénarios suivants :

* Utilisez `netstandard2.0` pour partager du code entre .NET Framework et toutes les autres implémentations de .net.
* Utilisez `netstandard2.1` pour partager du code entre mono, Xamarin et .net Core 3. x.

## <a name="see-also"></a>Voir aussi

- [Versions de .NET Standard (source)](https://github.com/dotnet/standard/blob/master/docs/versions.md)
- [Versions de .NET Standard (interface utilisateur interactive)](https://dotnet.microsoft.com/platform/dotnet-standard#versions)
- [Créer une bibliothèque de .NET Standard](../core/tutorials/library-with-visual-studio.md)
- [Ciblage multiplateforme](./library-guidance/cross-platform-targeting.md)
