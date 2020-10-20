---
title: Analyser les dépendances pour porter le code sur .NET Core
description: Découvrez comment analyser les dépendances externes afin de porter votre projet de .NET Framework sur .NET Core.
author: cartermp
ms.date: 10/22/2019
ms.openlocfilehash: 430da45052e3953ab49f182b1773fc6d74bd2221
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223609"
---
# <a name="analyze-your-dependencies-to-port-code-to-net-core"></a>Analyser vos dépendances pour porter le code sur .NET Core

Pour porter votre code sur .NET Core ou .NET Standard, vous devez comprendre vos dépendances. Les dépendances externes sont les packages ou fichiers NuGet que `.dll` vous référencez dans votre projet, mais que vous ne créez pas vous-même.

## <a name="migrate-your-nuget-packages-to-packagereference"></a>Migrer vos packages NuGet vers `PackageReference`

.NET core utilise [PackageReference](/nuget/consume-packages/package-references-in-project-files) pour spécifier les dépendances de package. Si vous utilisez [packages.config](/nuget/reference/packages-config) pour spécifier vos packages dans votre projet, convertissez-les au `PackageReference` format, car `packages.config` n’est pas pris en charge dans .net core.

Pour savoir comment procéder à la migration, consultez l’article [migrer à partir de packages.config vers PackageReference](/nuget/reference/migrate-packages-config-to-package-reference) .

## <a name="upgrade-your-nuget-packages"></a>Mettre à niveau vos packages NuGet

Après avoir migré votre projet au `PackageReference` format, vérifiez si vos packages sont compatibles avec .net core.

Tout d’abord, mettez à niveau vos packages vers la dernière version que vous pouvez. Pour ce faire, vous pouvez utiliser l’interface utilisateur du gestionnaire de package NuGet dans Visual Studio. Il est probable que les versions plus récentes de vos dépendances de package soient déjà compatibles avec .NET Core.

## <a name="analyze-your-package-dependencies"></a>Analyser les dépendances de votre package

Si vous n’avez pas encore vérifié que vos dépendances de package converties et mises à niveau fonctionnent sur .NET Core, vous pouvez effectuer les opérations suivantes :

### <a name="analyze-nuget-packages-using-nugetorg"></a>Analyser les packages NuGet à l’aide de nuget.org

Vous pouvez voir les monikers du Framework cible (TFM) que chaque package prend en charge sur [NuGet.org](https://www.nuget.org/) sous la section **dépendances** de la page package.

Bien que l’utilisation du site soit une méthode plus simple pour vérifier la compatibilité, les informations de **dépendances** ne sont pas disponibles sur le site pour tous les packages.

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a>Analyser les packages NuGet à l’aide de NuGet Package Explorer

Un package NuGet est lui-même un ensemble de dossiers qui contiennent des assemblys spécifiques aux plateformes. Vérifiez s’il existe un dossier qui contient un assembly compatible à l’intérieur du package.

Le moyen le plus simple d’inspecter les dossiers de package NuGet consiste à utiliser l’outil [NuGet package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) . Après l’avoir installé, effectuez les étapes suivantes pour afficher les noms de dossiers :

1. Ouvrez NuGet Package Explorer.
2. Cliquez sur **Open package from online feed**.
3. Recherchez le nom du package.
4. Sélectionnez le nom du package dans les résultats de la recherche et cliquez sur **Open**.
5. Développez le dossier *lib* qui se trouve sur la droite et examinez les noms de dossiers.

Recherchez un dossier avec des noms en utilisant l’un des modèles suivants : `netstandardX.Y` ou `netcoreappX.Y` .

Ces valeurs sont les [monikers du Framework cible (TFM)](../../standard/frameworks.md) qui correspondent aux versions de [.NET standard](../../standard/net-standard.md), .net Core et des profils de bibliothèque de classes portables traditionnels qui sont compatibles avec .net core.

> [!IMPORTANT]
> Lorsque vous observez les TFM pris en charge par un package, notez que `netcoreapp*`, bien que compatible, ne s’applique qu’aux projets .NET Core, pas aux projets .NET Standard.
> Une bibliothèque qui cible uniquement `netcoreapp*` et pas `netstandard*` ne peut être consommée que par d’autres applications .NET Core.

## <a name="net-framework-compatibility-mode"></a>Mode de compatibilité du .NET Framework

Après avoir analysé les packages NuGet, vous constaterez peut-être qu’ils ne ciblent que le .NET Framework.

Le mode de compatibilité du .NET Framework a été introduit dans .NET Standard 2.0. Ce mode de compatibilité permet aux projets .NET Standard et .NET Core de référencer des bibliothèques .NET Framework. Le référencement de bibliothèques .NET Framework ne fonctionne pas pour tous les projets, par exemple si la bibliothèque utilise des API WPF (Windows Presentation Foundation), mais cela débloque de nombreux scénarios de portage.

Lorsque vous référencez des packages NuGet qui ciblent .NET Framework dans votre projet, par exemple [Huitian. powercollections](https://www.nuget.org/packages/Huitian.PowerCollections), vous recevez un avertissement de secours de package ([NU1701](/nuget/reference/errors-and-warnings/nu1701)) semblable à l’exemple suivant :

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

Cet avertissement s’affiche lorsque vous ajoutez le package et chaque fois que vous générez une build, pour vous rappeler de tester ce package avec votre projet. Si votre projet fonctionne comme prévu, vous pouvez supprimer cet avertissement en modifiant les propriétés du package dans Visual Studio ou en modifiant manuellement le fichier projet dans votre éditeur de code favori.

Pour supprimer l’avertissement en modifiant le fichier projet, recherchez l’entrée `PackageReference` du package pour lequel vous souhaitez supprimer l’avertissement, puis ajoutez l’attribut `NoWarn`. L’attribut `NoWarn` accepte une liste séparée par des virgules de tous les ID d’avertissement. L’exemple suivant montre comment supprimer l’avertissement `NU1701` pour le package `Huitian.PowerCollections` en modifiant votre fichier projet manuellement :

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

Pour plus d’informations sur la façon de supprimer les avertissements du compilateur dans Visual Studio, consultez [Suppression d’avertissements pour les packages NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppress-warnings-for-nuget-packages).

## <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a>Ce qu’il faut faire quand votre dépendance de package NuGet ne s’exécute pas sur .NET Core

Voici quelques actions possibles si un package NuGet dont vous dépendez ne s’exécute pas sur .NET Core :

- Si le projet est open source et hébergé à un endroit comme GitHub, vous pouvez demander aux développeurs de le modifier.
- Vous pouvez contacter l’auteur directement sur [NuGet.org](https://www.nuget.org/). Recherchez le package, puis cliquez sur **contacter les propriétaires** sur le côté gauche de la page du package.
- Vous pouvez rechercher un autre package qui s’exécute sur .NET Core et qui réalise la même tâche que le package que vous utilisez.
- Vous pouvez essayer d’écrire vous-même le code qui était exécuté par le package.
- Vous pouvez éliminer la dépendance du package en modifiant les fonctionnalités de votre application, au moins jusqu’à ce qu’une version compatible du package soit disponible.

N’oubliez pas que les personnes chargées de la maintenance des projets open source et les éditeurs de packages NuGet sont souvent des bénévoles. Ils offrent leur contribution car ils s’intéressent à un domaine donné, ils le font gratuitement et ont souvent un autre travail dans la journée. N’oubliez pas que lorsque vous les Contactez pour demander la prise en charge de .NET Core.

Si vous ne parvenez pas à résoudre votre problème avec l’une de ces options, vous devrez peut-être effectuer un portage vers .NET Core à une date ultérieure.

L’équipe .NET aimerait savoir quelles bibliothèques doivent être prioritairement prises en charge avec .NET Core. Vous pouvez nous envoyer un e-mail à l’adresse dotnet@microsoft.com afin de nous indiquer les bibliothèques que vous voudriez utiliser.

## <a name="analyze-dependencies-that-arent-nuget-packages"></a>Analyser des dépendances qui ne sont pas des packages NuGet

Vous avez peut-être une dépendance qui n’est pas un package NuGet, comme une DLL dans le système de fichiers. La seule façon de déterminer la portabilité de cette dépendance est d’exécuter l’outil [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport). L’outil analyse les assemblys qui ciblent le .NET Framework et identifie les API qui ne sont pas portables sur d’autres plateformes .NET telles que .NET Core. Vous pouvez exécuter cet outil en tant qu’application console ou qu’[extension Visual Studio](../../standard/analyzers/portability-analyzer.md).

## <a name="next-steps"></a>Étapes suivantes

>[!div class="nextstepaction"]
>[Bibliothèques de portage](libraries.md)
