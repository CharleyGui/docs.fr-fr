---
title: Ajout de DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a4a564fb-c1c4-4135-b6c2-b030e51195e4
ms.openlocfilehash: fde1e2ace09e31234d199876ae7f063e01e7a7e4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203970"
---
# <a name="adding-datarelations"></a><span data-ttu-id="8da22-102">Ajout de DataRelations</span><span class="sxs-lookup"><span data-stu-id="8da22-102">Adding DataRelations</span></span>
<span data-ttu-id="8da22-103">Dans un objet <xref:System.Data.DataSet> contenant plusieurs objets <xref:System.Data.DataTable>, vous pouvez utiliser des objets <xref:System.Data.DataRelation> pour associer une table à une autre, pour vous déplacer dans les tables et pour retourner les lignes enfants ou parentes d'une table associée.</span><span class="sxs-lookup"><span data-stu-id="8da22-103">In a <xref:System.Data.DataSet> with multiple <xref:System.Data.DataTable> objects, you can use <xref:System.Data.DataRelation> objects to relate one table to another, to navigate through the tables, and to return child or parent rows from a related table.</span></span>  
  
 <span data-ttu-id="8da22-104">Les arguments requis pour créer un **DataRelation** sont un nom pour le **DataRelation** créé et un tableau d’une ou plusieurs <xref:System.Data.DataColumn> références aux colonnes qui servent de colonnes parent et enfant dans la relation.</span><span class="sxs-lookup"><span data-stu-id="8da22-104">The arguments required to create a **DataRelation** are a name for the **DataRelation** being created, and an array of one or more <xref:System.Data.DataColumn> references to the columns that serve as the parent and child columns in the relationship.</span></span> <span data-ttu-id="8da22-105">Une fois que vous avez créé un **DataRelation**, vous pouvez l’utiliser pour naviguer entre les tables et récupérer des valeurs.</span><span class="sxs-lookup"><span data-stu-id="8da22-105">After you have created a **DataRelation**, you can use it to navigate between tables and to retrieve values.</span></span>  
  
 <span data-ttu-id="8da22-106">L’ajout d’un DataRelation <xref:System.Data.DataSet> à un ajoute, <xref:System.Data.UniqueConstraint> par défaut, à la table parente <xref:System.Data.ForeignKeyConstraint> et à la table enfant.</span><span class="sxs-lookup"><span data-stu-id="8da22-106">Adding a **DataRelation** to a <xref:System.Data.DataSet> adds, by default, a <xref:System.Data.UniqueConstraint> to the parent table and a <xref:System.Data.ForeignKeyConstraint> to the child table.</span></span> <span data-ttu-id="8da22-107">Pour plus d’informations sur ces contraintes par défaut, consultez [contraintes de DataTable](datatable-constraints.md).</span><span class="sxs-lookup"><span data-stu-id="8da22-107">For more information about these default constraints, see [DataTable Constraints](datatable-constraints.md).</span></span>  
  
 <span data-ttu-id="8da22-108">L’exemple de code suivant crée un **DataRelation** à <xref:System.Data.DataTable> l’aide de <xref:System.Data.DataSet>deux objets dans un.</span><span class="sxs-lookup"><span data-stu-id="8da22-108">The following code example creates a **DataRelation** using two <xref:System.Data.DataTable> objects in a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8da22-109">Chaque <xref:System.Data.DataTable> contient une colonne nommée **CustID**, qui sert de lien entre les deux <xref:System.Data.DataTable> objets.</span><span class="sxs-lookup"><span data-stu-id="8da22-109">Each <xref:System.Data.DataTable> contains a column named **CustID**, which serves as a link between the two <xref:System.Data.DataTable> objects.</span></span> <span data-ttu-id="8da22-110">L’exemple ajoute un seul **DataRelation** à la <xref:System.Data.DataSet>collection relations de.</span><span class="sxs-lookup"><span data-stu-id="8da22-110">The example adds a single **DataRelation** to the **Relations** collection of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="8da22-111">Le premier argument de l’exemple spécifie le nom du **DataRelation** en cours de création.</span><span class="sxs-lookup"><span data-stu-id="8da22-111">The first argument in the example specifies the name of the **DataRelation** being created.</span></span> <span data-ttu-id="8da22-112">Le deuxième argument définit le **DataColumn** parent et le troisième argument définit le **DataColumn**enfant.</span><span class="sxs-lookup"><span data-stu-id="8da22-112">The second argument sets the parent **DataColumn** and the third argument sets the child **DataColumn**.</span></span>  
  
```vb  
customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustID"), _  
  customerOrders.Tables("Orders").Columns("CustID"))  
```  
  
```csharp  
customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustID"],  
  customerOrders.Tables["Orders"].Columns["CustID"]);  
```  
  
 <span data-ttu-id="8da22-113">Un **DataRelation** a également une propriété imbriquée qui, lorsqu’elle est définie sur **true**, fait en sorte que les lignes de la table enfant soient imbriquées dans la ligne associée de la table parente lorsqu' <xref:System.Data.DataSet.WriteXml%2A> elles sont écrites en tant qu’éléments XML à l’aide de.</span><span class="sxs-lookup"><span data-stu-id="8da22-113">A **DataRelation** also has a **Nested** property which, when set to **true**, causes the rows from the child table to be nested within the associated row from the parent table when written as XML elements using <xref:System.Data.DataSet.WriteXml%2A> .</span></span> <span data-ttu-id="8da22-114">Pour plus d’informations, consultez [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="8da22-114">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8da22-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8da22-115">See also</span></span>

- [<span data-ttu-id="8da22-116">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="8da22-116">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="8da22-117">Fournisseurs managés ADO.NET et centre de développement DataSet</span><span class="sxs-lookup"><span data-stu-id="8da22-117">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
