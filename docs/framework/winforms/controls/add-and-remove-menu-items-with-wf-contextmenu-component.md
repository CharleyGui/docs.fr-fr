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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Procédure : ajouter et supprimer des éléments de menu avec le composant ContextMenu de Windows Forms
Explique comment ajouter et supprimer des éléments de menu contextuel dans Windows Forms.  
  
 Le composant <xref:System.Windows.Forms.ContextMenu> Windows Forms fournit un menu de commandes fréquemment utilisées qui s’appliquent à l’objet sélectionné. Vous pouvez ajouter des éléments au menu contextuel en <xref:System.Windows.Forms.MenuItem> ajoutant des objets <xref:System.Windows.Forms.Menu.MenuItems%2A> à la collection.  
  
 Vous pouvez supprimer des éléments d’un menu contextuel de manière permanente. Toutefois, au moment de l’exécution, il peut être plus approprié de masquer ou de désactiver les éléments à la place.  
  
> [!IMPORTANT]
> Bien <xref:System.Windows.Forms.MenuStrip> que <xref:System.Windows.Forms.ContextMenuStrip> et remplacent et ajoutent des <xref:System.Windows.Forms.ContextMenu> fonctionnalités aux contrôles et des <xref:System.Windows.Forms.MainMenu> versions <xref:System.Windows.Forms.ContextMenu> antérieures, et sont conservés pour la <xref:System.Windows.Forms.MainMenu> compatibilité descendante et l’utilisation future si tel est votre choix.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Pour supprimer des éléments d’un menu contextuel  
  
1. Utilisez la <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> méthode <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> <xref:System.Windows.Forms.Menu.MenuItems%2A> ou<xref:System.Windows.Forms.ContextMenu> de la collection du composant pour supprimer un élément de menu particulier.  
  
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
  
     ou  
  
2. Utilisez la `Clear` méthode de la `MenuItems` collection du <xref:System.Windows.Forms.ContextMenu> composant pour supprimer tous les éléments du menu.  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ContextMenu>
- [ContextMenu, composant](contextmenu-component-windows-forms.md)
- [Vue d'ensemble du composant ContextMenu](contextmenu-component-overview-windows-forms.md)
