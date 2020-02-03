---
title: Commande dotnet sln
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et répertorier des projets dans un fichier solution.
ms.date: 10/29/2019
ms.openlocfilehash: e344deaae0867202a79a3c38df48a2be8d4d7d13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733085"
---
# <a name="dotnet-sln"></a>dotnet sln

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nom

`dotnet sln` : Modifie un fichier solution .NET Core.

## <a name="synopsis"></a>Résumé

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet sln` offre un moyen pratique d’ajouter, de supprimer et de lister des projets dans un fichier solution.

Pour que la commande `dotnet sln` puisse être utilisée, le fichier solution doit déjà exister. Si vous devez en créer un, utilisez la commande [dotnet new](dotnet-new.md), comme dans l’exemple suivant :

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Fichier solution à utiliser. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel. S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.

## <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="commands"></a>Commands

### `add`

Ajoute un ou plusieurs projets au fichier solution.

#### <a name="synopsis"></a>Résumé

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH>
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Fichier solution à utiliser. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel. S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.

- **`PROJECT_PATH`**

  Chemin d’accès au projet à ajouter à la solution. Ajoutez plusieurs projets en en ajoutant un après l’autre en les séparant par des espaces. Les extensions de [modèle de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell UNIX/Linux sont traitées correctement par la commande `dotnet sln`.

#### <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--in-root`**

  Place les projets à la racine de la solution, plutôt que de créer un dossier de solution. Disponible à partir du kit SDK .NET Core 3.0.

- **`-s|--solution-folder`**

  Chemin d’accès du dossier de solution de destination auquel ajouter les projets. Disponible à partir du kit SDK .NET Core 3.0.

### `remove`

Supprime un ou plusieurs projets du fichier solution.

#### <a name="synopsis"></a>Résumé

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH>
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Fichier solution à utiliser. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel. S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.

- **`PROJECT_PATH`**

  Chemin d’accès au projet à supprimer de la solution. Pour supprimer plusieurs projets, ajoutez-en un après l’autre, en les séparant par des espaces. Les extensions de [modèle de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell UNIX/Linux sont traitées correctement par la commande `dotnet sln`.

#### <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

### `list`

Liste tous les projets dans un fichier solution.

#### <a name="synopsis"></a>Résumé

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Fichier solution à utiliser. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel. S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.

#### <a name="options"></a>Options

- **`-h|--help`**

  Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

- Ajouter un projet C# à une solution :

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj
  ```

- Supprimer un projet C# d’une solution :

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj
  ```

- Ajouter plusieurs projets C# à une solution :

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Supprimer plusieurs projets C# d’une solution :

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Ajouter plusieurs C# projets à une solution à l’aide d’un modèle globbing (UNIX/Linux uniquement) :

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Supprimer plusieurs C# projets d’une solution à l’aide d’un modèle globbing (UNIX/Linux uniquement) :

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
