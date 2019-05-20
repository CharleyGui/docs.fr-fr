---
title: 'Procédure : Écrire et lire des messages dans un bloc de flux de données'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, reading and writing messages
ms.assetid: 1a9bf078-aa82-46eb-b95a-f87237f028c5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 564f5f880f32dbab1387d03f30082e1972c3f353
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591971"
---
# <a name="how-to-write-messages-to-and-read-messages-from-a-dataflow-block"></a>Procédure : Écrire et lire des messages dans un bloc de flux de données
Ce document explique comment utiliser la bibliothèque de flux de données TPL pour écrire et lire des messages sur un bloc de flux de données. La bibliothèque de flux de données TPL fournit à la fois des méthodes synchrones et asynchrones pour lire et écrire des messages sur un bloc de flux de données. Ce document utilise la classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601?displayProperty=nameWithType>. La classe <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> met en mémoire tampon des messages et fonctionne à la fois comme source et comme cible de message.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="writing-to-and-reading-from-a-dataflow-block-synchronously"></a>Écriture et lecture d’un bloc de flux de données de façon synchrone  
 L'exemple suivant utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> pour écrire sur un bloc de flux de données <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> et la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A> pour lire à partir du même objet.  
  
 [!code-csharp[TPLDataflow_ReadWrite#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#2)]
 [!code-vb[TPLDataflow_ReadWrite#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#2)]  
  
 Vous pouvez également utiliser la méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> pour lire à partir d'un bloc de flux de données, comme illustré dans l'exemple suivant. La méthode <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> ne bloque pas le thread actuel et est utile lorsque vous interrogez occasionnellement les données.  
  
 [!code-csharp[TPLDataflow_ReadWrite#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#3)]
 [!code-vb[TPLDataflow_ReadWrite#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#3)]  
  
 Comme la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A> agit de manière synchrone, l’objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dans les exemples précédents reçoit toutes les données avant que la deuxième boucle lise les données. L'exemple suivant étend le premier exemple en utilisant <xref:System.Threading.Tasks.Parallel.Invoke%2A> pour lire et écrire simultanément sur le bloc de messages. Comme <xref:System.Threading.Tasks.Parallel.Invoke%2A> effectue des actions simultanément, les valeurs ne sont pas écrites dans l'objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> dans un ordre spécifique.  
  
 [!code-csharp[TPLDataflow_ReadWrite#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#4)]
 [!code-vb[TPLDataflow_ReadWrite#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#4)]  
  
## <a name="writing-to-and-reading-from-a-dataflow-block-asynchronously"></a>Écriture et lecture d'un bloc de flux de données de façon asynchrone  
 L'exemple suivant utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> pour l'écriture asynchrone sur un objet <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> et la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> pour lire de façon asynchrone à partir du même objet. Cet exemple utilise des opérateurs [async](~/docs/csharp/language-reference/keywords/async.md) et [await](~/docs/csharp/language-reference/keywords/await.md) ([Async](~/docs/visual-basic/language-reference/modifiers/async.md) et [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) en Visual Basic) pour envoyer façon asynchrone des données et pour lire des données dans le bloc cible. La méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A> est utile lorsque vous devez autoriser un bloc de flux de données à reporter des messages. La méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A> est utile lorsque vous souhaitez traiter des données lorsque ces données deviennent disponibles. Pour plus d’informations sur la façon dont les messages se propagent à travers les blocs de messages, consultez la section Transmission des Messages dans un [flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md).  
  
 [!code-csharp[TPLDataflow_ReadWrite#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#5)]
 [!code-vb[TPLDataflow_ReadWrite#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#5)]  
  
## <a name="a-complete-example"></a>Un exemple complet  
 L'exemple suivant présente le code complet pour ce document.  
  
 [!code-csharp[TPLDataflow_ReadWrite#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_readwrite/cs/dataflowreadwrite.cs#1)]
 [!code-vb[TPLDataflow_ReadWrite#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_readwrite/vb/dataflowreadwrite.vb#1)]  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cet exemple montre comment lire et écrire directement sur un bloc de messages. Vous pouvez aussi connecter des blocs de flux de données pour former des *pipelines*, qui sont des séquences linéaires de blocs de flux de données, ou des *réseaux*, qui sont des graphiques des blocs de flux de données. Dans un pipeline ou un réseau, les sources propagent des données de manière asynchrone vers les cibles à mesure que les données deviennent disponibles. Pour obtenir un exemple qui crée un pipeline de flux de données de base, consultez [Procédure pas à pas : Création d’un pipeline de flux de données](../../../docs/standard/parallel-programming/walkthrough-creating-a-dataflow-pipeline.md). Pour obtenir un exemple qui crée un réseau plus complexe de flux de données, consultez [Procédure pas à pas : Utilisation d’un flux de données dans une application Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Voir aussi

- [Le flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
