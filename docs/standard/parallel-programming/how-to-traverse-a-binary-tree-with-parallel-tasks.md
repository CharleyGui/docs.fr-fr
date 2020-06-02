---
title: 'Procédure : parcourir un arbre binaire avec des tâches parallèles'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to traverse a tree
ms.assetid: 4265d169-6c69-4f36-b10d-b7ae7f72f4df
ms.openlocfilehash: 5ac81a61691ec20daafc9e18978ba5814a150383
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288067"
---
# <a name="how-to-traverse-a-binary-tree-with-parallel-tasks"></a><span data-ttu-id="d5d12-102">Procédure : parcourir un arbre binaire avec des tâches parallèles</span><span class="sxs-lookup"><span data-stu-id="d5d12-102">How to: Traverse a Binary Tree with Parallel Tasks</span></span>
<span data-ttu-id="d5d12-103">L’exemple suivant montre deux façons d’utiliser des tâches parallèles pour parcourir une arborescence de données.</span><span class="sxs-lookup"><span data-stu-id="d5d12-103">The following example shows two ways in which parallel tasks can be used to traverse a tree data structure.</span></span> <span data-ttu-id="d5d12-104">La création de l’arborescence en soi est considérée comme un exercice.</span><span class="sxs-lookup"><span data-stu-id="d5d12-104">The creation of the tree itself is left as an exercise.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5d12-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5d12-105">Example</span></span>  
 [!code-csharp[TPL#16](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/tpl.cs#16)]
 [!code-vb[TPL#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/treewalk.vb#16)]  
  
 <span data-ttu-id="d5d12-106">Les deux méthodes indiquées sont équivalentes d’un point de vue fonctionnel.</span><span class="sxs-lookup"><span data-stu-id="d5d12-106">The two methods shown are functionally equivalent.</span></span> <span data-ttu-id="d5d12-107">Si vous utilisez la méthode <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> pour créer et exécuter les tâches, vous obtenez un handle à partir des tâches, qui peut être utilisé pour attendre les tâches et gérer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="d5d12-107">By using the <xref:System.Threading.Tasks.TaskFactory.StartNew%2A> method to create and run the tasks, you get a handle back from the tasks which can be used to wait on the tasks and handle exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5d12-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5d12-108">See also</span></span>

- [<span data-ttu-id="d5d12-109">Bibliothèque parallèle de tâches</span><span class="sxs-lookup"><span data-stu-id="d5d12-109">Task Parallel Library (TPL)</span></span>](task-parallel-library-tpl.md)
