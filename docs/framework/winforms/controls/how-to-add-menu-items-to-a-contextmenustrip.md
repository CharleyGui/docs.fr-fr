---
title: 'Procédure : ajouter des éléments de menu à un ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrips [Windows Forms], adding menu items
- shortcut menus [Windows Forms], adding items
- context menus [Windows Forms], adding menu items
ms.assetid: 1ec14776-3ea2-4752-bd22-4fae0fd19e1a
ms.openlocfilehash: 85729082d34cc976fabdbc50629b528c5f28cf54
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624087"
---
# <a name="how-to-add-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="61a6e-102">Procédure : ajouter des éléments de menu à un ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="61a6e-102">How to: Add Menu Items to a ContextMenuStrip</span></span>
<span data-ttu-id="61a6e-103">Vous pouvez ajouter simplement un élément de menu ou de plusieurs éléments à la fois pour un <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="61a6e-103">You can add just one menu item or several items at a time to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
### <a name="to-add-a-single-menu-item-to-a-contextmenustrip"></a><span data-ttu-id="61a6e-104">Pour ajouter un seul élément de menu à un ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="61a6e-104">To add a single menu item to a ContextMenuStrip</span></span>  
  
- <span data-ttu-id="61a6e-105">Utilisez le <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> méthode pour ajouter un élément de menu à un <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="61a6e-105">Use the <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> method to add one menu item to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.Add(Me.toolStripMenuItem1)  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.Add(toolStripMenuItem1);  
    ```  
  
### <a name="to-add-several-menu-items-to-a-contextmenustrip"></a><span data-ttu-id="61a6e-106">Pour ajouter plusieurs éléments de menu à un ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="61a6e-106">To add several menu items to a ContextMenuStrip</span></span>  
  
- <span data-ttu-id="61a6e-107">Utilisez le <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> méthode pour ajouter plusieurs éléments de menu à un <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="61a6e-107">Use the <xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A> method to add several menu items to a <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>  
  
    ```vb  
    Me.contextMenuStrip1.Items.AddRange(New _  
       System.Windows.Forms.ToolStripItem() {Me.toolStripMenuItem1, _  
          Me.toolStripMenuItem2})  
    ```  
  
    ```csharp  
    this.contextMenuStrip1.Items.AddRange(new   
       System.Windows.Forms.ToolStripItem[] {  
          this.toolStripMenuItem1, this.toolStripMenuItem2});  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="61a6e-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="61a6e-108">See also</span></span>

- [<span data-ttu-id="61a6e-109">ContextMenuStrip, contrôle</span><span class="sxs-lookup"><span data-stu-id="61a6e-109">ContextMenuStrip Control</span></span>](contextmenustrip-control.md)
