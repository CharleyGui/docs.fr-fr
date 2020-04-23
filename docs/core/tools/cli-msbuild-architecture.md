---
title: Architecture des outils en ligne de commande .NET Core
description: Découvrez les différentes couches des outils .NET Core et les changements apportés aux versions récentes.
ms.date: 03/06/2017
ms.openlocfilehash: e1a9fe59225c17d54f6e7213d2b3c3fa70ee58e0
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102877"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Vue d’ensemble générale des modifications des outils .NET Core

Ce document décrit les modifications associées de passage de *project.json* à MSBuild et au système de projet *csproj*, avec des informations sur les modifications apportées aux couches d’outils .NET Core et à l’implémentation des commandes de l’interface CLI. Ces modifications ont été apportées lors du lancement du Kit de développement logiciel (SDK) .NET Core 1.0 et de Visual Studio 2017 le 7 mars 2017 (consultez [l’annonce](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)), mais ont été à l’origine implémentées avec le lancement de la préversion 3 du Kit SDK .NET Core.

## <a name="moving-away-from-projectjson"></a>Abandon de project.json

Le plus grand changement apporté aux outils pour .NET Core est certainement le [passage du système de projet project.json à csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/). Les dernières versions des outils en ligne de commande ne prennent pas en charge les fichiers *project.json*. Cela signifie qu’il ne peut pas être utilisé pour construire, exécuter ou publier des applications et des bibliothèques basées sur project.json. Pour utiliser cette version des outils, migrez vos projets existants ou en démarrez de nouveaux.

Dans le cadre de ce passage, le moteur de génération personnalisé qui a été développé pour générer des projets project.json a été remplacé par un moteur de génération mature et entièrement compatible appelé [MSBuild](https://github.com/Microsoft/msbuild). MSBuild est un moteur bien connu dans la communauté .NET. Il a été une technologie clé depuis la première version de la plate-forme. Parce qu’il a besoin de construire des applications .NET Core, MSBuild a été porté à .NET Core et peut être utilisé sur n’importe quelle plate-forme que .NET Core s’exécute sur. Une des principales promesses de .NET Core réside dans une pile de développement multiplateforme, et nous avons veillé à ce que cette évolution n’entrave pas cette promesse.

> [!TIP]
> Si vous êtes nouveau à MSBuild et souhaitez en savoir plus à ce sujet, vous pouvez commencer par lire l’article [msBuild concepts.](/visualstudio/msbuild/msbuild-concepts)

## <a name="the-tooling-layers"></a>Les couches des outils

Avec le changement de moteur de construction et l’abandon du système de projet existant, certaines questions suivent naturellement. Est-ce que l’un de ces changements modifie la « superposition » globale de l’écosystème d’outillage .NET Core? Existe-t-il de nouvelles parties et composants ?

Commençons par un rappel rapide de l’organisation en couches de Preview 2, comme l’illustre l’image suivante :

![Architecture générale des outils Preview 2](media/cli-msbuild-architecture/p2-arch.png)

La superposition des outils dans Preview 2 est simple. Au fond, la fondation est le CLI .NET Core. Tous les autres outils de niveau supérieur, tels que Visual Studio ou Visual Studio Code, dépendent et comptent sur l’OPC pour construire des projets, restaurer les dépendances, et ainsi de suite. Par exemple, si Visual Studio voulait effectuer une opération `dotnet restore` de restauration, il ferait appel à la commande dans l’ICI.

Avec le passage au nouveau système de projet, le schéma précédent change :

![Architecture générale du SDK .NET Core 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

La principale différence est que l’interface de ligne de commande n’est plus la couche de base, ce rôle étant rempli par le « composant SDK partagé ». Ce composant SDK partagé est un ensemble d’objectifs et de tâches associées qui sont responsables de la compilation du code, de sa publication, de l’emballage des paquets NuGet, etc. Le .NET Core SDK est open-source et est disponible sur GitHub sur le [repo SDK](https://github.com/dotnet/sdk).

> [!NOTE]
> Une « cible » est un terme MSBuild qui indique une opération nommée que MSBuild peut invoquer. Elle est généralement associée à une ou plusieurs tâches qui exécutent une logique que la cible est supposée effectuer. MSBuild prend en charge plusieurs cibles prédéfinies telles que `Copy` ou `Execute`, et permet aussi aux utilisateurs d’écrire leurs propres tâches à l’aide de code managé et de définir des cibles pour exécuter ces tâches. Pour plus d’informations, consultez [Tâches MSBuild](/visualstudio/msbuild/msbuild-tasks).

Tous les ensembles d’outils utilisent désormais le composant SDK partagé et ses cibles, interface de ligne de commande incluse. Par exemple, Visual Studio 2019 n’appelle pas dans la `dotnet restore` commande pour restaurer les dépendances pour les projets .NET Core. Au lieu de cela, il utilise la cible "Restaurer" directement. Comme il s’agit de cibles de MSBuild, vous pouvez également utiliser MSBuild sous forme brute pour les exécuter à l’aide de la commande [dotnet msbuild](dotnet-msbuild.md).

### <a name="cli-commands"></a>Commandes CLI

Le composant SDK partagé signifie que la majorité des commandes CLI existantes ont été réimplantées en tant que tâches et cibles MSBuild. Que cela signifie-t-il pour les commandes CLI et votre utilisation de l’ensemble d’outils ?

Du point de vue de l’utilisation, cela ne change pas la façon dont vous utilisez l’IMC. Le CLI a encore les commandes de base qui existaient dans le .NET Core 1.0 Aperçu 2 version:

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Ces commandes font toujours ce que vous attendez d’eux pour faire (nouveau projet, construire, le publier, l’emballer, et ainsi de suite). Vous pouvez consulter soit l’écran `dotnet <command> --help`d’aide de la commande (en utilisant ) ou la documentation sur ce site pour se familiariser avec leur comportement.

Du point de vue de l’exécution, les commandes CLI prennent leurs paramètres et construisent un appel à MSBuild « brut » qui définit les propriétés nécessaires et exécute la cible désirée. Pour mieux illustrer ce propos, considérons la commande suivante :

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

Cette commande publie une `pub` application dans un dossier à l’aide de la configuration "Release". En interne, cette commande se traduit par l’appel MSBuild suivant :

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Les exceptions notables `new` à `run` cette règle sont les et les commandes. Ils n’ont pas été mis en œuvre comme cibles MSBuild.

### <a name="implicit-restore"></a>Restauration implicite

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
