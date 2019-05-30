---
title: Commande dotnet add package
description: La commande « dotnet add package » est une option pratique pour ajouter une référence de package NuGet à un projet.
ms.date: 04/24/2019
ms.openlocfilehash: 82f178026b46eb0237243b8ae49d17fbcc1af6ec
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959242"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Cet article s’applique à : ✓** SDK .NET Core 1.x et ultérieur

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Name

`dotnet add package` : Ajoute une référence de package à un fichier projet.

## <a name="synopsis"></a>Résumé

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>Description

La commande `dotnet add package` est une option pratique pour ajouter une référence de package à un fichier projet. Une fois que vous avez exécuté la commande, il existe un contrôle de compatibilité qui vérifie que le package est compatible avec les frameworks du projet. Si le résultat du contrôle est positif, un élément `<PackageReference>` est ajouté au fichier projet et la commande [dotnet restore](dotnet-restore.md) est exécutée.

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

Par exemple, l’ajout de `Newtonsoft.Json` à *ToDo.csproj* produit une sortie similaire à l’exemple suivant :

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

Le fichier *ToDo.csproj* contient à présent un élément [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) pour le package référencé.

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>Arguments

* **`PROJECT`**

  Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

* **`PACKAGE_NAME`**

  Référence de package à ajouter.

## <a name="options"></a>Options

* **`-f|--framework <FRAMEWORK>`**

  Ajoute une référence de package uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.

* **`-h|--help`**

  Affiche une aide brève pour la commande.

* **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (par exemple, s’authentifier). Disponible à partir du kit SDK .NET Core 2.1, version 2.1.400 (ou version ultérieure).

* **`-n|--no-restore`**

  Ajoute une référence de package sans effectuer d’aperçu de restauration ni de contrôle de compatibilité.

* **`--package-directory <PACKAGE_DIRECTORY>`**

  Répertoire où restaurer les packages.

* **`-s|--source <SOURCE>`**

  Source de package NuGet à utiliser pendant l’opération de restauration.

* **`-v|--version <VERSION>`**

  Version du package. Consultez [Contrôle de version du package NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).

## <a name="examples"></a>Exemples

* Ajouter un package NuGet `Newtonsoft.Json` à un projet :

  ```console
  dotnet add package Newtonsoft.Json
  ```

* Ajouter une version spécifique d’un package à un projet :

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* Ajouter un package à l’aide d’une source NuGet spécifique :

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```
