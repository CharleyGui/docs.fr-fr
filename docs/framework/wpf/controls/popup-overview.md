---
title: Vue d'ensemble de Popup
description: En savoir plus sur le contrôle contextuel Windows Presentation Foundation, qui permet d’afficher le contenu dans une fenêtre qui flotte sur l’application actuelle.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], Popup
- Popup control [WPF], about Popup control
ms.assetid: 774f53ca-bff8-470e-9ce9-3928b4cf3d4c
ms.openlocfilehash: 84eaddc53366df6d1da1a0a005d3618268f8cce2
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167538"
---
# <a name="popup-overview"></a>Vue d'ensemble de Popup
Le <xref:System.Windows.Controls.Primitives.Popup> contrôle permet d’afficher le contenu dans une fenêtre distincte qui flotte au-dessus de la fenêtre d’application actuelle par rapport à un élément ou une coordonnée d’écran désigné. Cette rubrique présente le <xref:System.Windows.Controls.Primitives.Popup> contrôle et fournit des informations sur son utilisation.  

<a name="What_Is_a_Popup_"></a>
## <a name="what-is-a-popup"></a>Qu’est-ce qu’un contrôle Popup ?  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche le contenu dans une fenêtre distincte par rapport à un élément ou à un point sur l’écran. Lorsque le <xref:System.Windows.Controls.Primitives.Popup> est visible, la <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> propriété a la valeur `true` .  
  
> [!NOTE]
> Un <xref:System.Windows.Controls.Primitives.Popup> ne s’ouvre pas automatiquement lorsque le pointeur de la souris se déplace au-dessus de son objet parent. Si vous souhaitez <xref:System.Windows.Controls.Primitives.Popup> qu’un ouvre automatiquement, utilisez la <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> classe ou. Pour plus d’informations, consultez [Vue d’ensemble de l’info-bulle](tooltip-overview.md).  
  
<a name="APopupExample"></a>
## <a name="creating-a-popup"></a>Création d'une fenêtre contextuelle  
 L’exemple suivant montre comment définir un <xref:System.Windows.Controls.Primitives.Popup> contrôle qui est l’élément enfant d’un <xref:System.Windows.Controls.Button> contrôle. Étant donné qu’un <xref:System.Windows.Controls.Button> ne peut avoir qu’un seul élément enfant, cet exemple place le texte pour les <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.Popup> contrôles et dans un <xref:System.Windows.Controls.StackPanel> . Le contenu du <xref:System.Windows.Controls.Primitives.Popup> apparaît dans un <xref:System.Windows.Controls.TextBlock> contrôle, qui affiche son texte dans une fenêtre distincte qui flotte au-dessus de la fenêtre d’application près du <xref:System.Windows.Controls.Button> contrôle associé.  
  
 [!code-xaml[PopupSimple#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#1)]  
  
 [!code-xaml[PopupSimple#CreatePopupCodeXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupSimple/CSharp/Window1.xaml#createpopupcodexaml)]  
  
<a name="PopupUses"></a>
## <a name="controls-that-implement-a-popup"></a>Contrôles qui implémentent un contrôle Popup  
 Vous pouvez créer <xref:System.Windows.Controls.Primitives.Popup> des contrôles dans d’autres contrôles. Les contrôles suivants implémentent le <xref:System.Windows.Controls.Primitives.Popup> contrôle pour des utilisations spécifiques :  
  
- <xref:System.Windows.Controls.ToolTip>. Si vous souhaitez créer une info-bulle pour un élément, utilisez <xref:System.Windows.Controls.ToolTip> les <xref:System.Windows.Controls.ToolTipService> classes et. Pour plus d’informations, consultez [Vue d’ensemble de l’info-bulle](tooltip-overview.md).  
  
- <xref:System.Windows.Controls.ContextMenu>. Si vous souhaitez créer un menu contextuel pour un élément, utilisez le <xref:System.Windows.Controls.ContextMenu> contrôle. Pour plus d’informations, consultez [Vue d’ensemble de ContextMenu](contextmenu-overview.md).  
  
- <xref:System.Windows.Controls.ComboBox>. Si vous souhaitez créer un contrôle de sélection qui contient une zone de liste déroulante qui peut être affichée ou masquée, utilisez le <xref:System.Windows.Controls.ComboBox> contrôle.  
  
- <xref:System.Windows.Controls.Expander>. Si vous souhaitez créer un contrôle qui affiche un en-tête avec une zone réductible qui affiche du contenu, utilisez le <xref:System.Windows.Controls.Expander> contrôle. Pour plus d’informations, consultez [Vue d’ensemble d’Expander](expander-overview.md).  
  
<a name="PopupBehaviorandAppearance"></a>
## <a name="popup-behavior-and-appearance"></a>Comportement et apparence d’un contrôle Popup  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle fournit des fonctionnalités qui vous permettent de personnaliser son comportement et son apparence. Par exemple, vous pouvez définir le comportement d’ouverture et de fermeture, l’animation, l’opacité et les effets bitmap, ainsi que la <xref:System.Windows.Controls.Primitives.Popup> taille et la position.  
  
<a name="OpenandCloseBehavior"></a>
### <a name="open-and-close-behavior"></a>Comportement à l’ouverture et à la fermeture  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche son contenu lorsque la <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> propriété a la valeur `true` . Par défaut, <xref:System.Windows.Controls.Primitives.Popup> reste ouvert jusqu’à ce que la <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> propriété ait la valeur `false` . Toutefois, vous pouvez modifier le comportement par défaut en affectant à la propriété la valeur <xref:System.Windows.Controls.Primitives.Popup.StaysOpen%2A> `false` . Lorsque vous affectez la valeur à cette propriété `false` , la <xref:System.Windows.Controls.Primitives.Popup> fenêtre de contenu a la capture de la souris. Le <xref:System.Windows.Controls.Primitives.Popup> perd la capture de la souris et la fenêtre se ferme lorsqu’un événement de souris se produit en dehors de la <xref:System.Windows.Controls.Primitives.Popup> fenêtre.  
  
 Les <xref:System.Windows.Controls.Primitives.Popup.Opened> <xref:System.Windows.Controls.Primitives.Popup.Closed> événements et sont déclenchés lorsque la <xref:System.Windows.Controls.Primitives.Popup> fenêtre de contenu est ouverte ou fermée.  
  
<a name="Animation"></a>
### <a name="animation"></a>Animation  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle dispose d’une prise en charge intégrée pour les animations qui sont généralement associées à des comportements comme un fondu dans et un glisser-déplacer. Vous pouvez activer ces animations en affectant <xref:System.Windows.Controls.Primitives.Popup.PopupAnimation%2A> à la propriété une <xref:System.Windows.Controls.Primitives.PopupAnimation> valeur d’énumération. Pour <xref:System.Windows.Controls.Primitives.Popup> que les animations fonctionnent correctement, vous devez affecter <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> à la propriété la valeur `true` .  
  
 Vous pouvez également appliquer des animations comme <xref:System.Windows.Media.Animation.Storyboard> au <xref:System.Windows.Controls.Primitives.Popup> contrôle.  
  
<a name="OpacityandBitmapEffects"></a>
### <a name="opacity-and-bitmap-effects"></a>Effets d’opacité et bitmap  
 La <xref:System.Windows.UIElement.Opacity%2A> propriété d’un <xref:System.Windows.Controls.Primitives.Popup> contrôle n’a aucun effet sur son contenu. Par défaut, la <xref:System.Windows.Controls.Primitives.Popup> fenêtre de contenu est opaque. Pour créer un transparent <xref:System.Windows.Controls.Primitives.Popup> , affectez <xref:System.Windows.Controls.Primitives.Popup.AllowsTransparency%2A> à la propriété la valeur `true` .  
  
 Le contenu d’un <xref:System.Windows.Controls.Primitives.Popup> n’hérite pas des effets bitmap, tels que <xref:System.Windows.Media.Effects.DropShadowBitmapEffect> , que vous définissez directement sur le <xref:System.Windows.Controls.Primitives.Popup> contrôle ou sur tout autre élément de la fenêtre parente. Pour que les effets bitmap apparaissent sur le contenu d’un <xref:System.Windows.Controls.Primitives.Popup> , vous devez définir l’effet bitmap directement sur son contenu. Par exemple, si l’enfant d’un <xref:System.Windows.Controls.Primitives.Popup> est un <xref:System.Windows.Controls.StackPanel> , définissez l’effet bitmap sur <xref:System.Windows.Controls.StackPanel> .  
  
<a name="PopupSize"></a>
### <a name="popup-size"></a>Dimensionnement d’un contrôle Popup  
 Par défaut, un <xref:System.Windows.Controls.Primitives.Popup> est automatiquement dimensionné à son contenu. Lorsque le dimensionnement automatique se produit, certains effets bitmap peuvent être masqués, car la taille par défaut de la zone d’écran définie pour le <xref:System.Windows.Controls.Primitives.Popup> contenu ne fournit pas suffisamment d’espace pour l’affichage des effets bitmap.  
  
 <xref:System.Windows.Controls.Primitives.Popup>le contenu peut également être masqué lorsque vous définissez un <xref:System.Windows.UIElement.RenderTransform%2A> sur le contenu. Dans ce scénario, un contenu peut être masqué si le contenu de la transformation s' <xref:System.Windows.Controls.Primitives.Popup> étend au-delà de la zone de l’original <xref:System.Windows.Controls.Primitives.Popup> . Si un effet bitmap ou une transformation requiert plus d’espace, vous pouvez définir une marge autour du <xref:System.Windows.Controls.Primitives.Popup> contenu pour fournir davantage de zone pour le contrôle.  
  
<a name="DefiningPopupPosition"></a>
## <a name="defining-the-popup-position"></a>Définition de la position d’un contrôle Popup  
 Vous pouvez positionner un popup en définissant <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> les <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Propriétés,, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> , <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffsetProperty> . Pour plus d’informations, consultez [Comportement de positionnement de Popup](popup-placement-behavior.md). Lorsque <xref:System.Windows.Controls.Primitives.Popup> est affiché à l’écran, il ne se repositionne pas si son parent est repositionné.  
  
<a name="CustomizingPopupPlacement"></a>
### <a name="customizing-popup-placement"></a>Personnalisation du positionnement de la fenêtre contextuelle  
 Vous pouvez personnaliser le positionnement d’un <xref:System.Windows.Controls.Primitives.Popup> contrôle en spécifiant un ensemble de coordonnées relatives à l' <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> emplacement où vous souhaitez que le <xref:System.Windows.Controls.Primitives.Popup> s’affiche.  
  
 Pour personnaliser le placement, affectez à la propriété la valeur <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Custom> . Définissez ensuite un <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> délégué qui retourne un ensemble de points de positionnement possibles et les axes principaux (par ordre de préférence) pour le <xref:System.Windows.Controls.Primitives.Popup> . Le point qui indique la plus grande partie du <xref:System.Windows.Controls.Primitives.Popup> est automatiquement sélectionné. Pour voir un exemple, consultez [Spécifier une position de menu contextuel personnalisée](how-to-specify-a-custom-popup-position.md).  
  
<a name="PopupandtheVisualTree"></a>
## <a name="popup-and-the-visual-tree"></a>Contrôle Popup et arborescence d’éléments visuels  
 Un <xref:System.Windows.Controls.Primitives.Popup> contrôle n’a pas sa propre arborescence d’éléments visuels ; il retourne à la place une taille de 0 (zéro) lorsque la <xref:System.Windows.Controls.Primitives.Popup.MeasureOverride%2A> méthode pour <xref:System.Windows.Controls.Primitives.Popup> est appelée. Toutefois, lorsque vous affectez <xref:System.Windows.Controls.Primitives.Popup.IsOpen%2A> à la propriété de la valeur <xref:System.Windows.Controls.Primitives.Popup> `true` , une nouvelle fenêtre avec sa propre arborescence d’éléments visuels est créée. La nouvelle fenêtre contient le <xref:System.Windows.Controls.Primitives.Popup.Child%2A> contenu de <xref:System.Windows.Controls.Primitives.Popup> . La largeur et la hauteur de la nouvelle fenêtre ne peuvent pas dépasser 75 % de la largeur et de la hauteur de l’écran.  
  
 Le <xref:System.Windows.Controls.Primitives.Popup> contrôle conserve une référence à son <xref:System.Windows.Controls.Primitives.Popup.Child%2A> contenu en tant qu’enfant logique. Lorsque la nouvelle fenêtre est créée, le contenu de <xref:System.Windows.Controls.Primitives.Popup> devient un enfant visuel de la fenêtre et reste l’enfant logique de <xref:System.Windows.Controls.Primitives.Popup> . À l’inverse, <xref:System.Windows.Controls.Primitives.Popup> reste le parent logique de son <xref:System.Windows.Controls.Primitives.Popup.Child%2A> contenu.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.Popup>
- <xref:System.Windows.Controls.Primitives.PopupPrimaryAxis>
- <xref:System.Windows.Controls.Primitives.PlacementMode>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacement>
- <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Rubriques Comment](popup-how-to-topics.md)
- [Rubriques Comment](tooltip-how-to-topics.md)
