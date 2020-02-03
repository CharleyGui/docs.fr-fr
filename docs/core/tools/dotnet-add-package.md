---
title: Commande dotnet add package
description: La commande « dotnet add package » est une option pratique pour ajouter une référence de package NuGet à un projet.
ms.date: 06/26/2019
ms.openlocfilehash: 210dcf0efe06672264ebfa297589bdb387591a42
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733331"
---
# <a name="dotnet-add-package"></a>dotnet add package

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nom

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

- **`PROJECT`**

  Spécifie le nom du fichier projet. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel.

- **`PACKAGE_NAME`**

  Référence de package à ajouter.

## <a name="options"></a>Options

- **`-f|--framework <FRAMEWORK>`**

  Ajoute une référence de package uniquement quand vous ciblez un [framework](../../standard/frameworks.md) spécifique.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple). Disponible à partir du kit SDK .NET Core 2.1, version 2.1.400 (ou version ultérieure).

- **`-n|--no-restore`**

  Ajoute une référence de package sans effectuer d’aperçu de restauration ni de contrôle de compatibilité.

- **`--package-directory <PACKAGE_DIRECTORY>`**

  Répertoire où restaurer les packages. L’emplacement de restauration de package par défaut est `%userprofile%\.nuget\packages` sur Windows, et `~/.nuget/packages` sur macOS et Linux. Pour plus d’informations, consultez [Gérer les dossiers de packages globaux, les dossiers de cache et les dossiers temporaires dans NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders).

- **`-s|--source <SOURCE>`**

  Source de package NuGet à utiliser pendant l’opération de restauration.

- **`-v|--version <VERSION>`**

  Version du package. Consultez [Contrôle de version du package NuGet](https://docs.microsoft.com/nuget/reference/package-versioning).

## <a name="examples"></a>Exemples

- Ajouter un package NuGet `Newtonsoft.Json` à un projet :

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- Ajouter une version spécifique d’un package à un projet :

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- Ajouter un package à l’aide d’une source NuGet spécifique :

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>Voir aussi

- [Gestion des dossiers de packages globaux, des dossiers de cache et des dossiers temporaires dans NuGet](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [Gestion des versions des packages NuGet](https://docs.microsoft.com/nuget/reference/package-versioning)
