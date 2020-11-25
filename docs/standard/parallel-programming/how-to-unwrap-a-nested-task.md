---
title: 'Procédure : désencapsuler une tâche imbriquée'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
ms.openlocfilehash: 3eec3b7e8cc76ee171d88a7886b4983000848084
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722620"
---
# <a name="how-to-unwrap-a-nested-task"></a>Procédure : désencapsuler une tâche imbriquée

Vous pouvez retourner une tâche à partir d’une méthode, puis attendre ou poursuivre à partir de cette tâche, comme indiqué dans l’exemple suivant :  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 Dans l’exemple précédent, la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> est de type `string` (`String` en Visual Basic).  
  
 Toutefois, dans certains cas, il se peut que vous souhaitiez créer une tâche dans une autre tâche, puis retourner la tâche imbriquée. Dans ce cas, le `TResult` de la tâche englobante est lui-même une tâche. Dans l’exemple suivant, la propriété Result est une `Task<Task<string>>` en C# ou `Task(Of Task(Of String))` en Visual Basic.  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 Bien qu’il soit possible d’écrire du code pour désencapsuler la tâche externe et extraire la tâche d’origine et sa propriété <xref:System.Threading.Tasks.Task%601.Result%2A>, ce code n’est pas facile à écrire, car vous devez gérer des exceptions et des demandes d’annulation. Dans ce cas, nous vous recommandons d’utiliser l’une des méthodes d’extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>, comme indiqué dans l’exemple suivant.  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 Les méthodes <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> peuvent être utilisées pour transformer toute `Task<Task>` ou `Task<Task<TResult>>` (`Task(Of Task)` ou `Task(Of Task(Of TResult))` en Visual Basic) en `Task` ou `Task<TResult>` (`Task(Of TResult)` en Visual Basic). La nouvelle tâche représente entièrement la tâche imbriquée interne et inclut l’état d’annulation ainsi que toutes les exceptions.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant décrit comment utiliser la méthode d’extension <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A>.  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [Programmation asynchrone basée sur les tâches](task-based-asynchronous-programming.md)
