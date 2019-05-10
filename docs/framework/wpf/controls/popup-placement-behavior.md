---
title: Comportement de positionnement de Popup
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: a84ff7def944e1a037f4c26611e33de93ed9861e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650757"
---
# <a name="popup-placement-behavior"></a>Comportement de positionnement de Popup
Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche le contenu dans une fenêtre distincte qui flotte au-dessus d’une application. Vous pouvez spécifier la position d’un <xref:System.Windows.Controls.Primitives.Popup> par rapport à un contrôle, la souris ou l’écran à l’aide de la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés.  Ces propriétés fonctionnent ensemble pour vous permettent une grande souplesse en spécifiant la position de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
>  Le <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ContextMenu> classes également définir ces cinq propriétés et se comportent de la même façon.  

<a name="Positioning"></a>   
## <a name="positioning-the-popup"></a>Positionnement de la fenêtre contextuelle  
 Le placement d’un <xref:System.Windows.Controls.Primitives.Popup> peut être relatif à un <xref:System.Windows.UIElement> ou à l’écran entier.  L’exemple suivant crée quatre <xref:System.Windows.Controls.Primitives.Popup> contrôles qui sont relatives à un <xref:System.Windows.UIElement>: dans ce cas, une image. Tous les <xref:System.Windows.Controls.Primitives.Popup> contrôles ont le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriété définie sur `image1`, mais chaque <xref:System.Windows.Controls.Primitives.Popup> a une valeur différente pour la propriété de positionnement.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 L’illustration suivante montre l’image et le <xref:System.Windows.Controls.Primitives.Popup> contrôles  
  
 ![Image avec quatre contrôles popup](./media/popup-placement-behavior/popup-placement-intro.png "Image avec quatre contrôles Popup")    
  
 Cet exemple simple montre comment définir le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> et <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriétés, mais à l’aide de la <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés, vous contrôlez davantage où le <xref:System.Windows.Controls.Primitives.Popup> est positionné.  
  
<a name="Definitions"></a>   
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Définitions des termes du contrat : Anatomie d’une fenêtre contextuelle  
 Les termes suivants sont utiles pour comprendre comment la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>, et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés sont liés entre eux et le <xref:System.Windows.Controls.Primitives.Popup>:  
  
- Objet cible  
  
- Zone cible  
  
- Origine de la cible  
  
- Point d’alignement de la fenêtre contextuelle  
  
 Ces termes fournissent un moyen pratique pour faire référence aux différents aspects de la <xref:System.Windows.Controls.Primitives.Popup> et le contrôle auquel il est associé.  
  
### <a name="target-object"></a>Objet cible  
 Le *objet cible* est l’élément qui le <xref:System.Windows.Controls.Primitives.Popup> est associé. Si la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est définie, elle spécifie l’objet cible.  Si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> n’est pas définie et la <xref:System.Windows.Controls.Primitives.Popup> a un parent, le parent est l’objet cible.  S’il existe aucune <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> valeur et aucun parent, il n’existe aucun objet cible et le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport à l’écran.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> qui est l’enfant d’un <xref:System.Windows.Controls.Canvas>.  L’exemple ne définit pas le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> propriété sur le <xref:System.Windows.Controls.Primitives.Popup>. La valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, la <xref:System.Windows.Controls.Primitives.Popup> apparaît sous le <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 L’illustration suivante montre que le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport à la <xref:System.Windows.Controls.Canvas>.  
  
 ![Contrôle Popup sans PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Popup sans PlacementTarget.")  

 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> qui est l’enfant d’un <xref:System.Windows.Controls.Canvas>, mais cette fois le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> a la valeur `ellipse1`, de sorte que la fenêtre contextuelle apparaît sous le <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 L’illustration suivante montre que le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport à la <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Popup positionné par rapport à une ellipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "fenêtre contextuelle avec PlacementTarget")    
  
> [!NOTE]
>  Pour <xref:System.Windows.Controls.ToolTip>, la valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Pour <xref:System.Windows.Controls.ContextMenu>, la valeur par défaut <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Ces valeurs sont expliquées plus loin, dans la section « Comment les propriétés fonctionnent ensemble ».  
  
### <a name="target-area"></a>Zone cible  
 Le *zone cible* est la zone de l’écran qui le <xref:System.Windows.Controls.Primitives.Popup> est relative. Dans les exemples précédents, le <xref:System.Windows.Controls.Primitives.Popup> s’aligne sur les limites de l’objet cible, mais dans certains cas, le <xref:System.Windows.Controls.Primitives.Popup> est aligné avec d’autres limites, même si le <xref:System.Windows.Controls.Primitives.Popup> a un objet cible.  Si le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> propriété est définie, la zone cible est différente des limites de l’objet cible.  
  
 L’exemple suivant crée deux <xref:System.Windows.Controls.Canvas> d’objets, chacun d’eux contenant un <xref:System.Windows.Shapes.Rectangle> et un <xref:System.Windows.Controls.Primitives.Popup>.  Dans les deux cas, la cible de l’objet pour le <xref:System.Windows.Controls.Primitives.Popup> est le <xref:System.Windows.Controls.Canvas>. Le <xref:System.Windows.Controls.Primitives.Popup> dans la première <xref:System.Windows.Controls.Canvas> a le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> défini, avec ses <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>, et <xref:System.Windows.Rect.Height%2A> propriétés la valeur 50, 50, 50 et 100, respectivement. Le <xref:System.Windows.Controls.Primitives.Popup> dans la seconde <xref:System.Windows.Controls.Canvas> n’a pas le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> défini.  Par conséquent, la première <xref:System.Windows.Controls.Primitives.Popup> est positionnée au-dessous le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> et le second <xref:System.Windows.Controls.Primitives.Popup> est positionnée au-dessous du <xref:System.Windows.Controls.Canvas>. Chaque <xref:System.Windows.Controls.Canvas> contient également un <xref:System.Windows.Shapes.Rectangle> qui a les mêmes limites que le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> pour la première <xref:System.Windows.Controls.Primitives.Popup>.  Notez que le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ne crée pas d’élément visible dans l’application ; l’exemple crée un <xref:System.Windows.Shapes.Rectangle> pour représenter le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Popup avec et sans PlacementRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Popup avec et sans PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Origine de la cible et point d’alignement de la fenêtre contextuelle  
 *L’origine de la cible* et le *point d’alignement de la fenêtre contextuelle* sont des points de référence sur la zone cible et la fenêtre contextuelle respectivement, qui sont utilisés pour le positionnement. Vous pouvez utiliser la <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés pour décaler la fenêtre contextuelle à partir de la zone cible.  Le <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> sont relatives à l’origine de la cible et le point d’alignement. La valeur de la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété détermine où se trouvent le point d’alignement cible origine et la fenêtre contextuelle.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> et définit le <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> 20 aux propriétés.  Le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété est définie sur <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (la valeur par défaut), par conséquent, l’origine de la cible est l’angle inférieur gauche de la zone cible et le point d’alignement de fenêtre contextuelle est l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Positionnement Popup avec point d’alignement original cible](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "fenêtre contextuelle avec HorizontalOffset et VerticalOffset.")    
  
<a name="How"></a>   
## <a name="how-the-properties-work-together"></a>Comment les propriétés fonctionnent ensemble  
 Les valeurs de <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, et <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> doivent être considérées conjointement pour déterminer la zone de la cible, l’origine de la cible et point d’alignement.  Par exemple, si la valeur de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, il n’existe aucun objet cible, le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré, et la zone cible est les limites du pointeur de la souris. En revanche, si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent détermine l’objet cible et <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> détermine la zone cible.  
  
 Le tableau suivant décrit l’objet cible, la zone cible, origine de la cible et son point d’alignement et indique si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> et <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sont utilisés pour chaque <xref:System.Windows.Controls.Primitives.PlacementMode> valeur d’énumération.  
  
|PlacementMode|Objet cible|Zone cible|Origine de la cible|Point d’alignement de la fenêtre contextuelle|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|L’écran, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’écran.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|L’écran, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’écran.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle inférieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le centre de la zone cible.|Le centre de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Défini par le <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Défini par le <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|L’angle supérieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|Les limites du pointeur de souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré.|L’angle inférieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|Les limites du pointeur de souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur droit de la zone cible.|L’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> si elle est définie.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|L’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Les illustrations suivantes montrent le <xref:System.Windows.Controls.Primitives.Popup>, zone cible, origine de la cible et l’alignement du menu contextuel point pour chaque <xref:System.Windows.Controls.Primitives.PlacementMode> valeur. Dans chacune des figures, la zone cible est jaune et le <xref:System.Windows.Controls.Primitives.Popup> est bleu.  
  
 ![Popup avec positionnement Absolute ou AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "le positionnement est Absolute ou AbsolutePoint.")    
  
 ![Popup avec positionnement Bottom](./media/popup-placement-behavior/popup-placement-bottom.png "le positionnement est bas.")   
  
 ![Popup avec positionnement Center](./media/popup-placement-behavior/popup-placement-center.png "le positionnement est Center.")    
  
 ![Popup avec positionnement Left](./media/popup-placement-behavior/popup-placement-left.png "le positionnement est Left.")   
  
 ![Popup avec positionnement Mouse](./media/popup-placement-behavior/popup-placement-mouse.png "le positionnement est Mouse.")  
  
 ![Fenêtre contextuelle avec positionnement MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "le positionnement est MousePoint.")  
  
 ![Popup avec positionnement Relative ou RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "le positionnement est Relative ou RelativePoint.")    
  
 ![Popup avec positionnement Right](./media/popup-placement-behavior/popup-placement-right.png "le positionnement est Right.")    
  
 ![Popup avec positionnement Top](./media/popup-placement-behavior/popup-placement-top.png "le positionnement est Top.")    
  
<a name="When"></a>   
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Lorsque la fenêtre contextuelle est en contact avec le bord de l’écran  
 Pour des raisons de sécurité, un <xref:System.Windows.Controls.Primitives.Popup> ne peut pas être caché par le bord d’un écran. Une des trois actions suivantes se produit lorsque le <xref:System.Windows.Controls.Primitives.Popup> rencontre un bord d’écran :  
  
- La fenêtre contextuelle se réaligne le long du bord de l’écran qui masquerait le <xref:System.Windows.Controls.Primitives.Popup>.  
  
- La fenêtre contextuelle utilise un point d’alignement différent.  
  
- La fenêtre contextuelle utilise une origine de cible et un point d’alignement différents.  
  
 Ces options sont décrites plus loin dans cette section.  
  
 Le comportement de la <xref:System.Windows.Controls.Primitives.Popup> quand il rencontre un bord d’écran dépend de la valeur de la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> rencontre la fenêtre contextuelle de bord d’écran de propriété et qui. Le tableau suivant récapitule le comportement lorsque le <xref:System.Windows.Controls.Primitives.Popup> rencontre un bord d’écran pour chaque <xref:System.Windows.Controls.Primitives.PlacementMode> valeur.  
  
|PlacementMode|Bord supérieur|Bord inférieur|Bord gauche|Bord droit|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Alignement sur le bord supérieur.|Le point d’alignement de fenêtre contextuelle devient l’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Le point d’alignement de fenêtre contextuelle devient l’angle supérieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Alignement sur le bord supérieur.|L’origine de la cible devient l’angle supérieur gauche de la zone cible et le point d’alignement de fenêtre contextuelle devient l’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|L’origine de la cible devient l’angle supérieur droit de la zone cible et le point d’alignement de fenêtre contextuelle devient l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Alignement sur le bord supérieur.|L’origine de la cible devient l’angle supérieur gauche de la zone cible (les limites du pointeur de la souris) et le point d’alignement de fenêtre contextuelle devient l’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Alignement sur le bord supérieur.|Le point d’alignement de fenêtre contextuelle devient l’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Alignement sur le bord supérieur.|Le point d’alignement de fenêtre contextuelle devient l’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|L’origine de la cible devient l’angle supérieur gauche de la zone cible et le point d’alignement de fenêtre contextuelle devient l’angle supérieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|L’origine de la cible devient l’angle inférieur gauche de la zone cible et le point d’alignement de fenêtre contextuelle devient l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>. En effet, il s’agit du même que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alignement sur le bord de l’écran  
 Un <xref:System.Windows.Controls.Primitives.Popup> peut s’aligner sur le bord de l’écran en se repositionnant donc l’intégralité de <xref:System.Windows.Controls.Primitives.Popup> est visible sur l’écran.  Lorsque cela se produit, la distance entre le point d’alignement origine et la fenêtre contextuelle cible peut-être différer des valeurs de <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, ou <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, le <xref:System.Windows.Controls.Primitives.Popup> s’aligne sur chaque bord de l’écran.  Par exemple, supposons qu’un <xref:System.Windows.Controls.Primitives.Popup> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> définie sur <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> défini à 100.  Si le bord inférieur de l’écran masque tout ou partie de la <xref:System.Windows.Controls.Primitives.Popup>, le <xref:System.Windows.Controls.Primitives.Popup> se repositionne le long du bord inférieur de l’écran et la distance verticale entre l’origine de la cible et la fenêtre contextuelle point d’alignement est inférieure à 100. L’illustration suivante démontre ce comportement.  
  
 ![Fenêtre contextuelle qui s’aligne sur le bord d’écran](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "fenêtre contextuelle s’aligne sur le bord de l’écran.")    
  
### <a name="changing-the-popup-alignment-point"></a>Modification du point d’alignement de la fenêtre contextuelle  
 Si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, ou <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, le point d’alignement de fenêtre contextuelle change lorsque la fenêtre contextuelle rencontre du bord inférieur ou droit de l’écran.  
  
 L’illustration suivante montre que lorsque le bord d’écran inférieur masque tout ou partie de la <xref:System.Windows.Controls.Primitives.Popup>, le point d’alignement de fenêtre contextuelle est l’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord d’écran de bas](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup rencontre le bord inférieur de l’écran et modifie le point d’alignement.")  

 L’illustration suivante montre que lorsque le <xref:System.Windows.Controls.Primitives.Popup> est masqué par le bord droit de l’écran, le point d’alignement de fenêtre contextuelle est l’angle supérieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouvel alignement Popup en raison du bord de l’écran](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup rencontre le bord droit de l’écran et modifie le point d’alignement.")    
  
 Si le <xref:System.Windows.Controls.Primitives.Popup> rencontre les bords inférieur et droit de l’écran, le point d’alignement de fenêtre contextuelle est l’angle inférieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Modification de l’origine de la cible et du point d’alignement de la fenêtre contextuelle  
 Lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, ou <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, point de l’alignement d’origine et la fenêtre contextuelle de cible change si un bord d’écran certaines est rencontré.  Le bord d’écran qui provoque la modification de la position varie selon le <xref:System.Windows.Controls.Primitives.PlacementMode> valeur.  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord inférieur de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible et le point d’alignement de fenêtre contextuelle est l’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord d’écran de bas](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "le positionnement est Bottom et la fenêtre contextuelle rencontre le bord inférieur de l’écran.")    
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Left> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord gauche de l’écran, l’origine de la cible est l’angle supérieur droit de la zone cible et le point d’alignement de fenêtre contextuelle est l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord gauche de l’écran](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "le positionnement est Left et la fenêtre contextuelle rencontre le bord gauche de l’écran.")  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Right> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord droit de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible et le point d’alignement de fenêtre contextuelle est l’angle supérieur droit de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord de droit de l’écran](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "le positionnement est Right et la fenêtre contextuelle rencontre le bord droit de l’écran.")  

 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Top> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord supérieur de l’écran, l’origine de la cible est l’angle inférieur gauche de la zone cible et le point d’alignement de fenêtre contextuelle est l’angle supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord supérieur de l’écran](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "le positionnement est Top et la fenêtre contextuelle rencontre le bord supérieur de l’écran.")  
  
 L’illustration suivante montre que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> et <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord inférieur de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible (les limites du pointeur de la souris) et l’alignement de la fenêtre contextuelle point est l’angle inférieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![nouveau point d’alignement en raison de la souris près de bord de l’écran](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "le positionnement est Mouse et la fenêtre contextuelle rencontre le bord inférieur de l’écran.")    
  
### <a name="customizing-popup-placement"></a>Personnalisation du positionnement d’un contrôle Popup  
 Vous pouvez personnaliser le point d’alignement cible origine et la fenêtre contextuelle en définissant le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Définissez ensuite un <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> délégué qui retourne un ensemble de points de positionnement possibles et les axes principaux (dans l’ordre de préférence) pour le <xref:System.Windows.Controls.Primitives.Popup>. Le point qui présente la plus grande partie de la <xref:System.Windows.Controls.Primitives.Popup> est sélectionnée.  La position de la <xref:System.Windows.Controls.Primitives.Popup> est ajustée automatiquement si le <xref:System.Windows.Controls.Primitives.Popup> est caché par le bord de l’écran. Pour obtenir un exemple, consultez [Spécifier une position de menu contextuel personnalisée](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Voir aussi

- [Popup Placement Sample](https://github.com/dotnet/samples/tree/master/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS) (Exemple de positionnement de fenêtre contextuelle)
