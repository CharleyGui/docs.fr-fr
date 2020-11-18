---
title: 'Procédure : Spécifier le degré de parallélisme dans un bloc de flux de données'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
ms.openlocfilehash: bd77afd3e2d8ba71541ce8159a9faf3dea3aa3fe
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826864"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Procédure : Spécifier le degré de parallélisme dans un bloc de flux de données
Ce document décrit comment définir la propriété <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> pour permettre à un bloc de flux de données d'exécution de traiter plusieurs messages à la fois. Cela est utile quand vous avez un bloc de flux de données qui effectue un calcul de longue durée et qui peut tirer parti du traitement des messages en parallèle. Cet exemple utilise la classe <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> pour effectuer plusieurs opérations de flux de données simultanément ; toutefois, vous pouvez spécifier le degré maximum de parallélisme dans les types de bloc d'exécution prédéfinis fournis par la bibliothèque de flux de données TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> et <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Exemple  
 L'exemple suivant effectue deux calculs de flux de données et affiche le temps écoulé nécessaire pour chaque calcul. Le premier calcul spécifie un degré maximum de parallélisme de 1, qui est la valeur par défaut. Un degré maximum de parallélisme égal à 1 amène le bloc de flux de données à traiter les messages en série. Le deuxième calcul ressemble à la première, à ceci près qu'il spécifie un degré maximum de parallélisme égal au nombre de processeurs disponibles. Cela permet au bloc de flux de données d'effectuer plusieurs opérations en parallèle.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Par défaut, chaque bloc de flux de données prédéfini propage les messages dans l'ordre dans lequel ils sont reçus.  Bien que plusieurs messages soient traités simultanément quand vous spécifiez un degré maximum de parallélisme supérieur 1, ils sont toujours propagés dans l'ordre dans lequel ils sont reçus.  
  
 Étant donné que la propriété <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> représente le degré maximal de parallélisme, le bloc de flux de données peut s'exécuter avec un degré de parallélisme moindre spécifié par vos soins. Le bloc de flux de données peut utiliser un degré de parallélisme moindre pour satisfaire ses exigences fonctionnelles ou pour prendre en compte un manque de ressources système disponibles. Un bloc de flux de données ne choisit jamais un degré de parallélisme supérieur à celui que vous spécifiez.  
  
## <a name="see-also"></a>Voir aussi

- [Dataflow](dataflow-task-parallel-library.md)
