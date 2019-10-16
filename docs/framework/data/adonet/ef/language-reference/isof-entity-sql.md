---
title: ISOF (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b2b0d34-d0a7-4bcd-baf2-58aa8456d00b
ms.openlocfilehash: c4c4cbf74cb17cf43e79c42ff42d1e68122fd534
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319719"
---
# <a name="isof-entity-sql"></a><span data-ttu-id="d9e1c-102">ISOF (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-102">ISOF (Entity SQL)</span></span>
<span data-ttu-id="d9e1c-103">Détermine si le type d'une expression appartient au type spécifié ou à l'un de ses sous-types.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-103">Determines whether the type of an expression is of the specified type or one of its subtypes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9e1c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9e1c-104">Syntax</span></span>  
  
```sql  
expression IS [ NOT ] OF ( [ ONLY ] type )  
```  
  
## <a name="arguments"></a><span data-ttu-id="d9e1c-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="d9e1c-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="d9e1c-106">Toute expression de requête valide pour en déterminer le type.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-106">Any valid query expression to determine the type of.</span></span>  
  
 <span data-ttu-id="d9e1c-107">NOT</span><span class="sxs-lookup"><span data-stu-id="d9e1c-107">NOT</span></span>  
 <span data-ttu-id="d9e1c-108">Inverse le résultat EDM.Boolean de l'opérateur IS OF.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-108">Negates the EDM.Boolean result of IS OF.</span></span>  
  
 <span data-ttu-id="d9e1c-109">ONLY</span><span class="sxs-lookup"><span data-stu-id="d9e1c-109">ONLY</span></span>  
 <span data-ttu-id="d9e1c-110">Indique que l'opérateur IS OF ne retourne `true` que si `expression` appartient au type `type` et non à l'un de ses sous-types.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-110">Specifies that IS OF returns `true` only if `expression` is of type `type` and not any of one its subtypes.</span></span>  
  
 `type`  
 <span data-ttu-id="d9e1c-111">Type sur lequel tester `expression`.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-111">The type to test `expression` against.</span></span> <span data-ttu-id="d9e1c-112">Le type doit être qualifié par un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-112">The type must be namespace-qualified.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9e1c-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d9e1c-113">Return Value</span></span>  
 <span data-ttu-id="d9e1c-114">`true` si `expression` est de type T, qui est soit un type de base, soit un type dérivé de `type` ; null si `expression` a la valeur null au moment de l'exécution ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-114">`true` if `expression` is of type T and T is either a base type, or a derived type of `type`; null if `expression` is null at runtime; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9e1c-115">Notes</span><span class="sxs-lookup"><span data-stu-id="d9e1c-115">Remarks</span></span>  
 <span data-ttu-id="d9e1c-116">Les expressions `expression IS NOT OF (type)` et `expression IS NOT OF (ONLY type)` sont syntaxiquement équivalentes à `NOT (expression IS OF (type))` et `NOT (expression IS OF (ONLY type))`, respectivement.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-116">The expressions `expression IS NOT OF (type)` and `expression IS NOT OF (ONLY type)` are syntactically equivalent to `NOT (expression IS OF (type))` and `NOT (expression IS OF (ONLY type))`, respectively.</span></span>  
  
 <span data-ttu-id="d9e1c-117">Le tableau suivant indique le comportement de l'opérateur `IS OF` sur certains modèles courants et d'autres plus singuliers.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-117">The following table shows the behavior of `IS OF` operator over some typical- and corner patterns.</span></span> <span data-ttu-id="d9e1c-118">Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :</span><span class="sxs-lookup"><span data-stu-id="d9e1c-118">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="d9e1c-119">Motif</span><span class="sxs-lookup"><span data-stu-id="d9e1c-119">Pattern</span></span>|<span data-ttu-id="d9e1c-120">Comportement</span><span class="sxs-lookup"><span data-stu-id="d9e1c-120">Behavior</span></span>|  
|-------------|--------------|  
|<span data-ttu-id="d9e1c-121">null IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-121">null IS OF (EntityType)</span></span>|<span data-ttu-id="d9e1c-122">Exception</span><span class="sxs-lookup"><span data-stu-id="d9e1c-122">Throws</span></span>|  
|<span data-ttu-id="d9e1c-123">null IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-123">null IS OF (ComplexType)</span></span>|<span data-ttu-id="d9e1c-124">Exception</span><span class="sxs-lookup"><span data-stu-id="d9e1c-124">Throws</span></span>|  
|<span data-ttu-id="d9e1c-125">null IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-125">null IS OF (RowType)</span></span>|<span data-ttu-id="d9e1c-126">Exception</span><span class="sxs-lookup"><span data-stu-id="d9e1c-126">Throws</span></span>|  
|<span data-ttu-id="d9e1c-127">TREAT (null AS EntityType) IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-127">TREAT (null AS EntityType) IS OF (EntityType)</span></span>|<span data-ttu-id="d9e1c-128">Retourne DBNull</span><span class="sxs-lookup"><span data-stu-id="d9e1c-128">Returns DBNull</span></span>|  
|<span data-ttu-id="d9e1c-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-129">TREAT (null AS ComplexType) IS OF (ComplexType)</span></span>|<span data-ttu-id="d9e1c-130">Exception</span><span class="sxs-lookup"><span data-stu-id="d9e1c-130">Throws</span></span>|  
|<span data-ttu-id="d9e1c-131">TREAT (null AS RowType) IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-131">TREAT (null AS RowType) IS OF (RowType)</span></span>|<span data-ttu-id="d9e1c-132">Exception</span><span class="sxs-lookup"><span data-stu-id="d9e1c-132">Throws</span></span>|  
|<span data-ttu-id="d9e1c-133">EntityType IS OF (EntityType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-133">EntityType IS OF (EntityType)</span></span>|<span data-ttu-id="d9e1c-134">Retourne true/false</span><span class="sxs-lookup"><span data-stu-id="d9e1c-134">Returns true/false</span></span>|  
|<span data-ttu-id="d9e1c-135">ComplexType IS OF (ComplexType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-135">ComplexType IS OF (ComplexType)</span></span>|<span data-ttu-id="d9e1c-136">Exception</span><span class="sxs-lookup"><span data-stu-id="d9e1c-136">Throws</span></span>|  
|<span data-ttu-id="d9e1c-137">RowType IS OF (RowType)</span><span class="sxs-lookup"><span data-stu-id="d9e1c-137">RowType IS OF (RowType)</span></span>|<span data-ttu-id="d9e1c-138">Exception</span><span class="sxs-lookup"><span data-stu-id="d9e1c-138">Throws</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d9e1c-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="d9e1c-139">Example</span></span>  
 <span data-ttu-id="d9e1c-140">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] suivante utilise l’opérateur IS OF pour déterminer le type d’une expression de requête, puis utilise l’opérateur TREAT pour convertir un objet du type course en collection d’objets de type OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="d9e1c-140">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the IS OF operator to determine the type of a query expression, and then uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="d9e1c-141">Cette requête est basée sur le modèle [School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d9e1c-141">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 <span data-ttu-id="d9e1c-142">[ ! code-SQL [DP EntityServices concepts # TREAT_ISOF] ~/samples/snippets/tsql/VS_Snippets_Data/dp EntityServices concepts/TSQL/EntitySql. SQL # TREAT_ISOF)]</span><span class="sxs-lookup"><span data-stu-id="d9e1c-142">[!code-sql[DP EntityServices Concepts#TREAT_ISOF]~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9e1c-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d9e1c-143">See also</span></span>

- [<span data-ttu-id="d9e1c-144">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d9e1c-144">Entity SQL Reference</span></span>](entity-sql-reference.md)
