---
title: Déploiement d’applications .NET Core
description: Découvrez les différentes façons de déployer une application .NET Core.
ms.date: 12/03/2018
ms.openlocfilehash: 425f0d5bf11fd0572825d2025005aacf65d7d2cd
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920876"
---
# <a name="net-core-application-deployment"></a>Déploiement d’applications .NET Core

Vous pouvez créer trois types de déploiement pour les applications .NET Core :

- Déploiement dépendant du framework. Comme son nom l’indique, un déploiement dépendant du framework s’appuie sur la présence d’une version partagée à l’échelle du système de .NET Core sur le système cible. Comme .NET Core est déjà présent, votre application est également portable entre des installations de .NET Core. Votre application contient seulement son propre code et les dépendances tierces qui sont en dehors des bibliothèques .NET Core. Les déploiements dépendant du framework contiennent des fichiers *.dll* qui peuvent être lancés avec [l’utilitaire dotnet](../tools/dotnet.md) à partir de la ligne de commande. Par exemple, `dotnet app.dll` exécute une application nommée `app`.

- Déploiement autonome. Contrairement à un déploiement dépendant du framework, un déploiement autonome ne s’appuie sur la présence d’aucun composant partagé sur le système cible. Tous les composants, notamment les bibliothèques .NET Core et le runtime .NET Core, sont inclus avec l’application et sont isolées des autres applications .NET Core. Les déploiements autonomes incluent un fichier exécutable (comme *app.exe* sur les plateformes Windows pour une application nommée `app`), qui est une version renommée de l’hôte .NET Core spécifique à la plateforme, et un fichier *.dll* (comme *app.dll*), qui est l’application elle-même.

- Exécutables dépendant du framework. Produit un exécutable qui s’exécute sur une plateforme cible. Tout comme les déploiements dépendant du framework (FDD), les exécutables dépendant du framework (FDE) sont spécifiques à la plateforme et ne sont pas autonomes. Ces déploiements utilisent toujours une version .NET Core partagée à l’échelle du système pour s’exécuter. Contrairement à un SCD, votre application contient seulement son propre code et les éventuelles dépendances tierces situées à l’extérieur des bibliothèques .NET Core. Les FDE produisent un fichier exécutable qui s’exécute sur la plateforme cible.

## <a name="framework-dependent-deployments-fdd"></a>Déploiements dépendant du framework

Pour un déploiement dépendant du framework, vous déployez seulement votre application et les dépendances tierces. Votre application utilisera la version de .NET Core présente sur le système cible. Il s’agit du modèle de déploiement par défaut pour les applications .NET Core et ASP.NET Core qui ciblent .NET Core.

### <a name="why-create-a-framework-dependent-deployment"></a>Pourquoi créer un déploiement dépendant du framework ?

Un déploiement dépendant du framework présente plusieurs avantages :

- Vous n’avez pas à définir à l’avance les systèmes d’exploitation cible sur lesquels votre application .NET Core s’exécutera. Comme .NET Core utilise un format de fichier PE commun pour les fichiers exécutables et les bibliothèques quel que soit le système d’exploitation, .NET Core peuvent exécuter votre application quel que soit le système d’exploitation sous-jacent. Pour plus d’informations sur le format de fichier PE, consultez [Format de fichier d’assembly .NET](../../standard/assembly/file-format.md).

- Votre package de déploiement est de petite taille. Vous déployez seulement votre application et ses dépendances, et non pas .NET Core lui-même.

- À moins qu’ils ne soient remplacés, les FDD utiliseront le dernier runtime pris en charge installé sur le système cible. Cela permet à votre application d’utiliser la dernière version corrigée du runtime .NET Core. 

- Plusieurs applications utilisent la même installation de .NET Core, ce qui réduit l’utilisation de l’espace disque et de la mémoire sur les systèmes hôtes.

Il existe également quelques inconvénients :

- Votre application peut s’exécuter seulement si la version de .NET Core ciblée par votre application, [ou une version ultérieure](../versions/selection.md#framework-dependent-apps-roll-forward), est déjà installée sur le système hôte.

- Il est possible que le runtime et les bibliothèques .NET Core changent sans que vous le sachiez dans les versions futures. Dans de rares cas, ceci peut changer le comportement de votre application.

## <a name="self-contained-deployments-scd"></a>Déploiements autonomes

Pour un déploiement autonome, vous déployez votre application et les dépendances tierces requises, ainsi que la version de .NET Core utilisée pour générer l’application. La création d’un déploiement autonome n’inclut pas les [dépendances natives de .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) sur les différentes plateformes. Ces services doivent donc être présents avant l’exécution de l’application. Pour plus d’informations sur la liaison de version lors de l’exécution, consultez l’article sur la [liaison de version dans .NET Core](../versions/selection.md).

À compter du SDK (version 2.1.300) de NET Core 2.1, .NET Core prend en charge la *restauration par progression d’une version de correctif*. Lorsque vous créez un déploiement autonome, les outils .NET Core incluent automatiquement le dernier runtime pris en charge de la version .NET Core que votre application cible. (Le dernier Runtime desservi comprend des correctifs de sécurité et d’autres correctifs de bogues.) Le runtime desservi n’a pas besoin d’être présent sur votre système de génération ; elle est téléchargée automatiquement à partir de NuGet.org. Pour plus d’informations, notamment des instructions sur la façon de refuser la restauration par progression de la version corrective, consultez [restauration par progression du runtime de déploiement autonome](runtime-patch-selection.md).

Les déploiements dépendant de l’infrastructure (FDD) et les déploiements autonomes (SCD) utilisent des exécutables d’hôte distincts : vous pouvez donc signer un exécutable d’hôte pour un déploiement SCD avec votre signature de publieur.

### <a name="why-deploy-a-self-contained-deployment"></a>Pourquoi déployer un déploiement autonome ?

Le déploiement d’un déploiement autonome a deux avantages majeurs :

- Vous avez le contrôle exclusif de la version de .NET Core qui est déployée avec votre application. Vous pouvez vous-même assurer toute la maintenance de .NET Core.

- Vous avez la garantie que le système cible peut exécuter votre application .NET Core puisque vous fournissez la version du .NET Core sur laquelle elle est exécutée.

Elle a également plusieurs inconvénients :

- Comme .NET Core est inclus dans votre package de déploiement, vous devez choisir à l’avance les plateformes cibles pour lesquels vous générez des packages de déploiement.

- La taille de votre package de déploiement est relativement importante car vous devez inclure .NET Core ainsi que votre application et ses dépendances tierces.

  À compter de .NET Core 2.0, vous pouvez réduire la taille de votre déploiement sur les systèmes Linux d’environ 28 Mo à l’aide du [*mode de globalisation invariant*](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md) de .NET Core. En règle générale, .NET Core sur Linux s’appuie sur les [bibliothèques ICU](http://icu-project.org) pour la prise en charge de la globalisation. En mode invariant, les bibliothèques ne sont pas incluses dans votre déploiement, et toutes les cultures se comportent comme la [culture invariante](xref:System.Globalization.CultureInfo.InvariantCulture?displayProperty=nameWithType).

- Le déploiement de nombreuses applications .NET Core autonomes sur un système peut consommer une quantité significative d’espace disque car chaque application duplique les fichiers de .NET Core.

## <a name="framework-dependent-executables-fde"></a>Exécutables dépendant du framework (FDE)

À compter de .NET Core 2.2, vous pouvez déployer votre application en tant que FDE, ainsi que toutes les dépendances tierces requises. Votre application utilisera la version de .NET Core installée sur le système cible.

### <a name="why-deploy-a-framework-dependent-executable"></a>Pourquoi déployer un exécutable dépendant du framework ?

Un déploiement dépendant du framework présente plusieurs avantages :

- Votre package de déploiement est de petite taille. Vous déployez seulement votre application et ses dépendances, et non pas .NET Core lui-même.

- Plusieurs applications utilisent la même installation de .NET Core, ce qui réduit l’utilisation de l’espace disque et de la mémoire sur les systèmes hôtes.

- Votre application peut être exécutée en appelant l’exécutable publié, sans appeler directement l’utilitaire `dotnet`.

Il existe également quelques inconvénients :

- Votre application peut s’exécuter seulement si la version de .NET Core ciblée par votre application, [ou une version ultérieure](../versions/selection.md#framework-dependent-apps-roll-forward), est déjà installée sur le système hôte.

- Il est possible que le runtime et les bibliothèques .NET Core changent sans que vous le sachiez dans les versions futures. Dans de rares cas, ceci peut changer le comportement de votre application.

- Vous devez publier votre application pour chaque plateforme cible.

## <a name="step-by-step-examples"></a>Exemples étape par étape

Pour obtenir des exemples pas à pas de déploiement d’applications .NET Core avec le CLI .NET Core, consultez [publier des applications .net core avec le CLI .net Core](deploy-with-cli.md). Pour obtenir des exemples étape par étape de déploiement d’applications .NET Core avec Visual Studio, consultez [Déploiement d’applications .NET Core avec Visual Studio](deploy-with-vs.md). 

## <a name="see-also"></a>Voir aussi

- [Publier des applications .NET Core avec le CLI .NET Core](deploy-with-cli.md)
- [Déploiement d’applications .NET Core avec Visual Studio](deploy-with-vs.md)
- [Packages, métapackages et frameworks](../packages.md)
- [Catalogue d’identificateurs de runtime (RID) .NET Core](../rid-catalog.md)
