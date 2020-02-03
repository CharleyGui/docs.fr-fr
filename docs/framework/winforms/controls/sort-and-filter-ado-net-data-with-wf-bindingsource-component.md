---
title: Trier et filtrer les données ADO.NET avec le composant BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data
- data sorting [Windows Forms], ADO.NET
- data [Windows Forms], filtering
- BindingSource component [Windows Forms], sorting and filtering data
- filtering [Windows Forms], ADO.NET
- data [Windows Forms], sorting
- ADO.NET [Windows Forms]
ms.assetid: 6c206daf-d706-4602-9dbe-435343052063
ms.openlocfilehash: cf1da3bb94b26449eb72b0e4930b262236487acc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742976"
---
# <a name="how-to-sort-and-filter-adonet-data-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="30e5f-102">Comment : trier et filtrer des données ADO.NET avec le composant BindingSource Windows Forms</span><span class="sxs-lookup"><span data-stu-id="30e5f-102">How to: Sort and Filter ADO.NET Data with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="30e5f-103">Vous pouvez exposer la fonctionnalité de tri et de filtrage de <xref:System.Windows.Forms.BindingSource> contrôle via les propriétés <xref:System.Windows.Forms.BindingSource.Sort%2A> et <xref:System.Windows.Forms.BindingSource.Filter%2A>.</span><span class="sxs-lookup"><span data-stu-id="30e5f-103">You can expose the sorting and filtering capability of <xref:System.Windows.Forms.BindingSource> control through the <xref:System.Windows.Forms.BindingSource.Sort%2A> and <xref:System.Windows.Forms.BindingSource.Filter%2A> properties.</span></span> <span data-ttu-id="30e5f-104">Vous pouvez appliquer un tri simple lorsque la source de données sous-jacente est un <xref:System.ComponentModel.IBindingList>, et vous pouvez appliquer le filtrage et le tri avancé lorsque la source de données est un <xref:System.ComponentModel.IBindingListView>.</span><span class="sxs-lookup"><span data-stu-id="30e5f-104">You can apply simple sorting when the underlying data source is an <xref:System.ComponentModel.IBindingList>, and you can apply filtering and advanced sorting when the data source is an <xref:System.ComponentModel.IBindingListView>.</span></span> <span data-ttu-id="30e5f-105">La propriété <xref:System.Windows.Forms.BindingSource.Sort%2A> requiert une syntaxe ADO.NET standard : une chaîne représentant le nom d’une colonne de données dans la source de données, suivi de `ASC` ou `DESC` pour indiquer si la liste doit être triée par ordre croissant ou décroissant.</span><span class="sxs-lookup"><span data-stu-id="30e5f-105">The <xref:System.Windows.Forms.BindingSource.Sort%2A> property requires standard ADO.NET syntax: a string representing the name of a column of data in the data source followed by `ASC` or `DESC` to indicate whether the list should be sorted in ascending or descending order.</span></span> <span data-ttu-id="30e5f-106">Vous pouvez définir un tri avancé ou un tri sur plusieurs colonnes en séparant chaque colonne par un séparateur de virgule.</span><span class="sxs-lookup"><span data-stu-id="30e5f-106">You can set advanced sorting or multiple-column sorting by separating each column with a comma separator.</span></span> <span data-ttu-id="30e5f-107">La propriété <xref:System.Windows.Forms.BindingSource.Filter%2A> prend une expression de chaîne.</span><span class="sxs-lookup"><span data-stu-id="30e5f-107">The <xref:System.Windows.Forms.BindingSource.Filter%2A> property takes a string expression.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30e5f-108">Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application.</span><span class="sxs-lookup"><span data-stu-id="30e5f-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="30e5f-109">L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données.</span><span class="sxs-lookup"><span data-stu-id="30e5f-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="30e5f-110">Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="30e5f-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
### <a name="to-filter-data-with-the-bindingsource"></a><span data-ttu-id="30e5f-111">Pour filtrer des données avec le BindingSource</span><span class="sxs-lookup"><span data-stu-id="30e5f-111">To filter data with the BindingSource</span></span>  
  
- <span data-ttu-id="30e5f-112">Affectez à la propriété <xref:System.Windows.Forms.BindingSource.Filter%2A> la valeur expression de votre choix.</span><span class="sxs-lookup"><span data-stu-id="30e5f-112">Set the <xref:System.Windows.Forms.BindingSource.Filter%2A> property to expression that you want.</span></span>  
  
     <span data-ttu-id="30e5f-113">Dans l’exemple de code suivant, l’expression est un nom de colonne suivi de la valeur que vous souhaitez pour la colonne.</span><span class="sxs-lookup"><span data-stu-id="30e5f-113">In the following code example, the expression is a column name followed by value that you want for the column.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#11)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#11)]  
  
### <a name="to-sort-data-with-the-bindingsource"></a><span data-ttu-id="30e5f-114">Pour trier des données avec le BindingSource</span><span class="sxs-lookup"><span data-stu-id="30e5f-114">To sort data with the BindingSource</span></span>  
  
1. <span data-ttu-id="30e5f-115">Définissez la propriété <xref:System.Windows.Forms.BindingSource.Sort%2A> sur le nom de colonne que vous souhaitez suivi de `ASC` ou `DESC` pour indiquer l’ordre croissant ou décroissant.</span><span class="sxs-lookup"><span data-stu-id="30e5f-115">Set the <xref:System.Windows.Forms.BindingSource.Sort%2A> property to the column name that you want followed by `ASC` or `DESC` to indicate the ascending or descending order.</span></span>  
  
2. <span data-ttu-id="30e5f-116">Séparez plusieurs colonnes par une virgule.</span><span class="sxs-lookup"><span data-stu-id="30e5f-116">Separate multiple columns with a comma.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#12)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="30e5f-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="30e5f-117">Example</span></span>  
 <span data-ttu-id="30e5f-118">L’exemple de code suivant charge des données de la table Customers de l’exemple de base de données Northwind dans un contrôle <xref:System.Windows.Forms.DataGridView>, puis filtre et trie les données affichées.</span><span class="sxs-lookup"><span data-stu-id="30e5f-118">The following code example loads data from the Customers table of the Northwind sample database into a <xref:System.Windows.Forms.DataGridView> control, and filters and sorts the displayed data.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnectorFilterAndSort#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorFilterAndSort/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="30e5f-119">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="30e5f-119">Compiling the Code</span></span>  
 <span data-ttu-id="30e5f-120">Pour exécuter cet exemple, collez le code dans un formulaire qui contient un <xref:System.Windows.Forms.BindingSource> nommé `BindingSource1` et un <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="30e5f-120">To run this example, paste the code into a form that contains a <xref:System.Windows.Forms.BindingSource> named `BindingSource1` and a <xref:System.Windows.Forms.DataGridView> named `dataGridView1`.</span></span> <span data-ttu-id="30e5f-121">Gérez l’événement <xref:System.Windows.Forms.Form.Load> pour le formulaire et appelez `InitializeSortedFilteredBindingSource` dans la méthode de gestionnaire d’événements Load.</span><span class="sxs-lookup"><span data-stu-id="30e5f-121">Handle the <xref:System.Windows.Forms.Form.Load> event for the form and call `InitializeSortedFilteredBindingSource` in the load event handler method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e5f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30e5f-122">See also</span></span>

- <xref:System.Windows.Forms.BindingSource.Sort%2A>
- <xref:System.Windows.Forms.BindingSource.Filter%2A>
- <span data-ttu-id="30e5f-123">[Guide pratique pour installer des exemples de bases de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="30e5f-123">[How to: Install Sample Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/8b6y4c7s(v=vs.120))</span></span>
- [<span data-ttu-id="30e5f-124">BindingSource, composant</span><span class="sxs-lookup"><span data-stu-id="30e5f-124">BindingSource Component</span></span>](bindingsource-component.md)
