---
title: Vue d'ensemble du composant ContextMenu
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746200"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="8db3f-102">Vue d'ensemble du composant ContextMenu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="8db3f-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="8db3f-103">Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes, <xref:System.Windows.Forms.MainMenu> et les <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et l’utilisation future si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="8db3f-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="8db3f-104">Avec le composant Windows Forms <xref:System.Windows.Forms.ContextMenu>, vous pouvez fournir aux utilisateurs un menu contextuel facilement accessible des commandes fréquemment utilisées qui sont associées à l’objet sélectionné.</span><span class="sxs-lookup"><span data-stu-id="8db3f-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="8db3f-105">Les éléments d’un menu contextuel sont souvent un sous-ensemble des éléments des menus principaux qui apparaissent ailleurs dans l’application.</span><span class="sxs-lookup"><span data-stu-id="8db3f-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="8db3f-106">Un utilisateur peut généralement accéder à un menu contextuel en cliquant avec le bouton droit de la souris.</span><span class="sxs-lookup"><span data-stu-id="8db3f-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="8db3f-107">Sur Windows Forms, les menus contextuels sont associés à des contrôles.</span><span class="sxs-lookup"><span data-stu-id="8db3f-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="8db3f-108">Propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="8db3f-108">Key Properties</span></span>  
 <span data-ttu-id="8db3f-109">Vous pouvez associer un menu contextuel à un contrôle en affectant à la propriété <xref:System.Windows.Forms.Control.ContextMenu%2A> du contrôle la valeur du composant <xref:System.Windows.Forms.ContextMenu>.</span><span class="sxs-lookup"><span data-stu-id="8db3f-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="8db3f-110">Un menu contextuel unique peut être associé à plusieurs contrôles, mais chaque contrôle ne peut avoir qu’un seul menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="8db3f-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="8db3f-111">La propriété de clé du composant <xref:System.Windows.Forms.ContextMenu> est la propriété <xref:System.Windows.Forms.Menu.MenuItems%2A>.</span><span class="sxs-lookup"><span data-stu-id="8db3f-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="8db3f-112">Vous pouvez ajouter des éléments de menu en créant par programmation des objets <xref:System.Windows.Forms.MenuItem> et en les ajoutant à la <xref:System.Windows.Forms.Menu.MenuItemCollection> du menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="8db3f-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="8db3f-113">Étant donné que les éléments d’un menu contextuel sont généralement dessinés à partir d’autres menus, vous pouvez ajouter des éléments à un menu contextuel en les copiant le plus souvent.</span><span class="sxs-lookup"><span data-stu-id="8db3f-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db3f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8db3f-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
