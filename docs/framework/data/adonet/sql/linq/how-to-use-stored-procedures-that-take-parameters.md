---
title: 'Procédure : Utiliser des procédures stockées qui prennent des paramètres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 4f2636d3bb248adbb6b912887012b0b9c246c590
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793063"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a>Procédure : Utiliser des procédures stockées qui prennent des paramètres
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] mappe des paramètres de sortie à des paramètres de référence et, pour les types valeur, déclare le paramètre comme Nullable.  
  
 Pour obtenir un exemple d’utilisation d’un paramètre d’entrée dans une requête qui retourne un ensemble de [lignes, consultez Procédure : Retourne des](how-to-return-rowsets.md)ensembles de lignes.  
  
## <a name="example"></a>Exemples  
 L'exemple suivant prend un paramètre d'entrée unique (ID client) et retourne un paramètre de sortie (total des ventes pour ce client).  
  
```  
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
- [Utilisation de types Nullable](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [Types valeur Nullable](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
