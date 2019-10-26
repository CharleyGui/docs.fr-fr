---
title: Code source L2DBForm.xaml
ms.date: 10/22/2019
ms.topic: sample
ms.openlocfilehash: 290b00e136f0c49e1b27d4fa1bca7321eebe936e
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2019
ms.locfileid: "72920943"
---
# <a name="l2dbformxaml-source-code"></a><span data-ttu-id="c7020-102">Code source L2DBForm.xaml</span><span class="sxs-lookup"><span data-stu-id="c7020-102">L2DBForm.xaml source code</span></span>

<span data-ttu-id="c7020-103">Cette page contient et décrit le fichier source XAML pour la [liaison de données WPF à l’aide de LINQ to XML exemple](linq-to-xml-data-binding-sample.md).</span><span class="sxs-lookup"><span data-stu-id="c7020-103">This page contains and describes the XAML source file for the [WPF data binding using LINQ to XML example](linq-to-xml-data-binding-sample.md).</span></span>

## <a name="overall-ui-structure"></a><span data-ttu-id="c7020-104">Structure globale d’interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="c7020-104">Overall UI structure</span></span>

<span data-ttu-id="c7020-105">Comme c’est généralement le cas pour un projet WPF, ce fichier contient un élément parent, un <xref:System.Windows.Window> élément XML associé à la classe dérivée `L2XDBFrom` dans l’espace de noms `LinqToXmlDataBinding`.</span><span class="sxs-lookup"><span data-stu-id="c7020-105">As is typical for a WPF project, this file contains one parent element, a <xref:System.Windows.Window> XML element that's associated with the derived class `L2XDBFrom` in the `LinqToXmlDataBinding` namespace.</span></span>

<span data-ttu-id="c7020-106">La zone cliente est contenue dans un <xref:System.Windows.Controls.StackPanel> qui reçoit un arrière-plan bleu clair.</span><span class="sxs-lookup"><span data-stu-id="c7020-106">The client area is contained within a <xref:System.Windows.Controls.StackPanel> that's given a light blue background.</span></span> <span data-ttu-id="c7020-107">Ce volet contient quatre sections d'interface utilisateur <xref:System.Windows.Controls.DockPanel> séparées par des barres <xref:System.Windows.Controls.Separator> .</span><span class="sxs-lookup"><span data-stu-id="c7020-107">This panel contains four <xref:System.Windows.Controls.DockPanel> UI sections separated by <xref:System.Windows.Controls.Separator> bars.</span></span> <span data-ttu-id="c7020-108">L’objectif de ces sections est décrit [ici](linq-to-xml-data-binding-sample.md#overview).</span><span class="sxs-lookup"><span data-stu-id="c7020-108">The purpose of these sections is described [here](linq-to-xml-data-binding-sample.md#overview).</span></span>

<span data-ttu-id="c7020-109">Chaque section contient une étiquette qui l'identifie.</span><span class="sxs-lookup"><span data-stu-id="c7020-109">Each section contains a label that identifies it.</span></span> <span data-ttu-id="c7020-110">Dans les deux premières sections, cette étiquette est pivotée de 90 degrés par le biais d'une propriété <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span><span class="sxs-lookup"><span data-stu-id="c7020-110">In the first two sections, this label is rotated 90 degrees through the use of a <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.</span></span> <span data-ttu-id="c7020-111">Le reste de la section contient des éléments d’interface utilisateur adaptés à l’objectif de cette section, par exemple, les blocs de texte, les zones de texte et les boutons.</span><span class="sxs-lookup"><span data-stu-id="c7020-111">The rest of the section contains UI elements appropriate to the purpose of that section, for example, text blocks, text boxes, and buttons.</span></span> <span data-ttu-id="c7020-112">Parfois, un objet <xref:System.Windows.Controls.StackPanel> enfant est utilisé pour aligner ces contrôles enfants.</span><span class="sxs-lookup"><span data-stu-id="c7020-112">Sometimes a child <xref:System.Windows.Controls.StackPanel> is used to align these child controls.</span></span>

## <a name="window-resource-section"></a><span data-ttu-id="c7020-113">Section de ressources de fenêtre</span><span class="sxs-lookup"><span data-stu-id="c7020-113">Window resource section</span></span>

<span data-ttu-id="c7020-114">La balise `<Window.Resources>` d'ouverture sur la ligne 9 indique le début de la section de ressources de fenêtre.</span><span class="sxs-lookup"><span data-stu-id="c7020-114">The opening `<Window.Resources>` tag on line 9 indicates the start of the window resource section.</span></span> <span data-ttu-id="c7020-115">Cette section se termine par la balise de fermeture sur la ligne 35.</span><span class="sxs-lookup"><span data-stu-id="c7020-115">It ends with the closing tag on line 35.</span></span>

<span data-ttu-id="c7020-116">La balise `<ObjectDataProvider>` , qui s'étend de la ligne 11 à la ligne 25, déclare un objet <xref:System.Windows.Data.ObjectDataProvider>, nommé `LoadedBooks`, qui utilise un objet <xref:System.Xml.Linq.XElement> comme source.</span><span class="sxs-lookup"><span data-stu-id="c7020-116">The `<ObjectDataProvider>` tag, which spans lines 11 through 25, declares a <xref:System.Windows.Data.ObjectDataProvider>, named `LoadedBooks`, that uses an <xref:System.Xml.Linq.XElement> as the source.</span></span> <span data-ttu-id="c7020-117">Le <xref:System.Xml.Linq.XElement> est initialisé par l’analyse d’un document XML incorporé (un élément `CDATA`).</span><span class="sxs-lookup"><span data-stu-id="c7020-117">The <xref:System.Xml.Linq.XElement> is initialized by parsing an embedded XML document (a `CDATA` element).</span></span> <span data-ttu-id="c7020-118">Notez que les espaces blancs sont conservés lors de la déclaration du document XML incorporé et également lors de son analyse.</span><span class="sxs-lookup"><span data-stu-id="c7020-118">Notice that white space is preserved when declaring the embedded XML document and also when it's parsed.</span></span> <span data-ttu-id="c7020-119">Cela est dû au fait que le contrôle <xref:System.Windows.Controls.TextBlock>, qui est utilisé pour afficher le code XML brut, n’a pas de fonctionnalités spéciales de mise en forme XML.</span><span class="sxs-lookup"><span data-stu-id="c7020-119">White space is preserved because the <xref:System.Windows.Controls.TextBlock> control, which is used to display the raw XML, has no special XML formatting capabilities.</span></span>

<span data-ttu-id="c7020-120">Pour finir, un objet <xref:System.Windows.DataTemplate> nommé `BookTemplate` est défini sur les lignes 28 à 34.</span><span class="sxs-lookup"><span data-stu-id="c7020-120">Lastly, a <xref:System.Windows.DataTemplate> named `BookTemplate` is defined on lines 28 through 34.</span></span> <span data-ttu-id="c7020-121">Ce modèle est utilisé pour afficher les entrées dans la section **Book List** de l’interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="c7020-121">This template is used to display the entries in the **Book List** UI section.</span></span> <span data-ttu-id="c7020-122">Il utilise les propriétés dynamiques LINQ to XML et de liaison de données pour récupérer l'ID de livre et le nom de livre par le biais des affectations suivantes :</span><span class="sxs-lookup"><span data-stu-id="c7020-122">It uses data binding and LINQ to XML dynamic properties to retrieve the book ID and book name through the following assignments:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"Text="{Binding Path=Value}"
```

## <a name="data-binding-code"></a><span data-ttu-id="c7020-123">Code de liaison de données</span><span class="sxs-lookup"><span data-stu-id="c7020-123">Data binding code</span></span>

<span data-ttu-id="c7020-124">En plus de l'élément <xref:System.Windows.DataTemplate> , la liaison de données est utilisée à d'autres emplacements de ce fichier.</span><span class="sxs-lookup"><span data-stu-id="c7020-124">In addition to the <xref:System.Windows.DataTemplate> element, data binding is used in a number of other places in this file.</span></span>

<span data-ttu-id="c7020-125">Dans la balise `<StackPanel>` d'ouverture sur la ligne 38, le fournisseur de données <xref:System.Windows.FrameworkElement.DataContext%2A> est affecté à la propriété `LoadedBooks` de ce volet.</span><span class="sxs-lookup"><span data-stu-id="c7020-125">In the opening `<StackPanel>` tag on line 38, the <xref:System.Windows.FrameworkElement.DataContext%2A> property of this panel is set to the `LoadedBooks` data provider.</span></span>

```xaml
DataContext="{Binding Source={StaticResource LoadedBooks}}
```

<span data-ttu-id="c7020-126">La définition du contexte des données permet (sur la ligne 46) à l’objet <xref:System.Windows.Controls.TextBlock> nommé `tbRawXml` d’afficher le code XML brut en effectuant la liaison à la propriété `Xml` de ce fournisseur de données :</span><span class="sxs-lookup"><span data-stu-id="c7020-126">Setting the data context makes it possible (on line 46) for the <xref:System.Windows.Controls.TextBlock> named `tbRawXml` to display the raw XML by binding to this data provider's `Xml` property:</span></span>

```xaml
Text="{Binding Path=Xml}"
```

<span data-ttu-id="c7020-127">L'objet <xref:System.Windows.Controls.ListBox> dans la section d'interface utilisateur **Book List** , sur les lignes 58 à 62, définit le modèle pour ses éléments d'affichage au `BookTemplate` défini dans la section de ressources de fenêtre :</span><span class="sxs-lookup"><span data-stu-id="c7020-127">The <xref:System.Windows.Controls.ListBox> in the **Book List** UI section, on lines 58 through 62, sets the template for its display items to the `BookTemplate` defined in the window resource section:</span></span>

```xaml
ItemTemplate ="{StaticResource BookTemplate}"
```

<span data-ttu-id="c7020-128">Ensuite, sur les lignes 59 à 62, les valeurs réelles des livres sont liées à cette zone de texte :</span><span class="sxs-lookup"><span data-stu-id="c7020-128">Then, on lines 59 through 62, the actual values of the books are bound to this list box:</span></span>

```xaml
<ListBox.ItemsSource>
    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
</ListBox.ItemsSource>
```

<span data-ttu-id="c7020-129">La troisième section d'interface utilisateur, **Edit Selected Book**, lie d'abord la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> de l'objet <xref:System.Windows.Controls.StackPanel> parent à l'élément actuellement sélectionné dans la section d'interface utilisateur **Book List** (ligne 82) :</span><span class="sxs-lookup"><span data-stu-id="c7020-129">The third UI section, **Edit Selected Book**, first binds the <xref:System.Windows.FrameworkElement.DataContext%2A> of the parent <xref:System.Windows.Controls.StackPanel> to the currently selected item in from the **Book List** UI section (line 82):</span></span>

```xaml
DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}"
```

<span data-ttu-id="c7020-130">Elle utilise ensuite la liaison de données bidirectionnelle, de sorte que les valeurs actuelles des éléments de livre soient affichées dans et mises à jour à partir des deux zones de texte de ce volet.</span><span class="sxs-lookup"><span data-stu-id="c7020-130">It then uses two-way data binding, so that the current values of the book elements are displayed to, and updated from, the two text boxes in this panel.</span></span> <span data-ttu-id="c7020-131">La liaison de données aux propriétés dynamiques est similaire à celle utilisée dans le modèle de données `BookTemplate` :</span><span class="sxs-lookup"><span data-stu-id="c7020-131">Data binding to dynamic properties is similar to the data binding used in the `BookTemplate` data template:</span></span>

```xaml
Text="{Binding Path=Attribute[id].Value}"...Text="{Binding Path=Value}"
```

<span data-ttu-id="c7020-132">La dernière section de l’interface utilisateur, **Add New Book**, n’utilise pas la liaison de données dans son code XAML.</span><span class="sxs-lookup"><span data-stu-id="c7020-132">The last UI section, **Add New Book**, doesn't use data binding in its XAML code.</span></span> <span data-ttu-id="c7020-133">Au lieu de cela, la liaison de données est dans le code de son gestionnaire d’événements, dans le fichier *L2DBForm.xaml.cs*.</span><span class="sxs-lookup"><span data-stu-id="c7020-133">Instead, data binding is in its event handling code in the file *L2DBForm.xaml.cs*.</span></span>

## <a name="example"></a><span data-ttu-id="c7020-134">Exemple</span><span class="sxs-lookup"><span data-stu-id="c7020-134">Example</span></span>

### <a name="description"></a><span data-ttu-id="c7020-135">Description</span><span class="sxs-lookup"><span data-stu-id="c7020-135">Description</span></span>

> [!NOTE]
> <span data-ttu-id="c7020-136">Nous vous recommandons de copier le code ci-dessous dans un éditeur de code, tel que l'éditeur de code source C# fourni avec Visual Studio, afin de faciliter le suivi des numéros de lignes.</span><span class="sxs-lookup"><span data-stu-id="c7020-136">We recommend that you copy the following code below into a code editor, such as the C# source code editor in Visual Studio, so that line numbers will be easier to track.</span></span>

### <a name="code"></a><span data-ttu-id="c7020-137">Code</span><span class="sxs-lookup"><span data-stu-id="c7020-137">Code</span></span>

```xml
<Window x:Class="LinqToXmlDataBinding.L2XDBForm"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:system="clr-namespace:System;assembly=mscorlib"
    xmlns:xlinq="clr-namespace:System.Xml.Linq;assembly=System.Xml.Linq"
    xmlns:local="clr-namespace:LinqToXmlDataBinding"
    Title="WPF Data Binding using LINQ-to-XML" Height="665" Width="500" ResizeMode="NoResize">

    <Window.Resources>
        <!-- Books provider and inline data -->
        <ObjectDataProvider x:Key="LoadedBooks" ObjectType="{x:Type xlinq:XElement}" MethodName="Parse">
            <ObjectDataProvider.MethodParameters>
                <system:String xml:space="preserve">
<![CDATA[
<books xmlns="http://www.mybooks.com">
  <book id="0">book zero</book>
  <book id="1">book one</book>
  <book id="2">book two</book>
  <book id="3">book three</book>
</books>
]]>
                </system:String>
                <xlinq:LoadOptions>PreserveWhitespace</xlinq:LoadOptions>
            </ObjectDataProvider.MethodParameters>
        </ObjectDataProvider>

        <!-- Template for use in Books List listbox. -->
        <DataTemplate x:Key="BookTemplate">
            <StackPanel Orientation="Horizontal">
                <TextBlock Margin="3" Text="{Binding Path=Attribute[id].Value}"/>
                <TextBlock Margin="3" Text="-"/>
                <TextBlock Margin="3" Text="{Binding Path=Value}"/>
            </StackPanel>
        </DataTemplate>
    </Window.Resources>

    <!-- Main visual content container -->
    <StackPanel Background="lightblue" DataContext="{Binding Source={StaticResource LoadedBooks}}">
        <!-- Raw XML display section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">XML
            <Label.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Label.LayoutTransform>
            </Label>
            <TextBlock Name="tbRawXml" Height="200" Background="LightGray" Text="{Binding Path=Xml}" TextTrimming="CharacterEllipsis" />
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- List box to display all books section -->
        <DockPanel Margin="5">
            <Label  Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" FontWeight="Bold">Book List
                <Label.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Label.LayoutTransform>
            </Label>
            <ListBox Name="lbBooks" Height="200" Width="415" ItemTemplate ="{StaticResource BookTemplate}">
                <ListBox.ItemsSource>
                    <Binding Path="Elements[{http://www.mybooks.com}book]"/>
                </ListBox.ItemsSource>
            </ListBox>
            <Button Margin="5" DockPanel.Dock="Right" Height="30" Width ="130" Content="Remove Selected Book" Click="OnRemoveBook">
            <Button.LayoutTransform>
                <RotateTransform Angle="90"/>
            </Button.LayoutTransform>
            </Button>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Edit current selection section -->
        <DockPanel Margin="5">
            <TextBlock Margin="5" Height="30" Width="65" DockPanel.Dock="Right" Background="LightGray" TextWrapping="Wrap" TextAlignment="Center">
                    Changes are live!
                <TextBlock.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </TextBlock.LayoutTransform>
            </TextBlock>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Edit Selected Book</Label>
                <StackPanel Margin="1" DataContext="{Binding ElementName=lbBooks, Path=SelectedItem}">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="editAttributeTextBox" Width="410" Text="{Binding Path=Attribute[id].Value}">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book ID and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="editValueTextBox" Width="410" Text="{Binding Path=Value}" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Edit the selected book Value and see it changed.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>

        <Separator Height="4" Margin="5" />

        <!-- Add new book section -->
        <DockPanel Margin="5">
            <Button Margin="5" Height="30" DockPanel.Dock="Right" Click ="OnAddBook">Add Book
                <Button.LayoutTransform>
                    <RotateTransform Angle="90"/>
                </Button.LayoutTransform>
            </Button>
            <StackPanel>
                <Label Width="450" Background="Gray" FontSize="12" BorderBrush="Black" BorderThickness="1" HorizontalAlignment="Left" FontWeight="Bold">Add New Book</Label>
                <StackPanel Margin="1">
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">ID:</Label>
                        <TextBox Name="tbAddID" Width="410">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="Bold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                    <StackPanel Orientation="Horizontal">
                        <Label Width="40">Value:</Label>
                        <TextBox Name="tbAddValue" Width="410" Height="25">
                            <TextBox.ToolTip>
                                <TextBlock FontWeight="UltraBold" TextAlignment="Center">
                                    <Label>Enter a book ID and Value pair, then click Add Book.</Label>
                                </TextBlock>
                            </TextBox.ToolTip>
                        </TextBox>
                    </StackPanel>
                </StackPanel>
            </StackPanel>
        </DockPanel>
    </StackPanel>
</Window>
```

### <a name="comments"></a><span data-ttu-id="c7020-138">Comments</span><span class="sxs-lookup"><span data-stu-id="c7020-138">Comments</span></span>

<span data-ttu-id="c7020-139">Pour obtenir le code source C# pour les gestionnaires d’événements associés aux éléments d’interface utilisateur WPF, consultez [Code source L2DBForm.xaml.cs](l2dbform-xaml-cs-source-code.md).</span><span class="sxs-lookup"><span data-stu-id="c7020-139">For the C# source code for the event handlers associated with the WPF UI elements, see [L2DBForm.xaml.cs source code](l2dbform-xaml-cs-source-code.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7020-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c7020-140">See also</span></span>

- [<span data-ttu-id="c7020-141">Procédure pas à pas : exemple LinqToXmlDataBinding</span><span class="sxs-lookup"><span data-stu-id="c7020-141">Walkthrough: LinqToXmlDataBinding example</span></span>](linq-to-xml-data-binding-sample.md)
- [<span data-ttu-id="c7020-142">Code source L2DBForm.xaml.cs</span><span class="sxs-lookup"><span data-stu-id="c7020-142">L2DBForm.xaml.cs source code</span></span>](l2dbform-xaml-cs-source-code.md)
