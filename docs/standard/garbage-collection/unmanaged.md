---
title: Nettoyage de ressources non managées
description: Découvrez comment nettoyer les ressources non managées non gérées par le garbage collector .NET, telles que les fichiers, les fenêtres, les & les connexions réseau ou de base de données.
ms.date: 05/13/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
ms.openlocfilehash: 07a8d754f1fc2612ae53407fa1b12a1eab7e38f2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599829"
---
# <a name="cleaning-up-unmanaged-resources"></a>Nettoyage de ressources non managées

Pour la majorité des objets créés par votre application, vous pouvez vous appuyer sur le [garbage collector .net](index.md) pour gérer la gestion de la mémoire. Toutefois, lorsque vous créez des objets qui incluent des ressources non managées, vous devez libérer explicitement ces ressources une fois que vous avez fini de les utiliser. Les types les plus courants de ressources non managées sont des objets qui encapsulent les ressources du système d’exploitation, telles que les fichiers, les fenêtres, les connexions réseau ou les connexions de base de données. Bien que le récupérateur de mémoire puisse assurer le suivi de la durée de vie d'un objet qui encapsule une ressource non managée, il ne sait pas comment libérer et nettoyer la ressource non managée.

Si vos types utilisent les ressources non managées, procédez comme suit :

- Implémentez le [modèle de suppression](implementing-dispose.md). Pour cela, vous devez fournir une <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implémentation pour activer la version déterministe des ressources non managées. Un consommateur de votre type appelle <xref:System.IDisposable.Dispose%2A> lorsque l’objet (et les ressources qu’il utilise) n’est plus nécessaire. La méthode <xref:System.IDisposable.Dispose%2A> libère immédiatement les ressources non managées.

- Dans le cas où un consommateur de votre type oublie d’appeler <xref:System.IDisposable.Dispose%2A> , vous pouvez libérer vos ressources non managées. Il existe deux façons d'effectuer cette opération :

  - Utilisez un handle sécurisé pour encapsuler votre ressource non managée. Il s’agit de la technique recommandée. Les Handles sécurisés sont dérivés de la <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> classe abstraite et incluent une <xref:System.Object.Finalize%2A> méthode robuste. Lorsque vous utilisez un handle sécurisé, implémentez simplement l'interface <xref:System.IDisposable> et appelez la méthode <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> de votre handle sécurisé dans l'implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>. Le finaliseur du handle sécurisé est appelé automatiquement par le récupérateur de mémoire si sa méthode <xref:System.IDisposable.Dispose%2A> n'est pas appelé.

    —**ou**—

  - Remplacez la méthode <xref:System.Object.Finalize%2A?displayProperty=nameWithType> . La finalisation active la mise en production non déterministe des ressources non managées lorsque le consommateur d’un type n’appelle pas la méthode <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> pour les supprimer de manière déterministe. Définissez un [finaliseur](../../csharp/programming-guide/classes-and-structs/destructors.md) en substituant la <xref:System.Object.Finalize%2A?displayProperty=nameWithType> méthode.

  > [!WARNING]
  > Toutefois, étant donné que la finalisation de l’objet peut être une opération complexe et sujette aux erreurs, nous vous recommandons d’utiliser un handle sécurisé au lieu de fournir votre propre finaliseur.

Les consommateurs de votre type peuvent ensuite appeler directement votre implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> pour libérer la mémoire utilisée par les ressources non managées. Lorsque vous implémentez correctement une méthode <xref:System.IDisposable.Dispose%2A>, la méthode <xref:System.Object.Finalize%2A> de votre handle sécurisé ou votre propre substitution de la méthode <xref:System.Object.Finalize%2A?displayProperty=nameWithType> devient un dispositif de protection pour nettoyer les ressources si la méthode <xref:System.IDisposable.Dispose%2A> n'est pas appelée.

## <a name="in-this-section"></a>Dans cette section

[Implémentation d’une méthode dispose](implementing-dispose.md) décrit comment implémenter le modèle de suppression pour libérer des ressources non managées.

[Utilisation d’objets qui `IDisposable` implémentent](using-objects.md) décrit comment les consommateurs d’un type vérifient que son <xref:System.IDisposable.Dispose%2A> implémentation est appelée. `using`Pour ce faire, nous vous recommandons d’utiliser l’instruction C# (ou l’Visual Basic `Using` ).

## <a name="reference"></a>Informations de référence

| Type/membre | Description |
|--|--|
| <xref:System.IDisposable?displayProperty=nameWithType> | Définit la méthode <xref:System.IDisposable.Dispose%2A> pour libérer des ressources non managées. |
| <xref:System.Object.Finalize%2A?displayProperty=nameWithType> | Prévoit la finalisation de l’objet si les ressources non managées ne sont pas libérées par la méthode <xref:System.IDisposable.Dispose%2A>. |
| <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> | Supprime la finalisation. Cette méthode est généralement appelée à partir d'une méthode `Dispose` pour empêcher un finaliseur de s'exécuter. |
