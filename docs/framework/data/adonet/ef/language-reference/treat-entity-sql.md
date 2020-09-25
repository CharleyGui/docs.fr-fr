---
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: bb41c0fed944ce4db11878b9213a62c6f851418e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201042"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="e2082-102">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e2082-102">TREAT (Entity SQL)</span></span>

<span data-ttu-id="e2082-103">Traite un objet d'un type de base déterminé en tant qu'objet du type dérivé spécifié.</span><span class="sxs-lookup"><span data-stu-id="e2082-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2082-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2082-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e2082-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="e2082-105">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="e2082-106">Toute expression de requête valide qui retourne une entité.</span><span class="sxs-lookup"><span data-stu-id="e2082-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2082-107">Le type de l'expression spécifiée doit être un sous-type du type de données spécifié, ou le type de données doit être un sous-type du type de l'expression.</span><span class="sxs-lookup"><span data-stu-id="e2082-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="e2082-108">Type d'entité.</span><span class="sxs-lookup"><span data-stu-id="e2082-108">An entity type.</span></span> <span data-ttu-id="e2082-109">Le type doit être qualifié par un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="e2082-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2082-110">L'expression spécifiée doit être un sous-type du type de données spécifié, ou le type de données doit être un sous-type de l'expression.</span><span class="sxs-lookup"><span data-stu-id="e2082-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2082-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="e2082-111">Return Value</span></span>  

 <span data-ttu-id="e2082-112">Valeur du type de données spécifié.</span><span class="sxs-lookup"><span data-stu-id="e2082-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2082-113">Notes</span><span class="sxs-lookup"><span data-stu-id="e2082-113">Remarks</span></span>  

 <span data-ttu-id="e2082-114">TREAT est utilisé pour effectuer un upcast entre des classes connexes.</span><span class="sxs-lookup"><span data-stu-id="e2082-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="e2082-115">Par exemple, si `Employee` est dérivé de `Person` et que p est de type `Person`, `TREAT(p AS NamespaceName.Employee)` effectue un upcast d'une instance générique de `Person` vers `Employee`; autrement dit, cela vous permet de traiter p en tant que `Employee`.</span><span class="sxs-lookup"><span data-stu-id="e2082-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="e2082-116">TREAT est utilisé dans des scénarios d'héritage dans lesquels vous pouvez exécuter une requête de ce type :</span><span class="sxs-lookup"><span data-stu-id="e2082-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)
```  
  
 <span data-ttu-id="e2082-117">Cette requête effectue un upcast d'entités `Person` vers le type `Employee` .</span><span class="sxs-lookup"><span data-stu-id="e2082-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="e2082-118">S'il s'avère que la valeur de p n'est pas de type `Employee`, l'expression génère la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="e2082-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2082-119">L’expression spécifiée `Employee` doit être un sous-type du type de données spécifié `Person` , ou le type de données doit être un sous-type de l’expression.</span><span class="sxs-lookup"><span data-stu-id="e2082-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="e2082-120">Sinon, l'expression génère une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="e2082-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="e2082-121">Le tableau suivant indique le comportement de TREAT sur certains modèles communs et d'autres moins courants.</span><span class="sxs-lookup"><span data-stu-id="e2082-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="e2082-122">Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :</span><span class="sxs-lookup"><span data-stu-id="e2082-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="e2082-123">Modèle</span><span class="sxs-lookup"><span data-stu-id="e2082-123">Pattern</span></span>|<span data-ttu-id="e2082-124">Comportement</span><span class="sxs-lookup"><span data-stu-id="e2082-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="e2082-125">Retourne `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="e2082-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="e2082-126">Lève une exception.</span><span class="sxs-lookup"><span data-stu-id="e2082-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="e2082-127">Lève une exception/</span><span class="sxs-lookup"><span data-stu-id="e2082-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="e2082-128">Retourne `EntityType` ou la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="e2082-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="e2082-129">Lève une exception.</span><span class="sxs-lookup"><span data-stu-id="e2082-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="e2082-130">Lève une exception.</span><span class="sxs-lookup"><span data-stu-id="e2082-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="e2082-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="e2082-131">Example</span></span>  

 <span data-ttu-id="e2082-132">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur TREAT pour convertir un objet du type Course en collection d'objets du type OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="e2082-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="e2082-133">Cette requête est basée sur le modèle [School](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="e2082-133">The query is based on the [School Model](/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="e2082-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e2082-134">See also</span></span>

- [<span data-ttu-id="e2082-135">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e2082-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e2082-136">Types structurés Nullable</span><span class="sxs-lookup"><span data-stu-id="e2082-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
