---
title: Commande dotnet run
description: La commande dotnet run fournit une option pratique pour exécuter votre application à partir du code source.
ms.date: 02/19/2020
ms.openlocfilehash: c80f290c75e3bac65ae73fe8edada53db4ce86f8
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634414"
---
# <a name="dotnet-run"></a>dotnet run

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 2. x et versions ultérieures

## <a name="name"></a>Name

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

La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande. Elle est utile pour le développement itératif rapide en ligne de commande. La commande dépend de la [`dotnet build`](dotnet-build.md) commande pour générer le code. Les conditions requises pour la génération, par exemple le fait que le projet doit être restauré en premier, s’appliquent également à `dotnet run`.

Les fichiers de sortie sont écrits dans l’emplacement par défaut, à savoir `bin/<configuration>/<target>`. Par exemple, si vous avez une application `netcoreapp2.1` et que vous exécutez `dotnet run`, la sortie est placée dans `bin/Debug/netcoreapp2.1`. Les fichiers sont remplacés, si nécessaire. Les fichiers temporaires sont placés dans le répertoire `obj`.

Si le projet spécifie plusieurs frameworks, l’exécution de `dotnet run` entraîne une erreur, sauf si l’option `-f|--framework <FRAMEWORK>` est utilisée pour spécifier le framework.

La commande `dotnet run` est utilisée pour des projets, et pas pour des assemblys générés. Si vous tentez d’exécuter plutôt une DLL d’applications dépendantes du framework, vous devez utiliser [dotnet](dotnet.md) sans commande. Par exemple, pour exécuter `myapp.dll`, utilisez :

```dotnetcli
dotnet myapp.dll
```

Pour plus d’informations sur le `dotnet` pilote, consultez la rubrique [outils en ligne de commande .net (CLI)](index.md) .

Pour exécuter l’application, la commande `dotnet run` résout les dépendances de l’application externes au runtime partagé à partir du cache NuGet. Dans la mesure où elle utilise la mise en cache des dépendances, il n’est pas recommandé d’utiliser `dotnet run` pour exécuter des applications en production. [Créez plutôt un déploiement](../deploying/index.md) à l’aide de la commande [`dotnet publish`](dotnet-publish.md) et déployez le résultat publié.

### <a name="implicit-restore"></a>Restauration implicite

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="options"></a>Options

- **`--`**

  Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution. Tous les arguments après ce délimiteur sont passés à l’application exécutée.

- **`-c|--configuration <CONFIGURATION>`**

  Définit la configuration de build. La valeur par défaut pour la plupart des projets est `Debug` , mais vous pouvez remplacer les paramètres de configuration de build dans votre projet.

- **`-f|--framework <FRAMEWORK>`**

  Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié. Le framework doit être spécifié dans le fichier projet.

- **`--force`**

  Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

- **`-h|--help`**

  Affiche une aide brève pour la commande.

- **`--interactive`**

  Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple). Option disponible à partir du kit SDK .NET Core 3.0.

- **`--launch-profile <NAME>`**

  Nom du profil de lancement éventuel à utiliser au lancement de l’application. Les profils de lancement sont définis dans le fichier *launchSettings.js* et sont généralement appelés `Development` , `Staging` et `Production` . Pour plus d’informations, consultez [utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).

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

  Spécifie le runtime cible pour lequel restaurer les packages. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md). `-r` option Short disponible depuis le kit de développement logiciel (SDK) .NET Core 3,0.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. La valeur par défaut est `m`. Disponible depuis le kit de développement logiciel (SDK) .NET Core 2,1.

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

- Restaurez les dépendances et les outils pour le projet dans le répertoire actif uniquement avec une sortie minimale, puis exécutez le projet :

  ```dotnetcli
  dotnet run --verbosity m
  ```
