---
title: Présentation de C# -vous familiariser avec les outils de développement
description: Cet article constitue une introduction aux outils que vous utiliserez pour développer des applications C# et .NET sur votre ordinateur.
ms.date: 10/23/2018
ms.openlocfilehash: fe39bd5e89bb168316b19c62d6e022e36c58fc2f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850755"
---
# <a name="become-familiar-with-the-net-development-tools"></a>Vous familiariser avec les outils de développement .NET

La première étape pour exécuter un tutoriel sur votre ordinateur consiste à configurer un environnement de développement.
Le didacticiel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) contient des instructions pour la configuration de votre environnement de développement local sur Mac, PC ou Linux.

Vous pouvez aussi installer le [Kit SDK .NET Core](https://dotnet.microsoft.com/download) et [Visual Studio Code](https://code.visualstudio.com/).

## <a name="basic-application-development-flow"></a>Flux de développement d’une application de base

Vous créez des applications à l’aide de la commande [`dotnet new`](../../../core/tools/dotnet-new.md). Cette commande génère les fichiers et ressources nécessaires pour votre application. Les tutoriels de présentation de C# utilisent tous le type d’application `console`. Une fois que vous avez les bases, vous pouvez développer d’autres types d’applications.

Les autres commandes que vous utiliserez sont [`dotnet build`](../../../core/tools/dotnet-build.md) pour générer le fichier exécutable et [`dotnet run`](../../../core/tools/dotnet-run.md) pour exécuter le fichier exécutable.

## <a name="pick-your-tutorial"></a>Choisir un tutoriel

Vous pouvez commencer par l’un des tutoriels suivants :

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[Nombres en C#](numbers-in-csharp-local.md)

Dans le tutoriel [Nombres en C#](numbers-in-csharp-local.md), vous allez apprendre comment les ordinateurs stockent les nombres et comment effectuer des calculs avec différents types numériques. Vous apprendrez les bases de l’arrondi et comment effectuer des calculs mathématiques à l’aide de C#.

Ce tutoriel part du principe que vous avez terminé la leçon [Hello world](hello-world.yml).

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[Branches et boucles](branches-and-loops-local.md)

Le tutoriel [Branches et boucles](branches-and-loops-local.md) explique les bases de la sélection de différents chemins d’exécution de code en fonction des valeurs stockées dans des variables. Vous allez apprendre les principes fondamentaux du flux de contrôle, sur la base duquel les programmes prennent des décisions et choisissent différentes actions.

Ce tutoriel part du principe que vous avez fini les leçons [Hello world](hello-world.yml) et [Nombres en C#](numbers-in-csharp-local.md).

## <a name="list-collectionarrays-and-collectionsmd"></a>[Collection de listes](arrays-and-collections.md)

La leçon [Collection de listes](arrays-and-collections.md) vous présente le type Collection de listes qui stocke les séquences de données. Vous apprendrez à ajouter et à supprimer des éléments, à rechercher des éléments et à trier des listes. Vous découvrirez différents types de listes. 

Ce tutoriel part du principe que vous avez fini les leçons listées ci-dessus.

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[Présentation des classes](introduction-to-classes.md)

Ce dernier tutoriel de présentation de C#, qui s’exécute sur votre ordinateur, fait appel à votre propre environnement de développement local et à .NET Core.
Vous allez créer une application console et voir les fonctionnalités orientées objet de base qui font partie du langage C#.
