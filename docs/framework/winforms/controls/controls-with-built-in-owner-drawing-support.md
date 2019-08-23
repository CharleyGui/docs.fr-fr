---
title: Contrôles avec prise en charge intégrée des dessins owner-drawn
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930192"
---
# <a name="controls-with-built-in-owner-drawing-support"></a><span data-ttu-id="d6a97-102">Contrôles avec prise en charge intégrée des dessins owner-drawn</span><span class="sxs-lookup"><span data-stu-id="d6a97-102">Controls with Built-In Owner-Drawing Support</span></span>
<span data-ttu-id="d6a97-103">Le dessin owner-drawn dans Windows Forms, qui est également appelé dessin personnalisé, est une technique permettant de changer l’apparence visuelle de certains contrôles.</span><span class="sxs-lookup"><span data-stu-id="d6a97-103">Owner drawing in Windows Forms, which is also known as custom drawing, is a technique for changing the visual appearance of certain controls.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6a97-104">Le mot «contrôle» dans cette rubrique est utilisé pour signifier les classes qui dérivent <xref:System.ComponentModel.Component>de <xref:System.Windows.Forms.Control> ou de.</span><span class="sxs-lookup"><span data-stu-id="d6a97-104">The word "control" in this topic is used to mean classes that derive from either <xref:System.Windows.Forms.Control> or <xref:System.ComponentModel.Component>.</span></span>  
  
 <span data-ttu-id="d6a97-105">En général, Windows gère automatiquement la peinture en utilisant des paramètres <xref:System.Windows.Forms.Control.BackColor%2A> de propriété tels que pour déterminer l’apparence d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6a97-105">Typically, Windows handles painting automatically by using property settings such as <xref:System.Windows.Forms.Control.BackColor%2A> to determine the appearance of a control.</span></span> <span data-ttu-id="d6a97-106">Avec le dessin owner-drawn, vous contrôlez le processus de dessin, en changeant l’apparence des éléments qui ne sont pas disponibles via des propriétés.</span><span class="sxs-lookup"><span data-stu-id="d6a97-106">With owner drawing, you take over the painting process, changing elements of appearance that are not available by using properties.</span></span> <span data-ttu-id="d6a97-107">Par exemple, de nombreux contrôles vous permettent de définir la couleur du texte qui s’affiche, mais vous êtes limité à une seule couleur.</span><span class="sxs-lookup"><span data-stu-id="d6a97-107">For example, many controls let you set the color of the text that is displayed, but you are limited to a single color.</span></span> <span data-ttu-id="d6a97-108">Le dessin owner-drawn vous permet d’effectuer des opérations comme afficher une partie du texte en noir et une autre en rouge.</span><span class="sxs-lookup"><span data-stu-id="d6a97-108">Owner drawing enables you to do things like display part of the text in black and part in red.</span></span>  
  
 <span data-ttu-id="d6a97-109">Dans la pratique, le dessin owner-drawn est similaire au dessin de graphiques dans un formulaire.</span><span class="sxs-lookup"><span data-stu-id="d6a97-109">In practice, owner drawing is similar to drawing graphics on a form.</span></span> <span data-ttu-id="d6a97-110">Par exemple, vous pouvez utiliser des méthodes graphiques dans un gestionnaire pour que l' <xref:System.Windows.Forms.Control.Paint> événement du formulaire émule `ListBox` un contrôle, mais vous devez écrire votre propre code pour gérer toutes les interactions de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="d6a97-110">For example, you could use graphics methods in a handler for the form's <xref:System.Windows.Forms.Control.Paint> event to emulate a `ListBox` control, but you would have to write your own code to handle all user interaction.</span></span> <span data-ttu-id="d6a97-111">Avec le dessin owner-drawn, le contrôle utilise votre code pour dessiner son contenu, mais il conserve par ailleurs toutes ses capacités intrinsèques.</span><span class="sxs-lookup"><span data-stu-id="d6a97-111">With owner drawing, the control uses your code to draw its contents but otherwise retains all its intrinsic capabilities.</span></span> <span data-ttu-id="d6a97-112">Vous pouvez utiliser des méthodes graphiques pour dessiner chaque élément du contrôle ou pour personnaliser certains aspects de chaque élément, tout en utilisant l’apparence par défaut pour d’autres aspects de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="d6a97-112">You can use graphics methods to draw each item in the control or to customize some aspects of each item while you use the default appearance for other aspects of each item.</span></span>  
  
## <a name="owner-drawing-in-windows-forms-controls"></a><span data-ttu-id="d6a97-113">Dessin owner-drawn dans les contrôles Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a97-113">Owner Drawing in Windows Forms Controls</span></span>  
 <span data-ttu-id="d6a97-114">Pour effectuer du dessin owner-drawn dans les contrôles qui le prennent en charge, vous définissez généralement une propriété, et vous gérez un ou plusieurs événements.</span><span class="sxs-lookup"><span data-stu-id="d6a97-114">To perform owner drawing in controls that support it, you will typically set one property and handle one or more events.</span></span>  
  
 <span data-ttu-id="d6a97-115">La plupart des contrôles qui prennent en charge le dessin owner-drawn ont une propriété `OwnerDraw` ou `DrawMode` qui indique si le contrôle déclenche son ou ses événements de dessin quand il se dessine lui-même.</span><span class="sxs-lookup"><span data-stu-id="d6a97-115">Most controls that support owner drawing have an `OwnerDraw` or `DrawMode` property that indicates whether the control will raise its drawing-related event or events when it paints itself.</span></span>  
  
 <span data-ttu-id="d6a97-116">Les contrôles qui n’ont pas une propriété `OwnerDraw` ou `DrawMode` incluent le contrôle `DataGridView`, qui fournit des événements de dessin qui se produisent automatiquement, et le contrôle `ToolStrip`, qui est dessiné à l’aide d’une classe de rendu externe qui a ses propres événements de dessin.</span><span class="sxs-lookup"><span data-stu-id="d6a97-116">Controls that do not have an `OwnerDraw` or `DrawMode` property include the `DataGridView` control, which provides drawing events that occur automatically, and the `ToolStrip` control, which is drawn using an external rendering class that has its own drawing-related events.</span></span>  
  
 <span data-ttu-id="d6a97-117">Il existe de nombreux types d’événements de dessin, mais un événement de dessin se produit généralement pour dessiner un élément dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6a97-117">There are many different kinds of drawing events, but a typical drawing event occurs in order to draw a single item within a control.</span></span> <span data-ttu-id="d6a97-118">Le gestionnaire d’événements reçoit un objet `EventArgs` qui contient des informations sur l’élément dessiné et des outils que vous pouvez utiliser pour le dessiner.</span><span class="sxs-lookup"><span data-stu-id="d6a97-118">The event handler receives an `EventArgs` object that contains information about the item being drawn and tools you can use to draw it.</span></span> <span data-ttu-id="d6a97-119">Par exemple, cet objet contient généralement le numéro d’index de l’élément dans sa collection parent <xref:System.Drawing.Rectangle> , un qui indique les limites d’affichage de l' <xref:System.Drawing.Graphics> élément et un objet pour appeler les méthodes de peinture.</span><span class="sxs-lookup"><span data-stu-id="d6a97-119">For example, this object typically contains the item's index number within its parent collection, a <xref:System.Drawing.Rectangle> that indicates the item's display boundaries, and a <xref:System.Drawing.Graphics> object for calling paint methods.</span></span> <span data-ttu-id="d6a97-120">Pour certains événements, l’objet `EventArgs` fournit plus d’informations sur l’élément sur les méthodes que vous pouvez appeler pour dessiner certains aspects de l’élément par défaut, comme l’arrière-plan ou un rectangle de focus.</span><span class="sxs-lookup"><span data-stu-id="d6a97-120">For some events, the `EventArgs` object provides additional information about the item and methods that you can call to paint some aspects of the item by default, such as the background or a focus rectangle.</span></span>  
  
 <span data-ttu-id="d6a97-121">Pour créer un contrôle réutilisable contenant vos personnalisations owner-drawn, créez une classe qui dérive d’une classe de contrôle prenant en charge le dessin owner-drawn.</span><span class="sxs-lookup"><span data-stu-id="d6a97-121">To create a reusable control that contains your owner-drawn customizations, create a new class that derives from a control class that supports owner drawing.</span></span> <span data-ttu-id="d6a97-122">Au lieu de gérer les événements de dessin, incluez votre code de dessin owner-drawn dans la ou les méthodes `On`*nom_événement* appropriées de la nouvelle classe.</span><span class="sxs-lookup"><span data-stu-id="d6a97-122">Rather than handling drawing events, include your owner-drawing code in overrides for the appropriate `On`*EventName* method or methods in the new class.</span></span> <span data-ttu-id="d6a97-123">Vérifiez que vous appelez dans ce cas la ou les méthodes `On`*nom_événement* de la classe de base, pour que les utilisateurs de votre contrôle puissent gérer les événements de dessin owner-drawn et fournir une personnalisation supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="d6a97-123">Make sure that you call the base class `On`*EventName* method or methods in this case so that users of your control can handle owner-drawing events and provide additional customization.</span></span>  
  
 <span data-ttu-id="d6a97-124">Les contrôles Windows Forms suivants prennent en charge le dessin owner-drawn dans toutes les versions du .NET Framework :</span><span class="sxs-lookup"><span data-stu-id="d6a97-124">The following Windows Forms controls support owner drawing in all versions of the .NET Framework:</span></span>  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <span data-ttu-id="d6a97-125"><xref:System.Windows.Forms.MenuItem>(utilisé par <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu>)</span><span class="sxs-lookup"><span data-stu-id="d6a97-125"><xref:System.Windows.Forms.MenuItem> (used by <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu>)</span></span>  
  
- <xref:System.Windows.Forms.TabControl>  
  
 <span data-ttu-id="d6a97-126">Les contrôles suivants prennent en charge le dessin owner-drawn uniquement dans .NET Framework 2,0:</span><span class="sxs-lookup"><span data-stu-id="d6a97-126">The following controls support owner drawing only in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 <span data-ttu-id="d6a97-127">Les contrôles suivants prennent en charge le dessin owner-drawn et sont nouveaux dans .NET Framework 2,0:</span><span class="sxs-lookup"><span data-stu-id="d6a97-127">The following controls support owner drawing and are new in .NET Framework 2.0:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 <span data-ttu-id="d6a97-128">Les sections suivantes contiennent des informations détaillées supplémentaires pour chacun de ces contrôles.</span><span class="sxs-lookup"><span data-stu-id="d6a97-128">The following sections provide additional details for each of these controls.</span></span>  
  
### <a name="listbox-and-combobox-controls"></a><span data-ttu-id="d6a97-129">Contrôles Edit et Combobox</span><span class="sxs-lookup"><span data-stu-id="d6a97-129">ListBox and ComboBox Controls</span></span>  
 <span data-ttu-id="d6a97-130">Les <xref:System.Windows.Forms.ListBox> contrôles <xref:System.Windows.Forms.ComboBox> et vous permettent de dessiner des éléments individuels dans le contrôle, soit tous dans une seule taille, soit à des tailles différentes.</span><span class="sxs-lookup"><span data-stu-id="d6a97-130">The <xref:System.Windows.Forms.ListBox> and <xref:System.Windows.Forms.ComboBox> controls enable you to draw individual items in the control either all in one size, or in varying sizes.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6a97-131">Bien que <xref:System.Windows.Forms.CheckedListBox> le contrôle soit dérivé <xref:System.Windows.Forms.ListBox> du contrôle, il ne prend pas en charge le dessin owner-drawn.</span><span class="sxs-lookup"><span data-stu-id="d6a97-131">Although the <xref:System.Windows.Forms.CheckedListBox> control is derived from the <xref:System.Windows.Forms.ListBox> control, it does not support owner drawing.</span></span>  
  
 <span data-ttu-id="d6a97-132">Pour dessiner chaque élément de la même taille, affectez `DrawMode` à <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> la propriété la `DrawItem` valeur et gérez l’événement.</span><span class="sxs-lookup"><span data-stu-id="d6a97-132">To draw each item the same size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="d6a97-133">Pour dessiner chaque élément en utilisant une taille différente `DrawMode` , affectez à <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> la propriété la valeur et `DrawItem` gérez `MeasureItem` les événements et.</span><span class="sxs-lookup"><span data-stu-id="d6a97-133">To draw each item using a different size, set the `DrawMode` property to <xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> and handle both the `MeasureItem` and `DrawItem` events.</span></span> <span data-ttu-id="d6a97-134">L’événement `MeasureItem` vous permet d’indiquer la taille d’un élément avant que l’événement `DrawItem` se produise pour cet élément.</span><span class="sxs-lookup"><span data-stu-id="d6a97-134">The `MeasureItem` event lets you indicate the size of an item before the `DrawItem` event occurs for that item.</span></span>  
  
 <span data-ttu-id="d6a97-135">Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6a97-135">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [<span data-ttu-id="d6a97-136">Guide pratique pour Créer du texte de taille variable dans un contrôle ComboBox</span><span class="sxs-lookup"><span data-stu-id="d6a97-136">How to: Create Variable Sized Text in a ComboBox Control</span></span>](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a><span data-ttu-id="d6a97-137">MenuItem, composant</span><span class="sxs-lookup"><span data-stu-id="d6a97-137">MenuItem Component</span></span>  
 <span data-ttu-id="d6a97-138">Le <xref:System.Windows.Forms.MenuItem> composant représente un élément de menu unique dans <xref:System.Windows.Forms.MainMenu> un <xref:System.Windows.Forms.ContextMenu> composant ou.</span><span class="sxs-lookup"><span data-stu-id="d6a97-138">The <xref:System.Windows.Forms.MenuItem> component represents a single menu item in a <xref:System.Windows.Forms.MainMenu> or <xref:System.Windows.Forms.ContextMenu> component.</span></span>  
  
 <span data-ttu-id="d6a97-139">Pour dessiner un <xref:System.Windows.Forms.MenuItem>, définissez sa `OwnerDraw` propriété sur `true` et gérez son `DrawItem` événement.</span><span class="sxs-lookup"><span data-stu-id="d6a97-139">To draw a <xref:System.Windows.Forms.MenuItem>, set its `OwnerDraw` property to `true` and handle its `DrawItem` event.</span></span> <span data-ttu-id="d6a97-140">Pour personnaliser la taille de l’élément de menu avant que l’événement `DrawItem` se produise, gérez l’événement `MeasureItem` de l’élément.</span><span class="sxs-lookup"><span data-stu-id="d6a97-140">To customize the size of the menu item before the `DrawItem` event occurs, handle the item's `MeasureItem` event.</span></span>  
  
 <span data-ttu-id="d6a97-141">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6a97-141">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a><span data-ttu-id="d6a97-142">TabControl, contrôle</span><span class="sxs-lookup"><span data-stu-id="d6a97-142">TabControl Control</span></span>  
 <span data-ttu-id="d6a97-143">Le <xref:System.Windows.Forms.TabControl> contrôle vous permet de dessiner des onglets individuels dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6a97-143">The <xref:System.Windows.Forms.TabControl> control enables you to draw individual tabs in the control.</span></span> <span data-ttu-id="d6a97-144">Le dessin owner-drawn affecte uniquement les onglets; le <xref:System.Windows.Forms.TabPage> contenu n’est pas affecté.</span><span class="sxs-lookup"><span data-stu-id="d6a97-144">Owner drawing affects only the tabs; the <xref:System.Windows.Forms.TabPage> contents are not affected.</span></span>  
  
 <span data-ttu-id="d6a97-145">Pour dessiner chaque onglet dans un <xref:System.Windows.Forms.TabControl>, affectez `DrawMode` à <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> la propriété la valeur `DrawItem` et gérez l’événement.</span><span class="sxs-lookup"><span data-stu-id="d6a97-145">To draw each tab in a <xref:System.Windows.Forms.TabControl>, set the `DrawMode` property to <xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed> and handle the `DrawItem` event.</span></span> <span data-ttu-id="d6a97-146">Cet événement se produit une fois pour chaque onglet uniquement quand l’onglet est visible dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6a97-146">This event occurs once for each tab only when the tab is visible in the control.</span></span>  
  
 <span data-ttu-id="d6a97-147">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6a97-147">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a><span data-ttu-id="d6a97-148">ToolTip, composant</span><span class="sxs-lookup"><span data-stu-id="d6a97-148">ToolTip Component</span></span>  
 <span data-ttu-id="d6a97-149">Le <xref:System.Windows.Forms.ToolTip> composant vous permet de dessiner la totalité de l’info-bulle lorsqu’elle est affichée.</span><span class="sxs-lookup"><span data-stu-id="d6a97-149">The <xref:System.Windows.Forms.ToolTip> component enables you to draw the entire ToolTip when it is displayed.</span></span>  
  
 <span data-ttu-id="d6a97-150">Pour dessiner un <xref:System.Windows.Forms.ToolTip>, définissez sa `OwnerDraw` propriété sur `true` et gérez son `Draw` événement.</span><span class="sxs-lookup"><span data-stu-id="d6a97-150">To draw a <xref:System.Windows.Forms.ToolTip>, set its `OwnerDraw` property to `true` and handle its `Draw` event.</span></span> <span data-ttu-id="d6a97-151">Pour personnaliser la <xref:System.Windows.Forms.ToolTip> taille du avant que l' `Draw` événement se produise, gérez l' `Popup` événement et <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> définissez la propriété dans le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="d6a97-151">To customize the size of the <xref:System.Windows.Forms.ToolTip> before the `Draw` event occurs, handle the `Popup` event and set the <xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A> property in the event handler.</span></span>  
  
 <span data-ttu-id="d6a97-152">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6a97-152">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a><span data-ttu-id="d6a97-153">Contrôle ListView</span><span class="sxs-lookup"><span data-stu-id="d6a97-153">ListView Control</span></span>  
 <span data-ttu-id="d6a97-154">Le <xref:System.Windows.Forms.ListView> contrôle vous permet de dessiner des éléments individuels, des sous-éléments et des en-têtes de colonnes dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6a97-154">The <xref:System.Windows.Forms.ListView> control enables you to draw individual items, subitems, and column headers in the control.</span></span>  
  
 <span data-ttu-id="d6a97-155">Pour activer le dessin owner-drawn dans le contrôle, définissez la propriété `OwnerDraw` sur `true`.</span><span class="sxs-lookup"><span data-stu-id="d6a97-155">To enable owner drawing in the control, set the `OwnerDraw` property to `true`.</span></span>  
  
 <span data-ttu-id="d6a97-156">Pour dessiner chaque élément dans le contrôle, gérez l’événement `DrawItem`.</span><span class="sxs-lookup"><span data-stu-id="d6a97-156">To draw each item in the control, handle the `DrawItem` event.</span></span>  
  
 <span data-ttu-id="d6a97-157">Pour dessiner chaque sous-élément ou en-tête de colonne <xref:System.Windows.Forms.ListView.View%2A> dans le contrôle lorsque la propriété a `DrawSubItem` la `DrawColumnHeader` <xref:System.Windows.Forms.View.Details>valeur, gérez les événements et.</span><span class="sxs-lookup"><span data-stu-id="d6a97-157">To draw each subitem or column header in the control when the <xref:System.Windows.Forms.ListView.View%2A> property is set to <xref:System.Windows.Forms.View.Details>, handle the `DrawSubItem` and `DrawColumnHeader` events.</span></span>  
  
 <span data-ttu-id="d6a97-158">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6a97-158">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a><span data-ttu-id="d6a97-159">TreeView, contrôle</span><span class="sxs-lookup"><span data-stu-id="d6a97-159">TreeView Control</span></span>  
 <span data-ttu-id="d6a97-160">Le <xref:System.Windows.Forms.TreeView> contrôle vous permet de dessiner des nœuds individuels dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6a97-160">The <xref:System.Windows.Forms.TreeView> control enables you to draw individual nodes in the control.</span></span>  
  
 <span data-ttu-id="d6a97-161">Pour dessiner uniquement le texte affiché dans chaque nœud, affectez `DrawMode` à <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> la propriété la valeur `DrawNode` et gérez l’événement pour dessiner le texte.</span><span class="sxs-lookup"><span data-stu-id="d6a97-161">To draw only the text displayed in each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText> and handle the `DrawNode` event to draw the text.</span></span>  
  
 <span data-ttu-id="d6a97-162">Pour dessiner tous les éléments de chaque nœud, définissez `DrawMode` la propriété <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> sur et gérez `DrawNode` l’événement pour dessiner les éléments dont vous avez besoin, tels que le texte, les icônes, les cases à cocher, les signes plus et moins, et les lignes qui connectent les nœuds.</span><span class="sxs-lookup"><span data-stu-id="d6a97-162">To draw all elements of each node, set the `DrawMode` property to <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll> and handle the `DrawNode` event to draw whichever elements you need, such as text, icons, check boxes, plus and minus signs, and lines connecting the nodes.</span></span>  
  
 <span data-ttu-id="d6a97-163">Pour plus d’informations, notamment des exemples de code, consultez les rubriques de référence suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6a97-163">For more information, including code examples, see the following reference topics:</span></span>  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a><span data-ttu-id="d6a97-164">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="d6a97-164">DataGridView Control</span></span>  
 <span data-ttu-id="d6a97-165">Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de dessiner des cellules et des lignes individuelles dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d6a97-165">The <xref:System.Windows.Forms.DataGridView> control enables you to draw individual cells and rows in the control.</span></span>  
  
 <span data-ttu-id="d6a97-166">Pour dessiner des cellules individuelles, gérez l’événement `CellPainting`.</span><span class="sxs-lookup"><span data-stu-id="d6a97-166">To draw individual cells, handle the `CellPainting` event.</span></span>  
  
 <span data-ttu-id="d6a97-167">Pour dessiner des lignes individuelles ou des éléments de ligne, gérez un des événements `RowPrePaint` ou `RowPostPaint`, ou les deux.</span><span class="sxs-lookup"><span data-stu-id="d6a97-167">To draw individual rows or elements of rows, handle one or both of the `RowPrePaint` and `RowPostPaint` events.</span></span> <span data-ttu-id="d6a97-168">L’événement `RowPrePaint` se produit avant le dessin des cellules d’une ligne, et l’événement se produit `RowPostPaint` après le dessin des cellules.</span><span class="sxs-lookup"><span data-stu-id="d6a97-168">The `RowPrePaint` event occurs before the cells in a row are painted, and the `RowPostPaint` event occurs after the cells are painted.</span></span> <span data-ttu-id="d6a97-169">Vous pouvez gérer ces deux événements et l’événement `CellPainting` pour dessiner séparément l’arrière-plan de la ligne, les cellules individuelles et le premier plan de la ligne, ou vous pouvez fournir des personnalisations spécifiques là où vous en avez besoin et utiliser l’affichage par défaut pour les autres éléments de la ligne.</span><span class="sxs-lookup"><span data-stu-id="d6a97-169">You can handle both events and the `CellPainting` event to paint row background, individual cells, and row foreground separately, or you can provide specific customizations where you need them and use the default display for other elements of the row.</span></span>  
  
 <span data-ttu-id="d6a97-170">Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6a97-170">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [<span data-ttu-id="d6a97-171">Guide pratique : Personnaliser l’apparence des cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a97-171">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [<span data-ttu-id="d6a97-172">Guide pratique : Personnaliser l’apparence des lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a97-172">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a><span data-ttu-id="d6a97-173">ToolStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="d6a97-173">ToolStrip Control</span></span>  
 <span data-ttu-id="d6a97-174"><xref:System.Windows.Forms.ToolStrip>et les contrôles dérivés vous permettent de personnaliser tous les aspects de leur apparence.</span><span class="sxs-lookup"><span data-stu-id="d6a97-174"><xref:System.Windows.Forms.ToolStrip> and derived controls enable you to customize any aspect of their appearance.</span></span>  
  
 <span data-ttu-id="d6a97-175">Pour fournir un rendu personnalisé <xref:System.Windows.Forms.ToolStrip> pour les contrôles, `Renderer` définissez la <xref:System.Windows.Forms.ToolStripPanel>propriété <xref:System.Windows.Forms.ToolStrip>d' <xref:System.Windows.Forms.ToolStripManager>un,, <xref:System.Windows.Forms.ToolStripContentPanel> ou sur `ToolStripRenderer` un objet et gérez un ou plusieurs des nombreux événements de dessin fournis par le `ToolStripRenderer` classe.</span><span class="sxs-lookup"><span data-stu-id="d6a97-175">To provide custom rendering for <xref:System.Windows.Forms.ToolStrip> controls, set the `Renderer` property of a <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.ToolStripManager>, <xref:System.Windows.Forms.ToolStripPanel>, or <xref:System.Windows.Forms.ToolStripContentPanel> to a `ToolStripRenderer` object and handle one or more of the many drawing events provided by the `ToolStripRenderer` class.</span></span> <span data-ttu-id="d6a97-176">Vous pouvez également définir une `Renderer` propriété sur une instance de votre propre classe dérivée `ToolStripRenderer`de <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, ou <xref:System.Windows.Forms.ToolStripSystemRenderer> qui implémente ou substitue des méthodes `On` *EventName* spécifiques.</span><span class="sxs-lookup"><span data-stu-id="d6a97-176">Alternatively, set a `Renderer` property to an instance of your own class derived from `ToolStripRenderer`, <xref:System.Windows.Forms.ToolStripProfessionalRenderer>, or <xref:System.Windows.Forms.ToolStripSystemRenderer> that implements or overrides specific `On`*EventName* methods.</span></span>  
  
 <span data-ttu-id="d6a97-177">Pour plus d’informations, notamment des exemples de code, consultez les rubriques suivantes :</span><span class="sxs-lookup"><span data-stu-id="d6a97-177">For more information, including code examples, see the following topics:</span></span>  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [<span data-ttu-id="d6a97-178">Guide pratique pour Créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a97-178">How to: Create and Set a Custom Renderer for the ToolStrip Control in Windows Forms</span></span>](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [<span data-ttu-id="d6a97-179">Guide pratique : Dessiner un contrôle ToolStrip personnalisé</span><span class="sxs-lookup"><span data-stu-id="d6a97-179">How to: Custom Draw a ToolStrip Control</span></span>](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a><span data-ttu-id="d6a97-180">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d6a97-180">See also</span></span>

- [<span data-ttu-id="d6a97-181">Contrôles à utiliser dans les Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d6a97-181">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
