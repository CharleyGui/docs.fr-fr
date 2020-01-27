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
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>Comment : ajouter et supprimer des éléments de menu avec le composant ContextMenu Windows Forms
Explique comment ajouter et supprimer des éléments de menu contextuel dans Windows Forms.  
  
 Le composant Windows Forms <xref:System.Windows.Forms.ContextMenu> fournit un menu de commandes fréquemment utilisées qui s’appliquent à l’objet sélectionné. Vous pouvez ajouter des éléments au menu contextuel en ajoutant des objets <xref:System.Windows.Forms.MenuItem> à la collection <xref:System.Windows.Forms.Menu.MenuItems%2A>.  
  
 Vous pouvez supprimer des éléments d’un menu contextuel de manière permanente. Toutefois, au moment de l’exécution, il peut être plus approprié de masquer ou de désactiver les éléments à la place.  
  
> [!IMPORTANT]
> Bien que <xref:System.Windows.Forms.MenuStrip> et <xref:System.Windows.Forms.ContextMenuStrip> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.MainMenu> et <xref:System.Windows.Forms.ContextMenu> des versions précédentes, <xref:System.Windows.Forms.MainMenu> et les <xref:System.Windows.Forms.ContextMenu> sont conservés pour la compatibilité descendante et l’utilisation future si vous le souhaitez.  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>Pour supprimer des éléments d’un menu contextuel  
  
1. Utilisez la méthode <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> ou <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> de la collection <xref:System.Windows.Forms.Menu.MenuItems%2A> du composant <xref:System.Windows.Forms.ContextMenu> pour supprimer un élément de menu particulier.  
  
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
  
     \- ou -  
  
2. Utilisez la méthode `Clear` de la collection `MenuItems` du composant <xref:System.Windows.Forms.ContextMenu> pour supprimer tous les éléments du menu.  
  
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
