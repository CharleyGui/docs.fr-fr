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
# <a name="graphics-and-multimedia"></a><span data-ttu-id="66c7d-102">Graphiques et multimédia</span><span class="sxs-lookup"><span data-stu-id="66c7d-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="66c7d-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prend en charge le contenu multimédia, les graphiques vectoriels, l’animation et la composition de contenu, ce qui permet aux développeurs de créer facilement des interfaces utilisateur et du contenu intéressants.</span><span class="sxs-lookup"><span data-stu-id="66c7d-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="66c7d-104">À l’aide de Visual Studio, vous pouvez créer des graphiques vectoriels ou des animations complexes et intégrer les médias dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="66c7d-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="66c7d-105">Cette rubrique présente les fonctionnalités graphiques, d’animation et multimédia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qui vous permettent d’ajouter des graphiques, des effets de transition, du son et de la vidéo à vos applications.</span><span class="sxs-lookup"><span data-stu-id="66c7d-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="66c7d-106">L’utilisation de types WPF dans un service Windows est fortement déconseillée.</span><span class="sxs-lookup"><span data-stu-id="66c7d-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="66c7d-107">Si vous tentez d’utiliser des types WPF dans un service Windows, celui-ci risque de ne pas fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="66c7d-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="66c7d-108">Nouveautés Graphiques et multimédia dans WPF 4</span><span class="sxs-lookup"><span data-stu-id="66c7d-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="66c7d-109">Plusieurs modifications ont été apportées aux graphiques et aux animations.</span><span class="sxs-lookup"><span data-stu-id="66c7d-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="66c7d-110">Arrondi de disposition</span><span class="sxs-lookup"><span data-stu-id="66c7d-110">Layout Rounding</span></span>

  <span data-ttu-id="66c7d-111">Lorsque le bord d’un objet se trouve au milieu d’un dispositif de pixel, le système de graphiques indépendant des PPP peut créer des artefacts de rendu, tels que des bords flous ou semi-transparents.</span><span class="sxs-lookup"><span data-stu-id="66c7d-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="66c7d-112">Les versions précédentes de WPF incluaient l’accrochage pixel pour aider à gérer ce cas.</span><span class="sxs-lookup"><span data-stu-id="66c7d-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="66c7d-113">L’arrondi de position, introduit dans Silverlight 2, est une autre façon de déplacer des éléments afin que les bords tombent sur les limites de pixels entières.</span><span class="sxs-lookup"><span data-stu-id="66c7d-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="66c7d-114">WPF prend maintenant en <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> charge l’arrondissement de mise en page avec la propriété ci-jointe sur <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="66c7d-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="66c7d-115">Composition en cache</span><span class="sxs-lookup"><span data-stu-id="66c7d-115">Cached Composition</span></span>

  <span data-ttu-id="66c7d-116">En utilisant <xref:System.Windows.Media.BitmapCache> le <xref:System.Windows.Media.BitmapCacheBrush> nouveau et les classes, vous pouvez mettre en cache une partie complexe de l’arbre visuel comme une bitmap et améliorer considérablement le temps de rendu.</span><span class="sxs-lookup"><span data-stu-id="66c7d-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="66c7d-117">L’image bitmap reste réactive aux actions de l’utilisateur, comme des clics de souris, et vous pouvez la peindre sur d’autres éléments comme n’importe quel pinceau.</span><span class="sxs-lookup"><span data-stu-id="66c7d-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="66c7d-118">Prise en charge du Nuanceur de pixels 3</span><span class="sxs-lookup"><span data-stu-id="66c7d-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="66c7d-119">WPF 4 s’appuie <xref:System.Windows.Media.Effects.ShaderEffect> sur le support introduit dans WPF 3.5 SP1 en permettant aux applications d’écrire des effets en utilisant Pixel Shader (PS) version 3.0.</span><span class="sxs-lookup"><span data-stu-id="66c7d-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="66c7d-120">Le modèle du nuanceur PS 3.0 est plus sophistiqué que le modèle PS 2.0, pour davantage d’effets sur le matériel pris en charge.</span><span class="sxs-lookup"><span data-stu-id="66c7d-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="66c7d-121">Fonctions d'accélération</span><span class="sxs-lookup"><span data-stu-id="66c7d-121">Easing Functions</span></span>

  <span data-ttu-id="66c7d-122">Vous pouvez améliorer les animations avec les fonctions d’accélération, qui vous donnent un contrôle supplémentaire sur le comportement des animations.</span><span class="sxs-lookup"><span data-stu-id="66c7d-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="66c7d-123">Par exemple, vous <xref:System.Windows.Media.Animation.ElasticEase> pouvez appliquer une animation à une animation pour donner à l’animation un comportement élastique.</span><span class="sxs-lookup"><span data-stu-id="66c7d-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="66c7d-124">Pour plus d’informations, voir <xref:System.Windows.Media.Animation> les types d’assouplissement dans l’espace nom.</span><span class="sxs-lookup"><span data-stu-id="66c7d-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="66c7d-125">Graphiques et rendu</span><span class="sxs-lookup"><span data-stu-id="66c7d-125">Graphics and Rendering</span></span>

<span data-ttu-id="66c7d-126">WPF inclut le support pour des graphismes 2D de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="66c7d-126">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="66c7d-127">La fonctionnalité inclut des pinceaux, des géométries, des images, des formes et des transformations.</span><span class="sxs-lookup"><span data-stu-id="66c7d-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="66c7d-128">Pour plus d’informations, consultez [Graphiques](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="66c7d-129">Le rendu des éléments graphiques <xref:System.Windows.Media.Visual> est basé sur la classe.</span><span class="sxs-lookup"><span data-stu-id="66c7d-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="66c7d-130">La structure des objets visuels à l’écran est décrite par l’arborescence visuelle.</span><span class="sxs-lookup"><span data-stu-id="66c7d-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="66c7d-131">Pour plus d’informations, consultez [Vue d’ensemble du rendu graphique WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="66c7d-132">Formes 2D</span><span class="sxs-lookup"><span data-stu-id="66c7d-132">2D Shapes</span></span>

<span data-ttu-id="66c7d-133">WPF fournit une bibliothèque de formes 2D couramment utilisées et dessinées par vecteur, telles que des rectangles et des ellipses, que l’illustration suivante montre.</span><span class="sxs-lookup"><span data-stu-id="66c7d-133">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagramme affichant des ellipses et des rectangles.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="66c7d-135">Ces formes intrinsèques de WPF ne sont pas seulement des formes : ce sont des éléments programmables qui implémentent de nombreuses fonctionnalités que vous attendez de la plupart des contrôles courants, qui incluent l’entrée du clavier et de la souris.</span><span class="sxs-lookup"><span data-stu-id="66c7d-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="66c7d-136">L’exemple suivant montre <xref:System.Windows.UIElement.MouseUp> comment gérer l’événement soulevé en cliquant sur un <xref:System.Windows.Shapes.Ellipse> élément.</span><span class="sxs-lookup"><span data-stu-id="66c7d-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="66c7d-137">L’illustration suivante montre la sortie de l’exemple de balisage et code-behind [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.</span><span class="sxs-lookup"><span data-stu-id="66c7d-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Une boîte de messages disant "Vous avez cliqué sur l’ellipse!"](./media/index/messagebox-text-output.png)

<span data-ttu-id="66c7d-139">Pour plus d’informations, consultez [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="66c7d-140">Pour obtenir un exemple d’introduction, consultez [Exemples d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="66c7d-140">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="66c7d-141">Géométries 2D</span><span class="sxs-lookup"><span data-stu-id="66c7d-141">2D Geometries</span></span>

<span data-ttu-id="66c7d-142">Lorsque les formes 2D que WPF fournit ne sont pas suffisantes, vous pouvez utiliser le support WPF pour les géométries et les chemins pour créer votre propre.</span><span class="sxs-lookup"><span data-stu-id="66c7d-142">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="66c7d-143">L’illustration suivante montre comment vous pouvez utiliser des géométries pour créer des formes, comme un pinceau à dessin, et pour couper d’autres éléments WPF.</span><span class="sxs-lookup"><span data-stu-id="66c7d-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Capture d’écran montrant comment vous pouvez utiliser des géométries pour créer des formes.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="66c7d-145">Pour plus d’informations, voir [Aperçu de la géométrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="66c7d-146">Pour obtenir un exemple d’introduction, consultez [Exemples de géométries](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="66c7d-146">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="66c7d-147">Effets 2D</span><span class="sxs-lookup"><span data-stu-id="66c7d-147">2D Effects</span></span>

<span data-ttu-id="66c7d-148">WPF fournit une bibliothèque de classes 2D que vous pouvez utiliser pour créer une variété d’effets.</span><span class="sxs-lookup"><span data-stu-id="66c7d-148">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="66c7d-149">La capacité de rendu 2D de WPF offre la possibilité de peindre [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] des éléments qui ont des gradients, des bitmaps, des dessins et des vidéos; et de les manipuler en utilisant la rotation, l’échelle et la faussement.</span><span class="sxs-lookup"><span data-stu-id="66c7d-149">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="66c7d-150">L’illustration suivante donne un exemple des nombreux effets que vous pouvez réaliser en utilisant des pinceaux WPF.</span><span class="sxs-lookup"><span data-stu-id="66c7d-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Illustration montrant les différents pinceaux WPF et éléments de peinture.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="66c7d-152">Pour plus d’informations, voir [WPF Brushes Aperçu](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="66c7d-153">Pour obtenir un exemple d’introduction, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="66c7d-153">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="66c7d-154">Rendu 3D</span><span class="sxs-lookup"><span data-stu-id="66c7d-154">3D Rendering</span></span>

<span data-ttu-id="66c7d-155">WPF fournit un ensemble de capacités de rendu 3D qui s’intègrent avec le support [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]graphique 2D dans WPF afin que vous créiez une mise en page plus excitante, et la visualisation des données.</span><span class="sxs-lookup"><span data-stu-id="66c7d-155">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="66c7d-156">À une extrémité du spectre, WPF vous permet de rendre des images 2D sur les surfaces des formes 3D, ce que l’illustration suivante démontre.</span><span class="sxs-lookup"><span data-stu-id="66c7d-156">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Capture d’écran d’un échantillon montrant des formes 3D avec des textures différentes.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="66c7d-158">Pour plus d’informations, voir [3D Graphics Overview](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-158">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="66c7d-159">Pour un échantillon d’introduction, voir [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="66c7d-159">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="66c7d-160">Animation</span><span class="sxs-lookup"><span data-stu-id="66c7d-160">Animation</span></span>

<span data-ttu-id="66c7d-161">Utilisez l’animation pour agrandir, faire bouger, faire pivoter et réaliser des fondus avec les contrôles et les éléments pour créer des transitions de page intéressantes, et plus encore.</span><span class="sxs-lookup"><span data-stu-id="66c7d-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="66c7d-162">Parce que WPF vous permet d’animer la plupart des propriétés, non seulement vous pouvez animer la plupart des objets WPF, mais vous pouvez également utiliser WPF pour animer des objets personnalisés que vous créez.</span><span class="sxs-lookup"><span data-stu-id="66c7d-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Capture d’écran d’un cube animé.](./media/index/animate-custom-objects.png)

<span data-ttu-id="66c7d-164">Pour plus d’informations, voir [Aperçu animation](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="66c7d-165">Pour obtenir un exemple, consultez [Galerie d’exemples d’animation](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="66c7d-165">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="66c7d-166">Médias</span><span class="sxs-lookup"><span data-stu-id="66c7d-166">Media</span></span>

<span data-ttu-id="66c7d-167">Les images, la vidéo et l’audio constituent des méthodes multimédia riches de transférer des informations et des expériences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="66c7d-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="66c7d-168">Images</span><span class="sxs-lookup"><span data-stu-id="66c7d-168">Images</span></span>

<span data-ttu-id="66c7d-169">Les images, comprenant les icônes, les arrière-plans et même des parties des animations, sont une composante essentielle de la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="66c7d-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="66c7d-170">Parce que vous avez souvent besoin d’utiliser des images, WPF expose la possibilité de travailler avec eux de diverses façons.</span><span class="sxs-lookup"><span data-stu-id="66c7d-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="66c7d-171">L’illustration suivante montre l’une de ces façons.</span><span class="sxs-lookup"><span data-stu-id="66c7d-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="66c7d-172">![Capture d’écran d’échantillon de style](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="66c7d-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="66c7d-173">Pour plus d’informations, voir [Aperçu de l’imagerie](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="66c7d-174">Audio et vidéo</span><span class="sxs-lookup"><span data-stu-id="66c7d-174">Video and Audio</span></span>

<span data-ttu-id="66c7d-175">Une caractéristique essentielle des capacités graphiques de WPF est de fournir un soutien natif pour travailler avec le multimédia, qui comprend la vidéo et l’audio.</span><span class="sxs-lookup"><span data-stu-id="66c7d-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="66c7d-176">L’exemple suivant montre comment insérer un lecteur multimédia dans une application.</span><span class="sxs-lookup"><span data-stu-id="66c7d-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="66c7d-177"><xref:System.Windows.Controls.MediaElement>est capable de jouer à la fois la vidéo et l’audio, et est assez extensible pour permettre la création facile d’UIs personnalisés.</span><span class="sxs-lookup"><span data-stu-id="66c7d-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="66c7d-178">Pour plus d'informations, consultez [Vue d’ensemble du multimédia](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66c7d-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66c7d-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66c7d-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="66c7d-180">Graphisme 2D et acquisition d’images</span><span class="sxs-lookup"><span data-stu-id="66c7d-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="66c7d-181">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="66c7d-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="66c7d-182">Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="66c7d-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="66c7d-183">Peinture avec des images, des dessins et des objets visuels</span><span class="sxs-lookup"><span data-stu-id="66c7d-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="66c7d-184">Rubriques "Comment" relatives à l'animation et au minutage</span><span class="sxs-lookup"><span data-stu-id="66c7d-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="66c7d-185">Aperçu graphique 3D</span><span class="sxs-lookup"><span data-stu-id="66c7d-185">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="66c7d-186">Vue d’ensemble multimédia</span><span class="sxs-lookup"><span data-stu-id="66c7d-186">Multimedia Overview</span></span>](multimedia-overview.md)
