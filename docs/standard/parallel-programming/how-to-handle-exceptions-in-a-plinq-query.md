---
title: 'Procédure : gérer des exceptions dans une requête PLINQ'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
ms.openlocfilehash: aa583d8c31381d23e22f271db3d42d35e1fa14b2
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826942"
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Procédure : gérer des exceptions dans une requête PLINQ

Le premier exemple de cette rubrique montre comment gérer l’exception <xref:System.AggregateException?displayProperty=nameWithType> qui peut être levée à partir d’une requête PLINQ au cours de son exécution. Le deuxième exemple montre comment placer des blocs try-catch dans des délégués, le plus près possible de l’emplacement où l’exception sera levée. Vous pouvez ainsi les intercepter dès qu’ils se produisent et éventuellement poursuivre l’exécution de la requête. Lorsque les exceptions sont autorisées à se propager vers le thread lié, il est possible qu'une requête puisse continuer à traiter des éléments après que l'exception ait été levée.

Dans certains cas, quand PLINQ revient à l’exécution séquentielle et qu’une exception se produit, cette dernière peut être propagée directement, et non encapsulée dans une exception <xref:System.AggregateException>. En outre, les exceptions <xref:System.Threading.ThreadAbortException> sont toujours propagées directement.

> [!NOTE]
> Quand l'option «Uniquement mon code» est activée, Visual Studio peut s'arrêter sur la ligne qui lève l'exception et afficher un message d'erreur « exception non gérée par le code utilisateur ». Cette erreur est sans gravité. Vous pouvez appuyer sur F5 pour continuer et voir le comportement de gestion des exceptions qui est illustré dans les exemples ci-dessous. Pour empêcher Visual Studio de s'arrêter sur la première erreur, il suffit de désactiver la case à cocher Uniquement mon code sous **Outils, Options, Débogage, Général**.
>
> Cet exemple, destiné à illustrer l'utilisation, peut ne pas s'exécuter plus rapidement que la requête LINQ to Objects séquentielle équivalente. Pour plus d’informations sur l’accélération, consultez [Fonctionnement de l’accélération dans PLINQ](understanding-speedup-in-plinq.md).

## <a name="example"></a>Exemple

Cet exemple montre comment placer les blocs try-catch autour du code qui exécute la requête pour intercepter toute exception <xref:System.AggregateException?displayProperty=nameWithType> levée.

[!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
[!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]

Dans cet exemple, la requête ne peut pas continuer une fois l’exception levée. Au moment où votre code d’application intercepte l’exception, PLINQ a déjà arrêté la requête sur tous les threads.

## <a name="example"></a>Exemple

L’exemple suivant montre comment placer un bloc try-catch dans un délégué pour pouvoir intercepter une exception et poursuivre l’exécution des requêtes.

[!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
[!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]

## <a name="compiling-the-code"></a>Compilation du code

- Pour compiler et exécuter ces exemples, copiez-les dans l’exemple de données PLINQ et appelez la méthode à partir de Main.

## <a name="robust-programming"></a>Programmation fiable

N’interceptez pas d’exceptions, sauf si vous savez comment les gérer pour ne pas endommager l’état de votre programme.

## <a name="see-also"></a>Voir aussi

- <xref:System.Linq.ParallelEnumerable>
- [Parallel LINQ (PLINQ)](introduction-to-plinq.md)
