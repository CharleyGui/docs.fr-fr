---
title: Mappage de propriétés Windows Forms et WPF
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: ae4a97bc96a4f9e93942b4995f488c427fda3134
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917498"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mappage de propriétés Windows Forms et WPF
Les [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] technologies [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et ont deux modèles de propriété similaires mais différents. Le *mappage de propriété* prend en charge l’interopérabilité entre les deux architectures et fournit les fonctionnalités suivantes:  
  
- Facilite le mappage des modifications de propriétés pertinentes dans l’environnement hôte vers le contrôle ou l’élément hébergé.  
  
- Fournit la gestion par défaut pour le mappage des propriétés les plus couramment utilisées.  
  
- Permet une suppression, une substitution ou une extension aisée des propriétés par défaut.  
  
- Garantit que les modifications apportées aux valeurs de propriété sur l’hôte sont automatiquement détectées et traduites dans le contrôle ou l’élément hébergé.  
  
> [!NOTE]
> Les événements de modification de propriété ne sont pas propagés vers le haut du contrôle d’hébergement ou la hiérarchie d’éléments. La traduction de propriété n’est pas effectuée si la valeur locale d’une propriété ne change pas en raison de la définition directe, de styles, d’héritage, de liaison de données ou d’autres mécanismes qui modifient la valeur de la propriété.  
  
 Utilisez la <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> propriété sur l' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément et la <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> propriété sur <xref:System.Windows.Forms.Integration.ElementHost> le contrôle pour accéder au mappage de propriété.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mappage de propriété avec l’élément WindowsFormsHost  
 L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément traduit les propriétés par [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] défaut en leurs [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] équivalents à l’aide de la table de traduction suivante.  
  
|Hébergement Windows Presentation Foundation|Windows Forms|Comportement d’interopérabilité|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|L' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément définit la <xref:System.Windows.Forms.Control.BackColor%2A> propriété du contrôle hébergé et la <xref:System.Windows.Forms.Control.BackgroundImage%2A> propriété du contrôle hébergé. Le mappage est effectué à l’aide des règles suivantes:<br /><br /> -Si <xref:System.Windows.Controls.Control.Background%2A> est une couleur unie, elle est convertie et utilisée pour <xref:System.Windows.Forms.Control.BackColor%2A> définir la propriété du contrôle hébergé. La <xref:System.Windows.Forms.Control.BackColor%2A> propriété n’est pas définie sur le contrôle hébergé, car le contrôle hébergé peut hériter de la <xref:System.Windows.Forms.Control.BackColor%2A> valeur de la propriété. **Remarque :**  Le contrôle hébergé ne prend pas en charge la transparence. Toute couleur assignée à <xref:System.Windows.Forms.Control.BackColor%2A> doit être entièrement opaque, avec une valeur alpha de 0xFF. <br /><br /> -Si <xref:System.Windows.Controls.Control.Background%2A> n’est pas une couleur unie, <xref:System.Windows.Forms.Integration.WindowsFormsHost> le contrôle crée une image bitmap <xref:System.Windows.Controls.Control.Background%2A> à partir de la propriété. Le <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle assigne cette image bitmap à <xref:System.Windows.Forms.Control.BackgroundImage%2A> la propriété du contrôle hébergé. Cela donne un effet similaire à la transparence. **Remarque :**  Vous pouvez remplacer ce comportement ou vous pouvez supprimer le mappage <xref:System.Windows.Controls.Control.Background%2A> de propriété.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Si le mappage par défaut n’a pas été réassigné, <xref:System.Windows.Forms.Integration.WindowsFormsHost> le contrôle parcourt sa hiérarchie ancêtre jusqu’à ce qu’il trouve un ancêtre dont la <xref:System.Windows.FrameworkElement.Cursor%2A> propriété est définie. Cette valeur est convertie vers le curseur [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] correspondant le plus proche.<br /><br /> Si le mappage par défaut de <xref:System.Windows.FrameworkElement.ForceCursor%2A> la propriété n’a pas été réassigné, le parcours s’arrête sur le premier <xref:System.Windows.FrameworkElement.ForceCursor%2A> ancêtre avec `true`la valeur.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight>est mappé <xref:System.Windows.Forms.RightToLeft.No>à.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft>est mappé <xref:System.Windows.Forms.RightToLeft.Yes>à.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit>n’est pas mappé.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType>est mappé <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>à.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A>sur le du contrôle hébergé<xref:System.Drawing.Font?displayProperty=nameWithType>|Le jeu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés est traduit en un correspondant <xref:System.Drawing.Font>. Quand l’une de ces propriétés change, une <xref:System.Drawing.Font> nouvelle est créée. Pour <xref:System.Windows.FontStyles.Normal%2A> :<xref:System.Drawing.FontStyle.Italic> est désactivé. Pour <xref:System.Windows.FontStyles.Italic%2A> ou <xref:System.Windows.FontStyles.Oblique%2A> :<xref:System.Drawing.FontStyle.Italic> est activé.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A>sur le du contrôle hébergé<xref:System.Drawing.Font?displayProperty=nameWithType>|Le jeu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés est traduit en un correspondant <xref:System.Drawing.Font>. Quand l’une de ces propriétés change, une <xref:System.Drawing.Font> nouvelle est créée. Pour <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A> ,<xref:System.Windows.FontWeights.Heavy%2A> ,,<xref:System.Drawing.FontStyle.Bold> ,, ,ou<xref:System.Windows.FontWeights.UltraBold%2A>: est activé. <xref:System.Windows.FontWeights.SemiBold%2A> <xref:System.Windows.FontWeights.DemiBold%2A> <xref:System.Windows.FontWeights.ExtraBold%2A> <xref:System.Windows.FontWeights.Medium%2A> Pour <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, ,,<xref:System.Windows.FontWeights.Normal%2A>, ou<xref:System.Drawing.FontStyle.Bold> : estdésactivé.<xref:System.Windows.FontWeights.UltraLight%2A> <xref:System.Windows.FontWeights.Regular%2A> <xref:System.Windows.FontWeights.Thin%2A>|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|Le jeu de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] propriétés est traduit en un correspondant <xref:System.Drawing.Font>. Quand l’une de ces propriétés change, une <xref:System.Drawing.Font> nouvelle est créée. Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est redimensionné en fonction de la taille de police.<br /><br /> La taille de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] police dans est exprimée sous la forme d’un de 90-sixième [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] de pouce, et en tant qu’une sec. La conversion correspondante est la suivante:<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]taille de police [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] = taille de police * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Le <xref:System.Windows.Controls.Control.Foreground%2A> mappage de propriété est effectué à l’aide des règles suivantes:<br /><br /> -Si <xref:System.Windows.Controls.Control.Foreground%2A> est un <xref:System.Windows.Media.SolidColorBrush>, utilisez <xref:System.Windows.Media.SolidColorBrush.Color%2A> pour <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Si <xref:System.Windows.Controls.Control.Foreground%2A> est un <xref:System.Windows.Media.GradientBrush>, <xref:System.Windows.Media.GradientStop> utilisez la couleur du avec la valeur de décalage la plus <xref:System.Windows.Forms.Control.ForeColor%2A>basse pour.<br />-Pour tout autre <xref:System.Windows.Media.Brush> type, laissez <xref:System.Windows.Forms.Control.ForeColor%2A> inchangé. Cela signifie que la valeur par défaut est utilisée.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Lorsque <xref:System.Windows.UIElement.IsEnabled%2A> est défini, <xref:System.Windows.Forms.Integration.WindowsFormsHost> l’élément définit <xref:System.Windows.Forms.Control.Enabled%2A> la propriété sur le contrôle hébergé.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Les quatre valeurs de la <xref:System.Windows.Forms.Control.Padding%2A> propriété sur le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé sont définies sur la même <xref:System.Windows.Thickness> valeur.<br /><br /> -Les valeurs supérieures <xref:System.Int32.MaxValue> à sont définies <xref:System.Int32.MaxValue>sur.<br />-Les valeurs inférieures <xref:System.Int32.MinValue> à sont définies <xref:System.Int32.MinValue>sur.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible>est mappé <xref:System.Windows.Forms.Control.Visible%2A>à  =  .`true` Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est visible. Il n’est <xref:System.Windows.Forms.Control.Visible%2A> pas recommandé d’affecter explicitement la `false` valeur à la propriété du contrôle hébergé.<br />-   <xref:System.Windows.Visibility.Collapsed>est mappé <xref:System.Windows.Forms.Control.Visible%2A>  =  à ou`true` . `false` Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé n’est pas dessiné et sa zone est réduite.<br />-   <xref:System.Windows.Visibility.Hidden> : Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé occupe de l’espace dans la disposition, mais n’est pas visible. Dans ce cas, la <xref:System.Windows.Forms.Control.Visible%2A> propriété a la `true`valeur. Il n’est <xref:System.Windows.Forms.Control.Visible%2A> pas recommandé d’affecter explicitement la `false` valeur à la propriété du contrôle hébergé.|  
  
 Les propriétés jointes sur les éléments de conteneur sont <xref:System.Windows.Forms.Integration.WindowsFormsHost> entièrement prises en charge par l’élément.  
  
 Pour plus d’informations, consultez [Procédure pas à pas : Mappage des propriétés à l’aide](walkthrough-mapping-properties-using-the-windowsformshost-element.md)de l’élément WindowsFormsHost.  
  
## <a name="updates-to-parent-properties"></a>Mises à jour des propriétés parentes  
 Les modifications apportées à la plupart des propriétés parentes provoquent des notifications au contrôle enfant hébergé. La liste suivante décrit les propriétés qui n’entraînent pas de notifications lorsque leurs valeurs changent.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Par exemple, si vous modifiez la valeur de la <xref:System.Windows.Controls.Control.Background%2A> propriété de l' <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément, la <xref:System.Windows.Forms.Control.BackColor%2A> propriété du contrôle hébergé ne change pas.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mappage de propriété avec le contrôle ElementHost  
 Les propriétés suivantes fournissent une notification de modification intégrée. N’appelez pas la <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> méthode lorsque vous mappez ces propriétés:  
  
- AutoSize  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- Curseur  
  
- Station d' accueil  
  
- activé  
  
- Police  
  
- ForeColor  
  
- Lieu  
  
- Marge  
  
- Padding  
  
- Parent  
  
- Région  
  
- RightToLeft  
  
- Taille  
  
- TabIndex  
  
- Tabulation  
  
- Text  
  
- Visible  
  
 Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle traduit les propriétés par [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] défaut en leurs [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] équivalents à l’aide de la table de traduction suivante.  
  
 Pour plus d’informations, consultez [Procédure pas à pas : Mappage des propriétés à l’aide](walkthrough-mapping-properties-using-the-elementhost-control.md)du contrôle ElementHost.  
  
|Hébergement Windows Forms|Windows Presentation Foundation|Comportement d’interopérabilité|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|La définition de cette propriété force un redessine <xref:System.Windows.Media.ImageBrush>avec un. Si la <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> propriété est définie sur `false` (valeur par défaut), elle <xref:System.Windows.Media.ImageBrush> est basée sur l’apparence du <xref:System.Windows.Forms.Integration.ElementHost> contrôle, y compris ses <xref:System.Windows.Forms.Control.BackColor%2A>propriétés <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> , et toute peinture attachée gestionnaires d'.<br /><br /> Si la <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> propriété a la `true`valeur, le <xref:System.Windows.Media.ImageBrush> est basé sur l’apparence du <xref:System.Windows.Forms.Integration.ElementHost> parent du contrôle, y compris les <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> propriétés du <xref:System.Windows.Forms.Control.BackColor%2A>parent <xref:System.Windows.Forms.Control.BackgroundImage%2A>,, et toute peinture attachée gestionnaires d'.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|La définition de cette propriété entraîne le même comportement que <xref:System.Windows.Forms.Control.BackColor%2A> celui décrit pour le mappage.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|La définition de cette propriété entraîne le même comportement que <xref:System.Windows.Forms.Control.BackColor%2A> celui décrit pour le mappage.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] curseur standard est converti en curseur standard [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] correspondant. Si le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] n’est pas un curseur standard, la valeur par défaut est assignée.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Lorsque <xref:System.Windows.Forms.Control.Enabled%2A> est défini, le <xref:System.Windows.Forms.Integration.ElementHost> contrôle définit la <xref:System.Windows.UIElement.IsEnabled%2A> propriété sur l’élément hébergé.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|La <xref:System.Windows.Forms.Control.Font%2A> valeur est convertie en un ensemble [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de propriétés de police correspondant.|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A>sur un élément hébergé|Si <xref:System.Drawing.Font.Bold%2A> a la valeur `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> a la valeur <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Si <xref:System.Drawing.Font.Bold%2A> a la valeur `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> a la valeur <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A>sur un élément hébergé|Si <xref:System.Drawing.Font.Italic%2A> a la valeur `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> a la valeur <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Si <xref:System.Drawing.Font.Italic%2A> a la valeur `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> a la valeur <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations>sur un élément hébergé|S’applique uniquement lors de <xref:System.Windows.Controls.TextBlock> l’hébergement d’un contrôle.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations>sur un élément hébergé|S’applique uniquement lors de <xref:System.Windows.Controls.TextBlock> l’hébergement d’un contrôle.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No>est mappé <xref:System.Windows.FlowDirection.LeftToRight>à.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes>est mappé <xref:System.Windows.FlowDirection.RightToLeft>à.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|Le <xref:System.Windows.Forms.Integration.ElementHost> contrôle définit la <xref:System.Windows.UIElement.Visibility%2A> propriété sur l’élément hébergé à l’aide des règles suivantes:<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true`est mappé <xref:System.Windows.Visibility.Visible>à.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false`est mappé <xref:System.Windows.Visibility.Hidden>à.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
- [Interopérabilité WPF et Windows Forms](wpf-and-windows-forms-interoperation.md)
- [Procédure pas à pas : Mappage de propriétés à l’aide de l’élément WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Procédure pas à pas : Mappage de propriétés à l’aide du contrôle ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md)
