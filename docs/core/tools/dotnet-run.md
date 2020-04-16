---
title: Commande dotnet run
description: La commande dotnet run fournit une option pratique pour exécuter votre application à partir du code source.
ms.date: 02/19/2020
ms.openlocfilehash: 28ed13a17c127ae1c61548fed8491315db279c20
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463415"
---
# <a name="dotnet-run"></a>dotnet run

**Cet article s’applique à:** ✔️ .NET Core 2.x SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet run` - Exécute le code source sans commandes explicites de compilation ou de démarrage.

## <a name="synopsis"></a>Synopsis

```dotnetcli
dotnet run [-c|--configuration <CONFIGURATION>] [-f|--framework <FRAMEWORK>]
    [--force] [--interactive] [--launch-profile <NAME>] [--no-build]
    [--no-dependencies] [--no-launch-profile] [--no-restore]
    [-p|--project <PATH>] [-r|--runtime <RUNTIME_IDENTIFIER>]
    [-v|--verbosity <LEVEL>] [[--] [application arguments]]

dotnet run -h|--help
```

## <a name="description"></a>Description

La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande. Elle est utile pour le développement itératif rapide en ligne de commande. La commande dépend [`dotnet build`](dotnet-build.md) de la commande pour construire le code. Les conditions requises pour la génération, par exemple le fait que le projet doit être restauré en premier, s’appliquent également à `dotnet run`.

Les fichiers de sortie sont écrits dans l’emplacement par défaut, à savoir `bin/<configuration>/<target>`. Par exemple, si vous avez une application `netcoreapp2.1` et que vous exécutez `dotnet run`, la sortie est placée dans `bin/Debug/netcoreapp2.1`. Les fichiers sont remplacés, si nécessaire. Les fichiers temporaires sont placés dans le répertoire `obj`.

Si le projet spécifie plusieurs frameworks, l’exécution de `dotnet run` entraîne une erreur, sauf si l’option `-f|--framework <FRAMEWORK>` est utilisée pour spécifier le framework.

La commande `dotnet run` est utilisée pour des projets, et pas pour des assemblys générés. Si vous tentez d’exécuter plutôt une DLL d’applications dépendantes du framework, vous devez utiliser [dotnet](dotnet.md) sans commande. Par exemple, pour exécuter `myapp.dll`, utilisez :

```dotnetcli
dotnet myapp.dll
```

Pour plus d’informations sur le pilote `dotnet`, consultez la rubrique [Outils en ligne de commande (CLI) .NET Core](index.md).

Pour exécuter l’application, la commande `dotnet run` résout les dépendances de l’application externes au runtime partagé à partir du cache NuGet. Dans la mesure où elle utilise la mise en cache des dépendances, il n’est pas recommandé d’utiliser `dotnet run` pour exécuter des applications en production. [Créez plutôt un déploiement](../deploying/index.md) à l’aide de la commande [`dotnet publish`](dotnet-publish.md) et déployez le résultat publié.

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Options

- **`--`**

  Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution. Tous les arguments après ce délimiteur sont passés à l’application exécutée.

- **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par `Debug`défaut pour la plupart des projets est, mais vous pouvez remplacer les paramètres de configuration de construction dans votre projet.

- **`-f|--framework <FRAMEWORK>`**

  Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié. Le framework doit être spécifié dans le fichier projet.

- **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple). Option disponible à partir du kit SDK .NET Core 3.0.

- **`--launch-profile <NAME>`**

  Nom du profil de lancement éventuel à utiliser au lancement de l’application. Les profils de lancement sont définis dans le fichier `Development` *launchSettings.json* et sont généralement appelés , `Staging`, et `Production`. Pour plus d’informations, voir [Travailler avec plusieurs environnements](/aspnet/core/fundamentals/environments).

- **`--no-build`**

  Ne génère pas le projet avant l’exécution. L’indicateur `--no-restore` est également défini implicitement.

- **`--no-dependencies`**

  En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.

- **`--no-launch-profile`**

  N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.

- **`--no-restore`**

  N’effectue pas de restauration implicite à l’exécution de la commande.

- **`-p|--project <PATH>`**

  Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet). Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  Spécifie le runtime cible pour lequel restaurer les packages. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). `-r`option courte disponible depuis .NET Core 3.0 SDK.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `m`. Disponible depuis .NET Core 2.1 SDK.

## <a name="examples"></a>Exemples

- Exécutez le projet dans le répertoire actif :

  ```dotnetcli
  dotnet run
  ```

- Exécutez le projet spécifié :

  ```dotnetcli
  dotnet run --project ./projects/proj1/proj1.csproj
  ```

- Exécutez le projet dans le répertoire actuel (l’argument `--help` de cet exemple est passé à l’application, puisque l’option `--` vide est utilisée) :

  ```dotnetcli
  dotnet run --configuration Release -- --help
  ```

- Restaurer des dépendances et des outils pour le projet dans le répertoire actuel en montrant uniquement une sortie minimale, puis exécuter le projet : (SDK .NET Core 2.0 et ultérieur) :

  ```dotnetcli
  dotnet run --verbosity m
  ```
