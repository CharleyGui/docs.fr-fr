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
# <a name="wpf-content-model"></a>Modèle de contenu WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est une plateforme de présentation qui fournit de nombreux contrôles et des éléments de type contrôle dont le principal objectif est d’afficher différents types de contenu. Pour déterminer le contrôle à utiliser ou le contrôle d’où dériver, vous devez comprendre les types d’objets qu’un contrôle donné peut afficher de manière optimale.  
  
 Cette rubrique présente de manière synthétique le modèle de contenu pour les contrôles et les éléments de type contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le modèle de contenu décrit le contenu qui peut être utilisé dans un contrôle. Cette rubrique répertorie également les propriétés de contenu pour chaque modèle de contenu. Une propriété de contenu est une propriété qui est utilisée pour stocker le contenu de l’objet.  

<a name="classes_that_contain_arbitrary_content"></a>   
## <a name="classes-that-contain-arbitrary-content"></a>Classes qui contiennent du contenu arbitraire  
 Certains contrôles peuvent contenir un objet de tout type, tel qu’une chaîne, un objet <xref:System.DateTime> ou un <xref:System.Windows.UIElement> qui est un conteneur pour des éléments supplémentaires. Par exemple, un <xref:System.Windows.Controls.Button> peut contenir une image et du texte. ou un <xref:System.Windows.Controls.CheckBox> peut contenir la valeur de <xref:System.DateTime.Now%2A?displayProperty=nameWithType>.  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proposent quatre classes qui contiennent du contenu arbitraire. Le tableau suivant répertorie les classes, qui héritent de <xref:System.Windows.Controls.Control>.  
  
|Classe qui contient du contenu arbitraire|Contenu|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Objet arbitraire unique.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|En-tête et élément unique, correspondant tous deux à des objets arbitraires.|  
|<xref:System.Windows.Controls.ItemsControl>|Collection d’objets arbitraires.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|En-tête et collection d’éléments, correspondant tous deux à des objets arbitraires.|  
  
 Les contrôles qui héritent de ces classes peuvent contenir le même type de contenu et traiter le contenu de la même façon. L’illustration suivante montre un contrôle à partir de chaque modèle de contenu qui contient une image et du texte :  
  
 ![Capture d’écran montrant quatre contrôles différents, un à partir de chaque modèle de contenu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Contrôles qui contiennent un objet arbitraire unique  
 La classe <xref:System.Windows.Controls.ContentControl> contient un seul élément de contenu arbitraire. Sa propriété de contenu est <xref:System.Windows.Controls.ContentControl.Content%2A>. Les contrôles suivants héritent de <xref:System.Windows.Controls.ContentControl> et utilisent son modèle de contenu :  
  
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
  
 L’illustration suivante montre quatre boutons dont la <xref:System.Windows.Controls.ContentControl.Content%2A> est définie sur une chaîne, un objet <xref:System.DateTime>, un <xref:System.Windows.Shapes.Rectangle>et un <xref:System.Windows.Controls.Panel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>:  
  
 ![Capture d’écran montrant quatre boutons avec différents types de contenu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Pour obtenir un exemple de définition de la propriété <xref:System.Windows.Controls.ContentControl.Content%2A>, consultez <xref:System.Windows.Controls.ContentControl>.  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Contrôles qui contiennent un en-tête et un objet arbitraire unique  
 La classe <xref:System.Windows.Controls.HeaderedContentControl> hérite de <xref:System.Windows.Controls.ContentControl> et affiche le contenu avec un en-tête. Elle hérite de la propriété de contenu, <xref:System.Windows.Controls.ContentControl.Content%2A>, à partir de <xref:System.Windows.Controls.ContentControl> et définit la propriété <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> qui est de type <xref:System.Object>; par conséquent, les deux peuvent être un objet arbitraire.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedContentControl> et utilisent son modèle de contenu :  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 L’illustration suivante montre deux objets <xref:System.Windows.Controls.TabItem>. La première <xref:System.Windows.Controls.TabItem> a des objets <xref:System.Windows.UIElement> comme <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et le <xref:System.Windows.Controls.ContentControl.Content%2A>. La <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> est définie sur une <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>. La <xref:System.Windows.Controls.ContentControl.Content%2A> est définie sur une <xref:System.Windows.Controls.StackPanel> qui contient un <xref:System.Windows.Controls.TextBlock> et un <xref:System.Windows.Controls.Label>. La deuxième <xref:System.Windows.Controls.TabItem> a une chaîne dans le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et un <xref:System.Windows.Controls.TextBlock> dans le <xref:System.Windows.Controls.ContentControl.Content%2A>.  
  
 ![TabControl qui utilise différents types dans la propriété d’en-tête.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Pour obtenir un exemple de création d’objets <xref:System.Windows.Controls.TabItem>, consultez <xref:System.Windows.Controls.HeaderedContentControl>.  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Contrôles qui contiennent une collection d’objets arbitraires  
 La classe <xref:System.Windows.Controls.ItemsControl> hérite de <xref:System.Windows.Controls.Control> et peut contenir plusieurs éléments, tels que des chaînes, des objets ou d’autres éléments. Ses propriétés de contenu sont <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> et <xref:System.Windows.Controls.ItemsControl.Items%2A>. <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> est généralement utilisé pour remplir le <xref:System.Windows.Controls.ItemsControl> avec une collection de données. Si vous ne souhaitez pas utiliser de collection pour remplir le <xref:System.Windows.Controls.ItemsControl>, vous pouvez ajouter des éléments à l’aide de la propriété <xref:System.Windows.Controls.ItemsControl.Items%2A>.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.ItemsControl> et utilisent son modèle de contenu :  
  
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
  
 L’illustration suivante montre une <xref:System.Windows.Controls.ListBox> qui contient ces types d’éléments :  
  
- Chaîne.  
  
- Objet <xref:System.DateTime>.  
  
- <xref:System.Windows.UIElement>  
  
- <xref:System.Windows.Controls.Panel> qui contient un <xref:System.Windows.Shapes.Ellipse> et un <xref:System.Windows.Controls.TextBlock>.  
  
 ![Capture d’écran montrant un contrôle ListBox avec quatre types de contenu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Contrôles qui contiennent un en-tête et une collection d’objets arbitraires  
 La classe <xref:System.Windows.Controls.HeaderedItemsControl> hérite de <xref:System.Windows.Controls.ItemsControl> et peut contenir plusieurs éléments, tels que des chaînes, des objets ou d’autres éléments, ainsi qu’un en-tête. Elle hérite de la <xref:System.Windows.Controls.ItemsControl> propriétés de contenu, <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>et <xref:System.Windows.Controls.ItemsControl.Items%2A>, et définit la propriété <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> qui peut être un objet arbitraire.  
  
 Les contrôles suivants héritent de <xref:System.Windows.Controls.HeaderedItemsControl> et utilisent son modèle de contenu :  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Classes qui contiennent une collection d’objets UIElement  
 La classe <xref:System.Windows.Controls.Panel> positionne et organise les objets <xref:System.Windows.UIElement> enfants. Sa propriété de contenu est <xref:System.Windows.Controls.Panel.Children%2A>.  
  
 Les classes suivantes héritent de la classe <xref:System.Windows.Controls.Panel> et utilisent son modèle de contenu :  
  
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
  
 Pour plus d’informations, consultez la page [Vue d’ensemble de Panel](panels-overview.md).  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## <a name="classes-that-affect-the-appearance-of-a-uielement"></a>Classes qui affectent l’apparence d’un UIElement  
 La classe <xref:System.Windows.Controls.Decorator> applique des effets visuels sur ou autour d’un <xref:System.Windows.UIElement>enfant unique. Sa propriété de contenu est <xref:System.Windows.Controls.Decorator.Child%2A>. Les classes suivantes héritent de <xref:System.Windows.Controls.Decorator> et utilisent son modèle de contenu :  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 L’illustration suivante montre un <xref:System.Windows.Controls.TextBox> qui a (est décoré avec) un <xref:System.Windows.Controls.Border> autour de lui.  
  
 ![TextBox avec bordure noire](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock avec une bordure  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Classes qui fournissent des commentaires visuels sur un UIElement  
 La classe <xref:System.Windows.Documents.Adorner> fournit des signaux visuels à un utilisateur. Par exemple, utilisez un <xref:System.Windows.Documents.Adorner> pour ajouter des handles fonctionnels à des éléments ou pour fournir des informations d’État sur un contrôle. La classe <xref:System.Windows.Documents.Adorner> fournit une infrastructure qui vous permet de créer vos propres ornements. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne fournit aucun ornement implémenté. Pour plus d’informations, consultez [Vue d’ensemble des ornements](adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## <a name="classes-that-enable-users-to-enter-text"></a>Classes qui permettent aux utilisateurs d’entrer du texte  
 WPF fournit trois principaux contrôles qui permettent aux utilisateurs d’entrer du texte. Chaque contrôle affiche le texte de manière différente. Le tableau suivant répertorie ces trois contrôles liés au texte, leurs fonctions lors de l’affichage du texte et leurs propriétés qui contiennent le texte du contrôle.  
  
|Contrôle|Texte affiché en tant que|Propriété de contenu|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Texte brut|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Texte mis en forme|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Texte masqué (les caractères sont masqués)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## <a name="classes-that-display-your-text"></a>Classes qui affichent votre texte  
 Plusieurs classes peuvent être utilisées pour afficher du texte brut ou mis en forme. Vous pouvez utiliser <xref:System.Windows.Controls.TextBlock> pour afficher de petites quantités de texte. Si vous souhaitez afficher de grandes quantités de texte, utilisez les contrôles <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>ou <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
 La <xref:System.Windows.Controls.TextBlock> a deux propriétés de contenu : <xref:System.Windows.Controls.TextBlock.Text%2A> et <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Lorsque vous souhaitez afficher du texte qui utilise une mise en forme cohérente, la propriété <xref:System.Windows.Controls.TextBlock.Text%2A> est souvent le meilleur choix. Si vous envisagez d’utiliser une mise en forme différente dans tout le texte, utilisez la propriété <xref:System.Windows.Controls.TextBlock.Inlines%2A>. La propriété <xref:System.Windows.Controls.TextBlock.Inlines%2A> est une collection d’objets <xref:System.Windows.Documents.Inline>, qui spécifient comment mettre en forme le texte.  
  
 Le tableau suivant répertorie la propriété de contenu pour les classes <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>et <xref:System.Windows.Controls.FlowDocumentScrollViewer>.  
  
|Contrôle|Propriété de contenu|Type de propriété de contenu|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Document|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Document|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Document|<xref:System.Windows.Documents.FlowDocument>|  
  
 Le <xref:System.Windows.Documents.FlowDocument> implémente l’interface <xref:System.Windows.Documents.IDocumentPaginatorSource> ; par conséquent, les trois classes peuvent prendre une <xref:System.Windows.Documents.FlowDocument> en tant que contenu.  
  
<a name="classes_that_format_text"></a>   
## <a name="classes-that-format-your-text"></a>Classes de mise en forme du texte  
 <xref:System.Windows.Documents.TextElement> et ses classes connexes vous permettent de mettre en forme du texte. <xref:System.Windows.Documents.TextElement> objets contiennent et mettent en forme du texte dans des objets <xref:System.Windows.Controls.TextBlock> et <xref:System.Windows.Documents.FlowDocument>. Les deux principaux types d’objets <xref:System.Windows.Documents.TextElement> sont <xref:System.Windows.Documents.Block> éléments et <xref:System.Windows.Documents.Inline> éléments. Un élément <xref:System.Windows.Documents.Block> représente un bloc de texte, tel qu’un paragraphe ou une liste. Un élément <xref:System.Windows.Documents.Inline> représente une partie du texte d’un bloc. De nombreuses classes de <xref:System.Windows.Documents.Inline> spécifient la mise en forme du texte auquel elles sont appliquées. Chaque <xref:System.Windows.Documents.TextElement> possède son propre modèle de contenu. Pour plus d’informations, consultez la page [Vue d’ensemble du modèle de contenu de TextElement](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Avancé](../advanced/index.md)
