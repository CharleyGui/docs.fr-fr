---
title: 'Procédure : Utiliser des procédures stockées qui prennent des paramètres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: 17ae74a430df4d4a4670c2390ce7b2ee25b67c7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938712"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="baba5-102">Procédure : Utiliser des procédures stockées qui prennent des paramètres</span><span class="sxs-lookup"><span data-stu-id="baba5-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="baba5-103">mappe des paramètres de sortie à des paramètres de référence et, pour les types valeur, déclare le paramètre comme Nullable.</span><span class="sxs-lookup"><span data-stu-id="baba5-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="baba5-104">Pour obtenir un exemple d’utilisation d’un paramètre d’entrée dans une requête qui retourne un ensemble de [lignes, consultez Procédure: Retourne des](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)ensembles de lignes.</span><span class="sxs-lookup"><span data-stu-id="baba5-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="baba5-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="baba5-105">Example</span></span>  
 <span data-ttu-id="baba5-106">L'exemple suivant prend un paramètre d'entrée unique (ID client) et retourne un paramètre de sortie (total des ventes pour ce client).</span><span class="sxs-lookup"><span data-stu-id="baba5-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="baba5-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="baba5-107">Example</span></span>  
 <span data-ttu-id="baba5-108">Vous appelleriez cette procédure stockée comme suit :</span><span class="sxs-lookup"><span data-stu-id="baba5-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="baba5-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="baba5-109">See also</span></span>

- [<span data-ttu-id="baba5-110">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="baba5-110">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
- [<span data-ttu-id="baba5-111">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="baba5-111">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
- [<span data-ttu-id="baba5-112">Utilisation de types Nullable</span><span class="sxs-lookup"><span data-stu-id="baba5-112">Using Nullable Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="baba5-113">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="baba5-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
