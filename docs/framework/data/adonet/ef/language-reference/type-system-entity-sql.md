---
title: System, type (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: b8b721aff5b7886fdb897ecaa3dcc163ec94ae79
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149829"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="14822-102">System, type (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="14822-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="14822-103">prend en charge un certain nombre de types :</span><span class="sxs-lookup"><span data-stu-id="14822-103">supports a number of types:</span></span>  
  
- <span data-ttu-id="14822-104">Les types primitifs (simples), tels que `Int32` et `String.`</span><span class="sxs-lookup"><span data-stu-id="14822-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
- <span data-ttu-id="14822-105">Les types nominaux qui sont définis dans le schéma, tels que <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType> et <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="14822-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
- <span data-ttu-id="14822-106">Les types anonymes qui ne sont pas définis explicitement dans le schéma : <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType> et <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="14822-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="14822-107">Cette section traite des types anonymes qui ne sont pas définis explicitement dans le schéma, mais qui sont appuyés par l’entité SQL.</span><span class="sxs-lookup"><span data-stu-id="14822-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="14822-108">Pour plus d’informations sur les types primitifs et nominaux, voir [Les types de modèles conceptuels (CSDL).](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl)</span><span class="sxs-lookup"><span data-stu-id="14822-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="14822-109">Lignes</span><span class="sxs-lookup"><span data-stu-id="14822-109">Rows</span></span>  
 <span data-ttu-id="14822-110">La structure d'une ligne dépend de la séquence de membres typés et nommés que la ligne contient.</span><span class="sxs-lookup"><span data-stu-id="14822-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="14822-111">Un type de ligne n'a aucune identité et ne peut pas faire l'objet d'un héritage.</span><span class="sxs-lookup"><span data-stu-id="14822-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="14822-112">Les instances du même type de ligne sont équivalentes si les membres sont respectivement équivalents.</span><span class="sxs-lookup"><span data-stu-id="14822-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="14822-113">Les lignes n'ont aucun comportement au-delà de leur équivalence structurelle et n'ont aucun équivalent dans le Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="14822-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="14822-114">Les requêtes peuvent donner des structures qui contiennent des lignes ou des collections de lignes.</span><span class="sxs-lookup"><span data-stu-id="14822-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="14822-115">La liaison d’API entre les requêtes [!INCLUDE[esql](../../../../../../includes/esql-md.md)] et le langage hôte définit la façon dont les lignes sont réalisées dans la requête qui a produit le résultat.</span><span class="sxs-lookup"><span data-stu-id="14822-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="14822-116">Pour plus d’informations sur la façon de construire une ligne d’instance, voir [Construire des types](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="14822-116">For information on how to construct a row instance, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="14822-117">Collections</span><span class="sxs-lookup"><span data-stu-id="14822-117">Collections</span></span>  
 <span data-ttu-id="14822-118">Les types de collections représentent zéro instance ou plus d’autres objets.</span><span class="sxs-lookup"><span data-stu-id="14822-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="14822-119">Pour plus d’informations sur la façon de construire la collecte, voir [Construire des types](constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="14822-119">For information on how to construct collection, see [Constructing Types](constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="14822-120">References</span><span class="sxs-lookup"><span data-stu-id="14822-120">References</span></span>  
 <span data-ttu-id="14822-121">Une référence est un pointeur logique vers une entité spécifique dans un jeu d'entités spécifique.</span><span class="sxs-lookup"><span data-stu-id="14822-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="14822-122">prend en charge les opérateurs suivants pour construire, déconstruire et explorer les références :</span><span class="sxs-lookup"><span data-stu-id="14822-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
- [<span data-ttu-id="14822-123">Ref</span><span class="sxs-lookup"><span data-stu-id="14822-123">REF</span></span>](ref-entity-sql.md)  
  
- [<span data-ttu-id="14822-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="14822-124">CREATEREF</span></span>](createref-entity-sql.md)  
  
- [<span data-ttu-id="14822-125">Clé</span><span class="sxs-lookup"><span data-stu-id="14822-125">KEY</span></span>](key-entity-sql.md)  
  
- [<span data-ttu-id="14822-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="14822-126">DEREF</span></span>](deref-entity-sql.md)  
  
 <span data-ttu-id="14822-127">Vous pouvez explorer une référence en utilisant l'opérateur `.` (point) d'accès au membre.</span><span class="sxs-lookup"><span data-stu-id="14822-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="14822-128">L'extrait de code suivant extrait la propriété ID (de Order) en explorant la propriété r (référence).</span><span class="sxs-lookup"><span data-stu-id="14822-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```sql  
select o2.r.Id
from (select ref(o) as r from LOB.Orders as o) as o2
```  
  
 <span data-ttu-id="14822-129">Si la valeur de la référence est Null, si la cible de la référence n'existe pas, le résultat est null.</span><span class="sxs-lookup"><span data-stu-id="14822-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14822-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="14822-130">See also</span></span>

- [<span data-ttu-id="14822-131">Vue d'ensemble d'Entity SQL</span><span class="sxs-lookup"><span data-stu-id="14822-131">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="14822-132">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="14822-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="14822-133">CAST</span><span class="sxs-lookup"><span data-stu-id="14822-133">CAST</span></span>](cast-entity-sql.md)
- [<span data-ttu-id="14822-134">Spécifications CSDL, SSDL et MSL</span><span class="sxs-lookup"><span data-stu-id="14822-134">CSDL, SSDL, and MSL Specifications</span></span>](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)
