---
title: Vue d'ensemble du composant ContextMenu (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 6ae7817bc158f30fbf55b5f6228ecdf134d6657d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962185"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="fb171-102">Vue d'ensemble du composant ContextMenu (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fb171-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="fb171-103">Bien <xref:System.Windows.Forms.MenuStrip> que <xref:System.Windows.Forms.ContextMenuStrip> et remplacent et ajoutent des <xref:System.Windows.Forms.ContextMenu> fonctionnalités aux contrôles et des <xref:System.Windows.Forms.MainMenu> versions <xref:System.Windows.Forms.ContextMenu> antérieures, et sont conservés pour la <xref:System.Windows.Forms.MainMenu> compatibilité descendante et l’utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="fb171-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="fb171-104">Avec le composant <xref:System.Windows.Forms.ContextMenu> Windows Forms, vous pouvez fournir aux utilisateurs un menu contextuel facilement accessible des commandes fréquemment utilisées qui sont associées à l’objet sélectionné.</span><span class="sxs-lookup"><span data-stu-id="fb171-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="fb171-105">Les éléments d’un menu contextuel sont souvent un sous-ensemble des éléments des menus principaux qui apparaissent ailleurs dans l’application.</span><span class="sxs-lookup"><span data-stu-id="fb171-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="fb171-106">Un utilisateur peut généralement accéder à un menu contextuel en cliquant avec le bouton droit de la souris.</span><span class="sxs-lookup"><span data-stu-id="fb171-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="fb171-107">Sur Windows Forms, les menus contextuels sont associés à des contrôles.</span><span class="sxs-lookup"><span data-stu-id="fb171-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="fb171-108">Propriétés de clé</span><span class="sxs-lookup"><span data-stu-id="fb171-108">Key Properties</span></span>  
 <span data-ttu-id="fb171-109">Vous pouvez associer un menu contextuel à un contrôle en affectant à <xref:System.Windows.Forms.Control.ContextMenu%2A> la propriété du <xref:System.Windows.Forms.ContextMenu> contrôle la valeur du composant.</span><span class="sxs-lookup"><span data-stu-id="fb171-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="fb171-110">Un menu contextuel unique peut être associé à plusieurs contrôles, mais chaque contrôle ne peut avoir qu’un seul menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="fb171-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="fb171-111">La propriété de clé du <xref:System.Windows.Forms.ContextMenu> composant est la <xref:System.Windows.Forms.Menu.MenuItems%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="fb171-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="fb171-112">Vous pouvez ajouter <xref:System.Windows.Forms.MenuItem> <xref:System.Windows.Forms.Menu.MenuItemCollection> des éléments de menu en créant par programmation des objets et en les ajoutant au du menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="fb171-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="fb171-113">Étant donné que les éléments d’un menu contextuel sont généralement dessinés à partir d’autres menus, vous pouvez ajouter des éléments à un menu contextuel en les copiant le plus souvent.</span><span class="sxs-lookup"><span data-stu-id="fb171-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb171-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fb171-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
