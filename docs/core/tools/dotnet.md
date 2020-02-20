---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: 364978465b63401907b46ead64dbceb2f15c8169
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451166"
---
# <a name="dotnet-command"></a>Commande dotnet

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a>Name

`dotnet` - Outil de gestion du code source et des ressources binaires .NET.

## <a name="synopsis"></a>Synopsis

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a>Description

`dotnet` est un outil de gestion du code source et des ressources binaires .NET. Il expose les commandes qui permettent d’effectuer des tâches spécifiques, par exemple [`dotnet build`](dotnet-build.md) et [`dotnet run`](dotnet-run.md). Chaque commande définit ses propres arguments. Tapez `--help` après chaque commande pour accéder à une brève documentation d’aide.

Vous pouvez utiliser `dotnet` pour exécuter des applications en spécifiant une DLL d’application, par exemple `dotnet myapp.dll`. Pour plus d’informations sur les options de déploiement, consultez [Déploiement d’applications .NET Core](../deploying/index.md).

## <a name="options"></a>Options

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

`--additional-deps <PATH>`

Chemin d’un fichier *.deps.json* supplémentaire.

`--additionalprobingpath <PATH>`

Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.

`--depsfile`

Chemin d’un fichier *deps.json*.

Un fichier *DEPS. JSON* contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour traiter les conflits d’assembly. Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.

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

Définit le comportement quand le framework partagé requis n’est pas disponible. Voici à quoi `N` peut correspondre :

- `0` : désactiver l’extrapolation même pour les versions mineures.
- `1` : extrapoler la version mineure, mais pas la version majeure. Il s'agit du comportement par défaut.
- `2` : extrapoler les versions majeures et mineures.

 Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).

`--runtimeconfig`

Chemin d’un fichier *runtimeconfig.json*.

Un fichier *runtimeconfig. JSON* est un fichier de configuration qui contient des paramètres d’exécution. Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.

`--version`

Affiche la version du SDK .NET Core en cours d’utilisation.

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

`--additional-deps <PATH>`

Chemin d’un fichier *.deps.json* supplémentaire.

`--additionalprobingpath <PATH>`

Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.

`--depsfile`

Chemin d’un fichier *deps.json*.

Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys. Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

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

`--runtimeconfig`

Chemin d’un fichier *runtimeconfig.json*.

Un fichier *runtimeconfig. JSON* est un fichier de configuration qui contient des paramètres d’exécution. Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.

`--version`

Affiche la version du SDK .NET Core en cours d’utilisation.

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

`--additionalprobingpath <PATH>`

Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.

`--depsfile`

Chemin d’un fichier *deps.json*.

Un fichier *deps.json* contient une liste de dépendances, des dépendances de compilation et des informations de version utilisées pour tenter de résoudre les conflits d’assemblys. Pour plus d’informations sur ce fichier, consultez [Runtime Configuration Files sur GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).

`-d|--diagnostics`

Active la sortie de diagnostic.

`--fx-version <VERSION>`

Version du runtime .NET Core à utiliser pour exécuter l’application.

`-h|--help`

Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`. `dotnet --help` affiche une liste des commandes disponibles.

`--info`

Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.

`--runtimeconfig`

Chemin d’un fichier *runtimeconfig.json*.

Un fichier *runtimeconfig. JSON* est un fichier de configuration qui contient des paramètres d’exécution. Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).

`-v|--verbosity <LEVEL>`

Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Non pris en charge dans toutes les commandes ; consultez la page de commande spécifique pour déterminer si cette option est disponible.

`--version`

Affiche la version du SDK .NET Core en cours d’utilisation.

---

## <a name="dotnet-commands"></a>Commandes dotnet

### <a name="general"></a>Général

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

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

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

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

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

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

### <a name="global-tool-path-and-local-tools-commands"></a>Commandes globales, de chemin d’accès d’outil et d’outils locaux

Les outils sont des applications console qui sont installées à partir de packages NuGet et sont appelées à partir de l’invite de commandes. Vous pouvez écrire vous-même des outils ou installer des outils écrits par des tiers. Les outils sont également appelés outils globaux, outils de chemin d’accès d’outil et outils locaux. Pour plus d’informations, consultez [vue d’ensemble des outils .net Core](global-tools.md). Les outils globaux et de chemin d’accès aux outils sont disponibles à partir de kit SDK .NET Core 2,1. Les outils locaux sont disponibles à partir de kit SDK .NET Core 3,0.

Commande | Fonction
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Installe un outil sur votre ordinateur.
[dotnet tool list](dotnet-tool-list.md) | Répertorie tous les outils globaux, de chemin d’accès d’outil ou locaux actuellement installés sur votre ordinateur.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Désinstalle un outil de votre ordinateur.
[dotnet tool update](dotnet-tool-update.md) | Met à jour un outil qui est installé sur votre ordinateur.

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

## <a name="environment-variables"></a>Variables d'environnement

# <a name="net-core-21"></a>[.NET Core 2.1](#tab/netcore21)

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

# <a name="net-core-20"></a>[.NET Core 2.0](#tab/netcore20)

`DOTNET_PACKAGES`

Cache du package principal. S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.

`DOTNET_SERVICING`

Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft. Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`). Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`). Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.

`DOTNET_MULTILEVEL_LOOKUP`

Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global. Si elle n’est pas définie, la valeur par défaut est `true`. Définie sur `false` pour ne pas résoudre depuis l’emplacement global et avoir des installations .NET Core (les valeurs `0` ou `false` sont acceptées). Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

# <a name="net-core-1x"></a>[.NET Core 1.x](#tab/netcore1x)

`DOTNET_PACKAGES`

Cache du package principal. S’il n’est pas défini, les valeurs par défaut sont `$HOME/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.

`DOTNET_SERVICING`

Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.

`DOTNET_CLI_TELEMETRY_OPTOUT`

Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft. Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`). Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`). Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.

---

## <a name="see-also"></a>Voir aussi

- [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Paramètres de configuration du Runtime .NET Core](../run-time-config/index.md)
