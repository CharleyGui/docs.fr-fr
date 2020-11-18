---
title: 'Comment : implémenter un modèle de flux de données producteur-consommateur'
description: Découvrez comment implémenter un modèle de flux de données producteur-consommateur à l’aide de la bibliothèque de flux de données TPL dans .NET.
ms.date: 09/24/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TPL dataflow library, implementing producer-consumer pattern
- Task Parallel Library, dataflows
- producer-consumer patterns, implementing [TPL]
ms.assetid: 47a1d38c-fe9c-44aa-bd15-937bd5659b0b
ms.openlocfilehash: 3bc97cce2a063e7d5286ad886401cb6ae2ce3026
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826929"
---
# <a name="how-to-implement-a-producer-consumer-dataflow-pattern"></a>Comment : implémenter un modèle de flux de données producteur-consommateur

Dans cet article, vous allez apprendre à utiliser la bibliothèque de flux de données TPL pour implémenter un modèle producteur-consommateur. Dans ce modèle, le *producteur* envoie des messages à un bloc de message et le *consommateur* lit les messages de ce bloc.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Exemple

L’exemple suivant montre un modèle producteur-consommateur de base qui utilise des flux de données. La méthode `Produce` écrit des tableaux contenant les octets aléatoires de données dans un objet <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601?displayProperty=nameWithType>, et la méthode `Consume` lit les octets à partir d’un objet <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601?displayProperty=nameWithType>. En utilisant les interfaces <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> et <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>, et non leurs types dérivés, vous pouvez écrire du code réutilisable sur une variété de types de blocs de flux de données. Cet exemple utilise la classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601>. Dans la mesure où la classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> agit à la fois en tant que source et cible, le producteur et le consommateur peuvent utiliser un objet partagé pour transférer les données.

 La méthode `Produce` appelle la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> dans une boucle pour écrire de façon synchrone des données vers le bloc cible. Dès que la méthode `Produce` a écrit toutes les données dans le bloc cible, celle-ci appelle la méthode <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A> pour indiquer que le bloc n’aura jamais aucune donnée supplémentaire disponible. La méthode `Consume` utilise les opérateurs [async](../../csharp/language-reference/keywords/async.md) et [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) et [Await](../../visual-basic/language-reference/operators/await-operator.md) en Visual Basic) pour calculer de façon asynchrone le nombre total d’octets provenant de l’objet <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>. Pour agir de façon asynchrone, la méthode `Consume` appelle la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A> pour recevoir une notification lorsque le bloc source possède des données disponibles et lorsque le bloc source n’aura jamais aucune donnée supplémentaire disponible.

 [!code-csharp[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#1)]
 [!code-vb[TPLDataflow_ProducerConsumer#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#1)]

## <a name="robust-programming"></a>Programmation fiable

 L’exemple précédent utilise un seul consommateur pour traiter les données sources. Si votre application dispose de plusieurs consommateurs, utilisez la méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> pour lire des données à partir du bloc source, comme indiqué dans l’exemple suivant.

 [!code-csharp[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_producerconsumer/cs/dataflowproducerconsumer.cs#2)]
 [!code-vb[TPLDataflow_ProducerConsumer#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_producerconsumer/vb/dataflowproducerconsumer.vb#2)]

 La méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> retourne `False` si donnée n’est disponible. Lorsque plusieurs consommateurs doivent accéder simultanément au bloc source, ce mécanisme garantit que les données sont toujours disponibles après l’appel à <xref:System.Threading.Tasks.Dataflow.DataflowBlock.OutputAvailableAsync%2A>.

## <a name="see-also"></a>Voir aussi

- [Dataflow](dataflow-task-parallel-library.md)
