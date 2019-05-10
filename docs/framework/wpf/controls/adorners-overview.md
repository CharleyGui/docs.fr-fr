---
title: Vue d'ensemble des ornements
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b5788b3ddb14b1acae9c6661420ab439205d000b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591251"
---
# <a name="adorners-overview"></a>Vue d'ensemble des ornements
Les ornements sont un type spécial de <xref:System.Windows.FrameworkElement>, utilisé pour fournir des signaux visuels à un utilisateur. Les ornements permettent notamment d’ajouter des descripteurs fonctionnels à des éléments ou de fournir des informations d’état sur un contrôle.  

<a name="about_Adorners"></a>   
## <a name="about-adorners"></a>À propos des ornements  
 Un <xref:System.Windows.Documents.Adorner> personnalisé <xref:System.Windows.FrameworkElement> qui est lié à un <xref:System.Windows.UIElement>. Les ornements sont restitués dans un <xref:System.Windows.Documents.AdornerLayer>, qui est une surface de rendu qui est toujours au-dessus de l’élément orné ou une collection d’éléments ornés. Rendu d’un ornement est indépendant du rendu de la <xref:System.Windows.UIElement> qui l’ornement est lié. Un ornement est généralement positionné par rapport à l’élément auquel il est lié, au moyen de l’origine des coordonnées 2D standard située dans le coin supérieur gauche de l’élément orné.  
  
 Parmi les applications courantes des ornements, citons les suivantes :  
  
- Ajout de descripteurs fonctionnels à un <xref:System.Windows.UIElement> qui permettent à un utilisateur de manipuler l’élément d’une certaine façon (redimensionnement, rotation, repositionnement, etc.).  
  
- Retour visuel pour indiquer différents états, ou en réponse à différents événements  
  
- Superposition de décorations visuelles sur un <xref:System.Windows.UIElement>.  
  
- Masquage visuel ou remplacement de tout ou partie d’un <xref:System.Windows.UIElement>.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] fournit une infrastructure de base pour orner des éléments visuels. Le tableau suivant répertorie les principaux types utilisés pour orner des objets et leur but. Plusieurs exemples d’utilisation suivent.  
  
|||  
|-|-|  
|<xref:System.Windows.Documents.Adorner>|Classe de base abstraite à partir de laquelle toutes les implémentations d’ornement concrètes sont héritées.|  
|<xref:System.Windows.Documents.AdornerLayer>|Classe représentant une couche de rendu pour le ou les ornements d’un ou plusieurs éléments ornés.|  
|<xref:System.Windows.Documents.AdornerDecorator>|Classe permettant d’associer une couche d’ornement à une collection d’éléments.|  
  
<a name="implement_custom_Adorner"></a>   
## <a name="implementing-a-custom-adorner"></a>Implémentation d’un ornement personnalisé  
 L’infrastructure des ornements fournie par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est principalement destinée à prendre en charge la création d’ornements personnalisés. Un ornement personnalisé est créé en implémentant une classe qui hérite de la classe abstraite <xref:System.Windows.Documents.Adorner> classe.  
  
> [!NOTE]
>  Le parent d’un <xref:System.Windows.Documents.Adorner> est la <xref:System.Windows.Documents.AdornerLayer> qui restitue le <xref:System.Windows.Documents.Adorner>, pas l’élément orné.  
  
 L’exemple suivant montre une classe qui implémente un ornement simple. L’orne simplement les angles d’un <xref:System.Windows.UIElement> avec des cercles.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
 [!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]  
  
 L’illustration suivante montre le SimpleCircleAdorner appliqué à un <xref:System.Windows.Controls.TextBox>.  
  
 ![Capture d’écran qui affiche une zone de texte ornée.](./media/adorners-overview/simplecircleadorner-textbox.png)  
  
<a name="rendering_behavior_for_Adorners"></a>   
## <a name="rendering-behavior-for-adorners"></a>Comportement de rendu des ornements  
 Il est important de noter que les ornements n’incluent aucun comportement de rendu inhérent ; il appartient donc à l’implémenteur d’un ornement de vérifier son rendu.   Une façon courante d’implémentation du comportement de rendu consiste à remplacer le <xref:System.Windows.UIElement.OnRender%2A> méthode et l’utilisation d’un ou plusieurs <xref:System.Windows.Media.DrawingContext> objets pour restituer les visuels de l’ornement en fonction des besoins (comme indiqué dans l’exemple ci-dessus).  
  
> [!NOTE]
>  Tout ce que vous placez dans la couche d’ornement s’affiche au dessus de tous les styles que vous avez définis. En d’autres termes, les ornements sont toujours visuellement en haut et ne peuvent pas être substitués à l’aide de l’ordre de plan.  
  
<a name="adorner_events_hittest"></a>   
## <a name="events-and-hit-testing"></a>Événements et test de positionnement  
 Les ornements reçoivent des événements d’entrée comme n’importe quel autre <xref:System.Windows.FrameworkElement>.  Un ornement ayant toujours un ordre de plan plus élevé que l’élément qu’il orne, l’ornement reçoit des événements d’entrée (tel que <xref:System.Windows.UIElement.Drop> ou <xref:System.Windows.UIElement.MouseMove>) qui peuvent être prévus pour l’élément orné sous-jacent.  Un ornement peut écouter certains événements d’entrée et les passer à l’élément orné sous-jacent en déclenchant à nouveau l’événement.  
  
 Pour activer le test de positionnement direct d’éléments sous un ornement, définissez le test de positionnement <xref:System.Windows.UIElement.IsHitTestVisible%2A> propriété **false** sur l’ornement.  Pour plus d’informations sur le test de positionnement, consultez  
  
 [Test de positionnement dans la couche visuelle](../graphics-multimedia/hit-testing-in-the-visual-layer.md).  
  
<a name="adorn_single_element"></a>   
## <a name="adorning-a-single-uielement"></a>Ornementation d’un UIElement unique  
 Pour lier un ornement à un particulier <xref:System.Windows.UIElement>, procédez comme suit :  
  
1. Appelez la méthode statique <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour obtenir un <xref:System.Windows.Documents.AdornerLayer> de l’objet pour le <xref:System.Windows.UIElement> à orner. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> Remonte l’arborescence visuelle, en commençant à l’emplacement spécifié <xref:System.Windows.UIElement>et retourne la première couche d’ornement qu’il trouve. (Si aucune couche d’ornement n’est trouvée, la méthode retourne Null.)  
  
2. Appelez le <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode à laquelle lier l’ornement à la cible <xref:System.Windows.UIElement>.  
  
 L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) à un <xref:System.Windows.Controls.TextBox> nommé *myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.  
  
<a name="adorn_children_panel"></a>   
## <a name="adorning-the-children-of-a-panel"></a>Ornementation des enfants d’un panneau  
 Pour lier un ornement aux enfants d’un <xref:System.Windows.Controls.Panel>, procédez comme suit :  
  
1. Appelez le `static` méthode <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour rechercher une couche d’ornement pour l’élément dont les enfants doivent être ornés.  
  
2. Énumérez les enfants de l’élément parent et appelez le <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier un ornement à chaque élément enfant.  
  
 L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) aux enfants d’un <xref:System.Windows.Controls.StackPanel> nommé *myStackPanel*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media.AdornerHitTestResult>
- [Vue d’ensemble des formes et dessins de base dans WPF](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [Peinture avec des images, des dessins et des objets visuels](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [Vue d’ensemble des objets de dessin](../graphics-multimedia/drawing-objects-overview.md)
- [Rubriques de guide pratique](adorners-how-to-topics.md)
