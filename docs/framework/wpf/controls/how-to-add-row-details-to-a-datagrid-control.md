---
title: 'Procédure : ajouter des détails de ligne à un contrôle DataGrid'
description: Découvrez comment personnaliser la présentation des données lorsque vous utilisez le contrôle DataGrid Windows Presentation Foundation en ajoutant une section de détails des lignes.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: 8fd6b07f454681a0eed70d7a6208cfcc426dc920
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164952"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a><span data-ttu-id="1d839-103">Procédure : ajouter des détails de ligne à un contrôle DataGrid</span><span class="sxs-lookup"><span data-stu-id="1d839-103">How to: Add Row Details to a DataGrid Control</span></span>
<span data-ttu-id="1d839-104">Lorsque vous utilisez le <xref:System.Windows.Controls.DataGrid> contrôle, vous pouvez personnaliser la présentation des données en ajoutant une section de détails des lignes.</span><span class="sxs-lookup"><span data-stu-id="1d839-104">When using the <xref:System.Windows.Controls.DataGrid> control, you can customize the data presentation by adding a row details section.</span></span> <span data-ttu-id="1d839-105">L’ajout d’une section de détails de ligne vous permet de regrouper des données dans un modèle qui est éventuellement visible ou réduit.</span><span class="sxs-lookup"><span data-stu-id="1d839-105">Adding a row details section enables you to group some data in a template that is optionally visible or collapsed.</span></span> <span data-ttu-id="1d839-106">Par exemple, vous pouvez ajouter des détails de ligne à un <xref:System.Windows.Controls.DataGrid> qui présente uniquement un résumé des données de chaque ligne du <xref:System.Windows.Controls.DataGrid> , mais présente davantage de champs de données lorsque l’utilisateur sélectionne une ligne.</span><span class="sxs-lookup"><span data-stu-id="1d839-106">For example, you can add row details to a <xref:System.Windows.Controls.DataGrid> that presents only a summary of the data for each row in the <xref:System.Windows.Controls.DataGrid>, but presents more data fields when the user selects a row.</span></span> <span data-ttu-id="1d839-107">Vous définissez le modèle pour la section de détails des lignes dans la <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="1d839-107">You define the template for the row details section in the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property.</span></span> <span data-ttu-id="1d839-108">L’illustration suivante montre un exemple de section de détails de ligne.</span><span class="sxs-lookup"><span data-stu-id="1d839-108">The following illustration shows an example of a row details section.</span></span>  
  
 <span data-ttu-id="1d839-109">![DataGrid affiché avec détails de la ligne](./media/ndp-rowdetails.png "NDP_RowDetails")</span><span class="sxs-lookup"><span data-stu-id="1d839-109">![DataGrid shown with row details](./media/ndp-rowdetails.png "NDP_RowDetails")</span></span>  
  
 <span data-ttu-id="1d839-110">Vous définissez le modèle de détails de ligne en tant que XAML inline ou en tant que ressource.</span><span class="sxs-lookup"><span data-stu-id="1d839-110">You define the row details template as either inline XAML or as a resource.</span></span> <span data-ttu-id="1d839-111">Les deux approches sont présentées dans les procédures suivantes.</span><span class="sxs-lookup"><span data-stu-id="1d839-111">Both approaches are shown in the following procedures.</span></span> <span data-ttu-id="1d839-112">Un modèle de données qui est ajouté en tant que ressource peut être utilisé dans tout le projet sans recréer le modèle.</span><span class="sxs-lookup"><span data-stu-id="1d839-112">A data template that is added as a resource can be used throughout the project without re-creating the template.</span></span> <span data-ttu-id="1d839-113">Un modèle de données ajouté en tant que code XAML inline est uniquement accessible à partir du contrôle dans lequel il est défini.</span><span class="sxs-lookup"><span data-stu-id="1d839-113">A data template that is added as inline XAML is only accessible from the control where it is defined.</span></span>  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a><span data-ttu-id="1d839-114">Pour afficher les détails des lignes à l’aide du code XAML inline</span><span class="sxs-lookup"><span data-stu-id="1d839-114">To display row details by using inline XAML</span></span>  
  
1. <span data-ttu-id="1d839-115">Créez un <xref:System.Windows.Controls.DataGrid> qui affiche les données d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="1d839-115">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="1d839-116">Dans l'élément <xref:System.Windows.Controls.DataGrid>, ajoutez un élément <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d839-116">In the <xref:System.Windows.Controls.DataGrid> element, add a <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> element.</span></span>  
  
3. <span data-ttu-id="1d839-117">Créez un <xref:System.Windows.DataTemplate> qui définit l’apparence de la section de détails des lignes.</span><span class="sxs-lookup"><span data-stu-id="1d839-117">Create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="1d839-118">Le code XAML suivant montre <xref:System.Windows.Controls.DataGrid> et comment définir le en <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> ligne.</span><span class="sxs-lookup"><span data-stu-id="1d839-118">The following XAML shows the <xref:System.Windows.Controls.DataGrid> and how to define the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> inline.</span></span> <span data-ttu-id="1d839-119">Le <xref:System.Windows.Controls.DataGrid> affiche trois valeurs dans chaque ligne et trois valeurs supplémentaires lorsque la ligne est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="1d839-119">The <xref:System.Windows.Controls.DataGrid> displays three values in each row and three more values when the row is selected.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#1](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     <span data-ttu-id="1d839-120">Le code suivant montre la requête utilisée pour sélectionner les données qui sont affichées dans le <xref:System.Windows.Controls.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="1d839-120">The following code shows the query that is used to select the data that is displayed in the <xref:System.Windows.Controls.DataGrid>.</span></span> <span data-ttu-id="1d839-121">Dans cet exemple, la requête sélectionne des données à partir d’une entité qui contient des informations sur les clients.</span><span class="sxs-lookup"><span data-stu-id="1d839-121">In this example, the query selects data from an entity that contains customer information.</span></span>  
  
     [!code-csharp[DataGrid_RowDetails#2](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a><span data-ttu-id="1d839-122">Pour afficher les détails des lignes à l’aide d’une ressource</span><span class="sxs-lookup"><span data-stu-id="1d839-122">To display row details by using a resource</span></span>  
  
1. <span data-ttu-id="1d839-123">Créez un <xref:System.Windows.Controls.DataGrid> qui affiche les données d’une source de données.</span><span class="sxs-lookup"><span data-stu-id="1d839-123">Create a <xref:System.Windows.Controls.DataGrid> that displays data from a data source.</span></span>  
  
2. <span data-ttu-id="1d839-124">Ajoutez un <xref:System.Windows.FrameworkElement.Resources%2A> élément à l’élément racine, tel qu’un <xref:System.Windows.Window> contrôle ou un <xref:System.Windows.Controls.Page> contrôle, ou ajoutez un <xref:System.Windows.Application.Resources%2A> élément à la <xref:System.Windows.Application> classe dans le fichier app. XAML (ou application. Xaml).</span><span class="sxs-lookup"><span data-stu-id="1d839-124">Add a <xref:System.Windows.FrameworkElement.Resources%2A> element to the root element, such as a <xref:System.Windows.Window> control or a <xref:System.Windows.Controls.Page> control, or add a <xref:System.Windows.Application.Resources%2A> element to the <xref:System.Windows.Application> class in the App.xaml (or Application.xaml) file.</span></span>  
  
3. <span data-ttu-id="1d839-125">Dans l’élément Resources, créez un <xref:System.Windows.DataTemplate> qui définit l’apparence de la section de détails des lignes.</span><span class="sxs-lookup"><span data-stu-id="1d839-125">In the resources element, create a <xref:System.Windows.DataTemplate> that defines the appearance of the row details section.</span></span>  
  
     <span data-ttu-id="1d839-126">Le code XAML suivant montre le <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> défini dans la <xref:System.Windows.Application> classe.</span><span class="sxs-lookup"><span data-stu-id="1d839-126">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> defined in the <xref:System.Windows.Application> class.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#3](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4. <span data-ttu-id="1d839-127">Sur le <xref:System.Windows.DataTemplate> , définissez la [directive x :Key](../../../desktop-wpf/xaml-services/xkey-directive.md) sur une valeur qui identifie de façon unique le modèle de données.</span><span class="sxs-lookup"><span data-stu-id="1d839-127">On the <xref:System.Windows.DataTemplate>, set the [x:Key Directive](../../../desktop-wpf/xaml-services/xkey-directive.md) to a value that uniquely identifies the data template.</span></span>  
  
5. <span data-ttu-id="1d839-128">Dans l' <xref:System.Windows.Controls.DataGrid> élément, affectez <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> à la propriété la ressource définie dans les étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="1d839-128">In the <xref:System.Windows.Controls.DataGrid> element, set the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property to the resource defined in the previous steps.</span></span> <span data-ttu-id="1d839-129">Assignez la ressource en tant que ressource statique.</span><span class="sxs-lookup"><span data-stu-id="1d839-129">Assign the resource as a static resource.</span></span>  
  
     <span data-ttu-id="1d839-130">Le code XAML suivant montre la <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> propriété définie sur la ressource de l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="1d839-130">The following XAML shows the <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> property set to the resource from the previous example.</span></span>  
  
     [!code-xaml[DataGrid_RowDetails#4](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a><span data-ttu-id="1d839-131">Pour définir la visibilité et empêcher le défilement horizontal pour les détails de ligne</span><span class="sxs-lookup"><span data-stu-id="1d839-131">To set visibility and prevent horizontal scrolling for row details</span></span>  
  
1. <span data-ttu-id="1d839-132">Si nécessaire, affectez <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> une valeur à la propriété <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> .</span><span class="sxs-lookup"><span data-stu-id="1d839-132">If needed, set the <xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> property to a <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> value.</span></span>  
  
     <span data-ttu-id="1d839-133">Par défaut, la valeur est définie sur <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected> .</span><span class="sxs-lookup"><span data-stu-id="1d839-133">By default, the value is set to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>.</span></span> <span data-ttu-id="1d839-134">Vous pouvez lui affecter <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> la valeur pour afficher les détails de toutes les lignes ou <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> pour masquer les détails de toutes les lignes.</span><span class="sxs-lookup"><span data-stu-id="1d839-134">You can set it to <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible> to show the details for all of the rows or <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed> to hide the details for all rows.</span></span>  
  
2. <span data-ttu-id="1d839-135">Si nécessaire, affectez à la propriété la valeur <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> `true` pour empêcher la section des détails des lignes de faire défiler horizontalement.</span><span class="sxs-lookup"><span data-stu-id="1d839-135">If needed, set the <xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> property to `true` to prevent the row details section from scrolling horizontally.</span></span>
