---
title: 'Comment : utiliser Parallel.Invoke pour exécuter des opérations parallèles'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: f61bbf10bbeef736f66710f50e621c3619355a1d
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635802"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Comment : utiliser Parallel.Invoke pour exécuter des opérations parallèles

Cet exemple indique comment paralléliser des opérations à l'aide de <xref:System.Threading.Tasks.Parallel.Invoke%2A> dans la bibliothèque parallèle de tâches. Trois opérations sont effectuées sur la source de données partagée. Les opérations peuvent être exécutées en parallèle d’une manière simple, car aucune d’entre elles ne modifie la source.

> [!NOTE]
> Cette documentation utilise les expressions lambda pour définir les délégués de la bibliothèque parallèle de tâches. Si vous n’êtes pas familier avec les expressions lambda dans C ou Visual Basic, voir [Lambda Expressions dans PLINQ et TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Exemple

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Avec <xref:System.Threading.Tasks.Parallel.Invoke%2A>, vous exprimez simplement les actions que vous souhaitez exécuter simultanément, et le temps d’exécution gère tous les détails de planification de thread, y compris la mise à l’échelle automatiquement au nombre de cœurs sur l’ordinateur hôte.

Cet exemple parallélise les opérations et non les données. Vous pouvez également paralléliser les requêtes LINQ à l'aide de PLINQ et exécuter les requêtes séquentiellement. Vous pouvez aussi paralléliser les données à l'aide de PLINQ. Une autre option consiste à paralléliser à la fois les requêtes et les tâches. Bien que les frais généraux qui en résultent pourraient dégrader les performances sur les ordinateurs hôtes avec relativement peu de processeurs, il s’évolue mieux sur les ordinateurs avec de nombreux processeurs.

## <a name="compile-the-code"></a>Compiler le code

Copiez et collez l'exemple entier dans un projet Microsoft Visual Studio et appuyez sur **F5**.

## <a name="see-also"></a>Voir aussi

- [Programmation parallèle](../../../docs/standard/parallel-programming/index.md)
- [Comment : annuler une tâche et ses enfants](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
