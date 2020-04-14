---
title: Comportement de positionnement de Popup
ms.date: 03/30/2017
helpviewer_keywords:
- popups [WPF]
- Popup control [WPF], placing
- placing popups [WPF]
- positioning popups [WPF]
ms.assetid: fbf642e9-f670-4efd-a7af-a67468a1c8e1
ms.openlocfilehash: 1c377e62ffd334638031baee4d4831ac5a31acf3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81243256"
---
# <a name="popup-placement-behavior"></a>Comportement de positionnement de Popup
Un <xref:System.Windows.Controls.Primitives.Popup> contrôle affiche le contenu dans une fenêtre séparée qui flotte au-dessus d’une application. Vous pouvez <xref:System.Windows.Controls.Primitives.Popup> spécifier la position d’un parent à <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>un <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>contrôle, la souris, ou l’écran en utilisant le , , , <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>et les <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> propriétés.  Ces propriétés travaillent ensemble pour vous donner <xref:System.Windows.Controls.Primitives.Popup>la flexibilité dans la spécifier la position de la .  
  
> [!NOTE]
> Les <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ContextMenu> classes et les classes définissent également ces cinq propriétés et se comportent de la même façon.  

<a name="Positioning"></a>
## <a name="positioning-the-popup"></a>Positionnement de la fenêtre contextuelle  
 Le placement <xref:System.Windows.Controls.Primitives.Popup> d’un peut <xref:System.Windows.UIElement> être relatif à un ou à l’écran entier.  L’exemple suivant <xref:System.Windows.Controls.Primitives.Popup> crée quatre contrôles <xref:System.Windows.UIElement>qui sont relatifs à un — dans ce cas, une image. Tous les <xref:System.Windows.Controls.Primitives.Popup> contrôles <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> ont la `image1`propriété <xref:System.Windows.Controls.Primitives.Popup> réglée à , mais chacun a une valeur différente pour la propriété de placement.  
  
 [!code-xaml[PopupPositionSnippet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#3)]  
  
 L’illustration suivante montre <xref:System.Windows.Controls.Primitives.Popup> l’image et les contrôles  
  
 ![Image avec quatre contrôles Popup](./media/popup-placement-behavior/popup-placement-intro.png "Image avec quatre popups")
  
 Cet exemple simple montre comment <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> définir le et <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>les <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>propriétés, mais en utilisant le , , et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> les propriétés, vous avez encore plus de contrôle sur l’endroit où le <xref:System.Windows.Controls.Primitives.Popup> est positionné.  
  
<a name="Definitions"></a>
## <a name="definitions-of-terms-the-anatomy-of-a-popup"></a>Définitions des termes : anatomie d’une fenêtre contextuelle  
 Les termes suivants sont utiles <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>pour <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A>comprendre <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> comment le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.Popup>, , et les propriétés se rapportent les uns aux autres et le :  
  
- Objet cible  
  
- Zone cible  
  
- Origine de la cible  
  
- Point d’alignement de la fenêtre contextuelle  
  
 Ces termes fournissent un moyen pratique de <xref:System.Windows.Controls.Primitives.Popup> se référer à divers aspects de la et le contrôle qu’il est associé à.  
  
### <a name="target-object"></a>Objet cible  
 *L’objet cible* est <xref:System.Windows.Controls.Primitives.Popup> l’élément qui est associé. Si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> la propriété est définie, elle spécifie l’objet cible.  Si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> elle n’est <xref:System.Windows.Controls.Primitives.Popup> pas définie et qu’elle a un parent, le parent est l’objet cible.  S’il <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> n’y a pas de valeur et <xref:System.Windows.Controls.Primitives.Popup> pas de parent, il n’y a pas d’objet cible, et le est positionné par rapport à l’écran.  
  
 L’exemple suivant <xref:System.Windows.Controls.Primitives.Popup> crée un qui <xref:System.Windows.Controls.Canvas>est l’enfant d’un .  L’exemple ne <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> place pas <xref:System.Windows.Controls.Primitives.Popup>la propriété sur le . La valeur <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> par <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom?displayProperty=nameWithType>défaut <xref:System.Windows.Controls.Primitives.Popup> pour est <xref:System.Windows.Controls.Canvas>, de sorte que l’apparaît en dessous de la .  
  
 [!code-xaml[PopupPositionSnippet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#1)]  
  
 L’illustration suivante <xref:System.Windows.Controls.Primitives.Popup> montre que le <xref:System.Windows.Controls.Canvas>est positionné par rapport à la .  
  
 ![Contrôle Popup sans PlacementTarget](./media/popup-placement-behavior/popup-placement-no-placement-target.png "Popup sans PlacementTarget.")  

 L’exemple suivant <xref:System.Windows.Controls.Primitives.Popup> crée un qui <xref:System.Windows.Controls.Canvas>est l’enfant d’un , mais cette fois le <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est réglé à `ellipse1`, de sorte que le popup apparaît en dessous de la <xref:System.Windows.Shapes.Ellipse>.  
  
 [!code-xaml[PopupPositionSnippet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#2)]  
  
 L’illustration suivante <xref:System.Windows.Controls.Primitives.Popup> montre que le <xref:System.Windows.Shapes.Ellipse>est positionné par rapport à la .  
  
 ![Fenêtre contextuelle positionnée par rapport à une ellipse](./media/popup-placement-behavior/popup-placement-with-placement-target.png "Fenêtre contextuelle avec PlacementTarget")
  
> [!NOTE]
> Pour <xref:System.Windows.Controls.ToolTip>, la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> valeur <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>par défaut de est .  Pour <xref:System.Windows.Controls.ContextMenu>, la <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> valeur <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>par défaut de est . Ces valeurs sont expliquées plus loin, dans la section « Comment les propriétés fonctionnent ensemble ».  
  
### <a name="target-area"></a>Zone cible  
 La *zone cible* est la zone <xref:System.Windows.Controls.Primitives.Popup> sur l’écran que le est par rapport à. Dans les exemples <xref:System.Windows.Controls.Primitives.Popup> précédents, le est aligné avec les limites de <xref:System.Windows.Controls.Primitives.Popup> l’objet cible, mais dans <xref:System.Windows.Controls.Primitives.Popup> certains cas, le est aligné sur d’autres limites, même si le a un objet cible.  Si <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> la propriété est définie, la zone cible est différente des limites de l’objet cible.  
  
 L’exemple suivant <xref:System.Windows.Controls.Canvas> crée deux objets, chacun contenant un <xref:System.Windows.Shapes.Rectangle> et un <xref:System.Windows.Controls.Primitives.Popup>.  Dans les deux cas, <xref:System.Windows.Controls.Primitives.Popup> l’objet cible pour le est le <xref:System.Windows.Controls.Canvas>. Le <xref:System.Windows.Controls.Primitives.Popup> dans <xref:System.Windows.Controls.Canvas> le <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> premier a <xref:System.Windows.Rect.X%2A>l’ensemble, avec son , <xref:System.Windows.Rect.Y%2A>, <xref:System.Windows.Rect.Width%2A>et <xref:System.Windows.Rect.Height%2A> les propriétés réglées à 50, 50, 50, et 100, respectivement. Le <xref:System.Windows.Controls.Primitives.Popup> dans <xref:System.Windows.Controls.Canvas> le second <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> n’a pas le set.  En conséquence, le <xref:System.Windows.Controls.Primitives.Popup> premier est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> placé en <xref:System.Windows.Controls.Primitives.Popup> dessous de <xref:System.Windows.Controls.Canvas>la et la seconde est positionnée en dessous de la . Chacun <xref:System.Windows.Controls.Canvas> contient <xref:System.Windows.Shapes.Rectangle> également un qui a <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> les mêmes <xref:System.Windows.Controls.Primitives.Popup>limites que le pour le premier .  Notez <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> que le ne crée pas un élément visible dans l’application; l’exemple <xref:System.Windows.Shapes.Rectangle> crée un <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>pour représenter le .  
  
 [!code-xaml[PopupPositionSnippet#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#4)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Popup avec et sans PlacementRectangle](./media/popup-placement-behavior/popup-placement-placement-rectangle.png "Popup avec et sans PlacementRectangle.")  

### <a name="target-origin-and-popup-alignment-point"></a>Origine de la cible et point d’alignement de la fenêtre contextuelle  
 *L’origine de la cible* et le *point d’alignement de la fenêtre contextuelle* sont des points de référence sur la zone cible et la fenêtre contextuelle respectivement, qui sont utilisés pour le positionnement. Vous pouvez <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> utiliser <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> le et les propriétés pour compenser le popup de la zone cible.  Le <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> et sont relatifs à l’origine cible et le point d’alignement popup. La valeur <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> de la propriété détermine où se trouve l’origine cible et le point d’alignement du popup.  
  
 L’exemple suivant <xref:System.Windows.Controls.Primitives.Popup> crée <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> un <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> et définit le et les propriétés à 20.  La <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> propriété est <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> définie à (la valeur par défaut), de sorte que l’origine cible est le coin <xref:System.Windows.Controls.Primitives.Popup>inférieur gauche de la zone cible et le point d’alignement popup est le coin supérieur gauche de la .  
  
 [!code-xaml[PopupPositionSnippet#5](~/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS/Window1.xaml#5)]  
  
 L’illustration suivante montre le résultat de l’exemple précédent.  
  
 ![Positionnement de fenêtre contextuelle avec point d’alignement original cible](./media/popup-placement-behavior/popup-placement-target-origin-alignment-point.png "Popup avec HorizontalOffset et VerticalOffset.")
  
<a name="How"></a>
## <a name="how-the-properties-work-together"></a>Comment les propriétés fonctionnent ensemble  
 Les valeurs <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A>de <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> , , et doivent être considérés ensemble pour comprendre la zone cible correcte, l’origine cible, et le point d’alignement popup.  Par exemple, si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> la <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>valeur de est , <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> il n’y a pas d’objet cible, le est ignoré, et la zone cible est les limites du pointeur de souris. D’autre part, <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> c’est, le ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> le parent détermine l’objet cible et détermine la zone cible.  
  
 Le tableau suivant décrit l’objet cible, la zone cible, l’origine de la cible et le point d’alignement du popup et indique si <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> et <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> sont utilisés pour chaque <xref:System.Windows.Controls.Primitives.PlacementMode> valeur de recensement.  
  
|PlacementMode|Objet cible|Zone cible|Origine de la cible|Point d’alignement de la fenêtre contextuelle|  
|-------------------|-------------------|-----------------|-------------------|---------------------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|L’écran, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ou s’il est réglé.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relatif à l’écran.|L’angle supérieur gauche de la zone cible.|Le coin supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|L’écran, <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> ou s’il est réglé.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> relatif à l’écran.|L’angle supérieur gauche de la zone cible.|Le coin supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> par rapport à l’objet cible.|L’angle inférieur gauche de la zone cible.|Le coin supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> par rapport à l’objet cible.|Le centre de la zone cible.|Le centre <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Custom>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> par rapport à l’objet cible.|Défini par <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>le .|Défini par <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback>le .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> par rapport à l’objet cible.|L’angle supérieur gauche de la zone cible.|Le coin supérieur droit <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|Les limites du pointeur de souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré.|L’angle inférieur gauche de la zone cible.|Le coin supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Non applicable. <xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A> est ignoré.|Les limites du pointeur de souris. <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> est ignoré.|L’angle supérieur gauche de la zone cible.|Le coin supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> par rapport à l’objet cible.|L’angle supérieur gauche de la zone cible.|Le coin supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> par rapport à l’objet cible.|L’angle supérieur gauche de la zone cible.|Le coin supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> par rapport à l’objet cible.|L’angle supérieur droit de la zone cible.|Le coin supérieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|<xref:System.Windows.Controls.Primitives.Popup.PlacementTarget%2A>ou parent.|L’objet cible, ou <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> s’il est défini.  L’est <xref:System.Windows.Controls.Primitives.Popup.PlacementRectangle%2A> par rapport à l’objet cible.|L’angle supérieur gauche de la zone cible.|Le coin inférieur gauche <xref:System.Windows.Controls.Primitives.Popup>de la .|  
  
 Les illustrations suivantes <xref:System.Windows.Controls.Primitives.Popup>montrent la zone cible, l’origine <xref:System.Windows.Controls.Primitives.PlacementMode> cible et le point d’alignement popup pour chaque valeur. Dans chaque chiffre, la zone cible <xref:System.Windows.Controls.Primitives.Popup> est jaune, et la zone est bleue.  
  
 ![Fenêtre contextuelle avec positionnement Absolute ou AbsolutePoint](./media/popup-placement-behavior/popup-placement-absolute.png "Le placement est Absolute ou AbsolutePoint.")
  
 ![Fenêtre contextuelle avec positionnement Bottom](./media/popup-placement-behavior/popup-placement-bottom.png "Le placement est en bas.")
  
 ![Fenêtre contextuelle avec positionnement Center](./media/popup-placement-behavior/popup-placement-center.png "Le placement est centre.")
  
 ![Fenêtre contextuelle avec positionnement Left](./media/popup-placement-behavior/popup-placement-left.png "Le placement est à gauche.")
  
 ![Fenêtre contextuelle avec positionnement Mouse](./media/popup-placement-behavior/popup-placement-mouse.png "Le placement est La souris.")  
  
 ![Fenêtre contextuelle avec positionnement MousePoint](./media/popup-placement-behavior/popup-placement-mousepoint.png "Le placement est MousePoint.")  
  
 ![Fenêtre contextuelle avec positionnement Relative ou RelativePoint](./media/popup-placement-behavior/popup-placement-relative.png "Le placement est Relatif ou RelativePoint.")
  
 ![Fenêtre contextuelle avec positionnement Right](./media/popup-placement-behavior/popup-placement-right.png "Le placement est juste.")
  
 ![Fenêtre contextuelle avec positionnement Top](./media/popup-placement-behavior/popup-placement-top.png "Le placement est Top.")
  
<a name="When"></a>
## <a name="when-the-popup-encounters-the-edge-of-the-screen"></a>Lorsque la fenêtre contextuelle est en contact avec le bord de l’écran  
 Pour des raisons <xref:System.Windows.Controls.Primitives.Popup> de sécurité, un ne peut pas être caché par le bord d’un écran. L’une des trois choses <xref:System.Windows.Controls.Primitives.Popup> suivantes se produit lorsque les rencontres d’un bord d’écran:  
  
- Le popup se réaligne le long du <xref:System.Windows.Controls.Primitives.Popup>bord de l’écran qui obscurcirait le .  
  
- La fenêtre contextuelle utilise un point d’alignement différent.  
  
- La fenêtre contextuelle utilise une origine de cible et un point d’alignement différents.  
  
 Ces options sont décrites plus loin dans cette section.  
  
 Le comportement <xref:System.Windows.Controls.Primitives.Popup> du moment où il rencontre un <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> bord d’écran dépend de la valeur de la propriété et quel bord d’écran les rencontres popup. Le tableau suivant résume le <xref:System.Windows.Controls.Primitives.Popup> comportement lorsque les <xref:System.Windows.Controls.Primitives.PlacementMode> rencontres d’un bord d’écran pour chaque valeur.  
  
|PlacementMode|Bord supérieur|Bord inférieur|Bord gauche|Bord droit|  
|-------------------|--------------|-----------------|---------------|----------------|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>|Alignement sur le bord supérieur.|Le point d’alignement popup change vers <xref:System.Windows.Controls.Primitives.Popup>le coin inférieur gauche de la .|Alignement sur le bord gauche.|Le point d’alignement popup change dans <xref:System.Windows.Controls.Primitives.Popup>le coin supérieur droit de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>|Alignement sur le bord supérieur.|L’origine de la cible se transforme dans le coin supérieur gauche de la zone <xref:System.Windows.Controls.Primitives.Popup>cible et le point d’alignement popup change vers le coin inférieur gauche du .|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Center>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Left>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|L’origine cible change dans le coin supérieur droit de la zone cible et le <xref:System.Windows.Controls.Primitives.Popup>point d’alignement popup change vers le coin supérieur gauche de la .|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>|Alignement sur le bord supérieur.|L’origine de la cible se transforme dans le coin supérieur gauche de la zone cible (les limites <xref:System.Windows.Controls.Primitives.Popup>du pointeur de la souris) et le point d’alignement popup change vers le coin inférieur gauche de la .|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>|Alignement sur le bord supérieur.|Le point d’alignement popup change vers <xref:System.Windows.Controls.Primitives.Popup>le coin inférieur gauche de la .|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Relative>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>|Alignement sur le bord supérieur.|Le point d’alignement popup change vers <xref:System.Windows.Controls.Primitives.Popup>le coin inférieur gauche de la .|Alignement sur le bord gauche.|Le point d’alignement de la fenêtre contextuelle devient l’angle supérieur droit de la fenêtre contextuelle.|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Right>|Alignement sur le bord supérieur.|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|L’origine cible se transforme dans le coin supérieur gauche de la zone cible et <xref:System.Windows.Controls.Primitives.Popup>le point d’alignement popup change vers le coin supérieur-droit de la .|  
|<xref:System.Windows.Controls.Primitives.PlacementMode.Top>|L’origine de la cible se transforme dans le coin inférieur gauche de la zone <xref:System.Windows.Controls.Primitives.Popup>cible et le point d’alignement popup change vers le coin supérieur gauche du . En effet, c’est <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> la <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>même chose que quand est .|Alignement sur le bord inférieur.|Alignement sur le bord gauche.|Alignement sur le bord droit.|  
  
### <a name="aligning-to-the-screen-edge"></a>Alignement sur le bord de l’écran  
 A <xref:System.Windows.Controls.Primitives.Popup> peut s’aligner sur le bord de <xref:System.Windows.Controls.Primitives.Popup> l’écran en se repositionnant de sorte que l’ensemble est visible sur l’écran.  Lorsque cela se produit, la distance entre l’origine cible <xref:System.Windows.Controls.Primitives.Popup.HorizontalOffset%2A> et <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A>le point d’alignement popup peut différer des valeurs de et . Quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Absolute>est <xref:System.Windows.Controls.Primitives.PlacementMode.Center>, <xref:System.Windows.Controls.Primitives.PlacementMode.Relative>, <xref:System.Windows.Controls.Primitives.Popup> ou , l’aligne lui-même à chaque bord d’écran.  Supposons, par <xref:System.Windows.Controls.Primitives.Popup> exemple, qu’un a <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> réglé et <xref:System.Windows.Controls.Primitives.PlacementMode.Relative> <xref:System.Windows.Controls.Primitives.Popup.VerticalOffset%2A> réglé à 100.  Si le bord inférieur de l’écran <xref:System.Windows.Controls.Primitives.Popup>cache <xref:System.Windows.Controls.Primitives.Popup> tout ou partie de la , le repositionnement le long du bord inférieur de l’écran et la distance verticale entre l’origine cible et le point d’alignement popup est inférieure à 100. L’illustration suivante démontre ce comportement.  
  
 ![Fenêtre contextuelle alignée sur le bord de l’écran](./media/popup-placement-behavior/popup-placement-relative-screen-edge.png "Popup s’aligne sur le bord de l’écran.")
  
### <a name="changing-the-popup-alignment-point"></a>Modification du point d’alignement de la fenêtre contextuelle  
 Si <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.AbsolutePoint>est <xref:System.Windows.Controls.Primitives.PlacementMode.RelativePoint>, <xref:System.Windows.Controls.Primitives.PlacementMode.MousePoint>, ou , le point d’alignement popup change lorsque le popup rencontre le bord de l’écran inférieur ou droit.  
  
 L’illustration suivante démontre que lorsque le bord de <xref:System.Windows.Controls.Primitives.Popup>l’écran inférieur cache tout ou partie <xref:System.Windows.Controls.Primitives.Popup>du , le point d’alignement popup est le coin inférieur gauche de la .  
  
 ![Nouveau point d’alignement en raison du bord inférieur de l’écran](./media/popup-placement-behavior/popup-placement-relative-point-screen-edge.png "Popup rencontre le bord inférieur de l’écran et modifie le point d’alignement popup.")  

 L’illustration suivante démontre <xref:System.Windows.Controls.Primitives.Popup> que lorsque le est caché par le bord de l’écran <xref:System.Windows.Controls.Primitives.Popup>droit, le point d’alignement popup est le coin supérieur droit de la .  
  
 ![Nouveau point d’alignement de la fenêtre contextuelle en raison du bord de l’écran](./media/popup-placement-behavior/popup-placement-relative-point-right-screen-edge.png "Popup rencontre le bord droit de l’écran et change le point d’alignement popup.")
  
 Si <xref:System.Windows.Controls.Primitives.Popup> les rencontres les bords de l’écran inférieur et droit, <xref:System.Windows.Controls.Primitives.Popup>le point d’alignement popup est le coin inférieur droit de la .  
  
### <a name="changing-the-target-origin-and-popup-alignment-point"></a>Modification de l’origine de la cible et du point d’alignement de la fenêtre contextuelle  
 Quand <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom>est <xref:System.Windows.Controls.Primitives.PlacementMode.Left> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse>, <xref:System.Windows.Controls.Primitives.PlacementMode.Right>, <xref:System.Windows.Controls.Primitives.PlacementMode.Top>, ou , l’origine cible et le changement de point d’alignement popup si un certain bord d’écran est rencontré.  Le bord de l’écran qui <xref:System.Windows.Controls.Primitives.PlacementMode> provoque le changement de position dépend de la valeur.  
  
 L’illustration suivante démontre <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Bottom> que <xref:System.Windows.Controls.Primitives.Popup> quand est et les rencontres le bord inférieur de l’écran, l’origine cible est le <xref:System.Windows.Controls.Primitives.Popup>coin supérieur gauche de la zone cible et le point d’alignement popup est le coin inférieur gauche de la .  
  
 ![Nouveau point d’alignement en raison du bord inférieur de l’écran](./media/popup-placement-behavior/popup-placement-bottom-screen-edge.png "Placement est en bas et le popup rencontre le bord inférieur de l’écran.")
  
 L’illustration suivante démontre <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Left> que <xref:System.Windows.Controls.Primitives.Popup> quand est et les rencontres le bord de l’écran gauche, l’origine cible est le <xref:System.Windows.Controls.Primitives.Popup>coin supérieur-droit de la zone cible et le point d’alignement popup est le coin supérieur gauche de la .  
  
 ![Nouveau point d’alignement en raison du bord gauche de l’écran](./media/popup-placement-behavior/popup-placement-left-screen-edge.png "Le placement est à gauche et le popup rencontre le bord gauche de l’écran.")  
  
 L’illustration suivante démontre <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Right> que <xref:System.Windows.Controls.Primitives.Popup> quand est et les rencontres le bord de l’écran droit, l’origine cible est le <xref:System.Windows.Controls.Primitives.Popup>coin supérieur gauche de la zone cible et le point d’alignement popup est le coin supérieur droit de la .  
  
 ![Nouveau point d’alignement en raison du bord droit de l’écran](./media/popup-placement-behavior/popup-placement-right-screen-edge.png "Le placement est juste et le popup rencontre le bord droit de l’écran.")  

 L’illustration suivante démontre <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Top> que <xref:System.Windows.Controls.Primitives.Popup> quand est et les rencontres le bord de l’écran supérieur, l’origine cible est le <xref:System.Windows.Controls.Primitives.Popup>coin inférieur gauche de la zone cible et le point d’alignement popup est le coin supérieur gauche de la .  
  
 ![Nouveau point d’alignement en raison du bord supérieur de l’écran](./media/popup-placement-behavior/popup-placement-top-screen-edge.png "Placement est Top et le popup rencontre le bord supérieur de l’écran.")  
  
 L’illustration suivante démontre <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> <xref:System.Windows.Controls.Primitives.PlacementMode.Mouse> que <xref:System.Windows.Controls.Primitives.Popup> quand est et les rencontres le bord inférieur de l’écran, l’origine cible est le coin supérieur gauche de la <xref:System.Windows.Controls.Primitives.Popup>zone cible (les limites du pointeur de la souris) et le point d’alignement popup est le coin inférieur gauche de la .  
  
 ![Nouveau point d’alignement en raison de la proximité de la souris avec le bord de l’écran](./media/popup-placement-behavior/popup-placement-mouse-screen-edge.png "Placement est Souris et le popup rencontre le bord inférieur de l’écran.")
  
### <a name="customizing-popup-placement"></a>Personnalisation du positionnement de la fenêtre contextuelle  
 Vous pouvez personnaliser l’origine cible et le <xref:System.Windows.Controls.Primitives.Popup.Placement%2A> point <xref:System.Windows.Controls.Primitives.PlacementMode.Custom>d’alignement popup en définissant la propriété à . Ensuite, <xref:System.Windows.Controls.Primitives.CustomPopupPlacementCallback> définissez un délégué qui renvoie un ensemble de points de <xref:System.Windows.Controls.Primitives.Popup>placement possibles et axes primaires (par ordre de préférence) pour le . Le point qui montre la <xref:System.Windows.Controls.Primitives.Popup> plus grande partie de la est sélectionnée.  La position <xref:System.Windows.Controls.Primitives.Popup> de la est <xref:System.Windows.Controls.Primitives.Popup> automatiquement ajustée si le est caché par le bord de l’écran. Pour voir un exemple, consultez [Spécifier une position de menu contextuel personnalisée](how-to-specify-a-custom-popup-position.md).  
  
## <a name="see-also"></a>Voir aussi

- [Popup Placement Sample](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/VS_Snippets_Wpf/PopupPositionSnippet/CS) (Exemple de positionnement de fenêtre contextuelle)
