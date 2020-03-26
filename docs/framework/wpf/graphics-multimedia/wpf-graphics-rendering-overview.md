---
title: Aperçu de rendu de graphiques
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rendering
- rendering graphics [WPF]
ms.assetid: 6dec9657-4d8c-4e46-8c54-40fb80008265
ms.openlocfilehash: 9d58aa973f7de6c073611e13f2889913ff26dd55
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111918"
---
# <a name="wpf-graphics-rendering-overview"></a>Vue d'ensemble du rendu graphique de WPF
Cette rubrique offre une vue d’ensemble de la couche visuelle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Il met l’accent <xref:System.Windows.Media.Visual> sur le rôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de la classe pour rendre le soutien dans le modèle.  

<a name="role_of_visual_object"></a>
## <a name="role-of-the-visual-object"></a>Rôle de l’objet visuel  
 La <xref:System.Windows.Media.Visual> classe est l’abstraction <xref:System.Windows.FrameworkElement> de base dont chaque objet dérive. Elle sert également de point d’entrée pour l’écriture de nouveaux contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] et peut être considérée de diverses manières comme le handle de fenêtre (HWND) dans le modèle d’application Win32.  
  
 L’objet <xref:System.Windows.Media.Visual> est [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] un objet de base, dont le rôle principal est de fournir un support de rendu. Les contrôles d’interface <xref:System.Windows.Controls.TextBox>utilisateur, <xref:System.Windows.Media.Visual> tels que <xref:System.Windows.Controls.Button> et, dérivent de la classe, et l’utilisent pour persister leurs données de rendu. L’objet <xref:System.Windows.Media.Visual> fournit un support pour :  
  
- Affichage de sortie : rendu du contenu de dessin sérialisé persistant d’un objet visuel.  
  
- Transformations : exécution de transformations sur un objet visuel.  
  
- Détourage : prise en charge de la zone de détourage d’un objet visuel.  
  
- Test des résultats : détermination si une coordonnée ou une géométrie est contenue dans les limites d’un objet visuel.  
  
- Calculs de rectangle englobant : détermination du rectangle englobant d’un objet visuel.  
  
 Toutefois, <xref:System.Windows.Media.Visual> l’objet n’inclut pas de prise en charge des entités non-rendu, telles que :  
  
- Gestion des événements  
  
- Disposition  
  
- Styles  
  
- Liaison de données  
  
- Globalisation  
  
 <xref:System.Windows.Media.Visual>est exposée comme une classe abstraite publique à partir de laquelle les classes d’enfants doivent être dérivées. L’illustration suivante montre la hiérarchie des objets visuels exposés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 ![Diagramme des classes dérivées de l'objet Visual](./media/wpf-graphics-rendering-overview/classes-derived-visual-object.png)
  
### <a name="drawingvisual-class"></a>Classe DrawingVisual  
 Il <xref:System.Windows.Media.DrawingVisual> s’agit d’une classe de dessin léger qui est utilisée pour rendre des formes, des images ou du texte. Cette classe est considérée comme légère, car elle n’offre pas de dispositions ni d’options de gestion des événements, ce qui améliore ses performances d’exécution. C’est pourquoi, les dessins de ce type sont idéaux pour les arrière-plans et les images clipart. Le <xref:System.Windows.Media.DrawingVisual> peut être utilisé pour créer un objet visuel personnalisé. Pour plus d’informations, consultez [Utilisation d’objets DrawingVisual](using-drawingvisual-objects.md).  
  
### <a name="viewport3dvisual-class"></a>Classe Viewport3DVisual  
 Le <xref:System.Windows.Media.Media3D.Viewport3DVisual> fournit un pont <xref:System.Windows.Media.Visual> entre <xref:System.Windows.Media.Media3D.Visual3D> la 2D et les objets. La <xref:System.Windows.Media.Media3D.Visual3D> classe est la classe de base pour tous les éléments visuels 3D. L’exige <xref:System.Windows.Media.Media3D.Viewport3DVisual> que <xref:System.Windows.Media.Media3D.Viewport3DVisual.Camera%2A> vous définissiez une valeur et une <xref:System.Windows.Media.Media3D.Viewport3DVisual.Viewport%2A> valeur. La caméra vous permet d’afficher la scène. La fenêtre d’affichage détermine où la projection est mappée sur la surface 2D. Pour plus d’informations [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]sur la 3D en , voir [3D Graphics Overview](3-d-graphics-overview.md).  
  
### <a name="containervisual-class"></a>Classe ContainerVisual  
 La <xref:System.Windows.Media.ContainerVisual> classe est utilisée comme conteneur <xref:System.Windows.Media.Visual> pour une collection d’objets. La <xref:System.Windows.Media.DrawingVisual> classe dérive <xref:System.Windows.Media.ContainerVisual> de la classe, ce qui lui permet de contenir une collection d’objets visuels.  
  
### <a name="drawing-content-in-visual-objects"></a>Dessin de contenu dans des objets visuels  
 Un <xref:System.Windows.Media.Visual> objet stocke ses données de rendu comme une **liste d’instructions graphiques vectorielles**. Chaque élément de la liste d’instructions représente un ensemble de bas niveau de données graphiques et des ressources associées dans un format sérialisé. Quatre types de données de rendu différents peuvent du contenu de dessin.  
  
|Type de contenu de dessin|Description|  
|--------------------------|-----------------|  
|Graphismes vectoriels|Représente les données graphiques <xref:System.Windows.Media.Brush> vectorielles, ainsi que toute information et <xref:System.Windows.Media.Pen> information.|  
|Image|Représente une image au sein <xref:System.Windows.Rect>d’une région définie par un .|  
|Glyphe|Représente un dessin qui <xref:System.Windows.Media.GlyphRun>rend un , qui est une séquence de glyphes à partir d’une ressource de police spécifiée. Il s’agit de la représentation du texte.|  
|Vidéo|Représente un dessin qui rend de la vidéo.|  
  
 Le <xref:System.Windows.Media.DrawingContext> vous permet de <xref:System.Windows.Media.Visual> remplir un avec du contenu visuel. Lorsque vous <xref:System.Windows.Media.DrawingContext> utilisez les commandes de tirage d’un objet, vous stockez en fait un ensemble de données de rendu qui seront plus tard utilisées par le système graphique ; vous ne dessinez pas à l’écran en temps réel.  
  
 Lorsque vous [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] créez un contrôle, tel qu’un, <xref:System.Windows.Controls.Button>le contrôle génère implicitement des données de rendu pour se dessiner. Par exemple, <xref:System.Windows.Controls.ContentControl.Content%2A> l’établissement <xref:System.Windows.Controls.Button> de la propriété des causes du contrôle pour stocker une représentation de rendu d’un glyphe.  
  
 A <xref:System.Windows.Media.Visual> décrit son contenu comme <xref:System.Windows.Media.Drawing> un ou <xref:System.Windows.Media.DrawingGroup>plusieurs objets contenus dans un . A <xref:System.Windows.Media.DrawingGroup> décrit également les masques d’opacité, les transformations, les effets de bitmap et d’autres opérations qui sont appliquées à son contenu. <xref:System.Windows.Media.DrawingGroup>les opérations sont appliquées dans l’ordre <xref:System.Windows.Media.DrawingGroup.BitmapEffect%2A>suivant <xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A> <xref:System.Windows.Media.DrawingGroup.GuidelineSet%2A>lorsque le <xref:System.Windows.Media.DrawingGroup.Transform%2A>contenu est rendu: <xref:System.Windows.Media.DrawingGroup.OpacityMask%2A>, <xref:System.Windows.Media.DrawingGroup.Opacity%2A>, , , , et puis .  
  
 L’illustration suivante montre <xref:System.Windows.Media.DrawingGroup> l’ordre dans lequel les opérations sont appliquées pendant la séquence de rendu.  
  
 ![Ordre des opérations DrawingGroup](./media/graphcismm-drawinggroup-order.png "graphcismm_drawinggroup_order")  
Ordre des opérations DrawingGroup  
  
 Pour plus d’informations, consultez [Vue d’ensemble des objets de dessin](drawing-objects-overview.md).  
  
#### <a name="drawing-content-at-the-visual-layer"></a>Contenu de dessin sur la couche visuelle  
 Vous n’avez jamais <xref:System.Windows.Media.DrawingContext>directement instantané un ; vous pouvez, cependant, acquérir un contexte de <xref:System.Windows.Media.DrawingGroup.Open%2A?displayProperty=nameWithType> <xref:System.Windows.Media.DrawingVisual.RenderOpen%2A?displayProperty=nameWithType>dessin à partir de certaines méthodes, telles que et . L’exemple suivant <xref:System.Windows.Media.DrawingContext> récupère <xref:System.Windows.Media.DrawingVisual> un d’un et l’utilise pour dessiner un rectangle.  
  
 [!code-csharp[drawingvisualsample#101](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingVisualSample/CSharp/Window1.xaml.cs#101)]
 [!code-vb[drawingvisualsample#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DrawingVisualSample/visualbasic/window1.xaml.vb#101)]  
  
#### <a name="enumerating-drawing-content-at-the-visual-layer"></a>Énumération du contenu de dessin sur la couche visuelle  
 En plus de leurs <xref:System.Windows.Media.Drawing> autres utilisations, les objets fournissent également <xref:System.Windows.Media.Visual>un modèle d’objet pour énumérer le contenu d’un .  
  
> [!NOTE]
> Lorsque vous énumérez le contenu du visuel, vous <xref:System.Windows.Media.Drawing> récupérez des objets, et non la représentation sous-jacente des données de rendu comme une liste d’instructions graphiques vectorielles.  
  
 L’exemple suivant <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> utilise la <xref:System.Windows.Media.DrawingGroup> méthode <xref:System.Windows.Media.Visual> pour récupérer la valeur d’un et l’énumérer.  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
<a name="how_visual_objects_are_used_to_build_controls"></a>
## <a name="how-visual-objects-are-used-to-build-controls"></a>Comment les objets visuels sont utilisés pour générer des contrôles  
 Un grand nombre d’objets dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] sont composés d’autres objets visuels, ce qui signifie qu’ils peuvent contenir différentes hiérarchies d’objets descendants. Un grand nombre d’éléments de l’interface utilisateur dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], tels que les contrôles, sont composés de plusieurs objets visuels représentant différents types d’éléments de rendu. Par exemple, <xref:System.Windows.Controls.Button> le contrôle peut contenir un <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> <xref:System.Windows.Controls.ContentPresenter>certain <xref:System.Windows.Controls.TextBlock>nombre d’autres objets, y compris , , et .  
  
 Le code suivant <xref:System.Windows.Controls.Button> affiche un contrôle défini dans la balisage.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet1)]  
  
 Si vous énumériez les objets visuels qui <xref:System.Windows.Controls.Button> composent le contrôle par défaut, vous trouverez la hiérarchie des objets visuels illustrés ci-dessous :  
  
 ![Diagramme de la hiérarchie de l’arborescence d’éléments visuels](./media/wpf-graphics-rendering-overview/visual-object-diagram.gif)
  
 Le <xref:System.Windows.Controls.Button> contrôle <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> contient un élément, qui <xref:System.Windows.Controls.ContentPresenter> à son tour, contient un élément. L’élément <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> est responsable de l’établissement <xref:System.Windows.Controls.Button>d’une frontière et d’un arrière-plan pour le . L’élément <xref:System.Windows.Controls.ContentPresenter> est responsable de <xref:System.Windows.Controls.Button>l’affichage du contenu de la . Dans ce cas, puisque vous <xref:System.Windows.Controls.ContentPresenter> affichez <xref:System.Windows.Controls.TextBlock> du texte, l’élément contient un élément. Le fait <xref:System.Windows.Controls.Button> que le <xref:System.Windows.Controls.ContentPresenter> contrôle utilise un moyen que le contenu <xref:System.Windows.Controls.Image> pourrait être représenté par d’autres éléments, tels qu’une ou une géométrie, comme un <xref:System.Windows.Media.EllipseGeometry>.  
  
### <a name="control-templates"></a>Modèles de contrôle  
 La clé de l’expansion d’un contrôle <xref:System.Windows.Controls.ControlTemplate>dans une hiérarchie de contrôles est le . Un modèle de contrôle spécifie la hiérarchie d’objets visuels par défaut d’un contrôle. Lorsque vous référencez explicitement un contrôle, vous référencez implicitement sa hiérarchie d’objets visuels. Vous pouvez remplacer les valeurs par défaut d’un modèle de contrôle afin de créer une apparence visuelle personnalisée pour un contrôle. Par exemple, vous pouvez modifier la <xref:System.Windows.Controls.Button> valeur de couleur de fond du contrôle de sorte qu’il utilise une valeur linéaire de couleur de gradient au lieu d’une valeur de couleur solide. Pour plus d’informations, consultez [Styles et modèles de bouton](../controls/button-styles-and-templates.md).  
  
 Un élément d’interface <xref:System.Windows.Controls.Button> utilisateur, tel qu’un contrôle, contient plusieurs listes d’instructions graphiques vectorielles qui décrivent l’ensemble de la définition de rendu d’un contrôle. Le code suivant <xref:System.Windows.Controls.Button> affiche un contrôle défini dans la balisage.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet2](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet2)]  
  
 Si vous énumériez les objets visuels et les listes <xref:System.Windows.Controls.Button> d’instructions graphiques vectorielles qui composent le contrôle, vous trouverez la hiérarchie des objets illustrés ci-dessous :  
  
 ![Diagramme de l’arborescence d’éléments visuels et des données de rendu](./media/wpf-graphics-rendering-overview/visual-tree-rendering-data.png)  
  
 Le <xref:System.Windows.Controls.Button> contrôle <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> contient un élément, qui <xref:System.Windows.Controls.ContentPresenter> à son tour, contient un élément. L’élément <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> est responsable de dessiner tous les éléments graphiques discrets qui composent la bordure et l’arrière-plan d’un bouton. L’élément <xref:System.Windows.Controls.ContentPresenter> est responsable de <xref:System.Windows.Controls.Button>l’affichage du contenu de la . Dans ce cas, puisque vous affichez une image, l’élément <xref:System.Windows.Controls.ContentPresenter> contient un <xref:System.Windows.Controls.Image> élément.  
  
 Prenez note des différents points suivants sur la hiérarchie d’objets visuels et les listes d’instructions de graphismes vectoriels :  
  
- L’ordre de la hiérarchie représente l’ordre de rendu des informations de dessin. À partir de l’élément visuel racine, les éléments enfants sont parcourus de gauche à droite et de haut en bas. Si un élément comporte des éléments enfants, ils sont parcourus avant les frères de l’élément.  
  
- Les éléments de nœuds non-feuilles dans la hiérarchie, tels que, <xref:System.Windows.Controls.ContentPresenter>sont utilisés pour contenir des éléments pour enfants, ils ne contiennent pas de listes d’instructions.  
  
- Si un élément visuel contient une liste d’instructions de graphismes vectoriels et des enfants visuels, la liste d’instructions de l’élément visuel parent est rendue avant les dessins des objets enfants visuels.  
  
- Les éléments dans la liste d’instructions de graphismes vectoriels sont rendus de gauche à droite.  
  
<a name="visual_tree"></a>
## <a name="visual-tree"></a>Arborescence d'éléments visuels  
 L’arborescence d’éléments visuels contient tous les éléments visuels utilisés dans l’interface utilisateur d’une application. Étant donné qu’un élément visuel contient des informations de dessin persistantes, vous pouvez considérer l’arborescence d’éléments visuels comme un graphique de scène contenant toutes les informations de rendu nécessaires pour composer la sortie vers le périphérique d’affichage. Cette arborescence est l’accumulation de tous les éléments visuels créés directement par l’application, que ce soit dans le code ou dans la balise. L’arborescence d’éléments visuels contient également tous les éléments visuels créés par l’expansion du modèle d’éléments comme les contrôles et les objets de données.  
  
 Le code suivant <xref:System.Windows.Controls.StackPanel> montre un élément défini dans la balisage.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet3](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet3)]  
  
 Si vous énumériez les objets visuels <xref:System.Windows.Controls.StackPanel> qui composent l’élément dans l’exemple de balisage, vous trouverez la hiérarchie des objets visuels illustrés ci-dessous :  
  
 ![Diagramme de la hiérarchie de l’arborescence d’éléments visuels](./media/wpf-graphics-rendering-overview/visual-tree-hierarchy.gif)  
  
### <a name="rendering-order"></a>Ordre de rendu  
 L’arborescence d’éléments visuels détermine l’ordre de rendu des objets visuels et de dessin [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. L’ordre de parcours démarre avec l’objet visuel racine qui est le nœud supérieur de l’arborescence d’éléments visuels. Les enfants de l’objet visuel racine sont ensuite parcourus de gauche à droite. Si un objet visuel comporte des enfants, ses enfants sont parcourus avant les frères de l’objet visuel. Cela signifie que le contenu d’un objet visuel enfant est rendu avant le contenu de l’objet visuel.  
  
 ![Diagramme de l’ordre visuel de rendu d’arbre](./media/wpf-graphics-rendering-overview/visual-tree-rendering-order.gif)
  
### <a name="root-visual"></a>Objet visuel racine  
 L’**objet visuel racine** est le premier élément d’une hiérarchie d’arborescence d’éléments visuels. Dans la plupart des applications, la <xref:System.Windows.Window> classe <xref:System.Windows.Navigation.NavigationWindow>de base du visuel racine est soit ou . Toutefois, si vous hébergiez des objets visuels dans une application Win32, l’objet visuel racine serait le premier objet visuel hébergé dans la fenêtre Win32. Pour plus d’informations, consultez [Didacticiel : hébergement d’objets visuels dans une application Win32](tutorial-hosting-visual-objects-in-a-win32-application.md).  
  
### <a name="relationship-to-the-logical-tree"></a>Relation à l’arborescence logique  
 L’arborescence logique dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] représente les éléments d’une application au moment de l’exécution. Même si vous ne manipulez pas directement cette arborescence, cette vue de l’application est utile pour comprendre l’héritage de propriété et le routage d’événement. Contrairement à l’arbre visuel, l’arbre logique peut <xref:System.Windows.Documents.ListItem>représenter des objets de données non visuels, tels que . Dans de nombreux cas, l’arborescence logique est très étroitement liée aux définitions de balise d’une application. Le code suivant <xref:System.Windows.Controls.DockPanel> montre un élément défini dans la balisage.  
  
 [!code-xaml[VisualsOverview#VisualsOverviewSnippet5](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml#visualsoverviewsnippet5)]  
  
 Si vous énumériez les objets logiques <xref:System.Windows.Controls.DockPanel> qui composent l’élément dans l’exemple de balisage, vous trouverez la hiérarchie des objets logiques illustrés ci-dessous :  
  
 ![Diagramme de l’arborescence](./media/tree1-wcp.gif "Tree1_wcp")  
Diagramme de l’arborescence logique  
  
 L’arborescence d’éléments visuels et l’arborescence logique sont synchronisées avec l’ensemble actuel d’éléments d’application, reflétant tout ajout, suppression ou modification d’éléments. Toutefois, les arborescences présentent différentes vues de l’application. Contrairement à l’arbre visuel, l’arbre <xref:System.Windows.Controls.ContentPresenter> logique n’étend pas l’élément d’un contrôle. Cela signifie qu’il n’existe pas de correspondance directe entre une arborescence logique et une arborescence d’éléments visuels pour le même ensemble d’objets. En fait, invoquer la méthode de <xref:System.Windows.LogicalTreeHelper.GetChildren%2A> l’objet **LogicalTreeHelper** <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> et la méthode de l’objet **VisualTreeHelper** en utilisant le même élément qu’un paramètre donne des résultats différents.  
  
 Pour plus d’informations sur l’arborescence logique, consultez [Arborescences dans WPF](../advanced/trees-in-wpf.md).  
  
### <a name="viewing-the-visual-tree-with-xamlpad"></a>Affichage de l’arborescence d’éléments visuels avec XamlPad  
 L’outil, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XamlPad, offre une option pour visualiser et explorer l’arbre visuel qui correspond au contenu XAML actuellement défini. Cliquez sur le bouton **Show Visual Tree** (Afficher l’arborescence d’éléments visuels) de la barre de menus pour afficher l’arborescence d’éléments visuels. Ce qui suit illustre l’expansion du contenu XAML dans les nœuds d’arbres visuels dans le panneau **Visual Tree Explorer** de XamlPad:  
  
 ![Volet Explorateur de l’arborescence d’éléments visuels dans XamlPad](./media/wpf-graphics-rendering-overview/visual-tree-explorer.png)  

 Remarquez <xref:System.Windows.Controls.Label>comment <xref:System.Windows.Controls.TextBox>le <xref:System.Windows.Controls.Button> , , et contrôle chaque affichage d’une hiérarchie d’objets visuels distincts dans le panneau **Visual Tree Explorer** de XamlPad. C’est [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] parce <xref:System.Windows.Controls.ControlTemplate> que les contrôles ont un qui contient l’arbre visuel de ce contrôle. Lorsque vous référencez explicitement un contrôle, vous référencez implicitement sa hiérarchie d’objets visuels.  
  
### <a name="profiling-visual-performance"></a>Profilage des performances visuelles  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] fournit une suite d’outils de profilage des performances qui vous permettent d’analyser le comportement au moment de l’exécution de votre application et de déterminer les types d’optimisations des performances que vous pouvez appliquer. L’outil Profileur Visual fournit une vue graphique détaillée des données de performances en mappant directement à l’arborescence d’éléments visuels de l’application. Dans cette capture d’écran, la section **Utilisation du processeur** du Profileur Visual décrit précisément l’utilisation de services [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] de l’objet, tels que le rendu et la disposition.  
  
 ![Sortie du Générateur de profils Visual](./media/wpfperf-visualprofiler-04.png "WPFPerf_VisualProfiler_04")  
Sortie du Générateur de profils Visual  
  
<a name="visual_rendering_behavior"></a>
## <a name="visual-rendering-behavior"></a>Comportement de rendu d’objet visuel  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] introduit plusieurs fonctionnalités qui affectent le comportement de rendu d’objets visuels : graphiques en mode retenu, graphismes vectoriels et graphiques indépendants du périphérique.  
  
### <a name="retained-mode-graphics"></a>Graphiques en mode retenu  
 Une des clés pour comprendre le rôle de l’objet visuel est de comprendre la différence entre les systèmes graphiques en **mode exécution** et en **mode retenu**. Une application Win32 standard basée sur GDI ou GDI+ utilise un système graphique en mode exécution. Cela signifie que l’application est responsable de la mise à jour la partie de la zone client qui est invalidée en raison d’une action telle que le redimensionnement d’une fenêtre ou de la modification de l’apparence visuelle d’un objet.  
  
 ![Diagramme de la séquence de rendu Win32](./media/wpf-graphics-rendering-overview/win32-rendering-squence.png)  
  
 Au contraire, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise un système en mode retenu. Cela signifie que les objets d’application ayant une apparence visuelle définissent un ensemble de données de dessin sérialisées. Une fois que les données de dessin sont définies, le système est ensuite responsable de répondre à toutes les demandes de mise à jour pour le rendu des objets d’application. Même au moment de l’exécution, vous pouvez modifier ou créer des objets d’application en vous appuyant toujours sur le système pour répondre aux demandes de dessin. La puissance d’un système graphique en mode retenu est telle que les informations de dessin restent dans un état sérialisé par l’application, mais la responsabilité du rendu est laissée au système. Le diagramme suivant illustre comment l’application s’appuie sur [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] pour répondre aux demandes de dessin.  
  
 ![Diagramme de la séquence de rendu WPF](./media/wpf-graphics-rendering-overview/wpf-rendering-sequence.png)  

#### <a name="intelligent-redrawing"></a>Nouveau dessin intelligent  
 L’un des principaux avantages de l’utilisation de graphiques en mode retenu est que [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] peut optimiser efficacement ce qui doit être redessiné dans l’application. Même si vous avez une scène complexe avec différents niveaux d’opacité, vous ne devez généralement pas écrire du code spécial pour optimiser le nouveau dessin. Comparez cela avec la programmation Win32 dans laquelle vous pouvez consacrer beaucoup de temps à optimiser votre application en réduisant la quantité de nouveau dessin dans la région de mise à jour. Consultez [Nouveau dessin dans la région de mise à jour](/windows/desktop/gdi/redrawing-in-the-update-region) pour obtenir un exemple du type de complexité impliquée dans l’optimisation du nouveau dessin dans les applications Win32.  
  
### <a name="vector-graphics"></a>Graphismes vectoriels  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] utilise des **graphismes vectoriels** comme format des données de rendu. Les graphiques vectoriels, qui incluent les SVG (Scalable Vector Graphics), les métafichiers Windows (.wmf) et les polices TrueType, stockent les données de rendu et les transmettent sous forme de liste d’instructions qui décrivent comment recréer une image à l’aide de primitives graphiques. Par exemple, les polices TrueType sont des polices vectorielles qui décrivent un ensemble de lignes, de courbes et de commandes, plutôt qu’un tableau de pixels. L’un des principaux avantages des graphismes vectoriels est la possibilité de mettre à l’échelle à toute taille et résolution.  
  
 Contrairement aux graphismes vectoriels, les graphiques bitmap stockent les données de rendu sous forme de représentation pixel par pixel d’une image, prérendue pour une résolution spécifique. L’une des principales différences entre les formats de graphiques bitmap et de graphismes vectoriels est la fidélité à l’image source d’origine. Par exemple, lorsque la taille d’une image source est modifiée, les systèmes de graphiques bitmap étirent l’image, tandis que les systèmes de graphismes vectoriels mettent l’image à l’échelle, restant ainsi fidèle à l’image.  
  
 L’illustration suivante montre une image source qui a été redimensionnée à 300 %. Remarquez les distorsions qui apparaissent lorsque l’image source est étirée dans une image graphique bitmap plutôt que mise à l’échelle dans une image de graphisme vectoriel.  
  
 ![Différences entre graphiques raster et vectoriels](./media/wpf-graphics-rendering-overview/raster-vector-differences.png)  
  
 La balisage <xref:System.Windows.Shapes.Path> suivante montre deux éléments définis. Le deuxième élément <xref:System.Windows.Media.ScaleTransform> utilise un pour resize les instructions de dessin du premier élément par 300%. Notez que les <xref:System.Windows.Shapes.Path> instructions de dessin dans les éléments restent inchangées.  
  
 [!code-xaml[VectorGraphicsSnippets#VectorGraphicsSnippet1](~/samples/snippets/csharp/VS_Snippets_Wpf/VectorGraphicsSnippets/CS/PageOne.xaml#vectorgraphicssnippet1)]  
  
### <a name="about-resolution-and-device-independent-graphics"></a>À propos des graphiques indépendants de la résolution et du périphérique  
 Deux facteurs système déterminent la taille du texte et des graphiques sur votre écran : la résolution et les points par pouce (PPP). La résolution décrit le nombre de pixels qui apparaissent sur l’écran. Plus la résolution est élevée, plus les pixels sont petits, générant ainsi des graphiques et du texte plus petits. Un graphique affiché sur un écran défini sur 1024 x 768 apparaîtra beaucoup plus petit lorsque la résolution est définie sur 1600 x 1200.  
  
 L’autre paramètre système, PPP, décrit la taille d’un pouce d’écran en pixels. La plupart des systèmes Windows ont un DPI de 96, ce qui signifie qu’un pouce d’écran est de 96 pixels. L’augmentation du paramètre PPP rend le pouce d’écran plus grand ; la réduction du paramètre PPP rend le pouce d’écran plus petit. Cela signifie qu’un pouce d’écran n’a pas la même taille qu’un pouce réel ; dans la plupart des systèmes, ceci n’est probablement pas le cas. Lorsque vous augmentez le paramètre PPP, les graphiques et le texte reconnaissant la résolution sont plus volumineux car vous avez augmenté la taille du pouce d’écran. L’augmentation du paramètre PPP peut rendre du texte plus facile à lire, notamment à des hautes résolutions.  
  
 Toutes les applications ne reconnaissent pas la résolution : certaines utilisent les pixels matériels comme unité de mesure principale ; la modification du paramètre PPP système n’a aucun effet sur ces applications. Beaucoup d’autres applications utilisent des unités reconnaissant la résolution pour décrire les tailles de police, mais utilisent des pixels pour décrire tout le reste. La définition du paramètre PPP sur une valeur trop basse ou trop élevée peut entraîner des problèmes de disposition pour ces applications, car le texte des applications évolue avec le paramètre PPP du système, mais pas l’interface utilisateur des applications. Ce problème a été résolu pour les applications développées à l’aide de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prend en charge la mise à l’échelle automatique en utilisant le pixel indépendant du périphérique comme unité de mesure principale au lieu des pixels matériels ; les graphiques et le texte sont correctement mis à l’échelle sans intervention supplémentaire du développeur de l’application. L’illustration suivante montre un exemple d’affichage du texte et des graphiques [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] avec différents paramètres PPP.  
  
 ![Graphique et texte avec différents paramètres PPP](./media/graphicsmm-dpi-setting-examples.png "graphicsmm_dpi_setting_examples")  
Graphique et texte avec différents paramètres PPP  
  
<a name="visualtreehelper_class"></a>
## <a name="visualtreehelper-class"></a>Classe VisualTreeHelper  
 La <xref:System.Windows.Media.VisualTreeHelper> classe est une classe d’aide statique qui fournit des fonctionnalités de bas niveau pour la programmation au niveau de l’objet visuel, ce qui est utile dans des scénarios très spécifiques, tels que le développement de contrôles personnalisés haute performance. Dans la plupart des [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] cas, les <xref:System.Windows.Controls.Canvas> objets-cadres de haut niveau, tels que et, <xref:System.Windows.Controls.TextBlock>offrent une plus grande flexibilité et facilité d’utilisation.  
  
### <a name="hit-testing"></a>Test des résultats  
 La <xref:System.Windows.Media.VisualTreeHelper> classe fournit des méthodes pour les tests à succès sur les objets visuels lorsque le support de test par défaut ne répond pas à vos besoins. Vous pouvez <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> utiliser les <xref:System.Windows.Media.VisualTreeHelper> méthodes de la classe pour déterminer si une géométrie ou une valeur de coordonnées ponctuelles se trouve à l’intérieur de la limite d’un objet donné, comme un élément de contrôle ou graphique. Par exemple, vous pouvez utiliser le test des résultats pour déterminer si un clic de souris dans le rectangle englobant d’un objet se trouve dans la géométrie d’un cercle. Vous pouvez également choisir de substituer l’implémentation par défaut du test des résultats pour effectuer vos propres calculs de test des résultats personnalisés.  
  
 Pour plus d’informations sur le test des résultats, consultez [Test des résultats dans la couche visuelle](hit-testing-in-the-visual-layer.md).  
  
### <a name="enumerating-the-visual-tree"></a>Énumération de l’arborescence d’éléments visuels  
 La <xref:System.Windows.Media.VisualTreeHelper> classe offre des fonctionnalités pour énumérer les membres d’un arbre visuel. Pour récupérer un parent, appelez la <xref:System.Windows.Media.VisualTreeHelper.GetParent%2A> méthode. Pour récupérer un enfant, ou descendant direct, <xref:System.Windows.Media.VisualTreeHelper.GetChild%2A> d’un objet visuel, appelez la méthode. Cette méthode renvoie un enfant <xref:System.Windows.Media.Visual> du parent à l’index spécifié.  
  
 L’exemple suivant montre comment énumérer tous les descendants d’un objet visuel, qui est une technique utile si vous voulez sérialiser toutes les informations de rendu d’une hiérarchie d’objets visuels.  
  
 [!code-csharp[VisualsOverview#101](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#101)]
 [!code-vb[VisualsOverview#101](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#101)]  
  
 Dans la plupart des cas, l’arborescence logique est une représentation plus utile des éléments dans une application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Même si vous ne modifiez pas directement l’arborescence logique, cette vue de l’application est utile pour comprendre l’héritage de propriété et le routage d’événement. Contrairement à l’arbre visuel, l’arbre logique peut <xref:System.Windows.Documents.ListItem>représenter des objets de données non visuels, tels que . Pour plus d’informations sur l’arborescence logique, consultez [Arborescences dans WPF](../advanced/trees-in-wpf.md).  
  
 La <xref:System.Windows.Media.VisualTreeHelper> classe fournit des méthodes pour retourner le rectangle de délimitation des objets visuels. Vous pouvez retourner le rectangle de délimitation d’un objet visuel en appelant <xref:System.Windows.Media.VisualTreeHelper.GetContentBounds%2A>. Vous pouvez retourner le rectangle de délimitation de tous les descendants <xref:System.Windows.Media.VisualTreeHelper.GetDescendantBounds%2A>d’un objet visuel, y compris l’objet visuel lui-même, en appelant . Le code suivant montre comment vous pourriez calculer le rectangle englobant d’un objet visuel et de tous ses descendants.  
  
 [!code-csharp[VisualsOverview#102](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#102)]
 [!code-vb[VisualsOverview#102](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#102)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.Visual>
- <xref:System.Windows.Media.VisualTreeHelper>
- <xref:System.Windows.Media.DrawingVisual>
- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Test de positionnement dans la couche visuelle](hit-testing-in-the-visual-layer.md)
- [Utilisation d’objets DrawingVisual](using-drawingvisual-objects.md)
- [Didacticiel : hébergement d’objets visuels dans une application Win32](tutorial-hosting-visual-objects-in-a-win32-application.md)
- [Optimisation des performances des applications WPF](../advanced/optimizing-wpf-application-performance.md)
