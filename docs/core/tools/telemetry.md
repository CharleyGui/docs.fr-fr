---
title: Télémétrie du kit SDK .NET Core
description: Découvrez les fonctionnalités de télémétrie du kit SDK .NET Core, qui collecte des informations d’utilisation à des fins d’analyse, les types de données collectées et comment désactiver la télémétrie.
author: richlander
ms.date: 06/20/2018
ms.custom: seodec18
ms.openlocfilehash: 85cceab08fc6e4108a5b951c8b67c1ad5a28f6bb
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377501"
---
# <a name="net-core-sdk-telemetry"></a>Télémétrie du kit SDK .NET Core

Le [SDK .NET Core](index.md) inclut une [fonctionnalité de télémétrie](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry) qui recueille des informations d’utilisation. Il est important pour l’équipe .NET de comprendre la façon dont les outils sont utilisés, afin de pouvoir les améliorer. Pour plus d’informations, consultez les [enseignements tirés de la fonctionnalité de télémétrie du SDK .NET Core](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/).

Les données collectées sont anonymes et publiées sous forme regroupée en vue d’être utilisées par Microsoft et la communauté, sous la [licence Creative Commons Attribution](https://creativecommons.org/licenses/by/4.0/).

## <a name="scope"></a>Portée

La commande `dotnet` permet de lancer des applications et l’interface CLI .NET Core. La commande `dotnet` ne permet pas de collecter des données de télémétrie. Les commandes de l’interface CLI .NET Core exécutées par la commande `dotnet` collectent les données de télémétrie.

La télémétrie *n’est pas activée* quand vous utilisez la commande `dotnet` sans commande attachée :

- `dotnet`
- `dotnet [path-to-app]`

La télémétrie *est activée* quand vous utilisez les [commandes de l’interface CLI .NET Core](index.md), telles que les suivantes :

- `dotnet build`
- `dotnet pack`
- `dotnet restore`
- `dotnet run`

## <a name="how-to-opt-out"></a>Comment désactiver la fonctionnalité

La fonctionnalité de télémétrie du kit SDK .NET Core est activée par défaut. Pour la désactiver, affectez la valeur `1` ou `true` à la variable d’environnement `DOTNET_CLI_TELEMETRY_OPTOUT`.

## <a name="data-points"></a>Points de données

La fonctionnalité recueille les données suivantes :

- horodatage de l’appel&#8224;
- Commande appelée (par exemple, « build »)&#8224;
- Adresse IP de trois octets utilisée pour déterminer l’emplacement géographique&#8224;
- `ExitCode` de la commande
- Exécuteur de tests (pour les projets de test)
- Système d’exploitation et version&#8224;
- Si des ID d’exécution se trouvent sous le nœud runtimes
- Version du SDK .NET Core&#8224;

&#8224;Cette métrique est publiée.

À compter du SDK .NET Core 2.0, de nouveaux points de données sont collectés :

- Arguments et options de la commande `dotnet` : seuls les arguments et options connus sont collectés (pas les chaînes arbitraires).
- Si le SDK est en cours d’exécution dans un conteneur.
- Frameworks cibles.
- Adresse MAC hachée : ID unique et anonyme chiffré (SHA256) pour une machine. Cette métrique n’est pas publiée.
- Répertoire de travail actuel haché.

La fonctionnalité ne collecte pas les informations personnelles, telles que les noms d’utilisateurs et les adresses e-mail. Elle n’analyse pas votre code et n’extrait pas de données sensibles au niveau du projet, telles que le nom, le dépôt ou l’auteur. Les données sont envoyées en toute sécurité à des serveurs Microsoft à l’aide de la technologie [Microsoft Azure Application Insights](https://azure.microsoft.com/services/application-insights/), stockées à un emplacement dont l’accès est strictement limité et publiées conformément à des contrôles de sécurité stricts à partir de systèmes [Azure Storage](https://azure.microsoft.com/services/storage/) sécurisés.

L’équipe .NET souhaite savoir comment vous utilisez les outils et s’ils fonctionnent correctement, et non ce que vous créez avec les outils. Si vous pensez que la fonctionnalité de télémétrie collecte des données sensibles ou que les données sont gérées de manière non sécurisée ou incorrecte, soumettez un problème dans le dépôt [dotnet/cli](https://github.com/dotnet/cli/issues) afin que nous investiguions.

## <a name="published-data"></a>Données publiées

Les données publiées sont disponibles tous les trimestres et sont répertoriées dans la page [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Données d’utilisation du SDK .NET Core). Les colonnes d’un fichier de données sont les suivantes :

- Horodateur
- Occurrences&#8224;
- Commande
- Geography&#8225;
- OSFamily
- RuntimeID
- OSVersion
- SDKVersion

&#8224;La colonne *Occurrences* totalise le nombre d’utilisations de la commande concernée pour les métriques de la ligne donnée le jour indiqué.

&#8225;En règle générale, la colonne *Geography* affiche le nom d’un pays/d’une région. Dans certains cas, le continent Antarctica (Antarctique) apparaît dans cette colonne si .NET Core est utilisé dans ce continent ou que les données de localisation sont incorrectes.

### <a name="example"></a>Exemple

| Horodateur      | Occurrences | Commande | Geography | OSFamily | RuntimeID     | OSVersion | SDKVersion |
| -------------- | ----------- | ------- | --------- | -------- | ------------- | --------- | ---------- |
| 4/16/2017 0:00 | 8           | run     | Uganda    | Darwin   | osx.10.12-x64 | 10.12     | 1.0.1      |

### <a name="datasets"></a>Groupes de données

- [2016 - T3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q3.tsv)
- [2016 - T4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2016-q4.tsv)
- [2017 - T1](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q1.tsv)
- [2017 - T2](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q2.tsv)
- [2017 - T3](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q3.tsv)
- [2017 - T4](https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-2017-q4.tsv)

Des jeux de données supplémentaires sont publiés à l’aide d’un format d’URL standard. Remplacez `<YEAR>` par l’année, et `<QUARTER>` par le trimestre de l’année (utilisez `1`, `2`, `3` ou `4`). Les fichiers sont au format *TSV* (valeurs séparées par une tabulation).

`https://dotnetcli.blob.core.windows.net/usagedata/dotnet-cli-usage-<YEAR>-q<QUARTER>.tsv`

## <a name="license"></a>Licence

La distribution Microsoft de .NET Core est concédée sous licence avec les [Termes du contrat de licence logicielle Microsoft : Bibliothèque Microsoft .NET](https://aka.ms/dotnet-core-eula). Pour plus d’informations sur la collecte et le traitement de données, consultez la section intitulée « Données ».

Les [packages NuGet .NET](https://www.nuget.org/profiles/dotnetframework) utilisent la même licence, mais ne permettent pas la télémétrie (voir la section [Portée](#scope)).

## <a name="disclosure"></a>Divulgation d’informations

Le kit SDK .NET Core affiche le texte suivant quand vous exécutez pour la première fois l’une des [commandes CLI .NET Core](index.md) (par exemple `dotnet restore`). Le texte peut varier légèrement selon la version du SDK que vous exécutez. Lors de cette première exécution, Microsoft vous informe sur la collecte de données.

```console
Welcome to .NET Core!
---------------------
Learn more about .NET Core: https://aka.ms/dotnet-docs
Use 'dotnet --help' to see available commands or visit: https://aka.ms/dotnet-cli-docs

Telemetry
---------
The .NET Core tools collect usage data in order to help us improve your experience.
The data is anonymous and doesn't include command-line arguments.
The data is collected by Microsoft and shared with the community.
You can opt-out of telemetry by setting the DOTNET_CLI_TELEMETRY_OPTOUT environment variable to '1' or 'true' using your favorite shell.

Read more about .NET Core CLI Tools telemetry: https://aka.ms/dotnet-cli-telemetry
```

## <a name="see-also"></a>Voir aussi

- [What we've learned from .NET Core SDK Telemetry](https://devblogs.microsoft.com/dotnet/what-weve-learned-from-net-core-sdk-telemetry/) (Enseignements tirés de la fonctionnalité de télémétrie du SDK .NET Core)
- [Source de référence de télémétrie (dépôt dotnet/cli)](https://github.com/dotnet/cli/tree/master/src/dotnet/Telemetry)
- [.NET Core SDK Usage Data](https://github.com/dotnet/core/blob/master/release-notes/cli-usage-data.md) (Données d’utilisation du SDK .NET Core)
