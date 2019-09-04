---
title: TOP (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4a4a0954-82e2-4eae-bcaf-7c4552f3532d
ms.openlocfilehash: 8b55519b7f95deb6463af4c0a6a2a53975e5b5a2
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248970"
---
# <a name="top-entity-sql"></a><span data-ttu-id="dfec0-102">TOP (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dfec0-102">TOP (Entity SQL)</span></span>

<span data-ttu-id="dfec0-103">La clause SELECT peut avoir une sous-clause TOP facultative après le modificateur ALL/DISTINCT facultatif.</span><span class="sxs-lookup"><span data-stu-id="dfec0-103">The SELECT clause can have an optional TOP sub-clause following the optional ALL/DISTINCT modifier.</span></span> <span data-ttu-id="dfec0-104">La sous-clause TOP spécifie que seul le premier ensemble de lignes sera retourné à partir du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="dfec0-104">The TOP sub-clause specifies that only the first set of rows will be returned from the query result.</span></span>

## <a name="syntax"></a><span data-ttu-id="dfec0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfec0-105">Syntax</span></span>

```
[ TOP (n) ]
```

## <a name="arguments"></a><span data-ttu-id="dfec0-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="dfec0-106">Arguments</span></span>

<span data-ttu-id="dfec0-107">`n`Expression numérique qui spécifie le nombre de lignes à retourner.</span><span class="sxs-lookup"><span data-stu-id="dfec0-107">`n` The numeric expression that specifies the number of rows to be returned.</span></span> <span data-ttu-id="dfec0-108">`n` peut être un littéral numérique unique ou un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="dfec0-108">`n` could be a single numeric literal or a single parameter.</span></span>

## <a name="remarks"></a><span data-ttu-id="dfec0-109">Notes</span><span class="sxs-lookup"><span data-stu-id="dfec0-109">Remarks</span></span>

<span data-ttu-id="dfec0-110">L'expression TOP doit être un littéral numérique unique ou un paramètre unique.</span><span class="sxs-lookup"><span data-stu-id="dfec0-110">The TOP expression must be either a single numeric literal or a single parameter.</span></span> <span data-ttu-id="dfec0-111">Si un littéral constant est utilisé, le type de littéral doit implicitement pouvoir être promu en Edm.Int64 (octet, int16, int32 ou int64 ou tout type de fournisseur correspondant à un type qui peut être promu en Edm.Int64) et sa valeur doit être supérieure ou égale au zéro.</span><span class="sxs-lookup"><span data-stu-id="dfec0-111">If a constant literal is used, the literal type must be implicitly promotable to Edm.Int64 (byte, int16, int32 or int64 or any provider type that maps to a type that is promotable to Edm.Int64) and its value must be greater than or equal to zero.</span></span> <span data-ttu-id="dfec0-112">Dans le cas contraire, une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="dfec0-112">Otherwise an exception will be raised.</span></span> <span data-ttu-id="dfec0-113">Si un paramètre est utilisé comme expression, le type du paramètre doit aussi pouvoir être implicitement promu en Edm.Int64, mais la valeur réelle du paramètre ne pourra pas être validée au moment de la compilation, car les valeurs de paramètres sont liées tardivement.</span><span class="sxs-lookup"><span data-stu-id="dfec0-113">If a parameter is used as an expression, the parameter type must also be implicitly promotable to Edm.Int64, but there will be no validation of the actual parameter value during compilation because the parameter values are late bounded.</span></span>

<span data-ttu-id="dfec0-114">L'exemple suivant est une expression TOP constante :</span><span class="sxs-lookup"><span data-stu-id="dfec0-114">The following is an example of constant TOP expression:</span></span>

```sql
select distinct top(10) c.a1, c.a2 from T as a
```

<span data-ttu-id="dfec0-115">Voici un exemple d’expression TOP paramétrable :</span><span class="sxs-lookup"><span data-stu-id="dfec0-115">The following is an example of parameterized TOP expression:</span></span>

```sql
select distinct top(@topParam) c.a1, c.a2 from T as a
```

<span data-ttu-id="dfec0-116">TOP n'est pas déterministe, à moins que la requête soit triée.</span><span class="sxs-lookup"><span data-stu-id="dfec0-116">TOP is non-deterministic unless the query is sorted.</span></span> <span data-ttu-id="dfec0-117">Si vous avez besoin d'un résultat déterministe, utilisez les sous-clauses [SKIP](skip-entity-sql.md) et [LIMIT](limit-entity-sql.md) dans la clause [ORDER BY](order-by-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="dfec0-117">If you require a deterministic result, use the [SKIP](skip-entity-sql.md) and [LIMIT](limit-entity-sql.md) sub-clauses in the [ORDER BY](order-by-entity-sql.md) clause.</span></span> <span data-ttu-id="dfec0-118">TOP et SKIP/LIMIT s'excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="dfec0-118">The TOP and SKIP/LIMIT are mutually exclusive.</span></span>

## <a name="example"></a><span data-ttu-id="dfec0-119">Exemples</span><span class="sxs-lookup"><span data-stu-id="dfec0-119">Example</span></span>

<span data-ttu-id="dfec0-120">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante utilise TOP pour spécifier la ligne supérieure à retourner à partir du résultat de la requête.</span><span class="sxs-lookup"><span data-stu-id="dfec0-120">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TOP to specify the top one row to be returned from the query result.</span></span> <span data-ttu-id="dfec0-121">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="dfec0-121">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dfec0-122">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="dfec0-122">To compile and run this query, follow these steps:</span></span>

1. <span data-ttu-id="dfec0-123">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="dfec0-123">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>

2. <span data-ttu-id="dfec0-124">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="dfec0-124">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>

    [!code-csharp[DP EntityServices Concepts 2#TOP](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#top)]

## <a name="see-also"></a><span data-ttu-id="dfec0-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfec0-125">See also</span></span>

- [<span data-ttu-id="dfec0-126">SELECT</span><span class="sxs-lookup"><span data-stu-id="dfec0-126">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="dfec0-127">SKIP</span><span class="sxs-lookup"><span data-stu-id="dfec0-127">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="dfec0-128">LIMIT</span><span class="sxs-lookup"><span data-stu-id="dfec0-128">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="dfec0-129">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="dfec0-129">ORDER BY</span></span>](order-by-entity-sql.md)
- [<span data-ttu-id="dfec0-130">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="dfec0-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
