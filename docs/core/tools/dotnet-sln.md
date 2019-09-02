---
title: Commande dotnet sln
description: La commande dotnet-sln offre une option pratique pour ajouter, supprimer et lister des projets dans un fichier solution.
ms.date: 06/13/2018
ms.openlocfilehash: 3f18d6a2851d955d07cecc0cbc4c161cf0ec3e08
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202791"
---
# <a name="dotnet-sln"></a>dotnet sln

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet sln` : Modifie un fichier solution .NET Core.

## <a name="synopsis"></a>Résumé

```console
dotnet sln [<SOLUTION_NAME>] add <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] add <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] remove <PROJECT> <PROJECT> ...
dotnet sln [<SOLUTION_NAME>] remove <GLOBBING_PATTERN>
dotnet sln [<SOLUTION_NAME>] list
dotnet sln [-h|--help]
```

## <a name="description"></a>Description

La commande `dotnet sln` offre un moyen pratique d’ajouter, de supprimer et de lister des projets dans un fichier solution.

Pour que la commande `dotnet sln` puisse être utilisée, le fichier solution doit déjà exister. Si vous devez en créer un, utilisez la commande [dotnet new](dotnet-new.md), comme dans l’exemple suivant :

```console
dotnet new sln
```

## <a name="commands"></a>Commandes

`add <PROJECT> ...`

`add <GLOBBING_PATTERN>`

Ajoute un ou plusieurs projets au fichier solution. Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.

`remove <PROJECT> ...`

`remove <GLOBBING_PATTERN>`

Supprime un ou plusieurs projets du fichier solution. Les [modèles Globbing](https://en.wikipedia.org/wiki/Glob_(programming)) sont pris en charge sur les terminaux Unix/Linux.

`list`

Liste tous les projets dans un fichier solution.

## <a name="arguments"></a>Arguments

`SOLUTION_NAME`

Fichier solution à utiliser. Si aucun fichier n’est spécifié, la commande en recherche un dans le répertoire actuel. S’il existe plusieurs fichiers solution dans le répertoire, l’un d’eux doit être spécifié.

## <a name="options"></a>Options

`-h|--help`

Affiche une aide brève pour la commande.

## <a name="examples"></a>Exemples

Ajouter un projet C# à une solution :

`dotnet sln todo.sln add todo-app/todo-app.csproj`

Supprimer un projet C# d’une solution :

`dotnet sln todo.sln remove todo-app/todo-app.csproj`

Ajouter plusieurs projets C# à une solution :

`dotnet sln todo.sln add todo-app/todo-app.csproj back-end/back-end.csproj`

Supprimer plusieurs projets C# d’une solution :

`dotnet sln todo.sln remove todo-app/todo-app.csproj back-end/back-end.csproj`

Ajouter plusieurs projets C# à une solution avec un modèle d’utilisation des caractères génériques :

`dotnet sln todo.sln add **/*.csproj`

Supprimer plusieurs projets C# d’une solution avec un modèle d’utilisation des caractères génériques :

`dotnet sln todo.sln remove **/*.csproj`

> [!NOTE]
> L’utilisation des caractères génériques n’est pas une fonctionnalité de l’interface CLI, mais une fonctionnalité de l’interpréteur de commandes. Pour pouvoir développer les fichiers, vous devez utiliser un interpréteur de commandes qui prend en charge l’utilisation des caractères génériques. Pour plus d’informations sur l’utilisation des caractères génériques, voir [Wikipédia](https://en.wikipedia.org/wiki/Glob_(programming)).
