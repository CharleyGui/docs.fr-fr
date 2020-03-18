---
title: Paquets, métapackages et cadres - .NET Core
description: Découvrez la terminologie des packages, des métapackages et des infrastructures.
author: richlander
ms.date: 06/20/2016
ms.openlocfilehash: 657519edf1c0860ee3222c71ce85723e19029a9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398978"
---
# <a name="packages-metapackages-and-frameworks"></a>Packages, métapackages et frameworks

.NET Core est une plateforme constituée de packages NuGet. Certains produits bénéficient d’une définition de packages très précise, d’autres d’une définition plus grossière. Pour tenir compte de cette dualité, .NET Core est distribué comme un ensemble de paquets à grain fin et en morceaux plus grossiers avec un type d’emballage officieusement appelé [un métapackage](#metapackages).

Chacun des paquets .NET Core prend en charge l’exécution sur plusieurs implémentations .NET, représentées comme cadres. Certains de ces cadres sont des `net46`cadres traditionnels, comme , qui représente le cadre .NET. D’autres sont de nouveaux frameworks qui peuvent s’envisager comme des « frameworks basés sur des packages », qui établissent un nouveau modèle de définition de frameworks. Ces cadres basés sur des paquets sont entièrement créés et définis comme des paquets, formant une relation forte entre les paquets et les cadres.

## <a name="packages"></a>.

.NET Core est divisé en un ensemble de paquets qui fournissent des primitifs, des types de données de plus haut niveau, des types de composition d’applications et des services publics communs. Chacun de ces paquets représente un seul assemblage du même nom. Par exemple, le [paquet System.Runtime](https://www.nuget.org/packages/System.Runtime) contient System.Runtime.dll.

Il y a des avantages à définir les packages avec précision :

- Les packages définis avec précision peuvent être émis selon un calendrier qui leur est propre en ayant relativement peu testé d’autres packages.
- Ils peuvent offrir une prise en charge de systèmes d’exploitation et de processeurs différents.
- Ils peuvent avoir des dépendances spécifiques à une seule bibliothèque.
- Les applications sont plus petites, car les packages non référencés ne sont pas distribués avec elles.

Certains de ces avantages ne sont profitables que dans certaines circonstances. Par exemple, les packages .NET Core sont généralement émis selon le même calendrier avec la même prise en charge de plateforme. Dans le cas de la maintenance, des correctifs peuvent être distribués et installés sous forme de petites mises à jour de package uniques. En raison de la portée limitée des modifications, la validation et le délai de mise à disposition d’un correctif sont limitées au strict nécessaire pour une même bibliothèque.

Voici la liste des principaux packages NuGet pour .NET Core :

- [System.Runtime](https://www.nuget.org/packages/System.Runtime) - Le paquet le plus <xref:System.Object> <xref:System.String>fondamental <xref:System.Array> <xref:System.Action>.NET <xref:System.Collections.Generic.IList%601>Core, y compris , , , , et .
- [System.Collections](https://www.nuget.org/packages/System.Collections) : ensemble de collections (principalement) génériques, notamment <xref:System.Collections.Generic.List%601> et <xref:System.Collections.Generic.Dictionary%602>.
- [System.Net.Http](https://www.nuget.org/packages/System.Net.Http) : ensemble de types pour les communications réseau HTTP, notamment <xref:System.Net.Http.HttpClient> et <xref:System.Net.Http.HttpResponseMessage>.
- [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) : ensemble de types pour la lecture et l’écriture dans un stockage sur disque local ou en réseau, dont <xref:System.IO.File> et <xref:System.IO.Directory>.
- [System.Linq](https://www.nuget.org/packages/System.Linq) : ensemble de types pour l’interrogation d’objets, notamment `Enumerable` et <xref:System.Linq.ILookup%602>.
- [System.Reflection](https://www.nuget.org/packages/System.Reflection) - Un ensemble de types pour le chargement, <xref:System.Reflection.Assembly> <xref:System.Reflection.TypeInfo> l’inspection et l’activation des types, y compris, et <xref:System.Reflection.MethodInfo>.

En règle générale, il est plus facile et plus robuste d’inclure un [métapackage](#metapackages) que chacun des packages. Toutefois, si vous avez besoin d’un seul package, vous pouvez l’ajouter de la même manière que dans l’exemple suivant, qui fait référence au package [System.Runtime](https://www.nuget.org/packages/System.Runtime/).

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
  <ItemGroup>
    <PackageReference Include="System.Runtime" Version="4.3.0" />
  </ItemGroup>
</Project>
```

## <a name="metapackages"></a>Métapackages

Un métapackage est une convention de paquet NuGet pour décrire un ensemble de paquets qui sont significatifs ensemble. Un métapackage représente cet ensemble de paquets en les rendant dépendants. Le métapackage peut en option établir un cadre pour l’ensemble des paquets en spécifiant un cadre.

Les versions précédentes des outils .NET Core (les outils project.json et csproj) spécifiaient par défaut un framework et un métapackage. Actuellement, toutefois, le métapackage est implicitement référencé par le framework cible, de sorte que chaque métapackage est lié à un framework cible. Par exemple, le framework `netstandard1.6` référence le métapackage NetStandard.Library version 1.6.0. De même, le framework `netcoreapp2.1` référence le métapackage Microsoft.NETCore.App version 2.1.0. Pour plus d’informations, consultez [Implicit metapackage package reference in the .NET Core SDK](https://github.com/dotnet/core/blob/master/release-notes/1.0/sdk/1.0-rc3-implicit-package-refs.md) (Référence de package métapackage implicite dans le SDK .NET Core).

Cibler un cadre et implicitement référencer un métapackage signifie que, en fait, vous ajoutez une référence à chacun de ses paquets dépendants comme un seul geste. De cette façon, toutes les bibliothèques contenues dans ces packages sont disponibles pour IntelliSense (ou une expérience similaire) et pour la publication de votre application.

L’utilisation de métapackages confère les avantages suivants :

- Fournit une expérience utilisateur pratique pour référencer un ensemble étoffé de packages définis avec précision.
- Définit un ensemble de packages (comprenant des versions spécifiques) qui ont été testés et fonctionnent bien ensemble.

Le métapackage .NET Standard est le suivant :

- [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) - Décrit les bibliothèques qui font partie de la norme .NET. S’applique à toutes les implémentations .NET qui prennent en charge .NET Standard (par exemple, .NET Framework, .NET Core, et Mono). Établit le `netstandard` cadre.

Les principaux métapackages .NET Core sont les suivants :

- [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) : décrit les bibliothèques qui font partie de la distribution .NET Core. Établit le `.NETCoreApp` cadre. Dépend de la bibliothèque `NETStandard.Library` (plus petite).
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.App) : contient tous les packages pris en charge d’ASP.NET Core et d’Entity Framework Core, sauf ceux qui contiennent des dépendances tierces. Pour plus d’informations, voir [Métapackage Microsoft.AspNetCore.App pour ASP.NET Core](/aspnet/core/fundamentals/metapackage-app).
- [Microsoft.AspNetCore.All](https://www.nuget.org/packages/Microsoft.AspNetCore.All) : contient tous les packages pris en charge d’ASP.NET Core, d’Entity Framework Core, et des dépendances internes et tierces utilisées par ASP.NET Core et Entity Framework Core. Pour plus d’informations, consultez [Métapackage Microsoft.AspNetCore.All pour ASP.NET Core 2.x](/aspnet/core/fundamentals/metapackage).
- [Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) : ensemble de façades de compatibilité qui permettent aux bibliothèques de classes portables (PCL) basées sur mscorlib de s’exécuter sur .NET Core.

## <a name="frameworks"></a>Frameworks

Chaque package .NET Core prend en charge un ensemble de frameworks de runtime. Les frameworks décrivent un ensemble d’API disponibles (et éventuellement d’autres caractéristiques) sur lesquelles vous pouvez vous appuyer quand vous ciblez un framework donné. Leur version change à mesure que de nouvelles API sont ajoutés.

Par exemple, [System.IO.FileSystem](https://www.nuget.org/packages/System.IO.FileSystem) prend en charge les frameworks suivants :

- .NETFramework,Version=4.6
- .NETStandard,Version=1.3
- 6 plateformes Xamarin (par exemple, xamarinios10)

Il est utile de comparer les deux premiers de ces cadres, car ils sont des exemples des deux façons différentes dont les cadres sont définis :

- Le `.NETFramework,Version=4.6` cadre représente les API disponibles dans .NET Framework 4.6. Vous pouvez produire des bibliothèques compilées avec les assemblages de référence .NET Framework 4.6, puis distribuer ces bibliothèques dans des paquets NuGet dans un dossier net46 lib. Il sera utilisé pour les applications qui ciblent .NET Framework 4.6 ou qui sont compatibles avec elle. C’est ainsi que l’ensemble des frameworks fonctionne habituellement.

- `.NETStandard,Version=1.3` est un framework basé sur des packages. Il s’appuie sur des packages qui ciblent le framework pour définir et exposer des interfaces API selon le framework.

## <a name="package-based-frameworks"></a>Frameworks basés sur des packages

Il existe une relation réciproque entre les frameworks et les packages. La première partie consiste à définir les API accessibles à un framework donné, par exemple `netstandard1.3`. Les packages qui ciblent `netstandard1.3` (ou des frameworks compatibles tels que `netstandard1.0`) définissent les API disponibles pour `netstandard1.3`. On pourrait croire à première vue qu’il s’agit d’une définition circulaire, mais il n’en est rien. Étant « basée sur des packages », la définition d’API pour le framework est issue de packages. Le framework lui-même ne définit pas d’API.

La deuxième partie de la relation est la sélection de ressource. Les packages peuvent contenir des ressources pour plusieurs frameworks. Le framework est nécessaire pour déterminer quelle ressource sélectionner, par exemple `net46` ou `netstandard1.3`, pour une référence donnée à un ensemble de packages et/ou de métapackages. Il est important de choisir l’actif correct. Par exemple, il est peu probable qu’une ressource `net46` soit compatible avec le .NET Framework 4.0 ou .NET Core 1.0.

Cette relation est illustrée dans l’image suivante. L’*API* cible et définit le *framework*. Le *framework* est utilisé pour la *sélection de ressource*. La *ressource* vous fournit l’API.

![Composition d’un framework basé sur des packages](./media/packages/package-framework.png)

Les deux principaux frameworks basés sur des packages utilisés avec .NET Core sont les suivants :

- `netstandard`
- `netcoreapp`

### <a name="net-standard"></a>.NET Standard

Le cadre .NET Standard[(Target Framework Moniker](../standard/frameworks.md): `netstandard`) représente les API définies et construites au-dessus de [la norme .NET](../standard/net-standard.md). Les bibliothèques destinées à s’exécuter sur plusieurs runtimes doivent cibler ce framework. Ils seront pris en charge sur n’importe quel temps d’exécution .NET Standard-conforme, tels que .NET Core, .NET Framework, et Mono/Xamarin. Chacun de ces runtimes prend en charge un ensemble de versions .NET Standard, selon les API qu’ils implémentent.

Le `netstandard` cadre fait [`NETStandard.Library`](https://www.nuget.org/packages/NETStandard.Library) implicitement référence au métapackage. Par exemple, le fichier de projet MSBuild suivant indique que les cibles `netstandard1.6`du projet , qui fait référence au métapackage de la [ `NETStandard.Library` version 1.6.](https://www.nuget.org/packages/NETStandard.Library/1.6.0)

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.6</TargetFramework>
  </PropertyGroup>
</Project>
```

Toutefois, les références de framework et de métapackage dans le fichier projet ne doivent pas nécessairement correspondre et vous pouvez utiliser l’élément `<NetStandardImplicitPackageVersion>` dans votre fichier projet pour spécifier une version de framework inférieure à la version de métapackage. Par exemple, le fichier projet suivant est valide.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard1.3</TargetFramework>
    <NetStandardImplicitPackageVersion>1.6.0</NetStandardImplicitPackageVersion>
  </PropertyGroup>
</Project>
```

Il peut sembler étrange de cibler `netstandard1.3`, mais d’utiliser la version 1.6.0 de `NETStandard.Library`. Il s’agit d’un cas d’utilisation valide, car le métapackage maintient la prise en charge pour les anciennes versions de `netstandard`. Vous pouvez avoir procédé à une uniformisation sur la version 1.6.0 du métapackage et l’utiliser pour toutes vos bibliothèques, qui ciblent diverses versions de `netstandard`. Avec cette approche, vous avez seulement besoin de restaurer `NETStandard.Library` 1.6.0 et pas les versions antérieures.

L’inverse ne serait pas valide : le ciblage de `netstandard1.6` avec la version 1.3.0 de `NETStandard.Library`. Vous ne pouvez pas cibler un framework de version supérieure avec un métapackage de version inférieure, car ce dernier n’expose aucune ressource pour le framework de version supérieure. Le schéma de gestion de version des métapackages certifie que les métapackages correspondent à la version la plus récente du framework qu’ils décrivent. Grâce au schéma de gestion de version, la première version de `NETStandard.Library` est v1.6.0, étant donné qu’elle contient des ressources `netstandard1.6`. (Pour la symétrie avec l’exemple précédent, v1.3.0 est utilisé ici, mais il n’existe pas réellement.)

### <a name="net-core-application"></a>Application .NET Core

Le cadre .NET Core[(Target Framework Moniker](../standard/frameworks.md): `netcoreapp`) représente les forfaits et les API associés qui viennent avec la distribution .NET Core et le modèle d’application console qu’il fournit. Les applications .NET Core doivent utiliser ce framework, en raison du ciblage du modèle d’application console, tout comme les bibliothèques destinées à s’exécuter uniquement sur .NET Core. L’utilisation de ce framework contraint les applications et les bibliothèques à s’exécuter uniquement sur .NET Core.

Le métapackage `Microsoft.NETCore.App` cible le framework `netcoreapp`. Il donne accès à une soixantaine de bibliothèques, dont une quarantaine est fournie par le package `NETStandard.Library`, à laquelle s’ajoute une vingtaine de bibliothèques supplémentaires. Vous pouvez référencer des bibliothèques supplémentaires qui ciblent `netcoreapp` ou des frameworks compatibles, telles que `netstandard`, pour avoir accès à des API supplémentaires.

La plupart des bibliothèques supplémentaires fournies par `Microsoft.NETCore.App` ciblent aussi `netstandard`, vu que leurs dépendances sont satisfaites par d’autres bibliothèques `netstandard`. Cela signifie que les bibliothèques `netstandard` peuvent aussi référencer ces packages comme dépendances.
