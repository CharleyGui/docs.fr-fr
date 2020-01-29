---
title: Modèle de contenu
ms.date: 03/30/2017
helpviewer_keywords:
- UIElement class [WPF], displaying content
- content model [WPF], controls
- controls [WPF], displaying text
- content display [WPF], controls
- controls [WPF], formatting text
- displaying content [WPF]
- arbitrary content classes [WPF], content model
- ContentControl class [WPF], displaying content
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
ms.openlocfilehash: a84ab2e66b4e373591fc9365b1c17d0bb0c66713
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738282"
---
# <a name="wpf-content-model"></a><span data-ttu-id="0246a-102">Modèle de contenu WPF</span><span class="sxs-lookup"><span data-stu-id="0246a-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="0246a-103">est une plateforme de présentation qui fournit de nombreux contrôles et des éléments de type contrôle dont le principal objectif est d’afficher différents types de contenu.</span><span class="sxs-lookup"><span data-stu-id="0246a-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="0246a-104">Pour déterminer le contrôle à utiliser ou le contrôle d’où dériver, vous devez comprendre les types d’objets qu’un contrôle donné peut afficher de manière optimale.</span><span class="sxs-lookup"><span data-stu-id="0246a-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="0246a-105">Cette rubrique présente de manière synthétique le modèle de contenu pour les contrôles et les éléments de type contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0246a-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="0246a-106">Le modèle de contenu décrit le contenu qui peut être utilisé dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="0246a-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="0246a-107">Cette rubrique répertorie également les propriétés de contenu pour chaque modèle de contenu.</span><span class="sxs-lookup"><span data-stu-id="0246a-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="0246a-108">Une propriété de contenu est une propriété qui est utilisée pour stocker le contenu de l’objet.</span><span class="sxs-lookup"><span data-stu-id="0246a-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="0246a-109">Classes qui contiennent du contenu arbitraire</span><span class="sxs-lookup"><span data-stu-id="0246a-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="0246a-110">Certains contrôles peuvent contenir un objet de tout type, tel qu’une chaîne, un objet <xref:System.DateTime> ou un <xref:System.Windows.UIElement> qui est un conteneur pour des éléments supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="0246a-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="0246a-111">Par exemple, un <xref:System.Windows.Controls.Button> peut contenir une image et du texte. ou un <xref:System.Windows.Controls.CheckBox> peut contenir la valeur de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0246a-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="0246a-112">proposent quatre classes qui contiennent du contenu arbitraire.</span><span class="sxs-lookup"><span data-stu-id="0246a-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="0246a-113">Le tableau suivant répertorie les classes, qui héritent de <xref:System.Windows.Controls.Control>.</span><span class="sxs-lookup"><span data-stu-id="0246a-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="0246a-114">Classe qui contient du contenu arbitraire</span><span class="sxs-lookup"><span data-stu-id="0246a-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="0246a-115">Contenu</span><span class="sxs-lookup"><span data-stu-id="0246a-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="0246a-116">Objet arbitraire unique.</span><span class="sxs-lookup"><span data-stu-id="0246a-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="0246a-117">En-tête et élément unique, correspondant tous deux à des objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="0246a-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="0246a-118">Collection d’objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="0246a-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="0246a-119">En-tête et collection d’éléments, correspondant tous deux à des objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="0246a-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="0246a-120">Les contrôles qui héritent de ces classes peuvent contenir le même type de contenu et traiter le contenu de la même façon.</span><span class="sxs-lookup"><span data-stu-id="0246a-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="0246a-121">L’illustration suivante montre un contrôle à partir de chaque modèle de contenu qui contient une image et du texte :</span><span class="sxs-lookup"><span data-stu-id="0246a-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Capture d’écran montrant quatre contrôles différents, un à partir de chaque modèle de contenu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="0246a-123">Contrôles qui contiennent un objet arbitraire unique</span><span class="sxs-lookup"><span data-stu-id="0246a-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="0246a-124">La classe <xref:System.Windows.Controls.ContentControl> contient un seul élément de contenu arbitraire.</span><span class="sxs-lookup"><span data-stu-id="0246a-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="0246a-125">Sa propriété de contenu est <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="0246a-126">Les contrôles suivants héritent de <xref:System.Windows.Controls.ContentControl> et utilisent son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="0246a-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Button>  
  
- <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
- <xref:System.Windows.Controls.CheckBox>  
  
- <xref:System.Windows.Controls.ComboBoxItem>  
  
- <xref:System.Windows.Controls.ContentControl>  
  
- <xref:System.Windows.Controls.Frame>  
  
- <xref:System.Windows.Controls.GridViewColumnHeader>  
  
- <xref:System.Windows.Controls.GroupItem>  
  
- <xref:System.Windows.Controls.Label>  
  
- <xref:System.Windows.Controls.ListBoxItem>  
  
- <xref:System.Windows.Controls.ListViewItem>  
  
- <xref:System.Windows.Navigation.NavigationWindow>  
  
- <xref:System.Windows.Controls.RadioButton>  
  
- <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
- <xref:System.Windows.Controls.ScrollViewer>  
  
- <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
- <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
- <xref:System.Windows.Controls.ToolTip>  
  
- <xref:System.Windows.Controls.UserControl>  
  
- <xref:System.Windows.Window>  
  
 <span data-ttu-id="0246a-127">L’illustration suivante montre quatre boutons dont la <xref:System.Windows.Controls.ContentControl.Content%2A> est définie sur une chaîne, un objet <xref:System.DateTime>, un <xref:System.Windows.Shapes.Rectangle>et un <xref:System.Windows.Controls.Panel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>:</span><span class="sxs-lookup"><span data-stu-id="0246a-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Capture d’écran montrant quatre boutons avec différents types de contenu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="0246a-129">Pour obtenir un exemple de définition de la propriété <xref:System.Windows.Controls.ContentControl.Content%2A>, consultez <xref:System.Windows.Controls.ContentControl>.</span><span class="sxs-lookup"><span data-stu-id="0246a-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="0246a-130">Contrôles qui contiennent un en-tête et un objet arbitraire unique</span><span class="sxs-lookup"><span data-stu-id="0246a-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="0246a-131">La classe <xref:System.Windows.Controls.HeaderedContentControl> hérite de <xref:System.Windows.Controls.ContentControl> et affiche le contenu avec un en-tête.</span><span class="sxs-lookup"><span data-stu-id="0246a-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="0246a-132">Elle hérite de la propriété de contenu, <xref:System.Windows.Controls.ContentControl.Content%2A>, à partir de <xref:System.Windows.Controls.ContentControl> et définit la propriété <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> qui est de type <xref:System.Object>; par conséquent, les deux peuvent être un objet arbitraire.</span><span class="sxs-lookup"><span data-stu-id="0246a-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="0246a-133">Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedContentControl> et utilisent son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="0246a-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="0246a-134">L’illustration suivante montre deux objets <xref:System.Windows.Controls.TabItem>.</span><span class="sxs-lookup"><span data-stu-id="0246a-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="0246a-135">La première <xref:System.Windows.Controls.TabItem> a des objets <xref:System.Windows.UIElement> comme <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et le <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="0246a-136">La <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> est définie sur une <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="0246a-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="0246a-137">La <xref:System.Windows.Controls.ContentControl.Content%2A> est définie sur une <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Controls.TextBlock> et un <xref:System.Windows.Controls.Label>.</span><span class="sxs-lookup"><span data-stu-id="0246a-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="0246a-138">La deuxième <xref:System.Windows.Controls.TabItem> a une chaîne dans le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et un <xref:System.Windows.Controls.TextBlock> dans le <xref:System.Windows.Controls.ContentControl.Content%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl qui utilise différents types dans la propriété d’en-tête.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="0246a-140">Pour obtenir un exemple de création d’objets <xref:System.Windows.Controls.TabItem>, consultez <xref:System.Windows.Controls.HeaderedContentControl>.</span><span class="sxs-lookup"><span data-stu-id="0246a-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="0246a-141">Contrôles qui contiennent une collection d’objets arbitraires</span><span class="sxs-lookup"><span data-stu-id="0246a-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="0246a-142">La classe <xref:System.Windows.Controls.ItemsControl> hérite de <xref:System.Windows.Controls.Control> et peut contenir plusieurs éléments, tels que des chaînes, des objets ou d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="0246a-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="0246a-143">Ses propriétés de contenu sont <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> et <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="0246a-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> est généralement utilisé pour remplir le <xref:System.Windows.Controls.ItemsControl> avec une collection de données.</span><span class="sxs-lookup"><span data-stu-id="0246a-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="0246a-145">Si vous ne souhaitez pas utiliser de collection pour remplir le <xref:System.Windows.Controls.ItemsControl>, vous pouvez ajouter des éléments à l’aide de la propriété <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="0246a-146">Les contrôles suivants héritent de <xref:System.Windows.Controls.ItemsControl> et utilisent son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="0246a-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Menu>  
  
- <xref:System.Windows.Controls.Primitives.MenuBase>  
  
- <xref:System.Windows.Controls.ContextMenu>  
  
- <xref:System.Windows.Controls.ComboBox>  
  
- <xref:System.Windows.Controls.ItemsControl>  
  
- <xref:System.Windows.Controls.ListBox>  
  
- <xref:System.Windows.Controls.ListView>  
  
- <xref:System.Windows.Controls.TabControl>  
  
- <xref:System.Windows.Controls.TreeView>  
  
- <xref:System.Windows.Controls.Primitives.Selector>  
  
- <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 <span data-ttu-id="0246a-147">L’illustration suivante montre une <xref:System.Windows.Controls.ListBox> qui contient ces types d’éléments :</span><span class="sxs-lookup"><span data-stu-id="0246a-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="0246a-148">Chaîne.</span><span class="sxs-lookup"><span data-stu-id="0246a-148">A string.</span></span>  
  
- <span data-ttu-id="0246a-149">Objet <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="0246a-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="0246a-150"><xref:System.Windows.UIElement></span><span class="sxs-lookup"><span data-stu-id="0246a-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="0246a-151"><xref:System.Windows.Controls.Panel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="0246a-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Capture d’écran montrant un contrôle ListBox avec quatre types de contenu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="0246a-153">Contrôles qui contiennent un en-tête et une collection d’objets arbitraires</span><span class="sxs-lookup"><span data-stu-id="0246a-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="0246a-154">La classe <xref:System.Windows.Controls.HeaderedItemsControl> hérite de <xref:System.Windows.Controls.ItemsControl> et peut contenir plusieurs éléments, tels que des chaînes, des objets ou d’autres éléments, ainsi qu’un en-tête.</span><span class="sxs-lookup"><span data-stu-id="0246a-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="0246a-155">Elle hérite de la <xref:System.Windows.Controls.ItemsControl> propriétés de contenu, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>et <xref:System.Windows.Controls.ItemsControl.Items%2A>, et définit la propriété <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> qui peut être un objet arbitraire.</span><span class="sxs-lookup"><span data-stu-id="0246a-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="0246a-156">Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedItemsControl> et utilisent son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="0246a-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="0246a-157">Classes qui contiennent une collection d’objets UIElement</span><span class="sxs-lookup"><span data-stu-id="0246a-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="0246a-158">La classe <xref:System.Windows.Controls.Panel> positionne et organise les objets <xref:System.Windows.UIElement> enfants.</span><span class="sxs-lookup"><span data-stu-id="0246a-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="0246a-159">Sa propriété de contenu est <xref:System.Windows.Controls.Panel.Children%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="0246a-160">Les classes suivantes héritent de la classe <xref:System.Windows.Controls.Panel> et utilisent son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="0246a-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Canvas>  
  
- <xref:System.Windows.Controls.DockPanel>  
  
- <xref:System.Windows.Controls.Grid>  
  
- <xref:System.Windows.Controls.Primitives.TabPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
- <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
- <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
- <xref:System.Windows.Controls.StackPanel>  
  
- <xref:System.Windows.Controls.VirtualizingPanel>  
  
- <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
- <xref:System.Windows.Controls.WrapPanel>  
  
 <span data-ttu-id="0246a-161">Pour plus d’informations, consultez la page [Vue d’ensemble de Panel](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0246a-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="0246a-162">Classes qui affectent l’apparence d’un UIElement</span><span class="sxs-lookup"><span data-stu-id="0246a-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="0246a-163">La classe <xref:System.Windows.Controls.Decorator> applique des effets visuels sur ou autour d’un <xref:System.Windows.UIElement>enfant unique.</span><span class="sxs-lookup"><span data-stu-id="0246a-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="0246a-164">Sa propriété de contenu est <xref:System.Windows.Controls.Decorator.Child%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="0246a-165">Les classes suivantes héritent de <xref:System.Windows.Controls.Decorator> et utilisent son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="0246a-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="0246a-166">L’illustration suivante montre un <xref:System.Windows.Controls.TextBox> qui a (est décoré avec) un <xref:System.Windows.Controls.Border> autour de lui.</span><span class="sxs-lookup"><span data-stu-id="0246a-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="0246a-167">![TextBox avec bordure noire](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="0246a-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="0246a-168">TextBlock avec une bordure</span><span class="sxs-lookup"><span data-stu-id="0246a-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="0246a-169">Classes qui fournissent des commentaires visuels sur un UIElement</span><span class="sxs-lookup"><span data-stu-id="0246a-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="0246a-170">La classe <xref:System.Windows.Documents.Adorner> fournit des signaux visuels à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0246a-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="0246a-171">Par exemple, utilisez un <xref:System.Windows.Documents.Adorner> pour ajouter des handles fonctionnels à des éléments ou pour fournir des informations d’État sur un contrôle.</span><span class="sxs-lookup"><span data-stu-id="0246a-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="0246a-172">La classe <xref:System.Windows.Documents.Adorner> fournit une infrastructure qui vous permet de créer vos propres ornements.</span><span class="sxs-lookup"><span data-stu-id="0246a-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="0246a-173">ne fournit aucun ornement implémenté.</span><span class="sxs-lookup"><span data-stu-id="0246a-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="0246a-174">Pour plus d’informations, consultez [Vue d’ensemble des ornements](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0246a-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="0246a-175">Classes qui permettent aux utilisateurs d’entrer du texte</span><span class="sxs-lookup"><span data-stu-id="0246a-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="0246a-176">WPF fournit trois principaux contrôles qui permettent aux utilisateurs d’entrer du texte.</span><span class="sxs-lookup"><span data-stu-id="0246a-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="0246a-177">Chaque contrôle affiche le texte de manière différente.</span><span class="sxs-lookup"><span data-stu-id="0246a-177">Each control displays the text differently.</span></span> <span data-ttu-id="0246a-178">Le tableau suivant répertorie ces trois contrôles liés au texte, leurs fonctions lors de l’affichage du texte et leurs propriétés qui contiennent le texte du contrôle.</span><span class="sxs-lookup"><span data-stu-id="0246a-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="0246a-179">Contrôle</span><span class="sxs-lookup"><span data-stu-id="0246a-179">Control</span></span>|<span data-ttu-id="0246a-180">Texte affiché en tant que</span><span class="sxs-lookup"><span data-stu-id="0246a-180">Text is displayed as</span></span>|<span data-ttu-id="0246a-181">Propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="0246a-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="0246a-182">Texte brut</span><span class="sxs-lookup"><span data-stu-id="0246a-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="0246a-183">Texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="0246a-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="0246a-184">Texte masqué (les caractères sont masqués)</span><span class="sxs-lookup"><span data-stu-id="0246a-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a><span data-ttu-id="0246a-185">Classes qui affichent votre texte</span><span class="sxs-lookup"><span data-stu-id="0246a-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="0246a-186">Plusieurs classes peuvent être utilisées pour afficher du texte brut ou mis en forme.</span><span class="sxs-lookup"><span data-stu-id="0246a-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="0246a-187">Vous pouvez utiliser <xref:System.Windows.Controls.TextBlock> pour afficher de petites quantités de texte.</span><span class="sxs-lookup"><span data-stu-id="0246a-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="0246a-188">Si vous souhaitez afficher de grandes quantités de texte, utilisez les contrôles <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="0246a-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="0246a-189">La <xref:System.Windows.Controls.TextBlock> a deux propriétés de contenu : <xref:System.Windows.Controls.TextBlock.Text%2A> et <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="0246a-190">Lorsque vous souhaitez afficher du texte qui utilise une mise en forme cohérente, la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> est souvent le meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="0246a-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="0246a-191">Si vous envisagez d’utiliser une mise en forme différente dans tout le texte, utilisez la propriété <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="0246a-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="0246a-192">La propriété <xref:System.Windows.Controls.TextBlock.Inlines%2A> est une collection d’objets <xref:System.Windows.Documents.Inline>, qui spécifient comment mettre en forme le texte.</span><span class="sxs-lookup"><span data-stu-id="0246a-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="0246a-193">Le tableau suivant répertorie la propriété de contenu pour les classes <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>et <xref:System.Windows.Controls.FlowDocumentScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="0246a-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="0246a-194">Contrôle</span><span class="sxs-lookup"><span data-stu-id="0246a-194">Control</span></span>|<span data-ttu-id="0246a-195">Propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="0246a-195">Content property</span></span>|<span data-ttu-id="0246a-196">Type de propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="0246a-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="0246a-197">Document</span><span class="sxs-lookup"><span data-stu-id="0246a-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="0246a-198">Document</span><span class="sxs-lookup"><span data-stu-id="0246a-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="0246a-199">Document</span><span class="sxs-lookup"><span data-stu-id="0246a-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="0246a-200">Le <xref:System.Windows.Documents.FlowDocument> implémente l’interface <xref:System.Windows.Documents.IDocumentPaginatorSource> ; par conséquent, les trois classes peuvent prendre une <xref:System.Windows.Documents.FlowDocument> en tant que contenu.</span><span class="sxs-lookup"><span data-stu-id="0246a-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a><span data-ttu-id="0246a-201">Classes de mise en forme du texte</span><span class="sxs-lookup"><span data-stu-id="0246a-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="0246a-202"><xref:System.Windows.Documents.TextElement> et ses classes connexes vous permettent de mettre en forme du texte.</span><span class="sxs-lookup"><span data-stu-id="0246a-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="0246a-203"><xref:System.Windows.Documents.TextElement> objets contiennent et mettent en forme du texte dans des objets <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="0246a-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="0246a-204">Les deux principaux types d’objets <xref:System.Windows.Documents.TextElement> sont <xref:System.Windows.Documents.Block> éléments et <xref:System.Windows.Documents.Inline> éléments.</span><span class="sxs-lookup"><span data-stu-id="0246a-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="0246a-205">Un élément <xref:System.Windows.Documents.Block> représente un bloc de texte, tel qu’un paragraphe ou une liste.</span><span class="sxs-lookup"><span data-stu-id="0246a-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="0246a-206">Un élément <xref:System.Windows.Documents.Inline> représente une partie du texte d’un bloc.</span><span class="sxs-lookup"><span data-stu-id="0246a-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="0246a-207">De nombreuses classes de <xref:System.Windows.Documents.Inline> spécifient la mise en forme du texte auquel elles sont appliquées.</span><span class="sxs-lookup"><span data-stu-id="0246a-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="0246a-208">Chaque <xref:System.Windows.Documents.TextElement> possède son propre modèle de contenu.</span><span class="sxs-lookup"><span data-stu-id="0246a-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="0246a-209">Pour plus d’informations, consultez la page [Vue d’ensemble du modèle de contenu de TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0246a-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0246a-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0246a-210">See also</span></span>

- [<span data-ttu-id="0246a-211">Avancé</span><span class="sxs-lookup"><span data-stu-id="0246a-211">Advanced</span></span>](../advanced/index.md)
