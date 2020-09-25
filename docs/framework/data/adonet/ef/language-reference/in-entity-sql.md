---
title: IN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 51662950-ee01-4857-b7b9-311dd8515966
ms.openlocfilehash: 582a3b988247f1484197c0905fecf7f4407f88b0
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203668"
---
# <a name="in-entity-sql"></a><span data-ttu-id="db14f-102">IN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="db14f-102">IN (Entity SQL)</span></span>

<span data-ttu-id="db14f-103">Détermine si une valeur correspond à une valeur incluse dans une collection.</span><span class="sxs-lookup"><span data-stu-id="db14f-103">Determines whether a value matches any value in a collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db14f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db14f-104">Syntax</span></span>  
  
```sql  
value [ NOT ] IN expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="db14f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="db14f-105">Arguments</span></span>  

 `value`  
 <span data-ttu-id="db14f-106">Toute expression valide qui retourne la valeur dont rechercher une correspondance.</span><span class="sxs-lookup"><span data-stu-id="db14f-106">Any valid expression that returns the value to match.</span></span>  
  
 <span data-ttu-id="db14f-107">[ NOT ]</span><span class="sxs-lookup"><span data-stu-id="db14f-107">[ NOT ]</span></span>  
 <span data-ttu-id="db14f-108">Spécifie que la valeur du résultat `Boolean` de IN est inversée.</span><span class="sxs-lookup"><span data-stu-id="db14f-108">Specifies that the `Boolean` result of IN be negated.</span></span>  
  
 `expression`  
 <span data-ttu-id="db14f-109">Toute expression valide qui retourne la collection dans laquelle rechercher une correspondance.</span><span class="sxs-lookup"><span data-stu-id="db14f-109">Any valid expression that returns the collection to test for a match.</span></span> <span data-ttu-id="db14f-110">Toutes les expressions doivent être du même type que le `value`ou d'un type de base commun ou dérivé de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="db14f-110">All expressions must be of the same type or of a common base or derived type as `value`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db14f-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="db14f-111">Return Value</span></span>  

 <span data-ttu-id="db14f-112">`true` si la valeur est trouvée dans la collection ; null si la valeur ou la collection est Null ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="db14f-112">`true` if the value is found in the collection; null if the value is null or the collection is null; otherwise, `false`.</span></span> <span data-ttu-id="db14f-113">L'utilisation de NOT IN inverse les résultats de IN.</span><span class="sxs-lookup"><span data-stu-id="db14f-113">Using NOT IN negates the results of IN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db14f-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="db14f-114">Example</span></span>  

 <span data-ttu-id="db14f-115">La requête Entity SQL ci-dessous utilise l'opérateur IN pour déterminer si une valeur correspond à une valeur contenue dans une collection.</span><span class="sxs-lookup"><span data-stu-id="db14f-115">The following Entity SQL query uses the IN operator to determine whether a value matches any value in a collection.</span></span> <span data-ttu-id="db14f-116">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="db14f-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="db14f-117">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="db14f-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="db14f-118">Suivez la procédure indiquée dans [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="db14f-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="db14f-119">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="db14f-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#IN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#in)]  
  
## <a name="see-also"></a><span data-ttu-id="db14f-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="db14f-120">See also</span></span>

- [<span data-ttu-id="db14f-121">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="db14f-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
