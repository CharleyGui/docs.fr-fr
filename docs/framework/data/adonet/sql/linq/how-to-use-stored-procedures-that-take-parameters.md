---
title: 'Comment : utiliser des procédures stockées qui prennent des paramètres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 05ecc467f75fbeda785b4bac1c3b8b1ceeb173b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174327"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="1e4d3-102">Comment : utiliser des procédures stockées qui prennent des paramètres</span><span class="sxs-lookup"><span data-stu-id="1e4d3-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="1e4d3-103">mappe des paramètres de sortie à des paramètres de référence et, pour les types valeur, déclare le paramètre comme Nullable.</span><span class="sxs-lookup"><span data-stu-id="1e4d3-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="1e4d3-104">Pour un exemple de la façon d’utiliser un paramètre d’entrée dans une requête qui renvoie un jeu de ligne, voir [Comment: Return Rowsets](how-to-return-rowsets.md).</span><span class="sxs-lookup"><span data-stu-id="1e4d3-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e4d3-105"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1e4d3-105">Example</span></span>  
 <span data-ttu-id="1e4d3-106">L'exemple suivant prend un paramètre d'entrée unique (ID client) et retourne un paramètre de sortie (total des ventes pour ce client).</span><span class="sxs-lookup"><span data-stu-id="1e4d3-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1e4d3-107"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1e4d3-107">Example</span></span>  
 <span data-ttu-id="1e4d3-108">Vous appelleriez cette procédure stockée comme suit :</span><span class="sxs-lookup"><span data-stu-id="1e4d3-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="1e4d3-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e4d3-109">See also</span></span>

- [<span data-ttu-id="1e4d3-110">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="1e4d3-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="1e4d3-111">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="1e4d3-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="1e4d3-112">Types de valeur nuls (C)</span><span class="sxs-lookup"><span data-stu-id="1e4d3-112">Nullable Value Types (C#)</span></span>](../../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
- [<span data-ttu-id="1e4d3-113">Types valeur Nullable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e4d3-113">Nullable Value Types (Visual Basic)</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
