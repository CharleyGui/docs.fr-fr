---
title: Vue d'ensemble du contrôle MenuStrip
ms.date: 03/30/2017
f1_keywords:
- MenuStrip
helpviewer_keywords:
- MenuStrip control [Windows Forms], about MenuStrip control
- menus [Windows Forms], creating
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
ms.openlocfilehash: a536d13cb7be3f4e4e4a085e1a4da1b0899b3a0c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734471"
---
# <a name="menustrip-control-overview-windows-forms"></a><span data-ttu-id="f5e62-102">Vue d'ensemble du contrôle MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="f5e62-102">MenuStrip Control Overview (Windows Forms)</span></span>
<span data-ttu-id="f5e62-103">Les menus exposent les fonctionnalités à vos utilisateurs en détenant des commandes qui sont regroupées par un thème commun.</span><span class="sxs-lookup"><span data-stu-id="f5e62-103">Menus expose functionality to your users by holding commands that are grouped by a common theme.</span></span>  
  
 <span data-ttu-id="f5e62-104">Le contrôle de <xref:System.Windows.Forms.MenuStrip> a été introduit dans la version 2,0 du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f5e62-104">The <xref:System.Windows.Forms.MenuStrip> control was introduced in version 2.0 of the .NET Framework.</span></span> <span data-ttu-id="f5e62-105">Avec le contrôle <xref:System.Windows.Forms.MenuStrip>, vous pouvez facilement créer des menus comme ceux qui se trouvent dans Microsoft Office.</span><span class="sxs-lookup"><span data-stu-id="f5e62-105">With the <xref:System.Windows.Forms.MenuStrip> control, you can easily create menus like those found in Microsoft Office.</span></span>  
  
 <span data-ttu-id="f5e62-106">Le contrôle <xref:System.Windows.Forms.MenuStrip> prend en charge l’interface multidocument (MDI) et la fusion de menus, les info-bulles et le dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="f5e62-106">The <xref:System.Windows.Forms.MenuStrip> control supports the multiple-document interface (MDI) and menu merging, tool tips, and overflow.</span></span> <span data-ttu-id="f5e62-107">Vous pouvez améliorer l’utilisation et la lisibilité de vos menus en ajoutant des touches d’accès rapide, des touches de raccourci, des coches, des images et des barres de séparation.</span><span class="sxs-lookup"><span data-stu-id="f5e62-107">You can enhance the usability and readability of your menus by adding access keys, shortcut keys, check marks, images, and separator bars.</span></span>  
  
 <span data-ttu-id="f5e62-108">Le contrôle <xref:System.Windows.Forms.MenuStrip> remplace et ajoute des fonctionnalités au contrôle <xref:System.Windows.Forms.MainMenu> ; Toutefois, le contrôle de <xref:System.Windows.Forms.MainMenu> est conservé pour la compatibilité descendante et l’utilisation future si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="f5e62-108">The <xref:System.Windows.Forms.MenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.MainMenu> control; however, the <xref:System.Windows.Forms.MainMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
## <a name="ways-to-use-the-menustrip-control"></a><span data-ttu-id="f5e62-109">Méthodes d’utilisation du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="f5e62-109">Ways to Use the MenuStrip Control</span></span>  
 <span data-ttu-id="f5e62-110">Utilisez le contrôle <xref:System.Windows.Forms.MenuStrip> pour :</span><span class="sxs-lookup"><span data-stu-id="f5e62-110">Use the <xref:System.Windows.Forms.MenuStrip> control to:</span></span>  
  
- <span data-ttu-id="f5e62-111">Créez facilement des menus personnalisés et couramment employés qui prennent en charge les fonctionnalités avancées de mise en page et d’interface utilisateur, telles que le tri et l’alignement de texte et d’image, les opérations glisser-déplacer, MDI, le dépassement de capacité et d’autres modes d’accès aux commandes de menu.</span><span class="sxs-lookup"><span data-stu-id="f5e62-111">Create easily customized, commonly employed menus that support advanced user interface and layout features, such as text and image ordering and alignment, drag-and-drop operations, MDI, overflow, and alternate modes of accessing menu commands.</span></span>  
  
- <span data-ttu-id="f5e62-112">Prendre en charge l’apparence et le comportement typiques du système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="f5e62-112">Support the typical appearance and behavior of the operating system.</span></span>  
  
- <span data-ttu-id="f5e62-113">Gérez les événements de manière cohérente pour tous les conteneurs et éléments qu’ils contiennent, de la même façon que vous gérez des événements pour d’autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="f5e62-113">Handle events consistently for all containers and contained items, in the same way you handle events for other controls.</span></span>  
  
 <span data-ttu-id="f5e62-114">Le tableau suivant présente certaines propriétés particulièrement importantes des <xref:System.Windows.Forms.MenuStrip> et des classes associées.</span><span class="sxs-lookup"><span data-stu-id="f5e62-114">The following table shows some particularly important properties of <xref:System.Windows.Forms.MenuStrip> and associated classes.</span></span>  
  
|<span data-ttu-id="f5e62-115">Propriété</span><span class="sxs-lookup"><span data-stu-id="f5e62-115">Property</span></span>|<span data-ttu-id="f5e62-116">Description</span><span class="sxs-lookup"><span data-stu-id="f5e62-116">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|<span data-ttu-id="f5e62-117">Obtient ou définit le <xref:System.Windows.Forms.ToolStripMenuItem> utilisé pour afficher une liste de formulaires enfants MDI.</span><span class="sxs-lookup"><span data-stu-id="f5e62-117">Gets or sets the <xref:System.Windows.Forms.ToolStripMenuItem> that is used to display a list of MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=nameWithType>|<span data-ttu-id="f5e62-118">Obtient ou définit la manière dont les menus enfants sont fusionnés avec les menus parents dans les applications MDI.</span><span class="sxs-lookup"><span data-stu-id="f5e62-118">Gets or sets how child menus are merged with parent menus in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=nameWithType>|<span data-ttu-id="f5e62-119">Obtient ou définit la position d’un élément fusionné dans un menu dans les applications MDI.</span><span class="sxs-lookup"><span data-stu-id="f5e62-119">Gets or sets the position of a merged item within a menu in MDI applications.</span></span>|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=nameWithType>|<span data-ttu-id="f5e62-120">Obtient ou définit une valeur indiquant si le formulaire est un conteneur de formulaires enfants MDI.</span><span class="sxs-lookup"><span data-stu-id="f5e62-120">Gets or sets a value indicating whether the form is a container for MDI child forms.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<span data-ttu-id="f5e62-121">Obtient ou définit une valeur indiquant si les info-bulles sont affichées pour le <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="f5e62-121">Gets or sets a value indicating whether tool tips are shown for the <xref:System.Windows.Forms.MenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<span data-ttu-id="f5e62-122">Obtient ou définit une valeur indiquant si le <xref:System.Windows.Forms.MenuStrip> prend en charge les fonctionnalités de dépassement de capacité.</span><span class="sxs-lookup"><span data-stu-id="f5e62-122">Gets or sets a value indicating whether the <xref:System.Windows.Forms.MenuStrip> supports overflow functionality.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<span data-ttu-id="f5e62-123">Obtient ou définit les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="f5e62-123">Gets or sets the shortcut keys associated with the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<span data-ttu-id="f5e62-124">Obtient ou définit une valeur qui indique si les touches de raccourci associées à <xref:System.Windows.Forms.ToolStripMenuItem> sont affichées en regard de <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="f5e62-124">Gets or sets a value indicating whether the shortcut keys that are associated with the <xref:System.Windows.Forms.ToolStripMenuItem> are displayed next to the <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>|  
  
 <span data-ttu-id="f5e62-125">Le tableau suivant présente les principales classes auxiliaires <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="f5e62-125">The following table shows the important <xref:System.Windows.Forms.MenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="f5e62-126">Class</span><span class="sxs-lookup"><span data-stu-id="f5e62-126">Class</span></span>|<span data-ttu-id="f5e62-127">Description</span><span class="sxs-lookup"><span data-stu-id="f5e62-127">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="f5e62-128">Représente une option pouvant être sélectionnée, qui est affichée sur un <xref:System.Windows.Forms.MenuStrip> ou un <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="f5e62-128">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ContextMenuStrip>|<span data-ttu-id="f5e62-129">Représente un menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="f5e62-129">Represents a shortcut menu.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="f5e62-130">Représente un contrôle qui permet à l’utilisateur de sélectionner un élément unique dans une liste qui s’affiche lorsque l’utilisateur clique sur un <xref:System.Windows.Forms.ToolStripDropDownButton> ou sur un élément de menu de niveau supérieur.</span><span class="sxs-lookup"><span data-stu-id="f5e62-130">Represents a control that allows the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="f5e62-131">Fournit des fonctionnalités de base pour les contrôles dérivés de <xref:System.Windows.Forms.ToolStripItem> qui affichent des éléments déroulants lorsque l’utilisateur clique dessus.</span><span class="sxs-lookup"><span data-stu-id="f5e62-131">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f5e62-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f5e62-132">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.StatusStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
