---
title: Lier des données au contrôle DataGridView
ms.date: 02/08/2019
description: Découvrez comment le contrôle DataGridView prend en charge le modèle de liaison de données standard Windows Forms afin qu’il puisse être lié à une variété de sources de données.
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [Windows Forms], grids
- data binding [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 1660f69c-5711-45d2-abc1-e25bc6779124
ms.openlocfilehash: 3c3502804d1bc4a5eeffc22b4ec5f2773411ef69
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904414"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control"></a><span data-ttu-id="9f12d-103">Comment : lier des données au contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f12d-103">How to: Bind data to the Windows Forms DataGridView control</span></span>

<span data-ttu-id="9f12d-104">Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge le modèle de liaison de données standard Windows Forms, afin qu’il puisse être lié à une variété de sources de données.</span><span class="sxs-lookup"><span data-stu-id="9f12d-104">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it can bind to a variety of data sources.</span></span> <span data-ttu-id="9f12d-105">En général, vous liez à un <xref:System.Windows.Forms.BindingSource> qui gère l’interaction avec la source de données.</span><span class="sxs-lookup"><span data-stu-id="9f12d-105">Usually, you bind to a <xref:System.Windows.Forms.BindingSource> that manages the interaction with the data source.</span></span> <span data-ttu-id="9f12d-106"><xref:System.Windows.Forms.BindingSource>Peut être n’importe quelle Windows Forms source de données, ce qui vous offre une grande souplesse lors du choix ou de la modification de l’emplacement de vos données.</span><span class="sxs-lookup"><span data-stu-id="9f12d-106">The <xref:System.Windows.Forms.BindingSource> can be any Windows Forms data source, which gives you great flexibility when choosing or modifying your data's location.</span></span> <span data-ttu-id="9f12d-107">Pour plus d’informations sur les sources de données <xref:System.Windows.Forms.DataGridView> prises en charge par le contrôle, consultez [vue d’ensemble du contrôle DataGridView](datagridview-control-overview-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="9f12d-107">For more information about data sources the <xref:System.Windows.Forms.DataGridView> control supports, see the [DataGridView control overview](datagridview-control-overview-windows-forms.md).</span></span>  

<span data-ttu-id="9f12d-108">Visual Studio prend en charge la liaison de données au contrôle DataGridView.</span><span class="sxs-lookup"><span data-stu-id="9f12d-108">Visual Studio has extensive support for data binding to the DataGridView control.</span></span> <span data-ttu-id="9f12d-109">Pour plus d’informations, consultez [Comment : lier des données au contrôle DataGridView Windows Forms à l’aide du concepteur](bind-data-to-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="9f12d-109">For more information, see [How to: Bind data to the Windows Forms DataGridView control using the Designer](bind-data-to-the-datagrid-using-the-designer.md).</span></span>  

<span data-ttu-id="9f12d-110">Pour connecter un contrôle DataGridView à des données :</span><span class="sxs-lookup"><span data-stu-id="9f12d-110">To connect a DataGridView control to data:</span></span>

1. <span data-ttu-id="9f12d-111">Implémentez une méthode pour gérer les détails de la récupération des données.</span><span class="sxs-lookup"><span data-stu-id="9f12d-111">Implement a method to handle the details of retrieving the data.</span></span> <span data-ttu-id="9f12d-112">L’exemple de code suivant implémente une `GetData` méthode qui initialise un <xref:System.Data.SqlClient.SqlDataAdapter> et l’utilise pour remplir un <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="9f12d-112">The following code example implements a `GetData` method that initializes a <xref:System.Data.SqlClient.SqlDataAdapter>, and uses it to populate a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="9f12d-113">Il lie ensuite le <xref:System.Data.DataTable> à <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="9f12d-113">It then binds the <xref:System.Data.DataTable> to the <xref:System.Windows.Forms.BindingSource>.</span></span>

2. <span data-ttu-id="9f12d-114">Dans le gestionnaire d' <xref:System.Windows.Forms.Form.Load> événements du formulaire, liez le <xref:System.Windows.Forms.DataGridView> contrôle à <xref:System.Windows.Forms.BindingSource> et appelez la `GetData` méthode pour récupérer les données.</span><span class="sxs-lookup"><span data-stu-id="9f12d-114">In the form's <xref:System.Windows.Forms.Form.Load> event handler, bind the <xref:System.Windows.Forms.DataGridView> control to the <xref:System.Windows.Forms.BindingSource>, and call the `GetData` method to retrieve the data.</span></span>  

## <a name="example"></a><span data-ttu-id="9f12d-115">Exemple</span><span class="sxs-lookup"><span data-stu-id="9f12d-115">Example</span></span>

<span data-ttu-id="9f12d-116">Cet exemple de code complet récupère les données d’une base de données pour remplir un contrôle DataGridView dans un Windows Form.</span><span class="sxs-lookup"><span data-stu-id="9f12d-116">This complete code example retrieves data from a database to populate a DataGridView control in a Windows form.</span></span> <span data-ttu-id="9f12d-117">Le formulaire contient également des boutons permettant de recharger les données et de soumettre les modifications à la base de données.</span><span class="sxs-lookup"><span data-stu-id="9f12d-117">The form also has buttons to reload data and submit changes to the database.</span></span>  

<span data-ttu-id="9f12d-118">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="9f12d-118">This example requires:</span></span>

- <span data-ttu-id="9f12d-119">Accès à un exemple de base de données Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9f12d-119">Access to a Northwind SQL Server sample database.</span></span> <span data-ttu-id="9f12d-120">Pour plus d’informations sur l’installation de l’exemple de base de données Northwind, consultez [obtenir les exemples de bases de données pour les exemples de code ADO.net](../../data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="9f12d-120">For more information about installing the Northwind sample database, see [Get the sample databases for ADO.NET code samples](../../data/adonet/sql/linq/downloading-sample-databases.md).</span></span>

- <span data-ttu-id="9f12d-121">Références aux assemblys System, System. Windows. Forms, System. Data et System.Xml.</span><span class="sxs-lookup"><span data-stu-id="9f12d-121">References to the System, System.Windows.Forms, System.Data, and System.Xml assemblies.</span></span>  

<span data-ttu-id="9f12d-122">Pour générer et exécuter cet exemple, collez le code dans le fichier de code *Form1* dans un nouveau projet de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="9f12d-122">To build and run this example, paste the code into the *Form1* code file in a new Windows Forms project.</span></span> <span data-ttu-id="9f12d-123">Pour plus d’informations sur la génération à partir de la ligne de commande C# ou Visual Basic, consultez génération à partir de la [ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) ou [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="9f12d-123">For information about building from the C# or Visual Basic command line, see [Command-line building with csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) or [Build from the command line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
<span data-ttu-id="9f12d-124">Renseignez la `connectionString` variable dans l’exemple avec les valeurs de votre connexion Northwind SQL Server exemple de connexion à la base de données.</span><span class="sxs-lookup"><span data-stu-id="9f12d-124">Populate the `connectionString` variable in the example with the values for your Northwind SQL Server sample database connection.</span></span> <span data-ttu-id="9f12d-125">L’authentification Windows, également appelée sécurité intégrée, est un moyen plus sûr de se connecter à la base de données que de stocker un mot de passe dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="9f12d-125">Windows Authentication, also called integrated security, is a more secure way to connect to the database than storing a password in the connection string.</span></span> <span data-ttu-id="9f12d-126">Pour plus d’informations sur la sécurité des connexions, consultez [protéger les informations de connexion](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="9f12d-126">For more information about connection security, see [Protect connection information](../../data/adonet/protecting-connection-information.md).</span></span>  

[!code-csharp[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/CS/datagridviewboundeditable.cs)]
[!code-vb[System.Windows.Forms.DataGridViewBoundEditable](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewBoundEditable/VB/datagridviewboundeditable.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9f12d-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9f12d-127">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="9f12d-128">Afficher des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f12d-128">Display data in the Windows Forms DataGridView control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="9f12d-129">Protéger les informations de connexion</span><span class="sxs-lookup"><span data-stu-id="9f12d-129">Protect connection information</span></span>](../../data/adonet/protecting-connection-information.md)
