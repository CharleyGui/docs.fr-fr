---
title: Vue d'ensemble du composant MainMenu
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745115"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="1daa5-102">Vue d'ensemble du composant MainMenu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1daa5-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="1daa5-103">Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes, <xref:System.Windows.Forms.MainMenu> et les <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et l’utilisation future si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="1daa5-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="1daa5-104">Le composant Windows Forms <xref:System.Windows.Forms.MainMenu> affiche un menu au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="1daa5-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="1daa5-105">Tous les sous-menus du menu principal et les éléments individuels sont des objets <xref:System.Windows.Forms.MenuItem>.</span><span class="sxs-lookup"><span data-stu-id="1daa5-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="1daa5-106">Propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="1daa5-106">Key Properties</span></span>  
 <span data-ttu-id="1daa5-107">Un élément de menu peut être désigné comme élément par défaut en affectant à la propriété <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="1daa5-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="1daa5-108">L’élément par défaut s’affiche en gras lorsque l’utilisateur clique sur le menu.</span><span class="sxs-lookup"><span data-stu-id="1daa5-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="1daa5-109">La propriété <xref:System.Windows.Forms.MenuItem.Checked%2A> de l’élément de menu est `true` ou `false`, et indique si l’élément de menu est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="1daa5-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="1daa5-110">La propriété <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> de l’élément de menu personnalise l’apparence de l’élément sélectionné : si <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> a la valeur `true`, une case d’option apparaît en regard de l’élément. Si <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> est défini sur `false`, une coche apparaît en regard de l’élément.</span><span class="sxs-lookup"><span data-stu-id="1daa5-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1daa5-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1daa5-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="1daa5-112">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="1daa5-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
