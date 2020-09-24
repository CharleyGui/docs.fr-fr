---
title: Parcours des DataRelations
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: 5eb2ee16712be5ccd5e9aa0af4dde22dcaaeea09
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91148384"
---
# <a name="navigating-datarelations"></a><span data-ttu-id="772a9-102">Parcours des DataRelations</span><span class="sxs-lookup"><span data-stu-id="772a9-102">Navigating DataRelations</span></span>

<span data-ttu-id="772a9-103">L'une des principales fonctions d'un objet <xref:System.Data.DataRelation> est de permettre de passer d'un objet <xref:System.Data.DataTable> à un autre à l'intérieur d'un objet <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="772a9-103">One of the primary functions of a <xref:System.Data.DataRelation> is to allow navigation from one <xref:System.Data.DataTable> to another within a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="772a9-104">Cela vous permet de récupérer tous les <xref:System.Data.DataRow> objets connexes dans un **DataTable** lorsqu’un **DataRow** unique est donné à partir d’un **DataTable**associé.</span><span class="sxs-lookup"><span data-stu-id="772a9-104">This allows you to retrieve all the related <xref:System.Data.DataRow> objects in one **DataTable** when given a single **DataRow** from a related **DataTable**.</span></span> <span data-ttu-id="772a9-105">Par exemple, après avoir établi un **DataRelation** entre une table de clients et une table de commandes, vous pouvez récupérer toutes les lignes de commande pour une ligne de client particulière à l’aide de **GetChildRows**.</span><span class="sxs-lookup"><span data-stu-id="772a9-105">For example, after establishing a **DataRelation** between a table of customers and a table of orders, you can retrieve all the order rows for a particular customer row using **GetChildRows**.</span></span>  
  
 <span data-ttu-id="772a9-106">L’exemple de code suivant crée un **DataRelation** entre la table **Customers** et la table **Orders** d’un **DataSet** et retourne toutes les commandes pour chaque client.</span><span class="sxs-lookup"><span data-stu-id="772a9-106">The following code example creates a **DataRelation** between the **Customers** table and the **Orders** table of a **DataSet** and returns all the orders for each customer.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 <span data-ttu-id="772a9-107">L'exemple suivant s'appuie sur le précédent, en créant des relations entre quatre tables et en explorant ces relations.</span><span class="sxs-lookup"><span data-stu-id="772a9-107">The next example builds on the preceding example, relating four tables together and navigating those relationships.</span></span> <span data-ttu-id="772a9-108">Comme dans l’exemple précédent, **CustomerID** lie la table **Customers** à la table **Orders** .</span><span class="sxs-lookup"><span data-stu-id="772a9-108">As in the previous example, **CustomerID** relates the **Customers** table to the **Orders** table.</span></span> <span data-ttu-id="772a9-109">Pour chaque client de la table **Customers** , toutes les lignes enfants de la table **Orders** sont déterminées, afin de retourner le nombre de commandes d’un client particulier et leurs valeurs **OrderID** .</span><span class="sxs-lookup"><span data-stu-id="772a9-109">For each customer in the **Customers** table, all the child rows in the **Orders** table are determined, in order to return the number of orders a particular customer has and their **OrderID** values.</span></span>  
  
 <span data-ttu-id="772a9-110">L’exemple développé retourne également les valeurs des tables **OrderDetails** et **Products** .</span><span class="sxs-lookup"><span data-stu-id="772a9-110">The expanded example also returns the values from the **OrderDetails** and **Products** tables.</span></span> <span data-ttu-id="772a9-111">La table **Orders** est associée à la table **OrderDetails** avec **OrderID** pour déterminer, pour chaque commande client, les produits et quantités commandés.</span><span class="sxs-lookup"><span data-stu-id="772a9-111">The **Orders** table is related to the **OrderDetails** table using **OrderID** to determine, for each customer order, what products and quantities were ordered.</span></span> <span data-ttu-id="772a9-112">Étant donné que la table **OrderDetails** contient uniquement le **ProductID** d’un produit commandé, **OrderDetails** est lié à **Products** à l’aide de **ProductID** afin de retourner le **ProductName**.</span><span class="sxs-lookup"><span data-stu-id="772a9-112">Because the **OrderDetails** table only contains the **ProductID** of an ordered product, **OrderDetails** is related to **Products** using **ProductID** in order to return the **ProductName**.</span></span> <span data-ttu-id="772a9-113">Dans cette relation, la table **Products** est le parent et la table **Order Details** est l’enfant.</span><span class="sxs-lookup"><span data-stu-id="772a9-113">In this relation, the **Products** table is the parent and the **Order Details** table is the child.</span></span> <span data-ttu-id="772a9-114">Par conséquent, lors de l’itération au sein de la table **OrderDetails** , **GetParentRow** est appelé pour extraire la valeur **ProductName** associée.</span><span class="sxs-lookup"><span data-stu-id="772a9-114">As a result, when iterating through the **OrderDetails** table, **GetParentRow** is called to retrieve the related **ProductName** value.</span></span>  
  
 <span data-ttu-id="772a9-115">Notez que lorsque le **DataRelation** est créé pour les tables **Customers** et **Orders** , aucune valeur n’est spécifiée pour l’indicateur **createConstraints** (la valeur par défaut est **true**).</span><span class="sxs-lookup"><span data-stu-id="772a9-115">Notice that when the **DataRelation** is created for the **Customers** and **Orders** tables, no value is specified for the **createConstraints** flag (the default is **true**).</span></span> <span data-ttu-id="772a9-116">Cela suppose que toutes les lignes de la table **Orders** ont une valeur **CustomerID** qui existe dans la table **Customers** parent.</span><span class="sxs-lookup"><span data-stu-id="772a9-116">This assumes that all the rows in the **Orders** table have a **CustomerID** value that exists in the parent **Customers** table.</span></span> <span data-ttu-id="772a9-117">Si un **CustomerID** existe dans la table **Orders** et qu’il n’existe pas dans la table **Customers** , une <xref:System.Data.ForeignKeyConstraint> exception est levée.</span><span class="sxs-lookup"><span data-stu-id="772a9-117">If a **CustomerID** exists in the **Orders** table that does not exist in the **Customers** table, a <xref:System.Data.ForeignKeyConstraint> causes an exception to be thrown.</span></span>  
  
 <span data-ttu-id="772a9-118">Lorsque la colonne enfant peut contenir des valeurs qui ne sont pas contenues dans la colonne parente, affectez la valeur **false** à l’indicateur **createConstraints** lors de l’ajout du **DataRelation**.</span><span class="sxs-lookup"><span data-stu-id="772a9-118">When the child column might contain values that the parent column does not contain, set the **createConstraints** flag to **false** when adding the **DataRelation**.</span></span> <span data-ttu-id="772a9-119">Dans l’exemple, l’indicateur **createConstraints** est défini sur **false** pour le **DataRelation** entre la table **Orders** et la table **OrderDetails** .</span><span class="sxs-lookup"><span data-stu-id="772a9-119">In the example, the **createConstraints** flag is set to **false** for the **DataRelation** between the **Orders** table and the **OrderDetails** table.</span></span> <span data-ttu-id="772a9-120">Cela permet à l’application de retourner tous les enregistrements de la table **OrderDetails** et uniquement un sous-ensemble d’enregistrements de la table **Orders** sans générer d’exception Runtime.</span><span class="sxs-lookup"><span data-stu-id="772a9-120">This enables the application to return all the records from the **OrderDetails** table and only a subset of records from the **Orders** table without generating a run-time exception.</span></span> <span data-ttu-id="772a9-121">La sortie de l’exemple développé se présente comme suit.</span><span class="sxs-lookup"><span data-stu-id="772a9-121">The expanded sample generates output in the following format.</span></span>  
  
```output  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 <span data-ttu-id="772a9-122">L’exemple de code suivant est un exemple développé où les valeurs des tables **OrderDetails** et **Products** sont retournées, avec seulement un sous-ensemble des enregistrements de la table **Orders** en cours de retour.</span><span class="sxs-lookup"><span data-stu-id="772a9-122">The following code example is an expanded sample where the values from the **OrderDetails** and **Products** tables are returned, with only a subset of the records in the **Orders** table being returned.</span></span>  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="772a9-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="772a9-123">See also</span></span>

- [<span data-ttu-id="772a9-124">DataSets, DataTables et DataViews</span><span class="sxs-lookup"><span data-stu-id="772a9-124">DataSets, DataTables, and DataViews</span></span>](index.md)
- [<span data-ttu-id="772a9-125">Vue d'ensemble d’ADO.NET</span><span class="sxs-lookup"><span data-stu-id="772a9-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
