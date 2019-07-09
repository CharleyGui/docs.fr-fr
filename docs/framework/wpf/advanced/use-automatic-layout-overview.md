---
title: Vue d'ensemble de l'utilisation de la disposition automatique
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: d4a0fd819d08fdd936dd1ef35e8cd8c00947f9e0
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662686"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="e955e-102">Vue d'ensemble de l'utilisation de la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="e955e-102">Use Automatic Layout Overview</span></span>

<span data-ttu-id="e955e-103">Cette rubrique présente des instructions pour les développeurs sur la façon d’écrire [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications localisables [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e955e-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="e955e-104">Dans le passé, la localisation d’une interface utilisateur a été beaucoup de temps.</span><span class="sxs-lookup"><span data-stu-id="e955e-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="e955e-105">Chaque langue de l’interface utilisateur était adaptée nécessitait un réglage de pixel par pixel.</span><span class="sxs-lookup"><span data-stu-id="e955e-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="e955e-106">Aujourd'hui, grâce à la conception et des normes de codage, de droite [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] peut être construite afin que les traducteurs aient moins de redimensionnement et de repositionnement.</span><span class="sxs-lookup"><span data-stu-id="e955e-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="e955e-107">L’approche à écrire des applications qui peuvent être plus facilement redimensionnées et repositionnées est appelée à la disposition automatique et peut être obtenue en utilisant [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] design de l’application.</span><span class="sxs-lookup"><span data-stu-id="e955e-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="e955e-108">Avantages de l’utilisation de la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="e955e-108">Advantages of Using Automatic Layout</span></span>

<span data-ttu-id="e955e-109">Étant donné que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] système de présentation est puissant et flexible, il fournit la possibilité de disposer des éléments dans une application qui peuvent être ajustés pour répondre aux exigences des différentes langues.</span><span class="sxs-lookup"><span data-stu-id="e955e-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="e955e-110">La liste suivante souligne quelques-uns des avantages de la disposition automatique.</span><span class="sxs-lookup"><span data-stu-id="e955e-110">The following list points out some of the advantages of automatic layout.</span></span>

- <span data-ttu-id="e955e-111">L’interface utilisateur s’affiche correctement dans n’importe quel langage.</span><span class="sxs-lookup"><span data-stu-id="e955e-111">UI displays well  in any language.</span></span>

- <span data-ttu-id="e955e-112">Réduit le besoin de réajuster la position et la taille des contrôles une fois le texte traduit.</span><span class="sxs-lookup"><span data-stu-id="e955e-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>

- <span data-ttu-id="e955e-113">Réduit le besoin de réajuster la taille de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="e955e-113">Reduces the need to readjust window size.</span></span>

- <span data-ttu-id="e955e-114">Disposition de l’interface utilisateur s’affiche correctement dans n’importe quel langage.</span><span class="sxs-lookup"><span data-stu-id="e955e-114">UI layout renders properly in any language.</span></span>

- <span data-ttu-id="e955e-115">La localisation peut se trouver réduite à sa plus simple expression, à savoir la traduction d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e955e-115">Localization can be reduced to the point that it is little more than string translation.</span></span>

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a><span data-ttu-id="e955e-116">Disposition automatique et contrôles</span><span class="sxs-lookup"><span data-stu-id="e955e-116">Automatic Layout and Controls</span></span>

<span data-ttu-id="e955e-117">La disposition automatique permet à une application d’ajuster automatiquement la taille d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="e955e-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="e955e-118">Par exemple, un contrôle peut changer pour accommoder la longueur d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="e955e-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="e955e-119">Cette fonctionnalité permet aux responsables de la localisation de traduire la chaîne sans devoir redimensionner le contrôle pour que le texte traduit s’ajuste.</span><span class="sxs-lookup"><span data-stu-id="e955e-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="e955e-120">L’exemple suivant crée un bouton avec un contenu en anglais.</span><span class="sxs-lookup"><span data-stu-id="e955e-120">The following example creates a button with English content.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

<span data-ttu-id="e955e-121">Dans l’exemple, il vous suffit de changer le texte pour que le bouton soit en espagnol.</span><span class="sxs-lookup"><span data-stu-id="e955e-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="e955e-122">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e955e-122">For example,</span></span>

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

<span data-ttu-id="e955e-123">Le graphique suivant illustre la sortie des exemples de code :</span><span class="sxs-lookup"><span data-stu-id="e955e-123">The following graphic shows the output of the code samples:</span></span>

![Même bouton avec le texte dans différentes langues](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="e955e-125">Disposition automatique et normes de codage</span><span class="sxs-lookup"><span data-stu-id="e955e-125">Automatic Layout and Coding Standards</span></span>

<span data-ttu-id="e955e-126">À l’aide de l’approche de la disposition automatique nécessite un ensemble de codage et de normes de conception et de règles pour créer une interface utilisateur entièrement localisable.</span><span class="sxs-lookup"><span data-stu-id="e955e-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="e955e-127">Les indications suivantes vont simplifier le codage de votre disposition automatique.</span><span class="sxs-lookup"><span data-stu-id="e955e-127">The following guidelines will aid your automatic layout coding.</span></span>

<span data-ttu-id="e955e-128">**N’utilisez pas de positions absolues**</span><span class="sxs-lookup"><span data-stu-id="e955e-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="e955e-129">N’utilisez pas <xref:System.Windows.Controls.Canvas> , car il positionne les éléments absolument.</span><span class="sxs-lookup"><span data-stu-id="e955e-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="e955e-130">Utilisez <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, et <xref:System.Windows.Controls.Grid> pour positionner les contrôles.</span><span class="sxs-lookup"><span data-stu-id="e955e-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="e955e-131">Pour une discussion sur divers types de panneaux, consultez [vue d’ensemble de panneaux](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e955e-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="e955e-132">**Ne définissez pas une taille fixe pour une fenêtre**</span><span class="sxs-lookup"><span data-stu-id="e955e-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="e955e-133">Utilisez <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e955e-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e955e-134">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="e955e-134">For example:</span></span>

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="e955e-135">**Ajouter un <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="e955e-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="e955e-136">Ajouter un <xref:System.Windows.FrameworkElement.FlowDirection%2A> à l’élément racine de votre application.</span><span class="sxs-lookup"><span data-stu-id="e955e-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

  <span data-ttu-id="e955e-137">WPF fournit un moyen pratique pour prendre en charge horizontales, bidirectionnelles et des dispositions verticales.</span><span class="sxs-lookup"><span data-stu-id="e955e-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="e955e-138">Dans l’infrastructure de présentation, le <xref:System.Windows.FrameworkElement.FlowDirection%2A> propriété peut être utilisée pour définir la disposition.</span><span class="sxs-lookup"><span data-stu-id="e955e-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="e955e-139">Les modèles de sens du déroulement sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="e955e-139">The flow-direction patterns are:</span></span>

  - <span data-ttu-id="e955e-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) : disposition horizontale pour le Latin, Asie de l’est et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e955e-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>

  - <span data-ttu-id="e955e-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectionnelle pour l’arabe, hébreu et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e955e-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="e955e-142">**Utiliser des polices composites au lieu des polices physiques**</span><span class="sxs-lookup"><span data-stu-id="e955e-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="e955e-143">Avec les polices composites, le <xref:System.Windows.Controls.Control.FontFamily%2A> propriété ne doit pas être localisé.</span><span class="sxs-lookup"><span data-stu-id="e955e-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="e955e-144">Les développeurs peuvent utiliser l’une des polices suivantes ou créer la leur.</span><span class="sxs-lookup"><span data-stu-id="e955e-144">Developers can use one of the following fonts or create their own.</span></span>

  - <span data-ttu-id="e955e-145">Interface utilisateur globale</span><span class="sxs-lookup"><span data-stu-id="e955e-145">Global User Interface</span></span>
  - <span data-ttu-id="e955e-146">Sans Serif global</span><span class="sxs-lookup"><span data-stu-id="e955e-146">Global San Serif</span></span>
  - <span data-ttu-id="e955e-147">Serif global</span><span class="sxs-lookup"><span data-stu-id="e955e-147">Global Serif</span></span>

<span data-ttu-id="e955e-148">**Ajouter XML : lang**</span><span class="sxs-lookup"><span data-stu-id="e955e-148">**Add xml:lang**</span></span>

- <span data-ttu-id="e955e-149">Ajouter le `xml:lang` attribut dans l’élément racine de votre interface utilisateur, tel que `xml:lang="en-US"` pour une application en anglais.</span><span class="sxs-lookup"><span data-stu-id="e955e-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="e955e-150">Étant donné que les polices composites utilisent `xml:lang` pour déterminer la police à utiliser, définissez cette propriété pour prendre en charge les scénarios multilingues.</span><span class="sxs-lookup"><span data-stu-id="e955e-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a><span data-ttu-id="e955e-151">Disposition automatique et grilles</span><span class="sxs-lookup"><span data-stu-id="e955e-151">Automatic Layout and Grids</span></span>

<span data-ttu-id="e955e-152">Le <xref:System.Windows.Controls.Grid> élément, est utile pour la disposition automatique car il permet à un développeur positionner des éléments.</span><span class="sxs-lookup"><span data-stu-id="e955e-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="e955e-153">Un <xref:System.Windows.Controls.Grid> contrôle est capable de répartir l’espace disponible entre ses éléments enfants, à l’aide d’une disposition de ligne et de colonne.</span><span class="sxs-lookup"><span data-stu-id="e955e-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="e955e-154">Les éléments d’interface utilisateur peuvent s’étendre sur plusieurs cellules, et il est possible d’avoir des grilles imbriquées.</span><span class="sxs-lookup"><span data-stu-id="e955e-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="e955e-155">Les grilles sont utiles, car ils vous permettent de créer et de positionner une interface utilisateur complexe.</span><span class="sxs-lookup"><span data-stu-id="e955e-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="e955e-156">L’exemple suivant illustre l’utilisation d’une grille pour positionner des boutons et du texte.</span><span class="sxs-lookup"><span data-stu-id="e955e-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="e955e-157">Notez que la hauteur et la largeur des cellules sont définies sur <xref:System.Windows.GridUnitType.Auto>; par conséquent, la cellule qui contient le bouton avec une image s’ajuste à l’image.</span><span class="sxs-lookup"><span data-stu-id="e955e-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

<span data-ttu-id="e955e-158">Le graphique suivant montre la grille produite par le code précédent.</span><span class="sxs-lookup"><span data-stu-id="e955e-158">The following graphic shows the grid produced by the previous code.</span></span>

<span data-ttu-id="e955e-159">![Exemple de grille](./media/glob-grid.png "glob_grid") grille</span><span class="sxs-lookup"><span data-stu-id="e955e-159">![Grid example](./media/glob-grid.png "glob_grid") Grid</span></span>

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="e955e-160">Disposition automatique et grilles avec la propriété IsSharedSizeScope</span><span class="sxs-lookup"><span data-stu-id="e955e-160">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>

<span data-ttu-id="e955e-161">Un <xref:System.Windows.Controls.Grid> élément est utile dans des applications localisables pour créer des contrôles qui s’ajustent en fonction du contenu.</span><span class="sxs-lookup"><span data-stu-id="e955e-161">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="e955e-162">Cependant, il peut parfois être nécessaire que les contrôles conservent une taille particulière quel que soit le contenu.</span><span class="sxs-lookup"><span data-stu-id="e955e-162">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="e955e-163">Par exemple, pour les boutons « OK », « Annuler » et « Parcourir », vous n’avez probablement pas besoin que les boutons s’adaptent à la taille du contenu.</span><span class="sxs-lookup"><span data-stu-id="e955e-163">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="e955e-164">Dans ce cas le <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> propriété jointe est utile pour partager le même dimensionnement entre plusieurs éléments de grille.</span><span class="sxs-lookup"><span data-stu-id="e955e-164">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="e955e-165">L’exemple suivant montre comment partager des données entre plusieurs de dimensionnement de ligne et de colonne <xref:System.Windows.Controls.Grid> éléments.</span><span class="sxs-lookup"><span data-stu-id="e955e-165">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> <span data-ttu-id="e955e-166">Pour l’exemple de code complet, consultez [partage de propriétés de dimensionnement entre grilles](../controls/how-to-share-sizing-properties-between-grids.md)</span><span class="sxs-lookup"><span data-stu-id="e955e-166">For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md)</span></span>

## <a name="see-also"></a><span data-ttu-id="e955e-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e955e-167">See also</span></span>

- [<span data-ttu-id="e955e-168">Globalisation pour WPF</span><span class="sxs-lookup"><span data-stu-id="e955e-168">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="e955e-169">Utiliser la disposition automatique pour créer un bouton</span><span class="sxs-lookup"><span data-stu-id="e955e-169">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="e955e-170">Utiliser une grille pour la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="e955e-170">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
