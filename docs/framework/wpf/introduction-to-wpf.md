---
title: Présentation de WPF
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b8d7cf43-d1f2-4f3d-adb0-4f3a6428edc0
dev_langs:
- csharp
- vb
ms.openlocfilehash: 511ea04a522804b4b2ea2ff173d6cdd738e5c7bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186222"
---
# <a name="wpf-overview"></a><span data-ttu-id="3e789-102">Vue d’ensemble de WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-102">WPF overview</span></span>

<span data-ttu-id="3e789-103">Windows Presentation Foundation (WPF) vous permet de créer des applications clientes de bureau pour Windows avec des expériences utilisateur visuellement surprenantes.</span><span class="sxs-lookup"><span data-stu-id="3e789-103">Windows Presentation Foundation (WPF) lets you create desktop client applications for Windows with visually stunning user experiences.</span></span>

![Exemple d'interface utilisateur Contoso Healthcare](media/introduction-to-wpf/wpfintrofigure24.png)

<span data-ttu-id="3e789-105">Le cœur de WPF est un moteur de rendu vectoriel et indépendant de toute résolution, créé pour tirer parti du matériel graphique moderne.</span><span class="sxs-lookup"><span data-stu-id="3e789-105">The core of WPF is a resolution-independent and vector-based rendering engine that is built to take advantage of modern graphics hardware.</span></span> <span data-ttu-id="3e789-106">WPF étend le cœur avec un ensemble complet de fonctionnalités de développement d’applications qui incluent XAML (Extensible Application Markup Language), des contrôles, la liaison de données, la disposition, les graphiques 2D et 3D, l’animation, des styles, des modèles, des documents, des médias, du texte et de la typographie.</span><span class="sxs-lookup"><span data-stu-id="3e789-106">WPF extends the core with a comprehensive set of application-development features that include Extensible Application Markup Language (XAML), controls, data binding, layout, 2D and 3D graphics, animation, styles, templates, documents, media, text, and typography.</span></span> <span data-ttu-id="3e789-107">WPF fait partie de .NET : vous pouvez donc créer des applications qui incorporent d’autres éléments de l’API .NET.</span><span class="sxs-lookup"><span data-stu-id="3e789-107">WPF is part of .NET, so you can build applications that incorporate other elements of the .NET API.</span></span>

<span data-ttu-id="3e789-108">Cette vue d’ensemble est destinée aux utilisateurs inexpérimentés ; elle couvre les fonctions et les concepts clés de WPF.</span><span class="sxs-lookup"><span data-stu-id="3e789-108">This overview is intended for newcomers and covers the key capabilities and concepts of WPF.</span></span>

## <a name="program-with-wpf"></a><span data-ttu-id="3e789-109">Programmer avec WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-109">Program with WPF</span></span>

<span data-ttu-id="3e789-110">WPF existe en tant que sous-ensemble de types .NET qui sont (pour la plupart d’entre eux) dans l’espace de noms <xref:System.Windows>.</span><span class="sxs-lookup"><span data-stu-id="3e789-110">WPF exists as a subset of .NET types that are (for the most part) located in the <xref:System.Windows> namespace.</span></span> <span data-ttu-id="3e789-111">Si vous avez déjà créé des applications avec .NET en utilisant des technologies managées comme ASP.NET et Windows Forms, l’expérience de programmation WPF doit vous sembler familière ; vous instanciez des classes, vous définissez des propriétés, vous appelez des méthodes et vous gérez des événements, en utilisant votre langage de programmation .NET préféré, comme C# ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e789-111">If you have previously built applications with .NET using managed technologies like ASP.NET and Windows Forms, the fundamental WPF programming experience should be familiar; you instantiate classes, set properties, call methods, and handle events, using your favorite .NET programming language, such as C# or Visual Basic.</span></span>

<span data-ttu-id="3e789-112">WPF inclut des constructions de programmation supplémentaires qui améliorent les propriétés et événements : les [propriétés de dépendance](advanced/dependency-properties-overview.md) et [événements routés](advanced/routed-events-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-112">WPF includes additional programming constructs that enhance properties and events: [dependency properties](advanced/dependency-properties-overview.md) and [routed events](advanced/routed-events-overview.md).</span></span>

## <a name="markup-and-code-behind"></a><span data-ttu-id="3e789-113">Balisage et code-behind</span><span class="sxs-lookup"><span data-stu-id="3e789-113">Markup and code-behind</span></span>

<span data-ttu-id="3e789-114">WPF vous permet de développer une application en utilisant à la fois le *balisage* et le *code-behind*, une expérience avec laquelle les développeurs ASP.NET sont censés être familiarisés.</span><span class="sxs-lookup"><span data-stu-id="3e789-114">WPF lets you develop an application using both *markup* and *code-behind*, an experience with which ASP.NET developers should be familiar.</span></span> <span data-ttu-id="3e789-115">Vous utilisez généralement le balisage XAML pour implémenter l’apparence d’une application et les langages de programmation managés (code-behind) pour implémenter son comportement.</span><span class="sxs-lookup"><span data-stu-id="3e789-115">You generally use XAML markup to implement the appearance of an application while using managed programming languages (code-behind) to implement its behavior.</span></span> <span data-ttu-id="3e789-116">Cette séparation de l’apparence et du comportement présente les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="3e789-116">This separation of appearance and behavior has the following benefits:</span></span>

- <span data-ttu-id="3e789-117">Les coûts de développement et de maintenance sont réduits, car le balisage spécifique à l’apparence n’est pas fortement couplé avec le code spécifique au comportement.</span><span class="sxs-lookup"><span data-stu-id="3e789-117">Development and maintenance costs are reduced because appearance-specific markup is not tightly coupled with behavior-specific code.</span></span>

- <span data-ttu-id="3e789-118">Le développement est plus efficace, car les concepteurs peuvent implémenter l’apparence d’une application en même temps que les développeurs qui implémentent le comportement de l’application.</span><span class="sxs-lookup"><span data-stu-id="3e789-118">Development is more efficient because designers can implement an application's appearance simultaneously with developers who are implementing the application's behavior.</span></span>

- <span data-ttu-id="3e789-119">La[globalisation et la localisation](advanced/wpf-globalization-and-localization-overview.md) des applications WPF sont simplifiées.</span><span class="sxs-lookup"><span data-stu-id="3e789-119">[Globalization and localization](advanced/wpf-globalization-and-localization-overview.md) for WPF applications is simplified.</span></span>

### <a name="markup"></a><span data-ttu-id="3e789-120">balisage</span><span class="sxs-lookup"><span data-stu-id="3e789-120">Markup</span></span>

<span data-ttu-id="3e789-121">XAML est un langage de balisage fondé sur XML qui implémente l’apparence d’une application de façon déclarative.</span><span class="sxs-lookup"><span data-stu-id="3e789-121">XAML is an XML-based markup language that implements an application's appearance declaratively.</span></span> <span data-ttu-id="3e789-122">Vous l’utilisez généralement pour créer des fenêtres, des boîtes de dialogue, des pages et des contrôles utilisateur, et pour les remplir avec des contrôles, des formes et des graphismes.</span><span class="sxs-lookup"><span data-stu-id="3e789-122">You typically use it to create windows, dialog boxes, pages, and user controls, and to fill them with controls, shapes, and graphics.</span></span>

<span data-ttu-id="3e789-123">L’exemple suivant utilise XAML pour implémenter l’apparence d’une fenêtre qui contient un seul bouton :</span><span class="sxs-lookup"><span data-stu-id="3e789-123">The following example uses XAML to implement the appearance of a window that contains a single button:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button">Click Me!</Button>

</Window>
```

<span data-ttu-id="3e789-124">Plus précisément, ce code XAML définit une fenêtre et un bouton à l’aide des éléments `Window` et `Button` , respectivement.</span><span class="sxs-lookup"><span data-stu-id="3e789-124">Specifically, this XAML defines a window and a button by using the `Window` and `Button` elements, respectively.</span></span> <span data-ttu-id="3e789-125">Chaque élément est configuré avec des attributs, tels que l’attribut `Window` de l’élément `Title` pour spécifier le texte de la barre de titre de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3e789-125">Each element is configured with attributes, such as the `Window` element's `Title` attribute to specify the window's title-bar text.</span></span> <span data-ttu-id="3e789-126">Pendant l’exécution, WPF convertit les éléments et les attributs définis dans le balisage en instances des classes WPF.</span><span class="sxs-lookup"><span data-stu-id="3e789-126">At run time, WPF converts the elements and attributes that are defined in markup to instances of WPF classes.</span></span> <span data-ttu-id="3e789-127">Par exemple, l’élément `Window` est converti en une instance de la classe <xref:System.Windows.Window> dont la propriété <xref:System.Windows.Window.Title%2A> est la valeur de l’attribut `Title` .</span><span class="sxs-lookup"><span data-stu-id="3e789-127">For example, the `Window` element is converted to an instance of the <xref:System.Windows.Window> class whose <xref:System.Windows.Window.Title%2A> property is the value of the `Title` attribute.</span></span>

<span data-ttu-id="3e789-128">Le chiffre suivant montre l’interface utilisateur (UI) qui est définie par le XAML dans l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="3e789-128">The following figure shows the user interface (UI) that is defined by the XAML in the previous example:</span></span>

![Fenêtre contenant un bouton](media/introduction-to-wpf/wpfintrofigure10.png)

<span data-ttu-id="3e789-130">Comme XAML est basé sur XML, l’interface utilisateur que vous composez avec est assemblée dans une hiérarchie d’éléments imbriqués, connue sous le nom d’ [arborescence des éléments](advanced/trees-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-130">Since XAML is XML-based, the UI that you compose with it is assembled in a hierarchy of nested elements known as an [element tree](advanced/trees-in-wpf.md).</span></span> <span data-ttu-id="3e789-131">L’arborescence des éléments offre un moyen logique et intuitif de créer et gérer des interfaces utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3e789-131">The element tree provides a logical and intuitive way to create and manage UIs.</span></span>

### <a name="code-behind"></a><span data-ttu-id="3e789-132">Code-behind</span><span class="sxs-lookup"><span data-stu-id="3e789-132">Code-behind</span></span>

<span data-ttu-id="3e789-133">Le comportement principal d’une application est d’implémenter les fonctionnalités qui répondent aux interventions de l’utilisateur, y compris la gestion des événements (par exemple, un clic sur un menu, une barre d’outils ou un bouton) et, en réponse, l’appel à la logique métier et à la logique d’accès aux données.</span><span class="sxs-lookup"><span data-stu-id="3e789-133">The main behavior of an application is to implement the functionality that responds to user interactions, including handling events (for example, clicking a menu, tool bar, or button) and calling business logic and data access logic in response.</span></span> <span data-ttu-id="3e789-134">Dans WPF, ce comportement est implémenté dans le code associé au balisage.</span><span class="sxs-lookup"><span data-stu-id="3e789-134">In WPF, this behavior is implemented in code that is associated with markup.</span></span> <span data-ttu-id="3e789-135">Ce type de code est appelé code-behind.</span><span class="sxs-lookup"><span data-stu-id="3e789-135">This type of code is known as code-behind.</span></span> <span data-ttu-id="3e789-136">L’exemple suivant montre la majoration mise à jour de l’exemple précédent et le code-derrière:</span><span class="sxs-lookup"><span data-stu-id="3e789-136">The following example shows the updated markup from the previous example and the code-behind:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.AWindow"
    Title="Window with Button"
    Width="250" Height="100">

  <!-- Add button to window -->
  <Button Name="button" Click="button_Click">Click Me!</Button>

</Window>
```

```csharp
using System.Windows; // Window, RoutedEventArgs, MessageBox

namespace SDKSample
{
    public partial class AWindow : Window
    {
        public AWindow()
        {
            // InitializeComponent call is required to merge the UI
            // that is defined in markup with this class, including  
            // setting properties and registering event handlers
            InitializeComponent();
        }

        void button_Click(object sender, RoutedEventArgs e)
        {
            // Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!");
        }
    }
}
```

```vb
Namespace SDKSample

    Partial Public Class AWindow
        Inherits System.Windows.Window

        Public Sub New()

            ' InitializeComponent call is required to merge the UI
            ' that is defined in markup with this class, including  
            ' setting properties and registering event handlers
            InitializeComponent()

        End Sub

        Private Sub button_Click(ByVal sender As Object, ByVal e As RoutedEventArgs)

            ' Show message box when button is clicked.
            MessageBox.Show("Hello, Windows Presentation Foundation!")

        End Sub

    End Class

End Namespace
```

<span data-ttu-id="3e789-137">Dans cet exemple, le code-behind implémente une classe qui dérive de la classe <xref:System.Windows.Window> .</span><span class="sxs-lookup"><span data-stu-id="3e789-137">In this example, the code-behind implements a class that derives from the <xref:System.Windows.Window> class.</span></span> <span data-ttu-id="3e789-138">L’attribut `x:Class` est utilisé pour associer le balisage à la classe code-behind.</span><span class="sxs-lookup"><span data-stu-id="3e789-138">The `x:Class` attribute is used to associate the markup with the code-behind class.</span></span> <span data-ttu-id="3e789-139">`InitializeComponent` est appelé depuis le constructeur de la classe code-behind pour fusionner l’interface utilisateur définie dans le balisage avec la classe code-behind.</span><span class="sxs-lookup"><span data-stu-id="3e789-139">`InitializeComponent` is called from the code-behind class's constructor to merge the UI that is defined in markup with the code-behind class.</span></span> <span data-ttu-id="3e789-140">(est`InitializeComponent` généré pour vous lorsque votre application est construite, c’est pourquoi vous n’avez pas besoin de l’implémenter manuellement.) La combinaison `x:Class` `InitializeComponent` et de s’assurer que votre implémentation est correctement paralésée chaque fois qu’elle est créée.</span><span class="sxs-lookup"><span data-stu-id="3e789-140">(`InitializeComponent` is generated for you when your application is built, which is why you don't need to implement it manually.) The combination of `x:Class` and `InitializeComponent` ensure that your implementation is correctly initialized whenever it is created.</span></span> <span data-ttu-id="3e789-141">La classe code-behind implémente également un gestionnaire d’événements pour l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> du bouton.</span><span class="sxs-lookup"><span data-stu-id="3e789-141">The code-behind class also implements an event handler for the button's <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event.</span></span> <span data-ttu-id="3e789-142">Quand vous cliquez sur le bouton, le gestionnaire d’événements affiche un message en appelant la méthode <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="3e789-142">When the button is clicked, the event handler shows a message box by calling the <xref:System.Windows.MessageBox.Show%2A?displayProperty=fullName> method.</span></span>

<span data-ttu-id="3e789-143">Le chiffre suivant indique le résultat lorsque le bouton est cliqué :</span><span class="sxs-lookup"><span data-stu-id="3e789-143">The following figure shows the result when the button is clicked:</span></span>

![MessageBox](media/introduction-to-wpf/wpfintrofigure25.png)

## <a name="controls"></a><span data-ttu-id="3e789-145">Commandes</span><span class="sxs-lookup"><span data-stu-id="3e789-145">Controls</span></span>

<span data-ttu-id="3e789-146">Les expériences utilisateur fournies par le modèle d’application sont des contrôles construits</span><span class="sxs-lookup"><span data-stu-id="3e789-146">The user experiences that are delivered by the application model are constructed controls.</span></span> <span data-ttu-id="3e789-147">Dans WPF, *contrôle* est un terme général qui s’applique à une catégorie de classes WPF qui sont hébergées dans une fenêtre ou une page, qui ont une interface utilisateur et qui implémentent un certain comportement.</span><span class="sxs-lookup"><span data-stu-id="3e789-147">In WPF, *control* is an umbrella term that applies to a category of WPF classes that are hosted in either a window or a page, have a user interface, and implement some behavior.</span></span>

<span data-ttu-id="3e789-148">Pour plus d’informations, consultez [Contrôles](controls/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-148">For more information, see [Controls](controls/index.md).</span></span>

### <a name="wpf-controls-by-function"></a><span data-ttu-id="3e789-149">Contrôles WPF par fonction</span><span class="sxs-lookup"><span data-stu-id="3e789-149">WPF controls by function</span></span>

<span data-ttu-id="3e789-150">Les contrôles WPF intégrés sont énumérés ici :</span><span class="sxs-lookup"><span data-stu-id="3e789-150">The built-in WPF controls are listed here:</span></span>

- <span data-ttu-id="3e789-151">**Boutons**: <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.RepeatButton>et .</span><span class="sxs-lookup"><span data-stu-id="3e789-151">**Buttons**: <xref:System.Windows.Controls.Button> and <xref:System.Windows.Controls.Primitives.RepeatButton>.</span></span>

- <span data-ttu-id="3e789-152">**Affichage**de <xref:System.Windows.Controls.DataGrid> <xref:System.Windows.Controls.ListView>données <xref:System.Windows.Controls.TreeView>: , , et .</span><span class="sxs-lookup"><span data-stu-id="3e789-152">**Data Display**: <xref:System.Windows.Controls.DataGrid>, <xref:System.Windows.Controls.ListView>, and <xref:System.Windows.Controls.TreeView>.</span></span>

- <span data-ttu-id="3e789-153">**Date Display**and <xref:System.Windows.Controls.Calendar> <xref:System.Windows.Controls.DatePicker>Selection : et .</span><span class="sxs-lookup"><span data-stu-id="3e789-153">**Date Display and Selection**: <xref:System.Windows.Controls.Calendar> and <xref:System.Windows.Controls.DatePicker>.</span></span>

- <span data-ttu-id="3e789-154">**Dialog**Boxes <xref:Microsoft.Win32.OpenFileDialog> <xref:System.Windows.Controls.PrintDialog>: <xref:Microsoft.Win32.SaveFileDialog>, , et .</span><span class="sxs-lookup"><span data-stu-id="3e789-154">**Dialog Boxes**: <xref:Microsoft.Win32.OpenFileDialog>, <xref:System.Windows.Controls.PrintDialog>, and <xref:Microsoft.Win32.SaveFileDialog>.</span></span>

- <span data-ttu-id="3e789-155">**Encre numérique** <xref:System.Windows.Controls.InkCanvas> : <xref:System.Windows.Controls.InkPresenter>et .</span><span class="sxs-lookup"><span data-stu-id="3e789-155">**Digital Ink**: <xref:System.Windows.Controls.InkCanvas> and <xref:System.Windows.Controls.InkPresenter>.</span></span>

- <span data-ttu-id="3e789-156">**Documents** <xref:System.Windows.Controls.DocumentViewer>: <xref:System.Windows.Controls.FlowDocumentPageViewer> <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, <xref:System.Windows.Controls.StickyNoteControl>, , et .</span><span class="sxs-lookup"><span data-stu-id="3e789-156">**Documents**: <xref:System.Windows.Controls.DocumentViewer>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentScrollViewer>, and <xref:System.Windows.Controls.StickyNoteControl>.</span></span>

- <span data-ttu-id="3e789-157">**Entrée** <xref:System.Windows.Controls.TextBox>: <xref:System.Windows.Controls.RichTextBox>, <xref:System.Windows.Controls.PasswordBox>, et .</span><span class="sxs-lookup"><span data-stu-id="3e789-157">**Input**: <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.RichTextBox>, and <xref:System.Windows.Controls.PasswordBox>.</span></span>

- <span data-ttu-id="3e789-158">**Mise** <xref:System.Windows.Controls.Border>en <xref:System.Windows.Controls.Primitives.BulletDecorator> <xref:System.Windows.Controls.Canvas>page <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.Expander>: <xref:System.Windows.Controls.Grid> <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter> <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator> <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer> <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb> <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel> <xref:System.Windows.Window>, <xref:System.Windows.Controls.WrapPanel>, , , , , , , , , , , , , , et .</span><span class="sxs-lookup"><span data-stu-id="3e789-158">**Layout**: <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Primitives.BulletDecorator>, <xref:System.Windows.Controls.Canvas>, <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.Expander>, <xref:System.Windows.Controls.Grid>, <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridSplitter>, <xref:System.Windows.Controls.GroupBox>, <xref:System.Windows.Controls.Panel>, <xref:System.Windows.Controls.Primitives.ResizeGrip>, <xref:System.Windows.Controls.Separator>, <xref:System.Windows.Controls.Primitives.ScrollBar>, <xref:System.Windows.Controls.ScrollViewer>, <xref:System.Windows.Controls.StackPanel>, <xref:System.Windows.Controls.Primitives.Thumb>, <xref:System.Windows.Controls.Viewbox>, <xref:System.Windows.Controls.VirtualizingStackPanel>, <xref:System.Windows.Window>, and <xref:System.Windows.Controls.WrapPanel>.</span></span>

- <span data-ttu-id="3e789-159">**Médias** <xref:System.Windows.Controls.Image>: <xref:System.Windows.Controls.MediaElement>, <xref:System.Windows.Controls.SoundPlayerAction>, et .</span><span class="sxs-lookup"><span data-stu-id="3e789-159">**Media**: <xref:System.Windows.Controls.Image>, <xref:System.Windows.Controls.MediaElement>, and <xref:System.Windows.Controls.SoundPlayerAction>.</span></span>

- <span data-ttu-id="3e789-160">**Menus** <xref:System.Windows.Controls.ContextMenu>: <xref:System.Windows.Controls.Menu>, <xref:System.Windows.Controls.ToolBar>, et .</span><span class="sxs-lookup"><span data-stu-id="3e789-160">**Menus**: <xref:System.Windows.Controls.ContextMenu>, <xref:System.Windows.Controls.Menu>, and <xref:System.Windows.Controls.ToolBar>.</span></span>

- <span data-ttu-id="3e789-161">**Navigation** <xref:System.Windows.Controls.Frame>: <xref:System.Windows.Documents.Hyperlink> <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.TabControl>, et .</span><span class="sxs-lookup"><span data-stu-id="3e789-161">**Navigation**: <xref:System.Windows.Controls.Frame>, <xref:System.Windows.Documents.Hyperlink>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Navigation.NavigationWindow>, and <xref:System.Windows.Controls.TabControl>.</span></span>

- <span data-ttu-id="3e789-162">**Sélection** <xref:System.Windows.Controls.CheckBox>: <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, <xref:System.Windows.Controls.Slider>, , et .</span><span class="sxs-lookup"><span data-stu-id="3e789-162">**Selection**: <xref:System.Windows.Controls.CheckBox>, <xref:System.Windows.Controls.ComboBox>, <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.RadioButton>, and <xref:System.Windows.Controls.Slider>.</span></span>

- <span data-ttu-id="3e789-163">**Informations**utilisateur <xref:System.Windows.Controls.AccessText> <xref:System.Windows.Controls.Label>: <xref:System.Windows.Controls.Primitives.Popup> <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar> <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.ToolTip>, , , , et .</span><span class="sxs-lookup"><span data-stu-id="3e789-163">**User Information**: <xref:System.Windows.Controls.AccessText>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Primitives.Popup>, <xref:System.Windows.Controls.ProgressBar>, <xref:System.Windows.Controls.Primitives.StatusBar>, <xref:System.Windows.Controls.TextBlock>, and <xref:System.Windows.Controls.ToolTip>.</span></span>

## <a name="input-and-commands"></a><span data-ttu-id="3e789-164">Entrée et commandes</span><span class="sxs-lookup"><span data-stu-id="3e789-164">Input and commands</span></span>

<span data-ttu-id="3e789-165">Les contrôles détectent le plus souvent l’entrée utilisateur et y répondent.</span><span class="sxs-lookup"><span data-stu-id="3e789-165">Controls most often detect and respond to user input.</span></span> <span data-ttu-id="3e789-166">Le [système d’entrée WPF](advanced/input-overview.md) utilise des événements directs et routés pour prendre en charge la saisie de texte, la gestion du focus et la position de la souris.</span><span class="sxs-lookup"><span data-stu-id="3e789-166">The [WPF input system](advanced/input-overview.md) uses both direct and routed events to support text input, focus management, and mouse positioning.</span></span>

<span data-ttu-id="3e789-167">Les applications ont souvent des spécifications d’entrée complexes.</span><span class="sxs-lookup"><span data-stu-id="3e789-167">Applications often have complex input requirements.</span></span> <span data-ttu-id="3e789-168">WPF fournit un [système de commande](advanced/commanding-overview.md) qui sépare les actions d’entrée utilisateur du code qui répond à ces actions.</span><span class="sxs-lookup"><span data-stu-id="3e789-168">WPF provides a [command system](advanced/commanding-overview.md) that separates user-input actions from the code that responds to those actions.</span></span>

## <a name="layout"></a><span data-ttu-id="3e789-169">Disposition</span><span class="sxs-lookup"><span data-stu-id="3e789-169">Layout</span></span>

<span data-ttu-id="3e789-170">Quand vous créez une interface utilisateur, réorganisez vos contrôles par emplacement et par taille pour former une disposition.</span><span class="sxs-lookup"><span data-stu-id="3e789-170">When you create a user interface, you arrange your controls by location and size to form a layout.</span></span> <span data-ttu-id="3e789-171">L’une des spécifications clés de toute disposition est de s’adapter aux modifications de la taille de la fenêtre et des paramètres d’affichage.</span><span class="sxs-lookup"><span data-stu-id="3e789-171">A key requirement of any layout is to adapt to changes in window size and display settings.</span></span> <span data-ttu-id="3e789-172">Plutôt que de vous forcer à écrire le code pour vous adapter à une disposition, WPF vous fournit un système de disposition extensible de première classe.</span><span class="sxs-lookup"><span data-stu-id="3e789-172">Rather than forcing you to write the code to adapt a layout in these circumstances, WPF provides a first-class, extensible layout system for you.</span></span>

<span data-ttu-id="3e789-173">Le positionnement relatif est l’élément essentiel du système de disposition. Il augmente la capacité d’adaptation aux modifications des conditions d’affichage et de disposition des fenêtres.</span><span class="sxs-lookup"><span data-stu-id="3e789-173">The cornerstone of the layout system is relative positioning, which increases the ability to adapt to changing window and display conditions.</span></span> <span data-ttu-id="3e789-174">De plus, le système de disposition gère la négociation entre les contrôles pour déterminer la disposition.</span><span class="sxs-lookup"><span data-stu-id="3e789-174">In addition, the layout system manages the negotiation between controls to determine the layout.</span></span> <span data-ttu-id="3e789-175">La négociation est un processus qui s’effectue en deux étapes : premièrement, un contrôle informe son parent de l’emplacement et de la taille dont il a besoin ; deuxièmement, le parent informe le contrôle de l’espace dont il peut disposer.</span><span class="sxs-lookup"><span data-stu-id="3e789-175">The negotiation is a two-step process: first, a control tells its parent what location and size it requires; second, the parent tells the control what space it can have.</span></span>

<span data-ttu-id="3e789-176">Le système de disposition est exposé aux contrôles enfants par des classes WPF de base.</span><span class="sxs-lookup"><span data-stu-id="3e789-176">The layout system is exposed to child controls through base WPF classes.</span></span> <span data-ttu-id="3e789-177">Pour des dispositions courantes telles que les grilles, l’empilement et l’ancrage, WPF comprend plusieurs contrôles de disposition :</span><span class="sxs-lookup"><span data-stu-id="3e789-177">For common layouts such as grids, stacking, and docking, WPF includes several layout controls:</span></span>

- <span data-ttu-id="3e789-178"><xref:System.Windows.Controls.Canvas>: les contrôles enfants fournissent leur propre disposition.</span><span class="sxs-lookup"><span data-stu-id="3e789-178"><xref:System.Windows.Controls.Canvas>: Child controls provide their own layout.</span></span>

- <span data-ttu-id="3e789-179"><xref:System.Windows.Controls.DockPanel>:  les contrôles enfants sont alignés aux bords du panneau.</span><span class="sxs-lookup"><span data-stu-id="3e789-179"><xref:System.Windows.Controls.DockPanel>: Child controls are aligned to the edges of the panel.</span></span>

- <span data-ttu-id="3e789-180"><xref:System.Windows.Controls.Grid>: les contrôles enfants sont positionnés en lignes et en colonnes.</span><span class="sxs-lookup"><span data-stu-id="3e789-180"><xref:System.Windows.Controls.Grid>: Child controls are positioned by rows and columns.</span></span>

- <span data-ttu-id="3e789-181"><xref:System.Windows.Controls.StackPanel>: les contrôles enfants sont empilés verticalement ou horizontalement.</span><span class="sxs-lookup"><span data-stu-id="3e789-181"><xref:System.Windows.Controls.StackPanel>: Child controls are stacked either vertically or horizontally.</span></span>

- <span data-ttu-id="3e789-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: les contrôles enfants sont virtualisés et réorganisés sur une seule ligne, verticale ou horizontale.</span><span class="sxs-lookup"><span data-stu-id="3e789-182"><xref:System.Windows.Controls.VirtualizingStackPanel>: Child controls are virtualized and arranged on a single line that is either horizontally or vertically oriented.</span></span>

- <span data-ttu-id="3e789-183"><xref:System.Windows.Controls.WrapPanel>: les contrôles enfants sont positionnés de gauche à droite et renvoyés à la ligne suivante lorsqu’il y a plus de contrôles sur la ligne actuelle que l’espace ne l’autorise.</span><span class="sxs-lookup"><span data-stu-id="3e789-183"><xref:System.Windows.Controls.WrapPanel>: Child controls are positioned in left-to-right order and wrapped to the next line when there are more controls on the current line than space allows.</span></span>

<span data-ttu-id="3e789-184">L’exemple suivant <xref:System.Windows.Controls.DockPanel> utilise un <xref:System.Windows.Controls.TextBox> pour exposer plusieurs contrôles :</span><span class="sxs-lookup"><span data-stu-id="3e789-184">The following example uses a <xref:System.Windows.Controls.DockPanel> to lay out several <xref:System.Windows.Controls.TextBox> controls:</span></span>

[!code-xaml[IntroToWPFSnippets#LayoutMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_1.xaml)]

<span data-ttu-id="3e789-185">Le <xref:System.Windows.Controls.DockPanel> autorise les contrôles <xref:System.Windows.Controls.TextBox> enfants à lui dire comment les réorganiser.</span><span class="sxs-lookup"><span data-stu-id="3e789-185">The <xref:System.Windows.Controls.DockPanel> allows the child <xref:System.Windows.Controls.TextBox> controls to tell it how to arrange them.</span></span> <span data-ttu-id="3e789-186">Pour cela, le <xref:System.Windows.Controls.DockPanel> implémente une propriété jointe `Dock` exposée aux contrôles enfants pour permettre à chacun d’eux de spécifier un style d’ancrage.</span><span class="sxs-lookup"><span data-stu-id="3e789-186">To do this, the <xref:System.Windows.Controls.DockPanel> implements a `Dock` attached property that is exposed to the child controls to allow each of them to specify a dock style.</span></span>

> [!NOTE]
> <span data-ttu-id="3e789-187">Une propriété implémentée par un contrôle parent pour une utilisation par des contrôles enfants est une construction WPF appelée [propriété attachée](advanced/attached-properties-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-187">A property that's implemented by a parent control for use by child controls is a WPF construct called an [attached property](advanced/attached-properties-overview.md).</span></span>

<span data-ttu-id="3e789-188">Le chiffre suivant montre le résultat de la majoration XAML dans l’exemple précédent :</span><span class="sxs-lookup"><span data-stu-id="3e789-188">The following figure shows the result of the XAML markup in the preceding example:</span></span>

![Page DockPanel](media/introduction-to-wpf/wpfintrofigure11.png)

## <a name="data-binding"></a><span data-ttu-id="3e789-190">Liaison de données</span><span class="sxs-lookup"><span data-stu-id="3e789-190">Data binding</span></span>

<span data-ttu-id="3e789-191">La plupart des applications sont créées pour permettre aux utilisateurs d’afficher et de modifier des données.</span><span class="sxs-lookup"><span data-stu-id="3e789-191">Most applications are created to provide users with the means to view and edit data.</span></span> <span data-ttu-id="3e789-192">Pour les applications WPF, le travail de stockage et d’accès aux données est déjà fourni par des technologies telles que Microsoft SQL Server et ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="3e789-192">For WPF applications, the work of storing and accessing data is already provided for by technologies such as SQL Server and ADO .NET.</span></span> <span data-ttu-id="3e789-193">Après avoir accédé aux données et les avoir chargées dans les objets managés d’une application, les difficultés commencent pour les applications WPF.</span><span class="sxs-lookup"><span data-stu-id="3e789-193">After the data is accessed and loaded into an application's managed objects, the hard work for WPF applications begins.</span></span> <span data-ttu-id="3e789-194">Cela implique essentiellement deux opérations :</span><span class="sxs-lookup"><span data-stu-id="3e789-194">Essentially, this involves two things:</span></span>

1. <span data-ttu-id="3e789-195">La copie des données depuis les objets managés vers des contrôles, où les données pourront être affichées et modifiées.</span><span class="sxs-lookup"><span data-stu-id="3e789-195">Copying the data from the managed objects into controls, where the data can be displayed and edited.</span></span>

2. <span data-ttu-id="3e789-196">La garantie que les modifications apportées aux données à l’aide des contrôles sont recopiées vers les objets managés.</span><span class="sxs-lookup"><span data-stu-id="3e789-196">Ensuring that changes made to data by using controls are copied back to the managed objects.</span></span>

<span data-ttu-id="3e789-197">Pour simplifier le développement d’applications, WPF fournit un moteur de liaison de données pour effectuer automatiquement ces étapes.</span><span class="sxs-lookup"><span data-stu-id="3e789-197">To simplify application development, WPF provides a data binding engine to automatically perform these steps.</span></span> <span data-ttu-id="3e789-198">La principale unité du moteur de liaison de données est la classe <xref:System.Windows.Data.Binding> dont le rôle est de lier un contrôle (la cible de liaison) à un objet de données (la source de liaison).</span><span class="sxs-lookup"><span data-stu-id="3e789-198">The core unit of the data binding engine is the <xref:System.Windows.Data.Binding> class, whose job is to bind a control (the binding target) to a data object (the binding source).</span></span> <span data-ttu-id="3e789-199">Cette relation est illustrée par la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="3e789-199">This relationship is illustrated by the following figure:</span></span>

![Diagramme de liaison de données de base](media/introduction-to-wpf/databindingmostbasic.png)

<span data-ttu-id="3e789-201">L’exemple suivant montre comment lier une <xref:System.Windows.Controls.TextBox> à une instance d’un objet `Person` personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3e789-201">The next example demonstrates how to bind a <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object.</span></span> <span data-ttu-id="3e789-202">Le code suivant montre l’implémentation de `Person` :</span><span class="sxs-lookup"><span data-stu-id="3e789-202">The `Person` implementation is shown in the following code:</span></span>

[!code-vb[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_2.vb)]
[!code-csharp[SimpleDataBindingSnippets#PersonClassCODE](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_2.cs)]

<span data-ttu-id="3e789-203">La balisage suivante <xref:System.Windows.Controls.TextBox> lie l’exemple `Person` d’un objet personnalisé :</span><span class="sxs-lookup"><span data-stu-id="3e789-203">The following markup binds the <xref:System.Windows.Controls.TextBox> to an instance of a custom `Person` object:</span></span>

```xaml
 <Window
     xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
     xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
     x:Class="SDKSample.DataBindingWindow">

   <!-- Bind the TextBox to the data source (TextBox.Text to Person.Name) -->
   <TextBox Name="personNameTextBox" Text="{Binding Path=Name}" />

 </Window>
```

[!code-vb[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_6.vb)]
[!code-csharp[SimpleDataBindingSnippets#DataBindingCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_6.cs)]

<span data-ttu-id="3e789-204">Dans cet exemple, la classe `Person` est instanciée en code-behind et définie comme contexte de données de `DataBindingWindow`.</span><span class="sxs-lookup"><span data-stu-id="3e789-204">In this example, the `Person` class is instantiated in code-behind and is set as the data context for the `DataBindingWindow`.</span></span> <span data-ttu-id="3e789-205">Dans le balisage, la propriété <xref:System.Windows.Controls.TextBox.Text%2A> de la <xref:System.Windows.Controls.TextBox> est liée à la propriété `Person.Name` (à l’aide de la syntaxe XAML`{Binding ... }`).</span><span class="sxs-lookup"><span data-stu-id="3e789-205">In markup, the <xref:System.Windows.Controls.TextBox.Text%2A> property of the <xref:System.Windows.Controls.TextBox> is bound to the `Person.Name` property (using the "`{Binding ... }`" XAML syntax).</span></span> <span data-ttu-id="3e789-206">Ce code XAML demande à WPF de lier le contrôle <xref:System.Windows.Controls.TextBox> à l’objet `Person` stocké dans la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="3e789-206">This XAML tells WPF to bind the <xref:System.Windows.Controls.TextBox> control to the `Person` object that is stored in the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the window.</span></span>

<span data-ttu-id="3e789-207">Le moteur de liaison de données WPF fournit une prise en charge supplémentaire qui inclut la validation, le tri, le filtrage et le regroupement</span><span class="sxs-lookup"><span data-stu-id="3e789-207">The WPF data binding engine provides additional support that includes validation, sorting, filtering, and grouping.</span></span> <span data-ttu-id="3e789-208">En outre, la liaison de données prend en charge l’utilisation de modèles de données afin de créer une interface utilisateur personnalisée pour les données liées quand l’interface utilisateur affichée par les contrôles WPF standard n’est pas appropriée.</span><span class="sxs-lookup"><span data-stu-id="3e789-208">Furthermore, data binding supports the use of data templates to create custom user interface for bound data when the user interface displayed by the standard WPF controls is not appropriate.</span></span>

<span data-ttu-id="3e789-209">Pour plus d’informations, voir [Aperçu de la liaison des données](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-209">For more information, see [Data binding overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

## <a name="graphics"></a><span data-ttu-id="3e789-210">Graphiques</span><span class="sxs-lookup"><span data-stu-id="3e789-210">Graphics</span></span>

<span data-ttu-id="3e789-211">WPF présente un ensemble de fonctionnalités graphiques étendu, évolutif et flexible possédant les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="3e789-211">WPF introduces an extensive, scalable, and flexible set of graphics features that have the following benefits:</span></span>

- <span data-ttu-id="3e789-212">**Graphiques indépendants du périphérique et de toute résolution**.</span><span class="sxs-lookup"><span data-stu-id="3e789-212">**Resolution-independent and device-independent graphics**.</span></span> <span data-ttu-id="3e789-213">L’unité de mesure de base du système graphique WPF est le pixel indépendant du périphérique, soit 1/96ème de pouce, quelle que soit la résolution réelle de l’écran. Elle sert de base au rendu indépendant du périphérique et de la résolution.</span><span class="sxs-lookup"><span data-stu-id="3e789-213">The basic unit of measurement in the WPF graphics system is the device-independent pixel, which is 1/96th of an inch, regardless of actual screen resolution, and provides the foundation for resolution-independent and device-independent rendering.</span></span> <span data-ttu-id="3e789-214">Chaque pixel indépendant du périphérique est automatiquement mis à l’échelle pour correspondre au paramètre de points par pouce (ppp) du système de restitution.</span><span class="sxs-lookup"><span data-stu-id="3e789-214">Each device-independent pixel automatically scales to match the dots-per-inch (dpi) setting of the system it renders on.</span></span>

- <span data-ttu-id="3e789-215">**Précision améliorée**.</span><span class="sxs-lookup"><span data-stu-id="3e789-215">**Improved precision**.</span></span> <span data-ttu-id="3e789-216">Le système de coordonnées WPF est mesuré avec des nombres à virgule flottante double précision plutôt que simple précision.</span><span class="sxs-lookup"><span data-stu-id="3e789-216">The WPF coordinate system is measured with double-precision floating-point numbers rather than single-precision.</span></span> <span data-ttu-id="3e789-217">Les transformations et valeurs d’opacité sont également exprimées sous la forme de valeurs double précision.</span><span class="sxs-lookup"><span data-stu-id="3e789-217">Transformations and opacity values are also expressed as double-precision.</span></span> <span data-ttu-id="3e789-218">WPF prend également en charge une vaste gamme de couleurs (scRGB) et assure la prise en charge intégrée de la gestion des entrées issues de différents espaces de couleurs.</span><span class="sxs-lookup"><span data-stu-id="3e789-218">WPF also supports a wide color gamut (scRGB) and provides integrated support for managing inputs from different color spaces.</span></span>

- <span data-ttu-id="3e789-219">**Graphiques avancés et prise en charge de l’animation**.</span><span class="sxs-lookup"><span data-stu-id="3e789-219">**Advanced graphics and animation support**.</span></span> <span data-ttu-id="3e789-220">WPF simplifie la programmation graphique en gérant les scènes d’animation à votre place ; ainsi, vous n’avez pas besoin de vous préoccuper du traitement des scènes, du rendu des boucles ni de l’interpolation bilinéaire.</span><span class="sxs-lookup"><span data-stu-id="3e789-220">WPF simplifies graphics programming by managing animation scenes for you; there is no need to worry about scene processing, rendering loops, and bilinear interpolation.</span></span> <span data-ttu-id="3e789-221">En outre, WPF fournit une prise en charge du test de recherche et une prise en charge complète de la composition alpha.</span><span class="sxs-lookup"><span data-stu-id="3e789-221">Additionally, WPF provides hit-testing support and full alpha-compositing support.</span></span>

- <span data-ttu-id="3e789-222">**Accélération matérielle**.</span><span class="sxs-lookup"><span data-stu-id="3e789-222">**Hardware acceleration**.</span></span> <span data-ttu-id="3e789-223">Le système graphique WPF profite du matériel vidéo pour réduire l’utilisation du processeur.</span><span class="sxs-lookup"><span data-stu-id="3e789-223">The WPF graphics system takes advantage of graphics hardware to minimize CPU usage.</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="3e789-224">Formes 2D</span><span class="sxs-lookup"><span data-stu-id="3e789-224">2D shapes</span></span>

<span data-ttu-id="3e789-225">WPF fournit une bibliothèque de formes vectorielles 2D courantes, comme les rectangles et les ellipses présentés dans l’illustration suivante :</span><span class="sxs-lookup"><span data-stu-id="3e789-225">WPF provides a library of common vector-drawn 2D shapes, such as the rectangles and ellipses that are shown in the following illustration:</span></span>

![Ellipses et rectangles](media/introduction-to-wpf/wpfintrofigure4.PNG)

<span data-ttu-id="3e789-227">Les formes ont notamment pour intérêt de ne pas servir uniquement à l’affichage ; elles implémentent la majorité des fonctionnalités que vous attendez des contrôles, y compris l’entrée au clavier et à la souris.</span><span class="sxs-lookup"><span data-stu-id="3e789-227">An interesting capability of shapes is that they are not just for display; shapes implement many of the features that you expect from controls, including keyboard and mouse input.</span></span> <span data-ttu-id="3e789-228">L’exemple suivant <xref:System.Windows.UIElement.MouseUp> montre <xref:System.Windows.Shapes.Ellipse> l’événement d’un être manipulé :</span><span class="sxs-lookup"><span data-stu-id="3e789-228">The following example shows the <xref:System.Windows.UIElement.MouseUp> event of an <xref:System.Windows.Shapes.Ellipse> being handled:</span></span>

[!code-xaml[IntroToWPFSnippets#HandleEllipseMouseUpEventMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_7.xaml)]

[!code-vb[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_8.vb)]
[!code-csharp[IntroToWPFSnippets#HandleEllipseMouseUpEventCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_8.cs)]

<span data-ttu-id="3e789-229">Le chiffre suivant montre ce qui est produit par le code précédent :</span><span class="sxs-lookup"><span data-stu-id="3e789-229">The following figure shows what is produced by the preceding code:</span></span>

![Fenêtre avec le texte « vous avez cliqué sur l’ellipse&#33; »](media/introduction-to-wpf/wpfintrofigure12.png)

<span data-ttu-id="3e789-231">Pour plus d’informations, voir [Formes et dessin de base dans la vue d’ensemble WPF](../../desktop-wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-231">For more information, see [Shapes and basic drawing in WPF overview](../../desktop-wpf/data/data-binding-overview.md).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="3e789-232">Géométries 2D</span><span class="sxs-lookup"><span data-stu-id="3e789-232">2D geometries</span></span>

<span data-ttu-id="3e789-233">Les formes 2D fournies par WPF couvrent le jeu standard des formes de base.</span><span class="sxs-lookup"><span data-stu-id="3e789-233">The 2D shapes provided by WPF cover the standard set of basic shapes.</span></span> <span data-ttu-id="3e789-234">Toutefois, vous pouvez avoir besoin de créer des formes personnalisées afin de faciliter la conception d’une interface utilisateur personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3e789-234">However, you may need to create custom shapes to facilitate the design of a customized user interface.</span></span> <span data-ttu-id="3e789-235">Pour cela, WPF fournit des géométries.</span><span class="sxs-lookup"><span data-stu-id="3e789-235">For this purpose, WPF provides geometries.</span></span> <span data-ttu-id="3e789-236">L’illustration suivante montre l’utilisation de géométries pour créer une forme personnalisée qui peut être dessinée directement, utilisée comme pinceau ou pour découper d’autres formes et contrôles.</span><span class="sxs-lookup"><span data-stu-id="3e789-236">The following figure demonstrates the use of geometries to create a custom shape that can be drawn directly, used as a brush, or used to clip other shapes and controls.</span></span>

<span data-ttu-id="3e789-237">Les objets<xref:System.Windows.Shapes.Path> peuvent être utilisés pour dessiner des formes fermées ou ouvertes, plusieurs formes et même des formes courbées.</span><span class="sxs-lookup"><span data-stu-id="3e789-237"><xref:System.Windows.Shapes.Path> objects can be used to draw closed or open shapes, multiple shapes, and even curved shapes.</span></span>

<span data-ttu-id="3e789-238">Les objets <xref:System.Windows.Media.Geometry> peuvent être utilisés pour le découpage, les tests de recherche et le rendu de données graphiques 2D.</span><span class="sxs-lookup"><span data-stu-id="3e789-238"><xref:System.Windows.Media.Geometry> objects can be used for clipping, hit-testing, and rendering 2D graphic data.</span></span>

![Différentes utilisations d’un chemin](media/introduction-to-wpf/wpfintrofigure5.png)

<span data-ttu-id="3e789-240">Pour plus d’informations, consultez [Vue d’ensemble de Geometry](graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-240">For more information, see [Geometry overview](graphics-multimedia/geometry-overview.md).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="3e789-241">Effets 2D</span><span class="sxs-lookup"><span data-stu-id="3e789-241">2D effects</span></span>

<span data-ttu-id="3e789-242">Un sous-ensemble des fonctionnalités 2D de WPF inclut des effets visuels, comme des dégradés, des bitmaps, des dessins, la peinture avec des vidéos, la rotation, la mise à l’échelle et l’inclinaison.</span><span class="sxs-lookup"><span data-stu-id="3e789-242">A subset of WPF 2D capabilities includes visual effects, such as gradients, bitmaps, drawings, painting with videos, rotation, scaling, and skewing.</span></span> <span data-ttu-id="3e789-243">Ceux-ci sont tous réalisés avec des pinceaux; le chiffre suivant montre quelques exemples :</span><span class="sxs-lookup"><span data-stu-id="3e789-243">These are all achieved with brushes; the following figure shows some examples:</span></span>

![Illustration de différents pinceaux](media/introduction-to-wpf/wpfintrofigure6.png)

<span data-ttu-id="3e789-245">Pour plus d’informations, consultez [Vue d’ensemble des pinceaux WPF](graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-245">For more information, see [WPF brushes overview](graphics-multimedia/wpf-brushes-overview.md).</span></span>

### <a name="3d-rendering"></a><span data-ttu-id="3e789-246">Rendu 3D</span><span class="sxs-lookup"><span data-stu-id="3e789-246">3D rendering</span></span>

<span data-ttu-id="3e789-247">WPF comprend également des fonctionnalités de rendu 3D qui s’intègrent aux graphiques 2D, permettant ainsi la création d’interfaces utilisateur plus intéressantes.</span><span class="sxs-lookup"><span data-stu-id="3e789-247">WPF also includes 3D rendering capabilities that integrate with 2-d graphics to allow the creation of more exciting and interesting user interfaces.</span></span> <span data-ttu-id="3e789-248">Par exemple, le chiffre suivant montre des images 2D rendues sur des formes 3D :</span><span class="sxs-lookup"><span data-stu-id="3e789-248">For example, the following figure shows 2D images rendered onto 3D shapes:</span></span>

![Capture d'écran : exemple Visual3D](media/introduction-to-wpf/wpfintrofigure13.png)

<span data-ttu-id="3e789-250">Pour plus d’informations, consultez [Vue d’ensemble des graphismes 3D](graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-250">For more information, see [3D graphics overview](graphics-multimedia/3-d-graphics-overview.md).</span></span>

## <a name="animation"></a><span data-ttu-id="3e789-251">Animation</span><span class="sxs-lookup"><span data-stu-id="3e789-251">Animation</span></span>

<span data-ttu-id="3e789-252">La prise en charge d’animations WPF vous permet d’agrandir, de faire bouger, de faire pivoter et de réaliser des fondus avec les contrôles pour créer des transitions de page intéressantes, et plus encore.</span><span class="sxs-lookup"><span data-stu-id="3e789-252">WPF animation support lets you make controls grow, shake, spin, and fade, to create interesting page transitions, and more.</span></span> <span data-ttu-id="3e789-253">Vous pouvez animer la plupart des classes WPF, même les classes personnalisées.</span><span class="sxs-lookup"><span data-stu-id="3e789-253">You can animate most WPF classes, even custom classes.</span></span> <span data-ttu-id="3e789-254">Le chiffre suivant montre une animation simple en action :</span><span class="sxs-lookup"><span data-stu-id="3e789-254">The following figure shows a simple animation in action:</span></span>

![Images d'un cube animé](media/introduction-to-wpf/wpfintrofigure7.png)

<span data-ttu-id="3e789-256">Pour plus d’informations, consultez [Vue d’ensemble de l’animation](graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-256">For more information, see [Animation overview](graphics-multimedia/animation-overview.md).</span></span>

## <a name="media"></a><span data-ttu-id="3e789-257">Médias</span><span class="sxs-lookup"><span data-stu-id="3e789-257">Media</span></span>

<span data-ttu-id="3e789-258">L’un des moyens d’acheminer un contenu riche est d’utiliser des médias audiovisuels.</span><span class="sxs-lookup"><span data-stu-id="3e789-258">One way to convey rich content is through the use of audiovisual media.</span></span> <span data-ttu-id="3e789-259">WPF fournit une prise en charge spéciale pour les images, les vidéos et l’audio.</span><span class="sxs-lookup"><span data-stu-id="3e789-259">WPF provides special support for images, video, and audio.</span></span>

### <a name="images"></a><span data-ttu-id="3e789-260">Images</span><span class="sxs-lookup"><span data-stu-id="3e789-260">Images</span></span>

<span data-ttu-id="3e789-261">Les images sont communes à la plupart des applications et WPF fournit plusieurs façons de les utiliser.</span><span class="sxs-lookup"><span data-stu-id="3e789-261">Images are common to most applications, and WPF provides several ways to use them.</span></span> <span data-ttu-id="3e789-262">L’illustration suivante montre une interface utilisateur avec une zone de liste qui contient des images miniatures.</span><span class="sxs-lookup"><span data-stu-id="3e789-262">The following figure shows a user interface with a list box that contains thumbnail images.</span></span> <span data-ttu-id="3e789-263">Lorsque vous sélectionnez une miniature, l’image s’affiche en grand.</span><span class="sxs-lookup"><span data-stu-id="3e789-263">When a thumbnail is selected, the image is shown full-size.</span></span>

![Images miniatures et image plein écran](media/introduction-to-wpf/wpfintrofigure8.png)

<span data-ttu-id="3e789-265">Pour plus d’informations, consultez [Vue d’ensemble de la création d’images](graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-265">For more information, see [Imaging overview](graphics-multimedia/imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="3e789-266">Audio et vidéo</span><span class="sxs-lookup"><span data-stu-id="3e789-266">Video and audio</span></span>

<span data-ttu-id="3e789-267">Le contrôle <xref:System.Windows.Controls.MediaElement> peut lire des vidéos et de l’audio, et est assez flexible pour servir de base à un lecteur multimédia personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3e789-267">The <xref:System.Windows.Controls.MediaElement> control is capable of playing both video and audio, and it is flexible enough to be the basis for a custom media player.</span></span> <span data-ttu-id="3e789-268">La balisage XAML suivante met en œuvre un lecteur multimédia :</span><span class="sxs-lookup"><span data-stu-id="3e789-268">The following XAML markup implements a media player:</span></span>

[!code-xaml[IntroToWPFSnippets#MediaElementMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_9.xaml)]

<span data-ttu-id="3e789-269">La fenêtre dans la <xref:System.Windows.Controls.MediaElement> figure suivante montre le contrôle en action :</span><span class="sxs-lookup"><span data-stu-id="3e789-269">The window in the following figure shows the <xref:System.Windows.Controls.MediaElement> control in action:</span></span>

![Contrôle MediaElement avec audio et vidéo](media/introduction-to-wpf/wpfintrofigure1.png)

<span data-ttu-id="3e789-271">Pour plus d’informations, consultez [Graphisme et multimédia](graphics-multimedia/index.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-271">For more information, see [Graphics and multimedia](graphics-multimedia/index.md).</span></span>

## <a name="text-and-typography"></a><span data-ttu-id="3e789-272">Texte et typographie</span><span class="sxs-lookup"><span data-stu-id="3e789-272">Text and typography</span></span>

<span data-ttu-id="3e789-273">Pour faciliter un rendu de texte de qualité optimale, WPF offre les fonctionnalités suivantes :</span><span class="sxs-lookup"><span data-stu-id="3e789-273">To facilitate high-quality text rendering, WPF offers the following features:</span></span>

- <span data-ttu-id="3e789-274">Prise en charge de la police OpenType.</span><span class="sxs-lookup"><span data-stu-id="3e789-274">OpenType font support.</span></span>

- <span data-ttu-id="3e789-275">Améliorations ClearType.</span><span class="sxs-lookup"><span data-stu-id="3e789-275">ClearType enhancements.</span></span>

- <span data-ttu-id="3e789-276">Performances élevées tirant parti de l’accélération matérielle.</span><span class="sxs-lookup"><span data-stu-id="3e789-276">High performance that takes advantage of hardware acceleration.</span></span>

- <span data-ttu-id="3e789-277">Intégration de texte avec des médias, des graphiques et des animations.</span><span class="sxs-lookup"><span data-stu-id="3e789-277">Integration of text with media, graphics, and animation.</span></span>

- <span data-ttu-id="3e789-278">Prise en charge de polices internationales et de mécanismes de secours.</span><span class="sxs-lookup"><span data-stu-id="3e789-278">International font support and fallback mechanisms.</span></span>

<span data-ttu-id="3e789-279">Comme une démonstration de l’intégration du texte avec les graphiques, la figure suivante montre l’application de décorations de texte:</span><span class="sxs-lookup"><span data-stu-id="3e789-279">As a demonstration of text integration with graphics, the following figure shows the application of text decorations:</span></span>

![Texte avec différents ornements](media/introduction-to-wpf/wpfintrofigure23.png)

<span data-ttu-id="3e789-281">Pour plus d’informations, consultez [Typographie dans WPF](advanced/typography-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-281">For more information, see [Typography in Windows Presentation Foundation](advanced/typography-in-wpf.md).</span></span>

## <a name="customize-wpf-apps"></a><span data-ttu-id="3e789-282">Personnaliser des applications WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-282">Customize WPF apps</span></span>

<span data-ttu-id="3e789-283">Jusqu’à présent, vous avez vu les principaux blocs de construction de WPF pour le développement des applications.</span><span class="sxs-lookup"><span data-stu-id="3e789-283">Up to this point, you've seen the core WPF building blocks for developing applications.</span></span> <span data-ttu-id="3e789-284">Vous utilisez le modèle d’application pour héberger et transmettre le contenu de l’application, principalement composé de contrôles.</span><span class="sxs-lookup"><span data-stu-id="3e789-284">You use the application model to host and deliver application content, which consists mainly of controls.</span></span> <span data-ttu-id="3e789-285">Pour simplifier l’organisation des contrôles dans une interface utilisateur et garantir la conservation de cette organisation face aux modifications de la taille de la fenêtre et des paramètres d’affichage, vous utilisez le système de disposition WPF.</span><span class="sxs-lookup"><span data-stu-id="3e789-285">To simplify the arrangement of controls in a user interface, and to ensure the arrangement is maintained in the face of changes to window size and display settings, you use the WPF layout system.</span></span> <span data-ttu-id="3e789-286">Étant donné que la plupart des applications permettent aux utilisateurs d’interagir avec les données, vous utilisez la liaison de données pour réduire le travail de l’intégration de votre interface utilisateur avec des données.</span><span class="sxs-lookup"><span data-stu-id="3e789-286">Because most applications let users interact with data, you use data binding to reduce the work of integrating your user interface with data.</span></span> <span data-ttu-id="3e789-287">Pour améliorer l’apparence visuelle de votre application, vous utilisez la gamme complète de graphiques, d’animations et de prise en charge des supports fournie par WPF.</span><span class="sxs-lookup"><span data-stu-id="3e789-287">To enhance the visual appearance of your application, you use the comprehensive range of graphics, animation, and media support provided by WPF.</span></span>

<span data-ttu-id="3e789-288">Les concepts de base ne sont pourtant pas tout le temps suffisants pour créer et gérer une expérience utilisateur vraiment particulière et visuellement surprenante.</span><span class="sxs-lookup"><span data-stu-id="3e789-288">Often, though, the basics are not enough for creating and managing a truly distinct and visually stunning user experience.</span></span> <span data-ttu-id="3e789-289">Il est possible que les contrôles WPF standard ne s’intègrent pas à l’apparence souhaitée de votre application.</span><span class="sxs-lookup"><span data-stu-id="3e789-289">The standard WPF controls might not integrate with the desired appearance of your application.</span></span> <span data-ttu-id="3e789-290">Les données risquent de ne pas s’afficher de la manière la plus efficace.</span><span class="sxs-lookup"><span data-stu-id="3e789-290">Data might not be displayed in the most effective way.</span></span> <span data-ttu-id="3e789-291">L’expérience utilisateur globale de votre application peut ne pas être adaptée à l’apparence par défaut des thèmes Windows.</span><span class="sxs-lookup"><span data-stu-id="3e789-291">Your application's overall user experience may not be suited to the default look and feel of Windows themes.</span></span> <span data-ttu-id="3e789-292">À bien des égards, une technologie de présentation a autant besoin d’une extensibilité visuelle que de tout autre type d’extensibilité.</span><span class="sxs-lookup"><span data-stu-id="3e789-292">In many ways, a presentation technology needs visual extensibility as much as any other type of extensibility.</span></span>

<span data-ttu-id="3e789-293">C’est pourquoi WPF fournit différents mécanismes pour créer des expériences utilisateur uniques, y compris un modèle de contenu riche pour les contrôles, les déclencheurs, les modèles de contrôles et de données, les styles, les ressources d’interface utilisateur, les thèmes et les apparences.</span><span class="sxs-lookup"><span data-stu-id="3e789-293">For this reason, WPF provides a variety of mechanisms for creating unique user experiences, including a rich content model for controls, triggers, control and data templates, styles, user interface resources, and themes and skins.</span></span>

### <a name="content-model"></a><span data-ttu-id="3e789-294">Modèle de contenu</span><span class="sxs-lookup"><span data-stu-id="3e789-294">Content model</span></span>

<span data-ttu-id="3e789-295">L’objectif principal d’une majorité des contrôles WPF est d’afficher du contenu.</span><span class="sxs-lookup"><span data-stu-id="3e789-295">The main purpose of a majority of the WPF controls is to display content.</span></span> <span data-ttu-id="3e789-296">Dans WPF, le type et le nombre d’éléments qui peuvent constituer le contenu d’un contrôle sont appelés *modèle de contenu*du contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e789-296">In WPF, the type and number of items that can constitute the content of a control is referred to as the control's *content model*.</span></span> <span data-ttu-id="3e789-297">Certains contrôles peuvent contenir un seul élément et un seul type de contenu ; par exemple, le contenu d’une <xref:System.Windows.Controls.TextBox> est une valeur de chaîne assignée à la propriété <xref:System.Windows.Controls.TextBox.Text%2A> .</span><span class="sxs-lookup"><span data-stu-id="3e789-297">Some controls can contain a single item and type of content; for example, the content of a <xref:System.Windows.Controls.TextBox> is a string value that is assigned to the <xref:System.Windows.Controls.TextBox.Text%2A> property.</span></span> <span data-ttu-id="3e789-298">L’exemple suivant définit <xref:System.Windows.Controls.TextBox>le contenu d’un :</span><span class="sxs-lookup"><span data-stu-id="3e789-298">The following example sets the content of a <xref:System.Windows.Controls.TextBox>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.TextBoxContentWindow"
    Title="TextBox Content">

    <TextBox Text="This is the content of a TextBox." />
</Window>
```

<span data-ttu-id="3e789-299">Le chiffre suivant montre le résultat :</span><span class="sxs-lookup"><span data-stu-id="3e789-299">The following figure shows the result:</span></span>

![Contrôle TextBox contenant du texte](media/introduction-to-wpf/wpfintrofigure21.png)

<span data-ttu-id="3e789-301">Toutefois, d’autres contrôles peuvent contenir plusieurs éléments de différents types de contenu ; le contenu d’un <xref:System.Windows.Controls.Button>, spécifié par la propriété <xref:System.Windows.Controls.ContentControl.Content%2A>, peut contenir différents éléments, y compris des contrôles de disposition, du texte, des images et des formes.</span><span class="sxs-lookup"><span data-stu-id="3e789-301">Other controls, however, can contain multiple items of different types of content; the content of a <xref:System.Windows.Controls.Button>, specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property, can contain a variety of items including layout controls, text, images, and shapes.</span></span> <span data-ttu-id="3e789-302">L’exemple suivant <xref:System.Windows.Controls.Button> montre un <xref:System.Windows.Controls.DockPanel>contenu <xref:System.Windows.Controls.Label>avec <xref:System.Windows.Controls.Border>qui comprend <xref:System.Windows.Controls.MediaElement>un , un , un , et un :</span><span class="sxs-lookup"><span data-stu-id="3e789-302">The following example shows a <xref:System.Windows.Controls.Button> with content that includes a <xref:System.Windows.Controls.DockPanel>, a <xref:System.Windows.Controls.Label>, a <xref:System.Windows.Controls.Border>, and a <xref:System.Windows.Controls.MediaElement>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ButtonContentWindow"
    Title="Button Content">

  <Button Margin="20">
    <!-- Button Content -->
    <DockPanel Width="200" Height="180">
      <Label DockPanel.Dock="Top" HorizontalAlignment="Center">Click Me!</Label>
      <Border Background="Black" BorderBrush="Yellow" BorderThickness="2"
        CornerRadius="2" Margin="5">
        <MediaElement Source="media/wpf.wmv" Stretch="Fill" />
      </Border>
    </DockPanel>
  </Button>
</Window>
```

<span data-ttu-id="3e789-303">Le chiffre suivant montre le contenu de ce bouton :</span><span class="sxs-lookup"><span data-stu-id="3e789-303">The following figure shows the content of this button:</span></span>

![Bouton contenant plusieurs types de contenu](media/introduction-to-wpf/wpfintrofigure22.png)

<span data-ttu-id="3e789-305">Pour plus d’informations sur les types de contenu pris en charge par différents contrôles, consultez [Modèle de contenu WPF](controls/wpf-content-model.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-305">For more information on the kinds of content that is supported by various controls, see [WPF content model](controls/wpf-content-model.md).</span></span>

### <a name="triggers"></a><span data-ttu-id="3e789-306">Déclencheurs</span><span class="sxs-lookup"><span data-stu-id="3e789-306">Triggers</span></span>

<span data-ttu-id="3e789-307">Bien que l’objectif principal du balisage XAML soit d’implémenter l’apparence d’une application, vous pouvez également utiliser XAML pour implémenter certains aspects du comportement d’une application.</span><span class="sxs-lookup"><span data-stu-id="3e789-307">Although the main purpose of XAML markup is to implement an application's appearance, you can also use XAML to implement some aspects of an application's behavior.</span></span> <span data-ttu-id="3e789-308">Vous pouvez, par exemple, utiliser des déclencheurs pour modifier l’apparence d’une application à partir des interventions de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3e789-308">One example is the use of triggers to change an application's appearance based on user interactions.</span></span> <span data-ttu-id="3e789-309">Pour plus d’informations, voir [Styles et modèles](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-309">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="control-templates"></a><span data-ttu-id="3e789-310">Modèles de contrôle</span><span class="sxs-lookup"><span data-stu-id="3e789-310">Control templates</span></span>

<span data-ttu-id="3e789-311">Les interfaces utilisateur par défaut pour les contrôles WPF sont en général construites à partir d’autres formes et contrôles.</span><span class="sxs-lookup"><span data-stu-id="3e789-311">The default user interfaces for WPF controls are typically constructed from other controls and shapes.</span></span> <span data-ttu-id="3e789-312">Par exemple, un <xref:System.Windows.Controls.Button> est composé de contrôles <xref:Microsoft.Windows.Themes.ButtonChrome> et <xref:System.Windows.Controls.ContentPresenter> .</span><span class="sxs-lookup"><span data-stu-id="3e789-312">For example, a <xref:System.Windows.Controls.Button> is composed of both <xref:Microsoft.Windows.Themes.ButtonChrome> and <xref:System.Windows.Controls.ContentPresenter> controls.</span></span> <span data-ttu-id="3e789-313">Le <xref:Microsoft.Windows.Themes.ButtonChrome> fournit l’apparence du bouton standard, alors que le <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du bouton, comme spécifié par la propriété <xref:System.Windows.Controls.ContentControl.Content%2A> .</span><span class="sxs-lookup"><span data-stu-id="3e789-313">The <xref:Microsoft.Windows.Themes.ButtonChrome> provides the standard button appearance, while the <xref:System.Windows.Controls.ContentPresenter> displays the button's content, as specified by the <xref:System.Windows.Controls.ContentControl.Content%2A> property.</span></span>

<span data-ttu-id="3e789-314">Parfois, l’apparence par défaut d’un contrôle peut être incompatible avec l’apparence globale d’une application.</span><span class="sxs-lookup"><span data-stu-id="3e789-314">Sometimes the default appearance of a control may be incongruent with the overall appearance of an application.</span></span> <span data-ttu-id="3e789-315">Dans ce cas, vous pouvez utiliser un <xref:System.Windows.Controls.ControlTemplate> pour modifier l’apparence de l’interface utilisateur du contrôle sans modifier ni son contenu, ni son comportement.</span><span class="sxs-lookup"><span data-stu-id="3e789-315">In this case, you can use a <xref:System.Windows.Controls.ControlTemplate> to change the appearance of the control's user interface without changing its content and behavior.</span></span>

<span data-ttu-id="3e789-316">L’exemple suivant montre comment changer <xref:System.Windows.Controls.Button> l’apparence d’un en utilisant un <xref:System.Windows.Controls.ControlTemplate>:</span><span class="sxs-lookup"><span data-stu-id="3e789-316">The following example shows how to change the appearance of a <xref:System.Windows.Controls.Button> by using a <xref:System.Windows.Controls.ControlTemplate>:</span></span>

[!code-xaml[IntroToWPFSnippets#ButtonControlTemplateWindowMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_16.xaml)]

[!code-csharp[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_17.cs)]
[!code-vb[IntroToWPFSnippets#ButtonControlTemplateWindowCODEBEHIND](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_17.vb)]

<span data-ttu-id="3e789-317">Dans cet exemple, l’interface utilisateur du bouton par défaut a été remplacée par une <xref:System.Windows.Shapes.Ellipse> aux bords bleu foncé remplie à l’aide d’un <xref:System.Windows.Media.RadialGradientBrush>.</span><span class="sxs-lookup"><span data-stu-id="3e789-317">In this example, the default button user interface has been replaced with an <xref:System.Windows.Shapes.Ellipse> that has a dark blue border and is filled using a <xref:System.Windows.Media.RadialGradientBrush>.</span></span> <span data-ttu-id="3e789-318">Le contrôle <xref:System.Windows.Controls.ContentPresenter> affiche le contenu du <xref:System.Windows.Controls.Button>, « Click Me! ».</span><span class="sxs-lookup"><span data-stu-id="3e789-318">The <xref:System.Windows.Controls.ContentPresenter> control displays the content of the <xref:System.Windows.Controls.Button>, "Click Me!"</span></span> <span data-ttu-id="3e789-319">Quand l’utilisateur clique sur <xref:System.Windows.Controls.Button> , l’événement <xref:System.Windows.Controls.Primitives.ButtonBase.Click> est toujours déclenché dans le cadre du comportement par défaut du contrôle <xref:System.Windows.Controls.Button> .</span><span class="sxs-lookup"><span data-stu-id="3e789-319">When the <xref:System.Windows.Controls.Button> is clicked, the <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event is still raised as part of the <xref:System.Windows.Controls.Button> control's default behavior.</span></span> <span data-ttu-id="3e789-320">Le résultat est affiché dans la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="3e789-320">The result is shown in the following figure:</span></span>

![Bouton en forme d'ellipse et seconde fenêtre](media/introduction-to-wpf/wpfintrofigure2.png)

### <a name="data-templates"></a><span data-ttu-id="3e789-322">Modèles de données</span><span class="sxs-lookup"><span data-stu-id="3e789-322">Data templates</span></span>

<span data-ttu-id="3e789-323">Alors qu’un modèle de contrôle vous permet de spécifier l’apparence d’un contrôle, un modèle de données vous permet de spécifier l’apparence du contenu d’un contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e789-323">Whereas a control template lets you specify the appearance of a control, a data template lets you specify the appearance of a control's content.</span></span> <span data-ttu-id="3e789-324">Les modèles de données sont souvent utilisés pour améliorer l’affichage des données liées.</span><span class="sxs-lookup"><span data-stu-id="3e789-324">Data templates are frequently used to enhance how bound data is displayed.</span></span> <span data-ttu-id="3e789-325">Le chiffre suivant montre l’apparence par défaut <xref:System.Windows.Controls.ListBox> `Task` d’un qui est lié à une collection d’objets, où chaque tâche a un nom, une description et une priorité :</span><span class="sxs-lookup"><span data-stu-id="3e789-325">The following figure shows the default appearance for a <xref:System.Windows.Controls.ListBox> that is bound to a collection of `Task` objects, where each task has a name, description, and priority:</span></span>

![Zone de liste avec une apparence par défaut](media/introduction-to-wpf/wpfintrofigure18.png)

<span data-ttu-id="3e789-327">L’apparence par défaut correspond à ce que vous pourriez attendre d’une <xref:System.Windows.Controls.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="3e789-327">The default appearance is what you would expect from a <xref:System.Windows.Controls.ListBox>.</span></span> <span data-ttu-id="3e789-328">Toutefois, l’apparence par défaut de chaque tâche ne contient que le nom de la tâche.</span><span class="sxs-lookup"><span data-stu-id="3e789-328">However, the default appearance of each task contains only the task name.</span></span> <span data-ttu-id="3e789-329">Pour afficher le nom, la description et la priorité de la tâche, l’apparence par défaut des éléments de liste liés du contrôle <xref:System.Windows.Controls.ListBox> doit être modifiée à l’aide d’un <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="3e789-329">To show the task name, description, and priority, the default appearance of the <xref:System.Windows.Controls.ListBox> control's bound list items must be changed by using a <xref:System.Windows.DataTemplate>.</span></span> <span data-ttu-id="3e789-330">Le XAML suivant définit <xref:System.Windows.DataTemplate>un tel , qui est <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> appliqué à chaque tâche en utilisant l’attribut:</span><span class="sxs-lookup"><span data-stu-id="3e789-330">The following XAML defines such a <xref:System.Windows.DataTemplate>, which is applied to each task by using the <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> attribute:</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="SDKSample.DataTemplateWindow"
  Title="With a Data Template">
  <Window.Resources>
    <!-- Data Template (applied to each bound task item in the task collection) -->
    <DataTemplate x:Key="myTaskTemplate">
      <Border Name="border" BorderBrush="DarkSlateBlue" BorderThickness="2"
        CornerRadius="2" Padding="5" Margin="5">
        <Grid>
          <Grid.RowDefinitions>
            <RowDefinition/>
            <RowDefinition/>
            <RowDefinition/>
          </Grid.RowDefinitions>
          <Grid.ColumnDefinitions>
            <ColumnDefinition Width="Auto" />
            <ColumnDefinition />
          </Grid.ColumnDefinitions>
          <TextBlock Grid.Row="0" Grid.Column="0" Padding="0,0,5,0" Text="Task Name:"/>
          <TextBlock Grid.Row="0" Grid.Column="1" Text="{Binding Path=TaskName}"/>
          <TextBlock Grid.Row="1" Grid.Column="0" Padding="0,0,5,0" Text="Description:"/>
          <TextBlock Grid.Row="1" Grid.Column="1" Text="{Binding Path=Description}"/>
          <TextBlock Grid.Row="2" Grid.Column="0" Padding="0,0,5,0" Text="Priority:"/>
          <TextBlock Grid.Row="2" Grid.Column="1" Text="{Binding Path=Priority}"/>
        </Grid>
      </Border>
    </DataTemplate>
  </Window.Resources>

  <!-- UI -->
  <DockPanel>
    <!-- Title -->
    <Label DockPanel.Dock="Top" FontSize="18" Margin="5" Content="My Task List:"/>

    <!-- Data template is specified by the ItemTemplate attribute -->
    <ListBox
      ItemsSource="{Binding}"
      ItemTemplate="{StaticResource myTaskTemplate}"
      HorizontalContentAlignment="Stretch"
      IsSynchronizedWithCurrentItem="True"
      Margin="5,0,5,5" />

 </DockPanel>
</Window>
```

<span data-ttu-id="3e789-331">Le chiffre suivant montre l’effet de ce code :</span><span class="sxs-lookup"><span data-stu-id="3e789-331">The following figure shows the effect of this code:</span></span>

![Zone de liste utilisant un modèle de données](media/introduction-to-wpf/wpfintrofigure19.png)

<span data-ttu-id="3e789-333">Notez que la <xref:System.Windows.Controls.ListBox> a conservé son comportement et son apparence globale ; seule l’apparence du contenu affiché par la zone de liste a été modifiée.</span><span class="sxs-lookup"><span data-stu-id="3e789-333">Note that the <xref:System.Windows.Controls.ListBox> has retained its behavior and overall appearance; only the appearance of the content being displayed by the list box has changed.</span></span>

<span data-ttu-id="3e789-334">Pour plus d’informations, consultez [Vue d’ensemble des modèles de données](data/data-templating-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-334">For more information, see [Data templating overview](data/data-templating-overview.md).</span></span>

### <a name="styles"></a><span data-ttu-id="3e789-335">Styles</span><span class="sxs-lookup"><span data-stu-id="3e789-335">Styles</span></span>

<span data-ttu-id="3e789-336">Les styles permettent aux développeurs et aux concepteurs de standardiser leur produit avec une apparence particulière.</span><span class="sxs-lookup"><span data-stu-id="3e789-336">Styles enable developers and designers to standardize on a particular appearance for their product.</span></span> <span data-ttu-id="3e789-337">WPF fournit un modèle de style fort, dont la fondation est l’élément <xref:System.Windows.Style> .</span><span class="sxs-lookup"><span data-stu-id="3e789-337">WPF provides a strong style model, the foundation of which is the <xref:System.Windows.Style> element.</span></span> <span data-ttu-id="3e789-338">L’exemple suivant crée un style qui <xref:System.Windows.Controls.Button> définit la `Orange`couleur de fond pour chaque sur une fenêtre à:</span><span class="sxs-lookup"><span data-stu-id="3e789-338">The following example creates a style that sets the background color for every <xref:System.Windows.Controls.Button> on a window to `Orange`:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.StyleWindow"
    Title="Styles">
  <!-- Style that will be applied to all buttons -->
  <Style TargetType="{x:Type Button}">
    <Setter Property="Background" Value="Orange" />
    <Setter Property="BorderBrush" Value="Crimson" />
    <Setter Property="FontSize" Value="20" />
    <Setter Property="FontWeight" Value="Bold" />
    <Setter Property="Margin" Value="5" />
  </Style>
  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>

  <!-- This label will not have the style applied to it -->
  <Label>Don't Click Me!</Label>

  <!-- This button will have the style applied to it -->
  <Button>Click Me!</Button>
</Window>
```

<span data-ttu-id="3e789-339">Étant donné que ce style cible tous les contrôles <xref:System.Windows.Controls.Button>, il est automatiquement appliqué à tous les boutons de la fenêtre, comme le montre la figure suivante :</span><span class="sxs-lookup"><span data-stu-id="3e789-339">Because this style targets all <xref:System.Windows.Controls.Button> controls, the style is automatically applied to all the buttons in the window, as shown in the following figure:</span></span>

![Deux boutons orange](media/introduction-to-wpf/wpfintrofigure20.png)

<span data-ttu-id="3e789-341">Pour plus d’informations, voir [Styles et modèles](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-341">For more information, see [Styles and templates](../../desktop-wpf/fundamentals/styles-templates-overview.md).</span></span>

### <a name="resources"></a><span data-ttu-id="3e789-342">Ressources</span><span class="sxs-lookup"><span data-stu-id="3e789-342">Resources</span></span>

<span data-ttu-id="3e789-343">Les contrôles d’une application doivent partager la même apparence, ce qui peut tout inclure, depuis les polices et les couleurs d’arrière-plan jusqu’aux modèles de contrôle, modèles de données et styles.</span><span class="sxs-lookup"><span data-stu-id="3e789-343">Controls in an application should share the same appearance, which can include anything from fonts and background colors to control templates, data templates, and styles.</span></span> <span data-ttu-id="3e789-344">Vous pouvez utiliser la prise en charge de WPF pour les ressources d’interface utilisateur afin d’encapsuler ces ressources dans un emplacement unique en vue d’une réutilisation.</span><span class="sxs-lookup"><span data-stu-id="3e789-344">You can use WPF's support for user interface resources to encapsulate these resources in a single location for reuse.</span></span>

<span data-ttu-id="3e789-345">L’exemple suivant définit une couleur de <xref:System.Windows.Controls.Button> fond <xref:System.Windows.Controls.Label>commune qui est partagée par a et un :</span><span class="sxs-lookup"><span data-stu-id="3e789-345">The following example defines a common background color that is shared by a <xref:System.Windows.Controls.Button> and a <xref:System.Windows.Controls.Label>:</span></span>

```xaml
<Window
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.ResourcesWindow"
    Title="Resources Window">

  <!-- Define window-scoped background color resource -->
  <Window.Resources>
    <SolidColorBrush x:Key="defaultBackground" Color="Red" />
  </Window.Resources>

  <!-- Button background is defined by window-scoped resource -->
  <Button Background="{StaticResource defaultBackground}">One Button</Button>

  <!-- Label background is defined by window-scoped resource -->
  <Label Background="{StaticResource defaultBackground}">One Label</Label>
</Window>
```

<span data-ttu-id="3e789-346">Cet exemple implémente une ressource de couleur d’arrière-plan à l’aide de l’élément de propriété `Window.Resources` .</span><span class="sxs-lookup"><span data-stu-id="3e789-346">This example implements a background color resource by using the `Window.Resources` property element.</span></span> <span data-ttu-id="3e789-347">Cette ressource est disponible pour tous les enfants de la <xref:System.Windows.Window>.</span><span class="sxs-lookup"><span data-stu-id="3e789-347">This resource is available to all children of the <xref:System.Windows.Window>.</span></span> <span data-ttu-id="3e789-348">Il existe différentes portées de ressource, dont les suivantes, répertoriées dans l’ordre dans lequel elles sont résolues :</span><span class="sxs-lookup"><span data-stu-id="3e789-348">There are a variety of resource scopes, including the following, listed in the order in which they are resolved:</span></span>

1. <span data-ttu-id="3e789-349">Un contrôle individuel (à l’aide de la propriété <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> héritée).</span><span class="sxs-lookup"><span data-stu-id="3e789-349">An individual control (using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

2. <span data-ttu-id="3e789-350">Une <xref:System.Windows.Window> ou une <xref:System.Windows.Controls.Page> (également à l’aide de la propriété <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> héritée).</span><span class="sxs-lookup"><span data-stu-id="3e789-350">A <xref:System.Windows.Window> or a <xref:System.Windows.Controls.Page> (also using the inherited <xref:System.Windows.FrameworkElement.Resources%2A?displayProperty=fullName> property).</span></span>

3. <span data-ttu-id="3e789-351">Une <xref:System.Windows.Application> (à l’aide de la propriété <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="3e789-351">An <xref:System.Windows.Application> (using the <xref:System.Windows.Application.Resources%2A?displayProperty=fullName> property).</span></span>

<span data-ttu-id="3e789-352">Les diverses portées offrent une grande flexibilité en ce qui concerne la manière de définir et partager vos ressources.</span><span class="sxs-lookup"><span data-stu-id="3e789-352">The variety of scopes gives you flexibility with respect to the way in which you define and share your resources.</span></span>

<span data-ttu-id="3e789-353">Au lieu d’associer directement vos ressources à une portée précise, vous pouvez empaqueter une ou plusieurs ressources à l’aide d’un <xref:System.Windows.ResourceDictionary> séparé qui peut être référencé dans d’autres parties d’une application</span><span class="sxs-lookup"><span data-stu-id="3e789-353">As an alternative to directly associating your resources with a particular scope, you can package one or more resources by using a separate <xref:System.Windows.ResourceDictionary> that can be referenced in other parts of an application.</span></span> <span data-ttu-id="3e789-354">Par exemple, l’exemple suivant définit une couleur de fond par défaut dans un dictionnaire de ressources :</span><span class="sxs-lookup"><span data-stu-id="3e789-354">For example, the following example defines a default background color in a resource dictionary:</span></span>

```xaml
<ResourceDictionary
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">

  <!-- Define background color resource -->
  <SolidColorBrush x:Key="defaultBackground" Color="Red" />

  <!-- Define other resources -->
</ResourceDictionary>
```

<span data-ttu-id="3e789-355">L’exemple suivant fait référence au dictionnaire des ressources défini dans l’exemple précédent afin qu’il soit partagé sur une application :</span><span class="sxs-lookup"><span data-stu-id="3e789-355">The following example references the resource dictionary defined in the previous example so that it is shared across an application:</span></span>

```xaml
<Application
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Class="SDKSample.App">

  <Application.Resources>
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>
        <ResourceDictionary Source="BackgroundColorResources.xaml"/>
      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  </Application.Resources>
</Application>
```

<span data-ttu-id="3e789-356">Les ressources et les dictionnaires de ressources constituent la fondation de la prise en charge WPF pour les thèmes et les apparences.</span><span class="sxs-lookup"><span data-stu-id="3e789-356">Resources and resource dictionaries are the foundation of WPF support for themes and skins.</span></span>

<span data-ttu-id="3e789-357">Pour plus d’informations, consultez [Ressources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-357">For more information, see [Resources](../../desktop-wpf/fundamentals/xaml-resources-define.md).</span></span>

### <a name="custom-controls"></a><span data-ttu-id="3e789-358">Contrôles personnalisés</span><span class="sxs-lookup"><span data-stu-id="3e789-358">Custom controls</span></span>

<span data-ttu-id="3e789-359">Bien que WPF fournisse un hôte de prise en charge de la personnalisation, vous pouvez rencontrer des situations dans lesquelles des contrôles WPF existants ne satisfont pas les besoins de votre application ou de ses utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="3e789-359">Although WPF provides a host of customization support, you may encounter situations where existing WPF controls do not meet the needs of either your application or its users.</span></span> <span data-ttu-id="3e789-360">Cela peut se produire lorsque :</span><span class="sxs-lookup"><span data-stu-id="3e789-360">This can occur when:</span></span>

- <span data-ttu-id="3e789-361">l’interface utilisateur dont vous avez besoin ne peut pas être créée en personnalisant l’apparence des implémentations WPF existantes ;</span><span class="sxs-lookup"><span data-stu-id="3e789-361">The user interface that you require cannot be created by customizing the look and feel of existing WPF implementations.</span></span>

- <span data-ttu-id="3e789-362">le comportement dont vous avez besoin n’est pas pris en charge (ou difficilement) par les implémentations WPF existantes.</span><span class="sxs-lookup"><span data-stu-id="3e789-362">The behavior that you require is not supported (or not easily supported) by existing WPF implementations.</span></span>

<span data-ttu-id="3e789-363">Toutefois, à ce stade, vous pouvez tirer parti de l’un des trois modèles WPF pour créer un contrôle.</span><span class="sxs-lookup"><span data-stu-id="3e789-363">At this point, however, you can take advantage of one of three WPF models to create a new control.</span></span> <span data-ttu-id="3e789-364">Chaque modèle cible un scénario spécifique et requiert que votre contrôle personnalisé dérive d’une classe de base WPF spécifique.</span><span class="sxs-lookup"><span data-stu-id="3e789-364">Each model targets a specific scenario and requires your custom control to derive from a particular WPF base class.</span></span> <span data-ttu-id="3e789-365">Les trois modèles sont répertoriés ici :</span><span class="sxs-lookup"><span data-stu-id="3e789-365">The three models are listed here:</span></span>

- <span data-ttu-id="3e789-366">**Modèle de contrôle utilisateur**.</span><span class="sxs-lookup"><span data-stu-id="3e789-366">**User Control Model**.</span></span> <span data-ttu-id="3e789-367">Un contrôle personnalisé dérive d’ <xref:System.Windows.Controls.UserControl> et est composé d’un ou de plusieurs autres contrôles.</span><span class="sxs-lookup"><span data-stu-id="3e789-367">A custom control derives from <xref:System.Windows.Controls.UserControl> and is composed of one or more other controls.</span></span>

- <span data-ttu-id="3e789-368">**Modèle de contrôle**.</span><span class="sxs-lookup"><span data-stu-id="3e789-368">**Control Model**.</span></span> <span data-ttu-id="3e789-369">Un contrôle personnalisé dérive du <xref:System.Windows.Controls.Control> et est utilisé pour générer des implémentations qui séparent leur comportement de leur apparence à l’aide de modèles, comme la majorité des contrôles WPF.</span><span class="sxs-lookup"><span data-stu-id="3e789-369">A custom control derives from <xref:System.Windows.Controls.Control> and is used to build implementations that separate their behavior from their appearance using templates, much like the majority of WPF controls.</span></span> <span data-ttu-id="3e789-370">Le fait qu’il dérive du <xref:System.Windows.Controls.Control> offre une plus grande liberté pour créer une interface utilisateur personnalisée que des contrôles utilisateur, mais peut nécessiter plus d’effort.</span><span class="sxs-lookup"><span data-stu-id="3e789-370">Deriving from <xref:System.Windows.Controls.Control> allows you more freedom for creating a custom user interface than user controls, but it may require more effort.</span></span>

- <span data-ttu-id="3e789-371">**Modèle de l’élément d’infrastructure**.</span><span class="sxs-lookup"><span data-stu-id="3e789-371">**Framework Element Model**.</span></span> <span data-ttu-id="3e789-372">Un contrôle personnalisé dérive de <xref:System.Windows.FrameworkElement> quand son apparence est définie par une logique de rendu personnalisé (et non des modèles).</span><span class="sxs-lookup"><span data-stu-id="3e789-372">A custom control derives from <xref:System.Windows.FrameworkElement> when its appearance is defined by custom rendering logic (not templates).</span></span>

<span data-ttu-id="3e789-373">L’exemple suivant montre un contrôle numérique personnalisé <xref:System.Windows.Controls.UserControl>vers le haut/vers le bas qui dérive de :</span><span class="sxs-lookup"><span data-stu-id="3e789-373">The following example shows a custom numeric up/down control that derives from <xref:System.Windows.Controls.UserControl>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlMARKUP](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_33.xaml)]

[!code-csharp[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/csharp/wpf/introduction-to-wpf/introduction-to-wpf_34.cs)]
[!code-vb[IntroToWPFSnippets#UserControlCODEBEHIND1](~/samples/snippets/visualbasic/wpf/introduction-to-wpf/introduction-to-wpf_34.vb)]

<span data-ttu-id="3e789-374">L’exemple suivant illustre le XAML qui est nécessaire <xref:System.Windows.Window>pour intégrer le contrôle de l’utilisateur dans un :</span><span class="sxs-lookup"><span data-stu-id="3e789-374">The following example illustrates the XAML that is required to incorporate the user control into a <xref:System.Windows.Window>:</span></span>

[!code-xaml[IntroToWPFSnippets#UserControlWindowMARKUP1](~/samples/snippets/xaml/wpf/introduction-to-wpf/introduction-to-wpf_37.xaml)]

<span data-ttu-id="3e789-375">Le chiffre suivant `NumericUpDown` montre le <xref:System.Windows.Window>contrôle hébergé dans un :</span><span class="sxs-lookup"><span data-stu-id="3e789-375">The following figure shows the `NumericUpDown` control hosted in a <xref:System.Windows.Window>:</span></span>

![UserControl personnalisé](media/introduction-to-wpf/wpfintrofigure3.png)

<span data-ttu-id="3e789-377">Pour plus d’informations sur les contrôles personnalisés, consultez [Vue d’ensemble de la création de contrôles](controls/control-authoring-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3e789-377">For more information on custom controls, see [Control authoring overview](controls/control-authoring-overview.md).</span></span>

## <a name="wpf-best-practices"></a><span data-ttu-id="3e789-378">Bonnes pratiques pour WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-378">WPF best practices</span></span>

<span data-ttu-id="3e789-379">Comme pour toute plateforme de développement, WPF peut être utilisé de différentes manières pour obtenir le résultat souhaité.</span><span class="sxs-lookup"><span data-stu-id="3e789-379">As with any development platform, WPF can be used in a variety of ways to achieve the desired result.</span></span> <span data-ttu-id="3e789-380">Afin de garantir que vos applications WPF fournissent l’expérience utilisateur requise et répondent aux demandes du public en général, il existe des meilleures pratiques pour l’accessibilité, la globalisation, la localisation et les performances.</span><span class="sxs-lookup"><span data-stu-id="3e789-380">As a way of ensuring that your WPF applications provide the required user experience and meet the demands of the audience in general, there are recommended best practices for accessibility, globalization and localization, and performance.</span></span> <span data-ttu-id="3e789-381">Pour plus d'informations, consultez les pages suivantes :</span><span class="sxs-lookup"><span data-stu-id="3e789-381">For more information, see:</span></span>

- [<span data-ttu-id="3e789-382">Accessibilité</span><span class="sxs-lookup"><span data-stu-id="3e789-382">Accessibility</span></span>](../ui-automation/accessibility-best-practices.md)
- [<span data-ttu-id="3e789-383">Globalisation et localisation pour WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-383">WPF globalization and localization</span></span>](advanced/wpf-globalization-and-localization-overview.md)
- [<span data-ttu-id="3e789-384">Performances des applications WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-384">WPF app performance</span></span>](advanced/optimizing-wpf-application-performance.md)
- [<span data-ttu-id="3e789-385">Sécurité de WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-385">WPF security</span></span>](security-wpf.md)

## <a name="next-steps"></a><span data-ttu-id="3e789-386">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="3e789-386">Next steps</span></span>

<span data-ttu-id="3e789-387">Nous avons examiné les fonctionnalités principales de WPF.</span><span class="sxs-lookup"><span data-stu-id="3e789-387">We've looked at the key features of WPF.</span></span> <span data-ttu-id="3e789-388">Il est maintenant temps de créer votre première application WPF.</span><span class="sxs-lookup"><span data-stu-id="3e789-388">Now it's time to build your first WPF app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3e789-389">Procédure pas à pas : ma première application WPF pour poste de travail</span><span class="sxs-lookup"><span data-stu-id="3e789-389">Walkthrough: My first WPF desktop app</span></span>](getting-started/walkthrough-my-first-wpf-desktop-application.md)

## <a name="see-also"></a><span data-ttu-id="3e789-390">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e789-390">See also</span></span>

- [<span data-ttu-id="3e789-391">Bien démarrer avec WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-391">Get started with WPF</span></span>](getting-started/index.md)
- [<span data-ttu-id="3e789-392">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="3e789-392">Windows Presentation Foundation</span></span>](index.md)
- [<span data-ttu-id="3e789-393">Ressources communautaires WPF</span><span class="sxs-lookup"><span data-stu-id="3e789-393">WPF community resources</span></span>](getting-started/community-feedback.md)
