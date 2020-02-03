---
title: Collecter l’encre numérique
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
ms.openlocfilehash: 813a5313a6fbf83c36cdbed1f64ce69a217ad788
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747026"
---
# <a name="collect-ink"></a><span data-ttu-id="4d149-102">Collecter l’encre</span><span class="sxs-lookup"><span data-stu-id="4d149-102">Collect Ink</span></span>

<span data-ttu-id="4d149-103">La collecte d’encre numérique fait partie des principales fonctionnalités de la plateforme [Windows Presentation Foundation](../index.md).</span><span class="sxs-lookup"><span data-stu-id="4d149-103">The [Windows Presentation Foundation](../index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="4d149-104">Cette rubrique décrit les méthodes de collecte d’encre dans Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="4d149-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4d149-105">Composants requis</span><span class="sxs-lookup"><span data-stu-id="4d149-105">Prerequisites</span></span>

<span data-ttu-id="4d149-106">Pour utiliser les exemples suivants, vous devez d’abord installer Visual Studio et le SDK Windows.</span><span class="sxs-lookup"><span data-stu-id="4d149-106">To use the following examples, you must first install Visual Studio and the Windows SDK.</span></span> <span data-ttu-id="4d149-107">Vous devez également comprendre comment écrire des applications pour WPF.</span><span class="sxs-lookup"><span data-stu-id="4d149-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="4d149-108">Pour plus d’informations sur la prise en main de WPF, consultez [procédure pas à pas : ma première application de bureau WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="4d149-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="4d149-109">Utiliser l’élément InkCanvas</span><span class="sxs-lookup"><span data-stu-id="4d149-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="4d149-110">L’élément <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> offre le moyen le plus simple de collecter de l’encre dans WPF.</span><span class="sxs-lookup"><span data-stu-id="4d149-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="4d149-111">Utilisez un élément <xref:System.Windows.Controls.InkCanvas> pour recevoir et afficher l’entrée manuscrite.</span><span class="sxs-lookup"><span data-stu-id="4d149-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="4d149-112">Généralement, vous entrez de l’encre à l’aide d’un stylet qui interagit avec un digitaliseur pour produire des traits d’encre.</span><span class="sxs-lookup"><span data-stu-id="4d149-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="4d149-113">En outre, vous pouvez utiliser une souris à la place du stylet.</span><span class="sxs-lookup"><span data-stu-id="4d149-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="4d149-114">Les traits créés sont représentés en tant qu’objets <xref:System.Windows.Ink.Stroke>, et ils peuvent être manipulés à la fois par programmation et par entrée d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d149-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="4d149-115">Le <xref:System.Windows.Controls.InkCanvas> permet aux utilisateurs de sélectionner, modifier ou supprimer un <xref:System.Windows.Ink.Stroke>existant.</span><span class="sxs-lookup"><span data-stu-id="4d149-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="4d149-116">À l’aide de XAML, vous pouvez configurer la collecte manuscrite aussi facilement que l’ajout d’un élément **InkCanvas** à votre arborescence.</span><span class="sxs-lookup"><span data-stu-id="4d149-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="4d149-117">L’exemple suivant ajoute un <xref:System.Windows.Controls.InkCanvas> à un projet WPF par défaut créé dans Visual Studio :</span><span class="sxs-lookup"><span data-stu-id="4d149-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="4d149-118">L’élément **InkCanvas** peut également contenir des éléments enfants, ce qui permet d’ajouter des fonctionnalités d’annotation manuscrite à presque n’importe quel type d’élément XAML.</span><span class="sxs-lookup"><span data-stu-id="4d149-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="4d149-119">Par exemple, pour ajouter des fonctionnalités d’encrage à un élément de texte, il suffit d’en faire un enfant d’un <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="4d149-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="4d149-120">L’ajout de la prise en charge pour le marquage d’une image avec de l’encre est tout aussi simple :</span><span class="sxs-lookup"><span data-stu-id="4d149-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="4d149-121">Modes InkCollection</span><span class="sxs-lookup"><span data-stu-id="4d149-121">InkCollection Modes</span></span>

<span data-ttu-id="4d149-122">Le <xref:System.Windows.Controls.InkCanvas> fournit la prise en charge de différents modes d’entrée par le biais de sa propriété <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d149-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="4d149-123">Manipuler l’encre</span><span class="sxs-lookup"><span data-stu-id="4d149-123">Manipulate Ink</span></span>

<span data-ttu-id="4d149-124">Le <xref:System.Windows.Controls.InkCanvas> prend en charge de nombreuses opérations de modification de l’encre.</span><span class="sxs-lookup"><span data-stu-id="4d149-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="4d149-125">Par exemple, <xref:System.Windows.Controls.InkCanvas> prend en charge l’effacement du stylet, et aucun code supplémentaire n’est nécessaire pour ajouter la fonctionnalité à l’élément.</span><span class="sxs-lookup"><span data-stu-id="4d149-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="4d149-126">Sélection</span><span class="sxs-lookup"><span data-stu-id="4d149-126">Selection</span></span>

<span data-ttu-id="4d149-127">La définition du mode de sélection est aussi simple que la définition de la propriété <xref:System.Windows.Controls.InkCanvasEditingMode> sur **Select**.</span><span class="sxs-lookup"><span data-stu-id="4d149-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="4d149-128">Le code suivant définit le mode d’édition en fonction de la valeur d’une <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="4d149-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="4d149-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="4d149-129">DrawingAttributes</span></span>

<span data-ttu-id="4d149-130">Utilisez la propriété <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> pour modifier l’apparence des traits d’encre.</span><span class="sxs-lookup"><span data-stu-id="4d149-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="4d149-131">Par exemple, le membre <xref:System.Windows.Ink.DrawingAttributes.Color%2A> de <xref:System.Windows.Ink.DrawingAttributes> définit la couleur de la <xref:System.Windows.Ink.Stroke>rendue.</span><span class="sxs-lookup"><span data-stu-id="4d149-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="4d149-132">L’exemple suivant modifie la couleur des traits sélectionnés en rouge :</span><span class="sxs-lookup"><span data-stu-id="4d149-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="4d149-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="4d149-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="4d149-134">La propriété <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> permet d’accéder à des propriétés telles que la hauteur, la largeur et la couleur des traits à créer dans une <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="4d149-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="4d149-135">Une fois que vous modifiez la <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, tous les nouveaux traits entrés dans le <xref:System.Windows.Controls.InkCanvas> sont rendus avec les nouvelles valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="4d149-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="4d149-136">En plus de modifier le <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> dans le fichier code-behind, vous pouvez utiliser la syntaxe XAML pour spécifier les propriétés de <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d149-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="4d149-137">L’exemple suivant montre comment définir la propriété <xref:System.Windows.Ink.DrawingAttributes.Color%2A>.</span><span class="sxs-lookup"><span data-stu-id="4d149-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="4d149-138">Pour utiliser ce code, créez un projet WPF appelé « HelloInkCanvas » dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4d149-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="4d149-139">Remplacez le code du fichier *MainWindow. Xaml* par le code suivant :</span><span class="sxs-lookup"><span data-stu-id="4d149-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="4d149-140">Ensuite, ajoutez les gestionnaires d’événements de bouton suivants au fichier code-behind, à l’intérieur de la classe MainWindow :</span><span class="sxs-lookup"><span data-stu-id="4d149-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="4d149-141">Après avoir copié ce code, appuyez sur **F5** dans Visual Studio pour exécuter le programme dans le débogueur.</span><span class="sxs-lookup"><span data-stu-id="4d149-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="4d149-142">Notez que le <xref:System.Windows.Controls.StackPanel> place les boutons en haut du <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="4d149-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="4d149-143">Si vous essayez d’utiliser de l’encre en haut des boutons, le <xref:System.Windows.Controls.InkCanvas> collecte et restitue l’encre derrière les boutons.</span><span class="sxs-lookup"><span data-stu-id="4d149-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="4d149-144">Cela est dû au fait que les boutons sont frères de la <xref:System.Windows.Controls.InkCanvas>, par opposition aux enfants.</span><span class="sxs-lookup"><span data-stu-id="4d149-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="4d149-145">De même, les boutons sont plus haut dans l’ordre de plan ; l’encre est donc restituée derrière eux.</span><span class="sxs-lookup"><span data-stu-id="4d149-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d149-146">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d149-146">See also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
