---
title: Ajouter et supprimer des éléments de menu avec le composant ContextMenu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
ms.openlocfilehash: 989ab6d47ec761930a32f542b5fa1136e831f73d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746269"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="7fec8-102">Comment : ajouter et supprimer des éléments de menu avec le composant ContextMenu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7fec8-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="7fec8-103">Explique comment ajouter et supprimer des éléments de menu contextuel dans Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7fec8-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="7fec8-104">Le composant Windows Forms <xref:System.Windows.Forms.ContextMenu> fournit un menu de commandes fréquemment utilisées qui s’appliquent à l’objet sélectionné.</span><span class="sxs-lookup"><span data-stu-id="7fec8-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="7fec8-105">Vous pouvez ajouter des éléments au menu contextuel en ajoutant des objets <xref:System.Windows.Forms.MenuItem> à la collection <xref:System.Windows.Forms.Menu.MenuItems%2A>.</span><span class="sxs-lookup"><span data-stu-id="7fec8-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="7fec8-106">Vous pouvez supprimer des éléments d’un menu contextuel de manière permanente. Toutefois, au moment de l’exécution, il peut être plus approprié de masquer ou de désactiver les éléments à la place.</span><span class="sxs-lookup"><span data-stu-id="7fec8-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="7fec8-107">Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes, <xref:System.Windows.Forms.MainMenu> et les <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et l’utilisation future si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="7fec8-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="7fec8-108">Pour supprimer des éléments d’un menu contextuel</span><span class="sxs-lookup"><span data-stu-id="7fec8-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="7fec8-109">Utilisez la méthode <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> ou <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> de la collection <xref:System.Windows.Forms.Menu.MenuItems%2A> du composant <xref:System.Windows.Forms.ContextMenu> pour supprimer un élément de menu particulier.</span><span class="sxs-lookup"><span data-stu-id="7fec8-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     <span data-ttu-id="7fec8-110">\- ou -</span><span class="sxs-lookup"><span data-stu-id="7fec8-110">-or-</span></span>  
  
2. <span data-ttu-id="7fec8-111">Utilisez la méthode `Clear` de la collection `MenuItems` du composant <xref:System.Windows.Forms.ContextMenu> pour supprimer tous les éléments du menu.</span><span class="sxs-lookup"><span data-stu-id="7fec8-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7fec8-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7fec8-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="7fec8-113">ContextMenu, composant</span><span class="sxs-lookup"><span data-stu-id="7fec8-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="7fec8-114">Vue d'ensemble du composant ContextMenu</span><span class="sxs-lookup"><span data-stu-id="7fec8-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
