---
title: 'Procédure : Lier un objet DataView à un contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 2b73d60a-6049-446a-85a7-3e5a68b183e2
ms.openlocfilehash: cf2a47c5d29c0af680ee4ccae503e92d3a9124d8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194711"
---
# <a name="how-to-bind-a-dataview-object-to-a-windows-forms-datagridview-control"></a><span data-ttu-id="e176a-102">Procédure : Lier un objet DataView à un contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e176a-102">How to: Bind a DataView Object to a Windows Forms DataGridView Control</span></span>

<span data-ttu-id="e176a-103">Le contrôle <xref:System.Windows.Forms.DataGridView> offre un moyen puissant et flexible d'afficher des données sous forme de tableau.</span><span class="sxs-lookup"><span data-stu-id="e176a-103">The <xref:System.Windows.Forms.DataGridView> control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="e176a-104">Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge le modèle de liaison de données Windows Forms standard ; il peut donc créer une liaison avec <xref:System.Data.DataView> et diverses autres sources de données.</span><span class="sxs-lookup"><span data-stu-id="e176a-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to <xref:System.Data.DataView> and a variety of other data sources.</span></span> <span data-ttu-id="e176a-105">Dans la plupart des cas, toutefois, vous créerez une liaison avec un composant <xref:System.Windows.Forms.BindingSource> qui gérera les détails de l'interaction avec la source de données.</span><span class="sxs-lookup"><span data-stu-id="e176a-105">In most situations, however, you will bind to a <xref:System.Windows.Forms.BindingSource> component that will manage the details of interacting with the data source.</span></span>  
  
 <span data-ttu-id="e176a-106">Pour plus d’informations sur le <xref:System.Windows.Forms.DataGridView> contrôle, consultez [vue d’ensemble du contrôle DataGridView](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).</span><span class="sxs-lookup"><span data-stu-id="e176a-106">For more information about the <xref:System.Windows.Forms.DataGridView> control, see [DataGridView Control Overview](/dotnet/desktop/winforms/controls/datagridview-control-overview-windows-forms).</span></span>  
  
### <a name="to-connect-a-datagridview-control-to-a-dataview"></a><span data-ttu-id="e176a-107">Pour connecter un contrôle DataGridView à un DataView</span><span class="sxs-lookup"><span data-stu-id="e176a-107">To connect a DataGridView control to a DataView</span></span>  
  
1. <span data-ttu-id="e176a-108">Implémentez une méthode pour gérer les détails de la récupération des données d'une base de données.</span><span class="sxs-lookup"><span data-stu-id="e176a-108">Implement a method to handle the details of retrieving data from a database.</span></span> <span data-ttu-id="e176a-109">L'exemple de code suivant implémente une méthode `GetData` qui initialise un composant <xref:System.Data.SqlClient.SqlDataAdapter> et l'utilise pour remplir un <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="e176a-109">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter> component and uses it to fill a <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="e176a-110">Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.</span><span class="sxs-lookup"><span data-stu-id="e176a-110">Be sure to set the `connectionString` variable to a value that is appropriate for your database.</span></span> <span data-ttu-id="e176a-111">Vous devrez accéder à un serveur sur lequel est installé l'exemple de base de données SQL Server AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e176a-111">You will need access to a server with the AdventureWorks SQL Server sample database installed.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1getdata)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1GetData](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1getdata)]  
  
2. <span data-ttu-id="e176a-112">Dans le gestionnaire d'événements <xref:System.Windows.Forms.Form.Load> de votre formulaire, liez le contrôle <xref:System.Windows.Forms.DataGridView> au composant <xref:System.Windows.Forms.BindingSource> et appelez la méthode `GetData` pour récupérer les données de la base de données.</span><span class="sxs-lookup"><span data-stu-id="e176a-112">In the <xref:System.Windows.Forms.Form.Load> event handler of your form, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource> component and call the `GetData` method to retrieve the data from the database.</span></span> <span data-ttu-id="e176a-113">Le <xref:System.Data.DataView> est créé à partir d’une requête de LINQ to DataSet sur le contact <xref:System.Data.DataTable> et est ensuite lié au <xref:System.Windows.Forms.BindingSource> composant.</span><span class="sxs-lookup"><span data-stu-id="e176a-113">The <xref:System.Data.DataView> is created from a LINQ to DataSet query over the Contact <xref:System.Data.DataTable> and is then bound to the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
     [!code-csharp[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/CS/Form1.cs#ldvsample1formload)]
     [!code-vb[DP DataViewWinForms Sample#LDVSample1FormLoad](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataViewWinForms Sample/VB/Form1.vb#ldvsample1formload)]  
  
## <a name="see-also"></a><span data-ttu-id="e176a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e176a-114">See also</span></span>

- [<span data-ttu-id="e176a-115">Liaison de données et LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="e176a-115">Data Binding and LINQ to DataSet</span></span>](data-binding-and-linq-to-dataset.md)
