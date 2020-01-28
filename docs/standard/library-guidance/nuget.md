---
title: Bibliothèques NuGet et .NET
description: Meilleures pratiques recommandées pour l’empaquetage avec des bibliothèques NuGet pour .NET.
ms.date: 01/15/2019
ms.openlocfilehash: f1e8d39fe2988f11ce7fd351a4d6bee6d322f2b5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731374"
---
# <a name="nuget"></a>NuGet

Gestionnaire de packages pour l’écosystème .NET, NuGet est le principal moyen permettant aux développeurs de découvrir et d’obtenir des bibliothèques .NET open source. [NuGet.org](https://www.nuget.org/), un service gratuit fourni par Microsoft pour l’hébergement de packages NuGet, est l’hôte principal pour les packages NuGet publiques, mais vous pouvez publier dans des services NuGet personnalisés tels que [MyGet](https://www.myget.org/) et [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).

![NuGet](./media/nuget/nuget-logo.png "NuGet")

## <a name="create-a-nuget-package"></a>Créer un package NuGet

Un package NuGet (`*.nupkg`) est un fichier zip qui contient des assemblys .NET et les métadonnées associées.

Il existe deux façons principales de créer un package NuGet. La plus récente et recommandée consiste à créer un package à partir d’un projet de style SDK (fichier projet dont le contenu commence par `<Project Sdk="Microsoft.NET.Sdk">`). Les assemblys et cibles sont automatiquement ajoutés au package et les métadonnées restantes sont ajoutées au fichier MSBuild, notamment le nom du package et le numéro de version. La compilation avec la commande [`dotnet pack`](../../core/tools/dotnet-pack.md) génère un fichier `*.nupkg` au lieu d’assemblys.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

L’ancienne méthode de création d’un package NuGet utilise un fichier `*.nuspec` et l’outil de ligne de commande `nuget.exe`. Un fichier nuspec vous donne plus de contrôle, mais vous devez spécifier soigneusement les assemblys et les cibles à inclure dans le package NuGet final. Il est facile de commettre une erreur ou d’oublier de mettre à jour le fichier nuspec lors des modifications. Un fichier nuspec offre l’avantage de vous permettre de créer des packages NuGet pour les infrastructures qui ne gèrent pas encore un fichier projet de style SDK.

✔️ ENVISAGER d’utiliser un fichier projet de type SDK pour créer le package NuGet.

## <a name="package-dependencies"></a>Dépendances de package

Les dépendances de package NuGet sont traitées en détail dans l’article sur les [dépendances](./dependencies.md).

## <a name="important-nuget-package-metadata"></a>Métadonnées importantes de package NuGet

Un package NuGet prend en charge plusieurs [propriétés de métadonnées](/nuget/reference/nuspec). Le tableau suivant indique les principales métadonnées que chaque package sur NuGet.org doit fournir :

| Nom de la propriété MSBuild              | Nom nuspec              | Description  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | Identificateur du package. Un préfixe de l’identificateur peut être réservé s’il répond aux [critères](/nuget/reference/id-prefix-reservation). |
| `PackageVersion`                   | `version`                  | Version du package NuGet. Pour plus d’informations, consultez [Version du package NuGet](./versioning.md#nuget-package-version).             |
| `Title`                            | `title`                    | Un titre convivial du package. Ce champ est défini sur `PackageId` par défaut.             |
| `Description`                      | `description`              | Longue description du package affiché dans l’interface utilisateur.             |
| `Authors`                          | `authors`                  | Liste séparée par des virgules des auteurs de packages, qui correspondent aux noms de profil sur nuget.org.             |
| `PackageTags`                      | `tags`                     | Liste délimitée par des espaces des balises et mots clés qui décrivent le package. Les balises sont utilisées lors de la recherche des packages.             |
| `PackageIconUrl`                   | `iconUrl`                  | URL d’une image à utiliser comme icône pour le package. L’URL doit être de type HTTPS et l’image doit être au format 64 x 64, avec un arrière-plan transparent.             |
| `PackageProjectUrl`                | `projectUrl`               | Une URL pour la page d'accueil du projet ou le référentiel source.             |
| `PackageLicenseExpression`         | `license`                  | L’[identificateur SPDX](https://spdx.org/licenses/) de la licence du projet. Seules des licences OSI et FSF approuvées peuvent utiliser un identificateur. Les autres licences doivent utiliser `PackageLicenseFile`. En savoir plus sur les [`license`métadonnées](/nuget/reference/nuspec#license). |

> [!IMPORTANT]
> Par défaut, un projet sans licence possède un [copyright exclusif](https://choosealicense.com/no-permission/), ce qui empêche légalement d’autres personnes de l’utiliser.

✔️ ENVISAGER de choisir un nom de package NuGet avec un préfixe qui répond aux [critères](/nuget/reference/id-prefix-reservation)de réservation de préfixe de NuGet.

✔️ Utilisez une href HTTPs sur l’icône de votre package.

> Des sites comme NuGet.org fonctionnent avec HTTPS et l’affichage d’une image non-HTTPS créera un avertissement de contenu mixte.

✔️ Utilisez une image d’icône de package qui est 64x64 et qui possède un arrière-plan transparent pour un meilleur affichage des résultats.

✔️ envisagez de configurer le [lien source](./sourcelink.md) pour ajouter les métadonnées du contrôle de code source à vos assemblys et au package NuGet.

> Source Link ajoute automatiquement des métadonnées `RepositoryUrl` et `RepositoryType` au package NuGet. Source Link ajoute également des informations sur le code source exact à partir duquel le package a été créé. Par exemple, le hachage de validation est ajouté comme métadonnées à un package créé à partir d’un dépôt Git.

## <a name="pre-release-packages"></a>Packages de préversion

Les packages NuGet avec un suffixe de version sont considérés comme des [préversions](/nuget/create-packages/prerelease-packages). Par défaut, l’interface utilisateur du Gestionnaire de package NuGet affiche des versions stables, sauf si un utilisateur choisit des packages en préversion, ce qui rend ces packages en préversion idéaux pour les tests utilisateur limités.

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> Un package stable ne peut pas dépendre d’un package en préversion. Votre package doit être en préversion ou dépendre d’une version stable antérieure.

![Dépendance du package de préversion NuGet](./media/nuget/nuget-prerelease-package.png "Dépendance du package de préversion NuGet")

✔️ publier un package de préversion lors du test, de l’aperçu ou de l’expérimentation.

✔️ publiez un package stable quand il est prêt afin que d’autres packages stables puissent y faire référence.

## <a name="symbol-packages"></a>Packages de symboles

Les fichiers de symboles (`*.pdb`) sont produites par le compilateur .NET en même temps que les assemblys. Comme les fichiers de symboles mappent les emplacements d’exécution au code source d’origine, vous pouvez parcourir le code source en cours d’exécution à l’aide d’un débogueur. NuGet prend en charge la [génération d’un package de symboles distinct (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) contenant des fichiers de symboles ainsi que le package principal contenant les assemblys .NET. Dans le concept des packages de symboles, ces packages sont hébergés sur un serveur de symboles et téléchargés à la demande uniquement par un outil tel que Visual Studio.

NuGet.org héberge son propre [dépôt de serveur de symboles](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server). Les développeurs peuvent utiliser les symboles publiés sur le serveur de symboles NuGet.org en ajoutant `https://symbols.nuget.org/download/symbols` à leurs [sources de symboles dans Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).

> [!IMPORTANT]
> Le serveur de symboles NuGet.org prend uniquement en charge les nouveaux [fichiers de symboles portables](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) créés par les projets de style SDK.
>
> Pour utiliser le serveur de symboles NuGet.org lors du débogage d’une bibliothèque .NET, les développeurs doivent disposer de Visual Studio 2017 version 15,9 ou ultérieure.

Une alternative à la création d’un package de symboles est l’incorporation de fichiers de symboles dans le package NuGet principal. Le package NuGet principal sera plus important, mais les fichiers de symboles incorporés signifient que les développeurs n’ont pas besoin de configurer le serveur de symboles NuGet.org. Si vous générez votre package NuGet à l’aide d’un projet de style SDK, vous pouvez incorporer les fichiers de symboles en définissant la propriété `AllowedOutputExtensionsInPackageBuildOutputFolder` :

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

L’inconvénient des fichiers de symboles incorporés est qu’ils augmentent la taille du package d’environ 30 % pour les bibliothèques .NET compilées à l’aide de projets de style SDK. Si la taille de package est un problème, vous devez publier les symboles dans un package de symboles à la place.

✔️ envisagez de publier des symboles en tant que package de symboles (`*.snupkg`) dans NuGet.org

> Les packages de symboles (`*.snupkg`) permettent aux développeurs d’effectuer un débogage à la demande sans gonfler inutilement la taille du package principal ni impacter les performances de restauration pour les utilisateurs qui ne comptent pas déboguer le package NuGet.
>
> L’inconvénient est que les utilisateurs peuvent avoir besoin de rechercher et de configurer le serveur de symboles NuGet dans leur IDE (en tant que programme d’installation unique) pour obtenir des fichiers de symboles. Visual Studio 2019 version 16,1 a ajouté le serveur de symboles NuGet. org à la liste des serveurs de symboles par défaut.

>[!div class="step-by-step"]
>[Précédent](strong-naming.md)
>[Suivant](dependencies.md)
