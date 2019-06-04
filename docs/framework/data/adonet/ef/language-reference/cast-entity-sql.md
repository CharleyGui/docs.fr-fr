---
title: CAST (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 07b6d750-dfd4-48a9-b86c-3badcbba6f70
ms.openlocfilehash: 743c90cd9bc77a89051c59a217befa4275b28572
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489948"
---
# <a name="cast-entity-sql"></a><span data-ttu-id="46f2e-102">CAST (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="46f2e-102">CAST (Entity SQL)</span></span>
<span data-ttu-id="46f2e-103">Convertit une expression d'un type de données à un autre.</span><span class="sxs-lookup"><span data-stu-id="46f2e-103">Converts an expression of one data type to another.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46f2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46f2e-104">Syntax</span></span>  
  
```  
CAST ( expression AS data_type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="46f2e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="46f2e-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="46f2e-106">Toute expression valide convertible en `data_type`.</span><span class="sxs-lookup"><span data-stu-id="46f2e-106">Any valid expression that is convertible to `data_type`.</span></span>  
  
 `data_type`  
 <span data-ttu-id="46f2e-107">Type de données cible fourni par le système.</span><span class="sxs-lookup"><span data-stu-id="46f2e-107">The target system-supplied data type.</span></span> <span data-ttu-id="46f2e-108">Il doit s'agir d'un type primitif (scalaire).</span><span class="sxs-lookup"><span data-stu-id="46f2e-108">It must be a primitive (scalar) type.</span></span> <span data-ttu-id="46f2e-109">Le type de données `data_type` utilisé dépend de l'espace de requête.</span><span class="sxs-lookup"><span data-stu-id="46f2e-109">The `data_type` used depends on the query space.</span></span> <span data-ttu-id="46f2e-110">Si une requête est exécutée avec la classe <xref:System.Data.EntityClient.EntityCommand>, le type de données est un type défini dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="46f2e-110">If a query is executed with the <xref:System.Data.EntityClient.EntityCommand>, the data type is a type defined in the conceptual model.</span></span> <span data-ttu-id="46f2e-111">Pour plus d'informations, consultez [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span><span class="sxs-lookup"><span data-stu-id="46f2e-111">For more information, see [CSDL Specification](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md).</span></span> <span data-ttu-id="46f2e-112">Si une requête est exécutée avec la classe <xref:System.Data.Objects.ObjectQuery%601>, le type de données est un type CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="46f2e-112">If a query is executed with <xref:System.Data.Objects.ObjectQuery%601>, the data type is a common language runtime (CLR) type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="46f2e-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="46f2e-113">Return Value</span></span>  
 <span data-ttu-id="46f2e-114">Retourne la même valeur que `data_type`.</span><span class="sxs-lookup"><span data-stu-id="46f2e-114">Returns the same value as `data_type`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46f2e-115">Notes</span><span class="sxs-lookup"><span data-stu-id="46f2e-115">Remarks</span></span>  
 <span data-ttu-id="46f2e-116">L’expression de cast a une sémantique similaire à l’expression de conversion Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="46f2e-116">The cast expression has similar semantics to the Transact-SQL CONVERT expression.</span></span> <span data-ttu-id="46f2e-117">L'expression de cast sert à convertir une valeur d'un type en valeur d'un autre type.</span><span class="sxs-lookup"><span data-stu-id="46f2e-117">The cast expression is used to convert a value of one type into a value of another type.</span></span>  
  
```  
CAST( e as T )  
```  
  
 <span data-ttu-id="46f2e-118">Si e est de type S et que S est convertible en T, l'expression ci-dessus est une expression de cast valide.</span><span class="sxs-lookup"><span data-stu-id="46f2e-118">If e is of some type S, and S is convertible to T, then the above expression is a valid cast expression.</span></span> <span data-ttu-id="46f2e-119">T doit correspondre à un type primitif (scalaire).</span><span class="sxs-lookup"><span data-stu-id="46f2e-119">T must be a primitive (scalar) type.</span></span>  
  
 <span data-ttu-id="46f2e-120">Les valeurs des facettes Precision et Scale peuvent être éventuellement fournies lors de la conversion en `Edm.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="46f2e-120">Values for the precision and scale facets may optionally be provided when casting to `Edm.Decimal`.</span></span> <span data-ttu-id="46f2e-121">Si elles ne sont pas explicitement fournies, les valeurs par défaut des facettes Precision et Scale sont respectivement 18 et 0.</span><span class="sxs-lookup"><span data-stu-id="46f2e-121">If not explicitly provided, the default values for precision and scale are 18 and 0, respectively.</span></span> <span data-ttu-id="46f2e-122">Plus spécifiquement, les surcharges suivantes sont prises en charge pour `Decimal`:</span><span class="sxs-lookup"><span data-stu-id="46f2e-122">Specifically, the following overloads are supported for `Decimal`:</span></span>  
  
- `CAST( d as Edm.Decimal );`  
  
- `CAST( d as Edm.Decimal(precision) );`  
  
- `CAST( d as Edm.Decimal(precision, scale) );`  
  
 <span data-ttu-id="46f2e-123">L'utilisation d'une expression de cast est considérée comme une conversion explicite.</span><span class="sxs-lookup"><span data-stu-id="46f2e-123">The use of a cast expression is considered an explicit conversion.</span></span> <span data-ttu-id="46f2e-124">Les conversions explicites peuvent tronquer des données ou entraîner une perte de précision.</span><span class="sxs-lookup"><span data-stu-id="46f2e-124">Explicit conversions might truncate data or lose precision.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46f2e-125">CAST n'est pris en charge que sur les types primitifs et les types de membres d'énumération.</span><span class="sxs-lookup"><span data-stu-id="46f2e-125">CAST is only supported over primitive types and enumeration member types.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46f2e-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="46f2e-126">Example</span></span>  
 <span data-ttu-id="46f2e-127">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur CAST pour convertir une expression d'un type de données à une autre.</span><span class="sxs-lookup"><span data-stu-id="46f2e-127">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the CAST operator to cast an expression of one data type to another.</span></span> <span data-ttu-id="46f2e-128">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="46f2e-128">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="46f2e-129">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="46f2e-129">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="46f2e-130">Suivez la procédure décrite dans [Comment : Exécuter une requête qui retourne les résultats PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="46f2e-130">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="46f2e-131">Transmettez à la méthode `ExecutePrimitiveTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="46f2e-131">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CAST](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#cast)]  
  
## <a name="see-also"></a><span data-ttu-id="46f2e-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46f2e-132">See also</span></span>

- [<span data-ttu-id="46f2e-133">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="46f2e-133">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
