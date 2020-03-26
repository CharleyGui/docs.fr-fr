---
title: Commande dotnet
description: En savoir plus sur la commande dotnet (le pilote générique pour le CLI .NET Core) et son utilisation.
ms.date: 02/13/2020
ms.openlocfilehash: 8692d419afd528bf49e1dc7dc1a7a5fd698b363b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134078"
---
# <a name="dotnet-command"></a>Commande dotnet

**Cet article s’applique à:** ✔️ .NET Core 2.1 SDK et les versions ultérieures

## <a name="name"></a>Nom

`dotnet`- Le pilote générique pour le CLI .NET Core.

## <a name="synopsis"></a>Synopsis

Pour obtenir des informations sur les commandes disponibles et l’environnement :

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

Pour exécuter une commande (nécessite l’installation SDK):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

Pour exécuter une application :

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward`est disponible depuis .NET Core 3.x. Utilisation `--roll-forward-on-no-candidate-fx` pour .NET Core 2.x.

## <a name="description"></a>Description

La `dotnet` commande a deux fonctions :

- Il fournit des commandes pour travailler avec des projets .NET Core.

  Par exemple, [`dotnet build`](dotnet-build.md) construit un projet. Chaque commande définit ses propres options et arguments. Toutes les commandes `--help` prennent en charge l’option d’imprimer de la documentation brève sur la façon d’utiliser la commande.

- Il exécute des applications .NET Core.

  Vous spécifiez `.dll` le chemin vers un fichier de demande pour exécuter l’application. Par exemple, `dotnet myapp.dll` `myapp` exécute l’application. Voir [le déploiement de l’application .NET Core](../deploying/index.md) pour en savoir plus sur les options de déploiement.

## <a name="options"></a>Options

Différentes options sont `dotnet` disponibles pour lui-même, pour l’exécution d’une commande, et pour l’exécution d’une application.

### <a name="options-for-dotnet-by-itself"></a>Options pour dotnet par lui-même

Les options suivantes `dotnet` sont pour lui-même. Par exemple : `dotnet --info`. Ils impriment des informations sur l’environnement.

- **`--info`**

  Affiche des informations détaillées sur une installation .NET Core et l’environnement de la machine, par exemple le système d’exploitation actuel, ainsi que le SHA de validation de la version du .NET Core.

- **`--version`**

  Affiche la version du SDK .NET Core en cours d’utilisation.

- **`--list-runtimes`**

  Imprime une liste des temps d’exécution .NET Core installés.

- **`--list-sdks`**

  Imprime une liste des SDKs .NET Core installés.

- **`-h|--help`**

  Imprime une liste de commandes disponibles.

### <a name="sdk-options-for-running-a-command"></a>Options SDK pour l’exécution d’une commande

Les options suivantes `dotnet` sont pour avec une commande. Par exemple : `dotnet build --help`.

- **`-d|--diagnostics`**

  Active la sortie de diagnostic.

- **`-v|--verbosity <LEVEL>`**

  Définit le niveau de détail de la commande. Les valeurs autorisées sont `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` et `diag[nostic]`. Pas pris en charge dans tous les commandements. Voir la page de commande spécifique pour déterminer si cette option est disponible.

- **`-h|--help`**

  Affiche la documentation relative à une commande donnée, par exemple `dotnet build --help`.

- **`command options`**

  Chaque commande définit les options spécifiques à cette commande. Voir la page de commande spécifique pour une liste d’options disponibles.

### <a name="runtime-options"></a>Options d’exécution

Les options suivantes `dotnet` sont disponibles lors de l’exécution d’une application. Par exemple : `dotnet myapp.dll --fx-version 3.1.1`.

- **`--additionalprobingpath <PATH>`**

  Chemin d’accès contenant la stratégie de sondage et les assemblys à sonder.

- **`--additional-deps <PATH>`**

  Chemin d’un fichier *.deps.json* supplémentaire. Un fichier *deps.json* contient une liste de dépendances, de dépendances de compilation et d’informations de version utilisées pour résoudre les conflits d’assemblage. Pour plus d’informations, consultez [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) sur GitHub.

- **`--fx-version <VERSION>`**

  Version du runtime .NET Core à utiliser pour exécuter l’application.

- **`--runtimeconfig`**

  Chemin d’un fichier *runtimeconfig.json*. Un fichier *runtimeconfig.json* est un fichier de configuration qui contient des paramètres de temps d’exécution. Pour plus d’informations, voir [paramètres de configuration .NET Core run-time](../run-time-config/index.md#runtimeconfigjson).

- **`--roll-forward-on-no-candidate-fx <N>`****Disponible en .NET Core 2.x SDK.**

  Définit le comportement quand le framework partagé requis n’est pas disponible. Voici à quoi `N` peut correspondre :

  - `0` : désactiver l’extrapolation même pour les versions mineures.
  - `1` : extrapoler la version mineure, mais pas la version majeure. Il s'agit du comportement par défaut.
  - `2` : extrapoler les versions majeures et mineures.

   Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).

- **`--roll-forward <SETTING>`****Disponible en commençant par .NET Core SDK 3.0.**

  Contrôle la façon dont le rouleau vers l’avant est appliqué à l’application. La `SETTING` peut être l’une des valeurs suivantes. S’il `Minor` n’est pas spécifié, est la valeur par défaut.

  - `LatestPatch`- Roulez vers la version patch la plus élevée. Cette valeur désactive la restauration par progression d’une version mineure.
  - `Minor`- Rouler vers l’avant à la version mineure supérieure la plus basse, si la version mineure demandée est manquante. Si la version mineure demandée est présente, la stratégie LatestPatch est utilisée.
  - `Major`- Rouler vers l’avant à la version principale supérieure la plus basse, et la version mineure la plus basse, si la version majeure demandée est manquante. Si la version majeure demandée est présente, la stratégie Minor est utilisée.
  - `LatestMinor`- Rouler vers la version mineure la plus élevée, même si la version mineure demandée est présente. Conçu pour les scénarios d’hébergement de composant.
  - `LatestMajor`- Rouler vers l’avant à la plus haute version mineure majeure et la plus élevée, même si demandé majeur est présent. Conçu pour les scénarios d’hébergement de composant.
  - `Disable`- Ne roulez pas vers l’avant. Lier uniquement à la version spécifiée. Cette stratégie n’est pas recommandée pour une utilisation générale, car elle désactive la possibilité d’effectuer une restauration par progression vers les derniers correctifs. Cette valeur est recommandée uniquement à des fins de test.

À l’exception de `Disable`, tous les paramètres utiliseront la version patch disponible la plus élevée.

Le comportement de roll forward peut également être configuré dans une propriété de fichier de projet, une propriété de fichier de configuration de temps d’exécution, et une variable d’environnement. Pour plus d’informations, voir [Le roll time de la version majeure vers l’avant](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).

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
| [test dotnet](dotnet-test.md)                 | Exécute des tests à l’aide d’un lanceur de tests.                                     |

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
[dotnet nuget push](dotnet-nuget-push.md) | Effectue une transmission de type push d’un package sur le serveur et le publie.
[dotnet nuget locals](dotnet-nuget-locals.md) | Efface ou liste les ressources NuGet locales telles que le cache de requête HTTP, le cache temporaire ou le dossier de packages globaux à l’échelle de l’ordinateur.
[dotnet nuget ajouter source](dotnet-nuget-add-source.md) | Ajoute une source NuGet.
[dotnet nuget source désactiver](dotnet-nuget-disable-source.md) | Désactive une source NuGet.
[dotnet nuget activer la source](dotnet-nuget-enable-source.md) | Permet une source NuGet.
[dotnet nuget liste source](dotnet-nuget-list-source.md) | Répertorie toutes les sources NuGet configurées.
[dotnet nuget supprimer la source](dotnet-nuget-remove-source.md) | Supprime une source NuGet.
[source de mise à jour de nuget dotnet](dotnet-nuget-update-source.md) | Mise à jour d’une source NuGet.

### <a name="global-tool-path-and-local-tools-commands"></a>Commandes d’outils mondiaux, d’outils et d’outils locaux

Les outils sont des applications de console qui sont installées à partir de paquets NuGet et sont invoquées à partir de l’invite de commande. Vous pouvez écrire des outils vous-même ou installer des outils écrits par des tiers. Les outils sont également connus sous le nom d’outils globaux, d’outils de chemin à outils et d’outils locaux. Pour plus d’informations, voir [.NET Core outils aperçu](global-tools.md). Des outils globaux et de chemin d’outils sont disponibles à partir de .NET Core SDK 2.1. Les outils locaux sont disponibles à partir de .NET Core SDK 3.0.

Commande | Fonction
--- | ---
[dotnet tool install](dotnet-tool-install.md) | Installe un outil sur votre machine.
[dotnet tool list](dotnet-tool-list.md) | Répertorie tous les outils globaux, de chemin d’outils ou locaux actuellement installés sur votre machine.
[dotnet tool uninstall](dotnet-tool-uninstall.md) | Désinstalle un outil de votre machine.
[dotnet tool update](dotnet-tool-update.md) | Mise à jour d’un outil qui est installé sur votre machine.

### <a name="additional-tools"></a>Outils supplémentaires

À partir de .NET Core SDK 2.1.300, un certain nombre d’outils qui étaient disponibles uniquement par projet à l’aide de `DotnetCliToolReference` sont désormais disponibles dans le cadre du Kit de développement .NET Core. Ces outils sont répertoriés dans le tableau suivant :

| Outil                                              | Fonction                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | Crée et gère les certificats de développement.                |
| [Ef](/ef/core/miscellaneous/cli/dotnet)           | Outils en ligne de commande Entity Framework Core.                    |
| sql-cache                                         | Outils en ligne de commande du cache SQL Server.                         |
| [user-secrets](/aspnet/core/security/app-secrets) | Gère les secrets de développement de l’utilisateur.                            |
| [Regarder](/aspnet/core/tutorials/dotnet-watch)      | Démarre un observateur de fichier qui exécute une commande à chaque modification de fichier. |

Pour plus d’informations sur chaque outil, tapez `dotnet <tool-name> --help`.

## <a name="examples"></a>Exemples

Créez une nouvelle application de console .NET Core :

```dotnetcli
dotnet new console
```

Générez un projet et ses dépendances dans un répertoire donné :

```dotnetcli
dotnet build
```

Exécuter une application:

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>Variables d'environnement

- `DOTNET_ROOT`, `DOTNET_ROOT(x86)`

  Spécifie l’emplacement des temps d’exécution .NET Core, s’ils ne sont pas installés dans l’emplacement par défaut. L’emplacement par `C:\Program Files\dotnet`défaut sur Windows est . L’emplacement par défaut sur `/usr/share/dotnet`Linux et macOS est . Cette variable d’environnement n’est utilisée que lorsque vous exécutez des applications via des exécutables générés (apphosts). `DOTNET_ROOT(x86)`est utilisé à la place lors de l’exécution d’un 32 bits exécutable sur un système d’exploitation 64 bits.

- `DOTNET_PACKAGES`

  Le dossier de packages global. S’il n’est pas défini, les valeurs par défaut sont `~/.nuget/packages` sous Unix et `%userprofile%\.nuget\packages` sous Windows.

- `DOTNET_SERVICING`

  Spécifie l’emplacement de l’index de service que doit utiliser l’hôte partagé lors du chargement de l’exécution.

- `DOTNET_NOLOGO`

  Précise si les messages de bienvenue et de télémétrie .NET Core sont affichés en première diffusion. Configurez `true` pour couper ces `true` `1`messages `yes` (valeurs, , `false` ou acceptés) ou définis pour permettre (valeurs, `false` `0`, ou `no` accepté). Si elle n’est `false` pas définie, la valeur par défaut est et les messages seront affichés en première exécution. Notez que ce drapeau n’a `DOTNET_CLI_TELEMETRY_OPTOUT` aucun effet sur la télémétrie (voir pour refuser d’envoyer de la télémétrie).

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  Spécifie si les données concernant l’utilisation des outils .NET Core doivent être collectées et envoyées à Microsoft. Définie sur `true` pour ne pas adhérer à la fonctionnalité de télémétrie (valeurs acceptées : `true`, `1` ou `yes`). Sinon, définie sur `false` pour adhérer aux fonctionnalités de télémétrie (valeurs acceptées : `false`, `0` ou `no`). Si elle n’est pas définie, la valeur par défaut est `false`, et la fonctionnalité de télémétrie est active.

- `DOTNET_MULTILEVEL_LOOKUP`

  Spécifie si le runtime .NET Core, le framework partagé ou le SDK sont résolus à partir de l’emplacement global. Si elle n’est pas réglée, `true`elle par défaut à 1 (logique). Set à 0 `false`(logique) pour ne pas résoudre à partir de l’emplacement global et ont isolé les installations .NET Core. Pour plus d’informations sur la recherche multiniveau, consultez [Recherche SharedFX multiniveau](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).

- `DOTNET_ROLL_FORWARD`**Disponible en commençant par .NET Core 3.x SDK.**

  Détermine le comportement de rouler vers l’avant. Pour plus d’informations, voir l’option `--roll-forward` plus tôt dans cet article.

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponible en .NET Core 2.x SDK.**

  Désactive la restauration par progression d’une version mineure, si la valeur est `0`. Pour plus d'informations, consultez [Restauration par progression](../whats-new/dotnet-core-2-1.md#roll-forward).

- `DOTNET_CLI_UI_LANGUAGE`

  Définit la langue de l’interface utilisateur CLI en utilisant une valeur locale telle que `en-us`. Les valeurs prises en charge sont les mêmes que pour Visual Studio. Pour plus d’informations, voir la section sur la modification de la langue de l’installateur dans la [documentation d’installation Visual Studio](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019). Les règles de gestionnaire de ressources .NET s’appliquent, de sorte que vous n’avez pas à choisir un match&mdash;exact, vous pouvez également choisir les descendants dans l’arbre. `CultureInfo` Par exemple, si vous `fr-CA`le définissez, le `fr` CLI trouvera et utilisera les traductions. Si vous le définissez dans une langue qui n’est pas prise en charge, l’IMC retombe à l’anglais.

- `DOTNET_DISABLE_GUI_ERRORS`

  Pour les exécutables générés par l’INTERFACE graphique - désactive le dialogue popup, qui montre normalement pour certaines classes d’erreurs. Il n’écrit `stderr` et sort que dans ces cas.
  
- `DOTNET_ADDITIONAL_DEPS`

  Équivalent à l’option `--additional-deps`CLI .

- `DOTNET_RUNTIME_ID`

  Remplace le RID détecté.

- `DOTNET_SHARED_STORE`

  L’emplacement du « magasin partagé » auquel la résolution d’assemblage revient dans certains cas.

- `DOTNET_STARTUP_HOOKS`

  Liste des assemblages à charger et exécuter des crochets de démarrage à partir de.

- `COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`

  Contrôle les diagnostics traçant à `dotnet.exe`partir `hostfxr`des `hostpolicy`composants d’hébergement, tels que , , et .

## <a name="see-also"></a>Voir aussi

- [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [paramètres de configuration de temps d’exécution .NET Core](../run-time-config/index.md)
