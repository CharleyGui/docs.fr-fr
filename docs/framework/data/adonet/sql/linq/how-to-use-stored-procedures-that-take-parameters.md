---
title: 'Procédure : Utiliser des procédures stockées qui prennent des paramètres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: a54e2ee553629179022b68658d44cbcb02ab590f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184961"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Procédure : Utiliser des procédures stockées qui prennent des paramètres

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mappe des paramètres de sortie à des paramètres de référence et, pour les types valeur, déclare le paramètre comme Nullable.  
  
 Pour obtenir un exemple d’utilisation d’un paramètre d’entrée dans une requête qui retourne un ensemble de lignes, consultez [How to : Return](how-to-return-rowsets.md)rowset.  
  
## <a name="example"></a>Exemple  

 L'exemple suivant prend un paramètre d'entrée unique (ID client) et retourne un paramètre de sortie (total des ventes pour ce client).  
  
```sql
CREATE PROCEDURE [dbo].[CustOrderTotal]
@CustomerID nchar(5),  
@TotalSales money OUTPUT  
AS  
SELECT @TotalSales = SUM(OD.UNITPRICE*(1-OD.DISCOUNT) * OD.QUANTITY)  
FROM ORDERS O, "ORDER DETAILS" OD  
where O.CUSTOMERID = @CustomerID AND O.ORDERID = OD.ORDERID  
```  
  
 [!code-csharp[DLinqSprox#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/northwind-sprox.cs#2)]
 [!code-vb[DLinqSprox#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/northwind-sprox.vb#2)]  
  
## <a name="example"></a>Exemple  

 Vous appelleriez cette procédure stockée comme suit :  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a>Voir aussi

- [Procédures stockées](stored-procedures.md)
- [Téléchargement d’exemples de base de données](downloading-sample-databases.md)
- [Types valeur Nullable (C#)](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [Types valeur Nullable (Visual Basic)](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
