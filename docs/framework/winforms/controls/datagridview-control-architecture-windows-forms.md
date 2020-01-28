---
title: Architecture du contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742528"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="5b928-102">Architecture du contrôle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5b928-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="5b928-103">Le contrôle <xref:System.Windows.Forms.DataGridView> et ses classes associées sont conçus pour être un système flexible et extensible permettant d’afficher et de modifier des données tabulaires.</span><span class="sxs-lookup"><span data-stu-id="5b928-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="5b928-104">Ces classes sont toutes contenues dans l’espace de noms <xref:System.Windows.Forms?displayProperty=nameWithType>, et elles sont toutes nommées avec le préfixe « DataGridView ».</span><span class="sxs-lookup"><span data-stu-id="5b928-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="5b928-105">Éléments d'architecture</span><span class="sxs-lookup"><span data-stu-id="5b928-105">Architecture Elements</span></span>  
 <span data-ttu-id="5b928-106">Les principales classes auxiliaires <xref:System.Windows.Forms.DataGridView> dérivent de <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="5b928-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="5b928-107">Le modèle objet suivant illustre la hiérarchie d’héritage <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="5b928-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![Diagramme qui affiche la hiérarchie du modèle objet DataGridViewElement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="5b928-109">La classe <xref:System.Windows.Forms.DataGridViewElement> fournit une référence au contrôle parent <xref:System.Windows.Forms.DataGridView> et a une propriété <xref:System.Windows.Forms.DataGridViewElement.State%2A>, qui contient une valeur qui représente une combinaison de valeurs de l’énumération <xref:System.Windows.Forms.DataGridViewElementStates>.</span><span class="sxs-lookup"><span data-stu-id="5b928-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="5b928-110">Les sections suivantes décrivent plus en détail les classes <xref:System.Windows.Forms.DataGridView> Companion.</span><span class="sxs-lookup"><span data-stu-id="5b928-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="5b928-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="5b928-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="5b928-112">L’énumération <xref:System.Windows.Forms.DataGridViewElementStates> contient les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="5b928-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="5b928-113">Les valeurs de cette énumération peuvent être combinées avec les opérateurs logiques au niveau du bit, de sorte que la propriété <xref:System.Windows.Forms.DataGridViewElement.State%2A> peut exprimer plusieurs États à la fois.</span><span class="sxs-lookup"><span data-stu-id="5b928-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="5b928-114">Par exemple, un <xref:System.Windows.Forms.DataGridViewElement> peut être <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>simultanément, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>et <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="5b928-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="5b928-115">Cellules et bandes</span><span class="sxs-lookup"><span data-stu-id="5b928-115">Cells and Bands</span></span>  
 <span data-ttu-id="5b928-116">Le contrôle <xref:System.Windows.Forms.DataGridView> comprend deux types d’objets fondamentaux : les cellules et les bandes.</span><span class="sxs-lookup"><span data-stu-id="5b928-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="5b928-117">Toutes les cellules dérivent de la classe de base <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="5b928-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="5b928-118">Les deux types de bandes, <xref:System.Windows.Forms.DataGridViewColumn> et <xref:System.Windows.Forms.DataGridViewRow>, dérivent les deux de la classe de base <xref:System.Windows.Forms.DataGridViewBand>.</span><span class="sxs-lookup"><span data-stu-id="5b928-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="5b928-119">Le contrôle <xref:System.Windows.Forms.DataGridView> interagit avec plusieurs classes, mais les plus fréquemment rencontrées sont <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>et <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="5b928-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="5b928-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="5b928-120">DataGridViewCell</span></span>  
 <span data-ttu-id="5b928-121">La cellule est l’unité fondamentale de l’interaction pour le <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="5b928-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="5b928-122">L’affichage est centré sur les cellules et l’entrée de données est souvent effectuée par le biais de cellules.</span><span class="sxs-lookup"><span data-stu-id="5b928-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="5b928-123">Vous pouvez accéder aux cellules à l’aide de la collection <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> de la classe <xref:System.Windows.Forms.DataGridViewRow>, et vous pouvez accéder aux cellules sélectionnées à l’aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> du contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="5b928-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5b928-124">Le modèle objet suivant illustre cette utilisation et affiche la hiérarchie d’héritage <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="5b928-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![Diagramme qui affiche la hiérarchie du modèle objet DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="5b928-126">Le type de <xref:System.Windows.Forms.DataGridViewCell> est une classe de base abstraite, dont tous les types de cellule dérivent.</span><span class="sxs-lookup"><span data-stu-id="5b928-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="5b928-127"><xref:System.Windows.Forms.DataGridViewCell> et ses types dérivés ne sont pas des contrôles Windows Forms, mais certains contrôleurs de Windows Forms hôtes.</span><span class="sxs-lookup"><span data-stu-id="5b928-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="5b928-128">Toute fonctionnalité d’édition prise en charge par une cellule est généralement gérée par un contrôle hébergé.</span><span class="sxs-lookup"><span data-stu-id="5b928-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="5b928-129">les objets <xref:System.Windows.Forms.DataGridViewCell> ne contrôlent pas leurs propres fonctionnalités d’apparence et de peinture de la même façon que les contrôles Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5b928-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="5b928-130">Au lieu de cela, le <xref:System.Windows.Forms.DataGridView> est responsable de l’apparence de ses objets <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="5b928-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="5b928-131">Vous pouvez affecter de manière significative l’apparence et le comportement des cellules en interagissant avec les propriétés et événements du contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="5b928-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="5b928-132">Quand vous avez des exigences spéciales pour les personnalisations qui dépassent les capacités du contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez implémenter votre propre classe qui dérive de <xref:System.Windows.Forms.DataGridViewCell> ou de l’une de ses classes enfants.</span><span class="sxs-lookup"><span data-stu-id="5b928-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="5b928-133">La liste suivante répertorie les classes dérivées de <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="5b928-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- <span data-ttu-id="5b928-134">Vos types de cellules personnalisés</span><span class="sxs-lookup"><span data-stu-id="5b928-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="5b928-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="5b928-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="5b928-136">Le schéma du magasin de données attaché du contrôle <xref:System.Windows.Forms.DataGridView> est exprimé dans les colonnes du contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="5b928-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="5b928-137">Vous pouvez accéder aux colonnes du contrôle <xref:System.Windows.Forms.DataGridView> à l’aide de la collection <xref:System.Windows.Forms.DataGridView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b928-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="5b928-138">Vous pouvez accéder aux colonnes sélectionnées à l’aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b928-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="5b928-139">Le modèle objet suivant illustre cette utilisation et affiche la hiérarchie d’héritage <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="5b928-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![Diagramme qui affiche la hiérarchie du modèle objet DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="5b928-141">Certains des types de cellule clés ont des types de colonnes correspondants.</span><span class="sxs-lookup"><span data-stu-id="5b928-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="5b928-142">Celles-ci sont dérivées de la classe de base <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="5b928-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="5b928-143">La liste suivante répertorie les classes dérivées de <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="5b928-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- <span data-ttu-id="5b928-144">Vos types de colonnes personnalisés</span><span class="sxs-lookup"><span data-stu-id="5b928-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="5b928-145">Contrôles d’édition DataGridView</span><span class="sxs-lookup"><span data-stu-id="5b928-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="5b928-146">Les cellules qui prennent en charge la fonctionnalité d’édition avancée utilisent généralement un contrôle hébergé qui est dérivé d’un contrôle de Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5b928-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="5b928-147">Ces contrôles implémentent également l’interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="5b928-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="5b928-148">Le modèle objet suivant illustre l’utilisation de ces contrôles.</span><span class="sxs-lookup"><span data-stu-id="5b928-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![Diagramme montrant la hiérarchie du modèle objet du contrôle d’édition DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="5b928-150">Les contrôles d’édition suivants sont fournis avec le contrôle <xref:System.Windows.Forms.DataGridView> :</span><span class="sxs-lookup"><span data-stu-id="5b928-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="5b928-151">Pour plus d’informations sur la création de vos propres contrôles d’édition, consultez [Comment : héberger des contrôles dans Windows Forms des cellules DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="5b928-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="5b928-152">Le tableau suivant illustre la relation entre les types de cellules, les types de colonnes et les contrôles d’édition.</span><span class="sxs-lookup"><span data-stu-id="5b928-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="5b928-153">Type de cellule</span><span class="sxs-lookup"><span data-stu-id="5b928-153">Cell type</span></span>|<span data-ttu-id="5b928-154">Contrôle hébergé</span><span class="sxs-lookup"><span data-stu-id="5b928-154">Hosted control</span></span>|<span data-ttu-id="5b928-155">Type de colonne</span><span class="sxs-lookup"><span data-stu-id="5b928-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="5b928-156">N/A</span><span class="sxs-lookup"><span data-stu-id="5b928-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="5b928-157">N/A</span><span class="sxs-lookup"><span data-stu-id="5b928-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="5b928-158">N/A</span><span class="sxs-lookup"><span data-stu-id="5b928-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="5b928-159">N/A</span><span class="sxs-lookup"><span data-stu-id="5b928-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="5b928-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="5b928-160">DataGridViewRow</span></span>  
 <span data-ttu-id="5b928-161">La classe <xref:System.Windows.Forms.DataGridViewRow> affiche les champs de données d’un enregistrement à partir du magasin de données auquel le contrôle <xref:System.Windows.Forms.DataGridView> est attaché.</span><span class="sxs-lookup"><span data-stu-id="5b928-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="5b928-162">Vous pouvez accéder aux lignes du contrôle <xref:System.Windows.Forms.DataGridView> à l’aide de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b928-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="5b928-163">Vous pouvez accéder aux lignes sélectionnées à l’aide de la collection <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="5b928-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="5b928-164">Le modèle objet suivant illustre cette utilisation et affiche la hiérarchie d’héritage <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="5b928-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![Diagramme qui affiche la hiérarchie du modèle objet DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="5b928-166">Vous pouvez dériver vos propres types à partir de la classe <xref:System.Windows.Forms.DataGridViewRow>, bien que cela ne soit généralement pas nécessaire.</span><span class="sxs-lookup"><span data-stu-id="5b928-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="5b928-167">Le contrôle <xref:System.Windows.Forms.DataGridView> possède plusieurs événements et propriétés liés aux lignes pour personnaliser le comportement de ses objets <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="5b928-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="5b928-168">Si vous activez la propriété <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> du contrôle <xref:System.Windows.Forms.DataGridView>, une ligne spéciale pour l’ajout de nouvelles lignes apparaît comme dernière ligne.</span><span class="sxs-lookup"><span data-stu-id="5b928-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="5b928-169">Cette ligne fait partie de la collection <xref:System.Windows.Forms.DataGridView.Rows%2A>, mais elle possède des fonctionnalités spéciales qui peuvent nécessiter votre attention.</span><span class="sxs-lookup"><span data-stu-id="5b928-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="5b928-170">Pour plus d’informations, consultez [utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="5b928-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b928-171">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5b928-171">See also</span></span>

- [<span data-ttu-id="5b928-172">Vue d’ensemble du contrôle DataGridView</span><span class="sxs-lookup"><span data-stu-id="5b928-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="5b928-173">Personnalisation du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b928-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="5b928-174">Utilisation de la ligne pour les nouveaux enregistrements dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b928-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
