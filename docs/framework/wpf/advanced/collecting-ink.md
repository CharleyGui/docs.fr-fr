---
title: Collecter l’encre dans les applications WPF
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
ms.openlocfilehash: d2178a4cbf888baaf0ae84b03b3d463b0de658b1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645733"
---
# <a name="collect-ink"></a><span data-ttu-id="dfa89-102">Collecter l’encre</span><span class="sxs-lookup"><span data-stu-id="dfa89-102">Collect Ink</span></span>

<span data-ttu-id="dfa89-103">La collecte d’encre numérique fait partie des principales fonctionnalités de la plateforme [Windows Presentation Foundation](../index.md).</span><span class="sxs-lookup"><span data-stu-id="dfa89-103">The [Windows Presentation Foundation](../index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="dfa89-104">Cette rubrique décrit les méthodes de collecte d’encre dans Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="dfa89-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dfa89-105">Prérequis</span><span class="sxs-lookup"><span data-stu-id="dfa89-105">Prerequisites</span></span>

<span data-ttu-id="dfa89-106">Pour utiliser les exemples suivants, vous devez d’abord installer Visual Studio et le [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dfa89-106">To use the following examples, you must first install Visual Studio and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="dfa89-107">Vous devez également comprendre comment écrire des applications pour le WPF.</span><span class="sxs-lookup"><span data-stu-id="dfa89-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="dfa89-108">Pour plus d’informations sur la mise en route avec WPF, consultez [procédure pas à pas : Ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="dfa89-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="dfa89-109">Utilisez l’élément InkCanvas</span><span class="sxs-lookup"><span data-stu-id="dfa89-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="dfa89-110">Le <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> élément fournit le moyen le plus simple pour collecter l’encre dans WPF.</span><span class="sxs-lookup"><span data-stu-id="dfa89-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="dfa89-111">Utilisez un <xref:System.Windows.Controls.InkCanvas> élément pour recevoir et afficher l’entrée d’encre.</span><span class="sxs-lookup"><span data-stu-id="dfa89-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="dfa89-112">Généralement, vous entrez de l’encre à l’aide d’un stylet qui interagit avec un digitaliseur pour produire des traits d’encre.</span><span class="sxs-lookup"><span data-stu-id="dfa89-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="dfa89-113">En outre, vous pouvez utiliser une souris à la place du stylet.</span><span class="sxs-lookup"><span data-stu-id="dfa89-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="dfa89-114">Les traits créés sont représentés en tant que <xref:System.Windows.Ink.Stroke> objets et ils peuvent être manipulés par programme et par l’utilisateur d’entrée.</span><span class="sxs-lookup"><span data-stu-id="dfa89-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="dfa89-115">Le <xref:System.Windows.Controls.InkCanvas> permet aux utilisateurs de sélectionner, modifier ou supprimer une existante <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="dfa89-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="dfa89-116">À l’aide de XAML, vous pouvez définir la collecte d’encre aussi facilement que l’ajout d’un **InkCanvas** élément à votre arborescence.</span><span class="sxs-lookup"><span data-stu-id="dfa89-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="dfa89-117">L’exemple suivant ajoute un <xref:System.Windows.Controls.InkCanvas> à un projet WPF par défaut créé dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="dfa89-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="dfa89-118">Le **InkCanvas** élément peut également contenir des éléments enfants, ce qui permet d’ajouter des fonctions d’annotation manuscrite à quasiment tout type d’élément XAML.</span><span class="sxs-lookup"><span data-stu-id="dfa89-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="dfa89-119">Par exemple, pour ajouter des fonctions d’encrage à un élément de texte, définissez-le simplement qu’un enfant d’un <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="dfa89-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="dfa89-120">Ajout de prise en charge pour baliser une image avec l’encre est tout aussi simple :</span><span class="sxs-lookup"><span data-stu-id="dfa89-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="dfa89-121">Modes InkCollection</span><span class="sxs-lookup"><span data-stu-id="dfa89-121">InkCollection Modes</span></span>

<span data-ttu-id="dfa89-122">Le <xref:System.Windows.Controls.InkCanvas> prend en charge de différents modes d’entrée via son <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="dfa89-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="dfa89-123">Manipuler l’encre</span><span class="sxs-lookup"><span data-stu-id="dfa89-123">Manipulate Ink</span></span>

<span data-ttu-id="dfa89-124">Le <xref:System.Windows.Controls.InkCanvas> prend en charge de nombreuses opérations de modification de l’encre.</span><span class="sxs-lookup"><span data-stu-id="dfa89-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="dfa89-125">Par exemple, <xref:System.Windows.Controls.InkCanvas> prend en charge back-la gomme du stylet, et aucun code supplémentaire n’est nécessaire pour ajouter les fonctionnalités à l’élément.</span><span class="sxs-lookup"><span data-stu-id="dfa89-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="dfa89-126">Sélection</span><span class="sxs-lookup"><span data-stu-id="dfa89-126">Selection</span></span>

<span data-ttu-id="dfa89-127">Définition du mode de sélection est aussi simple que le paramètre le <xref:System.Windows.Controls.InkCanvasEditingMode> propriété **sélectionnez**.</span><span class="sxs-lookup"><span data-stu-id="dfa89-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="dfa89-128">Le code suivant définit le mode d’édition basé sur la valeur d’un <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="dfa89-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="dfa89-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="dfa89-129">DrawingAttributes</span></span>

<span data-ttu-id="dfa89-130">Utilisez le <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> propriété à modifier l’apparence des traits d’encre.</span><span class="sxs-lookup"><span data-stu-id="dfa89-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="dfa89-131">Par exemple, le <xref:System.Windows.Ink.DrawingAttributes.Color%2A> membre <xref:System.Windows.Ink.DrawingAttributes> définit la couleur rendue <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="dfa89-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="dfa89-132">L’exemple suivant modifie la couleur des traits sélectionnés en rouge :</span><span class="sxs-lookup"><span data-stu-id="dfa89-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="dfa89-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="dfa89-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="dfa89-134">Le <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriété fournit l’accès aux propriétés telles que la hauteur, la largeur et la couleur des traits à créer dans un <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="dfa89-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="dfa89-135">Une fois que vous modifiez le <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, tous les futurs traits entrés dans le <xref:System.Windows.Controls.InkCanvas> sont restitués avec les nouvelles valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="dfa89-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="dfa89-136">En plus de modifier le <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> dans le fichier code-behind, vous pouvez utiliser la syntaxe XAML pour la spécification <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> propriétés.</span><span class="sxs-lookup"><span data-stu-id="dfa89-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="dfa89-137">L’exemple suivant montre comment définir le <xref:System.Windows.Ink.DrawingAttributes.Color%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="dfa89-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="dfa89-138">Pour utiliser ce code, créez un projet WPF intitulé « HelloInkCanvas » dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dfa89-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="dfa89-139">Remplacez le code dans le *MainWindow.xaml* fichier par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="dfa89-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="dfa89-140">Ensuite, ajoutez les gestionnaires d’événements de bouton suivant pour le fichier code-behind, à l’intérieur de la classe MainWindow :</span><span class="sxs-lookup"><span data-stu-id="dfa89-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="dfa89-141">Après avoir copié ce code, appuyez sur **F5** dans Visual Studio pour exécuter le programme dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="dfa89-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="dfa89-142">Notez comment la <xref:System.Windows.Controls.StackPanel> place les boutons en haut de la <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="dfa89-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="dfa89-143">Si vous tentez de l’encre en haut des boutons, le <xref:System.Windows.Controls.InkCanvas> collecte et restitue l’encre derrière les boutons.</span><span class="sxs-lookup"><span data-stu-id="dfa89-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="dfa89-144">Il s’agit, car les boutons sont des frères du <xref:System.Windows.Controls.InkCanvas> par opposition aux enfants.</span><span class="sxs-lookup"><span data-stu-id="dfa89-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="dfa89-145">De même, les boutons sont plus haut dans l’ordre de plan ; l’encre est donc restituée derrière eux.</span><span class="sxs-lookup"><span data-stu-id="dfa89-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="dfa89-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dfa89-146">See also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
