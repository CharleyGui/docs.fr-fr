---
title: 'Procédure : Gérer les clés composites dans les requêtes'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ce2f14fd-1038-458a-91e3-a078c61f0d10
ms.openlocfilehash: a6c6e7d1c1d29a049b50f4ea9d70ef5cd9e89a44
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793570"
---
# <a name="how-to-handle-composite-keys-in-queries"></a>Procédure : Gérer les clés composites dans les requêtes
Certains opérateurs ne peuvent prendre qu’un seul argument. Si votre argument doit inclure plusieurs colonnes de la base de données, vous devez créer un type anonyme pour représenter la combinaison.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant présente une requête qui appelle l’opérateur `GroupBy` et qui peut prendre un seul argument `key`.  
  
 [!code-csharp[DLinqCompositeKeys#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#1)]
 [!code-vb[DLinqCompositeKeys#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#1)]  
  
## <a name="example"></a>Exemple  
 La même situation s'applique aux jointures, comme dans l'exemple suivant :  
  
 [!code-csharp[DLinqCompositeKeys#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCompositeKeys/cs/Program.cs#2)]
 [!code-vb[DLinqCompositeKeys#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCompositeKeys/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Concepts relatifs aux requêtes](query-concepts.md)
