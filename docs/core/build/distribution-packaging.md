---
title: Empaquetage de la distribution de .NET Core
description: Découvrez comment empaqueter, nommer et versionner .NET Core pour la distribution.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394161"
---
# <a name="net-core-distribution-packaging"></a>Empaquetage de la distribution de .NET Core

.NET Core est disponible sur de plus en plus de plateformes ; il est donc utile de savoir comment l’empaqueter, le nommer et le versionner. De cette manière, les chargés de maintenance des packages pourront garantir une expérience cohérente quelle que soit la plateforme choisie par les utilisateurs pour exécuter .NET. Cet article est utile pour les utilisateurs qui :

- Essaient de générer .NET Core à partir de la source.
- Souhaitent apporter des modifications à l’interface CLI .NET Core susceptibles d’impacter la disposition résultante ou les packages générés.

## <a name="disk-layout"></a>Disposition du disque

Une fois installé, .NET Core est constitué de plusieurs composants qui sont disposés comme suit dans le système de fichiers :

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- (1) **dotnet** L’hôte (également appelé « muxer ») a deux rôles distincts : activer un runtime pour lancer une application, et un SDK pour lui distribuer des commandes. L’hôte est un fichier exécutable natif (`dotnet.exe`).

Alors qu’il n’y a qu’un seul hôte, la plupart des autres composants sont dans des répertoires avec version (2,3,5,6). Cela signifie que plusieurs versions peuvent être présentes sur le système, car elles sont installées côte à côte.

- (2) **host/fxr/\<version fxr>** contient la logique de résolution du framework utilisé par l’hôte. L’hôte utilise la dernière version de hostfxr qui est installée. hostfxr est chargé de sélectionner le runtime approprié lors de l’exécution d’une application .NET Core. Par exemple, une application générée pour .NET Core 2.0.0 utilise le runtime 2.0.5 quand il est disponible. De même, hostfxr sélectionne le SDK approprié au cours du développement.

- (3) **sdk/\<version sdk>** Le SDK (également appelé « outils ») est un ensemble d’outils gérés servant à écrire et à générer des bibliothèques et des applications .NET Core. Le SDK inclut, entre autres, l’interface de ligne de commande de .NET Core (CLI), les compilateurs de langages managés, MSBuild, les cibles et les tâches de génération associées, NuGet et de nouveaux modèles de projet.

- (4) **sdk/NuGetFallbackFolder** contient un cache de packages NuGet utilisés par un SDK pendant l’opération de restauration, comme lors de l’exécution de `dotnet restore` ou `dotnet build /t:Restore`. Ce dossier est utilisé uniquement avant .NET Core 3,0. Il ne peut pas être généré à partir de la source, car il contient `nuget.org`des éléments binaires prégénérés à partir de.

Le dossier **shared** contient des frameworks. Un framework partagé fournit un ensemble de bibliothèques à un emplacement central, ce qui permet à différentes applications de les utiliser.

- (5) **shared/Microsoft.NETCore.App/\<version runtime>** Ce framework contient le runtime .NET Core et des bibliothèques managées qui le prennent en charge.

- (6) **Shared/Microsoft. AspNetCore. { Application, All}/\<aspnetcore version >** contient les bibliothèques ASP.net core. Les bibliothèques sous `Microsoft.AspNetCore.App` sont développées et prises en charge dans le cadre du projet .NET Core. Les bibliothèques sous `Microsoft.AspNetCore.All` sont un sur-ensemble qui contient également des bibliothèques de tiers.

- (7) **Shared/Microsoft. Desktop. app\</App Desktop version >** contient les bibliothèques de bureau Windows. Cela n’est pas inclus sur les plateformes non-Windows.

- (8) **LICENSE.txt,ThirdPartyNotices.txt** sont la licence .NET Core et les licences des bibliothèques de tiers utilisées dans .NET Core, respectivement.

- (9, 10) **dotnet.1.gz, dotnet** `dotnet.1.gz` est la page du manuel de dotnet. `dotnet` est un lien symbolique vers l’hôte dotnet (1). Ces fichiers sont installés aux emplacements habituels pour l’intégration du système.

- (11, 12) **Microsoft. Netcore. app. ref, Microsoft. AspNetCore. app. Ref** décrivent l’API d' `x.y` une version de .net Core et ASP.net Core respectivement. Ces packs sont utilisés lors de la compilation de ces versions cibles.

- (13) **Microsoft. Netcore. app. Host.\< RID >** contient un binaire natif pour la `rid`plateforme. Ce binaire est un modèle lors de la compilation d’une application .NET Core en binaire natif pour cette plateforme.

- (14) **Microsoft. WindowsDesktop. app. Ref** décrit l’API de `x.y` la version des applications de bureau Windows. Ces fichiers sont utilisés lors de la compilation pour cette cible. Cela n’est pas fourni sur les plateformes non-Windows.

- (15) **netstandard. Library. Ref** décrit l’API netstandard `x.y` . Ces fichiers sont utilisés lors de la compilation pour cette cible.

- (16) **/etc/dotnet/install_location** est un fichier qui contient le chemin d’accès complet au dossier qui contient `dotnet` le fichier binaire de l’hôte. Le chemin d’accès peut se terminer par un saut de ligne. Il n’est pas nécessaire d’ajouter ce fichier quand la racine `/usr/share/dotnet`est.

- (17) les **modèles** contiennent les modèles utilisés par le kit de développement logiciel (SDK). Par exemple, `dotnet new` recherche des modèles de projet ici.

## <a name="recommended-packages"></a>Packages recommandés

Le contrôle de version de .NET Core est basé sur les numéros de version `[major].[minor]` du composant runtime.
La version du SDK utilise les mêmes numéros `[major].[minor]` et a un `[patch]` indépendant qui combine la sémantique des fonctionnalités et des correctifs pour le SDK.
Par exemple :  SDK version 2.2.302 est la deuxième version du correctif de la troisième version des fonctionnalités du SDK qui prend en charge le runtime 2.2. Pour plus d’informations sur le fonctionnement de la gestion des versions, consultez [Vue d’ensemble de la gestion des versions .NET Core](../versions/index.md).

Le nom de certains packages inclut une partie du numéro de version. Cela vous permet d’installer une version spécifique.
Le reste de la version n’est pas inclus dans le nom de version. Ceci permet au Gestionnaire de package du système d’exploitation de mettre à jour les packages (par exemple d’installer automatiquement des correctifs de sécurité). Les gestionnaires de packages pris en charge sont spécifiques de Linux.

La liste suivante répertorie les packages recommandés :

- `dotnet-sdk-[major].[minor]`-Installe le dernier Kit de développement logiciel (SDK) pour un Runtime spécifique
  - **Version :** \<version du runtime >
  - **Exemple :** dotnet-sdk-2,1
  - **Comprend** (3),(4)
  - **Dépendances :** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`

- `aspnetcore-runtime-[major].[minor]`-Installe un runtime ASP.NET Core spécifique
  - **Version :** \<version du runtime aspnetcore >
  - **Exemple :** aspnetcore-runtime-2,1
  - **Comprend** (6)
  - **Dépendances :** `dotnet-runtime-[major].[minor]`

- `dotnet-runtime-deps-[major].[minor]` _(Facultatif)_ -installe les dépendances pour l’exécution des applications autonomes
  - **Version :** \<version du runtime >
  - **Exemple :** dotnet-Runtime-deps-2,1
  - **Dépendances :** _dépendances spécifiques à distribution_

- `dotnet-runtime-[major].[minor]`-Installe un Runtime spécifique
  - **Version :** \<version du runtime >
  - **Exemple :** dotnet-runtime-2,1
  - **Comprend** (5)
  - **Dépendances :** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`

- `dotnet-hostfxr`-dépendance
  - **Version :** \<version du runtime >
  - **Exemple :** dotnet-hostfxr
  - **Comprend**  (2)
  - **Dépendances :** `host:<runtime version>+`

- `dotnet-host`-dépendance
  - **Version :** \<version du runtime >
  - **Exemple :** dotnet-Host
  - **Comprend** (1), (8), (9), (10), (16)

- `dotnet-apphost-pack-[major].[minor]`-dépendance
  - **Version :** \<version du runtime >
  - **Comprend** 12

- `dotnet-targeting-pack-[major].[minor]`-Permet de cibler un Runtime qui n’est pas le plus récent
  - **Version :** \<version du runtime >
  - **Comprend** douze

- `aspnetcore-targeting-pack-[major].[minor]`-Permet de cibler un Runtime qui n’est pas le plus récent
  - **Version :** \<version du runtime aspnetcore >
  - **Comprend** 11

- `netstandard-targeting-pack-[major].[minor]`-Permet de cibler une version netstandard
  - **Version :** \<version du kit de développement logiciel >
  - **Comprend** 4,5

- `dotnet-templates-[major].[minor]`
  - **Version :** \<version du kit de développement logiciel >
  - **Comprend** 4,5

Le `dotnet-runtime-deps-[major].[minor]` nécessite de comprendre les _dépendances spécifiques à distribution_. Étant donné que le système de génération distribution peut être en mesure de le dériver automatiquement, le package est facultatif, auquel cas ces dépendances `dotnet-runtime-[major].[minor]` sont ajoutées directement au package.

Lorsque le contenu du package se trouve dans un dossier avec version, `[major].[minor]` le nom du package correspond au nom du dossier avec version. Pour tous les packages, à `netstandard-targeting-pack-[major].[minor]`l’exception de, cela correspond également à la version .net core.

Les dépendances entre les packages doivent utiliser une version _égale ou supérieure à_ la version requise. Par exemple, `dotnet-sdk-2.2:2.2.401` nécessite `aspnetcore-runtime-2.2 >= 2.2.6`. Cela permet à l’utilisateur de mettre à niveau son installation via un package racine (par exemple `dnf update dotnet-sdk-2.2`,).

La plupart des distributions nécessitent que tous les artefacts soient générés à partir de la source. Ceci a un certain impact sur les packages :

- Les bibliothèques de tiers sous `shared/Microsoft.AspNetCore.All` ne peuvent pas être facilement générées à partir de la source. Ce dossier est donc omis du package `aspnetcore-runtime`.

- `NuGetFallbackFolder` est rempli avec des artefacts binaires provenant de `nuget.org`. Il doit rester vide.

Plusieurs packages `dotnet-sdk` peuvent fournir les mêmes fichiers pour le `NuGetFallbackFolder`. Pour éviter des problèmes avec le Gestionnaire de package, ces fichiers doivent être identiques (somme de contrôle, date de modification, etc.).

## <a name="building-packages"></a>Génération des packages

Le référentiel [dotnet/source-build](https://github.com/dotnet/source-build) fournit des instructions qui expliquent comment créer un tarball source du Kit SDK .NET Core et de tous ses composants. La sortie du dépôt de builds sources correspond à la disposition décrite dans la première section de cet article.
