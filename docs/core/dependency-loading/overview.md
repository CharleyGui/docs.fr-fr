---
title: Chargement des dépendances-.NET Core
description: Vue d’ensemble du chargement des dépendances managées et non managées dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: 34deb802183f20cc92449c21eb7e149cc002850f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284220"
---
# <a name="dependency-loading-in-net-core"></a>Chargement des dépendances dans .NET Core

Chaque application .NET Core a des dépendances. Même l' `hello world` application simple a des dépendances sur des parties des bibliothèques de classes .net core.

La compréhension de la logique de chargement d’assembly .NET Core par défaut peut aider à comprendre et à déboguer les problèmes de déploiement classiques.

Dans certaines applications, les dépendances sont déterminées dynamiquement au moment de l’exécution. Dans ces situations, il est essentiel de comprendre comment les assemblys managés et les dépendances non managées sont chargés.

## <a name="understanding-assemblyloadcontext"></a>Présentation d’AssemblyLoadContext

L' <xref:System.Runtime.Loader.AssemblyLoadContext> API est essentielle à la conception du chargement .net core. L’article [Présentation de AssemblyLoadContext](understanding-assemblyloadcontext.md) fournit une vue d’ensemble conceptuelle de la conception.

## <a name="loading-details"></a>Chargement des détails

Les détails de l’algorithme de chargement sont présentés brièvement dans plusieurs articles :

- [Algorithme de chargement d’assembly managé](loading-managed.md)
- [Algorithme de chargement d’assembly satellite](loading-resources.md)
- [Algorithme de chargement de bibliothèque non managée (natif)](loading-unmanaged.md)
- [Détection par défaut](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Créer une application .NET Core avec des plug-ins

Le didacticiel [créer une application .net core avec des plug-ins](../tutorials/creating-app-with-plugin-support.md) décrit comment créer un AssemblyLoadContext personnalisé. Il utilise un <xref:System.Runtime.Loader.AssemblyDependencyResolver> pour résoudre les dépendances du plug-in. Le didacticiel isole correctement les dépendances du plug-in à partir de l’application d’hébergement.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Comment utiliser et déboguer la non-chargeabilité d’assembly dans .NET Core

L’article [comment utiliser et déboguer l’assembly dans .net Core](../../standard/assembly/unloadability.md) est un didacticiel pas à pas. Il montre comment charger une application .NET Core, l’exécuter, puis la décharger. L’article fournit également des conseils de débogage.
