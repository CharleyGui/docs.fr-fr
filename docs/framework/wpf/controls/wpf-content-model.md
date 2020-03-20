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
ms.openlocfilehash: ec4e96c0883489135b77f09a3c19f144cb4d30bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187403"
---
# <a name="wpf-content-model"></a><span data-ttu-id="f1c63-102">Modèle de contenu WPF</span><span class="sxs-lookup"><span data-stu-id="f1c63-102">WPF Content Model</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="f1c63-103">est une plateforme de présentation qui fournit de nombreux contrôles et des éléments de type contrôle dont le principal objectif est d’afficher différents types de contenu.</span><span class="sxs-lookup"><span data-stu-id="f1c63-103">is a presentation platform that provides many controls and control-like types whose primary purpose is to display different types of content.</span></span> <span data-ttu-id="f1c63-104">Pour déterminer le contrôle à utiliser ou le contrôle d’où dériver, vous devez comprendre les types d’objets qu’un contrôle donné peut afficher de manière optimale.</span><span class="sxs-lookup"><span data-stu-id="f1c63-104">To determine which control to use or which control to derive from, you should understand the kinds of objects a particular control can best display.</span></span>  
  
 <span data-ttu-id="f1c63-105">Cette rubrique présente de manière synthétique le modèle de contenu pour les contrôles et les éléments de type contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f1c63-105">This topic summarizes the content model for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] control and control-like types.</span></span> <span data-ttu-id="f1c63-106">Le modèle de contenu décrit le contenu qui peut être utilisé dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="f1c63-106">The content model describes what content can be used in a control.</span></span> <span data-ttu-id="f1c63-107">Cette rubrique répertorie également les propriétés de contenu pour chaque modèle de contenu.</span><span class="sxs-lookup"><span data-stu-id="f1c63-107">This topic also lists the content properties for each content model.</span></span> <span data-ttu-id="f1c63-108">Une propriété de contenu est une propriété qui est utilisée pour stocker le contenu de l’objet.</span><span class="sxs-lookup"><span data-stu-id="f1c63-108">A content property is a property that is used to store the content of the object.</span></span>  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a><span data-ttu-id="f1c63-109">Classes qui contiennent du contenu arbitraire</span><span class="sxs-lookup"><span data-stu-id="f1c63-109">Classes That Contain Arbitrary Content</span></span>  
 <span data-ttu-id="f1c63-110">Certaines commandes peuvent contenir un objet de n’importe quel type, comme une chaîne, un <xref:System.DateTime> objet ou un <xref:System.Windows.UIElement> conteneur pour des articles supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="f1c63-110">Some controls can contain an object of any type, such as a string, a <xref:System.DateTime> object, or a <xref:System.Windows.UIElement> that is a container for additional items.</span></span> <span data-ttu-id="f1c63-111">Par exemple, <xref:System.Windows.Controls.Button> un peut contenir une image et un texte; ou <xref:System.Windows.Controls.CheckBox> un peut contenir <xref:System.DateTime.Now%2A?displayProperty=nameWithType>la valeur de .</span><span class="sxs-lookup"><span data-stu-id="f1c63-111">For example, a <xref:System.Windows.Controls.Button> can contain an image and some text; or a <xref:System.Windows.Controls.CheckBox> can contain the value of <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.</span></span>  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="f1c63-112">proposent quatre classes qui contiennent du contenu arbitraire.</span><span class="sxs-lookup"><span data-stu-id="f1c63-112">has four classes that can contain arbitrary content.</span></span> <span data-ttu-id="f1c63-113">Le tableau suivant répertorie <xref:System.Windows.Controls.Control>les classes, qui héritent de .</span><span class="sxs-lookup"><span data-stu-id="f1c63-113">The following table lists the classes, which inherit from <xref:System.Windows.Controls.Control>.</span></span>  
  
|<span data-ttu-id="f1c63-114">Classe qui contient du contenu arbitraire</span><span class="sxs-lookup"><span data-stu-id="f1c63-114">Class that contains arbitrary content</span></span>|<span data-ttu-id="f1c63-115">Contenu</span><span class="sxs-lookup"><span data-stu-id="f1c63-115">Content</span></span>|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|<span data-ttu-id="f1c63-116">Objet arbitraire unique.</span><span class="sxs-lookup"><span data-stu-id="f1c63-116">A single arbitrary object.</span></span>|  
|<xref:System.Windows.Controls.HeaderedContentControl>|<span data-ttu-id="f1c63-117">En-tête et élément unique, correspondant tous deux à des objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="f1c63-117">A header and a single item, both of which are arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.ItemsControl>|<span data-ttu-id="f1c63-118">Collection d’objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="f1c63-118">A collection of arbitrary objects.</span></span>|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|<span data-ttu-id="f1c63-119">En-tête et collection d’éléments, correspondant tous deux à des objets arbitraires.</span><span class="sxs-lookup"><span data-stu-id="f1c63-119">A header and a collection of items, all of which are arbitrary objects.</span></span>|  
  
 <span data-ttu-id="f1c63-120">Les contrôles qui héritent de ces classes peuvent contenir le même type de contenu et traiter le contenu de la même façon.</span><span class="sxs-lookup"><span data-stu-id="f1c63-120">Controls that inherit from these classes can contain the same type of content and treat the content in the same way.</span></span> <span data-ttu-id="f1c63-121">L’illustration suivante montre un contrôle de chaque modèle de contenu qui contient une image et un texte :</span><span class="sxs-lookup"><span data-stu-id="f1c63-121">The following illustration shows one control from each content model that contains an image and some text:</span></span>  
  
 ![Capture d’écran qui montre quatre contrôles différents, un de chaque modèle de contenu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a><span data-ttu-id="f1c63-123">Contrôles qui contiennent un objet arbitraire unique</span><span class="sxs-lookup"><span data-stu-id="f1c63-123">Controls That Contain a Single Arbitrary Object</span></span>  
 <span data-ttu-id="f1c63-124">La <xref:System.Windows.Controls.ContentControl> classe contient un seul morceau de contenu arbitraire.</span><span class="sxs-lookup"><span data-stu-id="f1c63-124">The <xref:System.Windows.Controls.ContentControl> class contains a single piece of arbitrary content.</span></span> <span data-ttu-id="f1c63-125">Sa propriété <xref:System.Windows.Controls.ContentControl.Content%2A>de contenu est .</span><span class="sxs-lookup"><span data-stu-id="f1c63-125">Its content property is <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="f1c63-126">Les contrôles suivants <xref:System.Windows.Controls.ContentControl> héritent de son modèle de contenu et l’utilisent :</span><span class="sxs-lookup"><span data-stu-id="f1c63-126">The following controls inherit from <xref:System.Windows.Controls.ContentControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="f1c63-127">L’illustration suivante montre <xref:System.Windows.Controls.ContentControl.Content%2A> quatre boutons dont l’on <xref:System.Windows.Shapes.Rectangle>met une <xref:System.Windows.Controls.Panel> ficelle, <xref:System.Windows.Shapes.Ellipse> un <xref:System.Windows.Controls.TextBlock> <xref:System.DateTime> objet, un , et un qui contient un et un :</span><span class="sxs-lookup"><span data-stu-id="f1c63-127">The following illustration shows four buttons whose <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a string, a <xref:System.DateTime> object, a <xref:System.Windows.Shapes.Rectangle>, and a <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>:</span></span>  
  
 ![Capture d’écran qui affiche quatre boutons avec différents types de contenu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 <span data-ttu-id="f1c63-129">Pour un exemple de <xref:System.Windows.Controls.ContentControl.Content%2A> la façon <xref:System.Windows.Controls.ContentControl>de définir la propriété, voir .</span><span class="sxs-lookup"><span data-stu-id="f1c63-129">For an example of how to set the <xref:System.Windows.Controls.ContentControl.Content%2A> property, see <xref:System.Windows.Controls.ContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a><span data-ttu-id="f1c63-130">Contrôles qui contiennent un en-tête et un objet arbitraire unique</span><span class="sxs-lookup"><span data-stu-id="f1c63-130">Controls That Contain a Header and a Single Arbitrary Object</span></span>  
 <span data-ttu-id="f1c63-131">La <xref:System.Windows.Controls.HeaderedContentControl> classe hérite et affiche le <xref:System.Windows.Controls.ContentControl> contenu avec un en-tête.</span><span class="sxs-lookup"><span data-stu-id="f1c63-131">The <xref:System.Windows.Controls.HeaderedContentControl> class inherits from <xref:System.Windows.Controls.ContentControl> and displays content with a header.</span></span> <span data-ttu-id="f1c63-132">Il hérite de <xref:System.Windows.Controls.ContentControl.Content%2A>la <xref:System.Windows.Controls.ContentControl> propriété de <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> contenu, , <xref:System.Object>et définit la propriété qui est de type ; par conséquent, les deux peuvent être un objet arbitraire.</span><span class="sxs-lookup"><span data-stu-id="f1c63-132">It inherits the content property, <xref:System.Windows.Controls.ContentControl.Content%2A>, from <xref:System.Windows.Controls.ContentControl> and defines the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> property that is of type <xref:System.Object>; therefore, both can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="f1c63-133">Les contrôles suivants <xref:System.Windows.Controls.HeaderedContentControl> héritent de son modèle de contenu et l’utilisent :</span><span class="sxs-lookup"><span data-stu-id="f1c63-133">The following controls inherit from <xref:System.Windows.Controls.HeaderedContentControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 <span data-ttu-id="f1c63-134">L’illustration suivante <xref:System.Windows.Controls.TabItem> montre deux objets.</span><span class="sxs-lookup"><span data-stu-id="f1c63-134">The following illustration shows two <xref:System.Windows.Controls.TabItem> objects.</span></span> <span data-ttu-id="f1c63-135">Le <xref:System.Windows.Controls.TabItem> premier <xref:System.Windows.UIElement> a <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> des <xref:System.Windows.Controls.ContentControl.Content%2A>objets comme le et le .</span><span class="sxs-lookup"><span data-stu-id="f1c63-135">The first <xref:System.Windows.Controls.TabItem> has <xref:System.Windows.UIElement> objects as the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span> <span data-ttu-id="f1c63-136">Le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> est réglé <xref:System.Windows.Controls.StackPanel> à <xref:System.Windows.Shapes.Ellipse> un <xref:System.Windows.Controls.TextBlock>qui contient un et a .</span><span class="sxs-lookup"><span data-stu-id="f1c63-136">The <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span> <span data-ttu-id="f1c63-137">Le <xref:System.Windows.Controls.ContentControl.Content%2A> est réglé <xref:System.Windows.Controls.StackPanel> à <xref:System.Windows.Controls.TextBlock> un <xref:System.Windows.Controls.Label>qui contient a et a .</span><span class="sxs-lookup"><span data-stu-id="f1c63-137">The <xref:System.Windows.Controls.ContentControl.Content%2A> is set to a <xref:System.Windows.Controls.StackPanel> that contains a <xref:System.Windows.Controls.TextBlock> and a <xref:System.Windows.Controls.Label>.</span></span> <span data-ttu-id="f1c63-138">Le <xref:System.Windows.Controls.TabItem> second a une <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> chaîne <xref:System.Windows.Controls.TextBlock> dans <xref:System.Windows.Controls.ContentControl.Content%2A>le et un dans le .</span><span class="sxs-lookup"><span data-stu-id="f1c63-138">The second <xref:System.Windows.Controls.TabItem> has a string in the <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> and a <xref:System.Windows.Controls.TextBlock> in the <xref:System.Windows.Controls.ContentControl.Content%2A>.</span></span>  
  
 ![TabControl qui utilise différents types dans la propriété Header.](./media/wpf-content-model/control-content-model-tab.png)  
  
 <span data-ttu-id="f1c63-140">Pour un exemple de <xref:System.Windows.Controls.TabItem> la <xref:System.Windows.Controls.HeaderedContentControl>façon de créer des objets, voir .</span><span class="sxs-lookup"><span data-stu-id="f1c63-140">For an example of how to create <xref:System.Windows.Controls.TabItem> objects, see <xref:System.Windows.Controls.HeaderedContentControl>.</span></span>  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a><span data-ttu-id="f1c63-141">Contrôles qui contiennent une collection d’objets arbitraires</span><span class="sxs-lookup"><span data-stu-id="f1c63-141">Controls That Contain a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="f1c63-142">La <xref:System.Windows.Controls.ItemsControl> classe hérite de <xref:System.Windows.Controls.Control> plusieurs éléments, tels que des cordes, des objets ou d’autres éléments.</span><span class="sxs-lookup"><span data-stu-id="f1c63-142">The <xref:System.Windows.Controls.ItemsControl> class inherits from <xref:System.Windows.Controls.Control> and can contain multiple items, such as strings, objects, or other elements.</span></span> <span data-ttu-id="f1c63-143">Ses propriétés <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A>de contenu sont et .</span><span class="sxs-lookup"><span data-stu-id="f1c63-143">Its content properties are <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> and <xref:System.Windows.Controls.ItemsControl.Items%2A>.</span></span> <span data-ttu-id="f1c63-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>est généralement utilisé pour <xref:System.Windows.Controls.ItemsControl> remplir le avec une collecte de données.</span><span class="sxs-lookup"><span data-stu-id="f1c63-144"><xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> is typically used to populate the <xref:System.Windows.Controls.ItemsControl> with a data collection.</span></span> <span data-ttu-id="f1c63-145">Si vous ne voulez pas utiliser une <xref:System.Windows.Controls.ItemsControl>collection pour remplir le <xref:System.Windows.Controls.ItemsControl.Items%2A> , vous pouvez ajouter des éléments en utilisant la propriété.</span><span class="sxs-lookup"><span data-stu-id="f1c63-145">If you do not want to use a collection to populate the <xref:System.Windows.Controls.ItemsControl>, you can add items by using the <xref:System.Windows.Controls.ItemsControl.Items%2A> property.</span></span>  
  
 <span data-ttu-id="f1c63-146">Les contrôles suivants <xref:System.Windows.Controls.ItemsControl> héritent de son modèle de contenu et l’utilisent :</span><span class="sxs-lookup"><span data-stu-id="f1c63-146">The following controls inherit from <xref:System.Windows.Controls.ItemsControl> and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="f1c63-147">L’illustration suivante <xref:System.Windows.Controls.ListBox> montre un qui contient ces types d’éléments:</span><span class="sxs-lookup"><span data-stu-id="f1c63-147">The following illustration shows a <xref:System.Windows.Controls.ListBox> that contains these types of items:</span></span>  
  
- <span data-ttu-id="f1c63-148">Une chaîne.</span><span class="sxs-lookup"><span data-stu-id="f1c63-148">A string.</span></span>  
  
- <span data-ttu-id="f1c63-149">Objet <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="f1c63-149">A <xref:System.DateTime> object.</span></span>  
  
- <span data-ttu-id="f1c63-150"><xref:System.Windows.UIElement>.</span><span class="sxs-lookup"><span data-stu-id="f1c63-150">A <xref:System.Windows.UIElement>.</span></span>  
  
- <span data-ttu-id="f1c63-151">A <xref:System.Windows.Controls.Panel> qui <xref:System.Windows.Shapes.Ellipse> contient <xref:System.Windows.Controls.TextBlock>un et un .</span><span class="sxs-lookup"><span data-stu-id="f1c63-151">A <xref:System.Windows.Controls.Panel> that contains an <xref:System.Windows.Shapes.Ellipse> and a <xref:System.Windows.Controls.TextBlock>.</span></span>  
  
 ![Capture d’écran qui montre une ListBox avec quatre types de contenu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a><span data-ttu-id="f1c63-153">Contrôles qui contiennent un en-tête et une collection d’objets arbitraires</span><span class="sxs-lookup"><span data-stu-id="f1c63-153">Controls That Contain a Header and a Collection of Arbitrary Objects</span></span>  
 <span data-ttu-id="f1c63-154">La <xref:System.Windows.Controls.HeaderedItemsControl> classe hérite de <xref:System.Windows.Controls.ItemsControl> plusieurs éléments, tels que des cordes, des objets ou d’autres éléments, et un en-tête.</span><span class="sxs-lookup"><span data-stu-id="f1c63-154">The <xref:System.Windows.Controls.HeaderedItemsControl> class inherits from <xref:System.Windows.Controls.ItemsControl> and can contain multiple items, such as strings, objects, or other elements, and a header.</span></span> <span data-ttu-id="f1c63-155">Il hérite <xref:System.Windows.Controls.ItemsControl> des <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>propriétés <xref:System.Windows.Controls.ItemsControl.Items%2A>de contenu, <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> et , et il définit la propriété qui peut être un objet arbitraire.</span><span class="sxs-lookup"><span data-stu-id="f1c63-155">It inherits the <xref:System.Windows.Controls.ItemsControl> content properties, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>, and <xref:System.Windows.Controls.ItemsControl.Items%2A>, and it defines the <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> property that can be an arbitrary object.</span></span>  
  
 <span data-ttu-id="f1c63-156">Les contrôles suivants <xref:System.Windows.Controls.HeaderedItemsControl> héritent de son modèle de contenu et l’utilisent :</span><span class="sxs-lookup"><span data-stu-id="f1c63-156">The following controls inherit from <xref:System.Windows.Controls.HeaderedItemsControl> and use its content model:</span></span>  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a><span data-ttu-id="f1c63-157">Classes qui contiennent une collection d’objets UIElement</span><span class="sxs-lookup"><span data-stu-id="f1c63-157">Classes That Contain a Collection of UIElement Objects</span></span>  
 <span data-ttu-id="f1c63-158">La <xref:System.Windows.Controls.Panel> classe positionne <xref:System.Windows.UIElement> et arrange les objets pour enfants.</span><span class="sxs-lookup"><span data-stu-id="f1c63-158">The <xref:System.Windows.Controls.Panel> class positions and arranges child <xref:System.Windows.UIElement> objects.</span></span> <span data-ttu-id="f1c63-159">Sa propriété <xref:System.Windows.Controls.Panel.Children%2A>de contenu est .</span><span class="sxs-lookup"><span data-stu-id="f1c63-159">Its content property is <xref:System.Windows.Controls.Panel.Children%2A>.</span></span>  
  
 <span data-ttu-id="f1c63-160">Les classes suivantes <xref:System.Windows.Controls.Panel> héritent de la classe et utilisent son modèle de contenu :</span><span class="sxs-lookup"><span data-stu-id="f1c63-160">The following classes inherit from the <xref:System.Windows.Controls.Panel> class and use its content model:</span></span>  
  
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
  
 <span data-ttu-id="f1c63-161">Pour plus d’informations, consultez la page [Vue d’ensemble de Panel](panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1c63-161">For more information, see [Panels Overview](panels-overview.md).</span></span>  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a><span data-ttu-id="f1c63-162">Classes qui affectent l’apparence d’un UIElement</span><span class="sxs-lookup"><span data-stu-id="f1c63-162">Classes That Affect the Appearance of a UIElement</span></span>  
 <span data-ttu-id="f1c63-163">La <xref:System.Windows.Controls.Decorator> classe applique des effets visuels <xref:System.Windows.UIElement>sur ou autour d’un seul enfant.</span><span class="sxs-lookup"><span data-stu-id="f1c63-163">The <xref:System.Windows.Controls.Decorator> class applies visual effects onto or around a single child <xref:System.Windows.UIElement>.</span></span> <span data-ttu-id="f1c63-164">Sa propriété <xref:System.Windows.Controls.Decorator.Child%2A>de contenu est .</span><span class="sxs-lookup"><span data-stu-id="f1c63-164">Its content property is <xref:System.Windows.Controls.Decorator.Child%2A>.</span></span> <span data-ttu-id="f1c63-165">Les classes suivantes <xref:System.Windows.Controls.Decorator> héritent de son modèle de contenu et utilisent :</span><span class="sxs-lookup"><span data-stu-id="f1c63-165">The following classes inherit from <xref:System.Windows.Controls.Decorator> and use its content model:</span></span>  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 <span data-ttu-id="f1c63-166">L’illustration suivante <xref:System.Windows.Controls.TextBox> montre un qui a <xref:System.Windows.Controls.Border> (est décoré avec) un autour d’elle.</span><span class="sxs-lookup"><span data-stu-id="f1c63-166">The following illustration shows a <xref:System.Windows.Controls.TextBox> that has (is decorated with) a <xref:System.Windows.Controls.Border> around it.</span></span>  
  
 <span data-ttu-id="f1c63-167">![TextBox avec bordure noire](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span><span class="sxs-lookup"><span data-stu-id="f1c63-167">![TextBox with black border](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")</span></span>  
<span data-ttu-id="f1c63-168">TextBlock avec une bordure</span><span class="sxs-lookup"><span data-stu-id="f1c63-168">TextBlock that has a Border</span></span>  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a><span data-ttu-id="f1c63-169">Classes qui fournissent des commentaires visuels sur un UIElement</span><span class="sxs-lookup"><span data-stu-id="f1c63-169">Classes That Provide Visual Feedback About a UIElement</span></span>  
 <span data-ttu-id="f1c63-170">La <xref:System.Windows.Documents.Adorner> classe fournit des indices visuels à un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="f1c63-170">The <xref:System.Windows.Documents.Adorner> class provides visual cues to a user.</span></span> <span data-ttu-id="f1c63-171">Par exemple, <xref:System.Windows.Documents.Adorner> utilisez un pour ajouter des poignées fonctionnelles aux éléments ou fournir des informations d’état sur un contrôle.</span><span class="sxs-lookup"><span data-stu-id="f1c63-171">For example, use an <xref:System.Windows.Documents.Adorner> to add functional handles to elements or provide state information about a control.</span></span> <span data-ttu-id="f1c63-172">La <xref:System.Windows.Documents.Adorner> classe fournit un cadre afin que vous puissiez créer vos propres adorateurs.</span><span class="sxs-lookup"><span data-stu-id="f1c63-172">The <xref:System.Windows.Documents.Adorner> class provides a framework so that you can create your own adorners.</span></span> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="f1c63-173">ne fournit aucun ornement implémenté.</span><span class="sxs-lookup"><span data-stu-id="f1c63-173">does not provide any implemented adorners.</span></span> <span data-ttu-id="f1c63-174">Pour plus d’informations, consultez [Vue d’ensemble des ornements](adorners-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1c63-174">For more information, see [Adorners Overview](adorners-overview.md).</span></span>  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a><span data-ttu-id="f1c63-175">Classes qui permettent aux utilisateurs d’entrer du texte</span><span class="sxs-lookup"><span data-stu-id="f1c63-175">Classes That Enable Users to Enter Text</span></span>  
 <span data-ttu-id="f1c63-176">WPF fournit trois principaux contrôles qui permettent aux utilisateurs d’entrer du texte.</span><span class="sxs-lookup"><span data-stu-id="f1c63-176">WPF provides three primary controls that enable users to enter text.</span></span> <span data-ttu-id="f1c63-177">Chaque contrôle affiche le texte de manière différente.</span><span class="sxs-lookup"><span data-stu-id="f1c63-177">Each control displays the text differently.</span></span> <span data-ttu-id="f1c63-178">Le tableau suivant répertorie ces trois contrôles liés au texte, leurs fonctions lors de l’affichage du texte et leurs propriétés qui contiennent le texte du contrôle.</span><span class="sxs-lookup"><span data-stu-id="f1c63-178">The following table lists these three text-related controls, their capabilities when they display text, and their properties that contain the control's text.</span></span>  
  
|<span data-ttu-id="f1c63-179">Control</span><span class="sxs-lookup"><span data-stu-id="f1c63-179">Control</span></span>|<span data-ttu-id="f1c63-180">Texte affiché en tant que</span><span class="sxs-lookup"><span data-stu-id="f1c63-180">Text is displayed as</span></span>|<span data-ttu-id="f1c63-181">Propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="f1c63-181">Content property</span></span>|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|<span data-ttu-id="f1c63-182">Texte brut</span><span class="sxs-lookup"><span data-stu-id="f1c63-182">Plain text</span></span>|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|<span data-ttu-id="f1c63-183">Texte mis en forme</span><span class="sxs-lookup"><span data-stu-id="f1c63-183">Formatted text</span></span>|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|<span data-ttu-id="f1c63-184">Texte masqué (les caractères sont masqués)</span><span class="sxs-lookup"><span data-stu-id="f1c63-184">Hidden text (characters are masked)</span></span>|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a><span data-ttu-id="f1c63-185">Classes qui affichent votre texte</span><span class="sxs-lookup"><span data-stu-id="f1c63-185">Classes That Display Your Text</span></span>  
 <span data-ttu-id="f1c63-186">Plusieurs classes peuvent être utilisées pour afficher du texte brut ou mis en forme.</span><span class="sxs-lookup"><span data-stu-id="f1c63-186">Several classes can be used to display plain or formatted text.</span></span> <span data-ttu-id="f1c63-187">Vous pouvez <xref:System.Windows.Controls.TextBlock> utiliser pour afficher de petites quantités de texte.</span><span class="sxs-lookup"><span data-stu-id="f1c63-187">You can use <xref:System.Windows.Controls.TextBlock> to display small amounts of text.</span></span> <span data-ttu-id="f1c63-188">Si vous souhaitez afficher de grandes <xref:System.Windows.Controls.FlowDocumentReader>quantités de texte, utilisez le , <xref:System.Windows.Controls.FlowDocumentPageViewer>ou <xref:System.Windows.Controls.FlowDocumentScrollViewer> les contrôles.</span><span class="sxs-lookup"><span data-stu-id="f1c63-188">If you want to display large amounts of text, use the <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, or <xref:System.Windows.Controls.FlowDocumentScrollViewer> controls.</span></span>  
  
 <span data-ttu-id="f1c63-189">Le <xref:System.Windows.Controls.TextBlock> a deux <xref:System.Windows.Controls.TextBlock.Text%2A> propriétés de contenu: et <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1c63-189">The <xref:System.Windows.Controls.TextBlock> has two content properties: <xref:System.Windows.Controls.TextBlock.Text%2A> and <xref:System.Windows.Controls.TextBlock.Inlines%2A>.</span></span> <span data-ttu-id="f1c63-190">Lorsque vous souhaitez afficher du texte qui <xref:System.Windows.Controls.TextBlock.Text%2A> utilise un formatage cohérent, la propriété est souvent votre meilleur choix.</span><span class="sxs-lookup"><span data-stu-id="f1c63-190">When you want to display text that uses consistent formatting, the <xref:System.Windows.Controls.TextBlock.Text%2A> property is often your best choice.</span></span> <span data-ttu-id="f1c63-191">Si vous prévoyez d’utiliser différents formatages tout au long du texte, utilisez la <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriété.</span><span class="sxs-lookup"><span data-stu-id="f1c63-191">If you plan to use different formatting throughout the text, use the <xref:System.Windows.Controls.TextBlock.Inlines%2A> property.</span></span> <span data-ttu-id="f1c63-192">La <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriété est <xref:System.Windows.Documents.Inline> une collection d’objets, qui spécifient comment formater le texte.</span><span class="sxs-lookup"><span data-stu-id="f1c63-192">The <xref:System.Windows.Controls.TextBlock.Inlines%2A> property is a collection of <xref:System.Windows.Documents.Inline> objects, which specify how to format text.</span></span>  
  
 <span data-ttu-id="f1c63-193">Le tableau suivant répertorie la propriété de contenu pour <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, et <xref:System.Windows.Controls.FlowDocumentScrollViewer> les classes.</span><span class="sxs-lookup"><span data-stu-id="f1c63-193">The following table lists the content property for <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, and <xref:System.Windows.Controls.FlowDocumentScrollViewer> classes.</span></span>  
  
|<span data-ttu-id="f1c63-194">Control</span><span class="sxs-lookup"><span data-stu-id="f1c63-194">Control</span></span>|<span data-ttu-id="f1c63-195">Propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="f1c63-195">Content property</span></span>|<span data-ttu-id="f1c63-196">Type de propriété de contenu</span><span class="sxs-lookup"><span data-stu-id="f1c63-196">Content property type</span></span>|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|<span data-ttu-id="f1c63-197">Document</span><span class="sxs-lookup"><span data-stu-id="f1c63-197">Document</span></span>|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|<span data-ttu-id="f1c63-198">Document</span><span class="sxs-lookup"><span data-stu-id="f1c63-198">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|<span data-ttu-id="f1c63-199">Document</span><span class="sxs-lookup"><span data-stu-id="f1c63-199">Document</span></span>|<xref:System.Windows.Documents.FlowDocument>|  
  
 <span data-ttu-id="f1c63-200">Les <xref:System.Windows.Documents.FlowDocument> impléments de l’interface; <xref:System.Windows.Documents.IDocumentPaginatorSource> par conséquent, les trois <xref:System.Windows.Documents.FlowDocument> classes peuvent prendre un contenu comme.</span><span class="sxs-lookup"><span data-stu-id="f1c63-200">The <xref:System.Windows.Documents.FlowDocument> implements the <xref:System.Windows.Documents.IDocumentPaginatorSource> interface; therefore, all three classes can take a <xref:System.Windows.Documents.FlowDocument> as content.</span></span>  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a><span data-ttu-id="f1c63-201">Classes de mise en forme du texte</span><span class="sxs-lookup"><span data-stu-id="f1c63-201">Classes That Format Your Text</span></span>  
 <span data-ttu-id="f1c63-202"><xref:System.Windows.Documents.TextElement>et ses classes connexes vous permettent de formater le texte.</span><span class="sxs-lookup"><span data-stu-id="f1c63-202"><xref:System.Windows.Documents.TextElement> and its related classes allow you to format text.</span></span> <span data-ttu-id="f1c63-203"><xref:System.Windows.Documents.TextElement>objets contiennent et <xref:System.Windows.Controls.TextBlock> formater le texte et <xref:System.Windows.Documents.FlowDocument> les objets.</span><span class="sxs-lookup"><span data-stu-id="f1c63-203"><xref:System.Windows.Documents.TextElement> objects contain and format text in <xref:System.Windows.Controls.TextBlock> and <xref:System.Windows.Documents.FlowDocument> objects.</span></span> <span data-ttu-id="f1c63-204">Les deux principaux <xref:System.Windows.Documents.TextElement> types <xref:System.Windows.Documents.Block> d’objets sont des éléments et des <xref:System.Windows.Documents.Inline> éléments.</span><span class="sxs-lookup"><span data-stu-id="f1c63-204">The two primary types of <xref:System.Windows.Documents.TextElement> objects are <xref:System.Windows.Documents.Block> elements and <xref:System.Windows.Documents.Inline> elements.</span></span> <span data-ttu-id="f1c63-205">Un <xref:System.Windows.Documents.Block> élément représente un bloc de texte, tel qu’un paragraphe ou une liste.</span><span class="sxs-lookup"><span data-stu-id="f1c63-205">A <xref:System.Windows.Documents.Block> element represents a block of text, such as a paragraph or list.</span></span> <span data-ttu-id="f1c63-206">Un <xref:System.Windows.Documents.Inline> élément représente une partie du texte dans un bloc.</span><span class="sxs-lookup"><span data-stu-id="f1c63-206">An <xref:System.Windows.Documents.Inline> element represents a portion of text in a block.</span></span> <span data-ttu-id="f1c63-207">De <xref:System.Windows.Documents.Inline> nombreuses classes spécifient le formatage du texte auquel elles sont appliquées.</span><span class="sxs-lookup"><span data-stu-id="f1c63-207">Many <xref:System.Windows.Documents.Inline> classes specify formatting for the text to which they are applied.</span></span> <span data-ttu-id="f1c63-208">Chacun <xref:System.Windows.Documents.TextElement> a son propre modèle de contenu.</span><span class="sxs-lookup"><span data-stu-id="f1c63-208">Each <xref:System.Windows.Documents.TextElement> has its own content model.</span></span> <span data-ttu-id="f1c63-209">Pour plus d’informations, consultez la page [Vue d’ensemble du modèle de contenu de TextElement](../advanced/textelement-content-model-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1c63-209">For more information, see the [TextElement Content Model Overview](../advanced/textelement-content-model-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1c63-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1c63-210">See also</span></span>

- [<span data-ttu-id="f1c63-211">Avancé</span><span class="sxs-lookup"><span data-stu-id="f1c63-211">Advanced</span></span>](../advanced/index.md)
