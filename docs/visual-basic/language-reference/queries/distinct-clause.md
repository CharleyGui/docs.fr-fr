---
title: Distinct (clause)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryDistinct
helpviewer_keywords:
- Distinct clause [Visual Basic]
- Distinct statement [Visual Basic]
- queries [Visual Basic], Distinct
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
ms.openlocfilehash: 49eaab2e6a8c48d61518ea51ef2f644b6eb48314
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875273"
---
# <a name="distinct-clause-visual-basic"></a><span data-ttu-id="4b18c-102">Distinct, clause (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4b18c-102">Distinct Clause (Visual Basic)</span></span>

<span data-ttu-id="4b18c-103">Restreint les valeurs de la variable de portée actuelle pour éliminer les valeurs en double dans les clauses de requête suivantes.</span><span class="sxs-lookup"><span data-stu-id="4b18c-103">Restricts the values of the current range variable to eliminate duplicate values in subsequent query clauses.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b18c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4b18c-104">Syntax</span></span>  
  
```vb  
Distinct  
```  
  
## <a name="remarks"></a><span data-ttu-id="4b18c-105">Notes</span><span class="sxs-lookup"><span data-stu-id="4b18c-105">Remarks</span></span>  

 <span data-ttu-id="4b18c-106">Vous pouvez utiliser la `Distinct` clause pour retourner une liste d’éléments uniques.</span><span class="sxs-lookup"><span data-stu-id="4b18c-106">You can use the `Distinct` clause to return a list of unique items.</span></span> <span data-ttu-id="4b18c-107">La `Distinct` clause force la requête à ignorer les résultats de la requête en double.</span><span class="sxs-lookup"><span data-stu-id="4b18c-107">The `Distinct` clause causes the query to ignore duplicate query results.</span></span> <span data-ttu-id="4b18c-108">La `Distinct` clause s’applique aux valeurs dupliquées pour tous les champs de retour spécifiés par la `Select` clause.</span><span class="sxs-lookup"><span data-stu-id="4b18c-108">The `Distinct` clause applies to duplicate values for all return fields specified by the `Select` clause.</span></span> <span data-ttu-id="4b18c-109">Si aucune `Select` clause n’est spécifiée, la `Distinct` clause est appliquée à la variable de portée pour la requête identifiée dans la `From` clause.</span><span class="sxs-lookup"><span data-stu-id="4b18c-109">If no `Select` clause is specified, the `Distinct` clause is applied to the range variable for the query identified in the `From` clause.</span></span> <span data-ttu-id="4b18c-110">Si la variable de portée n’est pas un type immuable, la requête n’ignore un résultat de requête que si tous les membres du type correspondent à un résultat de requête existant.</span><span class="sxs-lookup"><span data-stu-id="4b18c-110">If the range variable is not an immutable type, the query will only ignore a query result if all members of the type match an existing query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b18c-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="4b18c-111">Example</span></span>  

 <span data-ttu-id="4b18c-112">L’expression de requête suivante joint une liste de clients et une liste de commandes client.</span><span class="sxs-lookup"><span data-stu-id="4b18c-112">The following query expression joins a list of customers and a list of customer orders.</span></span> <span data-ttu-id="4b18c-113">La `Distinct` clause est incluse pour retourner une liste de noms de clients uniques et de dates de commande.</span><span class="sxs-lookup"><span data-stu-id="4b18c-113">The `Distinct` clause is included to return a list of unique customer names and order dates.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#20)]  
  
## <a name="see-also"></a><span data-ttu-id="4b18c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b18c-114">See also</span></span>

- [<span data-ttu-id="4b18c-115">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4b18c-115">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="4b18c-116">Requêtes</span><span class="sxs-lookup"><span data-stu-id="4b18c-116">Queries</span></span>](index.md)
- [<span data-ttu-id="4b18c-117">From, clause</span><span class="sxs-lookup"><span data-stu-id="4b18c-117">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="4b18c-118">Clause SELECT</span><span class="sxs-lookup"><span data-stu-id="4b18c-118">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="4b18c-119">Clause WHERE</span><span class="sxs-lookup"><span data-stu-id="4b18c-119">Where Clause</span></span>](where-clause.md)
