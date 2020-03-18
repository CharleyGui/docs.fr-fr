---
title: 'Comment : utiliser JoinBlock pour lire des données issues de plusieurs sources'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
ms.openlocfilehash: 66fd7ed7a98b8be8f88f65ecb52710a1e40af778
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139739"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Comment : utiliser JoinBlock pour lire des données issues de plusieurs sources
Ce document explique comment utiliser la classe <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> pour effectuer une opération lorsque des données sont disponibles à partir de plusieurs sources. Il présente aussi comment utiliser le mode non gourmand pour permettre à plusieurs blocs de jointure de partager plus efficacement une source de données.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a> Exemple  
 L'exemple suivant définit trois types de ressources, `NetworkResource`, `FileResource` et `MemoryResource`, et effectue des opérations lorsque les ressources sont disponibles. Cet exemple nécessite une paire `NetworkResource` et `MemoryResource` pour effectuer la première opération et une paire `FileResource` et `MemoryResource` pour effectuer la seconde opération. Pour permettre aux opérations de se produire lorsque toutes les ressources requises sont disponibles, cet exemple utilise la classe <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Lorsqu'un objet <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> reçoit les données de toutes les sources, il envoie ces données à la cible, qui dans cet exemple est un objet <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Les objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> lisent à partir d'un pool partagé d'objets `MemoryResource`.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Pour permettre l'utilisation efficace du pool partagé des objets `MemoryResource`, cet exemple spécifie un objet <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> qui contient le jeu de propriétés <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> à `False` pour créer les objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> qui agissent en mode non gourmand. Un bloc de jointure non-gourmand remet les messages entrants jusqu'à ce qu'il y en ait un disponible à partir de chaque source. Si n'importe quel message remis à plus tard a été reçu par un autre bloc, le bloc de jointure redémarre le processus. Le mode non gourmand permet aux blocs de jointure qui partagent un ou plusieurs blocs sources d'avancer quand les autres blocs attendent des données. Dans cet exemple, si un objet `MemoryResource` est ajouté au pool `memoryResources`, le premier bloc de jointure peut progresser pour recevoir sa deuxième source de données. Si cet exemple visait à utiliser le mode gourmand, qui est la valeur par défaut, un bloc de jointure peut prendre l'objet `MemoryResource` et attendre que la deuxième ressource soit disponible. Toutefois, si l'autre bloc de jointure a sa deuxième source de données disponible, il ne peut pas avancer car l'objet `MemoryResource` a été pris par l'autre bloc de jointure.  
  
## <a name="robust-programming"></a>Programmation fiable  
 L'utilisation de jointures non gourmandes peut également vous aider à empêcher tout interblocage dans votre application. Dans une application logicielle, un *blocage* se produit lorsque au moins deux processus comportent chacun une ressource et attendent mutuellement qu’un autre processus en libère une autre. Examinez la requête qui définit deux objets <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Les deux objets lisent chacun des données de deux blocs sources partagés. En mode gourmand, si un bloc de jointure lit depuis la première source et le deuxième bloc de jointure lit depuis la seconde source, l'application peut être interbloquée car les deux blocs de jointure attendent mutuellement l'autre pour libérer sa ressource. En mode non gourmand, chaque bloc de jointure lit uniquement à partir de ses sources lorsque toutes les données sont disponibles, éliminant par conséquent, le risque d'interblocage.  
  
## <a name="see-also"></a>Voir aussi

- [Flux de données](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
