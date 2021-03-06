---
title: 'Procédure : utiliser Parallel_Invoke pour exécuter des opérations parallèles'
description: Consultez Comment utiliser la méthode Parallel. Invoke dans la bibliothèque parallèle de tâches (TPL), qui effectue des opérations parallèles sur une source de données partagée dans .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 6ec8f03216cc6225e909f5dc3128469047826166
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825479"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Procédure : utiliser Parallel_Invoke pour exécuter des opérations parallèles

Cet exemple indique comment paralléliser des opérations à l'aide de <xref:System.Threading.Tasks.Parallel.Invoke%2A> dans la bibliothèque parallèle de tâches. Trois opérations sont effectuées sur la source de données partagée. Les opérations peuvent être exécutées en parallèle de manière simple, car aucune d’elles ne modifie la source.

> [!NOTE]
> Cette documentation utilise les expressions lambda pour définir les délégués de la bibliothèque parallèle de tâches. Si vous n’êtes pas familiarisé avec les expressions lambda en C# ou Visual Basic, consultez [expressions lambda en PLINQ et tpl](lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Exemple

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Avec <xref:System.Threading.Tasks.Parallel.Invoke%2A> , vous exprimez simplement les actions que vous souhaitez exécuter simultanément, et le Runtime gère tous les détails de planification de thread, y compris la mise à l’échelle automatique jusqu’au nombre de cœurs sur l’ordinateur hôte.

Cet exemple parallélise les opérations et non les données. Vous pouvez également paralléliser les requêtes LINQ à l'aide de PLINQ et exécuter les requêtes séquentiellement. Vous pouvez aussi paralléliser les données à l'aide de PLINQ. Une autre option consiste à paralléliser à la fois les requêtes et les tâches. Bien que la surcharge résultante puisse dégrader les performances sur les ordinateurs hôtes avec relativement peu de processeurs, elle s’adapte mieux aux ordinateurs avec de nombreux processeurs.

## <a name="compile-the-code"></a>Compiler le code

Copiez et collez l'exemple entier dans un projet Microsoft Visual Studio et appuyez sur **F5**.

## <a name="see-also"></a>Voir aussi

- [Programmation parallèle](index.md)
- [Procédure : annuler une tâche et ses enfants](how-to-cancel-a-task-and-its-children.md)
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
