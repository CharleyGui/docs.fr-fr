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
ms.openlocfilehash: ecc54ad9453343f6306b0133fa180abd0db46f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596421"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="3be82-102">Graphiques et multimédia</span><span class="sxs-lookup"><span data-stu-id="3be82-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="3be82-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prend en charge le contenu multimédia, les graphiques vectoriels, l’animation et la composition de contenu, ce qui permet aux développeurs de créer facilement des interfaces utilisateur et du contenu intéressants.</span><span class="sxs-lookup"><span data-stu-id="3be82-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="3be82-104">À l’aide de Visual Studio, vous pouvez créer des graphiques vectoriels ou des animations complexes et intégrer des médias dans vos applications.</span><span class="sxs-lookup"><span data-stu-id="3be82-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="3be82-105">Cette rubrique présente les fonctionnalités graphiques, d’animation et multimédia de [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], qui vous permettent d’ajouter des graphiques, des effets de transition, du son et de la vidéo à vos applications.</span><span class="sxs-lookup"><span data-stu-id="3be82-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="3be82-106">L’utilisation de types WPF dans un service Windows est fortement déconseillée.</span><span class="sxs-lookup"><span data-stu-id="3be82-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="3be82-107">Si vous tentez d’utiliser des types WPF dans un service Windows, celui-ci risque de ne pas fonctionner comme prévu.</span><span class="sxs-lookup"><span data-stu-id="3be82-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="3be82-108">Nouveautés Graphiques et multimédia dans WPF 4</span><span class="sxs-lookup"><span data-stu-id="3be82-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="3be82-109">Plusieurs modifications ont été apportées aux graphiques et aux animations.</span><span class="sxs-lookup"><span data-stu-id="3be82-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="3be82-110">Arrondi de disposition</span><span class="sxs-lookup"><span data-stu-id="3be82-110">Layout Rounding</span></span>

  <span data-ttu-id="3be82-111">Lorsque le bord d’un objet se trouve au milieu d’un dispositif de pixel, le système de graphiques indépendant des PPP peut créer des artefacts de rendu, tels que des bords flous ou semi-transparents.</span><span class="sxs-lookup"><span data-stu-id="3be82-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="3be82-112">Les versions précédentes de WPF incluaient l’accrochage pixel pour aider à gérer ce cas.</span><span class="sxs-lookup"><span data-stu-id="3be82-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="3be82-113">L’arrondi de position, introduit dans Silverlight 2, est une autre façon de déplacer des éléments afin que les bords tombent sur les limites de pixels entières.</span><span class="sxs-lookup"><span data-stu-id="3be82-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="3be82-114">WPF prend désormais en charge l’arrondi de disposition avec la <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> propriété jointe sur <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="3be82-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="3be82-115">Composition en cache</span><span class="sxs-lookup"><span data-stu-id="3be82-115">Cached Composition</span></span>

  <span data-ttu-id="3be82-116">En utilisant les nouvelles <xref:System.Windows.Media.BitmapCache> <xref:System.Windows.Media.BitmapCacheBrush> classes et, vous pouvez mettre en cache une partie complexe de l’arborescence d’éléments visuels en tant que bitmap et améliorer beaucoup le temps de rendu.</span><span class="sxs-lookup"><span data-stu-id="3be82-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="3be82-117">L’image bitmap reste réactive aux actions de l’utilisateur, comme des clics de souris, et vous pouvez la peindre sur d’autres éléments comme n’importe quel pinceau.</span><span class="sxs-lookup"><span data-stu-id="3be82-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="3be82-118">Prise en charge du Nuanceur de pixels 3</span><span class="sxs-lookup"><span data-stu-id="3be82-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="3be82-119">WPF 4 s’appuie sur la <xref:System.Windows.Media.Effects.ShaderEffect> prise en charge introduite dans wpf 3,5 SP1 en permettant aux applications d’écrire des effets à l’aide de nuanceur de pixels (PS) version 3,0.</span><span class="sxs-lookup"><span data-stu-id="3be82-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="3be82-120">Le modèle du nuanceur PS 3.0 est plus sophistiqué que le modèle PS 2.0, pour davantage d’effets sur le matériel pris en charge.</span><span class="sxs-lookup"><span data-stu-id="3be82-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="3be82-121">Fonctions d'accélération</span><span class="sxs-lookup"><span data-stu-id="3be82-121">Easing Functions</span></span>

  <span data-ttu-id="3be82-122">Vous pouvez améliorer les animations avec les fonctions d’accélération, qui vous donnent un contrôle supplémentaire sur le comportement des animations.</span><span class="sxs-lookup"><span data-stu-id="3be82-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="3be82-123">Par exemple, vous pouvez appliquer un <xref:System.Windows.Media.Animation.ElasticEase> à une animation pour que l’animation soit un comportement élastique.</span><span class="sxs-lookup"><span data-stu-id="3be82-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="3be82-124">Pour plus d’informations, consultez les types d’accélération dans l' <xref:System.Windows.Media.Animation> espace de noms.</span><span class="sxs-lookup"><span data-stu-id="3be82-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="3be82-125">Graphiques et rendu</span><span class="sxs-lookup"><span data-stu-id="3be82-125">Graphics and Rendering</span></span>

<span data-ttu-id="3be82-126">WPF prend en charge les graphiques 2D de haute qualité.</span><span class="sxs-lookup"><span data-stu-id="3be82-126">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="3be82-127">La fonctionnalité inclut des pinceaux, des géométries, des images, des formes et des transformations.</span><span class="sxs-lookup"><span data-stu-id="3be82-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="3be82-128">Pour plus d’informations, consultez [Graphiques](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="3be82-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="3be82-129">Le rendu des éléments graphiques est basé sur la <xref:System.Windows.Media.Visual> classe.</span><span class="sxs-lookup"><span data-stu-id="3be82-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="3be82-130">La structure des objets visuels à l’écran est décrite par l’arborescence visuelle.</span><span class="sxs-lookup"><span data-stu-id="3be82-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="3be82-131">Pour plus d’informations, consultez [Vue d’ensemble du rendu graphique WPF](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3be82-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="3be82-132">Formes 2D</span><span class="sxs-lookup"><span data-stu-id="3be82-132">2D Shapes</span></span>

<span data-ttu-id="3be82-133">WPF fournit une bibliothèque de formes 2D couramment utilisées et dessinées à l’image, telles que des rectangles et des ellipses, comme le montre l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="3be82-133">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diagramme montrant des ellipses et des rectangles.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="3be82-135">Ces formes WPF intrinsèques ne sont pas seulement des formes : il s’agit d’éléments programmables qui implémentent un grand nombre des fonctionnalités que vous attendez de la plupart des contrôles courants, y compris l’entrée au clavier et à la souris.</span><span class="sxs-lookup"><span data-stu-id="3be82-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="3be82-136">L’exemple suivant montre comment gérer l' <xref:System.Windows.UIElement.MouseUp> événement déclenché en cliquant sur un <xref:System.Windows.Shapes.Ellipse> élément.</span><span class="sxs-lookup"><span data-stu-id="3be82-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="3be82-137">L’illustration suivante montre la sortie de l’exemple de balisage et code-behind [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] précédent.</span><span class="sxs-lookup"><span data-stu-id="3be82-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

![Une boîte de message indiquant « vous avez cliqué sur l’ellipse ! »](./media/index/messagebox-text-output.png)

<span data-ttu-id="3be82-139">Pour plus d’informations, consultez [Vue d’ensemble des formes et dessins de base dans WPF](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3be82-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="3be82-140">Pour obtenir un exemple d’introduction, consultez [Exemples d’éléments de forme](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="3be82-140">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="3be82-141">Géométries 2D</span><span class="sxs-lookup"><span data-stu-id="3be82-141">2D Geometries</span></span>

<span data-ttu-id="3be82-142">Lorsque les formes 2D fournies par WPF ne sont pas suffisantes, vous pouvez utiliser la prise en charge WPF pour les géométries et les chemins d’accès pour créer les vôtres.</span><span class="sxs-lookup"><span data-stu-id="3be82-142">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="3be82-143">L’illustration suivante montre comment vous pouvez utiliser des géométries pour créer des formes, comme un pinceau de dessin, et pour découper d’autres éléments WPF.</span><span class="sxs-lookup"><span data-stu-id="3be82-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Capture d’écran montrant comment vous pouvez utiliser des géométries pour créer des formes.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="3be82-145">Pour plus d’informations, consultez [vue d’ensemble de Geometry](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3be82-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="3be82-146">Pour obtenir un exemple d’introduction, consultez [Exemples de géométries](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="3be82-146">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="3be82-147">Effets 2D</span><span class="sxs-lookup"><span data-stu-id="3be82-147">2D Effects</span></span>

<span data-ttu-id="3be82-148">WPF fournit une bibliothèque de classes 2D que vous pouvez utiliser pour créer un grand nombre d’effets.</span><span class="sxs-lookup"><span data-stu-id="3be82-148">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="3be82-149">La fonctionnalité de rendu 2D de WPF offre la possibilité de peindre des [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] éléments qui ont des dégradés, des bitmaps, des dessins et des vidéos, et de les manipuler à l’aide de la rotation, de la mise à l’échelle et de l’inclinaison.</span><span class="sxs-lookup"><span data-stu-id="3be82-149">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="3be82-150">L’illustration suivante donne un exemple des nombreux effets que vous pouvez obtenir à l’aide de pinceaux WPF.</span><span class="sxs-lookup"><span data-stu-id="3be82-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Illustration montrant les différents pinceaux WPF et éléments de peinture.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="3be82-152">Pour plus d’informations, consultez [vue d’ensemble des pinceaux WPF](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3be82-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="3be82-153">Pour obtenir un exemple d’introduction, consultez [Exemples de pinceaux](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="3be82-153">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="3be82-154">Rendu 3D</span><span class="sxs-lookup"><span data-stu-id="3be82-154">3D Rendering</span></span>

<span data-ttu-id="3be82-155">WPF fournit un ensemble de fonctionnalités de rendu 3D qui s’intègrent à la prise en charge des graphiques 2D dans WPF pour vous permettre de créer une disposition plus passionnante, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] , et une visualisation des données.</span><span class="sxs-lookup"><span data-stu-id="3be82-155">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="3be82-156">À une extrémité du spectre, WPF vous permet d’afficher des images 2D sur les surfaces des formes 3D, comme le montre l’illustration suivante.</span><span class="sxs-lookup"><span data-stu-id="3be82-156">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Capture d’écran d’un exemple montrant des formes 3D avec différentes textures.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="3be82-158">Pour plus d’informations, consultez [vue d’ensemble des graphiques 3D](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3be82-158">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="3be82-159">Pour obtenir un exemple d’introduction, consultez l' [exemple 3D solids](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="3be82-159">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="3be82-160">Animation</span><span class="sxs-lookup"><span data-stu-id="3be82-160">Animation</span></span>

<span data-ttu-id="3be82-161">Utilisez l’animation pour agrandir, faire bouger, faire pivoter et réaliser des fondus avec les contrôles et les éléments pour créer des transitions de page intéressantes, et plus encore.</span><span class="sxs-lookup"><span data-stu-id="3be82-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="3be82-162">Étant donné que WPF vous permet d’animer la plupart des propriétés, vous pouvez non seulement animer la plupart des objets WPF, mais également utiliser WPF pour animer des objets personnalisés que vous créez.</span><span class="sxs-lookup"><span data-stu-id="3be82-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Capture d’écran d’un cube animé.](./media/index/animate-custom-objects.png)

<span data-ttu-id="3be82-164">Pour plus d’informations, consultez [vue d’ensemble](animation-overview.md)de l’animation.</span><span class="sxs-lookup"><span data-stu-id="3be82-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="3be82-165">Pour obtenir un exemple, consultez [Galerie d’exemples d’animation](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="3be82-165">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="3be82-166">Médias</span><span class="sxs-lookup"><span data-stu-id="3be82-166">Media</span></span>

<span data-ttu-id="3be82-167">Les images, la vidéo et l’audio constituent des méthodes multimédia riches de transférer des informations et des expériences utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3be82-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="3be82-168">Images</span><span class="sxs-lookup"><span data-stu-id="3be82-168">Images</span></span>

<span data-ttu-id="3be82-169">Les images, comprenant les icônes, les arrière-plans et même des parties des animations, sont une composante essentielle de la plupart des applications.</span><span class="sxs-lookup"><span data-stu-id="3be82-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="3be82-170">Étant donné que vous devez fréquemment utiliser des images, WPF expose la possibilité de les utiliser de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="3be82-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="3be82-171">L’illustration suivante montre l’une de ces façons.</span><span class="sxs-lookup"><span data-stu-id="3be82-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="3be82-172">![Capture d’écran de l’exemple de style](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="3be82-172">![Styling sample screenshot](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="3be82-173">Pour plus d’informations, consultez [vue d’ensemble de l’acquisition d’images](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3be82-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="3be82-174">Audio et vidéo</span><span class="sxs-lookup"><span data-stu-id="3be82-174">Video and Audio</span></span>

<span data-ttu-id="3be82-175">Une fonctionnalité essentielle des fonctionnalités graphiques de WPF consiste à fournir une prise en charge native de l’utilisation de fichiers multimédias, y compris la vidéo et l’audio.</span><span class="sxs-lookup"><span data-stu-id="3be82-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="3be82-176">L’exemple suivant montre comment insérer un lecteur multimédia dans une application.</span><span class="sxs-lookup"><span data-stu-id="3be82-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="3be82-177"><xref:System.Windows.Controls.MediaElement>peut écouter à la fois des données audio et vidéo, et est suffisamment extensible pour permettre la création facile d’interfaces utilisateur personnalisées.</span><span class="sxs-lookup"><span data-stu-id="3be82-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="3be82-178">Pour plus d'informations, consultez [Vue d’ensemble du multimédia](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3be82-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3be82-179">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3be82-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="3be82-180">Graphisme 2D et acquisition d’images</span><span class="sxs-lookup"><span data-stu-id="3be82-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="3be82-181">Vue d'ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="3be82-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="3be82-182">Vue d'ensemble de la peinture avec des couleurs unies ou des dégradés</span><span class="sxs-lookup"><span data-stu-id="3be82-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="3be82-183">Peinture avec des objets d'image, de dessin et visuels</span><span class="sxs-lookup"><span data-stu-id="3be82-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="3be82-184">Rubriques "Comment" relatives à l'animation et au minutage</span><span class="sxs-lookup"><span data-stu-id="3be82-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="3be82-185">Vue d’ensemble des graphiques 3D</span><span class="sxs-lookup"><span data-stu-id="3be82-185">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="3be82-186">Vue d'ensemble du multimédia</span><span class="sxs-lookup"><span data-stu-id="3be82-186">Multimedia Overview</span></span>](multimedia-overview.md)
