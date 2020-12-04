---
title: Règles de fiabilité (analyse du code)
description: En savoir plus sur les règles de fiabilité de l’analyse du code.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.reliabilityrules
helpviewer_keywords:
- rules, reliability
- reliability rules
- managed code analysis rules, reliability rules
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a747dd4dcda351a1ddb0f3d069bb7bac895c32f8
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2020
ms.locfileid: "96587798"
---
# <a name="reliability-rules"></a>Règles de fiabilité

Les règles de fiabilité prennent en charge la fiabilité des bibliothèques et des applications, telles que la mémoire et l’utilisation des threads. Les règles de fiabilité sont les suivantes :

|Règle|Description|
|----------|-----------------|
|[CA2000 : Supprimer les objets avant la mise hors de portée](ca2000.md)|Sachant qu'un événement exceptionnel peut se produire et empêcher l'exécution du finaliseur d'un objet, ce dernier doit plutôt être supprimé explicitement avant que toutes les références à lui soient hors de portée.|
|[CA2002 : Ne définissez pas un verrou sur des objets à identité faible](ca2002.md)|Un objet est dit d'identité faible lorsqu'il est accessible directement au-delà des limites d'un domaine d'application. Un thread qui essaie d'acquérir un verrou sur un objet qui affiche une identité faible peut être bloqué par un deuxième thread dans un domaine d'application différent qui dispose d'un verrou sur le même objet.|
|[CA2007 : N’attendez pas directement une Tâche](ca2007.md)|Une méthode asynchrone [attend](../../../csharp/language-reference/operators/await.md) directement un <xref:System.Threading.Tasks.Task> .|
|[CA2008 : Ne pas créer de tâches sans passer TaskScheduler](ca2008.md)|Une opération de création de tâche ou de continuation utilise une surcharge de méthode qui ne spécifie pas de <xref:System.Threading.Tasks.TaskScheduler> paramètre.|
|[CA2009 : N’appelez pas ToImmutableCollection sur une valeur ImmutableCollection](ca2009.md)|`ToImmutable` la méthode était inutilement appelée sur une collection immuable de l' <xref:System.Collections.Immutable> espace de noms.|
|[CA2011 : Ne pas assigner la propriété dans son setter](ca2011.md) | Une valeur a été assignée par erreur à une propriété dans son propre [accesseur Set](../../../csharp/programming-guide/classes-and-structs/using-properties.md#the-set-accessor). |
|[CA2012 : Utiliser correctement ValueTasks](ca2012.md) | Les ValueTasks retournés par les appels de membres sont censés être attendus directement.  Toute tentative d’utilisation d’un ValueTask à plusieurs reprises ou d’un accès direct à l’un des résultats avant qu’il ne soit connu peut entraîner une exception ou une altération.  En ignorant ce ValueTask, il est probable qu’il s’agit d’une indication d’un bogue fonctionnel et peut nuire aux performances. |
|[CA2013 : Ne pas utiliser ReferenceEquals avec des types valeur](ca2013.md) | Lors de la comparaison de valeurs à l’aide <xref:System.Object.ReferenceEquals%2A?displayProperty=fullName> de, si objA et objB sont des types valeur, ils sont boxed avant d’être passés à la <xref:System.Object.ReferenceEquals%2A> méthode. Cela signifie que même si objA et objB représentent la même instance d’un type valeur, la <xref:System.Object.ReferenceEquals%2A> méthode retourne néanmoins false. |
|[Ca2014 : n’utilisez pas stackalloc dans les boucles.](ca2014.md) | L’espace de pile alloué par stackalloc est libéré uniquement à la fin de l’appel de la méthode actuelle.  Son utilisation dans une boucle peut entraîner une croissance de pile illimitée et des conditions de dépassement de capacité de pile éventuelles. |
|[Ca2015 : ne définissez pas de finaliseur pour les types dérivés de MemoryManager &lt; T&gt;](ca2015.md) | L’ajout d’un finaliseur à un type dérivé de <xref:System.Buffers.MemoryManager%601> peut permettre la libération de la mémoire pendant qu’il est toujours utilisé par un <xref:System.Span%601> . |
|[CA2016 : Transférer le paramètre CancellationToken aux méthodes qui l’acceptent](ca2016.md) | Transférez le `CancellationToken` paramètre aux méthodes qui prennent une pour garantir que les notifications d’annulation d’opération sont correctement propagées, ou transmettez `CancellationToken.None` explicitement pour indiquer intentionnellement que le jeton n’est pas propagé. |
