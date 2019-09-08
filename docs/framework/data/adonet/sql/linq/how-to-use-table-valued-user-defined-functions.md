---
title: 'Procédure : Utiliser des fonctions tables définies par l’utilisateur'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5a4ae2b4-3290-4aa1-bc95-fc70c51b54cf
ms.openlocfilehash: 31797ae7d0fe23227cc4af733fbceac5d474f779
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781443"
---
# <a name="how-to-use-table-valued-user-defined-functions"></a>Procédure : Utiliser des fonctions tables définies par l’utilisateur
Une fonction table retourne un jeu de lignes unique (contrairement aux procédures stockées qui peuvent retourner plusieurs formes de résultats). Étant donné que le type de retour d’une fonction table est `Table`, vous pouvez utiliser une fonction table à tout endroit dans SQL où il est possible d’utiliser une table. Vous pouvez également utiliser la fonction table comme une table.  
  
## <a name="example"></a>Exemples  
 La fonction SQL suivante déclare explicitement qu'elle retourne un `TABLE`. Par conséquent, la structure de jeu de lignes retournée est définie implicitement.  
  
```  
CREATE FUNCTION ProductsCostingMoreThan(@cost money)  
RETURNS TABLE  
AS  
RETURN  
    SELECT ProductID, UnitPrice  
    FROM Products  
    WHERE UnitPrice > @cost  
```  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mappe la fonction comme suit :  
  
 [!code-csharp[DLinqUDFS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/northwind-tfunc.cs#1)]
 [!code-vb[DLinqUDFS#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/northwind-tfunc.vb#1)]  
  
## <a name="example"></a>Exemples  
 Le code SQL suivant montre que vous pouvez spécifier la jointure à la table que la fonction retourne et l'utiliser également comme n'importe quelle autre table :  
  
```  
SELECT p2.ProductName, p1.UnitPrice  
FROM dbo.ProductsCostingMoreThan(80.50)  
AS p1 INNER JOIN Products AS p2 ON p1.ProductID = p2.ProductID  
```  
  
 Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la requête serait restituée comme suit :  
  
 [!code-csharp[DLinqUDFS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqUDFS/cs/Program.cs#2)]
 [!code-vb[DLinqUDFS#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqUDFS/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions définies par l’utilisateur](user-defined-functions.md)
