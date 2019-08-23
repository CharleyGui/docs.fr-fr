---
title: 'Procédure : créer et définir un renderer personnalisé pour le contrôle ToolStrip dans Windows Forms'
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
ms.openlocfilehash: c354ace3a7d3ce43f549dd1295a85fbee004eb22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929741"
---
# <a name="how-to-create-and-set-a-custom-renderer-for-the-toolstrip-control-in-windows-forms"></a>Procédure : créer et définir un renderer personnalisé pour le contrôle ToolStrip dans Windows Forms
<xref:System.Windows.Forms.ToolStrip>les contrôles offrent un support facile pour les thèmes et les styles. Vous pouvez obtenir une apparence et un comportement entièrement personnalisés (apparence) en affectant à <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> la propriété ou <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> à la propriété un convertisseur personnalisé.  
  
 Vous pouvez assigner des convertisseurs <xref:System.Windows.Forms.ToolStrip>à <xref:System.Windows.Forms.MenuStrip>chaque <xref:System.Windows.Forms.ContextMenuStrip>contrôle individuel <xref:System.Windows.Forms.StatusStrip> ,, ou, ou vous pouvez <xref:System.Windows.Forms.ToolStripManager.Renderer%2A> utiliser la propriété pour affecter tous les objets <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> en affectant à <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode?displayProperty=nameWithType>la propriété la valeur.  
  
> [!NOTE]
> <xref:System.Windows.Forms.ToolStrip.RenderMode%2A>retourne <xref:System.Windows.Forms.ToolStripRenderMode.Custom> uniquement si la valeur de <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> n’est `null`pas.  
  
### <a name="to-create-a-custom-renderer"></a>Pour créer un convertisseur personnalisé  
  
1. Étendez <xref:System.Windows.Forms.ToolStripRenderer> la classe.  
  
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
  
1. Pour définir le convertisseur personnalisé pour un <xref:System.Windows.Forms.ToolStrip>, définissez la <xref:System.Windows.Forms.ToolStrip.Renderer%2A?displayProperty=nameWithType> propriété sur le convertisseur personnalisé.  
  
    ```vb  
    toolStrip1.Renderer = New RedTextRenderer()  
    ```  
  
    ```csharp  
    toolStrip1.Renderer = new RedTextRenderer();  
    ```  
  
2. Ou pour définir le convertisseur personnalisé pour toutes les <xref:System.Windows.Forms.ToolStrip> classes contenues dans votre application: Définissez la <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>propriété sur le convertisseur personnalisé et affectez à la propriété la valeur. <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType>  
  
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
