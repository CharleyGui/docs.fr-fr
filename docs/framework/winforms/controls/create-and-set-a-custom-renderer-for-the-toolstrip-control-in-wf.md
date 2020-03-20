---
title: 'Comment : Créer et définir un rendu personnalisé pour le contrôle ToolStrip'
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
ms.openlocfilehash: 49db0d785155f19b7220ac64011eaf4253aaa7e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182405"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Comment : créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans les Windows Forms
<xref:System.Windows.Forms.ToolStrip>les contrôles donnent un soutien facile aux thèmes et aux styles. Vous pouvez atteindre l’apparence et le comportement complètement <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> personnalisés <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> (regardez et sentez) en définissant soit la propriété ou la propriété à un rendu personnalisé.  
  
 Vous pouvez attribuer des <xref:System.Windows.Forms.ToolStrip>rendus <xref:System.Windows.Forms.MenuStrip> <xref:System.Windows.Forms.ContextMenuStrip>à <xref:System.Windows.Forms.StatusStrip> chaque individu, , <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> , ou le contrôle, <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> ou <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>vous pouvez utiliser la propriété pour affecter tous les objets en définissant la propriété à .  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>rendements <xref:System.Windows.Forms.ToolStripRenderMode.Custom> seulement si <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> la `null`valeur de n’est pas .  
  
### <a name="to-create-a-custom-renderer"></a>Pour créer un rendu personnalisé  
  
1. Prolongez <xref:System.Windows.Forms.ToolStripRenderer> la classe.  
  
2. Implémentez le rendu personnalisé souhaité en dominant approprié *on...* membres  
  
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
  
### <a name="to-set-the-custom-renderer-to-be-the-current-renderer"></a>Pour définir le rendu personnalisé pour être le rendu actuel  
  
1. Pour définir le rendu <xref:System.Windows.Forms.ToolStrip>personnalisé pour <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> un, définissez la propriété sur le rendu personnalisé.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Ou pour définir le rendu <xref:System.Windows.Forms.ToolStrip> personnalisé pour toutes les <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> classes contenues dans votre <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> application: Réglez la propriété au rendu personnalisé et définissez la propriété à <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
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
