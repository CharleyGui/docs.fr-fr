---
title: Comparaison de DataRows (LINQ to DataSet)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8fe0eadf-297b-487c-8d4b-7816753c2883
ms.openlocfilehash: 0903aac366426e8b4d271ae4bfaa54c79a198e5c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583749"
---
# <a name="comparing-datarows-linq-to-dataset"></a><span data-ttu-id="d5b12-102">Comparaison de DataRows (LINQ to DataSet)</span><span class="sxs-lookup"><span data-stu-id="d5b12-102">Comparing DataRows (LINQ to DataSet)</span></span>
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] <span data-ttu-id="d5b12-103">définit divers opérateurs d'ensembles pour comparer des éléments sources afin de vérifier s'ils sont égaux.</span><span class="sxs-lookup"><span data-stu-id="d5b12-103">defines various set operators to compare source elements to see if they are equal.</span></span> [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] <span data-ttu-id="d5b12-104">fournit les opérateurs d'ensembles suivants :</span><span class="sxs-lookup"><span data-stu-id="d5b12-104">provides the following set operators:</span></span>  
  
- <xref:System.Linq.Enumerable.Distinct%2A>  
  
- <xref:System.Linq.Enumerable.Union%2A>  
  
- <xref:System.Linq.Enumerable.Intersect%2A>  
  
- <xref:System.Linq.Enumerable.Except%2A>  
  
 <span data-ttu-id="d5b12-105">Ces opérateurs comparent des éléments de code source en appelant <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> et les méthodes <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> sur chaque collection d'éléments.</span><span class="sxs-lookup"><span data-stu-id="d5b12-105">These operators compare source elements by calling the <xref:System.Collections.Generic.IEqualityComparer%601.GetHashCode%2A> and <xref:System.Collections.Generic.IEqualityComparer%601.Equals%2A> methods on each collection of elements.</span></span> <span data-ttu-id="d5b12-106">Dans le cas d'un <xref:System.Data.DataRow>, ces opérateurs effectuent une comparaison de référence, ce qui n'est généralement pas le comportement idéal pour des opérations de jeu sur des données de tableau.</span><span class="sxs-lookup"><span data-stu-id="d5b12-106">In the case of a <xref:System.Data.DataRow>, these operators perform a reference comparison, which is generally not the ideal behavior for set operations over tabular data.</span></span> <span data-ttu-id="d5b12-107">Pour les opérations de jeu, il vous faut en général déterminer si les valeurs de l'élément sont égales, et pas les références d'élément.</span><span class="sxs-lookup"><span data-stu-id="d5b12-107">For set operations, you usually want to determine whether the element values are equal and not the element references.</span></span> <span data-ttu-id="d5b12-108">Par conséquent, la classe <xref:System.Data.DataRowComparer> a été ajoutée à [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d5b12-108">Therefore, the <xref:System.Data.DataRowComparer> class has been added to [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)].</span></span> <span data-ttu-id="d5b12-109">Cette classe peut être utilisée pour comparer des valeurs de ligne.</span><span class="sxs-lookup"><span data-stu-id="d5b12-109">This class can be used to compare row values.</span></span>  
  
 <span data-ttu-id="d5b12-110">La classe <xref:System.Data.DataRowComparer> contient une implémentation de comparaison de valeur pour <xref:System.Data.DataRow>, ce qui fait qu'elle peut être utilisée pour des opérations de jeu telles que <xref:System.Linq.Enumerable.Distinct%2A>.</span><span class="sxs-lookup"><span data-stu-id="d5b12-110">The <xref:System.Data.DataRowComparer> class contains a value comparison implementation for <xref:System.Data.DataRow>, so this class can be used for set operations such as <xref:System.Linq.Enumerable.Distinct%2A>.</span></span> <span data-ttu-id="d5b12-111">Cette classe ne peut pas être instanciée directement ; vous devez utiliser à la place la propriété <xref:System.Data.DataRowComparer.Default%2A> pour retourner une instance du <xref:System.Data.DataRowComparer%601>.</span><span class="sxs-lookup"><span data-stu-id="d5b12-111">This class cannot be directly instantiated; instead, the <xref:System.Data.DataRowComparer.Default%2A> property must be used to return an instance of the <xref:System.Data.DataRowComparer%601>.</span></span> <span data-ttu-id="d5b12-112">La méthode <xref:System.Data.DataRowComparer%601.Equals%2A> est ensuite appelée et les deux objets <xref:System.Data.DataRow> à comparer sont passés en tant que paramètres d'entrée.</span><span class="sxs-lookup"><span data-stu-id="d5b12-112">The <xref:System.Data.DataRowComparer%601.Equals%2A> method is then called and the two <xref:System.Data.DataRow> objects to be compared are passed in as input parameters.</span></span> <span data-ttu-id="d5b12-113">La méthode <xref:System.Data.DataRowComparer%601.Equals%2A> retourne `true` si le jeu trié de valeurs de colonne dans les deux objets <xref:System.Data.DataRow> comporte des valeurs égales ; sinon `false`.</span><span class="sxs-lookup"><span data-stu-id="d5b12-113">The <xref:System.Data.DataRowComparer%601.Equals%2A> method returns `true` if the ordered set of column values in both <xref:System.Data.DataRow> objects are equal; otherwise, `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5b12-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5b12-114">Example</span></span>  
 <span data-ttu-id="d5b12-115">Cet exemple utilise la méthode `Intersect` pour retourner les contacts qui apparaissent dans les deux tables.</span><span class="sxs-lookup"><span data-stu-id="d5b12-115">This example uses `Intersect` to return contacts that appear in both tables.</span></span>  
  
 [!code-csharp[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#intersect2)]
 [!code-vb[DP LINQ to DataSet Examples#Intersect2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#intersect2)]  
  
### <a name="example"></a><span data-ttu-id="d5b12-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d5b12-116">Example</span></span>  
 <span data-ttu-id="d5b12-117">L'exemple suivant compare deux lignes et obtient les codes de hachage.</span><span class="sxs-lookup"><span data-stu-id="d5b12-117">The following example compares two rows and gets their hash codes.</span></span>  
  
 [!code-vb[DP LINQ to DataSet Examples#CompareDifferentRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#comparedifferentrows)]  
  
## <a name="see-also"></a><span data-ttu-id="d5b12-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d5b12-118">See also</span></span>

- <xref:System.Data.DataRowComparer>
- [<span data-ttu-id="d5b12-119">Chargement de données dans un DataSet</span><span class="sxs-lookup"><span data-stu-id="d5b12-119">Loading Data Into a DataSet</span></span>](../../../../docs/framework/data/adonet/loading-data-into-a-dataset.md)
- [<span data-ttu-id="d5b12-120">Exemples LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="d5b12-120">LINQ to DataSet Examples</span></span>](../../../../docs/framework/data/adonet/linq-to-dataset-examples.md)
