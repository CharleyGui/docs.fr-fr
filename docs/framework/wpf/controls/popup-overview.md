---
title: Vue d'ensemble de Popup
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 7e6977737d362fd0df6321702bb8a1ac6cad66e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951427"
---
# <a name="popup-overview"></a>Vue d'ensemble de Popup
Le <xref:System.Windows.Controls.Primitives.Popup> contrôle permet d’afficher le contenu dans une fenêtre distincte qui flotte au-dessus de la fenêtre d’application actuelle par rapport à un élément ou une coordonnée d’écran désigné. Cette rubrique présente le <xref:System.Windows.Controls.Primitives.Popup> contrôle et fournit des informations sur son utilisation.  

<a name="What_Is_a_Popup_"></a>   
## <a name="what-is-a-popup"></a>Qu’est-ce qu’un contrôle Popup ?  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche le contenu dans une fenêtre distincte par rapport à un élément ou à un point sur l’écran. Lorsque le <xref:System.Windows.Controls.Primitives.Popup> est visible, la <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> propriété a la valeur `true`.  
  
> [!NOTE]
> Un <xref:System.Windows.Controls.Primitives.Popup> ne s’ouvre pas automatiquement lorsque le pointeur de la souris se déplace au-dessus de son objet parent. Si vous souhaitez qu' <xref:System.Windows.Controls.Primitives.Popup> un ouvre automatiquement, utilisez la <xref:System.Windows.Controls.ToolTip> classe <xref:System.Windows.Controls.ToolTipService> ou. Pour plus d’informations, consultez [Vue d’ensemble de l’info-bulle](tooltip-overview.md).  
  
<a name="APopupExample"></a>   
## <a name="creating-a-popup"></a>Création d'une fenêtre contextuelle  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.Primitives.Popup> contrôle qui est l’élément enfant d’un <xref:System.Windows.Controls.Button> contrôle. Étant donné <xref:System.Windows.Controls.Button> qu’un ne peut avoir qu’un seul élément enfant, cet exemple place <xref:System.Windows.Controls.Button> le texte <xref:System.Windows.Controls.Primitives.Popup> pour les contrôles <xref:System.Windows.Controls.StackPanel>et dans un. Le contenu du <xref:System.Windows.Controls.Primitives.Popup> apparaît dans un <xref:System.Windows.Controls.TextBlock> contrôle, qui affiche son texte dans une fenêtre distincte qui flotte au-dessus de la fenêtre d’application près <xref:System.Windows.Controls.Button> du contrôle associé.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>   
## <a name="controls-that-implement-a-popup"></a>Contrôles qui implémentent un contrôle Popup  
 Vous pouvez créer <xref:System.Windows.Controls.Primitives.Popup> des contrôles dans d’autres contrôles. Les contrôles suivants implémentent <xref:System.Windows.Controls.Primitives.Popup> le contrôle pour des utilisations spécifiques:  
  
- <xref:System.Windows.Controls.ToolTip>. Si vous souhaitez créer une info-bulle pour un élément, utilisez <xref:System.Windows.Controls.ToolTip> les <xref:System.Windows.Controls.ToolTipService> classes et. Pour plus d’informations, consultez [Vue d’ensemble de l’info-bulle](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Si vous souhaitez créer un menu contextuel pour un élément, utilisez le <xref:System.Windows.Controls.ContextMenu> contrôle. Pour plus d’informations, consultez [Vue d’ensemble de ContextMenu](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Si vous souhaitez créer un contrôle de sélection qui contient une zone de liste déroulante qui peut être affichée ou masquée, <xref:System.Windows.Controls.ComboBox> utilisez le contrôle.  
  
- <xref:System.Windows.Controls.Expander>. Si vous souhaitez créer un contrôle qui affiche un en-tête avec une zone réductible qui affiche du contenu <xref:System.Windows.Controls.Expander> , utilisez le contrôle. Pour plus d’informations, consultez [Vue d’ensemble d’Expander](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>   
## <a name="popup-behavior-and-appearance"></a>Comportement et apparence d’un contrôle Popup  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle fournit des fonctionnalités qui vous permettent de personnaliser son comportement et son apparence. Par exemple, vous pouvez définir le comportement d’ouverture et de fermeture, l’animation, l’opacité <xref:System.Windows.Controls.Primitives.Popup> et les effets bitmap, ainsi que la taille et la position.  
  
<a name="OpenandCloseBehavior"></a>   
### <a name="open-and-close-behavior"></a>Comportement à l’ouverture et à la fermeture  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche son contenu lorsque la <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> propriété a la valeur `true`. Par défaut, <xref:System.Windows.Controls.Primitives.Popup> reste ouvert jusqu’à <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> ce que la propriété `false`ait la valeur. Toutefois, vous pouvez modifier le comportement par défaut en affectant <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> à `false`la propriété la valeur. Lorsque vous affectez la valeur `false`à cette <xref:System.Windows.Controls.Primitives.Popup> propriété, la fenêtre de contenu a la capture de la souris. Le <xref:System.Windows.Controls.Primitives.Popup> perd la capture de la souris et la fenêtre se ferme lorsqu’un événement <xref:System.Windows.Controls.Primitives.Popup> de souris se produit en dehors de la fenêtre.  
  
 Les <xref:System.Windows.Controls.Primitives.Popup.Opened> événements <xref:System.Windows.Controls.Primitives.Popup.Closed> et sont déclenchés lorsque <xref:System.Windows.Controls.Primitives.Popup> la fenêtre de contenu est ouverte ou fermée.  
  
<a name="Animation"></a>   
### <a name="animation"></a>Animation  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle dispose d’une prise en charge intégrée pour les animations qui sont généralement associées à des comportements comme un fondu dans et un glisser-déplacer. Vous pouvez activer ces animations en affectant à <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> la propriété une <xref:System.Windows.Controls.Primitives.PopupAnimation> valeur d’énumération. Pour <xref:System.Windows.Controls.Primitives.Popup> que les animations fonctionnent correctement, vous devez affecter <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> à `true`la propriété la valeur.  
  
 Vous pouvez également appliquer des <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Controls.Primitives.Popup> animations comme au contrôle.  
  
<a name="OpacityandBitmapEffects"></a>   
### <a name="opacity-and-bitmap-effects"></a>Effets d’opacité et bitmap  
 La <xref:System.Windows.UIElement.Opacity%2A> propriété d’un <xref:System.Windows.Controls.Primitives.Popup> contrôle n’a aucun effet sur son contenu. Par défaut, la <xref:System.Windows.Controls.Primitives.Popup> fenêtre de contenu est opaque. Pour créer un transparent <xref:System.Windows.Controls.Primitives.Popup>, affectez <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> à `true`la propriété la valeur.  
  
 Le contenu d’un <xref:System.Windows.Controls.Primitives.Popup> n’hérite pas des effets bitmap, <xref:System.Windows.Media.Effects.DropShadowBitmapEffect>tels que, que vous définissez directement <xref:System.Windows.Controls.Primitives.Popup> sur le contrôle ou sur tout autre élément de la fenêtre parente. Pour que les effets bitmap apparaissent sur le contenu d' <xref:System.Windows.Controls.Primitives.Popup>un, vous devez définir l’effet bitmap directement sur son contenu. Par exemple, si l’enfant d’un <xref:System.Windows.Controls.Primitives.Popup> est un <xref:System.Windows.Controls.StackPanel>, définissez <xref:System.Windows.Controls.StackPanel>l’effet bitmap sur.  
  
<a name="PopupSize"></a>   
### <a name="popup-size"></a>Dimensionnement d’un contrôle Popup  
 Par défaut, un <xref:System.Windows.Controls.Primitives.Popup> est automatiquement dimensionné à son contenu. Lorsque le dimensionnement automatique se produit, certains effets bitmap peuvent être masqués, car la taille par défaut de la zone d' <xref:System.Windows.Controls.Primitives.Popup> écran définie pour le contenu ne fournit pas suffisamment d’espace pour l’affichage des effets bitmap.  
  
 <xref:System.Windows.Controls.Primitives.Popup>le contenu peut également être masqué lorsque vous définissez un <xref:System.Windows.UIElement.RenderTransform%2A> sur le contenu. Dans ce scénario, un contenu peut être masqué si le contenu de la transformation <xref:System.Windows.Controls.Primitives.Popup> s’étend au-delà de la <xref:System.Windows.Controls.Primitives.Popup>zone de l’original. Si un effet bitmap ou une transformation requiert plus d’espace, vous pouvez définir une marge <xref:System.Windows.Controls.Primitives.Popup> autour du contenu pour fournir davantage de zone pour le contrôle.  
  
<a name="DefiningPopupPosition"></a>   
## <a name="defining-the-popup-position"></a>Définition de la position d’un contrôle Popup  
 Vous pouvez positionner un popup en définissant <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>les <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>propriétés <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>,, <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> et. Pour plus d’informations, consultez [Comportement de positionnement de Popup](popup-placement-behavior.md). Lorsque <xref:System.Windows.Controls.Primitives.Popup> est affiché à l’écran, il ne se repositionne pas si son parent est repositionné.  
  
<a name="CustomizingPopupPlacement"></a>   
### <a name="customizing-popup-placement"></a>Personnalisation du positionnement d’un contrôle Popup  
 Vous pouvez personnaliser le positionnement d’un <xref:System.Windows.Controls.Primitives.Popup> contrôle en spécifiant un ensemble de coordonnées relatives à l' <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> emplacement où vous souhaitez que <xref:System.Windows.Controls.Primitives.Popup> le s’affiche.  
  
 Pour personnaliser le placement, affectez <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> à <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>la propriété la valeur. Définissez ensuite un <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> délégué qui retourne un ensemble de points de positionnement possibles et les axes principaux (par ordre de préférence) <xref:System.Windows.Controls.Primitives.Popup>pour le. Le point qui indique la plus grande partie du <xref:System.Windows.Controls.Primitives.Popup> est automatiquement sélectionné. Pour obtenir un exemple, consultez [Spécifier une position de menu contextuel personnalisée](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>   
## <a name="popup-and-the-visual-tree"></a>Contrôle Popup et arborescence d’éléments visuels  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle n’a pas sa propre arborescence d’éléments visuels; il retourne à la place une taille de 0 ( <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> zéro) <xref:System.Windows.Controls.Primitives.Popup> lorsque la méthode pour est appelée. Toutefois, lorsque vous affectez <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> à `true`la <xref:System.Windows.Controls.Primitives.Popup> propriété de la valeur, une nouvelle fenêtre avec sa propre arborescence d’éléments visuels est créée. La nouvelle fenêtre contient le <xref:System.Windows.Controls.Primitives.Popup.Child%2A> contenu de <xref:System.Windows.Controls.Primitives.Popup>. La largeur et la hauteur de la nouvelle fenêtre ne peuvent pas dépasser 75 % de la largeur et de la hauteur de l’écran.  
  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle conserve une référence à son <xref:System.Windows.Controls.Primitives.Popup.Child%2A> contenu en tant qu’enfant logique. Lorsque la nouvelle fenêtre est créée, le contenu de <xref:System.Windows.Controls.Primitives.Popup> devient un enfant visuel de la fenêtre et reste l’enfant logique de <xref:System.Windows.Controls.Primitives.Popup>. À l’inverse, <xref:System.Windows.Controls.Primitives.Popup> reste le parent logique de son <xref:System.Windows.Controls.Primitives.Popup.Child%2A> contenu.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Rubriques de guide pratique](popup-how-to-topics.md)
- [Rubriques de guide pratique](tooltip-how-to-topics.md)
