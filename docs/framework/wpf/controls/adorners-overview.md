---
title: Vue d'ensemble des ornements
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], about adorners
ms.assetid: 33d4c5c2-2daf-4e45-ba9a-5b673e2b8280
ms.openlocfilehash: b41c1f10f7e1b7c1799fd27270a3eeb9899ceeb6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111177"
---
# <a name="adorners-overview"></a><span data-ttu-id="8d085-102">Vue d'ensemble des ornements</span><span class="sxs-lookup"><span data-stu-id="8d085-102">Adorners Overview</span></span>

<span data-ttu-id="8d085-103">Les adorateurs sont un <xref:System.Windows.FrameworkElement>type spécial de , utilisé pour fournir des indices visuels à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8d085-103">Adorners are a special type of <xref:System.Windows.FrameworkElement>, used to provide visual cues to a user.</span></span> <span data-ttu-id="8d085-104">Les ornements permettent notamment d’ajouter des descripteurs fonctionnels à des éléments ou de fournir des informations d’état sur un contrôle.</span><span class="sxs-lookup"><span data-stu-id="8d085-104">Among other uses, Adorners can be used to add functional handles to elements or provide state information about a control.</span></span>

## <a name="about-adorners"></a><span data-ttu-id="8d085-105">À propos des ornements</span><span class="sxs-lookup"><span data-stu-id="8d085-105">About Adorners</span></span>

<span data-ttu-id="8d085-106">Un <xref:System.Windows.Documents.Adorner> est <xref:System.Windows.FrameworkElement> une coutume qui <xref:System.Windows.UIElement>est lié à un .</span><span class="sxs-lookup"><span data-stu-id="8d085-106">An <xref:System.Windows.Documents.Adorner> is a custom <xref:System.Windows.FrameworkElement> that is bound to a <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="8d085-107">Les adorateurs sont rendus <xref:System.Windows.Documents.AdornerLayer>dans un , qui est une surface de rendu qui est toujours au-dessus de l’élément orné ou une collection d’éléments ornés.</span><span class="sxs-lookup"><span data-stu-id="8d085-107">Adorners are rendered in an <xref:System.Windows.Documents.AdornerLayer>, which is a rendering surface that is always on top of the adorned element or a collection of adorned elements.</span></span> <span data-ttu-id="8d085-108">Le rendu d’un adorant est <xref:System.Windows.UIElement> indépendant du rendu de l’adorant lié à.</span><span class="sxs-lookup"><span data-stu-id="8d085-108">Rendering of an adorner is independent from rendering of the <xref:System.Windows.UIElement> that the adorner is bound to.</span></span> <span data-ttu-id="8d085-109">Un adorant est généralement positionné par rapport à l’élément auquel il est lié, en utilisant l’origine de coordonnées 2D standard située en haut à gauche de l’élément orné.</span><span class="sxs-lookup"><span data-stu-id="8d085-109">An adorner is typically positioned relative to the element to which it is bound, using the standard 2D coordinate origin located at the upper-left of the adorned element.</span></span>

<span data-ttu-id="8d085-110">Parmi les applications courantes des ornements, citons les suivantes :</span><span class="sxs-lookup"><span data-stu-id="8d085-110">Common applications for adorners include:</span></span>

- <span data-ttu-id="8d085-111">Ajout de poignées <xref:System.Windows.UIElement> fonctionnelles à un qui permet à un utilisateur de manipuler l’élément d’une manière ou d’une autre (resize, rotate, repositionnement, etc.).</span><span class="sxs-lookup"><span data-stu-id="8d085-111">Adding functional handles to a <xref:System.Windows.UIElement> that enable a user to manipulate the element in some way (resize, rotate, reposition, etc.).</span></span>
- <span data-ttu-id="8d085-112">Retour visuel pour indiquer différents états, ou en réponse à différents événements</span><span class="sxs-lookup"><span data-stu-id="8d085-112">Provide visual feedback to indicate various states, or in response to various events.</span></span>
- <span data-ttu-id="8d085-113">Superposer les <xref:System.Windows.UIElement>décorations visuelles sur un .</span><span class="sxs-lookup"><span data-stu-id="8d085-113">Overlay visual decorations on a <xref:System.Windows.UIElement>.</span></span>
- <span data-ttu-id="8d085-114">Masquer visuellement ou remplacer une <xref:System.Windows.UIElement>partie ou la totalité d’un .</span><span class="sxs-lookup"><span data-stu-id="8d085-114">Visually mask or override part or all of a <xref:System.Windows.UIElement>.</span></span>

[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="8d085-115">fournit une infrastructure de base pour orner des éléments visuels.</span><span class="sxs-lookup"><span data-stu-id="8d085-115">provides a basic framework for adorning visual elements.</span></span> <span data-ttu-id="8d085-116">Le tableau suivant répertorie les principaux types utilisés pour orner des objets et leur but.</span><span class="sxs-lookup"><span data-stu-id="8d085-116">The following table lists the primary types used when adorning objects, and their purpose.</span></span> <span data-ttu-id="8d085-117">Voici plusieurs exemples d’utilisation :</span><span class="sxs-lookup"><span data-stu-id="8d085-117">Several usage examples follow:</span></span>

|||
|-|-|
|<xref:System.Windows.Documents.Adorner>|<span data-ttu-id="8d085-118">Classe de base abstraite à partir de laquelle toutes les implémentations d’ornement concrètes sont héritées.</span><span class="sxs-lookup"><span data-stu-id="8d085-118">An abstract base class from which all concrete adorner implementations inherit.</span></span>|
|<xref:System.Windows.Documents.AdornerLayer>|<span data-ttu-id="8d085-119">Classe représentant une couche de rendu pour le ou les ornements d’un ou plusieurs éléments ornés.</span><span class="sxs-lookup"><span data-stu-id="8d085-119">A class representing a rendering layer for the adorner(s) of one or more adorned elements.</span></span>|
|<xref:System.Windows.Documents.AdornerDecorator>|<span data-ttu-id="8d085-120">Classe permettant d’associer une couche d’ornement à une collection d’éléments.</span><span class="sxs-lookup"><span data-stu-id="8d085-120">A class that enables an adorner layer to be associated with a collection of elements.</span></span>|

## <a name="implementing-a-custom-adorner"></a><span data-ttu-id="8d085-121">Implémentation d’un ornement personnalisé</span><span class="sxs-lookup"><span data-stu-id="8d085-121">Implementing a Custom Adorner</span></span>

<span data-ttu-id="8d085-122">L’infrastructure des ornements fournie par [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est principalement destinée à prendre en charge la création d’ornements personnalisés.</span><span class="sxs-lookup"><span data-stu-id="8d085-122">The adorners framework provided by [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] is intended primarily to support the creation of custom adorners.</span></span> <span data-ttu-id="8d085-123">Un adorant personnalisé est créé en mettant en <xref:System.Windows.Documents.Adorner> œuvre une classe qui hérite de la classe abstraite.</span><span class="sxs-lookup"><span data-stu-id="8d085-123">A custom adorner is created by implementing a class that inherits from the abstract <xref:System.Windows.Documents.Adorner> class.</span></span>

> [!NOTE]
> <span data-ttu-id="8d085-124">Le parent <xref:System.Windows.Documents.Adorner> d’un est <xref:System.Windows.Documents.AdornerLayer> <xref:System.Windows.Documents.Adorner>le qui rend le , pas l’élément étant orné.</span><span class="sxs-lookup"><span data-stu-id="8d085-124">The parent of an <xref:System.Windows.Documents.Adorner> is the <xref:System.Windows.Documents.AdornerLayer> that renders the <xref:System.Windows.Documents.Adorner>, not the element being adorned.</span></span>

<span data-ttu-id="8d085-125">L’exemple suivant montre une classe qui implémente un ornement simple.</span><span class="sxs-lookup"><span data-stu-id="8d085-125">The following example shows a class that implements a simple adorner.</span></span> <span data-ttu-id="8d085-126">L’exemple orne simplement les <xref:System.Windows.UIElement> coins d’un avec des cercles.</span><span class="sxs-lookup"><span data-stu-id="8d085-126">The example adorner simply adorns the corners of a <xref:System.Windows.UIElement> with circles.</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_simplecircleadornerbody)]
[!code-vb[Adorners_SimpleCircleAdorner#_SimpleCircleAdornerBody](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_simplecircleadornerbody)]
  
<span data-ttu-id="8d085-127">L’image suivante montre le SimpleCircleAdorner appliqué à un <xref:System.Windows.Controls.TextBox>:</span><span class="sxs-lookup"><span data-stu-id="8d085-127">The following image shows the SimpleCircleAdorner applied to a <xref:System.Windows.Controls.TextBox>:</span></span>

![Capture d’écran qui montre une boîte de texte ornée.](./media/adorners-overview/simplecircleadorner-textbox.png)

## <a name="rendering-behavior-for-adorners"></a><span data-ttu-id="8d085-129">Comportement de rendu des ornements</span><span class="sxs-lookup"><span data-stu-id="8d085-129">Rendering Behavior for Adorners</span></span>

<span data-ttu-id="8d085-130">Il est important de noter que les ornements n’incluent aucun comportement de rendu inhérent ; il appartient donc à l’implémenteur d’un ornement de vérifier son rendu.</span><span class="sxs-lookup"><span data-stu-id="8d085-130">It is important to note that adorners do not include any inherent rendering behavior; ensuring that an adorner renders is the responsibility of the adorner implementer.</span></span> <span data-ttu-id="8d085-131">Une façon courante d’implémenter le <xref:System.Windows.UIElement.OnRender%2A> comportement de rendu <xref:System.Windows.Media.DrawingContext> est de remplacer la méthode et d’utiliser un ou plusieurs objets pour rendre les visuels de l’adorant au besoin (comme indiqué dans l’exemple ci-dessus).</span><span class="sxs-lookup"><span data-stu-id="8d085-131">A common way of implementing rendering behavior is to override the <xref:System.Windows.UIElement.OnRender%2A> method and use one or more <xref:System.Windows.Media.DrawingContext> objects to render the adorner's visuals as needed (as shown in the example above).</span></span>

> [!NOTE]
> <span data-ttu-id="8d085-132">Tout ce que vous placez dans la couche d’ornement s’affiche au dessus de tous les styles que vous avez définis.</span><span class="sxs-lookup"><span data-stu-id="8d085-132">Anything placed in the adorner layer is rendered on top of the rest of any styles you have set.</span></span> <span data-ttu-id="8d085-133">En d’autres termes, les ornements sont toujours visuellement en haut et ne peuvent pas être substitués à l’aide de l’ordre de plan.</span><span class="sxs-lookup"><span data-stu-id="8d085-133">In other words, adorners are always visually on top and cannot be overridden using z-order.</span></span>

## <a name="events-and-hit-testing"></a><span data-ttu-id="8d085-134">Événements et test de positionnement</span><span class="sxs-lookup"><span data-stu-id="8d085-134">Events and Hit Testing</span></span>

<span data-ttu-id="8d085-135">Les adorateurs reçoivent des événements <xref:System.Windows.FrameworkElement>d’entrée comme les autres .</span><span class="sxs-lookup"><span data-stu-id="8d085-135">Adorners receive input events just like any other <xref:System.Windows.FrameworkElement>.</span></span>  <span data-ttu-id="8d085-136">Parce qu’un adorant a toujours un z-ordre plus élevé que l’élément qu’il orne, l’adorant reçoit des événements d’entrée (tels <xref:System.Windows.UIElement.Drop> que ou <xref:System.Windows.UIElement.MouseMove>) qui peuvent être destinés à l’élément orné sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="8d085-136">Because an adorner always has a higher z-order than the element it adorns, the adorner receives input events (such as <xref:System.Windows.UIElement.Drop> or <xref:System.Windows.UIElement.MouseMove>) that may be intended for the underlying adorned element.</span></span>  <span data-ttu-id="8d085-137">Un ornement peut écouter certains événements d’entrée et les passer à l’élément orné sous-jacent en déclenchant à nouveau l’événement.</span><span class="sxs-lookup"><span data-stu-id="8d085-137">An adorner can listen for certain input events and pass these on to the underlying adorned element by re-raising the event.</span></span>

<span data-ttu-id="8d085-138">Pour permettre l’essai de frappe de passage des éléments <xref:System.Windows.UIElement.IsHitTestVisible%2A> sous un ornement, définissez la propriété d’essai de coup à **faux** sur l’adorant.</span><span class="sxs-lookup"><span data-stu-id="8d085-138">To enable pass-through hit testing of elements under an adorner, set the hit test <xref:System.Windows.UIElement.IsHitTestVisible%2A> property to **false** on the adorner.</span></span>  <span data-ttu-id="8d085-139">Pour plus d’informations sur les tests à succès, voir [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span><span class="sxs-lookup"><span data-stu-id="8d085-139">For more information about hit testing, see [Hit Testing in the Visual Layer](../graphics-multimedia/hit-testing-in-the-visual-layer.md).</span></span>

## <a name="adorning-a-single-uielement"></a><span data-ttu-id="8d085-140">Ornementation d’un UIElement unique</span><span class="sxs-lookup"><span data-stu-id="8d085-140">Adorning a Single UIElement</span></span>

<span data-ttu-id="8d085-141">Pour lier un adorant à un particulier, <xref:System.Windows.UIElement>suivez ces étapes:</span><span class="sxs-lookup"><span data-stu-id="8d085-141">To bind an adorner to a particular <xref:System.Windows.UIElement>, follow these steps:</span></span>

1. <span data-ttu-id="8d085-142">Appelez la <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> méthode statique <xref:System.Windows.Documents.AdornerLayer> pour <xref:System.Windows.UIElement> obtenir un objet pour que le soit orné.</span><span class="sxs-lookup"><span data-stu-id="8d085-142">Call the static method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to get an <xref:System.Windows.Documents.AdornerLayer> object for the <xref:System.Windows.UIElement> to be adorned.</span></span> <span data-ttu-id="8d085-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>marche vers le haut de <xref:System.Windows.UIElement>l’arbre visuel, commençant à la spécifiée, et renvoie la première couche d’ornement qu’il trouve.</span><span class="sxs-lookup"><span data-stu-id="8d085-143"><xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> walks up the visual tree, starting at the specified <xref:System.Windows.UIElement>, and returns the first adorner layer it finds.</span></span> <span data-ttu-id="8d085-144">(Si aucune couche d’ornement n’est trouvée, la méthode retourne Null.)</span><span class="sxs-lookup"><span data-stu-id="8d085-144">(If no adorner layers are found, the method returns null.)</span></span>

2. <span data-ttu-id="8d085-145">Appelez <xref:System.Windows.Documents.AdornerLayer.Add%2A> la méthode pour lier <xref:System.Windows.UIElement>l’adorant à la cible .</span><span class="sxs-lookup"><span data-stu-id="8d085-145">Call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind the adorner to the target <xref:System.Windows.UIElement>.</span></span>

 <span data-ttu-id="8d085-146">L’exemple suivant lie un SimpleCircleAdorner (voir ci-dessus) à un <xref:System.Windows.Controls.TextBox> *myTextBox*nommé :</span><span class="sxs-lookup"><span data-stu-id="8d085-146">The following example binds a SimpleCircleAdorner (shown above) to a <xref:System.Windows.Controls.TextBox> named *myTextBox*:</span></span>

 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]

> [!NOTE]
> <span data-ttu-id="8d085-147">L’utilisation du [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pour lier un ornement à un autre élément n’est pas prise en charge pour l’instant.</span><span class="sxs-lookup"><span data-stu-id="8d085-147">Using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to bind an adorner to another element is currently not supported.</span></span>

## <a name="adorning-the-children-of-a-panel"></a><span data-ttu-id="8d085-148">Ornementation des enfants d’un panneau</span><span class="sxs-lookup"><span data-stu-id="8d085-148">Adorning the Children of a Panel</span></span>

<span data-ttu-id="8d085-149">Pour lier un adorant <xref:System.Windows.Controls.Panel>aux enfants d’un , suivez ces étapes:</span><span class="sxs-lookup"><span data-stu-id="8d085-149">To bind an adorner to the children of a <xref:System.Windows.Controls.Panel>, follow these steps:</span></span>

1. <span data-ttu-id="8d085-150">Appelez `static` la <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> méthode pour trouver une couche d’ornement pour l’élément dont les enfants doivent être ornés.</span><span class="sxs-lookup"><span data-stu-id="8d085-150">Call the `static` method <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> to find an adorner layer for the element whose children are to be adorned.</span></span>

2. <span data-ttu-id="8d085-151">Énumérer à travers les enfants de <xref:System.Windows.Documents.AdornerLayer.Add%2A> l’élément parent et appeler la méthode pour lier un ornement à chaque élément enfant.</span><span class="sxs-lookup"><span data-stu-id="8d085-151">Enumerate through the children of the parent element and call the <xref:System.Windows.Documents.AdornerLayer.Add%2A> method to bind an adorner to each child element.</span></span>

<span data-ttu-id="8d085-152">L’exemple suivant lie un SimpleCircleAdorner (montré ci-dessus) aux enfants d’un <xref:System.Windows.Controls.StackPanel> *myStackPanel*nommé :</span><span class="sxs-lookup"><span data-stu-id="8d085-152">The following example binds a SimpleCircleAdorner (shown above) to the children of a <xref:System.Windows.Controls.StackPanel> named *myStackPanel*:</span></span>

[!code-csharp[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornchildren)]
[!code-vb[Adorners_SimpleCircleAdorner#_AdornChildren](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornchildren)]

## <a name="see-also"></a><span data-ttu-id="8d085-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8d085-153">See also</span></span>

- <xref:System.Windows.Media.AdornerHitTestResult>
- [<span data-ttu-id="8d085-154">Vue d’ensemble des formes et dessins de base dans WPF</span><span class="sxs-lookup"><span data-stu-id="8d085-154">Shapes and Basic Drawing in WPF Overview</span></span>](../graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="8d085-155">Peinture avec des images, des dessins et des objets visuels</span><span class="sxs-lookup"><span data-stu-id="8d085-155">Painting with Images, Drawings, and Visuals</span></span>](../graphics-multimedia/painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="8d085-156">Vue d'ensemble des objets Drawing</span><span class="sxs-lookup"><span data-stu-id="8d085-156">Drawing Objects Overview</span></span>](../graphics-multimedia/drawing-objects-overview.md)
- [<span data-ttu-id="8d085-157">Sujets comment se passer</span><span class="sxs-lookup"><span data-stu-id="8d085-157">How-to Topics</span></span>](adorners-how-to-topics.md)
