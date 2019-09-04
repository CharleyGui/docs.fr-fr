---
title: '- Encadré (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 208e54ef-4741-4ec5-89d6-6ff700863cb0
ms.openlocfilehash: effd537bcd53052830f2195e18ca959b49d87255
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249923"
---
# <a name="--negative-entity-sql"></a><span data-ttu-id="4cd9f-102">- (négatif) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="4cd9f-102">- (Negative) (Entity SQL)</span></span>
<span data-ttu-id="4cd9f-103">Retourne la forme négative de la valeur d'une expression numérique.</span><span class="sxs-lookup"><span data-stu-id="4cd9f-103">Returns the negative of the value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4cd9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4cd9f-104">Syntax</span></span>  
  
```  
- expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="4cd9f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4cd9f-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="4cd9f-106">Toute expression valide de l'un des types de données numériques.</span><span class="sxs-lookup"><span data-stu-id="4cd9f-106">Any valid expression of any one of the numeric data types.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="4cd9f-107">Types de résultats</span><span class="sxs-lookup"><span data-stu-id="4cd9f-107">Result Types</span></span>  
 <span data-ttu-id="4cd9f-108">Type de données de l' `expression`.</span><span class="sxs-lookup"><span data-stu-id="4cd9f-108">The data type of `expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4cd9f-109">Notes</span><span class="sxs-lookup"><span data-stu-id="4cd9f-109">Remarks</span></span>  
 <span data-ttu-id="4cd9f-110">Si l' `expression` est un type non signé, le type du résultat sera le type signé le plus proche du type de l' `expression`.</span><span class="sxs-lookup"><span data-stu-id="4cd9f-110">If `expression` is an unsigned type, the result type will be the signed type that most closely relates to the type of `expression`.</span></span> <span data-ttu-id="4cd9f-111">Par exemple, si l' `expression` est de type Byte, une valeur de type Int16 sera retournée.</span><span class="sxs-lookup"><span data-stu-id="4cd9f-111">For example, if `expression` is of type Byte, a value of type Int16 will be returned.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4cd9f-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="4cd9f-112">Example</span></span>  
 <span data-ttu-id="4cd9f-113">La requête Entity SQL ci-dessous utilise l'opérateur arithmétique - pour retourner la forme négative de la valeur d'une expression numérique.</span><span class="sxs-lookup"><span data-stu-id="4cd9f-113">The following Entity SQL query uses the - arithmetic operator to return the negative of the value of a numeric expression.</span></span> <span data-ttu-id="4cd9f-114">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="4cd9f-114">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4cd9f-115">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="4cd9f-115">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="4cd9f-116">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="4cd9f-116">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="4cd9f-117">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="4cd9f-117">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#NEGATIVE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#negative)]  
  
## <a name="see-also"></a><span data-ttu-id="4cd9f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4cd9f-118">See also</span></span>

- [<span data-ttu-id="4cd9f-119">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="4cd9f-119">Entity SQL Reference</span></span>](entity-sql-reference.md)
