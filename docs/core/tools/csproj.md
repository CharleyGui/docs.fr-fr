---
title: Ajouts au format csproj pour .NET Core
description: Découvrir les différences entre les fichiers csproj existants et les fichiers csproj .NET Core
ms.topic: reference
ms.date: 04/08/2019
ms.openlocfilehash: 3ef6a89a8cd4f811bcdd41b9c9bedbc45da78098
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91078214"
---
# <a name="additions-to-the-csproj-format-for-net-core"></a>Ajouts au format csproj pour .NET Core

Ce document décrit les modifications qui ont été ajoutées aux fichiers projet dans le cadre du passage de *project.json* à *csproj* et [MSBuild](https://github.com/Microsoft/MSBuild). Pour plus d’informations de référence ou syntaxiques générales sur les fichiers projet, consultez la documentation sur les [fichiers projet MSBuild](/visualstudio/msbuild/msbuild-project-file-schema-reference).

## <a name="implicit-package-references"></a>Références de package implicites

Les métapackages sont référencés implicitement en fonction du ou des frameworks cibles spécifiés dans la propriété `<TargetFramework>` ou `<TargetFrameworks>` de votre fichier projet. `<TargetFrameworks>` est ignoré si `<TargetFramework>` est spécifié, indépendamment de l’ordre.

```xml
 <PropertyGroup>
   <TargetFramework>netcoreapp3.1</TargetFramework>
 </PropertyGroup>
 ```

 ```xml
 <PropertyGroup>
   <TargetFrameworks>netcoreapp3.1;net462</TargetFrameworks>
 </PropertyGroup>
 ```

### <a name="recommendations"></a>Recommandations

Comme les métapackages `Microsoft.NETCore.App` ou `NETStandard.Library` sont implicitement référencés, voici les bonnes pratiques que nous recommandons :

- Quand vous ciblez .NET Core ou .NET Standard, n’incluez jamais de référence explicite aux métapackages `Microsoft.NETCore.App` ou `NETStandard.Library` via un élément `<PackageReference>` dans votre fichier projet.
- Si vous avez besoin d’une version spécifique du runtime quand vous ciblez .NET Core, vous devez utiliser la propriété `<RuntimeFrameworkVersion>` dans votre projet (par exemple, `1.0.4`) au lieu de référencer le métapackage.
  - Cela peut se produire si vous utilisez des [déploiements autonomes](../deploying/index.md#publish-self-contained) et que vous devez utiliser une version de correctif spécifique du runtime 1.0.0 LTS, par exemple.
- Si vous avez besoin d’une version spécifique du métapackage `NETStandard.Library` quand vous ciblez .NET Standard, vous pouvez utiliser la propriété `<NetStandardImplicitPackageVersion>` et définir la version dont vous avez besoin.
- Vous ne devez pas ajouter ni mettre à jour explicitement les références au métapackage `Microsoft.NETCore.App` ou `NETStandard.Library` dans les projets .NET Framework. Si une version de `NETStandard.Library` est nécessaire lors de l’utilisation d’un package NuGet basé sur .NET Standard, NuGet installe automatiquement cette version.

## <a name="implicit-version-for-some-package-references"></a>Version implicite pour certaines références de packages

La plupart des utilisations de [`<PackageReference>`](#packagereference) requièrent la définition de l' `Version` attribut pour spécifier la version de package NuGet à utiliser. Cependant, lorsque vous utilisez .NET Core 2.1 ou 2.2 et référencez [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app) ou [Microsoft.AspNetCore.All](/aspnet/core/fundamentals/metapackage), cet attribut n’est pas nécessaire. Le Kit SDK .NET Core peut sélectionner automatiquement la version des packages à utiliser.

### <a name="recommendation"></a>Recommandation

Lorsque vous référencez les packages `Microsoft.AspNetCore.App` ou `Microsoft.AspNetCore.All`, ne spécifiez pas leur version. Si une version est spécifiée, le Kit SDK risque de générer l’avertissement NETSDK1071. Pour résoudre cet avertissement, supprimez la version du package, comme dans l’exemple suivant :

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.AspNetCore.App" />
</ItemGroup>
```

> Problème connu : le Kit SDK .NET Core 2.1 prend uniquement en charge cette syntaxe si le projet utilise également Microsoft.NET.Sdk.Web. Ce problème est résolu dans le SDK .NET Core 2.2.

Ces références aux métapackages ASP.NET Core ont un comportement légèrement différent de celui de la plupart des packages NuGet normaux. Les [déploiements dépendant du framework](../deploying/index.md#publish-framework-dependent) d’applications qui utilisent ces métapackages tirent automatiquement parti du framework partagé ASP.NET Core. Quand vous utilisez les métapackages **aucune** des ressources des packages NuGet ASP.NET Core référencés n’est déployée avec l’application — le framework partagé ASP.NET Core contient ces ressources. Les ressources présentes dans le framework partagé sont optimisées pour la plateforme cible afin d’améliorer la vitesse de démarrage des applications. Pour plus d’informations sur le framework partagé, consultez [Empaquetage de la distribution de .NET Core](../distribution-packaging.md).

Si une version *est* spécifiée, elle est traitée comme la version *minimale* du framework partagé ASP.NET Core pour les déploiements dépendant du framework, et comme une version *exacte* pour les déploiements autonomes. Cela peut avoir les conséquences suivantes :

- Si la version d’ASP.NET Core installée sur le serveur est inférieure à la version spécifiée sur PackageReference, le processus .NET Core n’est pas lancé. Les mises à jour du métapackage sont souvent disponibles sur NuGet.org avant que des mises à jour soient publiées dans les environnements d’hébergement comme Azure. La mise à jour de la version sur PackageReference avec ASP.NET Core peut entraîner l’échec d’une application déployée.
- Si l’application est déployée comme un [déploiement autonome](../deploying/index.md#publish-self-contained), cette application ne peut pas contenir les dernières mises à jour de sécurité pour .NET Core. Quand une version n’est pas spécifiée, le Kit SDK peut inclure automatiquement la dernière version ASP.NET Core dans le déploiement autonome.

## <a name="default-compilation-includes-in-net-core-projects"></a>Inclusions de compilation par défaut dans les projets .NET Core

Dans le cadre du passage au format *csproj* dans les dernières versions du SDK, nous avons déplacé les inclusions et exclusions par défaut pour les éléments de compilation et les ressources incorporées dans les fichiers de propriétés du SDK. Cela signifie que vous n’avez plus besoin de spécifier ces éléments dans votre fichier projet.

La principale raison de cette modification est de réduire l’encombrement de votre fichier projet. Les valeurs par défaut qui sont présentes dans le SDK doivent couvrir la plupart des cas d’utilisation courants, il est donc inutile de les répéter dans chaque projet que vous créez. Il en résulte des fichiers projet moins volumineux qui sont beaucoup plus faciles à comprendre et à modifier à la main, si nécessaire.

Le tableau suivant montre les éléments et les modèles [Glob](https://en.wikipedia.org/wiki/Glob_(programming)) inclus et exclus dans le SDK :

| Élément           | Inclure Glob                              | Exclure Glob                                                  | Supprimer Glob              |
|-------------------|-------------------------------------------|---------------------------------------------------------------|----------------------------|
| Compiler           | \*\*/\*.cs (ou autres extensions de langage) | \*\*/\*.user ;  \*\*/\*.\*proj ;  \*\*/\*.sln ;  \*\*/\*.vssscc  | N/A                      |
| EmbeddedResource  | \*\*/\*.resx                              | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | N/A                      |
| None              | \*\*/\*                                   | \*\*/\*.user ; \*\*/\*.\*proj ; \*\*/\*.sln ; \*\*/\*.vssscc     | \*\*/\*.cs; \*\*/\*.resx   |

> [!NOTE]
> **Exclure Glob** exclut toujours les dossiers `./bin` et `./obj`, respectivement représentés par les propriétés MSBuild `$(BaseOutputPath)` et `$(BaseIntermediateOutputPath)`. Dans l’ensemble, toutes les exclusions sont représentées par `$(DefaultItemExcludes)`.

Si vous avez des modèles Glob dans votre projet et que vous essayez de le générer à l’aide du dernier SDK, vous obtenez l’erreur suivante :

> Des éléments de compilation en double ont été inclus. Le SDK .NET inclut des éléments de compilation de votre répertoire de projet par défaut. Vous pouvez supprimer ces éléments de votre fichier projet ou définir la propriété 'EnableDefaultCompileItems' sur 'false' si vous voulez explicitement les inclure dans votre fichier projet.

Pour contourner cette erreur, vous pouvez supprimer les éléments `Compile` explicites qui correspondent à ceux répertoriés dans le tableau précédent ou vous pouvez définir la propriété `<EnableDefaultCompileItems>` sur `false`, comme ceci :

```xml
<PropertyGroup>
    <EnableDefaultCompileItems>false</EnableDefaultCompileItems>
</PropertyGroup>
```

Le fait de définir cette propriété avec la valeur `false` désactive l’inclusion implicite, ce qui rétablit le comportement des SDK précédents dans lesquels vous deviez spécifier les globs par défaut dans votre projet.

Ce changement ne modifie pas le mécanisme principal des autres inclusions. Toutefois, si vous voulez, par exemple, spécifier certains fichiers à publier avec votre application, vous pouvez toujours utiliser les mécanismes connus dans *csproj* correspondants (par exemple, l’élément `<Content>`).

`<EnableDefaultCompileItems>` désactive uniquement les modèles Glob `Compile`, mais n’affecte pas les autres modèles Glob, comme le modèle Glob implicite `None`, qui s’applique également aux éléments \*.cs. Par conséquent, **l’Explorateur de solutions** continue d’afficher des éléments \*.cs dans le cadre du projet, inclus en tant qu’éléments `None`. De la même façon, vous pouvez affecter à `<EnableDefaultNoneItems>` la valeur false pour désactiver le modèle Glob implicite `None`, comme ceci :

```xml
<PropertyGroup>
    <EnableDefaultNoneItems>false</EnableDefaultNoneItems>
</PropertyGroup>
```

Pour désactiver **tous les modèles Glob implicites**, vous pouvez affecter à la propriété `<EnableDefaultItems>` la valeur `false` comme dans l’exemple suivant :

```xml
<PropertyGroup>
    <EnableDefaultItems>false</EnableDefaultItems>
</PropertyGroup>
```

## <a name="how-to-see-the-whole-project-as-msbuild-sees-it"></a>Comment afficher la totalité du projet tel qu’il est perçu par MSBuild ?

Même si ces modifications csproj simplifient considérablement les fichiers projet, vous pouvez souhaiter voir le projet entièrement développé tel qu’il est perçu par MSBuild une fois le kit SDK et ses cibles inclus. Prétraitez le projet avec [le commutateur `/pp`](/visualstudio/msbuild/msbuild-command-line-reference#preprocess) de la commande [`dotnet msbuild`](dotnet-msbuild.md), qui affiche les fichiers qui sont importés, leurs sources et leurs contributions à la build sans réellement générer le projet :

```dotnetcli
dotnet msbuild -pp:fullproject.xml
```

Si le projet comporte plusieurs frameworks cibles, les résultats de la commande ne doivent se concentrer que sur un seul d'entre eux en le spécifiant en tant que propriété MSBuild :

```dotnetcli
dotnet msbuild -p:TargetFramework=netcoreapp3.1 -pp:fullproject.xml
```

## <a name="additions"></a>Ajouts

### <a name="sdk-attribute"></a>Attribut Sdk

L’élément `<Project>` racine du fichier *.csproj* a un nouvel attribut nommé `Sdk`. `Sdk` spécifie le SDK à utiliser par le projet. Le SDK, comme le décrit le [document de superposition](cli-msbuild-architecture.md), est un ensemble de [tâches](/visualstudio/msbuild/msbuild-tasks) et de [cibles](/visualstudio/msbuild/msbuild-targets) MSBuild pouvant générer du code .NET Core. Les kits de développement logiciel (SDK) suivants sont disponibles pour .NET Core :

1. Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk`
2. Le SDK .NET Core avec l’ID `Microsoft.NET.Sdk.Web`
3. Le Kit SDK de la bibliothèque de classes .NET Core Razor avec l’ID `Microsoft.NET.Sdk.Razor`
4. Service Worker .NET Core avec l’ID de `Microsoft.NET.Sdk.Worker` (depuis .net core 3,0)
5. Le WinForms .NET Core et WPF avec l’ID de `Microsoft.NET.Sdk.WindowsDesktop` (depuis .net core 3,0)

Vous devez définir l’attribut `Sdk` sur un de ces ID pour l’élément `<Project>` afin d’utiliser les outils .NET Core et générer votre code.

### <a name="packagereference"></a>PackageReference

Un élément `<PackageReference>` spécifie une [dépendance NuGet dans le projet](/nuget/consume-packages/package-references-in-project-files). L’attribut `Include` spécifie l’ID du package.

```xml
<PackageReference Include="package-id" Version="" PrivateAssets="" IncludeAssets="" ExcludeAssets="" />
```

#### <a name="version"></a>Version

L’attribut obligatoire `Version` spécifie la version du package à restaurer. L’attribut respecte les règles du schéma de la [plage de versions NuGet](/nuget/concepts/package-versioning#version-ranges) . Le comportement par défaut est une version minimale et une correspondance inclusive. Par exemple, la spécification de `Version="1.2.3"` est équivalente à la notation NuGet `[1.2.3, )` et signifie que le package résolu aura la version 1.2.3 si elle est disponible ou supérieure dans le cas contraire.

#### <a name="includeassets-excludeassets-and-privateassets"></a>IncludeAssets, ExcludeAssets et PrivateAssets

L’attribut `IncludeAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être utilisées. Par défaut, toutes les ressources du package sont incluses.

L’attribut `ExcludeAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` ne doivent pas être utilisées.

L’attribut `PrivateAssets` spécifie quelles ressources appartenant au package spécifié par `<PackageReference>` doivent être utilisées, mais sans être reprises dans le projet suivant. Les ressources `Analyzers`, `Build` et `ContentFiles` sont par défaut privées en l’absence de cet attribut.

> [!NOTE]
> `PrivateAssets`équivaut au *project.jssur*l' / élément*xproj* `SuppressParent` .

Ces attributs peuvent contenir un ou plusieurs éléments de la liste suivante, séparés par le caractère point-virgule `;` le cas échéant :

- `Compile` : le contenu du dossier *lib* est disponible pour la compilation.
- `Runtime` : le contenu du dossier *Runtime* est distribué.
- `ContentFiles` : Le contenu du dossier *contentfiles* est utilisé.
- `Build` : les propriétés/cibles du dossier de *génération* sont utilisées.
- `Native` : le contenu des ressources natives est copié dans le dossier de *sortie* pour l’exécution.
- `Analyzers` : Les analyseurs sont utilisés.

Sinon, l’attribut peut contenir :

- `None` : Aucune ressource n’est utilisée.
- `All` : Toutes les ressources sont utilisées.

### <a name="dotnetclitoolreference"></a>DotNetCliToolReference

Un élément `<DotNetCliToolReference>` spécifie l’outil CLI que l’utilisateur souhaite restaurer dans le contexte du projet. Il constitue une alternative au nœud `tools` dans *project.json*.

```xml
<DotNetCliToolReference Include="<package-id>" Version="" />
```

Notez que `DotNetCliToolReference` est [désormais déconseillé](https://github.com/dotnet/announcements/issues/107) en faveur des [Outils locaux .net Core](./global-tools.md#install-a-local-tool).

#### <a name="version"></a>Version

`Version` spécifie la version du package à restaurer. L’attribut respecte les règles du schéma de [contrôle de version de NuGet](/nuget/create-packages/dependency-versions#version-ranges). Le comportement par défaut est une version minimale et une correspondance inclusive. Par exemple, la spécification de `Version="1.2.3"` est équivalente à la notation NuGet `[1.2.3, )` et signifie que le package résolu aura la version 1.2.3 si elle est disponible ou supérieure dans le cas contraire.

### <a name="runtimeidentifiers"></a>RuntimeIdentifiers

L’élément de propriété `<RuntimeIdentifiers>` vous permet de spécifier une liste délimitée par des points-virgules d’[identificateurs de runtime (RID)](../rid-catalog.md) pour le projet.
Les RID permettent de publier des déploiements autonomes.

```xml
<RuntimeIdentifiers>win10-x64;osx.10.11-x64;ubuntu.16.04-x64</RuntimeIdentifiers>
```

### <a name="runtimeidentifier"></a>RuntimeIdentifier

L’élément de propriété `<RuntimeIdentifier>` vous permet de spécifier un seul [identificateur de runtime (RID)](../rid-catalog.md) pour le projet. Le RID permet de publier un déploiement autonome.

```xml
<RuntimeIdentifier>ubuntu.16.04-x64</RuntimeIdentifier>
```

Utilisez plutôt `<RuntimeIdentifiers>` (au pluriel) si vous devez publier pour plusieurs runtimes. `<RuntimeIdentifier>` peut fournir des builds plus rapides quand un seul runtime est nécessaire.

### <a name="packagetargetfallback"></a>PackageTargetFallback

L’élément de propriété `<PackageTargetFallback>` vous permet de spécifier un jeu de cibles compatibles à utiliser lors de la restauration des packages. Il est conçu pour permettre aux packages qui utilisent le [moniker du framework cible](/nuget/schema/target-frameworks) dotnet de fonctionner avec les packages qui ne déclarent pas de moniker du framework cible dotnet. Si votre projet utilise le moniker du framework cible dotnet, tous les packages dont il dépend doivent également avoir un moniker du framework cible dotnet, sauf si vous ajoutez `<PackageTargetFallback>` à votre projet pour permettre aux plateformes autres que dotnet d’être compatibles avec dotnet.

L’exemple suivant fournit les solutions de secours pour toutes les cibles dans votre projet :

```xml
<PackageTargetFallback>
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

L’exemple suivant spécifie les solutions de secours uniquement pour la cible `netcoreapp3.1` :

```xml
<PackageTargetFallback Condition="'$(TargetFramework)'=='netcoreapp3.1'">
    $(PackageTargetFallback);portable-net45+win8+wpa81+wp8
</PackageTargetFallback >
```

## <a name="build-events"></a>Événements de build

La façon dont les événements pré-build et postérieurs à la génération sont spécifiés dans le fichier projet a changé. Les propriétés PreBuildEvent et PostBuildEvent ne sont pas recommandées dans le format de projet de type SDK, car les macros telles que $ (ProjectDir) ne sont pas résolues. Par exemple, le code suivant n’est plus pris en charge :

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"</PreBuildEvent>
</PropertyGroup>
```

Dans les projets de type SDK, utilisez une cible MSBuild nommée `PreBuild` ou `PostBuild` et définissez la `BeforeTargets` propriété pour `PreBuild` ou `AfterTargets` pour la propriété de `PostBuild` . Pour l’exemple précédent, utilisez le code suivant :

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>

<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
>Vous pouvez utiliser n’importe quel nom pour les cibles MSBuild, mais l’IDE de Visual Studio reconnaît `PreBuild` et `PostBuild` cible. nous vous recommandons donc d’utiliser ces noms pour pouvoir modifier les commandes dans l’IDE de Visual Studio.

## <a name="nuget-metadata-properties"></a>Propriétés de métadonnées NuGet

Avec le passage à MSBuild, nous avons déplacé les métadonnées d’entrée utilisées lors de la compression d’un package NuGet à partir de *project.jssur des* fichiers *. csproj* . Les entrées sont des propriétés MSBuild qui doivent donc être placées dans un groupe `<PropertyGroup>`. Voici la liste des propriétés utilisées comme entrées dans le processus de compression lors de l’utilisation de la `dotnet pack` commande ou de la `Pack` cible MSBuild qui fait partie du kit de développement logiciel (SDK) :

### <a name="ispackable"></a>IsPackable

Valeur booléenne qui spécifie si le projet peut être compressé. La valeur par défaut est `true`.

### <a name="packageversion"></a>PackageVersion

Spécifie la version du package obtenu. Accepte toutes les formes de la chaîne de version NuGet. La valeur par défaut est la valeur de `$(Version)`, autrement dit, de la propriété `Version` dans le projet.

### <a name="packageid"></a>PackageId

Spécifie le nom du package obtenu. Si non spécifié, l’opération `pack` utilise par défaut le `AssemblyName` ou le nom du répertoire comme nom du package.

### <a name="title"></a>Intitulé

Titre convivial du package, généralement utilisé dans les affichages de l’interface utilisateur comme sur nuget.org et dans le gestionnaire de package de Visual Studio. Si non spécifié, l’ID de package est utilisé à la place.

### <a name="authors"></a>Auteurs

Liste délimitée par des points-virgules des auteurs de packages, qui correspondent aux noms de profil sur nuget.org. Ceux-ci sont affichés dans la galerie NuGet sur nuget.org et sont utilisés pour faire référence croisée aux packages par les mêmes auteurs.

### <a name="packagedescription"></a>PackageDescription

Description longue du package pour l’affichage de l’interface utilisateur.

### <a name="description"></a>Description

Description longue de l'assembly. Si `PackageDescription` n’est pas spécifié, cette propriété est également utilisée comme description du package.

### <a name="copyright"></a>Copyright

Détails de copyright pour le package.

### <a name="packagerequirelicenseacceptance"></a>PackageRequireLicenseAcceptance

Valeur booléenne qui spécifie si le client doit inviter l’utilisateur à accepter la licence du package avant d’installer le package. La valeur par défaut est `false`.

### <a name="developmentdependency"></a>DevelopmentDependency

Valeur booléenne qui spécifie si le package est marqué en tant que dépendance de développement uniquement, ce qui empêche l’inclusion du package en tant que dépendance dans d’autres packages. Avec PackageReference (NuGet 4.8 +), cet indicateur signifie également que les éléments multimédias de compilation sont exclus de la compilation. Pour plus d'informations, voir [Prise en charge de DevelopmentDependency pour PackageReference](https://github.com/NuGet/Home/wiki/DevelopmentDependency-support-for-PackageReference).

### <a name="packagelicenseexpression"></a>PackageLicenseExpression

[Identificateur de licence SPDX](https://spdx.org/licenses/) ou expression. Par exemple : `Apache-2.0`.

Voici la liste complète des [identificateurs de licence SPDX](https://spdx.org/licenses/). NuGet.org n’accepte que les licences approuvées OSI et FSF avec une expression de type licence.

La syntaxe exacte des expressions de licence est décrite ci-dessous dans [ABNF](https://tools.ietf.org/html/rfc5234).

```abnf
license-id            = <short form license identifier from https://spdx.org/spdx-specification-21-web-version#h.luq9dgcle9mo>

license-exception-id  = <short form license exception identifier from https://spdx.org/spdx-specification-21-web-version#h.ruv3yl8g6czd>

simple-expression = license-id / license-id”+”

compound-expression =  1*1(simple-expression /
                simple-expression "WITH" license-exception-id /
                compound-expression "AND" compound-expression /
                compound-expression "OR" compound-expression ) /
                "(" compound-expression ")" )

license-expression =  1*1(simple-expression / compound-expression / UNLICENSED)
```

> [!NOTE]
> Il n’est pas possible de spécifier plusieurs des éléments suivants à la fois : `PackageLicenseExpression`, `PackageLicenseFile` et `PackageLicenseUrl`.

### <a name="packagelicensefile"></a>PackageLicenseFile

Chemin d’un fichier de licence du package, si la licence utilisée n’a pas été attribuée à un identificateur SPDX, ou il s’agit d’une licence personnalisée (sinon, `PackageLicenseExpression` est recommandé).

Remplace `PackageLicenseUrl` , ne peut pas être combiné avec `PackageLicenseExpression` et nécessite Visual Studio version 15.9.4 et le kit de développement logiciel (SDK) .NET 2.1.502 ou 2.2.101 ou version ultérieure.

Vérifiez que le fichier de licence est empaqueté en l’ajoutant explicitement au projet ; voici un exemple d’utilisation :

```xml
<PropertyGroup>
  <PackageLicenseFile>LICENSE.txt</PackageLicenseFile>
</PropertyGroup>
<ItemGroup>
  <None Include="licenses\LICENSE.txt" Pack="true" PackagePath="$(PackageLicenseFile)"/>
</ItemGroup>
```

### <a name="packagelicenseurl"></a>PackageLicenseUrl

URL de la licence applicable au package. (_Déconseillé depuis Visual Studio 15.9.4, le kit SDK .NET 2.1.502 et 2.2.101_)

### <a name="packageicon"></a>PackageIcon

Chemin d’accès à une image dans le package à utiliser comme icône de package. En savoir plus sur les [ `icon` métadonnées](/nuget/reference/nuspec#icon). [PackageIconUrl est déconseillé](/nuget/reference/msbuild-targets#packageiconurl) en faveur de PackageIcon.

### <a name="packagereleasenotes"></a>PackageReleaseNotes

Notes de publication du package.

### <a name="packagetags"></a>PackageTags

Liste de balises séparées par un point-virgule qui désigne le package.

### <a name="packageoutputpath"></a>PackageOutputPath

Détermine le chemin de sortie dans lequel le package compressé est déposé. La valeur par défaut est `$(OutputPath)`.

### <a name="includesymbols"></a>IncludeSymbols

Cette valeur booléenne indique si le package doit créer un package de symboles supplémentaire quand le projet est compressé. Le format du package de symboles est contrôlé par la propriété `SymbolPackageFormat`.

### <a name="symbolpackageformat"></a>SymbolPackageFormat

Spécifie le format du package de symboles. Si la valeur est « symbols.nupkg », un package de symboles hérité est créé avec une extension *.symbols.nupkg* contenant des fichiers PDB, DLL et d’autres fichiers de sortie. Si la valeur est « snupkg », un package de symboles snupkg est créé, contenant les fichiers PDB portables. La valeur par défaut est « symbols.nupkg ».

### <a name="includesource"></a>IncludeSource

Cette valeur booléenne indique si le processus de compression doit créer un package source. Le package source contient le code source de la bibliothèque ainsi que les fichiers PDB. Les fichiers sources sont placés dans le répertoire `src/ProjectName` dans le fichier de package obtenu.

### <a name="istool"></a>IsTool

Spécifie si tous les fichiers de sortie sont copiés dans le dossier *tools* au lieu du dossier *lib*. Cela est différent d’un `DotNetCliTool` , qui est spécifié en définissant `PackageType` dans le fichier *. csproj* .

### <a name="repositoryurl"></a>RepositoryUrl

Spécifie l’URL du dépôt où réside le code source du package et/ou à partir de laquelle il est généré.

### <a name="repositorytype"></a>RepositoryType

Spécifie le type de dépôt. La valeur par défaut est « git ».

### <a name="repositorybranch"></a>RepositoryBranch

Spécifie le nom de la branche source dans le référentiel. Lorsque le projet est empaqueté dans un package NuGet, il est ajouté aux métadonnées du package.

### <a name="repositorycommit"></a>RepositoryCommit

Validation ou ensemble de modifications de référentiel facultatif pour indiquer la source à partir de laquelle le package a été généré. `RepositoryUrl` doit également être spécifié pour que cette propriété soit incluse. Lorsque le projet est empaqueté dans un package NuGet, cette validation ou cet ensemble de modifications est ajouté aux métadonnées du package.

### <a name="nopackageanalysis"></a>NoPackageAnalysis

Spécifie que le pack ne doit pas exécuter d’analyse du package après sa génération.

### <a name="minclientversion"></a>MinClientVersion

Spécifie la version minimale du client NuGet qui peut installer ce package, appliquée par nuget.exe et le gestionnaire de package Visual Studio.

### <a name="includebuildoutput"></a>IncludeBuildOutput

Cette valeur booléenne spécifie si les assemblys de sortie de la génération doivent être empaquetés dans le fichier *. nupkg* ou non.

### <a name="includecontentinpack"></a>IncludeContentInPack

Cette valeur booléenne indique si tous les éléments qui ont un type `Content` sont automatiquement inclus dans le package obtenu. La valeur par défaut est `true`.

### <a name="buildoutputtargetfolder"></a>BuildOutputTargetFolder

Spécifie le dossier où placer les assemblys de sortie. Les assemblys de sortie (et les autres fichiers de sortie) sont copiés dans les dossiers de leur framework respectif.

### <a name="contenttargetfolders"></a>ContentTargetFolders

Cette propriété spécifie l’emplacement par défaut où placer tous les fichiers de contenu si `PackagePath` n’est pas spécifié pour eux. La valeur par défaut est « content;contentFiles ».

### <a name="nuspecfile"></a>NuspecFile

Chemin relatif ou absolu du fichier *.nuspec* utilisé pour la compression.

> [!NOTE]
> Si le fichier *.nuspec* est spécifié, il est utilisé **exclusivement** pour les informations de packaging et toutes les informations non utilisées dans les projets.

### <a name="nuspecbasepath"></a>NuspecBasePath

Chemin de base pour le fichier *.nuspec*.

### <a name="nuspecproperties"></a>NuspecProperties

Liste de paires clé=valeur séparées par un point-virgule.

## <a name="assemblyinfo-properties"></a>Propriétés AssemblyInfo

Les [attributs d’assembly](../../standard/assembly/set-attributes.md) qui figurent généralement dans un fichier *AssemblyInfo* désormais générés automatiquement à partir des propriétés.

### <a name="properties-per-attribute"></a>Propriétés par attribut

Comme indiqué dans le tableau suivant, chaque attribut a une propriété qui contrôle son contenu et un autre qui désactive sa génération :

| Attribut                                                      | Propriété               | Propriété permettant de désactiver                             |
|----------------------------------------------------------------|------------------------|-------------------------------------------------|
| <xref:System.Reflection.AssemblyCompanyAttribute>              | `Company`              | `GenerateAssemblyCompanyAttribute`              |
| <xref:System.Reflection.AssemblyConfigurationAttribute>        | `Configuration`        | `GenerateAssemblyConfigurationAttribute`        |
| <xref:System.Reflection.AssemblyCopyrightAttribute>            | `Copyright`            | `GenerateAssemblyCopyrightAttribute`            |
| <xref:System.Reflection.AssemblyDescriptionAttribute>          | `Description`          | `GenerateAssemblyDescriptionAttribute`          |
| <xref:System.Reflection.AssemblyFileVersionAttribute>          | `FileVersion`          | `GenerateAssemblyFileVersionAttribute`          |
| <xref:System.Reflection.AssemblyInformationalVersionAttribute> | `InformationalVersion` | `GenerateAssemblyInformationalVersionAttribute` |
| <xref:System.Reflection.AssemblyProductAttribute>              | `Product`              | `GenerateAssemblyProductAttribute`              |
| <xref:System.Reflection.AssemblyTitleAttribute>                | `AssemblyTitle`        | `GenerateAssemblyTitleAttribute`                |
| <xref:System.Reflection.AssemblyVersionAttribute>              | `AssemblyVersion`      | `GenerateAssemblyVersionAttribute`              |
| <xref:System.Resources.NeutralResourcesLanguageAttribute>      | `NeutralLanguage`      | `GenerateNeutralResourcesLanguageAttribute`     |

Remarques :

- Le comportement par défaut de `AssemblyVersion` et `FileVersion` consiste à prendre la valeur de `$(Version)` sans suffixe. Par exemple, si `$(Version)` est `1.2.3-beta.4`, alors la valeur serait `1.2.3`.
- `InformationalVersion` utilise par défaut la valeur de `$(Version)`.
- `$(SourceRevisionId)` est ajouté à `InformationalVersion` si la propriété est présente. Cela peut être désactivé à l’aide de `IncludeSourceRevisionInInformationalVersion`.
- Les propriétés `Copyright` et `Description` sont également utilisées pour les métadonnées NuGet.
- `Configuration` est partagé avec le processus de génération et défini par le biais du paramètre `--configuration` des commandes `dotnet`.

### <a name="generateassemblyinfo"></a>GenerateAssemblyInfo

Valeur booléenne qui active ou désactive la génération AssemblyInfo. La valeur par défaut est `true`.

### <a name="generatedassemblyinfofile"></a>GeneratedAssemblyInfoFile

Chemin d’accès du fichier d’informations sur l’assembly généré. Utilise par défaut un fichier dans le répertoire `$(IntermediateOutputPath)` (obj).
