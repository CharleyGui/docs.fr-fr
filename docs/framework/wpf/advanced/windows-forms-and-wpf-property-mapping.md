---
title: Mappage de propriétés Windows Forms et WPF
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- property mapping [WPF interoperability]
- Windows Forms [WPF], interoperability with
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- WindowsFormsHost element property mapping [WPF]
ms.assetid: 999d8298-9c04-467d-a453-86e41002057d
ms.openlocfilehash: 07e58f87d886212426e25be83f988037549ab642
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76735235"
---
# <a name="windows-forms-and-wpf-property-mapping"></a>Mappage de propriétés Windows Forms et WPF
Les technologies [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ont deux modèles de propriété similaires mais différents. Le *mappage de propriété* prend en charge l’interopérabilité entre les deux architectures et fournit les fonctionnalités suivantes :  
  
- Facilite le mappage des modifications de propriétés pertinentes dans l’environnement hôte vers le contrôle ou l’élément hébergé.  
  
- Fournit la gestion par défaut pour le mappage des propriétés les plus couramment utilisées.  
  
- Permet une suppression, une substitution ou une extension aisée des propriétés par défaut.  
  
- Garantit que les modifications apportées aux valeurs de propriété sur l’hôte sont automatiquement détectées et traduites dans le contrôle ou l’élément hébergé.  
  
> [!NOTE]
> Les événements de modification de propriété ne sont pas propagés vers le haut du contrôle d’hébergement ou la hiérarchie d’éléments. La traduction de propriété n’est pas effectuée si la valeur locale d’une propriété ne change pas en raison de la définition directe, de styles, d’héritage, de liaison de données ou d’autres mécanismes qui modifient la valeur de la propriété.  
  
 Utilisez la propriété <xref:System.Windows.Forms.Integration.WindowsFormsHost.PropertyMap%2A> sur l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> et la propriété <xref:System.Windows.Forms.Integration.ElementHost.PropertyMap%2A> sur <xref:System.Windows.Forms.Integration.ElementHost> contrôle pour accéder au mappage de propriété.  
  
## <a name="property-mapping-with-the-windowsformshost-element"></a>Mappage de propriété avec l’élément WindowsFormsHost  
 L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> traduit les propriétés de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] par défaut en leurs équivalents [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] à l’aide de la table de traduction suivante.  
  
|Hébergement Windows Presentation Foundation|Windows Forms|Comportement d’interopérabilité|  
|---------------------------------------------|-------------------|-----------------------------|  
|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|L’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost> définit la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du contrôle hébergé et la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du contrôle hébergé. Le mappage est effectué à l’aide des règles suivantes :<br /><br /> -Si <xref:System.Windows.Controls.Control.Background%2A> est une couleur unie, elle est convertie et utilisée pour définir la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du contrôle hébergé. La propriété <xref:System.Windows.Forms.Control.BackColor%2A> n’est pas définie sur le contrôle hébergé, car le contrôle hébergé peut hériter de la valeur de la propriété <xref:System.Windows.Forms.Control.BackColor%2A>. **Remarque :**  Le contrôle hébergé ne prend pas en charge la transparence. Toute couleur assignée à <xref:System.Windows.Forms.Control.BackColor%2A> doit être entièrement opaque, avec une valeur alpha de 0xFF. <br /><br /> -Si <xref:System.Windows.Controls.Control.Background%2A> n’est pas une couleur unie, le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> crée une image bitmap à partir de la propriété <xref:System.Windows.Controls.Control.Background%2A>. Le contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> assigne cette image bitmap à la propriété <xref:System.Windows.Forms.Control.BackgroundImage%2A> du contrôle hébergé. Cela donne un effet similaire à la transparence. **Remarque :**  Vous pouvez remplacer ce comportement ou supprimer le mappage de propriété <xref:System.Windows.Controls.Control.Background%2A>.|  
|<xref:System.Windows.FrameworkElement.Cursor%2A>|<xref:System.Windows.Forms.Control.Cursor%2A>|Si le mappage par défaut n’a pas été réassigné, <xref:System.Windows.Forms.Integration.WindowsFormsHost> contrôle parcourt sa hiérarchie ancêtre jusqu’à ce qu’il trouve un ancêtre avec sa propriété <xref:System.Windows.FrameworkElement.Cursor%2A> définie. Cette valeur est convertie vers le curseur de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] correspondant le plus proche.<br /><br /> Si le mappage par défaut de la propriété <xref:System.Windows.FrameworkElement.ForceCursor%2A> n’a pas été réassigné, le parcours s’arrête sur le premier ancêtre avec <xref:System.Windows.FrameworkElement.ForceCursor%2A> défini sur `true`.|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FlowDirection.LeftToRight> correspond à <xref:System.Windows.Forms.RightToLeft.No>.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft> correspond à <xref:System.Windows.Forms.RightToLeft.Yes>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Inherit> n’est pas mappé.<br /><br /> <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> correspond à <xref:System.Windows.Forms.RightToLeft.Yes?displayProperty=nameWithType>.|  
|<xref:System.Windows.Controls.Control.FontStyle%2A>|<xref:System.Drawing.Font.Style%2A> sur le <xref:System.Drawing.Font?displayProperty=nameWithType> du contrôle hébergé|L’ensemble des propriétés de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est traduit en <xref:System.Drawing.Font>correspondant. Quand l’une de ces propriétés change, un nouveau <xref:System.Drawing.Font> est créé. Pour <xref:System.Windows.FontStyles.Normal%2A>: <xref:System.Drawing.FontStyle.Italic> est désactivé. Pour <xref:System.Windows.FontStyles.Italic%2A> ou <xref:System.Windows.FontStyles.Oblique%2A>: <xref:System.Drawing.FontStyle.Italic> est activé.|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Drawing.Font.Style%2A> sur le <xref:System.Drawing.Font?displayProperty=nameWithType> du contrôle hébergé|L’ensemble des propriétés de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est traduit en <xref:System.Drawing.Font>correspondant. Quand l’une de ces propriétés change, un nouveau <xref:System.Drawing.Font> est créé. Pour <xref:System.Windows.FontWeights.Black%2A>, <xref:System.Windows.FontWeights.Bold%2A>, <xref:System.Windows.FontWeights.DemiBold%2A>, <xref:System.Windows.FontWeights.ExtraBold%2A>, <xref:System.Windows.FontWeights.Heavy%2A>, <xref:System.Windows.FontWeights.Medium%2A>, <xref:System.Windows.FontWeights.SemiBold%2A>ou <xref:System.Windows.FontWeights.UltraBold%2A>: <xref:System.Drawing.FontStyle.Bold> est activé. Pour <xref:System.Windows.FontWeights.ExtraLight%2A>, <xref:System.Windows.FontWeights.Light%2A>, <xref:System.Windows.FontWeights.Normal%2A>, <xref:System.Windows.FontWeights.Regular%2A>, <xref:System.Windows.FontWeights.Thin%2A>ou <xref:System.Windows.FontWeights.UltraLight%2A>: <xref:System.Drawing.FontStyle.Bold> est désactivé.|  
|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|L’ensemble des propriétés de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est traduit en <xref:System.Drawing.Font>correspondant. Quand l’une de ces propriétés change, un nouveau <xref:System.Drawing.Font> est créé. Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est redimensionné en fonction de la taille de la police.<br /><br /> La taille de police en [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est exprimée sous la forme d’un quatre-vingt-sixième de pouce, et en [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] sous la forme d’une unité de mesure de la sec. La conversion correspondante est la suivante :<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] taille de police = [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taille de police * 72,0/96,0.|  
|<xref:System.Windows.Controls.Control.Foreground%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>)|<xref:System.Windows.Forms.Control.ForeColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|Le mappage de propriété <xref:System.Windows.Controls.Control.Foreground%2A> est effectué à l’aide des règles suivantes :<br /><br /> -Si <xref:System.Windows.Controls.Control.Foreground%2A> est un <xref:System.Windows.Media.SolidColorBrush>, utilisez <xref:System.Windows.Media.SolidColorBrush.Color%2A> pour <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Si <xref:System.Windows.Controls.Control.Foreground%2A> est un <xref:System.Windows.Media.GradientBrush>, utilisez la couleur du <xref:System.Windows.Media.GradientStop> avec la valeur de décalage la plus basse pour <xref:System.Windows.Forms.Control.ForeColor%2A>.<br />-Pour tout autre type de <xref:System.Windows.Media.Brush>, laissez <xref:System.Windows.Forms.Control.ForeColor%2A> inchangé. Cela signifie que la valeur par défaut est utilisée.|  
|<xref:System.Windows.UIElement.IsEnabled%2A>|<xref:System.Windows.Forms.Control.Enabled%2A>|Lorsque <xref:System.Windows.UIElement.IsEnabled%2A> est définie, <xref:System.Windows.Forms.Integration.WindowsFormsHost> élément définit la propriété <xref:System.Windows.Forms.Control.Enabled%2A> sur le contrôle hébergé.|  
|<xref:System.Windows.Controls.Control.Padding%2A>|<xref:System.Windows.Forms.Control.Padding%2A>|Les quatre valeurs de la propriété <xref:System.Windows.Forms.Control.Padding%2A> sur le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé sont définies sur la même valeur de <xref:System.Windows.Thickness>.<br /><br /> -Les valeurs supérieures à <xref:System.Int32.MaxValue> sont définies sur <xref:System.Int32.MaxValue>.<br />-Les valeurs inférieures à <xref:System.Int32.MinValue> sont définies sur <xref:System.Int32.MinValue>.|  
|<xref:System.Windows.UIElement.Visibility%2A>|<xref:System.Windows.Forms.Control.Visible%2A>|-   <xref:System.Windows.Visibility.Visible> est mappé à <xref:System.Windows.Forms.Control.Visible%2A> = `true`. Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé est visible. Il n’est pas recommandé de définir explicitement la propriété <xref:System.Windows.Forms.Control.Visible%2A> sur le contrôle hébergé sur `false`.<br />-   <xref:System.Windows.Visibility.Collapsed> est mappé à <xref:System.Windows.Forms.Control.Visible%2A> = `true` ou `false`. Le contrôle [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé n’est pas dessiné, et sa zone est réduite.<br />-   <xref:System.Windows.Visibility.Hidden> : le contrôle de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hébergé occupe de l’espace dans la disposition, mais n’est pas visible. Dans ce cas, la propriété <xref:System.Windows.Forms.Control.Visible%2A> est définie sur `true`. Il n’est pas recommandé de définir explicitement la propriété <xref:System.Windows.Forms.Control.Visible%2A> sur le contrôle hébergé sur `false`.|  
  
 Les propriétés jointes sur les éléments de conteneur sont entièrement prises en charge par l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>.  
  
 Pour plus d’informations, consultez [procédure pas à pas : mappage de propriétés à l’aide de l’élément WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md).  
  
## <a name="updates-to-parent-properties"></a>Mises à jour des propriétés parentes  
 Les modifications apportées à la plupart des propriétés parentes provoquent des notifications au contrôle enfant hébergé. La liste suivante décrit les propriétés qui n’entraînent pas de notifications lorsque leurs valeurs changent.  
  
- <xref:System.Windows.Controls.Control.Background%2A>  
  
- <xref:System.Windows.FrameworkElement.Cursor%2A>  
  
- <xref:System.Windows.FrameworkElement.ForceCursor%2A>  
  
- <xref:System.Windows.UIElement.Visibility%2A>  
  
 Par exemple, si vous modifiez la valeur de la propriété <xref:System.Windows.Controls.Control.Background%2A> de l’élément <xref:System.Windows.Forms.Integration.WindowsFormsHost>, la propriété <xref:System.Windows.Forms.Control.BackColor%2A> du contrôle hébergé ne change pas.  
  
## <a name="property-mapping-with-the-elementhost-control"></a>Mappage de propriété avec le contrôle ElementHost  
 Les propriétés suivantes fournissent une notification de modification intégrée. N’appelez pas la méthode <xref:System.Windows.FrameworkElement.OnPropertyChanged%2A> lorsque vous mappez ces propriétés :  
  
- Redimensionner automatiquement  
  
- BackColor  
  
- BackgroundImage  
  
- BackgroundImageLayout  
  
- BindingContext  
  
- CausesValidation  
  
- ContextMenu  
  
- ContextMenuStrip  
  
- Curseur  
  
- Station d' accueil  
  
- Enabled  
  
- Police  
  
- ForeColor  
  
- Emplacement  
  
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
  
 Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> traduit les propriétés de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] par défaut en leurs équivalents [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] à l’aide de la table de traduction suivante.  
  
 Pour plus d’informations, consultez [procédure pas à pas : mappage de propriétés à l’aide du contrôle ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md).  
  
|Hébergement Windows Forms|Windows Presentation Foundation|Comportement d’interopérabilité|  
|---------------------------|-------------------------------------|-----------------------------|  
|<xref:System.Windows.Forms.Control.BackColor%2A><br /><br /> (<xref:System.Drawing.Color?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|La définition de cette propriété force un redessinement avec un <xref:System.Windows.Media.ImageBrush>. Si la propriété <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> est définie sur `false` (valeur par défaut), cette <xref:System.Windows.Media.ImageBrush> est basée sur l’apparence du contrôle <xref:System.Windows.Forms.Integration.ElementHost>, y compris ses <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> propriétés et tous les gestionnaires de peintures attachés.<br /><br /> Si la propriété <xref:System.Windows.Forms.Integration.ElementHost.BackColorTransparent%2A> est définie sur `true`, le <xref:System.Windows.Media.ImageBrush> est basé sur l’apparence du parent du contrôle <xref:System.Windows.Forms.Integration.ElementHost>, y compris les <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Control.BackgroundImageLayout%2A> et les gestionnaires de peintures du parent.|  
|<xref:System.Windows.Forms.Control.BackgroundImage%2A><br /><br /> (<xref:System.Drawing.Image?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|La définition de cette propriété entraîne le même comportement que celui décrit pour le mappage de <xref:System.Windows.Forms.Control.BackColor%2A>.|  
|<xref:System.Windows.Forms.Control.BackgroundImageLayout%2A>|<xref:System.Windows.Controls.Control.Background%2A><br /><br /> (<xref:System.Windows.Media.Brush?displayProperty=nameWithType>) sur l’élément hébergé|La définition de cette propriété entraîne le même comportement que celui décrit pour le mappage de <xref:System.Windows.Forms.Control.BackColor%2A>.|  
|<xref:System.Windows.Forms.Control.Cursor%2A><br /><br /> (<xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.Cursor%2A><br /><br /> (<xref:System.Windows.Input.Cursor?displayProperty=nameWithType>)|Le curseur de [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] standard est traduit en [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] curseur standard correspondant. Si le [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] n’est pas un curseur standard, la valeur par défaut est assignée.|  
|<xref:System.Windows.Forms.Control.Enabled%2A>|<xref:System.Windows.UIElement.IsEnabled%2A>|Lorsque <xref:System.Windows.Forms.Control.Enabled%2A> est définie, le contrôle <xref:System.Windows.Forms.Integration.ElementHost> définit la propriété <xref:System.Windows.UIElement.IsEnabled%2A> sur l’élément hébergé.|  
|<xref:System.Windows.Forms.Control.Font%2A><br /><br /> (<xref:System.Drawing.Font?displayProperty=nameWithType>)|<xref:System.Windows.Controls.Control.FontFamily%2A><br /><br /> <xref:System.Windows.Controls.Control.FontSize%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStretch%2A><br /><br /> <xref:System.Windows.Controls.Control.FontStyle%2A><br /><br /> <xref:System.Windows.Controls.Control.FontWeight%2A>|La valeur <xref:System.Windows.Forms.Control.Font%2A> est convertie en un ensemble correspondant de propriétés de police [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|<xref:System.Drawing.Font.Bold%2A>|<xref:System.Windows.Controls.Control.FontWeight%2A> de l’élément hébergé|Si <xref:System.Drawing.Font.Bold%2A> a la valeur `true`, <xref:System.Windows.Controls.Control.FontWeight%2A> a la valeur <xref:System.Windows.FontWeights.Bold%2A>.<br /><br /> Si <xref:System.Drawing.Font.Bold%2A> a la valeur `false`, <xref:System.Windows.Controls.Control.FontWeight%2A> a la valeur <xref:System.Windows.FontWeights.Normal%2A>.|  
|<xref:System.Drawing.Font.Italic%2A>|<xref:System.Windows.Controls.Control.FontStyle%2A> de l’élément hébergé|Si <xref:System.Drawing.Font.Italic%2A> a la valeur `true`, <xref:System.Windows.Controls.Control.FontStyle%2A> a la valeur <xref:System.Windows.FontStyles.Italic%2A>.<br /><br /> Si <xref:System.Drawing.Font.Italic%2A> a la valeur `false`, <xref:System.Windows.Controls.Control.FontStyle%2A> a la valeur <xref:System.Windows.FontStyles.Normal%2A>.|  
|<xref:System.Drawing.Font.Strikeout%2A>|<xref:System.Windows.TextDecorations> de l’élément hébergé|S’applique uniquement lors de l’hébergement d’un contrôle de <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Drawing.Font.Underline%2A>|<xref:System.Windows.TextDecorations> de l’élément hébergé|S’applique uniquement lors de l’hébergement d’un contrôle de <xref:System.Windows.Controls.TextBlock>.|  
|<xref:System.Windows.Forms.Control.RightToLeft%2A><br /><br /> (<xref:System.Windows.Forms.RightToLeft?displayProperty=nameWithType>)|<xref:System.Windows.FrameworkElement.FlowDirection%2A><br /><br /> (<xref:System.Windows.FlowDirection>)|<xref:System.Windows.Forms.RightToLeft.No> correspond à <xref:System.Windows.FlowDirection.LeftToRight>.<br /><br /> <xref:System.Windows.Forms.RightToLeft.Yes> correspond à <xref:System.Windows.FlowDirection.RightToLeft>.|  
|<xref:System.Windows.Forms.Control.Visible%2A>|<xref:System.Windows.UIElement.Visibility%2A>|Le contrôle <xref:System.Windows.Forms.Integration.ElementHost> définit la propriété <xref:System.Windows.UIElement.Visibility%2A> sur l’élément hébergé à l’aide des règles suivantes :<br /><br /> -   <xref:System.Windows.Forms.Control.Visible%2A> = `true` est mappé à <xref:System.Windows.Visibility.Visible>.<br />-   <xref:System.Windows.Forms.Control.Visible%2A> = `false` est mappé à <xref:System.Windows.Visibility.Hidden>.|  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Interopérabilité WPF et Win32](wpf-and-win32-interoperation.md)
- [Interopérabilité WPF et Windows Forms](wpf-and-windows-forms-interoperation.md)
- [Procédure pas à pas : mappage de propriétés à l'aide de l'élément WindowsFormsHost](walkthrough-mapping-properties-using-the-windowsformshost-element.md)
- [Procédure pas à pas : mappage de propriété à l'aide du contrôle ElementHost](walkthrough-mapping-properties-using-the-elementhost-control.md)
