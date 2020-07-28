---
title: Vue d'ensemble des ornements
description: Découvrez Windows Presentation Foundation ornements, un type spécial de FrameworkElement qui fournit des piles à un utilisateur, telles que des handles fonctionnels pour des éléments.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: 43d4af9f86c6ae72a61f86d1ca19405c2dcc6cc8
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167736"
---
# <a name="adorners-overview"></a><span data-ttu-id="b26dd-103">Vue d'ensemble des ornements</span><span class="sxs-lookup"><span data-stu-id="b26dd-103">Adorners Overview</span></span>

<span data-ttu-id="b26dd-104">Les ornements sont un type spécial de <xref:System.Windows.FrameworkElement> , utilisé pour fournir des signaux visuels à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="b26dd-104">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="b26dd-105">Les ornements permettent notamment d’ajouter des descripteurs fonctionnels à des éléments ou de fournir des informations d’état sur un contrôle.</span><span class="sxs-lookup"><span data-stu-id="b26dd-105">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="b26dd-106">À propos des ornements</span><span class="sxs-lookup"><span data-stu-id="b26dd-106">About Adorners</span></span>

<span data-ttu-id="b26dd-107">Un <xref:System.Windows.Documents.Adorner> est un personnalisé <xref:System.Windows.FrameworkElement> qui est lié à un <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="b26dd-107">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="b26dd-108">Les ornements sont restitués dans un <xref:System.Windows.Documents.AdornerLayer> , qui est une surface de rendu toujours au-dessus de l’élément orné ou d’une collection d’éléments ornés.</span><span class="sxs-lookup"><span data-stu-id="b26dd-108">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="b26dd-109">Le rendu d’un ornement est indépendant du rendu du <xref:System.Windows.UIElement> auquel l’ornement est lié.</span><span class="sxs-lookup"><span data-stu-id="b26dd-109">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="b26dd-110">Un ornement est généralement positionné par rapport à l’élément auquel il est lié, à l’aide de l’origine de la coordonnée 2D standard située dans l’angle supérieur gauche de l’élément orné.</span><span class="sxs-lookup"><span data-stu-id="b26dd-110">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="b26dd-111">Parmi les applications courantes des ornements, citons les suivantes :</span><span class="sxs-lookup"><span data-stu-id="b26dd-111">Common applications for adorners include:</span></span>

- <span data-ttu-id="b26dd-112">Ajout de handles fonctionnels à un <xref:System.Windows.UIElement> qui permet à un utilisateur de manipuler l’élément d’une certaine façon (redimensionner, faire pivoter, repositionner, etc.).</span><span class="sxs-lookup"><span data-stu-id="b26dd-112">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="b26dd-113">Retour visuel pour indiquer différents états, ou en réponse à différents événements</span><span class="sxs-lookup"><span data-stu-id="b26dd-113">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="b26dd-114">Superposition des décorations visuelles sur un <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="b26dd-114">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="b26dd-115">Masquer ou substituer visuellement tout ou partie d’un <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="b26dd-115">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="b26dd-116">fournit une infrastructure de base pour orner des éléments visuels.</span><span class="sxs-lookup"><span data-stu-id="b26dd-116">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="b26dd-117">Le tableau suivant répertorie les principaux types utilisés pour orner des objets et leur but.</span><span class="sxs-lookup"><span data-stu-id="b26dd-117">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="b26dd-118">Voici quelques exemples d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="b26dd-118">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="b26dd-119">Classe de base abstraite à partir de laquelle toutes les implémentations d’ornement concrètes sont héritées.</span><span class="sxs-lookup"><span data-stu-id="b26dd-119">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="b26dd-120">Classe représentant une couche de rendu pour le ou les ornements d’un ou plusieurs éléments ornés.</span><span class="sxs-lookup"><span data-stu-id="b26dd-120">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="b26dd-121">Classe permettant d’associer une couche d’ornement à une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="b26dd-121">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="b26dd-122">Implémentation d’un ornement personnalisé</span><span class="sxs-lookup"><span data-stu-id="b26dd-122">Implementing a Custom Adorner</span></span>

<span data-ttu-id="b26dd-123">L’infrastructure des ornements fournie par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est principalement destinée à prendre en charge la création d’ornements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="b26dd-123">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="b26dd-124">Un ornement personnalisé est créé en implémentant une classe qui hérite de la classe abstraite <xref:System.Windows.Documents.Adorner> .</span><span class="sxs-lookup"><span data-stu-id="b26dd-124">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="b26dd-125">Le parent d’un <xref:System.Windows.Documents.Adorner> est le <xref:System.Windows.Documents.AdornerLayer> qui restitue <xref:System.Windows.Documents.Adorner> , et non l’élément qui est orné.</span><span class="sxs-lookup"><span data-stu-id="b26dd-125">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="b26dd-126">L’exemple suivant montre une classe qui implémente un ornement simple.</span><span class="sxs-lookup"><span data-stu-id="b26dd-126">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="b26dd-127">L’ornement d’exemple Orne simplement les angles d’un <xref:System.Windows.UIElement> avec des cercles.</span><span class="sxs-lookup"><span data-stu-id="b26dd-127">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="b26dd-128">L’illustration suivante montre le SimpleCircleAdorner appliqué à un <xref:System.Windows.Controls.TextBox> :</span><span class="sxs-lookup"><span data-stu-id="b26dd-128">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![Capture d’écran montrant une zone de texte ornée.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="b26dd-130">Comportement de rendu des ornements</span><span class="sxs-lookup"><span data-stu-id="b26dd-130">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="b26dd-131">Il est important de noter que les ornements n’incluent aucun comportement de rendu inhérent ; il appartient donc à l’implémenteur d’un ornement de vérifier son rendu.</span><span class="sxs-lookup"><span data-stu-id="b26dd-131">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="b26dd-132">Une méthode courante pour implémenter le comportement de rendu consiste à substituer la <xref:System.Windows.UIElement.OnRender%2A> méthode et à utiliser un ou plusieurs <xref:System.Windows.Media.DrawingContext> objets pour restituer les visuels de l’ornement en fonction des besoins (comme indiqué dans l’exemple ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="b26dd-132">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="b26dd-133">Tout ce que vous placez dans la couche d’ornement s’affiche au dessus de tous les styles que vous avez définis.</span><span class="sxs-lookup"><span data-stu-id="b26dd-133">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="b26dd-134">En d’autres termes, les ornements sont toujours visuellement en haut et ne peuvent pas être substitués à l’aide de l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="b26dd-134">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="b26dd-135">Événements et test de positionnement</span><span class="sxs-lookup"><span data-stu-id="b26dd-135">Events and Hit Testing</span></span>

<span data-ttu-id="b26dd-136">Les ornements reçoivent des événements d’entrée comme n’importe quel autre <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="b26dd-136">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="b26dd-137">Étant donné qu’un ornement a toujours un ordre de plan plus élevé que l’élément qu’il Orne, l’ornement reçoit des événements d’entrée (tels que <xref:System.Windows.UIElement.Drop> ou <xref:System.Windows.UIElement.MouseMove> ) qui peuvent être prévus pour l’élément orné sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="b26dd-137">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="b26dd-138">Un ornement peut écouter certains événements d’entrée et les passer à l’élément orné sous-jacent en déclenchant à nouveau l’événement.</span><span class="sxs-lookup"><span data-stu-id="b26dd-138">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="b26dd-139">Pour activer le test de positionnement direct d’éléments sous un ornement, affectez à la propriété de test de positionnement la <xref:System.Windows.UIElement.IsHitTestVisible%2A> **valeur false** sur l’ornement.</span><span class="sxs-lookup"><span data-stu-id="b26dd-139">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="b26dd-140">Pour plus d’informations sur le test de positionnement, consultez [test de positionnement dans la couche visuelle](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="b26dd-140">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="b26dd-141">Ornementation d’un UIElement unique</span><span class="sxs-lookup"><span data-stu-id="b26dd-141">Adorning a Single UIElement</span></span>

<span data-ttu-id="b26dd-142">Pour lier un ornement à un particulier <xref:System.Windows.UIElement> , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b26dd-142">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="b26dd-143">Appelez la méthode statique <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour obtenir un <xref:System.Windows.Documents.AdornerLayer> objet pour le <xref:System.Windows.UIElement> à orner.</span><span class="sxs-lookup"><span data-stu-id="b26dd-143">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="b26dd-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>parcourt l’arborescence d’éléments visuels, en commençant au spécifié <xref:System.Windows.UIElement> , et retourne la première couche d’ornements qu’elle trouve.</span><span class="sxs-lookup"><span data-stu-id="b26dd-144"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="b26dd-145">(Si aucune couche d’ornement n’est trouvée, la méthode retourne Null.)</span><span class="sxs-lookup"><span data-stu-id="b26dd-145">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="b26dd-146">Appelez la <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier l’ornement à la cible <xref:System.Windows.UIElement> .</span><span class="sxs-lookup"><span data-stu-id="b26dd-146">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="b26dd-147">L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) à <xref:System.Windows.Controls.TextBox> un *myTextBox*nommé :</span><span class="sxs-lookup"><span data-stu-id="b26dd-147">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="b26dd-148">L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="b26dd-148">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="b26dd-149">Ornementation des enfants d’un panneau</span><span class="sxs-lookup"><span data-stu-id="b26dd-149">Adorning the Children of a Panel</span></span>

<span data-ttu-id="b26dd-150">Pour lier un ornement aux enfants d’un <xref:System.Windows.Controls.Panel> , procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b26dd-150">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="b26dd-151">Appelez la `static` méthode <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> pour rechercher une couche d’ornement pour l’élément dont les enfants doivent être ornés.</span><span class="sxs-lookup"><span data-stu-id="b26dd-151">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="b26dd-152">Énumérez les enfants de l’élément parent et appelez la <xref:System.Windows.Documents.AdornerLayer.Add%2A> méthode pour lier un ornement à chaque élément enfant.</span><span class="sxs-lookup"><span data-stu-id="b26dd-152">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="b26dd-153">L’exemple suivant lie un SimpleCircleAdorner (illustré ci-dessus) aux enfants d’un <xref:System.Windows.Controls.StackPanel> *myStackPanel*nommé :</span><span class="sxs-lookup"><span data-stu-id="b26dd-153">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="b26dd-154">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b26dd-154">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="b26dd-155">Vue d'ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="b26dd-155">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="b26dd-156">Peinture avec des objets d'image, de dessin et visuels</span><span class="sxs-lookup"><span data-stu-id="b26dd-156">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="b26dd-157">Vue d'ensemble des objets Drawing</span><span class="sxs-lookup"><span data-stu-id="b26dd-157">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="b26dd-158">Rubriques Comment</span><span class="sxs-lookup"><span data-stu-id="b26dd-158">How-to Topics</span></span>](adorners-how-to-topics.md)
