---
title: Télémétrie du SDK .NET
description: Découvrez les fonctionnalités de télémétrie du SDK .NET qui collectent les informations d’utilisation à des fins d’analyse, quelles données sont collectées et comment les désactiver.
author: KathleenDollard
ms.date: 08/27/2019
ms.openlocfilehash: 4f137822c61e1a04eccd28ebd0cd56c04f4a85e2
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633867"
---
# <a name="net-sdk-telemetry"></a>Télémétrie du SDK .NET

Le [Kit de développement logiciel (SDK) .net](index.md) comprend une fonctionnalité de télémétrie qui collecte les données d’utilisation et les informations sur les exceptions lorsque l’interface CLI .net se bloque. L’interface CLI .NET est fournie avec le kit de développement logiciel (SDK) .NET et est l’ensemble de verbes qui vous permet de générer, tester et publier vos applications .NET. Il est important pour l’équipe .NET de comprendre comment les outils sont utilisés afin de les améliorer. Les informations sur les échecs aident l’équipe à résoudre les problèmes et à corriger les bogues.

Les données collectées sont publiées en agrégats dans le cadre de la [licence d’attribution de Creative](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Étendue

`dotnet` a deux fonctions : exécuter les applications et exécuter les commandes CLI. Les informations de télémétrie *ne sont pas collectées* quand vous utilisez `dotnet` pour démarrer une application au format suivant :

- `dotnet [path-to-app].dll`

Les données de télémétrie *sont collectées* lors de l’utilisation des commandes de l' [interface de commande CLI .net](index.md), telles que :

- `dotnet build`
- `dotnet pack`
- `dotnet run`

## <a name="how-to-opt-out"></a>Comment désactiver la fonctionnalité

La fonctionnalité de télémétrie du SDK .NET est activée par défaut. Pour désactiver la fonctionnalité de télémétrie, définissez la variable d’environnement `DOTNET_CLI_TELEMETRY_OPTOUT` sur `1` ou `true`.

Une seule entrée de télémétrie est également envoyée par le programme d’installation du kit de développement logiciel (SDK) .NET lors de la réussite de l’installation. Pour vous désabonner, définissez la `DOTNET_CLI_TELEMETRY_OPTOUT` variable d’environnement avant d’installer le kit de développement logiciel (SDK) .net.

## <a name="disclosure"></a>Divulgation d’informations

Le kit de développement logiciel (SDK) .NET affiche un texte similaire à ce qui suit lors de la première exécution de l’une des commandes de l' [interface de commande CLI .net](index.md) (par exemple, `dotnet build` ). Le texte peut varier légèrement selon la version du SDK que vous exécutez. Lors de cette première exécution, Microsoft vous informe sur la collecte de données.

```console
Telemetry
---------
The .NET tools collect usage data in order to help us improve your experience. The data is collected by Microsoft and shared with the community. You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

Pour désactiver ce message et le message d’accueil .NET, affectez la valeur `DOTNET_NOLOGO` à la variable d’environnement `true` . Notez que cette variable n’a aucun effet sur la désactivation de la télémétrie.

## <a name="data-points"></a>Points de données

La fonctionnalité de télémétrie ne collecte pas de données personnelles, comme les noms d’utilisateurs et les adresses e-mail. Elle n’analyse pas votre code et n’extrait pas de données au niveau du projet, comme le nom, le référentiel ou l’auteur. Les données sont envoyées de manière sécurisée à des serveurs Microsoft à l’aide de la technologie [Azure Monitor](https://azure.microsoft.com/services/monitor/), stockées à un emplacement dont l’accès est strictement limité et publiées conformément à des contrôles de sécurité stricts à partir de systèmes [Stockage Azure](https://azure.microsoft.com/services/storage/) sécurisés.

Nous prenons la protection de vos données au sérieux. Si vous pensez que la télémétrie collecte des données sensibles ou que les données sont gérées de manière inappropriée ou non, envoyez un problème dans le référentiel [dotnet/SDK](https://github.com/dotnet/sdk/issues) ou envoyez un e-mail à [dotnet@microsoft.com](mailto:dotnet@microsoft.com) pour investigation.

La fonctionnalité de télémétrie collecte les données suivantes :

| Versions du SDK | Données |
|--------------|------|
| Tous          | Horodatage de l’appel. |
| Tous          | Commande appelée (par exemple, « build »), hachée à partir de la version 2.1. |
| Tous          | Adresse IP de trois octets utilisée pour déterminer l’emplacement géographique. |
| Tous          | Système d’exploitation et version. |
| Tous          | ID du runtime (RID) sur lequel le kit SDK s’exécute. |
| Tous          | Version du kit de développement logiciel (SDK) .NET. |
| Tous          | Profil de télémétrie : valeur facultative utilisée uniquement avec l’adhésion explicite de l’utilisateur et employée en interne par Microsoft. |
| >=2.0        | Arguments et options de commande : plusieurs arguments et options sont collectés (pas de chaînes arbitraires). Consultez [options collectées](#collected-options). Hachage après la version 2.1.300. |
| >=2.0         | Si le SDK est en cours d’exécution dans un conteneur. |
| >=2.0         | Frameworks cibles (tirés de l’événement `TargetFramework`), hachés à partir de la version 2.1. |
| >=2.0         | Adresse de Access Control de média hachée ((SHA256). |
| >=2.0         | Répertoire de travail actuel haché. |
| >=2.0         | Rapport d’installation réussie, avec hachage du nom de fichier .exe du programme d’installation. |
| >=2.1.300     | Version du noyau. |
| >=2.1.300     | Version de Libc. |
| >=3.0.100     | Indique si la sortie a été redirigée (true ou false). |
| >=3.0.100     | En cas de plantage CLI/SDK, type d’exception et rapport des appels de procédures (seul le code CLI/SDK est inclus dans le rapport des appels de procédure envoyé). Pour plus d’informations, consultez la [télémétrie des exceptions de la CLI .net CLI/SDK collectées](#net-clisdk-crash-exception-telemetry-collected). |

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
| `--runtime`             | `dotnet build`,  `dotnet publish`                                                              |
| `--platform`            | `dotnet vstest`                                                                                |
| `--logger`              | `dotnet vstest`                                                                                |
| `--sdk-package-version` | `dotnet migrate`                                                                               |

À l’exception de `--verbosity` et `--sdk-package-version`, toutes les autres valeurs sont hachées à partir du SDK .NET Core 2.1.100.

## <a name="net-clisdk-crash-exception-telemetry-collected"></a>Télémétrie des exceptions de l’interface de commande .NET CLI/SDK collectées

Si le kit de développement logiciel (CLI) .NET échoue, il collecte le nom de l’exception et la trace de la pile du code CLI/SDK. Ces informations sont collectées pour évaluer les problèmes et améliorer la qualité du kit de développement logiciel (SDK) .NET et de l’interface CLI. Cet article fournit des informations sur les données que nous collectons. Il fournit également des conseils sur la façon dont les utilisateurs qui créent leur propre version du kit de développement logiciel (SDK) .NET peuvent éviter la divulgation accidentelle d’informations personnelles ou sensibles.

### <a name="types-of-collected-data"></a>Types de données collectées

.NET CLI recueille uniquement des informations sur les exceptions CLI/SDK, et non sur les exceptions de votre application. Les données collectées contiennent le nom de l’exception et le rapport des appels de procédure. Ce rapport porte sur le code CLI/SDK.

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

Les contributeurs .NET et toute autre personne exécutant une version du kit de développement logiciel (SDK) .NET qu’ils ont créés eux-mêmes doivent tenir compte du chemin d’accès au code source du SDK. Si un incident se produit lors de l’utilisation d’un kit de développement logiciel (SDK) .NET qui est une version de débogage personnalisée ou configuré avec des fichiers de symboles de build personnalisés, le chemin du fichier source SDK de l’ordinateur de build est collecté dans le cadre de la trace de la pile et n’est pas haché.

Pour cette raison, les versions personnalisées du kit de développement logiciel (SDK) .NET ne doivent pas se trouver dans les répertoires dont les noms de chemin d’accès exposent des informations personnelles

## <a name="see-also"></a>Voir aussi

- [Données de télémétrie de l’interface CLI .NET](https://dotnet.microsoft.com/platform/telemetry)
- [Source de référence de télémétrie (référentiel dotnet/SDK)](https://github.com/dotnet/sdk/tree/master/src/Cli/dotnet/Telemetry)
