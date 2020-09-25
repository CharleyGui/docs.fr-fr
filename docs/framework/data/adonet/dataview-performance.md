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
# <a name="dataview-performance"></a>Performances des DataViews

Cette rubrique décrit les avantages en termes de performances de l'utilisation des méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> de la classe <xref:System.Data.DataView>, et de la mise en cache d'un <xref:System.Data.DataView> dans une application Web.  
  
## <a name="find-and-findrows"></a>Find et FindRows  

 Le <xref:System.Data.DataView> construit un index. Il contient des clés créées à partir d'une ou plusieurs colonnes de la table ou de la vue. Ces clés sont stockées dans une structure qui permet au <xref:System.Data.DataView> de trouver rapidement et efficacement la ou les lignes associées aux valeurs de clé. Les opérations qui utilisent l’index, telles que le filtrage et le tri, voient les performances significatives. L'index d'un <xref:System.Data.DataView> est construit à la fois lors de la création du <xref:System.Data.DataView> et lorsque l'une des informations de tri ou de filtrage est modifiée. La création d'un <xref:System.Data.DataView>, suivie de la définition des informations de tri et de filtrage, entraîne la construction de l'index deux fois au moins : une fois lors de la création du <xref:System.Data.DataView>, puis à nouveau lorsqu'une des propriétés de tri ou de filtrage est modifiée. Pour plus d’informations sur le filtrage et le tri avec <xref:System.Data.DataView> , consultez [filtrage avec DataView](filtering-with-dataview-linq-to-dataset.md) et [Tri avec DataView](sorting-with-dataview-linq-to-dataset.md).  
  
 Si vous souhaitez retourner les résultats d'une requête particulière exécutée sur les données, vous pouvez, au lieu de fournir une vue dynamique d'un sous-ensemble des données, utiliser l'une des méthodes <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> du <xref:System.Data.DataView>, plutôt que de définir la propriété <xref:System.Data.DataView.RowFilter%2A>. L'utilisation de la propriété <xref:System.Data.DataView.RowFilter%2A> est optimale dans une application de liaison de données où un contrôle lié affiche des résultats filtrés. Le paramétrage de la propriété <xref:System.Data.DataView.RowFilter%2A> entraîne une nouvelle génération de l'index des données, ce qui accroît la charge sur votre application et, par voie de conséquence, fait baisser les performances. Les méthodes <xref:System.Data.DataView.Find%2A> et <xref:System.Data.DataView.FindRows%2A> utilisent l'index en cours sans qu'il soit nécessaire de le reconstruire. Si vous ne souhaitez appeler <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> qu'une seule fois, il est préférable d'utiliser le <xref:System.Data.DataView> existant. Si vous souhaitez appeler <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A> plusieurs fois, vous devez créer un nouveau <xref:System.Data.DataView> pour reconstruire l'index sur la colonne où vous voulez effectuer la recherche, pour appeler la méthode <xref:System.Data.DataView.Find%2A> ou <xref:System.Data.DataView.FindRows%2A>. Pour plus d’informations sur <xref:System.Data.DataView.Find%2A> les <xref:System.Data.DataView.FindRows%2A> méthodes et, consultez [recherche de lignes](./dataset-datatable-dataview/finding-rows.md).  
  
 L'exemple suivant utilise la méthode <xref:System.Data.DataView.Find%2A> pour rechercher un contact nommé « Zhu ».  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryorderbyfind)]
 [!code-vb[DP DataView Samples#LDVFromQueryOrderByFind](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryorderbyfind)]  
  
 L'exemple suivant utilise la méthode <xref:System.Data.DataView.FindRows%2A> pour rechercher tous les produits de couleur rouge.  
  
 [!code-csharp[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#ldvfromqueryfindrows)]
 [!code-vb[DP DataView Samples#LDVFromQueryFindRows](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#ldvfromqueryfindrows)]  
  
## <a name="aspnet"></a>ASP.NET  

 ASP.NET dispose d'un mécanisme de mise en cache qui vous permet de stocker en mémoire des objets dont la création mobilise beaucoup de ressources serveur. La mise en cache de ces types de ressources peut améliorer considérablement les performances de votre application. La mise en cache est implémentée par la classe <xref:System.Web.Caching.Cache>, avec les instances de cache spécifiques à chaque application. Parce que la création d’un nouvel objet <xref:System.Data.DataView> peut consommer beaucoup de ressources, il est préférable d’utiliser cette fonctionnalité de mise en cache dans les applications web pour éviter d’avoir à reconstruire le <xref:System.Data.DataView> à chaque actualisation de la page web.  
  
 Dans l'exemple suivant, le <xref:System.Data.DataView> est mis en cache pour éviter d'avoir à retrier les données à chaque actualisation de la page.  
  
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
  
## <a name="see-also"></a>Voir aussi

- [Liaison de données et LINQ to DataSet](data-binding-and-linq-to-dataset.md)
