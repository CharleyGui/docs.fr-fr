---
title: Vue d'ensemble de Popup
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 911130d52744c5ba54750f214829a5d1900e083c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185953"
---
# <a name="popup-overview"></a>Vue d'ensemble de Popup
Le <xref:System.Windows.Controls.Primitives.Popup> contrôle fournit un moyen d’afficher le contenu dans une fenêtre séparée qui flotte au-dessus de la fenêtre d’application actuelle par rapport à un élément désigné ou une coordonnées d’écran. Ce sujet introduit <xref:System.Windows.Controls.Primitives.Popup> le contrôle et fournit des informations sur son utilisation.  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>Qu’est-ce qu’un contrôle Popup ?  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche le contenu dans une fenêtre séparée par rapport à un élément ou un point sur l’écran. Lorsque <xref:System.Windows.Controls.Primitives.Popup> le est <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> visible, la `true`propriété est définie à .  
  
> [!NOTE]
> A <xref:System.Windows.Controls.Primitives.Popup> ne s’ouvre pas automatiquement lorsque le pointeur de la souris se déplace sur son objet parent. Si vous <xref:System.Windows.Controls.Primitives.Popup> voulez ouvrir automatiquement, <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> utilisez le ou la classe. Pour plus d’informations, consultez [Vue d’ensemble de l’info-bulle](tooltip-overview.md).  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>Création d'une fenêtre contextuelle  
 L’exemple suivant montre <xref:System.Windows.Controls.Primitives.Popup> comment définir un contrôle <xref:System.Windows.Controls.Button> qui est l’élément enfant d’un contrôle. Parce <xref:System.Windows.Controls.Button> qu’un seul élément enfant peut avoir <xref:System.Windows.Controls.Button> un <xref:System.Windows.Controls.Primitives.Popup> seul élément <xref:System.Windows.Controls.StackPanel>enfant, cet exemple place le texte pour et les contrôles dans un . Le contenu <xref:System.Windows.Controls.Primitives.Popup> de l’apparaît dans un <xref:System.Windows.Controls.TextBlock> contrôle, qui affiche son texte dans <xref:System.Windows.Controls.Button> une fenêtre séparée qui flotte au-dessus de la fenêtre d’application près du contrôle connexe.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>Contrôles qui implémentent un contrôle Popup  
 Vous pouvez <xref:System.Windows.Controls.Primitives.Popup> intégrer des contrôles dans d’autres contrôles. Les contrôles suivants <xref:System.Windows.Controls.Primitives.Popup> implémenter le contrôle pour des utilisations spécifiques :  
  
- <xref:System.Windows.Controls.ToolTip>. Si vous voulez créer un tooltip pour <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> un élément, utilisez le et les classes. Pour plus d’informations, consultez [Vue d’ensemble de l’info-bulle](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Si vous souhaitez créer un menu contextuelle <xref:System.Windows.Controls.ContextMenu> pour un élément, utilisez le contrôle. Pour plus d’informations, consultez [Vue d’ensemble de ContextMenu](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Si vous souhaitez créer un contrôle de sélection qui dispose d’une boîte <xref:System.Windows.Controls.ComboBox> de liste d’abandon qui peut être affichée ou cachée, utilisez le contrôle.  
  
- <xref:System.Windows.Controls.Expander>. Si vous souhaitez créer un contrôle qui affiche un en-tête <xref:System.Windows.Controls.Expander> avec une zone pliable qui affiche le contenu, utilisez le contrôle. Pour plus d’informations, consultez [Vue d’ensemble d’Expander](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Comportement et apparence d’un contrôle Popup  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle fournit des fonctionnalités qui vous permettent de personnaliser son comportement et son apparence. Par exemple, vous pouvez définir un comportement ouvert et proche, l’animation, l’opacité et les effets de bitmap, ainsi que <xref:System.Windows.Controls.Primitives.Popup> la taille et la position.  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>Comportement à l’ouverture et à la fermeture  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche son <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> contenu lorsque `true`la propriété est réglée à . Par défaut, <xref:System.Windows.Controls.Primitives.Popup> reste <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> ouvert jusqu’à ce que la propriété est réglée à `false`. Cependant, vous pouvez modifier le <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> comportement `false`par défaut en définissant la propriété à . Lorsque vous définissez `false`cette <xref:System.Windows.Controls.Primitives.Popup> propriété à , la fenêtre de contenu a capture de souris. La <xref:System.Windows.Controls.Primitives.Popup> capture de souris perd et la fenêtre <xref:System.Windows.Controls.Primitives.Popup> se ferme quand un événement de souris se produit à l’extérieur de la fenêtre.  
  
 Les <xref:System.Windows.Controls.Primitives.Popup.Opened> <xref:System.Windows.Controls.Primitives.Popup.Closed> événements et les <xref:System.Windows.Controls.Primitives.Popup> événements sont soulevés lorsque la fenêtre de contenu est ouverte ou fermée.  
  
<a name="Animation"></a>
### <a name="animation"></a>Animation  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle a intégré le soutien pour les animations qui sont généralement associées à des comportements comme fade-in et slide-in. Vous pouvez activer ces animations en définissant la <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> propriété à une <xref:System.Windows.Controls.Primitives.PopupAnimation> valeur de recensement. Pour <xref:System.Windows.Controls.Primitives.Popup> que les animations fonctionnent <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> correctement, `true`vous devez définir la propriété à .  
  
 Vous pouvez également appliquer <xref:System.Windows.Media.Animation.Storyboard> des <xref:System.Windows.Controls.Primitives.Popup> animations comme au contrôle.  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>Effets d’opacité et bitmap  
 La <xref:System.Windows.UIElement.Opacity%2A> propriété <xref:System.Windows.Controls.Primitives.Popup> pour un contrôle n’a aucun effet sur son contenu. Par défaut, <xref:System.Windows.Controls.Primitives.Popup> la fenêtre de contenu est opaque. Pour créer <xref:System.Windows.Controls.Primitives.Popup>un transparent <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> , `true`définir la propriété à .  
  
 Le contenu <xref:System.Windows.Controls.Primitives.Popup> d’un n’hérite pas <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>des effets de <xref:System.Windows.Controls.Primitives.Popup> bitmap, tels que , que vous définissez directement sur le contrôle ou sur tout autre élément dans la fenêtre parente. Pour que les effets de bitmap apparaissent sur le contenu d’un, <xref:System.Windows.Controls.Primitives.Popup>vous devez définir l’effet bitmap directement sur son contenu. Par exemple, si l’enfant d’un <xref:System.Windows.Controls.Primitives.Popup> est un <xref:System.Windows.Controls.StackPanel> <xref:System.Windows.Controls.StackPanel>, définir l’effet bitmap sur le .  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Dimensionnement d’un contrôle Popup  
 Par défaut, <xref:System.Windows.Controls.Primitives.Popup> a est automatiquement dimensionné à son contenu. Lorsque l’auto-dimensionnement se produit, certains effets de bitmap peuvent être <xref:System.Windows.Controls.Primitives.Popup> cachés parce que la taille par défaut de la zone d’écran qui est défini pour le contenu ne fournit pas assez d’espace pour les effets de bitmap à afficher.  
  
 <xref:System.Windows.Controls.Primitives.Popup>le contenu peut également être <xref:System.Windows.UIElement.RenderTransform%2A> masqué lorsque vous définissez un sur le contenu. Dans ce scénario, certains contenus pourraient être <xref:System.Windows.Controls.Primitives.Popup> cachés si le <xref:System.Windows.Controls.Primitives.Popup>contenu de la transformation s’étend au-delà de la zone de l’original . Si un effet bitmap ou transformer nécessite plus d’espace, vous pouvez définir une marge autour du <xref:System.Windows.Controls.Primitives.Popup> contenu afin de fournir plus de zone pour le contrôle.  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>Définition de la position d’un contrôle Popup  
 Vous pouvez positionner un <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>popup <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>en <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> définissant le , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, et les propriétés. Pour plus d’informations, consultez [Comportement de positionnement de Popup](popup-placement-behavior.md). Lorsqu’il <xref:System.Windows.Controls.Primitives.Popup> est affiché à l’écran, il ne se repositionne pas si son parent est repositionné.  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>Personnalisation du positionnement de la fenêtre contextuelle  
 Vous pouvez personnaliser le <xref:System.Windows.Controls.Primitives.Popup> placement d’un contrôle en spécifiant <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> un ensemble <xref:System.Windows.Controls.Primitives.Popup> de coordonnées qui sont relatives à l’endroit où vous voulez que le s’affiche.  
  
 Pour personnaliser le placement, définissez la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété à <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Ensuite, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> définissez un délégué qui renvoie un ensemble de points de <xref:System.Windows.Controls.Primitives.Popup>placement possibles et axes primaires (par ordre de préférence) pour le . Le point qui montre la <xref:System.Windows.Controls.Primitives.Popup> plus grande partie de la est automatiquement sélectionné. Pour voir un exemple, consultez [Spécifier une position de menu contextuel personnalisée](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Contrôle Popup et arborescence d’éléments visuels  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle n’a pas son propre arbre visuel; il renvoie plutôt une taille de <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> 0 <xref:System.Windows.Controls.Primitives.Popup> (zéro) lorsque la méthode pour est appelée. Cependant, lorsque vous <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> définissez la propriété de <xref:System.Windows.Controls.Primitives.Popup> `true`, une nouvelle fenêtre avec son propre arbre visuel est créé. La nouvelle fenêtre <xref:System.Windows.Controls.Primitives.Popup.Child%2A> contient <xref:System.Windows.Controls.Primitives.Popup>le contenu de . La largeur et la hauteur de la nouvelle fenêtre ne peuvent pas dépasser 75 % de la largeur et de la hauteur de l’écran.  
  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle maintient une <xref:System.Windows.Controls.Primitives.Popup.Child%2A> référence à son contenu en tant qu’enfant logique. Lorsque la nouvelle fenêtre est <xref:System.Windows.Controls.Primitives.Popup> créée, le contenu de devient un <xref:System.Windows.Controls.Primitives.Popup>enfant visuel de la fenêtre et reste l’enfant logique de . Inversement, <xref:System.Windows.Controls.Primitives.Popup> reste le <xref:System.Windows.Controls.Primitives.Popup.Child%2A> parent logique de son contenu.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Sujets comment se passer](popup-how-to-topics.md)
- [Sujets comment se passer](tooltip-how-to-topics.md)
