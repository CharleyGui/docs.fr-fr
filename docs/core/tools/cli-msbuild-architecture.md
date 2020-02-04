---
title: Architecture des outils en ligne de commande .NET Core
description: Découvrez les différentes couches des outils .NET Core et les changements apportés aux versions récentes.
ms.date: 03/06/2017
ms.openlocfilehash: 0064e7354f073be618bcf6a79962ab495927fadd
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980208"
---
# <a name="high-level-overview-of-changes-in-the-net-core-tools"></a>Vue d’ensemble générale des modifications des outils .NET Core

Ce document décrit les modifications associées de passage de *project.json* à MSBuild et au système de projet *csproj*, avec des informations sur les modifications apportées aux couches d’outils .NET Core et à l’implémentation des commandes de l’interface CLI. Ces modifications ont été apportées lors du lancement du Kit de développement logiciel (SDK) .NET Core 1.0 et de Visual Studio 2017 le 7 mars 2017 (consultez [l’annonce](https://devblogs.microsoft.com/dotnet/announcing-net-core-tools-1-0/)), mais ont été à l’origine implémentées avec le lancement de la préversion 3 du Kit SDK .NET Core.

## <a name="moving-away-from-projectjson"></a>Abandon de project.json

Le plus grand changement apporté aux outils pour .NET Core est certainement le [passage du système de projet project.json à csproj](https://devblogs.microsoft.com/dotnet/changes-to-project-json/). Les dernières versions des outils en ligne de commande ne prennent pas en charge les fichiers *project.json*. Cela signifie qu’il ne peut pas être utilisé pour générer, exécuter ou publier des applications et des bibliothèques basées sur Project. JSON. Pour utiliser cette version des outils, vous pouvez migrer vos projets existants ou en démarrer de nouveaux.

Dans le cadre de ce passage, le moteur de génération personnalisé qui a été développé pour générer des projets project.json a été remplacé par un moteur de génération mature et entièrement compatible appelé [MSBuild](https://github.com/Microsoft/msbuild). MSBuild est un moteur connu dans la communauté .NET. Il s’agit d’une technologie clé depuis la première version de la plateforme. Étant donné qu’il doit générer des applications .NET Core, MSBuild a été porté sur .NET Core et peut être utilisé sur n’importe quelle plateforme sur laquelle .NET Core s’exécute. Une des principales promesses de .NET Core réside dans une pile de développement multiplateforme, et nous avons veillé à ce que cette évolution n’entrave pas cette promesse.

> [!TIP]
> Si vous débutez avec MSBuild et que vous souhaitez en savoir plus à ce sujet, vous pouvez commencer par lire l’article [concepts de MSBuild](/visualstudio/msbuild/msbuild-concepts) .

## <a name="the-tooling-layers"></a>Les couches des outils

Le fait de quitter le système de projet existant et de changer de moteur de génération suscite naturellement la question de savoir si l’une ou l’autre de ces modifications change l’organisation en couches globale de l’ensemble de l’écosystème des outils .NET Core. Existe-t-il de nouvelles parties et composants ?

Commençons par un rappel rapide de l’organisation en couches de Preview 2, comme l’illustre l’image suivante :

![Architecture générale des outils Preview 2](media/cli-msbuild-architecture/p2-arch.png)

L’organisation en couches des outils est assez simple. En bas, la Fondation est le CLI .NET Core. Tous les autres outils de niveau supérieur, tels que Visual Studio ou Visual Studio Code, dépendent de l’interface CLI pour générer des projets, restaurer des dépendances, etc. Par exemple, si Visual Studio souhaite effectuer une opération de restauration, il appelle la commande `dotnet restore` ([Voir la remarque](#dotnet-restore-note)) dans l’interface CLI.

Avec le passage au nouveau système de projet, le schéma précédent change :

![Architecture générale du SDK .NET Core 1.0.0](media/cli-msbuild-architecture/p3-arch.png)

La principale différence est que l’interface de ligne de commande n’est plus la couche de base, ce rôle étant rempli par le « composant SDK partagé ». Ce composant SDK partagé est un ensemble de cibles et de tâches associées qui sont responsables de la compilation du code, de sa publication, de l’empaquetage des packages NuGet, etc. Le kit SDK .NET Core est open source et est disponible sur GitHub sur le [référentiel SDK](https://github.com/dotnet/sdk).

> [!NOTE]
> Une « cible » est un terme MSBuild qui indique une opération nommée que MSBuild peut appeler. Elle est généralement associée à une ou plusieurs tâches qui exécutent une logique que la cible est supposée effectuer. MSBuild prend en charge plusieurs cibles prédéfinies telles que `Copy` ou `Execute`, et permet aussi aux utilisateurs d’écrire leurs propres tâches à l’aide de code managé et de définir des cibles pour exécuter ces tâches. Pour plus d’informations, consultez [Tâches MSBuild](/visualstudio/msbuild/msbuild-tasks).

Tous les ensembles d’outils utilisent désormais le composant SDK partagé et ses cibles, interface de ligne de commande incluse. Par exemple, Visual Studio 2019 n’appelle pas la commande `dotnet restore` ([Voir la remarque](#dotnet-restore-note)) pour restaurer les dépendances des projets .net core. Au lieu de cela, il utilise directement la cible « Restore ». Comme il s’agit de cibles de MSBuild, vous pouvez également utiliser MSBuild sous forme brute pour les exécuter à l’aide de la commande [dotnet msbuild](dotnet-msbuild.md).

### <a name="cli-commands"></a>Commandes CLI

Le composant SDK partagé signifie que la plupart des commandes CLI existantes ont été réimplémentées comme cibles et tâches MSBuild. Que cela signifie-t-il pour les commandes CLI et votre utilisation de l’ensemble d’outils ?

Du point de vue de l’utilisation, il ne modifie pas la façon dont vous utilisez l’interface CLI. L’interface CLI possède toujours les commandes de base qui existaient dans la version préliminaire 2 de .NET Core 1,0 :

- `new`
- `restore`
- `run`
- `build`
- `publish`
- `test`
- `pack`

Ces commandes effectuent toujours ce que vous attendez (créer un projet, le générer, le publier, le compresser, etc.). Vous pouvez consulter l’écran d’aide de la commande (à l’aide de `dotnet <command> --help`) ou la documentation sur ce site pour vous familiariser avec leur comportement.

Du point de vue de l’exécution, les commandes CLI prennent leurs paramètres et construisent un appel à MSBuild « RAW » qui définit les propriétés nécessaires et exécute la cible souhaitée. Pour mieux illustrer ce propos, considérons la commande suivante :

   ```dotnetcli
   dotnet publish -o pub -c Release
   ```

Cette commande publie une application dans un dossier `pub` à l’aide de la configuration « Release ». En interne, cette commande se traduit par l’appel MSBuild suivant :

   ```dotnetcli
   dotnet msbuild -t:Publish -p:OutputPath=pub -p:Configuration=Release
   ```

Les exceptions notables à cette règle sont les commandes `new` et `run`. Elles n’ont pas été implémentées en tant que cibles MSBuild.

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
