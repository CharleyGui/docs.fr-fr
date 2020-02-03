---
title: Commande dotnet run
description: La commande dotnet run fournit une option pratique pour exécuter votre application à partir du code source.
ms.date: 10/31/2019
ms.openlocfilehash: 5920f0d1f04204b286fdf6f51f5fd13644846390
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734103"
---
# <a name="dotnet-run"></a>dotnet run

**Cet article s’applique à :** ✔️ Kit de développement logiciel (SDK) .net Core 1. x et versions ultérieures

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>Nom

`dotnet run` - Exécute le code source sans commandes explicites de compilation ou de démarrage.

## <a name="synopsis"></a>Résumé

<!-- markdownlint-disable MD025 -->

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--interactive] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [-r|--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [-v|--verbosity] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies]
    [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a>Description

La commande `dotnet run` fournit une option pratique pour exécuter votre application à partir du code source à l’aide d’une seule commande. Elle est utile pour le développement itératif rapide en ligne de commande. Elle dépend de la commande [`dotnet build`](dotnet-build.md) pour générer le code. Les conditions requises pour la génération, par exemple le fait que le projet doit être restauré en premier, s’appliquent également à `dotnet run`.

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

# <a name="net-core-30tabnetcore30"></a>[.NET Core 3.0](#tab/netcore30)

`--`

Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution. Tous les arguments après ce délimiteur sont passés à l’application exécutée.

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut de la plupart des projets est `Debug`.

`-f|--framework <FRAMEWORK>`

Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié. Le framework doit être spécifié dans le fichier projet.

`--force`

Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

`-h|--help`

Affiche une aide brève pour la commande.

`--interactive`

Permet à la commande de s’arrêter et d’attendre une saisie ou une action de l’utilisateur (son authentification, par exemple).

`--launch-profile <NAME>`

Nom du profil de lancement éventuel à utiliser au lancement de l’application. Les profils de lancement sont définis dans le fichier *launchSettings.json* et s’appellent généralement `Development`, `Staging` et `Production`. Pour plus d’informations, consultez [Utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).

`--no-build`

Ne génère pas le projet avant l’exécution. L’indicateur `--no-restore` est également défini implicitement.

`--no-dependencies`

En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.

`--no-launch-profile`

N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-p|--project <PATH>`

Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet). Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

`--runtime <RUNTIME_IDENTIFIER>`

Spécifie le runtime cible pour lequel restaurer les packages. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--`

Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution. Tous les arguments après ce délimiteur sont passés à l’application exécutée.

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut de la plupart des projets est `Debug`.

`-f|--framework <FRAMEWORK>`

Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié. Le framework doit être spécifié dans le fichier projet.

`--force`

Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

`-h|--help`

Affiche une aide brève pour la commande.

`--launch-profile <NAME>`

Nom du profil de lancement éventuel à utiliser au lancement de l’application. Les profils de lancement sont définis dans le fichier *launchSettings.json* et s’appellent généralement `Development`, `Staging` et `Production`. Pour plus d’informations, consultez [Utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).

`--no-build`

Ne génère pas le projet avant l’exécution. L’indicateur `--no-restore` est également défini implicitement.

`--no-dependencies`

En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.

`--no-launch-profile`

N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-p|--project <PATH>`

Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet). Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

`--runtime <RUNTIME_IDENTIFIER>`

Spécifie le runtime cible pour lequel restaurer les packages. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--`

Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution. Tous les arguments après ce délimiteur sont passés à l’application exécutée.

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut de la plupart des projets est `Debug`.

`-f|--framework <FRAMEWORK>`

Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié. Le framework doit être spécifié dans le fichier projet.

`--force`

Force la résolution de toutes les dépendances même si la dernière restauration a réussi. Définir cet indicateur revient à supprimer le fichier *project.assets.json*.

`-h|--help`

Affiche une aide brève pour la commande.

`--launch-profile <NAME>`

Nom du profil de lancement éventuel à utiliser au lancement de l’application. Les profils de lancement sont définis dans le fichier *launchSettings.json* et s’appellent généralement `Development`, `Staging` et `Production`. Pour plus d’informations, consultez [Utilisation de plusieurs environnements](/aspnet/core/fundamentals/environments).

`--no-build`

Ne génère pas le projet avant l’exécution. L’indicateur `--no-restore` est également défini implicitement.

`--no-dependencies`

En cas de restauration d’un projet avec des références entre projets (P2P), restaure le projet racine et non les références.

`--no-launch-profile`

N’essaie pas d’utiliser *launchSettings.json* pour configurer l’application.

`--no-restore`

N’effectue pas de restauration implicite à l’exécution de la commande.

`-p|--project <PATH>`

Spécifie le chemin du fichier projet à exécuter (nom de dossier ou chemin complet). Si aucune valeur n’est spécifiée, le répertoire actif est utilisé par défaut.

`--runtime <RUNTIME_IDENTIFIER>`

Spécifie le runtime cible pour lequel restaurer les packages. Pour connaître les identificateurs de runtime, consultez le [catalogue des identificateurs de runtime](../rid-catalog.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--`

Délimite les arguments à `dotnet run` parmi les arguments de l’application en cours d’exécution. Tous les arguments après ce délimiteur sont passés à l’application exécutée.

`-c|--configuration {Debug|Release}`

Définit la configuration de build. La valeur par défaut de la plupart des projets est `Debug`.

`-f|--framework <FRAMEWORK>`

Crée et exécute l’application à l’aide du [framework](../../standard/frameworks.md) spécifié. Le framework doit être spécifié dans le fichier projet.

`-h|--help`

Affiche une aide brève pour la commande.

`-p|--project <PATH/PROJECT.csproj>`

Spécifie le chemin d’accès et le nom du fichier projet. (Voir la remarque.) S’il n’est pas spécifié, le répertoire actif est utilisé par défaut.

> [!NOTE]
> Utilisez le chemin d’accès et le nom du fichier projet avec l’option `-p|--project`. Une régression dans l’interface CLI empêche de fournir un chemin de dossier avec le SDK .NET Core 1.x. Pour plus d’informations sur ce problème, consultez la page [dotnet run -p, impossible de démarrer un projet (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).

---

## <a name="examples"></a>Exemples

Exécutez le projet dans le répertoire actif :

`dotnet run`

Exécutez le projet spécifié :

`dotnet run --project ./projects/proj1/proj1.csproj`

Exécutez le projet dans le répertoire actuel (l’argument `--help` de cet exemple est passé à l’application, puisque l’option `--` vide est utilisée) :

`dotnet run --configuration Release -- --help`

Restaurer des dépendances et des outils pour le projet dans le répertoire actuel en montrant uniquement une sortie minimale, puis exécuter le projet : (SDK .NET Core 2.0 et ultérieur) :

`dotnet run --verbosity m`
