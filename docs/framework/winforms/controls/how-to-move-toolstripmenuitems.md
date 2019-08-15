---
title: 'Procédure : déplacer des ToolStripMenuItems'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039797"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="7779e-102">Procédure : déplacer des ToolStripMenuItems</span><span class="sxs-lookup"><span data-stu-id="7779e-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="7779e-103">Au moment du design, vous pouvez déplacer l’intégralité des menus de niveau supérieur et leurs éléments de menu vers un <xref:System.Windows.Forms.MenuStrip>autre emplacement sur le.</span><span class="sxs-lookup"><span data-stu-id="7779e-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="7779e-104">Vous pouvez également déplacer des éléments de menu individuels entre des menus de niveau supérieur ou modifier la position des éléments de menu dans un menu.</span><span class="sxs-lookup"><span data-stu-id="7779e-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="7779e-105">Pour déplacer un menu du plus haut niveau et ses éléments de menu vers un autre emplacement de niveau supérieur</span><span class="sxs-lookup"><span data-stu-id="7779e-105">To move a top-level menu and its menu items to another top-level location</span></span>

1. <span data-ttu-id="7779e-106">Cliquez et maintenez le bouton gauche de la souris enfoncé sur le menu que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="7779e-106">Click and hold down the left mouse button on the menu that you want to move.</span></span>

2. <span data-ttu-id="7779e-107">Faites glisser le point d’insertion vers le menu du plus haut niveau qui se trouve avant le nouvel emplacement prévu et relâchez le bouton gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="7779e-107">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>

     <span data-ttu-id="7779e-108">Le menu sélectionné se déplace à droite du point d’insertion.</span><span class="sxs-lookup"><span data-stu-id="7779e-108">The selected menu moves to the right of the insertion point.</span></span>

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="7779e-109">Pour déplacer un menu du plus haut niveau et ses éléments de menu vers un emplacement déroulant</span><span class="sxs-lookup"><span data-stu-id="7779e-109">To move a top-level menu and its menu items to a drop-down location</span></span>

1. <span data-ttu-id="7779e-110">Cliquez avec le bouton gauche sur le menu que vous souhaitez déplacer et appuyez sur CTRL + X, ou cliquez avec le bouton droit sur le menu et sélectionnez **couper** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7779e-110">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="7779e-111">Dans le menu du plus haut niveau de destination, cliquez sur l’élément de menu situé au-dessus du nouvel emplacement prévu et appuyez sur CTRL + V, ou cliquez avec le bouton droit sur l’élément de menu situé au-dessus du nouvel emplacement prévu et sélectionnez **coller** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7779e-111">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="7779e-112">Le menu que vous coupez est inséré après l’élément de menu sélectionné.</span><span class="sxs-lookup"><span data-stu-id="7779e-112">The menu that you cut is inserted after the selected menu item.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="7779e-113">Pour déplacer un élément de menu dans un menu à l’aide de l’éditeur de collections Items</span><span class="sxs-lookup"><span data-stu-id="7779e-113">To move a menu item within a menu using the Items Collection Editor</span></span>

1. <span data-ttu-id="7779e-114">Cliquez avec le bouton droit sur le menu qui contient l’élément de menu que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="7779e-114">Right-click the menu that contains the menu item you want to move.</span></span>

2. <span data-ttu-id="7779e-115">Dans le menu contextuel, choisissez **modifier DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="7779e-115">From the shortcut menu, choose **Edit DropDownItems**.</span></span>

3. <span data-ttu-id="7779e-116">Dans l **'éditeur de collections Items**, cliquez sur l’élément de menu que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="7779e-116">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>

4. <span data-ttu-id="7779e-117">Cliquez sur les flèches vers le haut et vers le bas pour déplacer l’élément de menu dans le menu.</span><span class="sxs-lookup"><span data-stu-id="7779e-117">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>

5. <span data-ttu-id="7779e-118">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="7779e-118">Click **OK**.</span></span>

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="7779e-119">Pour déplacer un élément de menu dans un menu à l’aide du clavier</span><span class="sxs-lookup"><span data-stu-id="7779e-119">To move a menu item within a menu using the keyboard</span></span>

1. <span data-ttu-id="7779e-120">Maintenez la touche ALT enfoncée.</span><span class="sxs-lookup"><span data-stu-id="7779e-120">Press and hold down the ALT key.</span></span>

2. <span data-ttu-id="7779e-121">Cliquez et maintenez enfoncé le bouton gauche de la souris sur l’élément de menu que vous souhaitez déplacer.</span><span class="sxs-lookup"><span data-stu-id="7779e-121">Click and hold the left mouse button on the menu item that you want to move.</span></span>

3. <span data-ttu-id="7779e-122">Faites glisser l’élément de menu vers le nouvel emplacement, puis relâchez le bouton gauche de la souris.</span><span class="sxs-lookup"><span data-stu-id="7779e-122">Drag the menu item to the new location and release the left mouse button.</span></span>

## <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="7779e-123">Pour déplacer un élément de menu vers un autre menu</span><span class="sxs-lookup"><span data-stu-id="7779e-123">To move a menu item to another menu</span></span>

1. <span data-ttu-id="7779e-124">Cliquez sur l’élément de menu que vous souhaitez déplacer et appuyez sur CTRL + X, ou cliquez avec le bouton droit sur l’élément de menu et choisissez **couper** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7779e-124">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>

2. <span data-ttu-id="7779e-125">Cliquez sur le menu qui contiendra l’élément de menu que vous avez coupé.</span><span class="sxs-lookup"><span data-stu-id="7779e-125">Left-click the menu that will contain the menu item that you cut.</span></span>

3. <span data-ttu-id="7779e-126">Cliquez sur l’élément de menu qui se trouve avant le nouvel emplacement prévu et appuyez sur CTRL + V, ou cliquez avec le bouton droit sur l’élément de menu qui se trouve avant le nouvel emplacement prévu et sélectionnez **coller** dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="7779e-126">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>

     <span data-ttu-id="7779e-127">L’élément de menu que vous coupez est inséré après l’élément de menu sélectionné.</span><span class="sxs-lookup"><span data-stu-id="7779e-127">The menu item that you cut is inserted after the selected menu item.</span></span>

## <a name="see-also"></a><span data-ttu-id="7779e-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7779e-128">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="7779e-129">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="7779e-129">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
