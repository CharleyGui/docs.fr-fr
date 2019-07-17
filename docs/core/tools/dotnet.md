---
title: Commande dotnet
description: Découvrez la commande dotnet (le pilote générique des outils .NET Core CLI) et comment l’utiliser.
ms.date: 06/04/2018
ms.openlocfilehash: 2134bf8ed66157619499b027f01d39e03e84411f
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859554"
---
# <a name="dotnet-command"></a>Commande dotnet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet` - Outil de gestion du code source et des ressources binaires .NET.

## <a name="synopsis"></a>Résumé

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a>Description

`dotnet` est un outil de gestion du code source et des ressources binaires .NET. Il expose les commandes qui permettent d’effectuer des tâches spécifiques, par exemple [`dotnet build`](dotnet-build.md) et [`dotnet run`](dotnet-run.md). Chaque commande définit ses propres arguments. Tapez `--help` après chaque commande pour accéder à une brève documentation d’aide.

Vous pouvez utiliser `dotnet` pour exécuter des applications en spécifiant une DLL d’application, par exemple `dotnet myapp.dll`. Pour plus d’informations sur les options de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

## <a name="options"></a>Options

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

Chemin du fichier *deps.json* supplémentaire.

`--additionalprobingpath <PATH>`

Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.

`-d|--diagnostics`

Active la sortie de diagnostic.

`--fx-version <VERSION>`

Version du runtime .NET Core à utiliser pour exécuter l’application.

`-h|--help`

Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`. `dotnet --help` affiche une liste des commandes disponibles.

`--info`

Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.

`--list-runtimes`

Affiche les runtimes .NET Core installés.

`--list-sdks`

Affiche les kits de développement logiciel .NET Core installés.

`--roll-forward-on-no-candidate-fx <N>`

Définit le comportement quand le framework partagé requis n’est pas disponible. `N` peut être :
* `0` : désactiver l’extrapolation même pour les versions mineures.
* `1` : extrapoler la version mineure, mais pas la version majeure. Il s'agit du comportement par défaut.
* `2` : extrapoler les versions majeures et mineures.

 Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.

`--version`

Affiche la version du SDK .NET Core en cours d’utilisation.

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

Chemin du fichier *deps.json* supplémentaire.

`--additionalprobingpath <PATH>`

Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.

`-d|--diagnostics`

Active la sortie de diagnostic.

`--fx-version <VERSION>`

Version du runtime .NET Core à utiliser pour exécuter l’application.

`-h|--help`

Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`. `dotnet --help` affiche une liste des commandes disponibles.

`--info`

Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.

`--roll-forward-on-no-candidate-fx`

 Désactive la restauration par progression d’une version mineure, si la valeur est `0`. Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.

`--version`

Affiche la version du SDK .NET Core en cours d’utilisation.

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.

`-d|--diagnostics`

Active la sortie de diagnostic.

`--fx-version <VERSION>`

Version du runtime .NET Core à utiliser pour exécuter l’application.

`-h|--help`

Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`. `dotnet --help` affiche une liste des commandes disponibles.

`--info`

Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.

`--version`

Affiche la version du SDK .NET Core en cours d’utilisation.

---

## <a name="dotnet-commands"></a>Commandes dotnet

### <a name="general"></a>Général

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

| Commande                                       | Fonction                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | Génère une application .NET Core.                                     |
| [dotnet build-server](dotnet-build-server.md) | Interagit avec les serveurs démarrés par une build.                          |
| [dotnet clean](dotnet-clean.md)               | Nettoie les sorties de build.                                                |
| [dotnet help](dotnet-help.md)                 | Affiche plus de documentation détaillée en ligne pour la commande.           |
| [dotnet migrate](dotnet-migrate.md)           | Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md)           | Fournit l’accès à la ligne de commande MSBuild.                        |
| [dotnet new](dotnet-new.md)                   | Initialise un projet C# ou F# pour un modèle donné.                |
| [dotnet pack](dotnet-pack.md)                 | Crée un package NuGet à partir de votre code.                               |
| [dotnet publish](dotnet-publish.md)           | Publie une application .NET dépendante du framework ou autonome. |
| [dotnet restore](dotnet-restore.md)           | Restaure les dépendances d’une application donnée.                  |
| [dotnet run](dotnet-run.md)                   | Exécute l’application à partir de la source.                                   |
| [dotnet sln](dotnet-sln.md)                   | Options pour ajouter, supprimer et lister des projets dans un fichier solution.       |
| [dotnet store](dotnet-store.md)               | Stocke les assemblys dans le magasin de packages de runtime.                     |
| [dotnet test](dotnet-test.md)                 | Exécute des tests à l’aide d’un lanceur de tests.                                     |

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

| Commande                             | Fonction                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Génère une application .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Nettoie les sorties de build.                                              |
| [dotnet help](dotnet-help.md)       | Affiche plus de documentation détaillée en ligne pour la commande.           |
| [dotnet migrate](dotnet-migrate.md) | Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Fournit l’accès à la ligne de commande MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Initialise un projet C# ou F# pour un modèle donné.                |
| [dotnet pack](dotnet-pack.md)       | Crée un package NuGet à partir de votre code.                               |
| [dotnet publish](dotnet-publish.md) | Publie une application .NET dépendante du framework ou autonome. |
| [dotnet restore](dotnet-restore.md) | Restaure les dépendances d’une application donnée.                  |
| [dotnet run](dotnet-run.md)         | Exécute l’application à partir de la source.                                   |
| [dotnet sln](dotnet-sln.md)         | Options pour ajouter, supprimer et lister des projets dans un fichier solution.       |
| [dotnet store](dotnet-store.md)     | Stocke les assemblys dans le magasin de packages de runtime.                     |
| [dotnet test](dotnet-test.md)       | Exécute des tests à l’aide d’un lanceur de tests.                                     |

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

| Commande                             | Fonction                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)     | Génère une application .NET Core.                                     |
| [dotnet clean](dotnet-clean.md)     | Nettoie les sorties de build.                                              |
| [dotnet migrate](dotnet-migrate.md) | Migre un projet Preview 2 valide vers un projet SDK .NET Core 1.0.  |
| [dotnet msbuild](dotnet-msbuild.md) | Fournit l’accès à la ligne de commande MSBuild.                        |
| [dotnet new](dotnet-new.md)         | Initialise un projet C# ou F# pour un modèle donné.                |
| [dotnet pack](dotnet-pack.md)       | Crée un package NuGet à partir de votre code.                               |
| [dotnet publish](dotnet-publish.md) | Publie une application .NET dépendante du framework ou autonome. |
| [dotnet restore](dotnet-restore.md) | Restaure les dépendances d’une application donnée.                  |
| [dotnet run](dotnet-run.md)         | Exécute l’application à partir de la source.                                   |
| [dotnet sln](dotnet-sln.md)         | Options pour ajouter, supprimer et lister des projets dans un fichier solution.       |
| [dotnet test](dotnet-test.md)       | Exécute des tests à l’aide d’un lanceur de tests.                                     |

---

### <a name="project-references"></a>Références de projets

Commande | Fonction
--- | ---
[dotnet add reference](dotnet-add-reference.md) | Ajoute une référence au projet.
[dotnet list reference](dotnet-list-reference.md) | Liste les références du projet.
[dotnet remove reference](dotnet-remove-reference.md) | Supprime une référence de projet.

### <a name="nuget-packages"></a>Packages NuGet

Commande | Fonction
--- | ---
[dotnet add package](dotnet-add-package.md) | Ajoute un package NuGet.
[dotnet remove package](dotnet-remove-package.md) | Supprime un package NuGet.

### <a name="nuget-commands"></a>Commandes NuGet

Commande | Fonction
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | Supprime ou retire un package du serveur.
[dotnet nuget locals](dotnet-nuget-locals.md) | Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.
[dotnet nuget push](dotnet-nuget-push.md) | Effectue une transmission de type push d’un package sur le serveur et le publie.

### <a name="global-tools-commands"></a>Outils et commandes globaux

Les [outils globaux .NET Core](global-tools.md) sont disponibles à partir de .NET Core SDK 2.1.300 :

Commande | Fonction
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Installe un outil global sur votre ordinateur.
[dotnet tool list](dotnet-tool-list.md) | Répertorie tous les outils globaux actuellement installés dans le répertoire par défaut de votre machine ou à l’emplacement du chemin spécifié.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Désinstalle un outil global de votre ordinateur.
[dotnet tool update](dotnet-tool-update.md) | Met à jour un outil global sur votre ordinateur.

### <a name="additional-tools"></a>Outils supplémentaires

À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core. Ces outils sont répertoriés dans le tableau suivant :

| Outil                                              | Fonction                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Crée et gère les certificats de développement.                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Outils en ligne de commande Entity Framework Core.                    |
| sql-cache                                         | Outils en ligne de commande du cache SQL Server.                         |
| [user-secrets](/aspnet/core/security/app-secrets) | Gère les secrets de développement de l’utilisateur.                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier. |

Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.

## <a name="examples"></a>Exemples

Crée une application console .NET Core :

`dotnet new console`

Restaurez les dépendances d’une application donnée :

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Générez un projet et ses dépendances dans un répertoire donné :

`dotnet build`

Exécutez une DLL d’application, par exemple `myapp.dll` :

`dotnet myapp.dll`

## <a name="environment-variables"></a>Variables d’environnement

# <a name="net-core-21tabnetcore21"></a>[.NET Core 2.1](#tab/netcore21)

`DOTNET_PACKAGES`

Le dossier de packages global. S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.

`DOTNET_SERVICING`

Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft. Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`). Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`). Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.

`DOTNET_MULTILEVEL_LOOKUP`

Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global. Si elle n’est pas définie, la valeur par défaut est `true`. Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées). Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

Désactive la restauration par progression d’une version mineure, si la valeur est `0`. Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).

# <a name="net-core-20tabnetcore20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Cache du package principal. S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.

`DOTNET_SERVICING`

Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft. Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`). Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`). Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.

`DOTNET_MULTILEVEL_LOOKUP`

Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global. Si elle n’est pas définie, la valeur par défaut est `true`. Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées). Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1xtabnetcore1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Cache du package principal. S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.

`DOTNET_SERVICING`

Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft. Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`). Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`). Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.

---
