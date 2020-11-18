---
title: 'Procédure pas à pas : Créer un type de bloc de flux de données personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, creating custom dataflow blocks
- dataflow blocks, creating custom in TPL
ms.assetid: a6147146-0a6a-4d9b-ab0f-237b3c1ac691
ms.openlocfilehash: 71f9002cc13f30bfe7988540472b09979d4e9d0a
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829958"
---
# <a name="walkthrough-creating-a-custom-dataflow-block-type"></a>Procédure pas à pas : Créer un type de bloc de flux de données personnalisé
Bien que la bibliothèque de flux de données TPL fournisse plusieurs types de blocs de flux de données offrant une large gamme de fonctionnalités, vous pouvez aussi créer des types de blocs personnalisés. Ce document décrit comment créer un type de bloc de flux de données qui implémente un comportement personnalisé.  
  
## <a name="prerequisites"></a>Prérequis  
 Consultez [Flux de données](dataflow-task-parallel-library.md) avant de lire ce document.  

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]
  
## <a name="defining-the-sliding-window-dataflow-block"></a>Définition du bloc de flux de données d’une fenêtre coulissante  
 Imaginez une application de flux de données qui exige que les valeurs d’entrée soient mises en mémoire tampon, puis affichées sous la forme d’une fenêtre coulissante. Par exemple, pour les valeurs d’entrée {0, 1, 2, 3, 4, 5} et une taille de fenêtre de 3, un bloc de flux de données de fenêtre coulissante génère les tableaux de sortie {0, 1, 2}, {1, 2, 3}, {2, 3, 4,} et {3, 4, 5}. Les sections suivantes décrivent deux façons de créer un type de bloc de flux de données qui implémente ce comportement personnalisé. La première technique utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> pour combiner la fonctionnalité d’un objet <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601> et d’un objet <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> dans un bloc propagateur. La seconde technique définit une classe dérivée de <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> et combine la fonctionnalité existante pour générer le comportement personnalisé.  
  
## <a name="using-the-encapsulate-method-to-define-the-sliding-window-dataflow-block"></a>Utilisation de la méthode d’encapsulage pour définir le bloc de flux d’une fenêtre coulissante  
 L’exemple suivant utilise la méthode <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Encapsulate%2A> pour créer un bloc propagateur à partir d’une source et d’une cible. Un bloc propagateur permet à un bloc source et à un bloc cible d’agir en tant que destinataire et expéditeur des données.  
  
 Cette technique est utile lorsque vous avez besoin d’une fonctionnalité de flux de données personnalisée, mais pas d’un type qui fournit d’autres méthodes, propriétés ou champs.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#1)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#1)]  
  
## <a name="deriving-from-ipropagatorblock-to-define-the-sliding-window-dataflow-block"></a>Dérivation d’IPropagatorBlock pour définir le bloc de flux de données d’une fenêtre coulissante  
 L’exemple suivant montre la classe `SlidingWindowBlock`. Cette classe est dérivée <xref:System.Threading.Tasks.Dataflow.IPropagatorBlock%602> pour pouvoir agir à la fois comme une source et une cible de données. Comme dans l’exemple précédent, la classe `SlidingWindowBlock` s’appuie sur des types de blocs de flux de données existants. Cependant, la classe `SlidingWindowBlock` implémente également les méthodes requises par les interfaces <xref:System.Threading.Tasks.Dataflow.ISourceBlock%601>, <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601> et <xref:System.Threading.Tasks.Dataflow.IDataflowBlock>. Toutes ces méthodes transfèrent le travail aux membres du type de bloc de flux de données prédéfini. Par exemple, la méthode `Post` transmet le travail au membre de données `m_target`, qui est également un objet <xref:System.Threading.Tasks.Dataflow.ITargetBlock%601>.  
  
 Cette technique est utile lorsque vous avez besoin d’une fonctionnalité de flux de données personnalisée, mais également d’un type qui fournit d’autres méthodes, propriétés ou champs. Par exemple, la classe `SlidingWindowBlock` est également dérivée de <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601> afin de fournir les méthodes <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceive%2A> et <xref:System.Threading.Tasks.Dataflow.IReceivableSourceBlock%601.TryReceiveAll%2A>. La classe `SlidingWindowBlock` apporte également une extensibilité en fournissant la propriété `WindowSize`, qui récupère le nombre d’éléments dans la fenêtre coulissante.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#2)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#2)]  
  
## <a name="the-complete-example"></a>Exemple complet  
 L'exemple suivant présente le code complet pour cette visite. Il montre également comment utiliser les deux blocs de fenêtre coulissante dans une méthode qui écrit dans le bloc, lit à partir de celui-ci, puis imprime les résultats dans la console.  
  
 [!code-csharp[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_slidingwindowblock/cs/slidingwindowblock.cs#100)]
 [!code-vb[TPLDataflow_SlidingWindowBlock#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_slidingwindowblock/vb/slidingwindowblock.vb#100)]  
  
## <a name="see-also"></a>Voir aussi

- [Dataflow](dataflow-task-parallel-library.md)
