---
title: Présentation de C# -vous familiariser avec les outils de développement
description: Cet article constitue une introduction aux outils que vous utiliserez pour développer des applications C# et .NET sur votre ordinateur.
ms.date: 10/23/2018
ms.openlocfilehash: 0b1df9e733eef92b1eeb0a7f3ba3ba49602f219d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156569"
---
# <a name="become-familiar-with-the-net-development-tools"></a>Vous familiariser avec les outils de développement .NET

La première étape pour exécuter un tutoriel sur votre ordinateur consiste à configurer un environnement de développement.
Le tutoriel .NET [Hello World en 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) a des instructions pour configurer votre environnement de développement local sur Windows, Linux ou macOS.

Vous pouvez aussi installer le [Kit SDK .NET Core](https://dotnet.microsoft.com/download) et [Visual Studio Code](https://code.visualstudio.com/).

## <a name="basic-application-development-flow"></a>Flux de développement d’une application de base

Vous créerez des [`dotnet new`](../../../core/tools/dotnet-new.md) applications à l’aide de la commande. Cette commande génère les fichiers et ressources nécessaires pour votre application. Les tutoriels de présentation de C# utilisent tous le type d’application `console`. Une fois que vous avez les bases, vous pouvez développer d’autres types d’applications.

Les autres commandes que vous [`dotnet build`](../../../core/tools/dotnet-build.md) utiliserez sont pour [`dotnet run`](../../../core/tools/dotnet-run.md) construire l’exécutable, et pour exécuter l’exécutable.

## <a name="pick-your-tutorial"></a>Choisir un tutoriel

Vous pouvez commencer par l’un des tutoriels suivants :

## <a name="numbers-in-c"></a>[Nombres en C#](numbers-in-csharp-local.md)

Dans le tutoriel [Nombres en C#](numbers-in-csharp-local.md), vous allez apprendre comment les ordinateurs stockent les nombres et comment effectuer des calculs avec différents types numériques. Vous apprendrez les bases de l’arrondi et comment effectuer des calculs mathématiques à l’aide de C#.

Ce tutoriel part du principe que vous avez terminé la leçon [Hello world](hello-world.yml).

## <a name="branches-and-loops"></a>[Branches et boucles](branches-and-loops-local.md)

Le tutoriel [Branches et boucles](branches-and-loops-local.md) explique les bases de la sélection de différents chemins d’exécution de code en fonction des valeurs stockées dans des variables. Vous allez apprendre les principes fondamentaux du flux de contrôle, sur la base duquel les programmes prennent des décisions et choisissent différentes actions.

Ce tutoriel part du principe que vous avez fini les leçons [Hello world](hello-world.yml) et [Nombres en C#](numbers-in-csharp-local.md).

## <a name="list-collection"></a>[Collection de listes](arrays-and-collections.md)

La leçon [Collection de listes](arrays-and-collections.md) vous présente le type Collection de listes qui stocke les séquences de données. Vous apprendrez à ajouter et à supprimer des éléments, à rechercher des éléments et à trier des listes. Vous découvrirez différents types de listes.

Ce tutoriel part du principe que vous avez fini les leçons listées ci-dessus.

## <a name="introduction-to-classes"></a>[Présentation des classes](introduction-to-classes.md)

Ce dernier tutoriel de présentation de C#, qui s’exécute sur votre ordinateur, fait appel à votre propre environnement de développement local et à .NET Core.
Vous allez créer une application console et voir les fonctionnalités orientées objet de base qui font partie du langage C#.
