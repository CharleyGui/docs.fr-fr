---
title: 'Procédure : Utiliser des procédures stockées qui prennent des paramètres'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b935fd84-cb9c-4205-8c48-658d5db2ec93
ms.openlocfilehash: e9d77cd1dc82e1b103c5f0d9f3f447ed105acaec
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003244"
---
# <a name="how-to-use-stored-procedures-that-take-parameters"></a><span data-ttu-id="7bad2-102">Procédure : Utiliser des procédures stockées qui prennent des paramètres</span><span class="sxs-lookup"><span data-stu-id="7bad2-102">How to: Use Stored Procedures that Take Parameters</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="7bad2-103">mappe des paramètres de sortie à des paramètres de référence et, pour les types valeur, déclare le paramètre comme Nullable.</span><span class="sxs-lookup"><span data-stu-id="7bad2-103">maps output parameters to reference parameters, and for value types declares the parameter as nullable.</span></span>  
  
 <span data-ttu-id="7bad2-104">Pour obtenir un exemple d’utilisation d’un paramètre d’entrée dans une requête qui retourne un ensemble de lignes, consultez [How à : Retourne les ensembles de lignes @ no__t-0.</span><span class="sxs-lookup"><span data-stu-id="7bad2-104">For an example of how to use an input parameter in a query that returns a rowset, see [How to: Return Rowsets](how-to-return-rowsets.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bad2-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="7bad2-105">Example</span></span>  
 <span data-ttu-id="7bad2-106">L'exemple suivant prend un paramètre d'entrée unique (ID client) et retourne un paramètre de sortie (total des ventes pour ce client).</span><span class="sxs-lookup"><span data-stu-id="7bad2-106">The following example takes a single input parameter (the customer ID) and returns an out parameter (the total sales for that customer).</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="7bad2-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="7bad2-107">Example</span></span>  
 <span data-ttu-id="7bad2-108">Vous appelleriez cette procédure stockée comme suit :</span><span class="sxs-lookup"><span data-stu-id="7bad2-108">You would call this stored procedure as follows:</span></span>  
  
 [!code-csharp[DLinqSprox#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSprox/cs/Program.cs#3)]
 [!code-vb[DLinqSprox#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSprox/vb/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7bad2-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7bad2-109">See also</span></span>

- [<span data-ttu-id="7bad2-110">Procédures stockées</span><span class="sxs-lookup"><span data-stu-id="7bad2-110">Stored Procedures</span></span>](stored-procedures.md)
- [<span data-ttu-id="7bad2-111">Téléchargement d’exemples de base de données</span><span class="sxs-lookup"><span data-stu-id="7bad2-111">Downloading Sample Databases</span></span>](downloading-sample-databases.md)
- [<span data-ttu-id="7bad2-112">Utilisation des types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="7bad2-112">Using Nullable Value Types</span></span>](../../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
- [<span data-ttu-id="7bad2-113">Types valeur Nullable</span><span class="sxs-lookup"><span data-stu-id="7bad2-113">Nullable Value Types</span></span>](../../../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
