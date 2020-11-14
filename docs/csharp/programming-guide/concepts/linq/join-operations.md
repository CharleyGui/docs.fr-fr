---
title: JoinOpérations (C#)
description: Une jointure de deux sources de données associe des objets à des objets qui partagent un attribut dans des sources de données. En savoir plus sur les méthodes de jointure dans l’infrastructure LINQ en C#.
ms.date: 07/20/2015
ms.assetid: 5105e0da-1267-4c00-837a-f0e9602279b8
no-loc:
- 'Join'
- 'GroupJoin'
ms.openlocfilehash: 1b453f1752edf0cc126f8e27dbdd9e91ad9143f3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165692"
---
# <a name="no-locjoin-operations-c"></a><span data-ttu-id="06b39-104">JoinOpérations (C#)</span><span class="sxs-lookup"><span data-stu-id="06b39-104">Join Operations (C#)</span></span>

<span data-ttu-id="06b39-105">Une *jointure* de deux sources de données est l’association des objets d’une source de données aux objets qui partagent un attribut commun dans une autre source de données.</span><span class="sxs-lookup"><span data-stu-id="06b39-105">A *join* of two data sources is the association of objects in one data source with objects that share a common attribute in another data source.</span></span>  
  
 <span data-ttu-id="06b39-106">JoinING est une opération importante dans les requêtes qui ciblent des sources de données dont les relations ne peuvent pas être suivies directement.</span><span class="sxs-lookup"><span data-stu-id="06b39-106">Joining is an important operation in queries that target data sources whose relationships to each other cannot be followed directly.</span></span> <span data-ttu-id="06b39-107">En programmation orientée objet, cela peut correspondre à une corrélation entre objets qui n'est pas modélisée, par exemple la direction vers l'arrière dans une relation à sens unique.</span><span class="sxs-lookup"><span data-stu-id="06b39-107">In object-oriented programming, this could mean a correlation between objects that is not modeled, such as the backwards direction of a one-way relationship.</span></span> <span data-ttu-id="06b39-108">Voici un exemple de relation à sens unique : une classe Customer a une propriété de type City, alors que la classe City n'a aucune propriété correspondant à une collection d'objets Customer.</span><span class="sxs-lookup"><span data-stu-id="06b39-108">An example of a one-way relationship is a Customer class that has a property of type City, but the City class does not have a property that is a collection of Customer objects.</span></span> <span data-ttu-id="06b39-109">Si vous avez une liste d'objets City et si vous souhaitez rechercher tous les clients de chaque ville, vous pouvez recourir à une opération de jointure.</span><span class="sxs-lookup"><span data-stu-id="06b39-109">If you have a list of City objects and you want to find all the customers in each city, you could use a join operation to find them.</span></span>  
  
 <span data-ttu-id="06b39-110">Les méthodes de jointure fournies dans le framework LINQ sont <xref:System.Linq.Enumerable.Join%2A> et <xref:System.Linq.Enumerable.GroupJoin%2A>.</span><span class="sxs-lookup"><span data-stu-id="06b39-110">The join methods provided in the LINQ framework are <xref:System.Linq.Enumerable.Join%2A> and <xref:System.Linq.Enumerable.GroupJoin%2A>.</span></span> <span data-ttu-id="06b39-111">Ces méthodes effectuent des équijointures, qui sont des jointures associant deux sources de données en fonction de l’égalité de leurs clés.</span><span class="sxs-lookup"><span data-stu-id="06b39-111">These methods perform equijoins, or joins that match two data sources based on equality of their keys.</span></span> <span data-ttu-id="06b39-112">(Pour comparaison, Transact-SQL prend en charge les opérateurs de jointure autres que « Equals », par exemple l’opérateur « inférieur à ».) En termes de base de données relationnelle, <xref:System.Linq.Enumerable.Join%2A> implémente une jointure interne, un type de jointure dans lequel seuls les objets qui ont une correspondance dans l’autre jeu de données sont retournés.</span><span class="sxs-lookup"><span data-stu-id="06b39-112">(For comparison, Transact-SQL supports join operators other than 'equals', for example the 'less than' operator.) In relational database terms, <xref:System.Linq.Enumerable.Join%2A> implements an inner join, a type of join in which only those objects that have a match in the other data set are returned.</span></span> <span data-ttu-id="06b39-113">La méthode <xref:System.Linq.Enumerable.GroupJoin%2A> n’a aucun équivalent direct dans le contexte des bases de données relationnelles, mais elle implémente un sur-ensemble de jointures internes et de jointures externes gauches.</span><span class="sxs-lookup"><span data-stu-id="06b39-113">The <xref:System.Linq.Enumerable.GroupJoin%2A> method has no direct equivalent in relational database terms, but it implements a superset of inner joins and left outer joins.</span></span> <span data-ttu-id="06b39-114">Une jointure externe gauche est une jointure qui retourne chaque élément de la source de données (gauche), même si elle n’a pas d’éléments corrélés dans l’autre source de données.</span><span class="sxs-lookup"><span data-stu-id="06b39-114">A left outer join is a join that returns each element of the first (left) data source, even if it has no correlated elements in the other data source.</span></span>  
  
 <span data-ttu-id="06b39-115">L'illustration suivante présente une vue conceptuelle de deux ensembles, ainsi que leurs éléments inclus dans une jointure interne ou une jointure externe gauche.</span><span class="sxs-lookup"><span data-stu-id="06b39-115">The following illustration shows a conceptual view of two sets and the elements within those sets that are included in either an inner join or a left outer join.</span></span>  
  
 ![Deux cercles se chevauchant montrant l’interne&#47;externe.](./media/join-operations/join-method-overlapping-circles.png)  
  
## <a name="methods"></a><span data-ttu-id="06b39-117">Méthodes</span><span class="sxs-lookup"><span data-stu-id="06b39-117">Methods</span></span>  
  
|<span data-ttu-id="06b39-118">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="06b39-118">Method Name</span></span>|<span data-ttu-id="06b39-119">Description</span><span class="sxs-lookup"><span data-stu-id="06b39-119">Description</span></span>|<span data-ttu-id="06b39-120">Syntaxe d'expression de requête C#</span><span class="sxs-lookup"><span data-stu-id="06b39-120">C# Query Expression Syntax</span></span>|<span data-ttu-id="06b39-121">Informations complémentaires</span><span class="sxs-lookup"><span data-stu-id="06b39-121">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|Join|<span data-ttu-id="06b39-122">Joins deux séquences basées sur des fonctions de sélection de clé et extrait des paires de valeurs.</span><span class="sxs-lookup"><span data-stu-id="06b39-122">Joins two sequences based on key selector functions and extracts pairs of values.</span></span>|`join … in … on … equals …`|<xref:System.Linq.Enumerable.Join%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Join%2A?displayProperty=nameWithType>|  
|GroupJoin|<span data-ttu-id="06b39-123">Joindeux séquences basées sur des fonctions de sélection de clé et regroupent les correspondances résultantes pour chaque élément.</span><span class="sxs-lookup"><span data-stu-id="06b39-123">Joins two sequences based on key selector functions and groups the resulting matches for each element.</span></span>|`join … in … on … equals … into …`|<xref:System.Linq.Enumerable.GroupJoin%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.GroupJoin%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="06b39-124">Exemples de syntaxe d’expression de requête</span><span class="sxs-lookup"><span data-stu-id="06b39-124">Query expression syntax examples</span></span>
  
### Join  
  
<span data-ttu-id="06b39-125">L’exemple suivant utilise la `join … in … on … equals …` clause pour joindre deux séquences en fonction d’une valeur spécifique :</span><span class="sxs-lookup"><span data-stu-id="06b39-125">The following example uses the `join … in … on … equals …` clause to join two sequences based on specific value:</span></span>
  
[!code-csharp[Join](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#Join)]  

### GroupJoin  

<span data-ttu-id="06b39-126">L’exemple suivant utilise la `join … in … on … equals … into …` clause pour joindre deux séquences en fonction d’une valeur spécifique et regroupe les correspondances résultantes pour chaque élément :</span><span class="sxs-lookup"><span data-stu-id="06b39-126">The following example uses the `join … in … on … equals … into …` clause to join two sequences based on specific value and groups the resulting matches for each element:</span></span>
  
[!code-csharp[GroupJoin](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csLINQJoinOperation/CS/JoinOperation.cs#GroupJoin)]  
  
## <a name="see-also"></a><span data-ttu-id="06b39-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="06b39-127">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="06b39-128">Vue d’ensemble des opérateurs de requête standard (C#)</span><span class="sxs-lookup"><span data-stu-id="06b39-128">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="06b39-129">Types anonymes</span><span class="sxs-lookup"><span data-stu-id="06b39-129">Anonymous Types</span></span>](../../classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="06b39-130">Formulation Join des requêtes s et Cross-Product</span><span class="sxs-lookup"><span data-stu-id="06b39-130">Formulate Joins and Cross-Product Queries</span></span>](../../../../framework/data/adonet/sql/linq/formulate-joins-and-cross-product-queries.md)
- [<span data-ttu-id="06b39-131">join, clause</span><span class="sxs-lookup"><span data-stu-id="06b39-131">join clause</span></span>](../../../language-reference/keywords/join-clause.md)
- [<span data-ttu-id="06b39-132">Joinà l’aide de clés composites</span><span class="sxs-lookup"><span data-stu-id="06b39-132">Join by using composite keys</span></span>](../../../linq/join-by-using-composite-keys.md)
- [<span data-ttu-id="06b39-133">Comment joindre du contenu issu de fichiers différents (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="06b39-133">How to join content from dissimilar files (LINQ) (C#)</span></span>](./how-to-join-content-from-dissimilar-files-linq.md)
- [<span data-ttu-id="06b39-134">Classer les résultats d’une clause join</span><span class="sxs-lookup"><span data-stu-id="06b39-134">Order the results of a join clause</span></span>](../../../linq/order-the-results-of-a-join-clause.md)
- [<span data-ttu-id="06b39-135">Effectuer des opérations de jointure personnalisées</span><span class="sxs-lookup"><span data-stu-id="06b39-135">Perform custom join operations</span></span>](../../../linq/perform-custom-join-operations.md)
- [<span data-ttu-id="06b39-136">Effectuer des jointures groupées</span><span class="sxs-lookup"><span data-stu-id="06b39-136">Perform grouped joins</span></span>](../../../linq/perform-grouped-joins.md)
- [<span data-ttu-id="06b39-137">Effectuer des jointures internes</span><span class="sxs-lookup"><span data-stu-id="06b39-137">Perform inner joins</span></span>](../../../linq/perform-inner-joins.md)
- [<span data-ttu-id="06b39-138">Effectuer des jointures externes gauches</span><span class="sxs-lookup"><span data-stu-id="06b39-138">Perform left outer joins</span></span>](../../../linq/perform-left-outer-joins.md)
- [<span data-ttu-id="06b39-139">Comment remplir des collections d’objets à partir de plusieurs sources (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="06b39-139">How to populate object collections from multiple sources (LINQ) (C#)</span></span>](./how-to-populate-object-collections-from-multiple-sources-linq.md)
