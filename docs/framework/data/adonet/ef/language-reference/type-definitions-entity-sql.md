---
title: Définitions de type (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 7e4e6f0e9f64816d10a69a8b0639728e4cd7af80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201016"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="12eea-102">Définitions de type (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="12eea-102">Type Definitions (Entity SQL)</span></span>

<span data-ttu-id="12eea-103">Une définition de type est utilisée dans l'instruction de déclaration d'une fonction incluse [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="12eea-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="12eea-104">Notes</span><span class="sxs-lookup"><span data-stu-id="12eea-104">Remarks</span></span>  

 <span data-ttu-id="12eea-105">L’instruction de déclaration pour une fonction inline se compose du mot clé [Function](function-entity-sql.md) suivi de l’identificateur représentant le nom de la fonction (par exemple, « myavg ») suivi d’une liste de définitions de paramètres entre parenthèses (par exemple, « redevances collection (Decimal) »).</span><span class="sxs-lookup"><span data-stu-id="12eea-105">The declaration statement for an inline function consists of the [FUNCTION](function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="12eea-106">La liste de définitions de paramètres est composée de zéro, une ou plusieurs définitions de paramètres.</span><span class="sxs-lookup"><span data-stu-id="12eea-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="12eea-107">Chaque définition de paramètre se compose d’un identificateur (le nom du paramètre de la fonction, par exemple, « dues ») suivi d’une définition de type (par exemple, « Collection(Decimal) »).</span><span class="sxs-lookup"><span data-stu-id="12eea-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="12eea-108">Les définitions de type peuvent correspondre :</span><span class="sxs-lookup"><span data-stu-id="12eea-108">The type definitions can be either:</span></span>  
  
- <span data-ttu-id="12eea-109">au type de l'identificateur (par exemple, « Int32 » ou « AdventureWorks.Order ») ;</span><span class="sxs-lookup"><span data-stu-id="12eea-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
- <span data-ttu-id="12eea-110">au mot clé `COLLECTION` suivi par une autre définition de type entre parenthèses (par exemple, « Collection(AdventureWorks.Order) ») ;</span><span class="sxs-lookup"><span data-stu-id="12eea-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
- <span data-ttu-id="12eea-111">au mot clé ROW suivi par une liste de définitions de propriétés entre parenthèses (par exemple, « Ligne (x AdventureWorks.Order) »).</span><span class="sxs-lookup"><span data-stu-id="12eea-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="12eea-112">Les définitions de propriétés ont un format tel que « `identifier type_definition` , `identifier type_definition` ,... ».</span><span class="sxs-lookup"><span data-stu-id="12eea-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
- <span data-ttu-id="12eea-113">au mot clé REF suivi par le type de l'identificateur entre parenthèses (par exemple, « Ref(AdventureWorks.Order) »).</span><span class="sxs-lookup"><span data-stu-id="12eea-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="12eea-114">L’opérateur de définition de type REF a besoin d’un type d’entité comme argument.</span><span class="sxs-lookup"><span data-stu-id="12eea-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="12eea-115">Vous ne pouvez pas spécifier un type primitif comme argument.</span><span class="sxs-lookup"><span data-stu-id="12eea-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="12eea-116">Vous pouvez également imbriquer des définitions de type (par exemple, « Collection(Row(x Ref(AdventureWorks.Order))) »).</span><span class="sxs-lookup"><span data-stu-id="12eea-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="12eea-117">Les options de définition de type sont :</span><span class="sxs-lookup"><span data-stu-id="12eea-117">The type definition options are:</span></span>  
  
- <span data-ttu-id="12eea-118">`IdentifierName supported_type` ou</span><span class="sxs-lookup"><span data-stu-id="12eea-118">`IdentifierName supported_type`, or</span></span>  
  
- <span data-ttu-id="12eea-119">`IdentifierName` COLLECTION(`type_definition`) ou</span><span class="sxs-lookup"><span data-stu-id="12eea-119">`IdentifierName` COLLECTION(`type_definition`), or</span></span>  
  
- <span data-ttu-id="12eea-120">`IdentifierName` ROW(`property_definition`) ou</span><span class="sxs-lookup"><span data-stu-id="12eea-120">`IdentifierName` ROW(`property_definition`), or</span></span>  
  
- <span data-ttu-id="12eea-121">`IdentifierName` REF(`supported_entity_type`).</span><span class="sxs-lookup"><span data-stu-id="12eea-121">`IdentifierName` REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="12eea-122">L'option de définition de propriété est `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="12eea-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="12eea-123">Les types pris en charge sont tous les types figurant dans l'espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="12eea-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="12eea-124">Ils incluent à la fois les types primitifs et les types d'entités.</span><span class="sxs-lookup"><span data-stu-id="12eea-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="12eea-125">Les types d'entités pris en charge font référence uniquement aux types d'entités dans l'espace de noms actuel.</span><span class="sxs-lookup"><span data-stu-id="12eea-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="12eea-126">Ils n'incluent pas les types primitifs.</span><span class="sxs-lookup"><span data-stu-id="12eea-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="12eea-127">Exemples</span><span class="sxs-lookup"><span data-stu-id="12eea-127">Examples</span></span>  

 <span data-ttu-id="12eea-128">L'exemple suivant correspond à une définition de type simple.</span><span class="sxs-lookup"><span data-stu-id="12eea-128">The following is an example of a simple type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="12eea-129">L'exemple suivant correspond à une définition de type COLLECTION.</span><span class="sxs-lookup"><span data-stu-id="12eea-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="12eea-130">L'exemple suivant correspond à une définition de type ROW.</span><span class="sxs-lookup"><span data-stu-id="12eea-130">The following is an example of a ROW type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="12eea-131">L'exemple suivant correspond à une définition de type REF.</span><span class="sxs-lookup"><span data-stu-id="12eea-131">The following is an example of a REF type definition.</span></span>  
  
```sql  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="12eea-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="12eea-132">See also</span></span>

- [<span data-ttu-id="12eea-133">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="12eea-133">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="12eea-134">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="12eea-134">Entity SQL Reference</span></span>](entity-sql-reference.md)
