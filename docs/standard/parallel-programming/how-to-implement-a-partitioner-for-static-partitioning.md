---
title: 'Procédure : implémenter un partitionneur pour un partitionnement statique'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- tasks, how to create a static partitioner
ms.assetid: f4410508-cac6-4ba7-bef1-c5e68b2794f3
ms.openlocfilehash: 22d2cf788d4726488512703356a75f84efd04250
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84278504"
---
# <a name="how-to-implement-a-partitioner-for-static-partitioning"></a><span data-ttu-id="c287d-102">Procédure : implémenter un partitionneur pour un partitionnement statique</span><span class="sxs-lookup"><span data-stu-id="c287d-102">How to: Implement a Partitioner for Static Partitioning</span></span>
<span data-ttu-id="c287d-103">L’exemple suivant montre une façon d’implémenter un partitionneur personnalisé simple pour PLINQ qui exécute le partitionnement statique.</span><span class="sxs-lookup"><span data-stu-id="c287d-103">The following example shows one way to implement a simple custom partitioner for PLINQ that performs static partitioning.</span></span> <span data-ttu-id="c287d-104">Étant donné que le partitionneur ne prend pas en charge les partitions dynamiques, il n’est pas utilisable à partir de <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c287d-104">Because the partitioner does not support dynamic partitions, it is not consumable from <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c287d-105">Ce partitionneur particulier peut fournir une accélération par rapport au partitionneur de plage par défaut pour les sources de données pour lequel chaque élément requiert une quantité croissante de temps de traitement.</span><span class="sxs-lookup"><span data-stu-id="c287d-105">This particular partitioner might provide speedup over the default range partitioner for data sources for which each element requires an increasing amount of processing time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c287d-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="c287d-106">Example</span></span>  
 [!code-csharp[TPL_Partitioners#05](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#05)]  
  
 <span data-ttu-id="c287d-107">Les partitions dans cet exemple sont basées sur l’hypothèse d’une augmentation linéaire du temps de traitement pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="c287d-107">The partitions in this example are based on the assumption of a linear increase in processing time for each element.</span></span> <span data-ttu-id="c287d-108">Dans le monde réel, il peut être difficile de prédire le temps de traitement de cette façon.</span><span class="sxs-lookup"><span data-stu-id="c287d-108">In the real world, it might be difficult to predict processing times in this way.</span></span> <span data-ttu-id="c287d-109">Si vous utilisez un partitionneur statique avec une source de données spécifique, vous pouvez optimiser la formule de partitionnement pour la source, ajouter une logique d’équilibrage de charge ou utiliser une méthode de partitionnement par segments, comme illustré dans [Guide pratique pour implémenter des partitions dynamiques](how-to-implement-dynamic-partitions.md).</span><span class="sxs-lookup"><span data-stu-id="c287d-109">If you are using a static partitioner with a specific data source, you can optimize the partitioning formula for the source, add load-balancing logic, or use a chunk partitioning approach as demonstrated in [How to: Implement Dynamic Partitions](how-to-implement-dynamic-partitions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c287d-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c287d-110">See also</span></span>

- [<span data-ttu-id="c287d-111">Partitionneurs personnalisés pour PLINQ et TPL</span><span class="sxs-lookup"><span data-stu-id="c287d-111">Custom Partitioners for PLINQ and TPL</span></span>](custom-partitioners-for-plinq-and-tpl.md)
