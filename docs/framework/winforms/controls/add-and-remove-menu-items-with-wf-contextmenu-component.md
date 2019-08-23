---
title: 'Procédure : ajouter et supprimer des éléments de menu avec le composant ContextMenu de Windows Forms'
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
ms.openlocfilehash: 5d1862b1fc1398f0f8c2217b51c4efb93db639af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957020"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a><span data-ttu-id="ec982-102">Procédure : ajouter et supprimer des éléments de menu avec le composant ContextMenu de Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ec982-102">How to: Add and Remove Menu Items with the Windows Forms ContextMenu Component</span></span>
<span data-ttu-id="ec982-103">Explique comment ajouter et supprimer des éléments de menu contextuel dans Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="ec982-103">Explains how to add and remove shortcut menu items in Windows Forms.</span></span>  
  
 <span data-ttu-id="ec982-104">Le composant <xref:System.Windows.Forms.ContextMenu> Windows Forms fournit un menu de commandes fréquemment utilisées qui s’appliquent à l’objet sélectionné.</span><span class="sxs-lookup"><span data-stu-id="ec982-104">The Windows Forms <xref:System.Windows.Forms.ContextMenu> component provides a menu of frequently used commands that are relevant to the selected object.</span></span> <span data-ttu-id="ec982-105">Vous pouvez ajouter des éléments au menu contextuel en <xref:System.Windows.Forms.MenuItem> ajoutant des objets <xref:System.Windows.Forms.Menu.MenuItems%2A> à la collection.</span><span class="sxs-lookup"><span data-stu-id="ec982-105">You can add items to the shortcut menu by adding <xref:System.Windows.Forms.MenuItem> objects to the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection.</span></span>  
  
 <span data-ttu-id="ec982-106">Vous pouvez supprimer des éléments d’un menu contextuel de manière permanente. Toutefois, au moment de l’exécution, il peut être plus approprié de masquer ou de désactiver les éléments à la place.</span><span class="sxs-lookup"><span data-stu-id="ec982-106">You can remove items from a shortcut menu permanently; however, at run time it may be more appropriate to hide or disable the items instead.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="ec982-107">Bien <xref:System.Windows.Forms.MenuStrip> que <xref:System.Windows.Forms.ContextMenuStrip> et remplacent et ajoutent des <xref:System.Windows.Forms.ContextMenu> fonctionnalités aux contrôles et des <xref:System.Windows.Forms.MainMenu> versions <xref:System.Windows.Forms.ContextMenu> antérieures, et sont conservés pour la <xref:System.Windows.Forms.MainMenu> compatibilité descendante et l’utilisation future si tel est votre choix.</span><span class="sxs-lookup"><span data-stu-id="ec982-107">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a><span data-ttu-id="ec982-108">Pour supprimer des éléments d’un menu contextuel</span><span class="sxs-lookup"><span data-stu-id="ec982-108">To remove items from a shortcut menu</span></span>  
  
1. <span data-ttu-id="ec982-109">Utilisez la <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> méthode <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> <xref:System.Windows.Forms.Menu.MenuItems%2A> ou<xref:System.Windows.Forms.ContextMenu> de la collection du composant pour supprimer un élément de menu particulier.</span><span class="sxs-lookup"><span data-stu-id="ec982-109">Use the <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> or <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> method of the <xref:System.Windows.Forms.Menu.MenuItems%2A> collection of the <xref:System.Windows.Forms.ContextMenu> component to remove a particular menu item.</span></span>  
  
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
  
     <span data-ttu-id="ec982-110">ou</span><span class="sxs-lookup"><span data-stu-id="ec982-110">-or-</span></span>  
  
2. <span data-ttu-id="ec982-111">Utilisez la `Clear` méthode de la `MenuItems` collection du <xref:System.Windows.Forms.ContextMenu> composant pour supprimer tous les éléments du menu.</span><span class="sxs-lookup"><span data-stu-id="ec982-111">Use the `Clear` method of the `MenuItems` collection of the <xref:System.Windows.Forms.ContextMenu> component to remove all items from the menu.</span></span>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ec982-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ec982-112">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- [<span data-ttu-id="ec982-113">ContextMenu, composant</span><span class="sxs-lookup"><span data-stu-id="ec982-113">ContextMenu Component</span></span>](contextmenu-component-windows-forms.md)
- [<span data-ttu-id="ec982-114">Vue d'ensemble du composant ContextMenu</span><span class="sxs-lookup"><span data-stu-id="ec982-114">ContextMenu Component Overview</span></span>](contextmenu-component-overview-windows-forms.md)
