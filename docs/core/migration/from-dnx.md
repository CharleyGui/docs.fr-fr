---
title: Migration de DNX vers l’interface CLI .NET Core
description: Migrez des outils DNX vers les outils de l’interface CLI .NET Core.
ms.date: 06/20/2016
ms.openlocfilehash: e15e7ce10bb7a36deb2acd2abb9a0bd4ec8cd4a9
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920624"
---
# <a name="migrating-from-dnx-to-net-core-cli-projectjson"></a>Migration de DNX vers l’interface CLI .NET Core (project.json)

## <a name="overview"></a>Vue d'ensemble de
Avec la version RC1 de .NET Core et ASP.NET Core 1.0, nous avons introduit les outils DNX. Avec la version RC2 de .NET Core et ASP.NET Core 1.0, nous sommes passés de DNX à l’interface CLI .NET Core.

Pour rappel, revenons sur ce qu’était DNX. DNX était un runtime et un ensemble d’outils qui servait à générer des applications .NET Core et, plus précisément, des applications ASP.NET Core 1.0. Il était constitué de 3 composants principaux :

1. DNVM : script d’installation pour obtenir DNX.
2. DNX (Dotnet Execution Runtime) : runtime chargé d’exécuter votre code.
3. DNU (Dotnet Developer Utility) : outils permettant de gérer les dépendances, générer et publier les applications.

Avec l’introduction de l’interface CLI, tous les éléments ci-dessus sont désormais intégrés à un même ensemble d’outils. Cependant, comme DNX était disponible du temps de RC1, vous vous en êtes peut-être servi pour créer des projets et souhaitez maintenant passer aux nouveaux outils CLI.

Vous trouverez dans ce guide de migration les points essentiels à connaître pour migrer des projets de DNX vers l’interface CLI .NET Core. Si vous voulez simplement créer un projet sur .NET Core de toutes pièces, vous pouvez sans problème ignorer ce document.

## <a name="main-changes-in-the-tooling"></a>Principales évolutions des outils
Les outils ont fait l’objet de modifications générales dont il convient tout d’abord d’exposer les grandes lignes.

### <a name="no-more-dnvm"></a>Disparition de DNVM
DNVM (*DotNet Version Manager*) était un script bash/PowerShell qui servait à installer un DNX sur un ordinateur. Il permettait aux utilisateurs d’obtenir les DNX dont ils avaient à partir du flux qu’ils spécifiaient (ou ceux par défaut), mais aussi de marquer un certain DNX comme étant « actif », ce qui le plaçait sur le $PATH pour la session donnée. Les différents outils pouvaient ainsi être utilisés.

DNVM a été supprimé, car son ensemble de fonctionnalités a été rendu redondant par les modifications apportées au CLI .NET Core.

L’interface CLI est intégrée de deux manières :

1. Programmes d’installation natifs pour une plateforme donnée
2. Script d’installation pour les autres cas (comme les serveurs CI)

Compte tenu de cela, les fonctionnalités d’installation de DNVM ne sont pas nécessaires. Mais qu’en est-il des fonctionnalités de sélection de runtime ?

Pour référencer un runtime dans votre fichier `project.json`, vous devez ajouter un package d’une certaine version à vos dépendances. Cette modification permettra à votre application d’utiliser les nouveaux éléments de runtime. Rien ne différencie l’installation de ces éléments sur votre ordinateur de celle de l’interface CLI : vous installez le runtime avec l’un des programmes d’installation natifs pris en charge ou à l’aide de son script d’installation.

### <a name="different-commands"></a>Des commandes différentes
Si vous avez utilisé DNX, vous avez utilisé les commandes de l’un de ses trois composants (DNX, DNU ou DNVM). Avec l’interface CLI, certaines de ces commandes ont évolué, d’autres ne sont plus disponibles et d’autres sont identiques mais utilisent une sémantique légèrement différente.

Le tableau ci-dessous montre la correspondance entre les commandes DNX/DNU et leurs équivalents CLI.

| Commande DNX                    | Commande CLI    | Description                                                                                                     |
|--------------------------------|----------------|-----------------------------------------------------------------------------------------------------------------|
| dnx run                        | dotnet run     | Exécute du code à partir de la source.                                                                                           |
| dnu build                      | dotnet build   | Génère un fichier binaire IL de votre code.                                                                                |
| dnu pack                       | dotnet pack    | Empaquète votre code dans un package NuGet.                                                                        |
| DNX \[commande] (par exemple, « dnx web ») | N/A\*          | Dans le contexte de DNX, exécute une commande telle que définie dans le fichier project.json.                                                     |
| dnu install                    | N/A\*          | Dans le contexte de DNX, installe un package en tant que dépendance.                                                            |
| dnu restore                    | dotnet restore | Restaure les dépendances spécifiées dans votre fichier project.json. ([voir la remarque](#dotnet-restore-note))                                                            |
| dnu publish                    | dotnet publish | Publie votre application pour le déploiement dans l’une des trois formes possibles (portable, portable avec natif et autonome). |
| dnu wrap                       | N/A\*          | Dans le contexte de DNX, encapsule un fichier project.json dans un fichier csproj.                                                                    |
| dnu commands                   | N/A\*          | Dans le contexte de DNX, gère les commandes installées globalement.                                                           |

(\*) - ces fonctionnalités ne sont pas prises en charge dans l’interface CLI de par sa conception.

## <a name="dnx-features-that-are-not-supported"></a>Fonctionnalités DNX non prises en charge
Comme le montre le tableau ci-dessus, certaines fonctionnalités de l’environnement de DNX ne sont pas prises en charge dans l’interface CLI, du moins pour l’instant. Dans cette section, nous allons nous intéresser aux fonctionnalités les plus importantes, nous expliquerons les raisons pour lesquelles nous avons décidé de renoncer à leur prise en charge, puis nous vous indiquerons des solutions de contournement au cas où vous en auriez besoin.

### <a name="global-commands"></a>Commandes globales
DNU reposait sur un concept appelé « commandes globales ». Il s’agissait pour l’essentiel d’applications console empaquetées sous forme de packages NuGet avec un script d’interpréteur de commandes qui appelait le DNX spécifié destiné à exécuter l’application.

L’interface CLI ne prend pas en charge ce concept. En revanche, il prend en charge l’ajout de commandes par projet qui peuvent être appelées à l’aide de la syntaxe `dotnet <command>` bien connue.

### <a name="installing-dependencies"></a>Installation de dépendances
À partir de v1, le CLI .NET Core n’a pas de commande `install` pour l’installation des dépendances. Pour installer un package à partir de NuGet, vous devez l’ajouter en tant que dépendance à votre fichier `project.json`, puis exécuter `dotnet restore` ([voir la remarque](#dotnet-restore-note)).

### <a name="running-your-code"></a>Exécution de votre code
Il existe deux façons principales d’exécuter du code. La première consiste à partir de la source, avec `dotnet run`. Contrairement à `dnx run`, aucune compilation en mémoire n’est effectuée. En fait, `dotnet build` est appelé pour générer le code, puis le fichier binaire généré est exécuté.

L’autre méthode consiste à utiliser `dotnet` proprement dit pour exécuter le code. Pour cela, il convient d’indiquer le chemin de votre assembly : `dotnet path/to/an/assembly.dll`.

## <a name="migrating-your-dnx-project-to-net-core-cli"></a>Migration d’un projet DNX vers l’interface CLI .NET Core
Outre l’utilisation de nouvelles commandes pendant que vous travaillez sur votre code, vous allez devoir encore migrer trois éléments majeurs de DNX :

1. Migrez le fichier `global.json`, le cas échéant, pour pouvoir utiliser l’interface CLI.
2. Migrez le fichier projet (`project.json`) proprement dit vers les outils de l’interface CLI.
3. Migrez les API DNX vers leurs équivalents BCL.

### <a name="changing-the-globaljson-file"></a>Modification du fichier global.json
Le fichier `global.json` fait office de fichier de solution pour les projets RC1 et RC2 (ou ultérieurs). Pour que les CLI .NET Core (ainsi que Visual Studio) différencient la version RC1 et les versions ultérieures, elles utilisent la propriété `"sdk": { "version" }` pour faire la distinction entre le projet RC1 et les versions ultérieures. Si `global.json` ne contient pas ce nœud, il est supposé être de la dernière version.

Pour mettre à jour le fichier `global.json`, supprimez la propriété ou définissez-la avec la version exacte des outils que vous voulez utiliser, en l’occurrence, **1.0.0-preview2-003121** :

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```

### <a name="migrating-the-project-file"></a>Migration du fichier projet

L’interface CLI et DNX utilisent le même système de projet basé sur le fichier `project.json`. La syntaxe et la sémantique du fichier projet sont pratiquement identiques, avec de petites différences en fonction des scénarios. Le schéma a également subi quelques modifications, ce que vous pouvez constater dans le [fichier de schéma](http://json.schemastore.org/project).

Si vous créez une application console, vous devez ajouter l’extrait de code suivant à votre fichier projet :

```json
"buildOptions": {
    "emitEntryPoint": true
}
```

Ce code indique à `dotnet build` d’émettre un point d’entrée pour votre application, ce qui rend effectivement le code exécutable. Si vous créez une bibliothèque de classes, omettez simplement la section ci-dessus. Bien sûr, une fois que vous avez ajouté l’extrait de code ci-dessus à votre fichier `project.json`, vous devez ajouter un point d’entrée statique. Suite à l’abandon de DNX, les services DI qu’il proposait ne sont plus disponibles et il convient donc d’utiliser un point d’entrée .NET de base : `static void Main()`.

Si votre `project.json` contient une section « commands », vous pouvez la supprimer. Une partie des commandes qui existaient sous forme de commandes DNU, telles que les commandes de l’interface CLI Entity Framework, sont portées dans l’interface CLI pour devenir des extensions par projet. Si vous avez créé vos propres commandes et que vous les utilisez dans vos projets, vous devez les remplacer par des extensions CLI. Dans ce cas, le nœud `commands` dans `project.json` doit être remplacé par le nœud `tools` et il doit répertorier les dépendances d’outils.

Une fois ces opérations effectuées, vous devez choisir le type de portabilité que vous voulez pour votre application. Avec .NET Core, nous nous sommes employés à mettre à votre disposition une gamme d’options de portabilité. Par exemple, vous pouvez faire de votre application une application entièrement *portable* ou une application *autonome*. L’option d’application portable se rapproche plus du mode de fonctionnement des applications .NET Framework : elle a besoin d’un composant partagé pour être exécutée sur l’ordinateur cible (.NET Core). L’application autonome n’a pas besoin de .NET Core pour être installée sur la cible, mais vous devez produire une application pour chaque système d’exploitation que vous voulez prendre en charge. Ces différents types de portabilité et d’autres sont décrits dans le document sur les [types de portabilité d’application](../deploying/index.md).

Dès lors que vous avez déterminé le type de portabilité que vous voulez utiliser, vous devez modifier le ou les frameworks ciblés. Si vous écriviez des applications pour .NET Core, il est très probable que vous utilisiez `dnxcore50` comme framework ciblé. Avec l’interface CLI et compte tenu des changements apportés par la nouvelle bibliothèque [.NET Standard](../../standard/net-standard.md), vous devez opter pour l’un des frameworks suivants :

1. `netcoreapp1.0` : si vous écrivez des applications sur .NET Core (y compris des applications ASP.NET Core)
2. `netstandard1.6` : si vous écrivez des bibliothèques de classes pour .NET Core

Si vous utilisez d’autres cibles `dnx`, comme `dnx451`, vous devez aussi les modifier. `dnx451` doit être remplacé par `net451`.
Pour plus d’informations, consultez la rubrique [.NET Standard](../../standard/net-standard.md).

Votre fichier `project.json` est maintenant pratiquement prêt. Vous devez parcourir la liste de vos dépendances et les mettre à jour vers leurs versions plus récentes, surtout si vous utilisez des dépendances ASP.NET Core. Si vous utilisez des packages distincts pour les API BCL, vous pouvez utiliser le package de runtime comme indiqué dans le document sur les [types de portabilité d’application](../deploying/index.md).

Dès que vous êtes prêt, vous pouvez tenter une restauration avec `dotnet restore` ([voir la remarque](#dotnet-restore-note)). Selon la version de vos dépendances, vous pouvez rencontrer des erreurs si NuGet ne parvient pas à résoudre les dépendances pour l’un des frameworks ciblés ci-dessus. Il s’agit d’un problème ponctuel ; avec le temps, de plus en plus de packages incluront une prise en charge pour ces frameworks. Pour l’heure, si vous rencontrez ce problème, vous pouvez utiliser l’instruction `imports` dans le nœud `framework` pour indiquer à NuGet qu’il peut restaurer les packages ciblant le framework désigné dans l’instruction « imports ».
Les erreurs de restauration que vous obtenez dans ce cas doivent fournir suffisamment d’informations pour identifier les frameworks que vous devez importer. Si vous êtes un peu perdu ou que vous débutez, le fait de spécifier `dnxcore50` et `portable-net45+win8` dans l’instruction `imports` devrait normalement faire l’affaire. L’extrait de code JSON ci-dessous en constitue une bonne illustration :

```json
    "frameworks": {
        "netcoreapp1.0": {
            "imports": ["dnxcore50", "portable-net45+win8"]
        }
    }
```

L’exécution de `dotnet build` risque d’afficher des erreurs de build, même si leur nombre devrait rester limité. Dès lors que votre code se génère et s’exécute correctement, vous pouvez le tester avec le runner. Exécutez `dotnet <path-to-your-assembly>` et regardez-le s’exécuter.

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
