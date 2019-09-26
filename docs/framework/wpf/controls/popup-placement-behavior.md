---
title: Comportement de positionnement de Popup
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: ca984aa724cf3f076d6073aa8b8179abfb91d26c
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/25/2019
ms.locfileid: "69951735"
---
# <a name="popup-placement-behavior"></a>Comportement de positionnement de Popup
Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche le contenu dans une fenêtre distincte qui flotte sur une application. Vous pouvez spécifier la position d’un <xref:System.Windows.Controls.Primitives.Popup> en fonction d’un contrôle, de la souris ou de l’écran à <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>l' <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>aide des <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>propriétés, <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>,, et.  Ces propriétés fonctionnent ensemble pour vous offrir la possibilité de spécifier la position du <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
> Les <xref:System.Windows.Controls.ToolTip> classes <xref:System.Windows.Controls.ContextMenu> et définissent également ces cinq propriétés et se comportent de la même façon.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Positionnement de la fenêtre contextuelle  
 Le positionnement d’un <xref:System.Windows.Controls.Primitives.Popup> peut être relatif à un <xref:System.Windows.UIElement> ou à l’écran entier.  L’exemple suivant crée quatre <xref:System.Windows.Controls.Primitives.Popup> contrôles relatifs à un <xref:System.Windows.UIElement>, dans le cas présent, une image. La propriété <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup> de tous les <xref:System.Windows.Controls.Primitives.Popup> contrôles a la valeur ,maischacund’euxaunevaleurdifférentepour`image1`la propriété placement.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 L’illustration suivante montre l’image et les <xref:System.Windows.Controls.Primitives.Popup> contrôles.  
  
 ![Image avec quatre contrôles Popup](./media/popup-placement-behavior/popup-placement-intro.png "Image avec quatre fenêtres contextuelles")    
  
 Cet exemple simple <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> montre comment définir les propriétés et <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> , mais en utilisant les <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>propriétés, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> , vous avez encore plus de contrôle sur l' <xref:System.Windows.Controls.Primitives.Popup> emplacement où est positionné.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Définitions des termes : Anatomie d’une fenêtre contextuelle  
 Les termes suivants sont utiles pour comprendre comment les <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>propriétés <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> sont liées les unes aux autres et <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Objet cible  
  
- Zone cible  
  
- Origine de la cible  
  
- Point d’alignement de la fenêtre contextuelle  
  
 Ces termes offrent un moyen pratique de faire référence à différents aspects du <xref:System.Windows.Controls.Primitives.Popup> et du contrôle auquel il est associé.  
  
### <a name="target-object"></a>Objet cible  
 L' *objet cible* est l’élément auquel le <xref:System.Windows.Controls.Primitives.Popup> est associé. Si la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriété est définie, elle spécifie l’objet cible.  Si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> n’est pas défini et que <xref:System.Windows.Controls.Primitives.Popup> le a un parent, le parent est l’objet cible.  S’il n’y <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a aucune valeur ni aucun parent, il n’y a pas d' <xref:System.Windows.Controls.Primitives.Popup> objet cible et est positionné par rapport à l’écran.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> qui est l’enfant d’un <xref:System.Windows.Controls.Canvas>.  L’exemple ne définit pas la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriété sur le <xref:System.Windows.Controls.Primitives.Popup>. La valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> de <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>est, donc <xref:System.Windows.Controls.Primitives.Popup> le s’affiche <xref:System.Windows.Controls.Canvas>sous le.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 L’illustration suivante montre que <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport <xref:System.Windows.Controls.Canvas>à.  
  
 ![Contrôle Popup sans PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Popup sans PlacementTarget.")  

 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> qui est l’enfant d’un <xref:System.Windows.Controls.Canvas>, mais cette `ellipse1`fois la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a la valeur, de sorte que la fenêtre contextuelle <xref:System.Windows.Shapes.Ellipse>s’affiche sous le.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 L’illustration suivante montre que <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport <xref:System.Windows.Shapes.Ellipse>à.  
  
 ![Fenêtre contextuelle positionnée par rapport à une ellipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Popup avec PlacementTarget")    
  
> [!NOTE]
> Pour <xref:System.Windows.Controls.ToolTip>, la valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> de <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>est.  Pour <xref:System.Windows.Controls.ContextMenu>, la valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> de <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>est. Ces valeurs sont expliquées plus loin, dans la section « Comment les propriétés fonctionnent ensemble ».  
  
### <a name="target-area"></a>Zone cible  
 La *zone cible* correspond à la zone de l’écran à <xref:System.Windows.Controls.Primitives.Popup> laquelle est relatif. Dans les exemples précédents, <xref:System.Windows.Controls.Primitives.Popup> est aligné avec les limites de l’objet cible, mais dans certains cas <xref:System.Windows.Controls.Primitives.Popup> , est aligné sur les autres limites, même si <xref:System.Windows.Controls.Primitives.Popup> a un objet cible.  Si la <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> propriété est définie, la zone cible est différente des limites de l’objet cible.  
  
 L’exemple suivant crée deux <xref:System.Windows.Controls.Canvas> objets, chacun contenant un <xref:System.Windows.Shapes.Rectangle> et un <xref:System.Windows.Controls.Primitives.Popup>.  Dans les deux cas, l’objet cible pour <xref:System.Windows.Controls.Primitives.Popup> est le <xref:System.Windows.Controls.Canvas>. Le <xref:System.Windows.Controls.Primitives.Popup> dans le premier <xref:System.Windows.Controls.Canvas> a le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jeu, avec ses <xref:System.Windows.Rect.X%2A>propriétés <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, et <xref:System.Windows.Rect.Height%2A> ayant respectivement la valeur 50, 50, 50 et 100. Le <xref:System.Windows.Controls.Primitives.Popup> de la seconde <xref:System.Windows.Controls.Canvas> n’a pas le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> jeu.  Par conséquent, le <xref:System.Windows.Controls.Primitives.Popup> premier est positionné sous le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> et le second <xref:System.Windows.Controls.Primitives.Popup> est positionné sous le <xref:System.Windows.Controls.Canvas>. Chaque <xref:System.Windows.Controls.Canvas> contient également un <xref:System.Windows.Shapes.Rectangle> qui a les <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> mêmes limites que pour le premier <xref:System.Windows.Controls.Primitives.Popup>.  Notez que <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ne crée pas d’élément visible dans l’application ; l’exemple crée un <xref:System.Windows.Shapes.Rectangle> pour représenter le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Popup avec et sans PlacementRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Popup avec et sans PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Origine de la cible et point d’alignement de la fenêtre contextuelle  
 *L’origine de la cible* et le *point d’alignement de la fenêtre contextuelle* sont des points de référence sur la zone cible et la fenêtre contextuelle respectivement, qui sont utilisés pour le positionnement. Vous pouvez utiliser les <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> propriétés <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> et pour décaler la fenêtre contextuelle de la zone cible.  Les <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et<xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> sont relatifs à l’origine de la cible et au point d’alignement de la fenêtre contextuelle. La valeur de la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété détermine où se trouvent l’origine de la cible et le point d’alignement de la fenêtre contextuelle.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> et affecte à <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> la <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriété et la valeur 20.  La <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété a la <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> valeur (valeur par défaut). par conséquent, l’origine de la cible est l’angle inférieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle <xref:System.Windows.Controls.Primitives.Popup>est l’angle supérieur gauche du.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Positionnement de la fenêtre contextuelle avec point d’alignement d’origine cible](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Popup avec HorizontalOffset et VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Comment les propriétés fonctionnent ensemble  
 Les valeurs de <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>et <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> doivent être considérées ensemble pour déterminer la zone cible correcte, l’origine de la cible et le point d’alignement de la fenêtre contextuelle.  Par exemple, si la valeur de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, il n’y a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> aucun objet cible, est ignoré et la zone cible est la limite du pointeur de la souris. En revanche, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> si est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> parent ou détermine l’objet cible et <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> détermine la zone cible.  
  
 Le tableau suivant décrit l’objet cible, la zone cible, l’origine de la cible et le point d' <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> alignement <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> de la fenêtre contextuelle <xref:System.Windows.Controls.Primitives.PlacementMode> , et indique si et sont utilisés pour chaque valeur d’énumération.  
  
|PlacementMode|Objet cible|Zone cible|Origine de la cible|Point d’alignement de la fenêtre contextuelle|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>est ignoré.|L’écran, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’écran.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>est ignoré.|L’écran, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’écran.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’objet cible.|L’angle inférieur gauche de la zone cible.|L’angle supérieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’objet cible.|Le centre de la zone cible.|Centre de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’objet cible.|Défini par le <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Défini par le <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|L’angle supérieur droit de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>est ignoré.|Les limites du pointeur de souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>est ignoré.|L’angle inférieur gauche de la zone cible.|L’angle supérieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>est ignoré.|Les limites du pointeur de souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>est ignoré.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’objet cible.|L’angle supérieur droit de la zone cible.|L’angle supérieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> Est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|L’angle inférieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Les illustrations suivantes montrent le <xref:System.Windows.Controls.Primitives.Popup>, la zone cible, l’origine de la cible et le point <xref:System.Windows.Controls.Primitives.PlacementMode> d’alignement de la fenêtre contextuelle pour chaque valeur. Dans chaque figure, la zone cible est jaune et la <xref:System.Windows.Controls.Primitives.Popup> est bleue.  
  
 ![Popup avec positionnement absolu ou AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "Placement est Absolute ou AbsolutePoint.")    
  
 ![Fenêtre contextuelle avec positionnement en bas] Le (./media/popup-placement-behavior/popup-placement-bottom.png "positionnement est en bas.")   
  
 ![Popup avec positionnement centré](./media/popup-placement-behavior/popup-placement-center.png "Placement est centré.")    
  
 ![Popup avec positionnement à gauche] Le (./media/popup-placement-behavior/popup-placement-left.png "positionnement est conservé.")   
  
 ![Popup avec positionnement de la souris] Le (./media/popup-placement-behavior/popup-placement-mouse.png "positionnement est Mouse.")  
  
 ![Popup avec positionnement positionnement MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Placement est positionnement MousePoint.")  
  
 ![Popup avec positionnement relatif ou RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "Placement est relatif ou RelativePoint.")    
  
 ![Popup avec positionnement à droite](./media/popup-placement-behavior/popup-placement-right.png "Le positionnement est correct.")    
  
 ![Popup avec positionnement supérieur] Le (./media/popup-placement-behavior/popup-placement-top.png "positionnement est Top.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Lorsque la fenêtre contextuelle est en contact avec le bord de l’écran  
 Pour des raisons de sécurité <xref:System.Windows.Controls.Primitives.Popup> , un ne peut pas être masqué par le bord d’un écran. L’un des trois événements suivants se produit lorsque <xref:System.Windows.Controls.Primitives.Popup> le rencontre un bord d’écran :  
  
- La fenêtre contextuelle s’aligne sur le bord de l’écran qui masquerait le <xref:System.Windows.Controls.Primitives.Popup>.  
  
- La fenêtre contextuelle utilise un point d’alignement différent.  
  
- La fenêtre contextuelle utilise une origine de cible et un point d’alignement différents.  
  
 Ces options sont décrites plus loin dans cette section.  
  
 Le comportement du <xref:System.Windows.Controls.Primitives.Popup> lorsqu’il rencontre un bord d’écran dépend de la valeur de la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété et du bord d’écran que la fenêtre contextuelle rencontre. Le tableau suivant résume le comportement lorsque <xref:System.Windows.Controls.Primitives.Popup> rencontre un bord d’écran pour chaque <xref:System.Windows.Controls.Primitives.PlacementMode> valeur.  
  
|PlacementMode|Bord supérieur|Bord inférieur|Bord gauche|Bord droit|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Alignement sur le bord supérieur.|Le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche <xref:System.Windows.Controls.Primitives.Popup>de.|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit <xref:System.Windows.Controls.Primitives.Popup>de.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Alignement sur le bord supérieur.|L’origine de la cible devient l’angle supérieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche <xref:System.Windows.Controls.Primitives.Popup>de.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|L’origine de la cible devient l’angle supérieur droit de la zone cible et le point d’alignement de la fenêtre contextuelle devient l’angle supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Alignement sur le bord supérieur.|L’origine de la cible devient l’angle supérieur gauche de la zone cible (les limites du pointeur de la souris) et le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche <xref:System.Windows.Controls.Primitives.Popup>de.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Alignement sur le bord supérieur.|Le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche <xref:System.Windows.Controls.Primitives.Popup>de.|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Alignement sur le bord supérieur.|Le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche <xref:System.Windows.Controls.Primitives.Popup>de.|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|L’origine de la cible devient l’angle supérieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit <xref:System.Windows.Controls.Primitives.Popup>de.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|L’origine de la cible devient l’angle inférieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle devient l’angle supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de. En effet, c’est le même que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alignement sur le bord de l’écran  
 Un <xref:System.Windows.Controls.Primitives.Popup> peut s’aligner sur le bord de l’écran en le repositionnant pour que l' <xref:System.Windows.Controls.Primitives.Popup> ensemble soit visible à l’écran.  Lorsque cela se produit, la distance entre l’origine de la cible et le point d’alignement de la <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> fenêtre <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>contextuelle peut être différente des valeurs de et. Quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, ou<xref:System.Windows.Controls.Primitives.PlacementMode.Center> ,le<xref:System.Windows.Controls.Primitives.Popup> s’aligne sur chaque bord d’écran. <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>  Par exemple, supposons qu' <xref:System.Windows.Controls.Primitives.Popup> un <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a défini <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> sur <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> et défini sur 100.  Si le bord inférieur de l’écran masque tout ou partie du <xref:System.Windows.Controls.Primitives.Popup>, le <xref:System.Windows.Controls.Primitives.Popup> se repositionne le long du bord inférieur de l’écran et la distance verticale entre l’origine de la cible et le point d’alignement de la fenêtre contextuelle est inférieure à 100. L’illustration suivante démontre ce comportement.  
  
 ![Fenêtre contextuelle qui s’aligne sur le bord de l’écran] La (./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "fenêtre contextuelle s’aligne sur le bord de l’écran.")    
  
### <a name="changing-the-popup-alignment-point"></a>Modification du point d’alignement de la fenêtre contextuelle  
 Si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, ou<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, le point d’alignement de la fenêtre contextuelle change lorsque la fenêtre contextuelle rencontre le bord inférieur ou droit de l’écran. <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>  
  
 L’illustration suivante montre que lorsque le bord inférieur de l’écran masque tout ou partie du <xref:System.Windows.Controls.Primitives.Popup>, le point d’alignement de la fenêtre contextuelle est l’angle inférieur <xref:System.Windows.Controls.Primitives.Popup>gauche de.  
  
 ![Nouveau point d’alignement en raison du bord inférieur de l’écran](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup rencontre le bord inférieur de l’écran et modifie le point d’alignement de la fenêtre contextuelle.")  

 L’illustration suivante montre que lorsque le <xref:System.Windows.Controls.Primitives.Popup> est masqué par le bord droit <xref:System.Windows.Controls.Primitives.Popup>de l’écran, le point d’alignement de la fenêtre contextuelle est le coin supérieur droit du.  
  
 ![Nouveau point d’alignement de la fenêtre contextuelle en raison du bord de l’écran](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup rencontre le bord droit de l’écran et modifie le point d’alignement de la fenêtre contextuelle.")    
  
 Si le <xref:System.Windows.Controls.Primitives.Popup> rencontre les bords inférieur et droit <xref:System.Windows.Controls.Primitives.Popup>de l’écran, le point d’alignement de la fenêtre contextuelle est le coin inférieur droit du.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Modification de l’origine de la cible et du point d’alignement de la fenêtre contextuelle  
 Quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, ,<xref:System.Windows.Controls.Primitives.PlacementMode.Left> ,ou<xref:System.Windows.Controls.Primitives.PlacementMode.Top>, l’origine de la cible et le point d’alignement de la fenêtre contextuelle changent si un bord d’écran spécifique est rencontré. <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> <xref:System.Windows.Controls.Primitives.PlacementMode.Right>  Le bord d’écran à l’origine de la modification de la <xref:System.Windows.Controls.Primitives.PlacementMode> position dépend de la valeur.  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> et que <xref:System.Windows.Controls.Primitives.Popup> le rencontre le bord inférieur de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle inférieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord inférieur de l’écran] Le (./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "positionnement est bas et la fenêtre contextuelle rencontre le bord inférieur de l’écran.")    
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Left> et que <xref:System.Windows.Controls.Primitives.Popup> le rencontre le bord gauche de l’écran, l’origine de la cible est l’angle supérieur droit de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord gauche de l’écran] Le (./media/popup-placement-behavior/popup-placement-left-screen-edge.png "positionnement est laissé et la fenêtre contextuelle rencontre le bord gauche de l’écran.")  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Right> et que <xref:System.Windows.Controls.Primitives.Popup> le est le bord droit de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle supérieur droit de <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord droit de l’écran] Le (./media/popup-placement-behavior/popup-placement-right-screen-edge.png "positionnement est Right et la fenêtre contextuelle rencontre le bord droit de l’écran.")  

 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Top> et que <xref:System.Windows.Controls.Primitives.Popup> le rencontre le bord supérieur de l’écran, l’origine de la cible est l’angle inférieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord supérieur de l’écran] Le (./media/popup-placement-behavior/popup-placement-top-screen-edge.png "positionnement est Top et la fenêtre contextuelle rencontre le bord supérieur de l’écran.")  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> a <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> la forme <xref:System.Windows.Controls.Primitives.Popup> et que le rencontre le bord inférieur de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible (les limites du pointeur de la souris) et l’alignement de la fenêtre contextuelle point est l’angle inférieur gauche de <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nouveau point d’alignement en raison du bord de la souris près de l’écran] L' (./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "emplacement est Mouse et la fenêtre contextuelle rencontre le bord inférieur de l’écran.")    
  
### <a name="customizing-popup-placement"></a>Personnalisation du positionnement d’un contrôle Popup  
 Vous pouvez personnaliser l’origine de la cible et le point d’alignement <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> de la <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>fenêtre contextuelle en affectant à la propriété la valeur. Définissez ensuite un <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> délégué qui retourne un ensemble de points de positionnement possibles et les axes principaux (par ordre de préférence) <xref:System.Windows.Controls.Primitives.Popup>pour le. Le point qui affiche la plus grande partie du <xref:System.Windows.Controls.Primitives.Popup> est sélectionné.  La position du <xref:System.Windows.Controls.Primitives.Popup> est ajustée automatiquement si le <xref:System.Windows.Controls.Primitives.Popup> est masqué par le bord de l’écran. Pour obtenir un exemple, consultez [Spécifier une position de menu contextuel personnalisée](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Voir aussi

- [Popup Placement Sample](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS) (Exemple de positionnement de fenêtre contextuelle)
