---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240868"
---
# <a name="dotnet-command"></a>Commande dotnet

**Cet article s’applique à : ✔️ le kit de** développement logiciel (SDK) .net Core 2,1 et versions ultérieures

## <a name="name"></a>Nom

`dotnet`-pilote générique du CLI .NET Core.

## <a name="synopsis"></a>Synopsis

Pour obtenir des informations sur les commandes disponibles et l’environnement :

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

Pour exécuter une commande (installation du kit de développement logiciel (SDK) requise) :

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

Pour exécuter une application :

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward` est disponible depuis .NET Core 3. x. Utilisez `--roll-forward-on-no-candidate-fx` pour .NET Core 2. x.

## <a name="description"></a>Description

La commande `dotnet` a deux fonctions :

- Il fournit des commandes pour travailler avec les projets .NET Core.

  Par exemple, [`dotnet build`](dotnet-build.md) génère un projet. Chaque commande définit ses propres options et arguments. Toutes les commandes prennent en charge l’option `--help` pour imprimer une brève documentation sur la façon d’utiliser la commande.

- Il exécute des applications .NET Core.

  Vous spécifiez le chemin d’accès à un fichier d' `.dll` d’application pour exécuter l’application. Par exemple, `dotnet myapp.dll` exécute l’application `myapp`. Consultez [déploiement d’applications .net Core](../deploying/index.md) pour en savoir plus sur les options de déploiement.

## <a name="options"></a>Options

Différentes options sont disponibles pour la `dotnet` seule, pour exécuter une commande et pour exécuter une application.

### <a name="options-for-dotnet-by-itself"></a>Options de dotnet par lui-même

Les options suivantes sont destinées à `dotnet` par elle-même. Par exemple : `dotnet --info`. Ils affichent des informations sur l’environnement.

- **`--info`**

  Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.

- **`--version`**

  Affiche la version du SDK .NET Core en cours d’utilisation.

- **`--list-runtimes`**

  Imprime une liste des runtimes .NET Core installés.

- **`--list-sdks`**

  Affiche la liste des kits de développement logiciel (SDK) .NET Core installés.

- **`-h|--help`**

  Imprime une liste des commandes disponibles.

### <a name="sdk-options-for-running-a-command"></a>Options du kit de développement logiciel pour exécuter une commande

Les options suivantes concernent `dotnet` avec une commande. Par exemple : `dotnet build --help`.

- **`-d|--diagnostics`**

  Active la sortie de diagnostic.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Non pris en charge dans chaque commande. Consultez la page de commande spécifique pour déterminer si cette option est disponible.

- **`-h|--help`**

  Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.

- **`command options`**

  Chaque commande définit des options spécifiques à cette commande. Pour obtenir la liste des options disponibles, consultez la page de commande spécifique.

### <a name="runtime-options"></a>Options d’exécution

Les options suivantes sont disponibles lorsque `dotnet` exécute une application. Par exemple : `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.

- **`--additional-deps <PATH>`**

  Chemin d’un fichier *.deps.json* supplémentaire. Un fichier *DEPS. JSON* contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour traiter les conflits d’assembly. Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.

- **`--fx-version <VERSION>`**

  Version du runtime .NET Core à utiliser pour exécuter l’application.

- **`--runtimeconfig`**

  Chemin d’un fichier *runtimeconfig.json*. Un fichier *runtimeconfig. JSON* est un fichier de configuration qui contient des paramètres d’exécution. Pour plus d’informations, consultez [paramètres de configuration du Runtime .net Core](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`** **disponibles dans le kit de développement logiciel (SDK) .net Core 2. x.**

  Définit le comportement quand le framework partagé requis n’est pas disponible. Voici à quoi `N` peut correspondre :

  - `0` : désactiver l’extrapolation même pour les versions mineures.
  - `1` : extrapoler la version mineure, mais pas la version majeure. Il s'agit du comportement par défaut.
  - `2` : extrapoler les versions majeures et mineures.

   Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`** **disponibles à partir de kit SDK .net Core 3,0.**

  Contrôle la façon dont la restauration par progression est appliquée à l’application. L' `SETTING` peut prendre l’une des valeurs suivantes. S’il n’est pas spécifié, `Minor` est la valeur par défaut.

  - `LatestPatch` : restauration par progression vers la version de correctif la plus récente. Cette valeur désactive la restauration par progression d’une version mineure.
  - `Minor`-restaurer à la version mineure la plus basse, si la version mineure demandée est manquante. Si la version mineure demandée est présente, la stratégie LatestPatch est utilisée.
  - `Major`-restaurer la version principale la plus basse, et la version mineure la plus faible, si la version principale demandée est manquante. Si la version principale demandée est présente, la stratégie mineure est utilisée.
  - `LatestMinor` : restauration par progression vers la version mineure la plus élevée, même si la version mineure demandée est présente. Conçu pour les scénarios d’hébergement de composant.
  - `LatestMajor` : restauration par progression vers la version mineure la plus élevée et la plus élevée, même si la version principale demandée est présente. Conçu pour les scénarios d’hébergement de composant.
  - `Disable`-ne pas restaurer par progression. Lier uniquement à la version spécifiée. Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs. Cette valeur est recommandée uniquement à des fins de test.

À l’exception de `Disable`, tous les paramètres utilisent la version de correctif la plus élevée disponible.

Le comportement de restauration par progression peut également être configuré dans une propriété de fichier projet, une propriété de fichier de configuration au moment de l’exécution et une variable d’environnement. Pour plus d’informations, consultez [restauration par progression du runtime de version principale](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

## <a name="dotnet-commands"></a>Commandes dotnet

### <a name="general"></a>Général

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

Créez une application de console .NET Core :

```dotnetcli
dotnet new console
```

Générez un projet et ses dépendances dans un répertoire donné :

```dotnetcli
dotnet build
```

Exécuter une application :

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Variables d'environnement

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Spécifie l’emplacement des runtimes .NET Core, s’ils ne sont pas installés à l’emplacement par défaut. L’emplacement par défaut sur Windows est `C:\Program Files\dotnet`. L’emplacement par défaut sur Linux et macOS est `/usr/share/dotnet`. Cette variable d’environnement est utilisée uniquement lors de l’exécution d’applications via des exécutables générés (apphosts). `DOTNET_ROOT(x86)` est utilisé à la place lors de l’exécution d’un fichier exécutable 32 bits sur un système d’exploitation 64 bits.

- `DOTNET_PACKAGES`

  Le dossier de packages global. S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.

- `DOTNET_SERVICING`

  Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft. Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`). Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`). Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.

- `DOTNET_MULTILEVEL_LOOKUP`

  Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global. S’il n’est pas défini, la valeur par défaut est 1 (`true`logique). Affectez la valeur 0 (`false`logique) pour ne pas résoudre à partir de l’emplacement global et disposer d’installations .NET Core isolées. Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD` **disponibles à partir du kit de développement logiciel (SDK) .net Core 3. x.**

  Détermine le comportement de restauration par progression. Pour plus d’informations, consultez l’option `--roll-forward` plus haut dans cet article.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **disponibles dans le kit de développement logiciel (SDK) .net Core 2. x.**

  Désactive la restauration par progression d’une version mineure, si la valeur est `0`. Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  Définit la langue de l’interface utilisateur CLI à l’aide d’une valeur de paramètres régionaux telle que `en-us`. Les valeurs prises en charge sont les mêmes que pour Visual Studio. Pour plus d’informations, consultez la section relative à la modification du langage d’installation dans la [documentation d’installation de Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Les règles .NET Resource Manager s’appliquent. vous n’avez donc pas besoin de choisir une correspondance exacte&mdash;vous pouvez également choisir des descendants dans l’arborescence des `CultureInfo`. Par exemple, si vous affectez la valeur `fr-CA`, l’interface CLI trouvera et utilisera les traductions `fr`. Si vous définissez une langue qui n’est pas prise en charge, l’interface CLI revient à l’anglais.

- `DOTNET_DISABLE_GUI_ERRORS`

  Pour les exécutables générés par l’interface utilisateur graphique : désactive la boîte de dialogue qui apparaît normalement pour certaines classes d’erreurs. Il écrit uniquement dans `stderr` et se termine dans ces cas.
  
- `DOTNET_ADDITIONAL_DEPS`

  Équivalent de l’option `--additional-deps`de l’interface CLI.

- `DOTNET_RUNTIME_ID`

  Remplace le RID détecté.

- `DOTNET_SHARED_STORE`

  Emplacement du « magasin partagé » dans lequel la résolution de l’assembly revient dans certains cas.

- `DOTNET_STARTUP_HOOKS`

  Liste des assemblys à partir desquels charger et exécuter des raccordements de démarrage.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Contrôle le suivi des diagnostics à partir des composants d’hébergement, tels que `dotnet.exe`, `hostfxr`et `hostpolicy`.

## <a name="see-also"></a>Voir aussi

- [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [Paramètres de configuration du Runtime .NET Core](../run-time-config/index.md)
