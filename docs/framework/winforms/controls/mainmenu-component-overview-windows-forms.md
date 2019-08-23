---
title: Vue d'ensemble du composant MainMenu (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: fe46683faee13bad951d5a7185aad8a687c290ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952133"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="a7a6f-102">Vue d'ensemble du composant MainMenu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a7a6f-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="a7a6f-103">Bien <xref:System.Windows.Forms.MenuStrip> que <xref:System.Windows.Forms.ContextMenuStrip> et remplacent et ajoutent des <xref:System.Windows.Forms.ContextMenu> fonctionnalités aux contrôles et des <xref:System.Windows.Forms.MainMenu> versions <xref:System.Windows.Forms.ContextMenu> antérieures, et sont conservés pour la <xref:System.Windows.Forms.MainMenu> compatibilité descendante et l’utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="a7a6f-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="a7a6f-104">Le composant <xref:System.Windows.Forms.MainMenu> Windows Forms affiche un menu au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="a7a6f-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="a7a6f-105">Tous les sous-menus du menu principal et les éléments individuels <xref:System.Windows.Forms.MenuItem> sont des objets.</span><span class="sxs-lookup"><span data-stu-id="a7a6f-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="a7a6f-106">Propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="a7a6f-106">Key Properties</span></span>  
 <span data-ttu-id="a7a6f-107">Un élément de menu peut être désigné comme élément par défaut en affectant <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> à `true`la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="a7a6f-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="a7a6f-108">L’élément par défaut s’affiche en gras lorsque l’utilisateur clique sur le menu.</span><span class="sxs-lookup"><span data-stu-id="a7a6f-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="a7a6f-109">La propriété de l' <xref:System.Windows.Forms.MenuItem.Checked%2A> élément de menu `true` a `false`la valeur ou, et indique si l’élément de menu est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="a7a6f-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="a7a6f-110"><xref:System.Windows.Forms.MenuItem.RadioCheck%2A> La propriété de l’élément de menu personnalise l’apparence de l’élément sélectionné <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> : si a `true`la valeur, une case d’option apparaît en regard `false`de <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> l’élément; si a la valeur, une coche apparaît en regard de l’élément.</span><span class="sxs-lookup"><span data-stu-id="a7a6f-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7a6f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7a6f-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="a7a6f-112">Vue d'ensemble du contrôle MenuStrip</span><span class="sxs-lookup"><span data-stu-id="a7a6f-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
