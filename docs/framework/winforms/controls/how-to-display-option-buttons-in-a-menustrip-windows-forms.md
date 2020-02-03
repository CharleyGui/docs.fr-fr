---
title: "Comment : afficher des cases d'option dans un MenuStrip"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MenuStrip [Windows Forms], displaying option buttons
- displaying option buttons [Windows Forms], MenuStrip [Windows Forms]
- option buttons [Windows Forms], displaying in MenuStrip
ms.assetid: 8b596af2-9ff8-4f7b-93d7-cba830e167f4
ms.openlocfilehash: f3010e71396ce562e9dbdefd4b75b36f3a81ffb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735527"
---
# <a name="how-to-display-option-buttons-in-a-menustrip-windows-forms"></a><span data-ttu-id="34952-102">Comment : afficher des cases d'option dans un MenuStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="34952-102">How to: Display Option Buttons in a MenuStrip (Windows Forms)</span></span>

<span data-ttu-id="34952-103">Les cases d’option, également appelées cases d’option, sont similaires aux cases à cocher, à ceci près que les utilisateurs ne peuvent sélectionner qu’un seul à la fois.</span><span class="sxs-lookup"><span data-stu-id="34952-103">Option buttons, also known as radio buttons, are similar to check boxes except that users can select only one at a time.</span></span> <span data-ttu-id="34952-104">Bien que la classe <xref:System.Windows.Forms.ToolStripMenuItem> ne fournisse pas par défaut le comportement de bouton d’option, la classe fournit un comportement de case à cocher que vous pouvez personnaliser pour implémenter le comportement de bouton d’option pour les éléments de menu dans un contrôle <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="34952-104">Although by default the <xref:System.Windows.Forms.ToolStripMenuItem> class does not provide option-button behavior, the class does provide check-box behavior that you can customize to implement option-button behavior for menu items in a <xref:System.Windows.Forms.MenuStrip> control.</span></span>

<span data-ttu-id="34952-105">Lorsque la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> d’un élément de menu est `true`, les utilisateurs peuvent cliquer sur l’élément pour basculer l’affichage d’une coche.</span><span class="sxs-lookup"><span data-stu-id="34952-105">When the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property of a menu item is `true`, users can click the item to toggle the display of a check mark.</span></span> <span data-ttu-id="34952-106">La propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> indique l’état actuel de l’élément.</span><span class="sxs-lookup"><span data-stu-id="34952-106">The <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property indicates the current state of the item.</span></span> <span data-ttu-id="34952-107">Pour implémenter un comportement de bouton d’option de base, vous devez vous assurer que lorsqu’un élément est sélectionné, vous affectez à la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> de l’élément sélectionné précédemment la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="34952-107">To implement basic option-button behavior, you must ensure that when an item is selected, you set the <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> property for the previously selected item to `false`.</span></span>

<span data-ttu-id="34952-108">Les procédures suivantes décrivent comment implémenter cette fonctionnalité et d’autres fonctionnalités dans une classe qui hérite de la classe <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="34952-108">The following procedures describe how to implement this and additional functionality in a class that inherits the <xref:System.Windows.Forms.ToolStripMenuItem> class.</span></span> <span data-ttu-id="34952-109">La classe `ToolStripRadioButtonMenuItem` remplace des membres tels que <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> et <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pour fournir le comportement de sélection et l’apparence des cases d’option.</span><span class="sxs-lookup"><span data-stu-id="34952-109">The `ToolStripRadioButtonMenuItem` class overrides members such as <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> and <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> to provide the selection behavior and appearance of option buttons.</span></span> <span data-ttu-id="34952-110">En outre, cette classe remplace la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> afin que les options d’un sous-menu soient désactivées, sauf si l’élément parent est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="34952-110">Additionally, this class overrides the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that options on a submenu are disabled unless the parent item is selected.</span></span>

## <a name="to-implement-option-button-selection-behavior"></a><span data-ttu-id="34952-111">Pour implémenter le comportement de sélection d’un bouton d’option</span><span class="sxs-lookup"><span data-stu-id="34952-111">To implement option-button selection behavior</span></span>

1. <span data-ttu-id="34952-112">Initialisez la propriété <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> sur `true` pour activer la sélection de l’élément.</span><span class="sxs-lookup"><span data-stu-id="34952-112">Initialize the <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> property to `true` to enable item selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#110](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#110)]
     [!code-vb[ToolStripRadioButtonMenuItem#110](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#110)]

2. <span data-ttu-id="34952-113">Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> pour effacer la sélection de l’élément sélectionné précédemment lorsqu’un nouvel élément est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="34952-113">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A> method to clear the selection of the previously selected item when a new item is selected.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#120](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#120)]
     [!code-vb[ToolStripRadioButtonMenuItem#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#120)]

3. <span data-ttu-id="34952-114">Remplacez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> pour vous assurer que le fait de cliquer sur un élément qui a déjà été sélectionné n’efface pas la sélection.</span><span class="sxs-lookup"><span data-stu-id="34952-114">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnClick%2A> method to ensure that clicking an item that has already been selected will not clear the selection.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#130](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#130)]
     [!code-vb[ToolStripRadioButtonMenuItem#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#130)]

## <a name="to-modify-the-appearance-of-the-option-button-items"></a><span data-ttu-id="34952-115">Pour modifier l’apparence des éléments de bouton d’option</span><span class="sxs-lookup"><span data-stu-id="34952-115">To modify the appearance of the option-button items</span></span>

1. <span data-ttu-id="34952-116">Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> pour remplacer la coche par défaut par une case d’option à l’aide de la classe <xref:System.Windows.Forms.RadioButtonRenderer>.</span><span class="sxs-lookup"><span data-stu-id="34952-116">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method to replace the default check-mark with an option button by using the <xref:System.Windows.Forms.RadioButtonRenderer> class.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#140](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#140)]
     [!code-vb[ToolStripRadioButtonMenuItem#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#140)]

2. <span data-ttu-id="34952-117">Substituez les méthodes <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>et <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> pour suivre l’état de la souris et vous assurer que la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> peint l’état de bouton d’option correct.</span><span class="sxs-lookup"><span data-stu-id="34952-117">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseEnter%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseLeave%2A>, <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseDown%2A>, and <xref:System.Windows.Forms.ToolStripMenuItem.OnMouseUp%2A> methods to track the state of the mouse and ensure that the <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A> method paints the correct option-button state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#150](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#150)]
     [!code-vb[ToolStripRadioButtonMenuItem#150](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#150)]

## <a name="to-disable-options-on-a-submenu-when-the-parent-item-is-not-selected"></a><span data-ttu-id="34952-118">Pour désactiver les options dans un sous-menu lorsque l’élément parent n’est pas sélectionné</span><span class="sxs-lookup"><span data-stu-id="34952-118">To disable options on a submenu when the parent item is not selected</span></span>

1. <span data-ttu-id="34952-119">Substituez la propriété <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> afin que l’élément soit désactivé lorsqu’il a un élément parent avec une valeur <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> de `true` et une valeur <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> de `false`.</span><span class="sxs-lookup"><span data-stu-id="34952-119">Override the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property so that the item is disabled when it has a parent item with both a <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A> value of `true` and a <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A> value of `false`.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#160](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#160)]
     [!code-vb[ToolStripRadioButtonMenuItem#160](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#160)]

2. <span data-ttu-id="34952-120">Substituez la méthode <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> pour vous abonner au <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> événement de l’élément parent.</span><span class="sxs-lookup"><span data-stu-id="34952-120">Override the <xref:System.Windows.Forms.ToolStripMenuItem.OnOwnerChanged%2A> method to subscribe to the <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event of the parent item.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#170](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#170)]
     [!code-vb[ToolStripRadioButtonMenuItem#170](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#170)]

3. <span data-ttu-id="34952-121">Dans le gestionnaire de l’événement de <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> parent-élément, invalidez l’élément pour mettre à jour l’affichage avec le nouvel état activé.</span><span class="sxs-lookup"><span data-stu-id="34952-121">In the handler for the parent-item <xref:System.Windows.Forms.ToolStripMenuItem.CheckedChanged> event, invalidate the item to update the display with the new enabled state.</span></span>

     [!code-csharp[ToolStripRadioButtonMenuItem#180](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#180)]
     [!code-vb[ToolStripRadioButtonMenuItem#180](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#180)]

## <a name="example"></a><span data-ttu-id="34952-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="34952-122">Example</span></span>

<span data-ttu-id="34952-123">L’exemple de code suivant fournit la classe `ToolStripRadioButtonMenuItem` complète, ainsi qu’une classe <xref:System.Windows.Forms.Form> et une classe `Program` pour illustrer le comportement de la case d’option.</span><span class="sxs-lookup"><span data-stu-id="34952-123">The following code example provides the complete `ToolStripRadioButtonMenuItem` class, and a <xref:System.Windows.Forms.Form> class and `Program` class to demonstrate the option-button behavior.</span></span>

[!code-csharp[ToolStripRadioButtonMenuItem#000](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/cs/ToolStripRadioButtonMenuItem.cs#000)]
[!code-vb[ToolStripRadioButtonMenuItem#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripRadioButtonMenuItem/vb/ToolStripRadioButtonMenuItem.vb#000)]

## <a name="compiling-the-code"></a><span data-ttu-id="34952-124">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="34952-124">Compiling the Code</span></span>

<span data-ttu-id="34952-125">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="34952-125">This example requires:</span></span>

- <span data-ttu-id="34952-126">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="34952-126">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="34952-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34952-127">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnCheckedChanged%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.OnPaint%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.RadioButtonRenderer>
- [<span data-ttu-id="34952-128">MenuStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="34952-128">MenuStrip Control</span></span>](menustrip-control-windows-forms.md)
- [<span data-ttu-id="34952-129">Guide pratique pour implémenter un ToolStripRenderer personnalisé</span><span class="sxs-lookup"><span data-stu-id="34952-129">How to: Implement a Custom ToolStripRenderer</span></span>](how-to-implement-a-custom-toolstriprenderer.md)
