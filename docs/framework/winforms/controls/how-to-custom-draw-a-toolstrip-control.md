---
title: 'Procédure : personnaliser le dessin d’un contrôle ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], custom drawing
- drawing [Windows Forms], owner
- ProfessionalColorTable class [Windows Forms], overriding
- examples [Windows Forms], toolbars
- drawing [Windows Forms], custom
- toolbars [Windows Forms], changing colors
- ToolStrip control [Windows Forms], drawing
- ToolStrip control [Windows Forms], changing colors
- custom drawing
- owner drawing
ms.assetid: 94e7d7bd-a752-441c-b5b3-7acf98881163
ms.openlocfilehash: 810a680a1a9d9065e80ed87453a728fe628a953d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935366"
---
# <a name="how-to-custom-draw-a-toolstrip-control"></a>Procédure : personnaliser le dessin d’un contrôle ToolStrip
Les contrôles <xref:System.Windows.Forms.ToolStrip> disposent des classes de rendu (peinture) associées suivantes :  
  
- <xref:System.Windows.Forms.ToolStripSystemRenderer> fournit l'apparence et le style de votre système d'exploitation.  
  
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer> fournit l'apparence et le style de Microsoft Office.  
  
- <xref:System.Windows.Forms.ToolStripRenderer> est la classe de base abstraite pour les deux autres classes de rendu.  
  
 Pour le dessin personnalisé (également appelé Owner Draw) d'un <xref:System.Windows.Forms.ToolStrip>, vous pouvez substituer l'une des classes du convertisseur et modifier un aspect de la logique de rendu.  
  
 Les procédures suivantes décrivent divers aspects du dessin personnalisé.  
  
### <a name="to-switch-between-the-provided-renderers"></a>Pour basculer entre les convertisseurs fournis  
  
- Affectez à la propriété <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> la valeur <xref:System.Windows.Forms.ToolStripRenderMode> souhaitée.  
  
     Avec <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>, la propriété statique <xref:System.Windows.Forms.ToolStrip.RenderMode%2A> détermine le convertisseur pour votre application. Les autres valeurs de <xref:System.Windows.Forms.ToolStripRenderMode> sont <xref:System.Windows.Forms.ToolStripRenderMode.Custom>, <xref:System.Windows.Forms.ToolStripRenderMode.Professional> et <xref:System.Windows.Forms.ToolStripRenderMode.System>.  
  
### <a name="to-change-the-microsoft-officestyle-borders-to-straight"></a>Pour appliquer des bordures de style Microsoft Office droites  
  
- Substituez <xref:System.Windows.Forms.ToolStripProfessionalRenderer.OnRenderToolStripBorder%2A?displayProperty=nameWithType>, mais n'appelez pas la classe de base.  
  
> [!NOTE]
> Il existe une version de cette méthode pour <xref:System.Windows.Forms.ToolStripRenderer>, <xref:System.Windows.Forms.ToolStripSystemRenderer> et <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
### <a name="to-change-the-professionalcolortable"></a>Pour modifier ProfessionalColorTable  
  
- Substituez <xref:System.Windows.Forms.ProfessionalColorTable> et modifiez les couleurs de votre choix.  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As _  
    System.EventArgs) Handles Me.Load  
        Dim t As MyColorTable = New MyColorTable  
        ToolStrip1.Renderer = New ToolStripProfessionalRenderer(t)  
    End Sub  
  
    Class MyColorTable   
    Inherits ProfessionalColorTable  
  
    Public Overrides ReadOnly Property ButtonPressedGradientBegin() As Color  
        Get  
            Return Color.Red  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientMiddle() _  
    As System.Drawing.Color  
        Get  
            Return Color.Blue  
        End Get  
            End Property  
  
    Public Overrides ReadOnly Property ButtonPressedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Green  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientBegin() _  
    As Color  
        Get  
            Return Color.Yellow  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientMiddle() As System.Drawing.Color  
        Get  
            Return Color.Orange  
        End Get  
    End Property  
  
    Public Overrides ReadOnly Property ButtonSelectedGradientEnd() _  
    As System.Drawing.Color  
        Get  
            Return Color.Violet  
        End Get  
    End Property  
    End Class  
    ```  
  
### <a name="to-change-the-rendering-for-all-toolstrip-controls-in-your-application"></a>Pour modifier le rendu de tous les contrôles ToolStrip dans votre application  
  
1. Utilisez la propriété <xref:System.Windows.Forms.ToolStripManager.RenderMode%2A?displayProperty=nameWithType> pour choisir l'un des convertisseurs fournis.  
  
2. Utilisez <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> pour assigner un convertisseur personnalisé.  
  
3. Vérifiez que <xref:System.Windows.Forms.ToolStrip.RenderMode%2A?displayProperty=nameWithType> a la valeur par défaut de <xref:System.Windows.Forms.ToolStripRenderMode.ManagerRenderMode>.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-the-entire-application"></a>Pour désactiver les couleurs Microsoft Office pour l'application entière  
  
- Réglez <xref:System.Windows.Forms.ToolStripManager.VisualStylesEnabled%2A?displayProperty=nameWithType> sur `false`.  
  
### <a name="to-turn-off-the-microsoft-office-colors-for-one-toolstrip-control"></a>Pour désactiver les couleurs Microsoft Office pour un contrôle ToolStrip  
  
- Utilisez du code semblable à l'exemple suivant.  
  
    ```vb  
    Dim colorTable As ProfessionalColorTable()  
    colorTable.UseSystemColors = True  
    Dim toolStrip.Renderer As ToolStripProfessionalRenderer(colorTable)  
    ```  
  
    ```csharp  
    ProfessionalColorTable colorTable = new ProfessionalColorTable();  
    colorTable.UseSystemColors = true;  
    toolStrip.Renderer = new ToolStripProfessionalRenderer(colorTable);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolStripSystemRenderer>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- <xref:System.Windows.Forms.ToolStripRenderer>
- [Contrôles avec prise en charge intégrée du dessin owner-drawn](controls-with-built-in-owner-drawing-support.md)
- [Guide pratique pour Créer et définir un convertisseur personnalisé pour le contrôle ToolStrip dans Windows Forms](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)
- [Vue d’ensemble du contrôle ToolStrip](toolstrip-control-overview-windows-forms.md)
