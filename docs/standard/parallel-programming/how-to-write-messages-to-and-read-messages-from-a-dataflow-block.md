---
title: 'Comment : écrire et lire des messages à partir d’un bloc de flux de données'
ms.date: 09/10/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
ms.openlocfilehash: 8eb92d917bb2b03c2a505a2ba238598e0c1a450c
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022855"
---
# <a name="how-to-write-and-read-messages-from-a-dataflow-block"></a>Comment : écrire et lire des messages à partir d’un bloc de flux de données

Cet article explique comment utiliser la bibliothèque de flux de données TPL (Task Parallel Library) pour écrire et lire des messages dans un bloc de flux de données. La bibliothèque de flux de données TPL fournit à la fois des méthodes synchrones et asynchrones pour lire et écrire des messages sur un bloc de flux de données. Cet article explique comment utiliser la <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType> classe. La <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> classe met en mémoire tampon les messages et se comporte comme une source de message et une cible de message.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-and-reading-synchronously"></a>Écriture et lecture synchrones

L'exemple suivant utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> pour écrire sur un bloc de flux de données <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> et la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> pour lire à partir du même objet.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="2":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="2":::

Vous pouvez également utiliser la méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> pour lire à partir d'un bloc de flux de données, comme illustré dans l'exemple suivant. La méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ne bloque pas le thread actuel et est utile lorsque vous interrogez occasionnellement les données.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="3":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="3":::

Comme la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> agit de manière synchrone, l’objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dans les exemples précédents reçoit toutes les données avant que la deuxième boucle lise les données. L'exemple suivant étend le premier exemple en utilisant <xref:System.Threading.Tasks.Task.WhenAll(System.Threading.Tasks.Task[])?displayProperty=nameWithType> pour lire et écrire simultanément sur le bloc de messages. Comme <xref:System.Threading.Tasks.Task.WhenAll%2A> effectue des actions simultanément, les valeurs ne sont pas écrites dans l'objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dans un ordre spécifique.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="4":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="4":::

## <a name="writing-and-reading-asynchronously"></a>Écriture et lecture asynchrones

L'exemple suivant utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> pour l'écriture asynchrone sur un objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> et la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> pour lire de façon asynchrone à partir du même objet. Cet exemple utilise des opérateurs [async](../../csharp/language-reference/keywords/async.md) et [await](../../csharp/language-reference/operators/await.md) ([Async](../../visual-basic/language-reference/modifiers/async.md) et [Await](../../visual-basic/language-reference/operators/await-operator.md) en Visual Basic) pour envoyer façon asynchrone des données et pour lire des données dans le bloc cible. La méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> est utile lorsque vous devez autoriser un bloc de flux de données à reporter des messages. La méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> est utile lorsque vous souhaitez traiter des données lorsque ces données deviennent disponibles. Pour plus d’informations sur la façon dont les messages se propagent à travers les blocs de messages, consultez la section Transmission des Messages dans un [flux de données](dataflow-task-parallel-library.md).

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="5":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="5":::

## <a name="a-complete-example"></a>Un exemple complet

L’exemple suivant illustre l’ensemble du code de cet article.

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs" id="1":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb" id="1":::

## <a name="next-steps"></a>Étapes suivantes

Cet exemple montre comment lire et écrire directement sur un bloc de messages. Vous pouvez aussi connecter des blocs de flux de données pour former des *pipelines*, qui sont des séquences linéaires de blocs de flux de données, ou des *réseaux*, qui sont des graphiques des blocs de flux de données. Dans un pipeline ou un réseau, les sources propagent des données de manière asynchrone vers les cibles à mesure que les données deviennent disponibles. Pour obtenir un exemple de création d’un pipeline de flux de données, consultez [Procédure pas à pas : création d’un pipeline de flux de données](walkthrough-creating-a-dataflow-pipeline.md). Pour obtenir un exemple de création d’un réseau de flux de données plus complexe, consultez [Procédure pas à pas : utilisation de flux de données dans une application Windows Forms](walkthrough-using-dataflow-in-a-windows-forms-application.md).

## <a name="see-also"></a>Voir aussi

- [Flux de données (bibliothèque parallèle de tâches)](dataflow-task-parallel-library.md)
