---
title: Interrogation de DataSets (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: bb68d2e4-623d-4d60-85e3-965254f6fee7
ms.openlocfilehash: f42cd792772a4e2b9f24ea8f76ea588da10d9c51
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91184974"
---
# <a name="querying-datasets-linq-to-dataset"></a><span data-ttu-id="1877d-102">Interrogation de DataSets (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="1877d-102">Querying DataSets (LINQ to DataSet)</span></span>

<span data-ttu-id="1877d-103">Une fois qu'un objet <xref:System.Data.DataSet> a été rempli avec des données, vous pouvez commencer de l'interroger.</span><span class="sxs-lookup"><span data-stu-id="1877d-103">After a <xref:System.Data.DataSet> object has been populated with data, you can begin querying it.</span></span> <span data-ttu-id="1877d-104">La formulation de requêtes avec LINQ to DataSet est semblable à l’utilisation de LINQ (Language-Integrated Query) sur d’autres sources de données compatibles LINQ.</span><span class="sxs-lookup"><span data-stu-id="1877d-104">Formulating queries with LINQ to DataSet is similar to using Language-Integrated Query (LINQ) against other LINQ-enabled data sources.</span></span> <span data-ttu-id="1877d-105">Toutefois, n’oubliez pas que lorsque vous utilisez des requêtes LINQ sur un <xref:System.Data.DataSet> objet, vous interrogez une énumération d' <xref:System.Data.DataRow> objets au lieu d’une énumération d’un type personnalisé.</span><span class="sxs-lookup"><span data-stu-id="1877d-105">Remember, however, that when you use LINQ queries over a <xref:System.Data.DataSet> object, you're querying an enumeration of <xref:System.Data.DataRow> objects instead of an enumeration of a custom type.</span></span> <span data-ttu-id="1877d-106">Cela signifie que vous pouvez utiliser n’importe quel membre de la <xref:System.Data.DataRow> classe dans vos requêtes LINQ.</span><span class="sxs-lookup"><span data-stu-id="1877d-106">This means that you can use any of the members of the <xref:System.Data.DataRow> class in your LINQ queries.</span></span> <span data-ttu-id="1877d-107">Cela vous permet de créer des requêtes riches et complexes.</span><span class="sxs-lookup"><span data-stu-id="1877d-107">This lets you create rich, complex queries.</span></span>  
  
 <span data-ttu-id="1877d-108">Comme pour les autres implémentations de LINQ, vous pouvez créer des requêtes LINQ to DataSet dans deux formes différentes : la syntaxe d’expression de requête et la syntaxe de requête fondée sur une méthode.</span><span class="sxs-lookup"><span data-stu-id="1877d-108">As with other implementations of LINQ, you can create LINQ to DataSet queries in two different forms: query expression syntax and method-based query syntax.</span></span> <span data-ttu-id="1877d-109">Vous pouvez utiliser une syntaxe d'expression de requête ou une syntaxe de requête fondée sur une méthode sur des tables uniques d'un <xref:System.Data.DataSet>, sur plusieurs tables sur un <xref:System.Data.DataSet>, ou sur les tables d'un <xref:System.Data.DataSet> typé.</span><span class="sxs-lookup"><span data-stu-id="1877d-109">You can use query expression syntax or method-based query syntax to perform queries against single tables in a <xref:System.Data.DataSet>, against multiple tables in a <xref:System.Data.DataSet>, or against tables in a typed <xref:System.Data.DataSet>.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1877d-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1877d-110">In This Section</span></span>  

 [<span data-ttu-id="1877d-111">Requêtes de table unique</span><span class="sxs-lookup"><span data-stu-id="1877d-111">Single-Table Queries</span></span>](single-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="1877d-112">Explique comment exécuter des requêtes d'analyse unique.</span><span class="sxs-lookup"><span data-stu-id="1877d-112">Describes how to perform single-table queries.</span></span>  
  
 [<span data-ttu-id="1877d-113">Requêtes de table croisée</span><span class="sxs-lookup"><span data-stu-id="1877d-113">Cross-Table Queries</span></span>](cross-table-queries-linq-to-dataset.md)  
 <span data-ttu-id="1877d-114">Explique comment exécuter des requêtes d'analyse croisée.</span><span class="sxs-lookup"><span data-stu-id="1877d-114">Describes how to perform cross-table queries.</span></span>  
  
 [<span data-ttu-id="1877d-115">Interrogation de DataSets typés</span><span class="sxs-lookup"><span data-stu-id="1877d-115">Querying Typed DataSets</span></span>](querying-typed-datasets.md)  
 <span data-ttu-id="1877d-116">Explique comment interroger des objets <xref:System.Data.DataSet> typés.</span><span class="sxs-lookup"><span data-stu-id="1877d-116">Describes how to query typed <xref:System.Data.DataSet> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1877d-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1877d-117">See also</span></span>

- [<span data-ttu-id="1877d-118">Exemples de LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="1877d-118">LINQ to DataSet Examples</span></span>](linq-to-dataset-examples.md)
- [<span data-ttu-id="1877d-119">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="1877d-119">Loading Data Into a DataSet</span></span>](loading-data-into-a-dataset.md)
