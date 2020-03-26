---
title: Graphiques et multimédia
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: 8636afcc5b63b71dc729812a7f3eb4945ba49494
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112035"
---
# <a name="graphics-and-multimedia"></a>Graphiques et multimédia

<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prend en charge le contenu multimédia, les graphiques vectoriels, l’animation et la composition de contenu, ce qui permet aux développeurs de créer facilement des interfaces utilisateur et du contenu intéressants. À l’aide de Visual Studio, vous pouvez créer des graphiques vectoriels ou des animations complexes et intégrer les médias dans vos applications.

Cette rubrique présente les fonctionnalités graphiques, d’animation et multimédia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qui vous permettent d’ajouter des graphiques, des effets de transition, du son et de la vidéo à vos applications.

> [!NOTE]
> L’utilisation de types WPF dans un service Windows est fortement déconseillée. Si vous tentez d’utiliser des types WPF dans un service Windows, celui-ci risque de ne pas fonctionner comme prévu.

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a>Nouveautés Graphiques et multimédia dans WPF 4

Plusieurs modifications ont été apportées aux graphiques et aux animations.

- Arrondi de disposition

  Lorsque le bord d’un objet se trouve au milieu d’un dispositif de pixel, le système de graphiques indépendant des PPP peut créer des artefacts de rendu, tels que des bords flous ou semi-transparents. Les versions précédentes de WPF incluaient l’accrochage pixel pour aider à gérer ce cas. L’arrondi de position, introduit dans Silverlight 2, est une autre façon de déplacer des éléments afin que les bords tombent sur les limites de pixels entières. WPF prend maintenant en <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> charge l’arrondissement de mise en page avec la propriété ci-jointe sur <xref:System.Windows.FrameworkElement>.

- Composition en cache

  En utilisant <xref:System.Windows.Media.BitmapCache> le <xref:System.Windows.Media.BitmapCacheBrush> nouveau et les classes, vous pouvez mettre en cache une partie complexe de l’arbre visuel comme une bitmap et améliorer considérablement le temps de rendu. L’image bitmap reste réactive aux actions de l’utilisateur, comme des clics de souris, et vous pouvez la peindre sur d’autres éléments comme n’importe quel pinceau.

- Prise en charge du Nuanceur de pixels 3

  WPF 4 s’appuie <xref:System.Windows.Media.Effects.ShaderEffect> sur le support introduit dans WPF 3.5 SP1 en permettant aux applications d’écrire des effets en utilisant Pixel Shader (PS) version 3.0. Le modèle du nuanceur PS 3.0 est plus sophistiqué que le modèle PS 2.0, pour davantage d’effets sur le matériel pris en charge.

- Fonctions d'accélération

  Vous pouvez améliorer les animations avec les fonctions d’accélération, qui vous donnent un contrôle supplémentaire sur le comportement des animations. Par exemple, vous <xref:System.Windows.Media.Animation.ElasticEase> pouvez appliquer une animation à une animation pour donner à l’animation un comportement élastique. Pour plus d’informations, voir <xref:System.Windows.Media.Animation> les types d’assouplissement dans l’espace nom.

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a>Graphiques et rendu

WPF inclut le support pour des graphismes 2D de haute qualité. La fonctionnalité inclut des pinceaux, des géométries, des images, des formes et des transformations. Pour plus d’informations, consultez [Graphiques](graphics.md). Le rendu des éléments graphiques <xref:System.Windows.Media.Visual> est basé sur la classe. La structure des objets visuels à l’écran est décrite par l’arborescence visuelle. Pour plus d’informations, consultez [Vue d’ensemble du rendu graphique WPF](wpf-graphics-rendering-overview.md).

### <a name="2d-shapes"></a>Formes 2D

WPF fournit une bibliothèque de formes 2D couramment utilisées et dessinées par vecteur, telles que des rectangles et des ellipses, que l’illustration suivante montre.

![Diagramme affichant des ellipses et des rectangles.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

Ces formes intrinsèques de WPF ne sont pas seulement des formes : ce sont des éléments programmables qui implémentent de nombreuses fonctionnalités que vous attendez de la plupart des contrôles courants, qui incluent l’entrée du clavier et de la souris. L’exemple suivant montre <xref:System.Windows.UIElement.MouseUp> comment gérer l’événement soulevé en cliquant sur un <xref:System.Windows.Shapes.Ellipse> élément.

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

L’illustration suivante montre la sortie de l’exemple de balisage et code-behind [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.

![Une boîte de messages disant "Vous avez cliqué sur l’ellipse!"](./media/index/messagebox-text-output.png)

Pour plus d’informations, consultez [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md). Pour obtenir un exemple d’introduction, consultez [Exemples d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).

### <a name="2d-geometries"></a>Géométries 2D

Lorsque les formes 2D que WPF fournit ne sont pas suffisantes, vous pouvez utiliser le support WPF pour les géométries et les chemins pour créer votre propre. L’illustration suivante montre comment vous pouvez utiliser des géométries pour créer des formes, comme un pinceau à dessin, et pour couper d’autres éléments WPF.

![Capture d’écran montrant comment vous pouvez utiliser des géométries pour créer des formes.](./media/index/use-geometries-create-shapes.png)

Pour plus d’informations, voir [Aperçu de la géométrie](geometry-overview.md). Pour obtenir un exemple d’introduction, consultez [Exemples de géométries](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).

### <a name="2d-effects"></a>Effets 2D

WPF fournit une bibliothèque de classes 2D que vous pouvez utiliser pour créer une variété d’effets. La capacité de rendu 2D de WPF offre la possibilité de peindre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des éléments qui ont des gradients, des bitmaps, des dessins et des vidéos; et de les manipuler en utilisant la rotation, l’échelle et la faussement. L’illustration suivante donne un exemple des nombreux effets que vous pouvez réaliser en utilisant des pinceaux WPF.

![Illustration montrant les différents pinceaux WPF et éléments de peinture.](./media/index/brushes-paint-elements.png)

Pour plus d’informations, voir [WPF Brushes Aperçu](wpf-brushes-overview.md). Pour obtenir un exemple d’introduction, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).

<a name="rendering"></a>

## <a name="3d-rendering"></a>Rendu 3D

WPF fournit un ensemble de capacités de rendu 3D qui s’intègrent avec le support [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]graphique 2D dans WPF afin que vous créiez une mise en page plus excitante, et la visualisation des données. À une extrémité du spectre, WPF vous permet de rendre des images 2D sur les surfaces des formes 3D, ce que l’illustration suivante démontre.

![Capture d’écran d’un échantillon montrant des formes 3D avec des textures différentes.](./media/index/visual-three-dimensional-shape.png)

Pour plus d’informations, voir [3D Graphics Overview](3-d-graphics-overview.md). Pour un échantillon d’introduction, voir [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).

<a name="animation"></a>

## <a name="animation"></a>Animation

Utilisez l’animation pour agrandir, faire bouger, faire pivoter et réaliser des fondus avec les contrôles et les éléments pour créer des transitions de page intéressantes, et plus encore. Parce que WPF vous permet d’animer la plupart des propriétés, non seulement vous pouvez animer la plupart des objets WPF, mais vous pouvez également utiliser WPF pour animer des objets personnalisés que vous créez.

![Capture d’écran d’un cube animé.](./media/index/animate-custom-objects.png)

Pour plus d’informations, voir [Aperçu animation](animation-overview.md). Pour obtenir un exemple, consultez [Galerie d’exemples d’animation](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).

<a name="media"></a>

## <a name="media"></a>Médias

Les images, la vidéo et l’audio constituent des méthodes multimédia riches de transférer des informations et des expériences utilisateur.

### <a name="images"></a>Images

Les images, comprenant les icônes, les arrière-plans et même des parties des animations, sont une composante essentielle de la plupart des applications. Parce que vous avez souvent besoin d’utiliser des images, WPF expose la possibilité de travailler avec eux de diverses façons. L’illustration suivante montre l’une de ces façons.

![Capture d’écran d’échantillon de style](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")

Pour plus d’informations, voir [Aperçu de l’imagerie](imaging-overview.md).

### <a name="video-and-audio"></a>Audio et vidéo

Une caractéristique essentielle des capacités graphiques de WPF est de fournir un soutien natif pour travailler avec le multimédia, qui comprend la vidéo et l’audio. L’exemple suivant montre comment insérer un lecteur multimédia dans une application.

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<xref:System.Windows.Controls.MediaElement>est capable de jouer à la fois la vidéo et l’audio, et est assez extensible pour permettre la création facile d’UIs personnalisés.

Pour plus d'informations, consultez [Vue d’ensemble du multimédia](multimedia-overview.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [Graphisme 2D et acquisition d’images](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés](painting-with-solid-colors-and-gradients-overview.md)
- [Peinture avec des images, des dessins et des objets visuels](painting-with-images-drawings-and-visuals.md)
- [Rubriques "Comment" relatives à l'animation et au minutage](animation-and-timing-how-to-topics.md)
- [Aperçu graphique 3D](3-d-graphics-overview.md)
- [Vue d’ensemble multimédia](multimedia-overview.md)
