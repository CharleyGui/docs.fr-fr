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
# <a name="wpf-content-model"></a>Modèle de contenu WPF
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est une plateforme de présentation qui fournit de nombreux contrôles et des éléments de type contrôle dont le principal objectif est d’afficher différents types de contenu. Pour déterminer le contrôle à utiliser ou le contrôle d’où dériver, vous devez comprendre les types d’objets qu’un contrôle donné peut afficher de manière optimale.  
  
 Cette rubrique présente de manière synthétique le modèle de contenu pour les contrôles et les éléments de type contrôle [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Le modèle de contenu décrit le contenu qui peut être utilisé dans un contrôle. Cette rubrique répertorie également les propriétés de contenu pour chaque modèle de contenu. Une propriété de contenu est une propriété qui est utilisée pour stocker le contenu de l’objet.  

<a name="classes_that_contain_arbitrary_content"></a>
## <a name="classes-that-contain-arbitrary-content"></a>Classes qui contiennent du contenu arbitraire  
 Certaines commandes peuvent contenir un objet de n’importe quel type, comme une chaîne, un <xref:System.DateTime> objet ou un <xref:System.Windows.UIElement> conteneur pour des articles supplémentaires. Par exemple, <xref:System.Windows.Controls.Button> un peut contenir une image et un texte; ou <xref:System.Windows.Controls.CheckBox> un peut contenir <xref:System.DateTime.Now%2A?displayProperty=nameWithType>la valeur de .  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] proposent quatre classes qui contiennent du contenu arbitraire. Le tableau suivant répertorie <xref:System.Windows.Controls.Control>les classes, qui héritent de .  
  
|Classe qui contient du contenu arbitraire|Contenu|  
|-------------------------------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|Objet arbitraire unique.|  
|<xref:System.Windows.Controls.HeaderedContentControl>|En-tête et élément unique, correspondant tous deux à des objets arbitraires.|  
|<xref:System.Windows.Controls.ItemsControl>|Collection d’objets arbitraires.|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|En-tête et collection d’éléments, correspondant tous deux à des objets arbitraires.|  
  
 Les contrôles qui héritent de ces classes peuvent contenir le même type de contenu et traiter le contenu de la même façon. L’illustration suivante montre un contrôle de chaque modèle de contenu qui contient une image et un texte :  
  
 ![Capture d’écran qui montre quatre contrôles différents, un de chaque modèle de contenu.](./media/wpf-content-model/control-content-model-image-text.png)  
  
### <a name="controls-that-contain-a-single-arbitrary-object"></a>Contrôles qui contiennent un objet arbitraire unique  
 La <xref:System.Windows.Controls.ContentControl> classe contient un seul morceau de contenu arbitraire. Sa propriété <xref:System.Windows.Controls.ContentControl.Content%2A>de contenu est . Les contrôles suivants <xref:System.Windows.Controls.ContentControl> héritent de son modèle de contenu et l’utilisent :  
  
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
  
 L’illustration suivante montre <xref:System.Windows.Controls.ContentControl.Content%2A> quatre boutons dont l’on <xref:System.Windows.Shapes.Rectangle>met une <xref:System.Windows.Controls.Panel> ficelle, <xref:System.Windows.Shapes.Ellipse> un <xref:System.Windows.Controls.TextBlock> <xref:System.DateTime> objet, un , et un qui contient un et un :  
  
 ![Capture d’écran qui affiche quatre boutons avec différents types de contenu.](./media/wpf-content-model/control-content-model-buttons.png)  
  
 Pour un exemple de <xref:System.Windows.Controls.ContentControl.Content%2A> la façon <xref:System.Windows.Controls.ContentControl>de définir la propriété, voir .  
  
### <a name="controls-that-contain-a-header-and-a-single-arbitrary-object"></a>Contrôles qui contiennent un en-tête et un objet arbitraire unique  
 La <xref:System.Windows.Controls.HeaderedContentControl> classe hérite et affiche le <xref:System.Windows.Controls.ContentControl> contenu avec un en-tête. Il hérite de <xref:System.Windows.Controls.ContentControl.Content%2A>la <xref:System.Windows.Controls.ContentControl> propriété de <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> contenu, , <xref:System.Object>et définit la propriété qui est de type ; par conséquent, les deux peuvent être un objet arbitraire.  
  
 Les contrôles suivants <xref:System.Windows.Controls.HeaderedContentControl> héritent de son modèle de contenu et l’utilisent :  
  
- <xref:System.Windows.Controls.Expander>  
  
- <xref:System.Windows.Controls.GroupBox>  
  
- <xref:System.Windows.Controls.TabItem>  
  
 L’illustration suivante <xref:System.Windows.Controls.TabItem> montre deux objets. Le <xref:System.Windows.Controls.TabItem> premier <xref:System.Windows.UIElement> a <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> des <xref:System.Windows.Controls.ContentControl.Content%2A>objets comme le et le . Le <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> est réglé <xref:System.Windows.Controls.StackPanel> à <xref:System.Windows.Shapes.Ellipse> un <xref:System.Windows.Controls.TextBlock>qui contient un et a . Le <xref:System.Windows.Controls.ContentControl.Content%2A> est réglé <xref:System.Windows.Controls.StackPanel> à <xref:System.Windows.Controls.TextBlock> un <xref:System.Windows.Controls.Label>qui contient a et a . Le <xref:System.Windows.Controls.TabItem> second a une <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> chaîne <xref:System.Windows.Controls.TextBlock> dans <xref:System.Windows.Controls.ContentControl.Content%2A>le et un dans le .  
  
 ![TabControl qui utilise différents types dans la propriété Header.](./media/wpf-content-model/control-content-model-tab.png)  
  
 Pour un exemple de <xref:System.Windows.Controls.TabItem> la <xref:System.Windows.Controls.HeaderedContentControl>façon de créer des objets, voir .  
  
### <a name="controls-that-contain-a-collection-of-arbitrary-objects"></a>Contrôles qui contiennent une collection d’objets arbitraires  
 La <xref:System.Windows.Controls.ItemsControl> classe hérite de <xref:System.Windows.Controls.Control> plusieurs éléments, tels que des cordes, des objets ou d’autres éléments. Ses propriétés <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> <xref:System.Windows.Controls.ItemsControl.Items%2A>de contenu sont et . <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>est généralement utilisé pour <xref:System.Windows.Controls.ItemsControl> remplir le avec une collecte de données. Si vous ne voulez pas utiliser une <xref:System.Windows.Controls.ItemsControl>collection pour remplir le <xref:System.Windows.Controls.ItemsControl.Items%2A> , vous pouvez ajouter des éléments en utilisant la propriété.  
  
 Les contrôles suivants <xref:System.Windows.Controls.ItemsControl> héritent de son modèle de contenu et l’utilisent :  
  
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
  
 L’illustration suivante <xref:System.Windows.Controls.ListBox> montre un qui contient ces types d’éléments:  
  
- Une chaîne.  
  
- Objet <xref:System.DateTime> .  
  
- <xref:System.Windows.UIElement>.  
  
- A <xref:System.Windows.Controls.Panel> qui <xref:System.Windows.Shapes.Ellipse> contient <xref:System.Windows.Controls.TextBlock>un et un .  
  
 ![Capture d’écran qui montre une ListBox avec quatre types de contenu.](./media/wpf-content-model/control-content-model-listbox.png)  
  
### <a name="controls-that-contain-a-header-and-a-collection-of-arbitrary-objects"></a>Contrôles qui contiennent un en-tête et une collection d’objets arbitraires  
 La <xref:System.Windows.Controls.HeaderedItemsControl> classe hérite de <xref:System.Windows.Controls.ItemsControl> plusieurs éléments, tels que des cordes, des objets ou d’autres éléments, et un en-tête. Il hérite <xref:System.Windows.Controls.ItemsControl> des <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>propriétés <xref:System.Windows.Controls.ItemsControl.Items%2A>de contenu, <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> et , et il définit la propriété qui peut être un objet arbitraire.  
  
 Les contrôles suivants <xref:System.Windows.Controls.HeaderedItemsControl> héritent de son modèle de contenu et l’utilisent :  
  
- <xref:System.Windows.Controls.MenuItem>  
  
- <xref:System.Windows.Controls.ToolBar>  
  
- <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>
## <a name="classes-that-contain-a-collection-of-uielement-objects"></a>Classes qui contiennent une collection d’objets UIElement  
 La <xref:System.Windows.Controls.Panel> classe positionne <xref:System.Windows.UIElement> et arrange les objets pour enfants. Sa propriété <xref:System.Windows.Controls.Panel.Children%2A>de contenu est .  
  
 Les classes suivantes <xref:System.Windows.Controls.Panel> héritent de la classe et utilisent son modèle de contenu :  
  
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
 La <xref:System.Windows.Controls.Decorator> classe applique des effets visuels <xref:System.Windows.UIElement>sur ou autour d’un seul enfant. Sa propriété <xref:System.Windows.Controls.Decorator.Child%2A>de contenu est . Les classes suivantes <xref:System.Windows.Controls.Decorator> héritent de son modèle de contenu et utilisent :  
  
- <xref:System.Windows.Documents.AdornerDecorator>  
  
- <xref:System.Windows.Controls.Border>  
  
- <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
- <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
- <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
- <xref:System.Windows.Controls.InkPresenter>  
  
- <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
- <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
- <xref:System.Windows.Controls.Viewbox>  
  
 L’illustration suivante <xref:System.Windows.Controls.TextBox> montre un qui a <xref:System.Windows.Controls.Border> (est décoré avec) un autour d’elle.  
  
 ![TextBox avec bordure noire](./media/layout-border-around-textbox.png "Layout_Border_around_TextBox")  
TextBlock avec une bordure  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>
## <a name="classes-that-provide-visual-feedback-about-a-uielement"></a>Classes qui fournissent des commentaires visuels sur un UIElement  
 La <xref:System.Windows.Documents.Adorner> classe fournit des indices visuels à un utilisateur. Par exemple, <xref:System.Windows.Documents.Adorner> utilisez un pour ajouter des poignées fonctionnelles aux éléments ou fournir des informations d’état sur un contrôle. La <xref:System.Windows.Documents.Adorner> classe fournit un cadre afin que vous puissiez créer vos propres adorateurs. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ne fournit aucun ornement implémenté. Pour plus d’informations, consultez [Vue d’ensemble des ornements](adorners-overview.md).  
  
<a name="classes_that_enable_users_to_enter_text"></a>
## <a name="classes-that-enable-users-to-enter-text"></a>Classes qui permettent aux utilisateurs d’entrer du texte  
 WPF fournit trois principaux contrôles qui permettent aux utilisateurs d’entrer du texte. Chaque contrôle affiche le texte de manière différente. Le tableau suivant répertorie ces trois contrôles liés au texte, leurs fonctions lors de l’affichage du texte et leurs propriétés qui contiennent le texte du contrôle.  
  
|Control|Texte affiché en tant que|Propriété de contenu|  
|-------------|--------------------------|----------------------|  
|<xref:System.Windows.Controls.TextBox>|Texte brut|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|Texte mis en forme|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|Texte masqué (les caractères sont masqués)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>
## <a name="classes-that-display-your-text"></a>Classes qui affichent votre texte  
 Plusieurs classes peuvent être utilisées pour afficher du texte brut ou mis en forme. Vous pouvez <xref:System.Windows.Controls.TextBlock> utiliser pour afficher de petites quantités de texte. Si vous souhaitez afficher de grandes <xref:System.Windows.Controls.FlowDocumentReader>quantités de texte, utilisez le , <xref:System.Windows.Controls.FlowDocumentPageViewer>ou <xref:System.Windows.Controls.FlowDocumentScrollViewer> les contrôles.  
  
 Le <xref:System.Windows.Controls.TextBlock> a deux <xref:System.Windows.Controls.TextBlock.Text%2A> propriétés de contenu: et <xref:System.Windows.Controls.TextBlock.Inlines%2A>. Lorsque vous souhaitez afficher du texte qui <xref:System.Windows.Controls.TextBlock.Text%2A> utilise un formatage cohérent, la propriété est souvent votre meilleur choix. Si vous prévoyez d’utiliser différents formatages tout au long du texte, utilisez la <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriété. La <xref:System.Windows.Controls.TextBlock.Inlines%2A> propriété est <xref:System.Windows.Documents.Inline> une collection d’objets, qui spécifient comment formater le texte.  
  
 Le tableau suivant répertorie la propriété de contenu pour <xref:System.Windows.Controls.FlowDocumentReader>, <xref:System.Windows.Controls.FlowDocumentPageViewer>, et <xref:System.Windows.Controls.FlowDocumentScrollViewer> les classes.  
  
|Control|Propriété de contenu|Type de propriété de contenu|  
|-------------|----------------------|---------------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Document|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Document|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Document|<xref:System.Windows.Documents.FlowDocument>|  
  
 Les <xref:System.Windows.Documents.FlowDocument> impléments de l’interface; <xref:System.Windows.Documents.IDocumentPaginatorSource> par conséquent, les trois <xref:System.Windows.Documents.FlowDocument> classes peuvent prendre un contenu comme.  
  
<a name="classes_that_format_text"></a>
## <a name="classes-that-format-your-text"></a>Classes de mise en forme du texte  
 <xref:System.Windows.Documents.TextElement>et ses classes connexes vous permettent de formater le texte. <xref:System.Windows.Documents.TextElement>objets contiennent et <xref:System.Windows.Controls.TextBlock> formater le texte et <xref:System.Windows.Documents.FlowDocument> les objets. Les deux principaux <xref:System.Windows.Documents.TextElement> types <xref:System.Windows.Documents.Block> d’objets sont des éléments et des <xref:System.Windows.Documents.Inline> éléments. Un <xref:System.Windows.Documents.Block> élément représente un bloc de texte, tel qu’un paragraphe ou une liste. Un <xref:System.Windows.Documents.Inline> élément représente une partie du texte dans un bloc. De <xref:System.Windows.Documents.Inline> nombreuses classes spécifient le formatage du texte auquel elles sont appliquées. Chacun <xref:System.Windows.Documents.TextElement> a son propre modèle de contenu. Pour plus d’informations, consultez la page [Vue d’ensemble du modèle de contenu de TextElement](../advanced/textelement-content-model-overview.md).  
  
## <a name="see-also"></a>Voir aussi

- [Avancé](../advanced/index.md)
