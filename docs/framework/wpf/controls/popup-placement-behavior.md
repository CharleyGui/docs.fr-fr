---
title: Comportement de positionnement de Popup
description: Découvrez comment spécifier la position d’une fenêtre contextuelle Windows Presentation Foundation par rapport à un contrôle, la souris ou l’écran en utilisant des propriétés.
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 8184805518bc56693ead4c7d1f0e9a1bff9bff8f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167752"
---
# <a name="popup-placement-behavior"></a>Comportement de positionnement de Popup
Un contrôle <xref:System.Windows.Controls.Primitives.Popup> affiche le contenu dans une fenêtre distincte qui flotte au-dessus d’une application. Vous pouvez spécifier la position d’un <xref:System.Windows.Controls.Primitives.Popup> par rapport à un contrôle, la souris ou l’écran en utilisant les propriétés <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>.  Utilisées conjointement, ces propriétés vous donnent toute la souplesse nécessaire pour spécifier la position du <xref:System.Windows.Controls.Primitives.Popup>.  
  
> [!NOTE]
> Les classes <xref:System.Windows.Controls.ToolTip> et <xref:System.Windows.Controls.ContextMenu> définissent également ces cinq propriétés et se comportent de la même façon.  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>Positionnement de la fenêtre contextuelle  
 Le positionnement d’un <xref:System.Windows.Controls.Primitives.Popup> peut être relatif à un <xref:System.Windows.UIElement> ou à l’écran entier.  L’exemple suivant crée quatre contrôles <xref:System.Windows.Controls.Primitives.Popup> relatifs à un <xref:System.Windows.UIElement>, dans le cas présent, une image. Tous les contrôles <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ont la propriété <xref:System.Windows.Controls.Primitives.Popup> définie avec la valeur `image1`, mais chaque <xref:System.Windows.Controls.Primitives.Popup> a une valeur différente pour la propriété de positionnement.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 L’illustration suivante montre l’image et les contrôles <xref:System.Windows.Controls.Primitives.Popup>  
  
 ![Image avec quatre contrôles Popup](./media/popup-placement-behavior/popup-placement-intro.png "Image avec quatre contrôles popup")
  
 Cet exemple simple montre comment définir les propriétés <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> et <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, mais en utilisant les propriétés <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>, vous avez encore plus de contrôle sur l’emplacement où se trouve le <xref:System.Windows.Controls.Primitives.Popup>.  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Définition des termes : Anatomie d’une fenêtre contextuelle  
 Les termes suivants sont utiles pour comprendre comment les propriétés <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>, <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> sont liées les unes aux autres et au <xref:System.Windows.Controls.Primitives.Popup> :  
  
- Objet cible  
  
- Zone cible  
  
- Origine de la cible  
  
- Point d’alignement de la fenêtre contextuelle  
  
 Ces termes offrent un moyen pratique de se référer aux différents aspects du <xref:System.Windows.Controls.Primitives.Popup> et du contrôle auquel il est associé.  
  
### <a name="target-object"></a>Objet cible  
 L’*objet cible* est l’élément auquel le <xref:System.Windows.Controls.Primitives.Popup> est associé. Si la propriété <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est définie, elle spécifie l’objet cible.  Si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> n’est pas défini et que le <xref:System.Windows.Controls.Primitives.Popup> a un parent, le parent est l’objet cible.  S’il n’y a aucune valeur <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> et aucun parent, il n’y a aucun objet cible et le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport à l’écran.  
  
 L'exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> qui est l’enfant d’un <xref:System.Windows.Controls.Canvas>.  L’exemple ne définit pas la propriété <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> sur le <xref:System.Windows.Controls.Primitives.Popup>. La valeur par défaut de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>, donc le <xref:System.Windows.Controls.Primitives.Popup> apparaît sous le <xref:System.Windows.Controls.Canvas>.  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 L’illustration suivante montre que le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport au <xref:System.Windows.Controls.Canvas>.  
  
 ![Contrôle Popup sans PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Fenêtre contextuelle sans PlacementTarget.")  

 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> qui est l’enfant d’un <xref:System.Windows.Controls.Canvas>, mais cette fois, la <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est définie sur `ellipse1`, de sorte que la fenêtre contextuelle apparaisse sous <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 L’illustration suivante montre que le <xref:System.Windows.Controls.Primitives.Popup> est positionné par rapport au <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Fenêtre contextuelle positionnée par rapport à une ellipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Fenêtre contextuelle avec PlacementTarget")
  
> [!NOTE]
> Pour <xref:System.Windows.Controls.ToolTip>, la valeur par défaut de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>.  Pour <xref:System.Windows.Controls.ContextMenu>, la valeur par défaut de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>. Ces valeurs sont expliquées plus loin, dans la section « Comment les propriétés fonctionnent ensemble ».  
  
### <a name="target-area"></a>Zone cible  
 La *zone cible* correspond à la zone de l’écran à laquelle le <xref:System.Windows.Controls.Primitives.Popup> est lié. Dans les exemples précédents, le <xref:System.Windows.Controls.Primitives.Popup> est aligné sur les limites de l’objet cible, mais dans certains cas, le <xref:System.Windows.Controls.Primitives.Popup> est aligné sur d’autres limites, même si le <xref:System.Windows.Controls.Primitives.Popup> a un objet cible.  Si la propriété <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est définie, la zone cible est différente des limites de l’objet cible.  
  
 L’exemple suivant crée deux objets <xref:System.Windows.Controls.Canvas>, chacun contenant un <xref:System.Windows.Shapes.Rectangle> et un <xref:System.Windows.Controls.Primitives.Popup>.  Dans les deux cas, l’objet cible pour le <xref:System.Windows.Controls.Primitives.Popup> est le <xref:System.Windows.Controls.Canvas>. Le <xref:System.Windows.Controls.Primitives.Popup> du premier <xref:System.Windows.Controls.Canvas> a le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> défini, avec ses propriétés <xref:System.Windows.Rect.X%2A>, <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A> et <xref:System.Windows.Rect.Height%2A> définies respectivement avec les valeurs 50, 50, 50 et 100. Le <xref:System.Windows.Controls.Primitives.Popup> du second <xref:System.Windows.Controls.Canvas> n’a pas le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> défini.  En conséquence, le premier <xref:System.Windows.Controls.Primitives.Popup> est positionné sous le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> et le second <xref:System.Windows.Controls.Primitives.Popup> est positionné sous le <xref:System.Windows.Controls.Canvas>. Chaque <xref:System.Windows.Controls.Canvas> contient également un <xref:System.Windows.Shapes.Rectangle> qui a les mêmes limites que le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> du premier <xref:System.Windows.Controls.Primitives.Popup>.  Notez que le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ne crée pas d’élément visible dans l’application ; l’exemple crée un <xref:System.Windows.Shapes.Rectangle> pour représenter le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>.  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Fenêtre contextuelle avec et sans PlacementRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Fenêtre contextuelle avec et sans PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Origine de la cible et point d’alignement de la fenêtre contextuelle  
 *L’origine de la cible* et le *point d’alignement de la fenêtre contextuelle* sont des points de référence sur la zone cible et la fenêtre contextuelle respectivement, qui sont utilisés pour le positionnement. Vous pouvez utiliser les propriétés <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> pour décaler la fenêtre contextuelle de la zone cible.  Les <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> sont relatifs à l’origine de la cible et au point d’alignement de la fenêtre contextuelle. La valeur de la propriété <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> détermine où se trouvent l’origine de la cible et le point d’alignement de la fenêtre contextuelle.  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.Primitives.Popup> et définit les propriétés <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> avec la valeur 20.  La propriété <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est définie avec <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> (la valeur par défaut), donc l’origine de la cible est l’angle inférieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Positionnement de fenêtre contextuelle avec point d’alignement original cible](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Fenêtre contextuelle avec HorizontalOffset et VerticalOffset.")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>Comment les propriétés fonctionnent ensemble  
 Les valeurs de <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>et <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> doivent être considérées ensemble pour déterminer la zone cible, l’origine de la cible et le point d’alignement de la fenêtre contextuelle appropriés.  Par exemple, si la valeur de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, il n’y a aucun objet cible, le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré et la zone cible est la limite du pointeur de la souris. En revanche, si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou le parent détermine l’objet cible et le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> détermine la zone cible.  
  
 Le tableau suivant décrit l’objet cible, la zone cible, l’origine de la cible et le point d’alignement de la fenêtre contextuelle, et indique si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> et <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sont utilisés pour chaque valeur d’énumération <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
|PlacementMode|Objet cible|Zone cible|Origine de la cible|Point d’alignement de la fenêtre contextuelle|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|L’écran, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’écran.|L’angle supérieur gauche de la zone cible.|Angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|L’écran, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’écran.|L’angle supérieur gauche de la zone cible.|Angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle inférieur gauche de la zone cible.|Angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Le centre de la zone cible.|Centre du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|Défini par le <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|Défini par le <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|Angle supérieur droit du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|Les limites du pointeur de souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré.|L’angle inférieur gauche de la zone cible.|Angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|Les limites du pointeur de souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré.|L’angle supérieur gauche de la zone cible.|Angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|Angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|Angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur droit de la zone cible.|Angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ou parent.|Objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  Le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est relatif à l’objet cible.|L’angle supérieur gauche de la zone cible.|Angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|  
  
 Les illustrations suivantes montrent le <xref:System.Windows.Controls.Primitives.Popup>, la zone cible, l’origine de la cible et le point d’alignement de la fenêtre contextuelle pour chaque valeur <xref:System.Windows.Controls.Primitives.PlacementMode>. Dans chaque figure, la zone cible est jaune et la <xref:System.Windows.Controls.Primitives.Popup> est bleue.  
  
 ![Fenêtre contextuelle avec positionnement Absolute ou AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "Le positionnement est Absolute ou AbsolutePoint.")
  
 ![Fenêtre contextuelle avec positionnement Bottom](./media/popup-placement-behavior/popup-placement-bottom.png "Le positionnement est Bottom.")
  
 ![Fenêtre contextuelle avec positionnement Center](./media/popup-placement-behavior/popup-placement-center.png "Le positionnement est Center.")
  
 ![Fenêtre contextuelle avec positionnement Left](./media/popup-placement-behavior/popup-placement-left.png "Le positionnement est Left.")
  
 ![Fenêtre contextuelle avec positionnement Mouse](./media/popup-placement-behavior/popup-placement-mouse.png "Le positionnement est Mouse.")  
  
 ![Fenêtre contextuelle avec positionnement MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Le positionnement est MousePoint.")  
  
 ![Fenêtre contextuelle avec positionnement Relative ou RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "Le positionnement est Relative ou RelativePoint.")
  
 ![Fenêtre contextuelle avec positionnement Right](./media/popup-placement-behavior/popup-placement-right.png "Le positionnement est Right.")
  
 ![Fenêtre contextuelle avec positionnement Top](./media/popup-placement-behavior/popup-placement-top.png "Le positionnement est Top.")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Lorsque la fenêtre contextuelle est en contact avec le bord de l’écran  
 Pour des raisons de sécurité, un <xref:System.Windows.Controls.Primitives.Popup> ne peut pas être masqué par le bord d’un écran. L’un des trois événements suivants se produit lorsque le <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord d’un écran :  
  
- La fenêtre contextuelle se réaligne le long du bord de l’écran qui masquerait le <xref:System.Windows.Controls.Primitives.Popup>.  
  
- La fenêtre contextuelle utilise un point d’alignement différent.  
  
- La fenêtre contextuelle utilise une origine de cible et un point d’alignement différents.  
  
 Ces options sont décrites plus loin dans cette section.  
  
 Le comportement du <xref:System.Windows.Controls.Primitives.Popup> lorsqu’il rencontre un bord d’écran dépend de la valeur de la propriété <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> et du bord d’écran que la fenêtre contextuelle rencontre. Le tableau suivant résume le comportement lorsque le <xref:System.Windows.Controls.Primitives.Popup> rencontre un bord d’écran pour chaque valeur <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
|PlacementMode|Bord supérieur|Bord inférieur|Bord gauche|Bord droit|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Alignement sur le bord supérieur.|Le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Alignement sur le bord supérieur.|L’origine de la cible devient l’angle supérieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|L’origine de la cible devient l’angle supérieur droit de la zone cible et le point d’alignement de la fenêtre contextuelle devient l’angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Alignement sur le bord supérieur.|L’origine de la cible devient l’angle supérieur gauche de la zone cible (les limites du pointeur de la souris) et le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Alignement sur le bord supérieur.|Le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Alignement sur le bord supérieur.|Le point d’alignement de la fenêtre contextuelle devient l’angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|L’origine de la cible devient l’angle supérieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit du <xref:System.Windows.Controls.Primitives.Popup>.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|L’origine de la cible devient l’angle inférieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle devient l’angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>. En effet, c’est pareil que lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alignement sur le bord de l’écran  
 Un <xref:System.Windows.Controls.Primitives.Popup> peut s’aligner sur le bord de l’écran en se repositionnant afin que le <xref:System.Windows.Controls.Primitives.Popup> soit visible à l’écran en entier.  Lorsque cela se produit, la distance entre l’origine de la cible et le point d’alignement de la fenêtre contextuelle peut être différente des valeurs de <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>. Quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>, <xref:System.Windows.Controls.Primitives.PlacementMode.Center>ou <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, le <xref:System.Windows.Controls.Primitives.Popup> s’aligne sur chaque bord d’écran.  Par exemple, supposons qu’un <xref:System.Windows.Controls.Primitives.Popup> a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> défini avec <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> défini avec la valeur 100.  Si le bord inférieur de l’écran masque tout ou partie du <xref:System.Windows.Controls.Primitives.Popup>, le <xref:System.Windows.Controls.Primitives.Popup> se repositionne le long du bord inférieur de l’écran, et la distance verticale entre l’origine de la cible et le point d’alignement de la fenêtre contextuelle est inférieure à 100. L’illustration suivante démontre ce comportement.  
  
 ![Fenêtre contextuelle alignée sur le bord de l’écran](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "La fenêtre contextuelle s’aligne sur le bord de l’écran.")
  
### <a name="changing-the-popup-alignment-point"></a>Modification du point d’alignement de la fenêtre contextuelle  
 Si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>ou <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, le point d’alignement de la fenêtre contextuelle change lorsque la fenêtre contextuelle rencontre le bord inférieur ou droit de l’écran.  
  
 L’illustration suivante montre que lorsque le bord inférieur de l’écran masque tout ou partie du <xref:System.Windows.Controls.Primitives.Popup>, le point d’alignement de la fenêtre contextuelle est l’angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord inférieur de l’écran](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "La fenêtre contextuelle est en contact avec le bord inférieur de l’écran et change son point d’alignement.")  

 L’illustration suivante montre que quand le <xref:System.Windows.Controls.Primitives.Popup> est masqué par le bord droit de l’écran, le point d’alignement de la fenêtre contextuelle est l’angle supérieur droit du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement de la fenêtre contextuelle en raison du bord de l’écran](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "La fenêtre contextuelle est en contact avec le bord droit de l’écran et change son point d’alignement.")
  
 Si le <xref:System.Windows.Controls.Primitives.Popup> rencontre les bords inférieur et droit de l’écran, le point d’alignement de la fenêtre contextuelle est l’angle inférieur droit du <xref:System.Windows.Controls.Primitives.Popup>.  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Modification de l’origine de la cible et du point d’alignement de la fenêtre contextuelle  
 Lorsque <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>, <xref:System.Windows.Controls.Primitives.PlacementMode.Left>, <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>ou <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, l’origine de la cible et le point d’alignement de la fenêtre contextuelle changent si un bord d’écran spécifique est rencontré.  Le bord d’écran à l’origine du changement de position dépend de la valeur <xref:System.Windows.Controls.Primitives.PlacementMode>.  
  
 L’illustration suivante montre que quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> et que le <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord inférieur de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord inférieur de l’écran](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Le positionnement a la valeur Bottom et la fenêtre contextuelle est en contact avec le bord inférieur de l’écran.")
  
 L’illustration suivante montre que quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Left> et que le <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord gauche de l’écran, l’origine de la cible est l’angle supérieur droit de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord gauche de l’écran](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Le positionnement a la valeur Left et la fenêtre contextuelle est en contact avec le bord gauche de l’écran.")  
  
 L’illustration suivante montre que quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Right> et que le <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord droit de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle supérieur droit du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord droit de l’écran](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Le positionnement a la valeur Right et la fenêtre contextuelle est en contact avec le bord droit de l’écran.")  

 L’illustration suivante montre que quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Top> et que le <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord supérieur de l’écran, l’origine de la cible est l’angle inférieur gauche de la zone cible et le point d’alignement de la fenêtre contextuelle est l’angle supérieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison du bord supérieur de l’écran](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Le positionnement a la valeur Top et la fenêtre contextuelle est en contact avec le bord supérieur de l’écran.")  
  
 L’illustration suivante montre que quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> est <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> et que le <xref:System.Windows.Controls.Primitives.Popup> rencontre le bord inférieur de l’écran, l’origine de la cible est l’angle supérieur gauche de la zone cible (les limites du pointeur de la souris) et le point d’alignement de la fenêtre contextuelle est l’angle inférieur gauche du <xref:System.Windows.Controls.Primitives.Popup>.  
  
 ![Nouveau point d’alignement en raison de la proximité de la souris avec le bord de l’écran](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Le positionnement a la valeur Mouse et la fenêtre contextuelle est en contact avec le bord inférieur de l’écran.")
  
### <a name="customizing-popup-placement"></a>Personnalisation du positionnement d’un contrôle Popup  
 Vous pouvez personnaliser l’origine de la cible et le point d’alignement de la fenêtre contextuelle en affectant à la propriété <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> la valeur <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>. Définissez ensuite un délégué <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> qui retourne un ensemble de points de positionnement possibles et les axes principaux (par ordre de préférence) pour le <xref:System.Windows.Controls.Primitives.Popup>. Le point qui montre la plus grande partie du <xref:System.Windows.Controls.Primitives.Popup> est sélectionné.  La position du <xref:System.Windows.Controls.Primitives.Popup> est automatiquement ajustée si le <xref:System.Windows.Controls.Primitives.Popup> est masqué par le bord de l’écran. Pour obtenir un exemple, consultez [Spécifier une position de menu contextuel personnalisée](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Voir aussi

- [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS) (Exemple de positionnement de fenêtre contextuelle)
