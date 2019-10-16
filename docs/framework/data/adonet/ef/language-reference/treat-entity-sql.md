---
title: TREAT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 5b77f156-55de-4cb4-8154-87f707d4c635
ms.openlocfilehash: 38099fa83ed78b40d46faeb5e617157f7aa7c1a1
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319263"
---
# <a name="treat-entity-sql"></a><span data-ttu-id="7d133-102">TREAT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7d133-102">TREAT (Entity SQL)</span></span>
<span data-ttu-id="7d133-103">Traite un objet d'un type de base déterminé en tant qu'objet du type dérivé spécifié.</span><span class="sxs-lookup"><span data-stu-id="7d133-103">Treats an object of a particular base type as an object of the specified derived type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d133-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d133-104">Syntax</span></span>  
  
```sql  
TREAT ( expression as type)  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d133-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7d133-105">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="7d133-106">Toute expression de requête valide qui retourne une entité.</span><span class="sxs-lookup"><span data-stu-id="7d133-106">Any valid query expression that returns an entity.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d133-107">Le type de l'expression spécifiée doit être un sous-type du type de données spécifié, ou le type de données doit être un sous-type du type de l'expression.</span><span class="sxs-lookup"><span data-stu-id="7d133-107">The type of the specified expression must be a subtype of the specified data type, or the data type must be a subtype of the type of expression.</span></span>  
  
 `type`  
 <span data-ttu-id="7d133-108">Type d'entité.</span><span class="sxs-lookup"><span data-stu-id="7d133-108">An entity type.</span></span> <span data-ttu-id="7d133-109">Le type doit être qualifié par un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="7d133-109">The type must be qualified by a namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d133-110">L'expression spécifiée doit être un sous-type du type de données spécifié, ou le type de données doit être un sous-type de l'expression.</span><span class="sxs-lookup"><span data-stu-id="7d133-110">The specified expression must be a subtype of the specified data type, or the data type must be a subtype of the expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d133-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7d133-111">Return Value</span></span>  
 <span data-ttu-id="7d133-112">Valeur du type de données spécifié.</span><span class="sxs-lookup"><span data-stu-id="7d133-112">A value of the specified data type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d133-113">Notes</span><span class="sxs-lookup"><span data-stu-id="7d133-113">Remarks</span></span>  
 <span data-ttu-id="7d133-114">TREAT est utilisé pour effectuer un upcast entre des classes connexes.</span><span class="sxs-lookup"><span data-stu-id="7d133-114">TREAT is used to perform upcasting between related classes.</span></span> <span data-ttu-id="7d133-115">Par exemple, si `Employee` est dérivé de `Person` et que p est de type `Person`, `TREAT(p AS NamespaceName.Employee)` effectue un upcast d'une instance générique de `Person` vers `Employee`; autrement dit, cela vous permet de traiter p en tant que `Employee`.</span><span class="sxs-lookup"><span data-stu-id="7d133-115">For example, if `Employee` derives from `Person` and p is of type `Person`, `TREAT(p AS NamespaceName.Employee)` upcasts a generic `Person` instance to `Employee`; that is, it allows you to treat p as `Employee`.</span></span>  
  
 <span data-ttu-id="7d133-116">TREAT est utilisé dans des scénarios d'héritage dans lesquels vous pouvez exécuter une requête de ce type :</span><span class="sxs-lookup"><span data-stu-id="7d133-116">TREAT is used in inheritance scenarios where you can do a query like the following:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)   
```  
  
 <span data-ttu-id="7d133-117">Cette requête effectue un upcast d'entités `Person` vers le type `Employee` .</span><span class="sxs-lookup"><span data-stu-id="7d133-117">This query upcasts `Person` entities to the `Employee` type.</span></span> <span data-ttu-id="7d133-118">S'il s'avère que la valeur de p n'est pas de type `Employee`, l'expression génère la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="7d133-118">If the value of p is not actually of type `Employee`, the expression yields the value `null`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d133-119">L’expression spécifiée `Employee` doit être un sous-type du type de données spécifié `Person`, ou le type de données doit être un sous-type de l’expression.</span><span class="sxs-lookup"><span data-stu-id="7d133-119">The specified expression `Employee` must be a subtype of the specified data type `Person`, or the data type must be a subtype of the expression.</span></span> <span data-ttu-id="7d133-120">Sinon, l'expression génère une erreur de compilation.</span><span class="sxs-lookup"><span data-stu-id="7d133-120">Otherwise, the expression will result in a compile-time error.</span></span>  
  
 <span data-ttu-id="7d133-121">Le tableau suivant indique le comportement de TREAT sur certains modèles communs et d'autres moins courants.</span><span class="sxs-lookup"><span data-stu-id="7d133-121">The following table shows the behavior of treat over some typical patterns and some less common patterns.</span></span> <span data-ttu-id="7d133-122">Toutes les exceptions sont levées côté client avant que le fournisseur soit appelé :</span><span class="sxs-lookup"><span data-stu-id="7d133-122">All exceptions are thrown from the client side before the provider gets invoked:</span></span>  
  
|<span data-ttu-id="7d133-123">Motif</span><span class="sxs-lookup"><span data-stu-id="7d133-123">Pattern</span></span>|<span data-ttu-id="7d133-124">Comportement</span><span class="sxs-lookup"><span data-stu-id="7d133-124">Behavior</span></span>|  
|-------------|--------------|  
|`TREAT (null AS EntityType)`|<span data-ttu-id="7d133-125">Retourne `DbNull`.</span><span class="sxs-lookup"><span data-stu-id="7d133-125">Returns `DbNull`.</span></span>|  
|`TREAT (null AS ComplexType)`|<span data-ttu-id="7d133-126">Lève une exception.</span><span class="sxs-lookup"><span data-stu-id="7d133-126">Throws an exception.</span></span>|  
|`TREAT (null AS RowType)`|<span data-ttu-id="7d133-127">Lève une exception/</span><span class="sxs-lookup"><span data-stu-id="7d133-127">Throws an exception/</span></span>|  
|`TREAT (EntityType AS EntityType)`|<span data-ttu-id="7d133-128">Retourne `EntityType` ou la valeur `null`.</span><span class="sxs-lookup"><span data-stu-id="7d133-128">Returns `EntityType` or `null`.</span></span>|  
|`TREAT (ComplexType AS ComplexType)`|<span data-ttu-id="7d133-129">Lève une exception.</span><span class="sxs-lookup"><span data-stu-id="7d133-129">Throws an exception.</span></span>|  
|`TREAT (RowType AS RowType)`|<span data-ttu-id="7d133-130">Lève une exception.</span><span class="sxs-lookup"><span data-stu-id="7d133-130">Throws an exception.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d133-131">Exemple</span><span class="sxs-lookup"><span data-stu-id="7d133-131">Example</span></span>  
 <span data-ttu-id="7d133-132">La requête [!INCLUDE[esql](../../../../../../includes/esql-md.md)] ci-dessous utilise l'opérateur TREAT pour convertir un objet du type Course en collection d'objets du type OnsiteCourse.</span><span class="sxs-lookup"><span data-stu-id="7d133-132">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the TREAT operator to convert an object of the type Course to a collection of objects of the type OnsiteCourse.</span></span> <span data-ttu-id="7d133-133">Cette requête est basée sur le modèle [School](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="7d133-133">The query is based on the [School Model](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb896300(v=vs.100)).</span></span>  
  
 [!code-sql[DP EntityServices Concepts#TREAT_ISOF](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#treat_isof)]  
  
## <a name="see-also"></a><span data-ttu-id="7d133-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7d133-134">See also</span></span>

- [<span data-ttu-id="7d133-135">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7d133-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="7d133-136">Types structurés autorisant la valeur null</span><span class="sxs-lookup"><span data-stu-id="7d133-136">Nullable Structured Types</span></span>](nullable-structured-types-entity-sql.md)
