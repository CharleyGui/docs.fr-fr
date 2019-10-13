---
title: Vue d'ensemble de l'utilisation de la disposition automatique
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 2fe473da3eeabef3852e3003e61b3b9604332855
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291272"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="713ae-102">Vue d'ensemble de l'utilisation de la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="713ae-102">Use Automatic Layout Overview</span></span>

<span data-ttu-id="713ae-103">Cette rubrique présente les instructions permettant aux développeurs d’écrire des applications [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] avec des interfaces utilisateur localisables.</span><span class="sxs-lookup"><span data-stu-id="713ae-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable user interfaces (UIs).</span></span> <span data-ttu-id="713ae-104">Dans le passé, la localisation d’une interface utilisateur était un processus fastidieux.</span><span class="sxs-lookup"><span data-stu-id="713ae-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="713ae-105">Chaque langue pour laquelle l’interface utilisateur a été adaptée a nécessité un réglage pixel par pixel.</span><span class="sxs-lookup"><span data-stu-id="713ae-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="713ae-106">Aujourd’hui, avec les normes de conception et de codage appropriées, les interfaces utilisateur peuvent être créées afin que les localiseurs aient moins de redimensionnement et de repositionnement.</span><span class="sxs-lookup"><span data-stu-id="713ae-106">Today with the right design and right coding standards, UIs can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="713ae-107">L’approche consistant à écrire des applications qui peuvent être plus facilement redimensionnées et repositionnées est appelée disposition automatique et peut être obtenue à l’aide de la conception d’application [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="713ae-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="713ae-108">Avantages de l’utilisation de la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="713ae-108">Advantages of Using Automatic Layout</span></span>

<span data-ttu-id="713ae-109">Étant donné que le système de présentation [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] est puissant et flexible, il offre la possibilité de mettre en forme les éléments d’une application qui peuvent être ajustés en fonction des besoins des différentes langues.</span><span class="sxs-lookup"><span data-stu-id="713ae-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="713ae-110">La liste suivante souligne quelques-uns des avantages de la disposition automatique.</span><span class="sxs-lookup"><span data-stu-id="713ae-110">The following list points out some of the advantages of automatic layout.</span></span>

- <span data-ttu-id="713ae-111">L’interface utilisateur s’affiche correctement dans n’importe quelle langue.</span><span class="sxs-lookup"><span data-stu-id="713ae-111">UI displays well  in any language.</span></span>

- <span data-ttu-id="713ae-112">Réduit le besoin de réajuster la position et la taille des contrôles une fois le texte traduit.</span><span class="sxs-lookup"><span data-stu-id="713ae-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>

- <span data-ttu-id="713ae-113">Réduit le besoin de réajuster la taille de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="713ae-113">Reduces the need to readjust window size.</span></span>

- <span data-ttu-id="713ae-114">La disposition de l’interface utilisateur s’affiche correctement dans n’importe quelle langue.</span><span class="sxs-lookup"><span data-stu-id="713ae-114">UI layout renders properly in any language.</span></span>

- <span data-ttu-id="713ae-115">La localisation peut se trouver réduite à sa plus simple expression, à savoir la traduction d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="713ae-115">Localization can be reduced to the point that it is little more than string translation.</span></span>

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a><span data-ttu-id="713ae-116">Disposition automatique et contrôles</span><span class="sxs-lookup"><span data-stu-id="713ae-116">Automatic Layout and Controls</span></span>

<span data-ttu-id="713ae-117">La disposition automatique permet à une application d’ajuster automatiquement la taille d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="713ae-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="713ae-118">Par exemple, un contrôle peut changer pour accommoder la longueur d’une chaîne.</span><span class="sxs-lookup"><span data-stu-id="713ae-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="713ae-119">Cette fonctionnalité permet aux responsables de la localisation de traduire la chaîne sans devoir redimensionner le contrôle pour que le texte traduit s’ajuste.</span><span class="sxs-lookup"><span data-stu-id="713ae-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="713ae-120">L’exemple suivant crée un bouton avec un contenu en anglais.</span><span class="sxs-lookup"><span data-stu-id="713ae-120">The following example creates a button with English content.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

<span data-ttu-id="713ae-121">Dans l’exemple, il vous suffit de changer le texte pour que le bouton soit en espagnol.</span><span class="sxs-lookup"><span data-stu-id="713ae-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="713ae-122">Par exemple :</span><span class="sxs-lookup"><span data-stu-id="713ae-122">For example,</span></span>

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

<span data-ttu-id="713ae-123">Le graphique suivant montre la sortie des exemples de code :</span><span class="sxs-lookup"><span data-stu-id="713ae-123">The following graphic shows the output of the code samples:</span></span>

![Même bouton avec le texte dans différentes langues](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="713ae-125">Disposition automatique et normes de codage</span><span class="sxs-lookup"><span data-stu-id="713ae-125">Automatic Layout and Coding Standards</span></span>

<span data-ttu-id="713ae-126">L’utilisation de l’approche de mise en page automatique requiert un ensemble de règles et de normes de codage et de conception pour produire une interface utilisateur entièrement localisable.</span><span class="sxs-lookup"><span data-stu-id="713ae-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="713ae-127">Les indications suivantes vont simplifier le codage de votre disposition automatique.</span><span class="sxs-lookup"><span data-stu-id="713ae-127">The following guidelines will aid your automatic layout coding.</span></span>

<span data-ttu-id="713ae-128">**N’utilisez pas de positions absolues**</span><span class="sxs-lookup"><span data-stu-id="713ae-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="713ae-129">N’utilisez pas <xref:System.Windows.Controls.Canvas>, car il positionne les éléments de manière absolue.</span><span class="sxs-lookup"><span data-stu-id="713ae-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="713ae-130">Utilisez <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> et <xref:System.Windows.Controls.Grid> pour positionner les contrôles.</span><span class="sxs-lookup"><span data-stu-id="713ae-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="713ae-131">Pour plus d’informations sur les différents types de panneaux, consultez [vue d’ensemble des panneaux](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="713ae-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="713ae-132">**Ne pas définir une taille fixe pour une fenêtre**</span><span class="sxs-lookup"><span data-stu-id="713ae-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="713ae-133">Utilisez <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="713ae-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="713ae-134">Exemple :</span><span class="sxs-lookup"><span data-stu-id="713ae-134">For example:</span></span>

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="713ae-135">**Ajouter un <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="713ae-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="713ae-136">Ajoutez un <xref:System.Windows.FrameworkElement.FlowDirection%2A> à l’élément racine de votre application.</span><span class="sxs-lookup"><span data-stu-id="713ae-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

  <span data-ttu-id="713ae-137">WPF offre un moyen pratique de prendre en charge les dispositions horizontales, bidirectionnelles et verticales.</span><span class="sxs-lookup"><span data-stu-id="713ae-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="713ae-138">Dans Presentation Framework, la propriété <xref:System.Windows.FrameworkElement.FlowDirection%2A> peut être utilisée pour définir la disposition.</span><span class="sxs-lookup"><span data-stu-id="713ae-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="713ae-139">Les modèles de sens du déroulement sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="713ae-139">The flow-direction patterns are:</span></span>

  - <span data-ttu-id="713ae-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) : disposition horizontale pour le latin, Asie de l’est, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="713ae-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>

  - <span data-ttu-id="713ae-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) : bidirectionnel pour l’arabe, l’hébreu, etc.</span><span class="sxs-lookup"><span data-stu-id="713ae-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="713ae-142">**Utiliser des polices composites à la place des polices physiques**</span><span class="sxs-lookup"><span data-stu-id="713ae-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="713ae-143">Avec les polices composites, la propriété <xref:System.Windows.Controls.Control.FontFamily%2A> n’a pas besoin d’être localisée.</span><span class="sxs-lookup"><span data-stu-id="713ae-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="713ae-144">Les développeurs peuvent utiliser l’une des polices suivantes ou créer la leur.</span><span class="sxs-lookup"><span data-stu-id="713ae-144">Developers can use one of the following fonts or create their own.</span></span>

  - <span data-ttu-id="713ae-145">Interface utilisateur globale</span><span class="sxs-lookup"><span data-stu-id="713ae-145">Global User Interface</span></span>
  - <span data-ttu-id="713ae-146">Sans Serif global</span><span class="sxs-lookup"><span data-stu-id="713ae-146">Global San Serif</span></span>
  - <span data-ttu-id="713ae-147">Serif global</span><span class="sxs-lookup"><span data-stu-id="713ae-147">Global Serif</span></span>

<span data-ttu-id="713ae-148">**Ajouter XML : lang**</span><span class="sxs-lookup"><span data-stu-id="713ae-148">**Add xml:lang**</span></span>

- <span data-ttu-id="713ae-149">Ajoutez l’attribut `xml:lang` dans l’élément racine de votre interface utilisateur, tel que `xml:lang="en-US"` pour une application en anglais.</span><span class="sxs-lookup"><span data-stu-id="713ae-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="713ae-150">Étant donné que les polices composites utilisent `xml:lang` pour déterminer la police à utiliser, définissez cette propriété pour prendre en charge les scénarios multilingues.</span><span class="sxs-lookup"><span data-stu-id="713ae-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a><span data-ttu-id="713ae-151">Disposition automatique et grilles</span><span class="sxs-lookup"><span data-stu-id="713ae-151">Automatic Layout and Grids</span></span>

<span data-ttu-id="713ae-152">L’élément <xref:System.Windows.Controls.Grid>, est utile pour la disposition automatique, car il permet à un développeur de positionner des éléments.</span><span class="sxs-lookup"><span data-stu-id="713ae-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="713ae-153">Un contrôle <xref:System.Windows.Controls.Grid> est en charge de la distribution de l’espace disponible parmi ses éléments enfants, à l’aide d’une disposition de colonne et de ligne.</span><span class="sxs-lookup"><span data-stu-id="713ae-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="713ae-154">Les éléments d’interface utilisateur peuvent s’étendre sur plusieurs cellules et il est possible d’avoir des grilles dans des grilles.</span><span class="sxs-lookup"><span data-stu-id="713ae-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="713ae-155">Les grilles sont utiles car elles vous permettent de créer et de positionner une interface utilisateur complexe.</span><span class="sxs-lookup"><span data-stu-id="713ae-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="713ae-156">L’exemple suivant illustre l’utilisation d’une grille pour positionner des boutons et du texte.</span><span class="sxs-lookup"><span data-stu-id="713ae-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="713ae-157">Notez que la hauteur et la largeur des cellules sont définies sur <xref:System.Windows.GridUnitType.Auto> ; par conséquent, la cellule qui contient le bouton avec une image s’ajuste pour correspondre à l’image.</span><span class="sxs-lookup"><span data-stu-id="713ae-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

<span data-ttu-id="713ae-158">Le graphique suivant montre la grille produite par le code précédent.</span><span class="sxs-lookup"><span data-stu-id="713ae-158">The following graphic shows the grid produced by the previous code.</span></span>

<span data-ttu-id="713ae-159">Grille ![exemple]de grille(./media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="713ae-159">![Grid example](./media/glob-grid.png "glob_grid") Grid</span></span>

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="713ae-160">Disposition automatique et grilles avec la propriété IsSharedSizeScope</span><span class="sxs-lookup"><span data-stu-id="713ae-160">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>

<span data-ttu-id="713ae-161">Un élément <xref:System.Windows.Controls.Grid> est utile dans les applications localisables pour créer des contrôles qui s’ajustent pour s’adapter au contenu.</span><span class="sxs-lookup"><span data-stu-id="713ae-161">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="713ae-162">Cependant, il peut parfois être nécessaire que les contrôles conservent une taille particulière quel que soit le contenu.</span><span class="sxs-lookup"><span data-stu-id="713ae-162">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="713ae-163">Par exemple, pour les boutons « OK », « Annuler » et « Parcourir », vous n’avez probablement pas besoin que les boutons s’adaptent à la taille du contenu.</span><span class="sxs-lookup"><span data-stu-id="713ae-163">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="713ae-164">Dans ce cas, la propriété jointe <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> est utile pour partager le même dimensionnement entre plusieurs éléments de grille.</span><span class="sxs-lookup"><span data-stu-id="713ae-164">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="713ae-165">L’exemple suivant montre comment partager des données de dimensionnement de colonne et de ligne entre plusieurs éléments <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="713ae-165">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> <span data-ttu-id="713ae-166">Pour obtenir l’exemple de code complet, consultez [partager des propriétés de dimensionnement entre grilles](../controls/how-to-share-sizing-properties-between-grids.md).</span><span class="sxs-lookup"><span data-stu-id="713ae-166">For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="713ae-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="713ae-167">See also</span></span>

- [<span data-ttu-id="713ae-168">Globalisation pour WPF</span><span class="sxs-lookup"><span data-stu-id="713ae-168">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="713ae-169">Utiliser la disposition automatique pour créer un bouton</span><span class="sxs-lookup"><span data-stu-id="713ae-169">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="713ae-170">Utiliser une grille pour la disposition automatique</span><span class="sxs-lookup"><span data-stu-id="713ae-170">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
