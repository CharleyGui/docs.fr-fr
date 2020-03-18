---
title: Restauration par progression du runtime pour les déploiements d’applications autonomes .NET Core.
description: Découvrez-en plus sur les modifications apportées à la commande dotnet publish pour les déploiements autonomes.
author: KathleenDollard
ms.date: 05/31/2018
ms.openlocfilehash: 22385c7b5d2bf87755fd51cd6268d21fe3431c74
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75740783"
---
# <a name="self-contained-deployment-runtime-roll-forward"></a>Restauration par progression du runtime de déploiement autonome

[Les déploiements d’applications autonomes](index.md) .NET Core incluent à la fois les bibliothèques .NET Core et le runtime .NET Core. À compter du SDK .NET Core 2.1 (version 2.1.300), un déploiement d’applications autonome [publie le runtime du correctif le plus élevé sur votre machine](https://github.com/dotnet/designs/pull/36). Par défaut, [`dotnet publish`](../tools/dotnet-publish.md) pour un déploiement autonome sélectionne la dernière version installée dans le cadre du SDK sur la machine d’édition. Ainsi, votre application déployée peut exécuter des correctifs de sécurité (et d’autres correctifs) disponibles pendant `publish`. La demande doit être rééditée pour obtenir un nouveau correctif. Les applications autonomes sont créées en spécifiant `-r <RID>` dans la commande `dotnet publish` ou en spécifiant l’[identificateur du runtime (RID)](../rid-catalog.md) dans le fichier projet (csproj/vbproj) ou sur la ligne de commande.

## <a name="patch-version-roll-forward-overview"></a>Vue d’ensemble de la restauration par progression d’une version de correctif

[`restore`](../tools/dotnet-restore.md), [`build`](../tools/dotnet-build.md) [`publish`](../tools/dotnet-publish.md) et `dotnet` sont des commandes qui peuvent fonctionner séparément. Le choix du runtime fait partie de l’opération `restore`, et non de `publish` ou `build`. Si vous appelez `publish`, la dernière version du correctif est choisie. Si vous appelez `publish` avec l’argument `--no-restore`, alors vous risquez de ne pas obtenir la version de correctif voulue, car un `restore` antérieur n’a peut-être pas été exécuté avec la nouvelle stratégie de publication des applications autonomes. Dans ce cas, une erreur de build est générée avec un texte similaire au suivant :

  « Le projet a été restauré à l’aide de Microsoft.NETCore.App version 2.0.0, mais avec les paramètres actuels, la version 2.0.6 serait plutôt utilisée. Pour résoudre ce problème, vérifiez que les mêmes paramètres sont utilisés pour la restauration et pour les opérations qui suivent, comme la génération ou la publication. En général, ce problème peut se produire si la propriété RuntimeIdentifier est définie lors de la génération ou de la publication, mais pas lors de la restauration.

> [!NOTE]
> `restore` et `build` peut être exécutées implicitement dans le cadre d’une autre commande, comme `publish`. Quand vous exécutez une commande implicitement dans le cadre d’une autre commande, un contexte supplémentaire est fourni afin de produire les artefacts adéquats. Quand vous exécutez une commande `publish` avec un runtime (par exemple, `dotnet publish -r linux-x64`), la commande `restore` implicite restaure les packages du runtime linux-x64. Si vous appelez `restore` explicitement, les packages du runtime ne sont pas restaurés par défaut, car ce contexte n’est pas fourni.

## <a name="how-to-avoid-restore-during-publish"></a>Comment éviter la restauration pendant la publication

L’exécution de `restore` dans le cadre de l’opération `publish` peut ne pas convenir à votre scénario. Pour éviter `restore` pendant `publish` quand vous créez des applications autonomes, procédez effectuez les étapes suivantes :

- Définissez la propriété `RuntimeIdentifiers` sur une liste séparée par des points-virgules de tous les [RID](../rid-catalog.md) à publier.
- Attribuez à la propriété `TargetLatestRuntimePatch` la valeur `true`.

## <a name="no-restore-argument-with-dotnet-publish-options"></a>Argument No-restore avec des options dotnet publish

Pour créer à la fois des applications autonomes et des [applications dépendant du framework](index.md) avec le même fichier projet, quand vous voulez utiliser l’argument `--no-restore` avec `dotnet publish`, choisissez l’une des possibilités suivantes :

1. Préférez le comportement dépendant du framework. Si l’application dépend du framework, il s’agit du comportement par défaut. Si l’application est autonome et peut utiliser un runtime local 2.1.0 sans correctif, définissez `TargetLatestRuntimePatch` sur `false` dans le fichier projet.

2. Préférez le comportement autonome. Si l’application est autonome, il s’agit du comportement par défaut. Si l’application dépend du framework et nécessite l’installation du dernier correctif, définissez `TargetLatestRuntimePatch` sur `true` dans le fichier projet.

3. Prenez le contrôle explicite de la version du framework du runtime en définissant `RuntimeFrameworkVersion` sur la version de correctif spécifique dans le fichier projet.
