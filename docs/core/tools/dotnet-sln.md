---
title: Commande dotnet sln
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
ms.date: 12/07/2020
ms.openlocfilehash: 480634550f6fa1983bb46f51b439dc8a686ead3c
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851694"
---
# <a name="dotnet-sln"></a>dotnet sln

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Nom

`dotnet sln` -Répertorie ou modifie les projets dans un fichier solution .NET.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet sln [<SOLUTION_FILE>] [command]

dotnet sln [command] -h|--help
```

## <a name="description"></a>Description

La `dotnet sln` commande offre un moyen pratique de répertorier et de modifier des projets dans un fichier solution.

Pour que la commande `dotnet sln` puisse être utilisée, le fichier solution doit déjà exister. Si vous devez en créer un, utilisez la commande [dotnet New](dotnet-new.md) , comme dans l’exemple suivant :

```dotnetcli
dotnet new sln
```

## <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Fichier solution à utiliser. Si cet argument est omis, la commande recherche un dans le répertoire actif. S’il ne trouve aucun fichier solution ou plusieurs fichiers solution, la commande échoue.

## <a name="options"></a>Options

- **`-h|--help`**

  Imprime une description de l’utilisation de la commande.

## <a name="commands"></a>Commandes

### `list`

Liste tous les projets dans un fichier solution.

#### <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet sln list [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Fichier solution à utiliser. Si cet argument est omis, la commande recherche un dans le répertoire actif. S’il ne trouve aucun fichier solution ou plusieurs fichiers solution, la commande échoue.

#### <a name="options"></a>Options

- **`-h|--help`**

  Imprime une description de l’utilisation de la commande.
  
### `add`

Ajoute un ou plusieurs projets au fichier solution.

#### <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet sln [<SOLUTION_FILE>] add [--in-root] [-s|--solution-folder <PATH>] <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln add [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Fichier solution à utiliser. Si elle n’est pas spécifiée, la commande recherche un répertoire actif et échoue s’il existe plusieurs fichiers solution.

- **`PROJECT_PATH`**

  Chemin d’accès au projet ou aux projets à ajouter à la solution. Les extensions de [modèle de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell UNIX/Linux sont traitées correctement par la `dotnet sln` commande.

#### <a name="options"></a>Options

- **`-h|--help`**

  Imprime une description de l’utilisation de la commande.

- **`--in-root`**

  Place les projets à la racine de la solution, plutôt que de créer un dossier de solution. Option disponible à partir du kit SDK .NET Core 3.0.

- **`-s|--solution-folder <PATH>`**

  Chemin d’accès du dossier de solution de destination auquel ajouter les projets. Option disponible à partir du kit SDK .NET Core 3.0.

### `remove`

Supprime un ou plusieurs projets du fichier solution.

#### <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet sln [<SOLUTION_FILE>] remove <PROJECT_PATH> [<PROJECT_PATH>...]
dotnet sln [<SOLUTION_FILE>] remove [-h|--help]
```

#### <a name="arguments"></a>Arguments

- **`SOLUTION_FILE`**

  Fichier solution à utiliser. Si n’est pas spécifié, la commande recherche un répertoire actif et échoue s’il existe plusieurs fichiers solution.

- **`PROJECT_PATH`**

  Chemin d’accès au projet ou aux projets à ajouter à la solution. Les extensions de [modèle de globbing](https://en.wikipedia.org/wiki/Glob_(programming)) de shell UNIX/Linux sont traitées correctement par la `dotnet sln` commande.

#### <a name="options"></a>Options

- **`-h|--help`**

  Imprime une description de l’utilisation de la commande.

## <a name="examples"></a>Exemples

- Répertorier les projets dans une solution :

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

- Ajoutez plusieurs projets C# à la racine d’une solution :

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

- Ajouter plusieurs projets C# à une solution à l’aide d’un modèle globbing (UNIX/Linux uniquement) :

  ```dotnetcli
  dotnet sln todo.sln add **/*.csproj
  ```

- Ajouter plusieurs projets C# à une solution à l’aide d’un modèle globbing (Windows PowerShell uniquement) :

  ```dotnetcli
  dotnet sln todo.sln add (ls -r **/*.csproj)
  ```

- Supprimer plusieurs projets C# d’une solution à l’aide d’un modèle globbing (UNIX/Linux uniquement) :

  ```dotnetcli
  dotnet sln todo.sln remove **/*.csproj
  ```

- Supprimer plusieurs projets C# d’une solution à l’aide d’un modèle globbing (Windows PowerShell uniquement) :

  ```dotnetcli
  dotnet sln todo.sln remove (ls -r **/*.csproj)
  ```

- Créer une solution, une application console et deux bibliothèques de classes. Ajoutez les projets à la solution et utilisez l' `--solution-folder` option de `dotnet sln` pour organiser les bibliothèques de classes dans un dossier de solution.

  ```dotnetcli
  dotnet new sln -n mysolution
  dotnet new console -o myapp
  dotnet new classlib -o mylib1
  dotnet new classlib -o mylib2
  dotnet sln mysolution.sln add myapp\myapp.csproj
  dotnet sln mysolution.sln add mylib1\mylib1.csproj --solution-folder mylibs
  dotnet sln mysolution.sln add mylib2\mylib2.csproj --solution-folder mylibs
  ```

  La capture d’écran suivante montre le résultat obtenu dans Visual Studio 2019 **Explorateur de solutions**:

  :::image type="content" source="media/dotnet-sln/dotnet-sln-solution-folder.png" alt-text="Explorateur de solutions de l’indication des projets de bibliothèque de classes regroupés dans un dossier de solution.":::
