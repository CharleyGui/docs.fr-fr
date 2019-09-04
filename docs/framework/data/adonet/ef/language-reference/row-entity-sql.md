---
title: ROW (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 06da96e8-55d7-486c-991a-4e514d837ff9
ms.openlocfilehash: dfd0031f49cbdf41797cecf21c149fafde4d7a8c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249250"
---
# <a name="row-entity-sql"></a><span data-ttu-id="6e262-102">ROW (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6e262-102">ROW (Entity SQL)</span></span>
<span data-ttu-id="6e262-103">Construit des enregistrements anonymes structurellement typés à partir d'une ou plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="6e262-103">Constructs anonymous, structurally typed records from one or more values.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e262-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e262-104">Syntax</span></span>  
  
```  
ROW ( expression [ AS alias ] [,...] )  
```  
  
## <a name="arguments"></a><span data-ttu-id="6e262-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6e262-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="6e262-106">Toute expression de requête valide qui retourne une valeur à construire dans un type de ligne.</span><span class="sxs-lookup"><span data-stu-id="6e262-106">Any valid query expression that returns a value to construct in a row type.</span></span>  
  
 `alias`  
 <span data-ttu-id="6e262-107">Spécifie un alias pour la valeur spécifiée dans un type de ligne.</span><span class="sxs-lookup"><span data-stu-id="6e262-107">Specifies an alias for the value specified in a row type.</span></span> <span data-ttu-id="6e262-108">Si aucun alias n'est fourni, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] essaie de générer un alias en fonction des règles de génération d'alias [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="6e262-108">If an alias is not provided, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to generate an alias based on the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] alias generation rules.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e262-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6e262-109">Return Value</span></span>  
 <span data-ttu-id="6e262-110">Type de ligne.</span><span class="sxs-lookup"><span data-stu-id="6e262-110">A row type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e262-111">Notes</span><span class="sxs-lookup"><span data-stu-id="6e262-111">Remarks</span></span>  
 <span data-ttu-id="6e262-112">Les constructeurs de ligne s'avèrent utiles dans [!INCLUDE[esql](../../../../../../includes/esql-md.md)] pour construire des enregistrements anonymes structurellement types à partir d'une ou plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="6e262-112">You use row constructors in the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] to construct anonymous, structurally typed records from one or more values.</span></span> <span data-ttu-id="6e262-113">Le type de résultat d'un constructeur de ligne est un type de ligne dont les types de champ correspondent aux types des valeurs qui ont servi à construire la ligne.</span><span class="sxs-lookup"><span data-stu-id="6e262-113">The result type of a row constructor is a row type whose field types correspond to the types of the values that were used to construct the row.</span></span> <span data-ttu-id="6e262-114">Par exemple, l'expression suivante construit une valeur de type `Record(a int, b string, c int)`.</span><span class="sxs-lookup"><span data-stu-id="6e262-114">For example, the following expression constructs a value of type `Record(a int, b string, c int)`.</span></span>  
  
```  
ROW(1 AS a, "abc" AS b, a+34 AS c)  
```  
  
 <span data-ttu-id="6e262-115">Si vous ne fournissez pas d'alias pour une expression contenue dans un constructeur de ligne, Entity Framework essaie d'en générer un.</span><span class="sxs-lookup"><span data-stu-id="6e262-115">If you do not provide an alias for an expression in a row constructor, the Entity Framework will try to generate one.</span></span> <span data-ttu-id="6e262-116">Pour plus d'informations, voir la section « Règles d'alias » de la rubrique [Identificateurs](identifiers-entity-sql.md) .</span><span class="sxs-lookup"><span data-stu-id="6e262-116">For more information, see the "Aliasing Rules" section of the [Identifiers](identifiers-entity-sql.md) topic.</span></span>  
  
 <span data-ttu-id="6e262-117">Les règles suivantes s'appliquent à l'utilisation d'alias dans les expressions d'un constructeur de ligne :</span><span class="sxs-lookup"><span data-stu-id="6e262-117">The following rules apply to expression aliasing in a row constructor:</span></span>  
  
- <span data-ttu-id="6e262-118">les expressions contenues dans un constructeur de ligne ne peuvent pas faire référence aux autres alias du même constructeur ;</span><span class="sxs-lookup"><span data-stu-id="6e262-118">Expressions in a row constructor cannot refer to other aliases in the same constructor.</span></span>  
  
- <span data-ttu-id="6e262-119">deux expressions contenues dans un même constructeur de ligne ne peuvent pas avoir le même alias.</span><span class="sxs-lookup"><span data-stu-id="6e262-119">Two expressions in the same row constructor cannot have the same alias.</span></span>  
  
 <span data-ttu-id="6e262-120">Pour plus d’informations sur les constructeurs de requête, consultez [construction de types](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="6e262-120">For more information about query constructors, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e262-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="6e262-121">Example</span></span>  
 <span data-ttu-id="6e262-122">La requête Entity SQL ci-dessous utilise l'opérateur ROW pour construire des enregistrements anonymes structurellement typés.</span><span class="sxs-lookup"><span data-stu-id="6e262-122">The following Entity SQL query uses the ROW operator to construct anonymous, structurally typed records.</span></span> <span data-ttu-id="6e262-123">Cette requête est basée sur le modèle de vente AdventureWorks Sales Model.</span><span class="sxs-lookup"><span data-stu-id="6e262-123">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6e262-124">Pour compiler et exécuter cette requête, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="6e262-124">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6e262-125">Suivez la procédure décrite [dans la rubrique Procédure : Exécutez une requête qui retourne les résultats](../how-to-execute-a-query-that-returns-structuraltype-results.md)de StructuralType.</span><span class="sxs-lookup"><span data-stu-id="6e262-125">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="6e262-126">Transmettez à la méthode `ExecuteStructuralTypeQuery` la requête suivante en tant qu'argument :</span><span class="sxs-lookup"><span data-stu-id="6e262-126">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ROW](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#row)]  
  
## <a name="see-also"></a><span data-ttu-id="6e262-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e262-127">See also</span></span>

- [<span data-ttu-id="6e262-128">Construction de types</span><span class="sxs-lookup"><span data-stu-id="6e262-128">Constructing Types</span></span>](constructing-types-entity-sql.md)
- [<span data-ttu-id="6e262-129">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6e262-129">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="6e262-130">Définitions de type</span><span class="sxs-lookup"><span data-stu-id="6e262-130">Type Definitions</span></span>](type-definitions-entity-sql.md)
