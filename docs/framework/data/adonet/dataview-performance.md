---
title: Performances des DataViews
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 90820e49-9d46-41f6-9a3d-6c0741bbd8eb
ms.openlocfilehash: b2483becce31ab75d8b55b7a642c4ada83da59f6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183349"
---
# <a name="dataview-performance"></a><span data-ttu-id="ef133-102">Performances des DataViews</span><span class="sxs-lookup"><span data-stu-id="ef133-102">DataView Performance</span></span>

<span data-ttu-id="ef133-103">Cette rubrique décrit les avantages en termes de performances de l'utilisation des méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> de la classe <xref:System.Data.DataView>, et de la mise en cache d'un <xref:System.Data.DataView> dans une application Web.</span><span class="sxs-lookup"><span data-stu-id="ef133-103">This topic discusses the performance benefits of using the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView> class, and of caching a <xref:System.Data.DataView> in a Web application.</span></span>  
  
## <a name="find-and-findrows"></a><span data-ttu-id="ef133-104">Find et FindRows</span><span class="sxs-lookup"><span data-stu-id="ef133-104">Find and FindRows</span></span>  

 <span data-ttu-id="ef133-105">Le <xref:System.Data.DataView> construit un index.</span><span class="sxs-lookup"><span data-stu-id="ef133-105"><xref:System.Data.DataView> constructs an index.</span></span> <span data-ttu-id="ef133-106">Il contient des clés créées à partir d'une ou plusieurs colonnes de la table ou de la vue.</span><span class="sxs-lookup"><span data-stu-id="ef133-106">An index contains keys built from one or more columns in the table or view.</span></span> <span data-ttu-id="ef133-107">Ces clés sont stockées dans une structure qui permet au <xref:System.Data.DataView> de trouver rapidement et efficacement la ou les lignes associées aux valeurs de clé.</span><span class="sxs-lookup"><span data-stu-id="ef133-107">These keys are stored in a structure that enables the <xref:System.Data.DataView> to find the row or rows associated with the key values quickly and efficiently.</span></span> <span data-ttu-id="ef133-108">Les opérations qui utilisent l’index, telles que le filtrage et le tri, voient les performances significatives.</span><span class="sxs-lookup"><span data-stu-id="ef133-108">Operations that use the index, such as filtering and sorting, see significant performance increases.</span></span> <span data-ttu-id="ef133-109">L'index d'un <xref:System.Data.DataView> est construit à la fois lors de la création du <xref:System.Data.DataView> et lorsque l'une des informations de tri ou de filtrage est modifiée.</span><span class="sxs-lookup"><span data-stu-id="ef133-109">The index for a <xref:System.Data.DataView> is built both when the <xref:System.Data.DataView> is created and when any of the sorting or filtering information is modified.</span></span> <span data-ttu-id="ef133-110">La création d'un <xref:System.Data.DataView>, suivie de la définition des informations de tri et de filtrage, entraîne la construction de l'index deux fois au moins : une fois lors de la création du <xref:System.Data.DataView>, puis à nouveau lorsqu'une des propriétés de tri ou de filtrage est modifiée.</span><span class="sxs-lookup"><span data-stu-id="ef133-110">Creating a <xref:System.Data.DataView> and then setting the sorting or filtering information later causes the index to be built at least twice: once when the <xref:System.Data.DataView> is created, and again when any of the sort or filter properties are modified.</span></span> <span data-ttu-id="ef133-111">Pour plus d’informations sur le filtrage et le tri avec <xref:System.Data.DataView> , consultez [filtrage avec DataView](filtering-with-dataview-linq-to-dataset.md) et [Tri avec DataView](sorting-with-dataview-linq-to-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ef133-111">For more information about filtering and sorting with <xref:System.Data.DataView>, see [Filtering with DataView](filtering-with-dataview-linq-to-dataset.md) and [Sorting with DataView](sorting-with-dataview-linq-to-dataset.md).</span></span>  
  
 <span data-ttu-id="ef133-112">Si vous souhaitez retourner les résultats d'une requête particulière exécutée sur les données, vous pouvez, au lieu de fournir une vue dynamique d'un sous-ensemble des données, utiliser l'une des méthodes <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> du <xref:System.Data.DataView>, plutôt que de définir la propriété <xref:System.Data.DataView.RowFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef133-112">If you want to return the results of a particular query on the data, as opposed to providing a dynamic view of a subset of the data, you can use the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods of the <xref:System.Data.DataView>, rather than setting the <xref:System.Data.DataView.RowFilter%2A> property.</span></span> <span data-ttu-id="ef133-113">L'utilisation de la propriété <xref:System.Data.DataView.RowFilter%2A> est optimale dans une application de liaison de données où un contrôle lié affiche des résultats filtrés.</span><span class="sxs-lookup"><span data-stu-id="ef133-113">The <xref:System.Data.DataView.RowFilter%2A> property is best used in a data-bound application where a bound control displays filtered results.</span></span> <span data-ttu-id="ef133-114">Le paramétrage de la propriété <xref:System.Data.DataView.RowFilter%2A> entraîne une nouvelle génération de l'index des données, ce qui accroît la charge sur votre application et, par voie de conséquence, fait baisser les performances.</span><span class="sxs-lookup"><span data-stu-id="ef133-114">Setting the <xref:System.Data.DataView.RowFilter%2A> property rebuilds the index for the data, adding overhead to your application and decreasing performance.</span></span> <span data-ttu-id="ef133-115">Les méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> utilisent l'index en cours sans qu'il soit nécessaire de le reconstruire.</span><span class="sxs-lookup"><span data-stu-id="ef133-115">The <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods use the current index without requiring the index to be rebuilt.</span></span> <span data-ttu-id="ef133-116">Si vous ne souhaitez appeler <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> qu'une seule fois, il est préférable d'utiliser le <xref:System.Data.DataView> existant.</span><span class="sxs-lookup"><span data-stu-id="ef133-116">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> only once, then you should use the existing <xref:System.Data.DataView>.</span></span> <span data-ttu-id="ef133-117">Si vous souhaitez appeler <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> plusieurs fois, vous devez créer un nouveau <xref:System.Data.DataView> pour reconstruire l'index sur la colonne où vous voulez effectuer la recherche, pour appeler la méthode <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="ef133-117">If you are going to call <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> multiple times, you should create a new <xref:System.Data.DataView> to rebuild the index on the column you want to search on, and then call the <xref:System.Data.DataView.Find%2A> or <xref:System.Data.DataView.FindRows%2A> methods.</span></span> <span data-ttu-id="ef133-118">Pour plus d’informations sur <xref:System.Data.DataView.Find%2A> les <xref:System.Data.DataView.FindRows%2A> méthodes et, consultez [recherche de lignes](./dataset-datatable-dataview/finding-rows.md).</span><span class="sxs-lookup"><span data-stu-id="ef133-118">For more information about the <xref:System.Data.DataView.Find%2A> and <xref:System.Data.DataView.FindRows%2A> methods, see [Finding Rows](./dataset-datatable-dataview/finding-rows.md).</span></span>  
  
 <span data-ttu-id="ef133-119">L'exemple suivant utilise la méthode <xref:System.Data.DataView.Find%2A> pour rechercher un contact nommé « Zhu ».</span><span class="sxs-lookup"><span data-stu-id="ef133-119">The following example uses the <xref:System.Data.DataView.Find%2A> method to find a contact with the last name "Zhu".</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 <span data-ttu-id="ef133-120">L'exemple suivant utilise la méthode <xref:System.Data.DataView.FindRows%2A> pour rechercher tous les produits de couleur rouge.</span><span class="sxs-lookup"><span data-stu-id="ef133-120">The following example uses the <xref:System.Data.DataView.FindRows%2A> method to find all the red colored products.</span></span>  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a><span data-ttu-id="ef133-121">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ef133-121">ASP.NET</span></span>  

 <span data-ttu-id="ef133-122">ASP.NET dispose d'un mécanisme de mise en cache qui vous permet de stocker en mémoire des objets dont la création mobilise beaucoup de ressources serveur.</span><span class="sxs-lookup"><span data-stu-id="ef133-122">ASP.NET has a caching mechanism that allows you to store objects that require extensive server resources to create in memory.</span></span> <span data-ttu-id="ef133-123">La mise en cache de ces types de ressources peut améliorer considérablement les performances de votre application.</span><span class="sxs-lookup"><span data-stu-id="ef133-123">Caching these types of resources can significantly improve the performance of your application.</span></span> <span data-ttu-id="ef133-124">La mise en cache est implémentée par la classe <xref:System.Web.Caching.Cache>, avec les instances de cache spécifiques à chaque application.</span><span class="sxs-lookup"><span data-stu-id="ef133-124">Caching is implemented by the <xref:System.Web.Caching.Cache> class, with cache instances that are private to each application.</span></span> <span data-ttu-id="ef133-125">Parce que la création d’un nouvel objet <xref:System.Data.DataView> peut consommer beaucoup de ressources, il est préférable d’utiliser cette fonctionnalité de mise en cache dans les applications web pour éviter d’avoir à reconstruire le <xref:System.Data.DataView> à chaque actualisation de la page web.</span><span class="sxs-lookup"><span data-stu-id="ef133-125">Because creating a new <xref:System.Data.DataView> object can be resource intensive, you might want to use this caching functionality in Web applications so that the <xref:System.Data.DataView> does not have to be rebuilt every time the Web page is refreshed.</span></span>  
  
 <span data-ttu-id="ef133-126">Dans l'exemple suivant, le <xref:System.Data.DataView> est mis en cache pour éviter d'avoir à retrier les données à chaque actualisation de la page.</span><span class="sxs-lookup"><span data-stu-id="ef133-126">In the following example, the <xref:System.Data.DataView> is cached so that the data does not have to be re-sorted when the page is refreshed.</span></span>  
  
```vb  
If (Cache("ordersView") = Nothing) Then  
  
Dim dataSet As New DataSet()  
  
   FillDataSet(dataSet)  
  
   Dim orders As DataTable = dataSet.Tables("SalesOrderHeader")  
  
   Dim query = _  
                    From order In orders.AsEnumerable() _  
                    Where order.Field(Of Boolean)("OnlineOrderFlag") = True _  
                    Order By order.Field(Of Decimal)("TotalDue") _  
                    Select order  
  
   Dim view As DataView = query.AsDataView()  
  
   Cache.Insert("ordersView", view)  
  
End If  
  
Dim ordersView = CType(Cache("ordersView"), DataView)  
  
GridView1.DataSource = ordersView  
GridView1.DataBind()  
```  
  
```csharp  
if (Cache["ordersView"] == null)  
{  
   // Fill the DataSet.
   DataSet dataSet = FillDataSet();  
  
   DataTable orders = dataSet.Tables["SalesOrderHeader"];  
  
   EnumerableRowCollection<DataRow> query =  
                        from order in orders.AsEnumerable()  
                        where order.Field<bool>("OnlineOrderFlag") == true  
                        orderby order.Field<decimal>("TotalDue")  
                        select order;  
  
   DataView view = query.AsDataView();  
   Cache.Insert("ordersView", view);  
}  
  
DataView ordersView = (DataView)Cache["ordersView"];  
  
GridView1.DataSource = ordersView;  
GridView1.DataBind();  
```  
  
## <a name="see-also"></a><span data-ttu-id="ef133-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ef133-127">See also</span></span>

- [<span data-ttu-id="ef133-128">Liaison de données et LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="ef133-128">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
