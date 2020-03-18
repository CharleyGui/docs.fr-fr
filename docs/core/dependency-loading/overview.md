---
title: Chargement de dépendance - .NET Core
description: Aperçu du chargement de dépendance géré et non géré dans .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416663"
---
# <a name="dependency-loading-in-net-core"></a>Chargement de dépendance dans .NET Core

Chaque application .NET Core a des dépendances. Même l’application simple `hello world` a des dépendances sur des parties des bibliothèques de classe .NET Core.

Comprendre la logique de chargement par défaut .NET Core peut aider à comprendre et à déboguer les problèmes de déploiement typiques.

Dans certaines applications, les dépendances sont déterminées dynamiquement au moment de l’exécution. Dans ces situations, il est essentiel de comprendre comment les assemblages gérés et les dépendances non gérées sont chargés.

## <a name="understanding-assemblyloadcontext"></a>Présentation d’AssemblyLoadContext

L’API <xref:System.Runtime.Loader.AssemblyLoadContext> est au cœur de la conception de chargement .NET Core. [L’article Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) fournit un aperçu conceptuel de la conception.

## <a name="loading-details"></a>Chargement des détails

Les détails de l’algorithme de chargement sont brièvement couverts dans plusieurs articles :

- [Algorithme de chargement d’assemblage géré](loading-managed.md)
- [Algorithme de chargement d’assemblage par satellite](loading-resources.md)
- [Algorithme de chargement de bibliothèque non gestion (indigène)](loading-unmanaged.md)
- [Sondage par défaut](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a>Créer une application .NET Core avec des plug-ins

Le tutoriel [Créer une application .NET Core avec des plugins](../tutorials/creating-app-with-plugin-support.md) décrit comment créer un assemblyLoadContext personnalisé. Il utilise <xref:System.Runtime.Loader.AssemblyDependencyResolver> un pour résoudre les dépendances du plugin. Le tutoriel isole correctement les dépendances du plugin de l’application d’hébergement.

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a>Comment utiliser et déboguer la non-chargeabilité d’assembly dans .NET Core

Le [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article est un tutoriel étape par étape. Il montre comment charger une application .NET Core, exécuter, puis le décharger. L’article fournit également des conseils de débogage.
