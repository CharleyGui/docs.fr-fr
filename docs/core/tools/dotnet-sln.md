---
title: Commande dotnet sln
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
ms.date: 02/14/2020
ms.openlocfilehash: b2455c04a46b2a10b8142d8ddc2d8129f2154b27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77543480"
---
# <a name="dotnet-sln"></a>dotnet sln

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet sln`- Listes ou modifications des projets dans un fichier de solution .NET Core.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command] [-h|--help]
```

## <a name="description"></a>Description

La `dotnet sln` commande fournit un moyen pratique d’énumérer et de modifier des projets dans un fichier de solution.

Pour que la commande `dotnet sln` puisse être utilisée, le fichier solution doit déjà exister. Si vous avez besoin d’en créer un, utilisez la nouvelle commande [dotnet,](dotnet-new.md) comme dans l’exemple suivant :

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Le fichier de solution à utiliser. Si cet argument est omis, la commande recherche l’annuaire actuel pour un. S’il ne trouve aucun fichier de solution ou plusieurs fichiers de solution, la commande échoue.

## <a name="options"></a>Options

- **`-h|--help`**

  Imprime une description de la façon d’utiliser la commande.

## <a name="commands"></a>Commandes

### `list`

Liste tous les projets dans un fichier solution.

#### <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Le fichier de solution à utiliser. Si cet argument est omis, la commande recherche l’annuaire actuel pour un. S’il ne trouve aucun fichier de solution ou plusieurs fichiers de solution, la commande échoue.

#### <a name="options"></a>Options

- **`-h|--help`**

  Imprime une description de la façon d’utiliser la commande.
  
### `add`

Ajoute un ou plusieurs projets au fichier de solution.

#### <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Le fichier de solution à utiliser. S’il n’est pas précisé, la commande recherche l’annuaire actuel pour un et échoue s’il ya plusieurs fichiers de solution.

- **`PROJECT_PATH`**

  Le chemin vers le projet ou les projets à ajouter à la solution. Les extensions [de motifs de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) `dotnet sln` de coquilles Unix/Linux sont traitées correctement par la commande.

#### <a name="options"></a>Options

- **`-h|--help`**

  Imprime une description de la façon d’utiliser la commande.

- **`--in-root`**

  Place les projets à la racine de la solution, plutôt que de créer un dossier de solution. Option disponible à partir du kit SDK .NET Core 3.0.

- **`-s|--solution-folder`**

  Le chemin de dossier de solution de destination pour ajouter les projets à. Option disponible à partir du kit SDK .NET Core 3.0.

### `remove`

Supprime un ou plusieurs projets du fichier solution.

#### <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Le fichier de solution à utiliser. Si elle n’est pas précisée, la commande recherche l’annuaire actuel pour un et échoue s’il existe plusieurs fichiers de solutions.

- **`PROJECT_PATH`**

  Le chemin vers le projet ou les projets à ajouter à la solution. Les extensions [de motifs de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) `dotnet sln` de coquilles Unix/Linux sont traitées correctement par la commande.

#### <a name="options"></a>Options

- **`-h|--help`**

  Imprime une description de la façon d’utiliser la commande.

## <a name="examples"></a>Exemples

- Énumérez les projets dans une solution :

  ```dotnetcli
  dotnet sln todo.sln list
  ```

- Ajouter un projet C# à une solution :

  ```dotnetcli
  dotnet sln add todo-app/todo-app.csproj
  ```

- Supprimer un projet C# d’une solution :

  ```dotnetcli
  dotnet sln remove todo-app/todo-app.csproj
  ```

- Ajoutez plusieurs projets C à la racine d’une solution :

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj --in-root
  ```

- Ajouter plusieurs projets C# à une solution :

  ```dotnetcli
  dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Supprimer plusieurs projets C# d’une solution :

  ```dotnetcli
  dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj
  ```

- Ajoutez plusieurs projets C à une solution à l’aide d’un modèle de glisse (Unix/Linux uniquement) :

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Supprimer plusieurs projets C d’une solution à l’aide d’un modèle de globbing (Unix/Linux uniquement) :

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```
