---
title: 'Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStrip control [Windows Forms], custom rendering
- toolbars [Windows Forms], rendering
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], rendering
ms.assetid: 88a804ba-679f-4ba3-938a-0dc396199c5b
ms.openlocfilehash: ad5ced42754fba6a714452220dd824c4f54fb5e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743408"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms
les contrôles <xref:System.Windows.Forms.ToolStrip> offrent un support facile pour les thèmes et les styles. Vous pouvez obtenir une apparence et un comportement entièrement personnalisés (apparence) en affectant à la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> ou à la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> la valeur d’un convertisseur personnalisé.  
  
 Vous pouvez assigner des convertisseurs à chaque <xref:System.Windows.Forms.ToolStrip>individuel, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.ContextMenuStrip>ou <xref:System.Windows.Forms.StatusStrip> contrôle, ou vous pouvez utiliser la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> pour affecter tous les objets en affectant à la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> la valeur <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> retourne <xref:System.Windows.Forms.ToolStripRenderMode.Custom> uniquement si la valeur de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> n’est pas `null`.  
  
### <a name="to-create-a-custom-renderer"></a>Pour créer un convertisseur personnalisé  
  
1. Étendez la classe <xref:System.Windows.Forms.ToolStripRenderer>.  
  
2. Implémentez le rendu personnalisé souhaité en remplaçant *le approprié sur...* membres  
  
    ```vb  
    Public Class RedTextRenderer  
        Inherits System.Windows.Forms.ToolStripRenderer  
        Protected Overrides Sub OnRenderItemText(ByVal e As _  
            ToolStripItemTextRenderEventArgs)   
            e.TextColor = Color.Red  
            e.TextFont = New Font("Helvetica", 7, FontStyle.Bold)  
            MyBase.OnRenderItemText(e)  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    public class RedTextRenderer : _  
        System.Windows.Forms.ToolStripRenderer  
    {  
        protected override void _  
            OnRenderItemText(ToolStripItemTextRenderEventArgs e)  
        {  
            e.TextColor = Color.Red;  
            e.TextFont = new Font("Helvetica", 7, FontStyle.Bold);  
           base.OnRenderItemText(e);  
        }  
    }  
    ```  
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Pour définir le convertisseur personnalisé comme le convertisseur actuel  
  
1. Pour définir le convertisseur personnalisé pour une <xref:System.Windows.Forms.ToolStrip>, définissez la propriété <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> sur le convertisseur personnalisé.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Ou pour définir le convertisseur personnalisé pour toutes les classes <xref:System.Windows.Forms.ToolStrip> contenues dans votre application : définissez la propriété <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> sur le convertisseur personnalisé et définissez la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> sur <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
    ```vb  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode  
    ToolStripManager.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.RenderMode = ToolStripRenderMode.ManagerRenderMode;  
    ToolStripManager.Renderer = new RedTextRenderer();  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStripManager.Renderer%2A>
- <xref:System.Windows.Forms.ToolStripRenderer>
- <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Architecture du contrôle ToolStrip](toolstrip-control-architecture.md)
- [Résumé de la technologie ToolStrip](toolstrip-technology-summary.md)
