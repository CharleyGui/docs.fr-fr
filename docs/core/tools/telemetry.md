---
title: Télémétrie du kit SDK .NET Core
description: Découvrez les fonctionnalités de télémétrie du kit SDK .NET Core, qui collecte des informations d’utilisation à des fins d’analyse, les types de données collectées et comment désactiver la télémétrie.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: abc9f8e1ef134ebfb5ec9acacb629d5180aaf83b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625915"
---
# <a name="net-core-sdk-telemetry"></a>Télémétrie du kit SDK .NET Core

Le kit [SDK .NET Core](index.md) comprend une fonctionnalité de télémétrie qui collecte les données d’utilisation et les informations sur les exceptions quand l’interface CLI .NET Core plante. L’interface CLI .NET Core s’accompagne du kit SDK .NET Core. C’est cet ensemble de verbes qui vous permet de générer, tester et publier vos applications .NET Core. Il est important pour l’équipe .NET de comprendre comment les outils sont utilisés afin de les améliorer. Les informations sur les échecs aident l’équipe à résoudre les problèmes et à corriger les bogues.

Les données collectées sont anonymes et publiées de manière groupée selon les termes de la [licence Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/). 

## <a name="scope"></a>Étendue

`dotnet` a deux fonctions : exécuter les applications et exécuter les commandes CLI. Les informations de télémétrie *ne sont pas collectées* quand vous utilisez `dotnet` pour démarrer une application au format suivant :

- `dotnet [path-to-app].dll`

Les informations de télémétrie *sont collectées* quand vous utilisez les [commandes de l’interface CLI .NET Core](index.md), par exemple :

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Comment désactiver la fonctionnalité

La fonctionnalité de télémétrie du kit SDK .NET Core est activée par défaut. Pour désactiver la fonctionnalité de télémétrie, définissez la variable d’environnement `DOTNET_CLI_TELEMETRY_OPTOUT` sur `1` ou `true`. 

Une entrée de télémétrie unique est aussi envoyée par le programme d’installation du kit SDK .NET Core quand l’installation aboutit. Pour désactiver cette fonctionnalité, définissez la variable d’environnement `DOTNET_CLI_TELEMETRY_OPTOUT` avant d’installer le kit SDK .NET Core.

## <a name="disclosure"></a>Divulgation d’informations

Le kit SDK .NET Core affiche un texte similaire au suivant quand vous exécutez pour la première fois l’une des [commandes CLI .NET Core](index.md) (par exemple `dotnet build`). Le texte peut varier légèrement selon la version du SDK que vous exécutez. Lors de cette première exécution, Microsoft vous informe sur la collecte de données.

```console
Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience. The data is anonymous. It is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="data-points"></a>Points de données

La fonctionnalité de télémétrie ne collecte pas de données personnelles, comme les noms d’utilisateurs et les adresses e-mail. Elle n’analyse pas votre code et n’extrait pas de données au niveau du projet, comme le nom, le référentiel ou l’auteur. Les données sont envoyées de manière sécurisée à des serveurs Microsoft à l’aide de la technologie [Azure Monitor](https://azure.microsoft.com/services/monitor/), stockées à un emplacement dont l’accès est strictement limité et publiées conformément à des contrôles de sécurité stricts à partir de systèmes [Stockage Azure](https://azure.microsoft.com/services/storage/) sécurisés.

Nous prenons la protection de vos données au sérieux. Si vous pensez que la fonctionnalité de télémétrie collecte des données sensibles ou que les données sont gérées de manière non sécurisée ou incorrecte, signalez un problème dans le dépôt [dotnet/cli](https://github.com/dotnet/cli/issues) ou envoyez un e-mail à [dotnet@microsoft.com](mailto:dotnet@microsoft.com) afin que nous étudions le problème.

La fonctionnalité de télémétrie collecte les données suivantes :

| Versions du SDK | Données |
|--------------|------|
| Tous          | Horodatage de l’appel. |
| Tous          | Commande appelée (par exemple, « build »), hachée à partir de la version 2.1. |
| Tous          | Adresse IP de trois octets utilisée pour déterminer l’emplacement géographique. |
| Tous          | Système d’exploitation et version. |
| Tous          | ID du runtime (RID) sur lequel le kit SDK s’exécute. |
| Tous          | Version du kit SDK .NET Core. |
| Tous          | Profil de télémétrie : valeur facultative utilisée uniquement avec l’adhésion explicite de l’utilisateur et employée en interne par Microsoft. |
| >=2.0        | Arguments et options de commande : plusieurs arguments et options sont collectés (pas de chaînes arbitraires). Consultez [options collectées](#collected-options). Hachage après la version 2.1.300. |
| >=2.0         | Si le SDK est en cours d’exécution dans un conteneur. |
| >=2.0         | Frameworks cibles (tirés de l’événement `TargetFramework`), hachés à partir de la version 2.1. |
| >=2.0         | Adresse MAC (Media Access Control) hachée : ID unique et anonyme (SHA256) du point de vue du chiffrement pour une machine. |
| >=2.0         | Répertoire de travail actuel haché. |
| >=2.0         | Rapport d’installation réussie, avec hachage du nom de fichier .exe du programme d’installation. |
| >=2.1.300     | Version du noyau. |
| >=2.1.300     | Version de Libc. |
| >=3.0.100     | Indique si la sortie a été redirigée (true ou false). |
| >=3.0.100     | En cas de plantage CLI/SDK, type d’exception et rapport des appels de procédures (seul le code CLI/SDK est inclus dans le rapport des appels de procédure envoyé). Pour plus d’informations, consultez [Informations de télémétrie collectées en cas d’exception résultant d’un plantage CLI/SDK .NET Core](#net-core-clisdk-crash-exception-telemetry-collected). |

### <a name="collected-options"></a>Options collectées

Certaines commandes envoient des données supplémentaires. Un sous-ensemble de commandes envoie le premier argument :

| Commande               | Données du premier argument envoyées                |
|-----------------------|-----------------------------------------|
| `dotnet help <arg>`   | La commande help fait l’objet d’une requête.  |
| `dotnet new <arg>`    | Nom du modèle (haché).             |
| `dotnet add <arg>`    | Mot `package` ou `reference`.      |
| `dotnet remove <arg>` | Mot `package` ou `reference`.      |
| `dotnet list <arg>`   | Mot `package` ou `reference`.      |
| `dotnet sln <arg>`    | Mot `add`, `list` ou `remove`.    |
| `dotnet nuget <arg>`  | Mot `delete`, `locals` ou `push`. |

Un sous-ensemble de commandes envoie les options sélectionnées si elles sont utilisées, ainsi que leurs valeurs :

| Option                  | Commandes                                                                                       |
|-------------------------|------------------------------------------------------------------------------------------------|
| `--verbosity`           | Toutes les commandes                                                                                   |
| `--language`            | `dotnet new`                                                                                   |
| `--configuration`       | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`                  |
| `--framework`           | `dotnet build`, `dotnet clean`, `dotnet publish`, `dotnet run`, `dotnet test`, `dotnet vstest` |
| `--runtime`             | `dotnet build`, `dotnet publish`                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

À l’exception de `--verbosity` et `--sdk-package-version`, toutes les autres valeurs sont hachées à partir du SDK .NET Core 2.1.100.

## <a name="net-core-clisdk-crash-exception-telemetry-collected"></a>Informations de télémétrie collectées en cas d’exception résultant d’un plantage CLI/SDK .NET Core

Si l’interface CLI ou le kit SDK .NET Core plante, le nom de l’exception et le rapport des appels de procédure du code CLI/SDK sont collectés. Ces informations permettent d’évaluer les problèmes et d’améliorer la qualité du kit SDK .NET Core et de l’interface CLI. Cet article fournit des informations sur les données que nous collectons. Il fournit aussi des conseils sur la façon dont les utilisateurs qui créent leur propre version du SDK .NET Core peuvent éviter de divulguer par inadvertance des informations personnelles ou sensibles.

### <a name="types-of-collected-data"></a>Types de données collectées

L’interface CLI .NET Core collecte des informations pour les exceptions CLI/SDK uniquement, et non pour les exceptions de votre application. Les données collectées contiennent le nom de l’exception et le rapport des appels de procédure. Ce rapport porte sur le code CLI/SDK.

L’exemple suivant montre le type des données collectées :

```console
System.IO.IOException
at System.ConsolePal.WindowsConsoleStream.Write(Byte[] buffer, Int32 offset, Int32 count)
at System.IO.StreamWriter.Flush(Boolean flushStream, Boolean flushEncoder)
at System.IO.StreamWriter.Write(Char[] buffer)
at System.IO.TextWriter.WriteLine()
at System.IO.TextWriter.SyncTextWriter.WriteLine()
at Microsoft.DotNet.Cli.Utils.Reporter.WriteLine()
at Microsoft.DotNet.Tools.Run.RunCommand.EnsureProjectIsBuilt()
at Microsoft.DotNet.Tools.Run.RunCommand.Execute()
at Microsoft.DotNet.Tools.Run.RunCommand.Run(String[] args)
at Microsoft.DotNet.Cli.Program.ProcessArgs(String[] args, ITelemetry telemetryClient)
at Microsoft.DotNet.Cli.Program.Main(String[] args)
```

### <a name="avoid-inadvertent-disclosure-of-information"></a>Éviter la divulgation involontaire des informations

Les contributeurs .NET Core et les autres personnes exécutant une version du kit SDK .NET Core qu’ils ont eux-mêmes créée doivent prendre en considération le chemin du code source de leur kit SDK. Si un plantage se produit pendant l’utilisation d’un kit SDK .NET Core qui correspond à une build de débogage personnalisée ou qui est configurée avec des fichiers de symboles de build personnalisés, le chemin des fichiers sources du SDK de la machine de build est collecté dans le rapport des appels de procédure et n’est pas haché.

Pour cette raison, les builds personnalisées du kit SDK .NET Core ne doivent pas être placées dans des répertoires dont les noms du chemin exposent des informations personnelles ou sensibles. 

## <a name="see-also"></a>Voir aussi

- [.NET Core CLI Telemetry - 2019 Q2 Data](https://dotnet.microsoft.com/platform/telemetry/dotnet-core-cli-2019q2)
- [Source d’informations de référence sur la télémétrie (dépôt dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
