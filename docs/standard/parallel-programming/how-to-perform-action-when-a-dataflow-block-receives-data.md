---
title: 'Procédure : Exécuter des actions quand un bloc de flux de données reçoit des données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, receiving data
ms.assetid: fc2585dc-965e-4632-ace7-73dd02684ed3
ms.openlocfilehash: c0fe9d1aa0e907ab28cf53cc97488a15e6434cda
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674838"
---
# <a name="how-to-perform-action-when-a-dataflow-block-receives-data"></a>Procédure : Exécuter des actions quand un bloc de flux de données reçoit des données

Les types de *Bloc de flux de données d’exécution* appellent un délégué fourni par l’utilisateur lorsqu’ils reçoivent des données. Les classes <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> sont des types de bloc de flux de données d'exécution. Vous pouvez utiliser le mot clé `delegate` (`Sub` en Visual Basic), <xref:System.Action%601>, <xref:System.Func%602> ou une expression lambda quand vous fournissez une fonction de travail dans un bloc de flux de données d’exécution. Ce document explique comment utiliser <xref:System.Func%602> et les expressions lambda pour effectuer l’action dans des blocs d’exécution.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Exemple  

 L'exemple suivant utilise le flux de données pour lire un fichier de disque et calcule le nombre d'octets qui sont égaux à zéro dans ce fichier. Il utilise <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pour lire le fichier et calculer le nombre d'octets nuls, et <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> pour imprimer le nombre d'octets nuls sur la console. L'objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> spécifie un objet <xref:System.Func%602> pour effectuer le travail lorsque les blocs reçoivent les données. L'objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> utilise une expression lambda pour afficher sur la console le nombre d'octets nuls qui sont lus.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#1)]
 [!code-vb[TPLDataflow_ExecutionBlocks#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#1)]  
  
 Bien que vous puissiez spécifier une expression lambda à un objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602>, cet exemple utilise <xref:System.Func%602> pour permettre à l'autre code d'utiliser la méthode `CountBytes`. L’objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> utilise une expression lambda car le travail à effectuer est spécifique à cette tâche et n’est pas susceptible d’être utile depuis un autre code. Pour plus d’informations sur la façon dont les expressions lambda fonctionnent dans la bibliothèque de tâches en parallèle, consultez [Expressions lambda en PLINQ et dans la bibliothèque parallèle de tâches](lambda-expressions-in-plinq-and-tpl.md).  
  
 La section Résumé des types délégués dans le document de [flux](dataflow-task-parallel-library.md) de données résume les types délégués que vous pouvez fournir aux <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> objets, et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> . La table indique également si le type délégué fonctionne de façon synchrone ou asynchrone.  
  
## <a name="robust-programming"></a>Programmation fiable  

 Cet exemple fournit un délégué de type <xref:System.Func%602> à l'objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> pour effectuer la tâche du bloc de flux de données de façon synchrone. Pour permettre au bloc de flux de données de se comporter de façon asynchrone, fournissez un délégué de type <xref:System.Func%601> au bloc de flux de données. Lorsqu’un bloc de flux de données se comporte de façon asynchrone, la tâche du bloc de flux de données se termine uniquement lorsque l’objet <xref:System.Threading.Tasks.Task%601> retourné s’achève. L’exemple suivant modifie la méthode `CountBytes` et utilise les opérateurs [async](../../csharp/language-reference/keywords/async.md) et [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) et [Await](../../visual-basic/language-reference/operators/await-operator.md) en Visual Basic) pour calculer de façon asynchrone le nombre total d’octets qui sont égaux à zéro dans le fichier fourni. La méthode <xref:System.IO.FileStream.ReadAsync%2A> effectue de façon asynchrone des opérations de lecture de fichiers.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#2)]
 [!code-vb[TPLDataflow_ExecutionBlocks#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#2)]  
  
 Utilisez également des expressions lambda asynchrones pour effectuer une action dans un bloc de flux de données d’exécution. L’exemple suivant modifie l’objet <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> utilisé dans l’exemple précédent pour qu’il utilise une expression lambda pour effectuer de manière asynchrone le travail.  
  
 [!code-csharp[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_executionblocks/cs/dataflowexecutionblocks.cs#3)]
 [!code-vb[TPLDataflow_ExecutionBlocks#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_executionblocks/vb/dataflowexecutionblocks.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Dataflow](dataflow-task-parallel-library.md)
