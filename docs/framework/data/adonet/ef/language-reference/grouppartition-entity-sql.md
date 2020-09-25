---
title: GROUPPARTITION (Entity SQL)
ms.date: 03/30/2017
ms.assetid: d0482e9b-086c-451c-9dfa-ccb024a9efb6
ms.openlocfilehash: 11abebeac682fed9e3a007986bb2f5c7bdb80f16
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204474"
---
# <a name="grouppartition-entity-sql"></a><span data-ttu-id="b6538-102">GROUPPARTITION (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b6538-102">GROUPPARTITION (Entity SQL)</span></span>

<span data-ttu-id="b6538-103">Retourne une collection de valeurs d'argument projetées en dehors de la partition de groupe actuelle à laquelle l'agrégat est associé.</span><span class="sxs-lookup"><span data-stu-id="b6538-103">Returns a collection of argument values that are projected off the current group partition to which the aggregate is related.</span></span> <span data-ttu-id="b6538-104">L'agrégat `GroupPartition` est un agrégat basé sur les groupes et n'a aucune forme basée sur les collections.</span><span class="sxs-lookup"><span data-stu-id="b6538-104">The `GroupPartition` aggregate is a group-based aggregate and has no collection-based form.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6538-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6538-105">Syntax</span></span>  
  
```sql  
GROUPPARTITION( [ALL|DISTINCT] expression )  
```  
  
## <a name="arguments"></a><span data-ttu-id="b6538-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="b6538-106">Arguments</span></span>  

 `expression`  
 <span data-ttu-id="b6538-107">Toute expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="b6538-107">Any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6538-108">Notes</span><span class="sxs-lookup"><span data-stu-id="b6538-108">Remarks</span></span>  

 <span data-ttu-id="b6538-109">La requête suivante produit une liste de produits et une collection de quantités de ligne de commande pour chaque produit :</span><span class="sxs-lookup"><span data-stu-id="b6538-109">The following query produces a list of products and a collection of order line quantities per each product:</span></span>  
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="b6538-110">Les deux requêtes suivantes sont sémantiquement égales :</span><span class="sxs-lookup"><span data-stu-id="b6538-110">The following two queries are semantically equal:</span></span>  
  
```sql  
SELECT p, Sum(GroupPartition(ol.Quantity)) FROM LOB.OrderLines AS ol
  GROUP BY ol.Product AS p
SELET p, Sum(ol.Quantity) FROM LOB.OrderLines AS ol
  group by ol.Product as p  
```  
  
 <span data-ttu-id="b6538-111">L'opérateur `GROUPPARTITION` peut être utilisé conjointement à des fonctions d'agrégation définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b6538-111">The `GROUPPARTITION` operator can be used in conjunction with user-defined aggregate functions.</span></span>  
  
<span data-ttu-id="b6538-112">`GROUPPARTITION` est un opérateur d'agrégation spécial qui maintient une référence au jeu de données d'entrée groupé.</span><span class="sxs-lookup"><span data-stu-id="b6538-112">`GROUPPARTITION` is a special aggregate operator that holds a reference to the grouped input set.</span></span> <span data-ttu-id="b6538-113">Cette référence peut être utilisée n'importe où dans la requête où GROUP BY est dans la portée.</span><span class="sxs-lookup"><span data-stu-id="b6538-113">This reference can be used anywhere in the query where GROUP BY is in scope.</span></span> <span data-ttu-id="b6538-114">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="b6538-114">For example:</span></span>
  
```sql  
SELECT p, GroupPartition(ol.Quantity) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="b6538-115">Avec un régulier `GROUP BY` , les résultats du regroupement sont masqués.</span><span class="sxs-lookup"><span data-stu-id="b6538-115">With a regular `GROUP BY`, the results of the grouping are hidden.</span></span> <span data-ttu-id="b6538-116">Vous pouvez utiliser les résultats uniquement dans une fonction d'agrégation.</span><span class="sxs-lookup"><span data-stu-id="b6538-116">You can only use the results in an aggregate function.</span></span> <span data-ttu-id="b6538-117">Pour voir les résultats du regroupement, vous devez mettre en corrélation les résultats du regroupement et le jeu de données d'entrée à l'aide d'une sous-requête.</span><span class="sxs-lookup"><span data-stu-id="b6538-117">In order to see the results of the grouping, you have to correlate the results of the grouping and the input set by using a subquery.</span></span> <span data-ttu-id="b6538-118">Les deux requêtes suivantes sont équivalentes :</span><span class="sxs-lookup"><span data-stu-id="b6538-118">The following two queries are equivalent:</span></span>  
  
```sql  
SELET p, (SELECT q FROM GroupPartition(ol.Quantity) AS q) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
SELECT p, (SELECT ol.Quantity AS q FROM LOB.OrderLines AS ol2 WHERE ol2.Product = p) FROM LOB.OrderLines AS ol GROUP BY ol.Product AS p
```  
  
 <span data-ttu-id="b6538-119">Comme le montre l'exemple, l'opérateur d'agrégation GROUPPARTITION simplifie l'obtention d'une référence au jeu de données d'entrée après le regroupement.</span><span class="sxs-lookup"><span data-stu-id="b6538-119">As seen from the example, the GROUPPARTITION aggregate operator makes it easier to get a reference to the input set after the grouping.</span></span>  
  
 <span data-ttu-id="b6538-120">L'opérateur GROUPPARTITION peut spécifier toute expression [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dans l'entrée de l'opérateur lorsque vous utilisez le paramètre `expression` .</span><span class="sxs-lookup"><span data-stu-id="b6538-120">The GROUPPARTITION operator can specify any [!INCLUDE[esql](../../../../../../includes/esql-md.md)] expression in the operator input when you use the `expression` parameter.</span></span>  
  
 <span data-ttu-id="b6538-121">Par exemple, toutes les expressions d'entrée suivantes de la partition de groupe sont valides :</span><span class="sxs-lookup"><span data-stu-id="b6538-121">For instance all of the following input expressions to the group partition are valid:</span></span>  
  
```sql  
SELECT groupkey, GroupPartition(b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(1) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition(a + b) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey
SELECT groupkey, GroupPartition({a + b}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition({42}) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
SELECT groupkey, GroupPartition(b > a) FROM {1,2,3} AS a INNER JOIN {4,5,6} AS b ON true GROUP BY a AS groupkey  
```  
  
## <a name="example"></a><span data-ttu-id="b6538-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="b6538-122">Example</span></span>  

 <span data-ttu-id="b6538-123">L'exemple ci-dessous montre comment utiliser la clause GROUPPARTITION avec la clause GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="b6538-123">The following example shows how to use the GROUPPARTITION clause with the GROUP BY clause.</span></span> <span data-ttu-id="b6538-124">La clause GROUP BY regroupe les entités `SalesOrderHeader` par leur élément `Contact`.</span><span class="sxs-lookup"><span data-stu-id="b6538-124">The GROUP BY clause groups `SalesOrderHeader` entities by their `Contact`.</span></span> <span data-ttu-id="b6538-125">La clause GROUPPARTITION projette alors la propriété `TotalDue` pour chaque groupe, ce qui génère une collection de valeurs décimales.</span><span class="sxs-lookup"><span data-stu-id="b6538-125">The GROUPPARTITION clause then projects the `TotalDue` property for each group, resulting in a collection of decimals.</span></span>  
  
 [!code-sql[DP EntityServices Concepts#Collection_GroupPartition](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#collection_grouppartition)]
