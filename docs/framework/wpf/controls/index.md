---
title: Commandes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 2ec8c0a99f4e2431aed0d8c24168b7329de669f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187536"
---
# <a name="controls"></a>Commandes
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]navires avec beaucoup de composants d’interface utilisateur communs qui sont <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label>utilisés <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Menu>dans presque toutes les applications Windows, telles que , , , , et <xref:System.Windows.Controls.ListBox>. Par le passé, ces objets étaient connus sous le nom de contrôles. Bien [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] que le SDK continue d’utiliser le terme « contrôle » pour signifier vaguement n’importe quelle classe qui <xref:System.Windows.Controls.Control> représente un objet visible dans une application, il est important de noter qu’une classe n’a pas besoin d’hériter de la classe pour avoir une présence visible. Les classes qui <xref:System.Windows.Controls.Control> héritent de la classe contiennent un <xref:System.Windows.Controls.ControlTemplate>, ce qui permet au consommateur d’un contrôle de changer radicalement l’apparence du contrôle sans avoir à créer une nouvelle sous-classe.  Ce sujet traite de la façon dont <xref:System.Windows.Controls.Control> les contrôles (à la fois [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ceux qui héritent de la classe et ceux qui ne le font pas) sont couramment utilisés dans .  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>Création d’une instance d’un contrôle  
 Vous pouvez ajouter un contrôle à [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] une application en utilisant l’un ou l’autre ou le code.  L’exemple suivant montre comment créer une application simple qui demande à un utilisateur d’entrer son nom et son prénom.  Cet exemple crée six contrôles : deux étiquettes, deux [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]boîtes de texte et deux boutons, en . Tous les contrôles peuvent être créés de la même façon.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 L’exemple suivant crée la même application dans le code. Pour la brièveté, <xref:System.Windows.Controls.Grid>la `grid1`création de la , , a été exclue de l’échantillon. `grid1`a les mêmes définitions de colonne [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et de ligne que ce qui est indiqué dans l’exemple précédent.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>Changement de l’apparence d’un contrôle  
 Vous pouvez couramment être amené à changer l’apparence d’un contrôle pour ajuster l’aspect de votre application. Vous pouvez changer l’apparence d’un contrôle en effectuant l’une des opérations suivantes, selon ce que vous souhaitez accomplir :  
  
- Modifier la valeur d’une propriété du contrôle  
  
- Créez <xref:System.Windows.Style> un pour le contrôle.  
  
- Créez un <xref:System.Windows.Controls.ControlTemplate> nouveau pour le contrôle.  
  
### <a name="changing-a-controls-property-value"></a>Changement de la valeur de propriété d’un contrôle  
 Beaucoup de contrôles ont des propriétés qui vous <xref:System.Windows.Controls.Control.Background%2A> permettent <xref:System.Windows.Controls.Button>de changer la façon dont le contrôle apparaît, comme le d’un . Vous pouvez définir les [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] propriétés de valeur dans les deux et le code. L’exemple suivant <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.FontSize%2A>définit <xref:System.Windows.Controls.Control.FontWeight%2A> le , <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], et les propriétés sur un in .  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 L’exemple suivant définit les mêmes propriétés dans le code.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Création d’un style pour un contrôle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vous donne la possibilité de spécifier l’apparence des contrôles en gros, au lieu de définir des propriétés sur chaque instance de l’application, en créant un <xref:System.Windows.Style>. L’exemple suivant <xref:System.Windows.Style> crée un <xref:System.Windows.Controls.Button> qui est appliqué à chacun dans l’application. <xref:System.Windows.Style>définitions sont généralement [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] définies dans <xref:System.Windows.ResourceDictionary> <xref:System.Windows.FrameworkElement.Resources%2A> un , <xref:System.Windows.FrameworkElement>comme la propriété de la .  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Vous pouvez également appliquer un style à seulement certains contrôles d’un type spécifique en `Style` assignant une clé au style et en spécifiant cette clé dans la propriété de votre contrôle.  Pour plus d’informations sur les styles, voir [Styling et Templating](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Création d’un ControlTemplate  
 A <xref:System.Windows.Style> vous permet de définir des propriétés sur plusieurs contrôles à la <xref:System.Windows.Controls.Control> fois, mais parfois vous <xref:System.Windows.Style>voudrez peut-être personnaliser l’apparence d’un au-delà de ce que vous pouvez faire en créant un . Les classes qui <xref:System.Windows.Controls.Control> héritent de la classe ont <xref:System.Windows.Controls.ControlTemplate> <xref:System.Windows.Controls.Control>un , qui définit la structure et l’apparence d’un . La <xref:System.Windows.Controls.Control.Template%2A> propriété <xref:System.Windows.Controls.Control> d’un est public, <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> de sorte que vous pouvez donner un qui est différent de son défaut. Vous pouvez souvent <xref:System.Windows.Controls.ControlTemplate> spécifier un nouveau pour un <xref:System.Windows.Controls.Control> au lieu <xref:System.Windows.Controls.Control>d’hériter d’un contrôle pour personnaliser l’apparence d’un .  
  
 Considérez le contrôle <xref:System.Windows.Controls.Button>très commun, .  Le comportement principal <xref:System.Windows.Controls.Button> d’un est de permettre à une application de prendre des mesures lorsque l’utilisateur clique dessus.  Par défaut, <xref:System.Windows.Controls.Button> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] l’in apparaît comme un rectangle surélevé.  Lors du développement d’une application, vous voudrez <xref:System.Windows.Controls.Button>peut-être profiter du comportement d’un -- c’est-à-dire en manipulant l’événement de clic du bouton -- mais vous pouvez modifier l’apparence du bouton au-delà de ce que vous pouvez faire en changeant les propriétés du bouton.  Dans ce cas, vous <xref:System.Windows.Controls.ControlTemplate>pouvez créer un nouveau .  
  
 L’exemple suivant <xref:System.Windows.Controls.ControlTemplate> crée <xref:System.Windows.Controls.Button>un pour un .  Le <xref:System.Windows.Controls.ControlTemplate> crée <xref:System.Windows.Controls.Button> un avec des coins arrondis et un fond de gradient.  Le <xref:System.Windows.Controls.ControlTemplate> contient <xref:System.Windows.Controls.Border> <xref:System.Windows.Controls.Border.Background%2A> un <xref:System.Windows.Media.LinearGradientBrush> dont <xref:System.Windows.Media.GradientStop> est un avec deux objets.  Le <xref:System.Windows.Media.GradientStop> premier utilise la <xref:System.Windows.Media.GradientStop.Color%2A> liaison de <xref:System.Windows.Media.GradientStop> données pour lier la propriété de la couleur de l’arrière-plan du bouton.  Lorsque vous <xref:System.Windows.Controls.Control.Background%2A> définissez <xref:System.Windows.Controls.Button>la propriété de la , la <xref:System.Windows.Media.GradientStop>couleur de cette valeur sera utilisé comme le premier . Pour plus d’informations sur la liaison des données, voir [Aperçu de la liaison des données](../../../desktop-wpf/data/data-binding-overview.md). L’exemple crée <xref:System.Windows.Trigger> également un qui <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> change `true`l’apparence du moment où est .  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> La <xref:System.Windows.Controls.Control.Background%2A> propriété <xref:System.Windows.Controls.Button> de la doit <xref:System.Windows.Media.SolidColorBrush> être mis à un pour l’exemple de travailler correctement.  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>Abonnement à des événements  
 Vous pouvez vous abonner à [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] l’événement d’un contrôle en utilisant l’un ou l’autre ou le code, mais vous ne pouvez gérer un événement dans le code.  L’exemple suivant montre comment `Click` s’abonner à l’événement d’un <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 L’exemple suivant `Click` traite de <xref:System.Windows.Controls.Button>l’événement d’un .  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>Contenu riche dans les contrôles  
 La plupart des <xref:System.Windows.Controls.Control> classes qui héritent de la classe ont la capacité de contenir du contenu riche. Par exemple, <xref:System.Windows.Controls.Label> un peut contenir n’importe <xref:System.Windows.Controls.Image>quel objet, comme une chaîne, un , ou un <xref:System.Windows.Controls.Panel>.  Les classes suivantes fournissent un soutien pour le contenu riche [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]et agissent comme classes de base pour la plupart des contrôles dans .  
  
- <xref:System.Windows.Controls.ContentControl>-- Quelques exemples de classes <xref:System.Windows.Controls.Label>qui <xref:System.Windows.Controls.Button>héritent de cette classe sont, , , et <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>-- Quelques exemples de classes <xref:System.Windows.Controls.ListBox>qui <xref:System.Windows.Controls.Menu>héritent de cette classe sont, , , et <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>-- Quelques exemples de classes <xref:System.Windows.Controls.TabItem>qui <xref:System.Windows.Controls.GroupBox>héritent de cette classe sont, , , et <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Certains exemples de classes qui <xref:System.Windows.Controls.MenuItem> <xref:System.Windows.Controls.TreeViewItem>héritent de cette classe sont , , , et <xref:System.Windows.Controls.ToolBar>.  

 Pour plus d’informations sur ces classes de base, voir [WPF Content Model](wpf-content-model.md).  
  
## <a name="see-also"></a>Voir aussi

- [Application d’un style et création de modèles](styling-and-templating.md)
- [Contrôles par catégorie](controls-by-category.md)
- [Bibliothèque de contrôles](control-library.md)
- [Vue d'ensemble des modèles de données](../data/data-templating-overview.md)
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Entrée](../advanced/input-wpf.md)
- [Activer une commande](../advanced/how-to-enable-a-command.md)
- [Procédures pas à pas : création d’un bouton animé personnalisé](walkthroughs-create-a-custom-animated-button.md)
- [Personnalisation des contrôles](control-customization.md)
