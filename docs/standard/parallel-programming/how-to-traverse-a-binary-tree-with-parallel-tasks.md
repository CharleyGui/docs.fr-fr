---
title: 'Procédure : parcourir un arbre binaire avec des tâches parallèles'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: ca70021c7d071abe480cb4ed866e34f171cc3b45
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825531"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a>Procédure : parcourir un arbre binaire avec des tâches parallèles
L’exemple suivant montre deux façons d’utiliser des tâches parallèles pour parcourir une arborescence de données. La création de l’arborescence en soi est considérée comme un exercice.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 Les deux méthodes indiquées sont équivalentes d’un point de vue fonctionnel. Si vous utilisez la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> pour créer et exécuter les tâches, vous obtenez un handle à partir des tâches, qui peut être utilisé pour attendre les tâches et gérer les exceptions.  
  
## <a name="see-also"></a>Voir aussi

- [Bibliothèque parallèle de tâches](task-parallel-library-tpl.md)
