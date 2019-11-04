---
title: Contrôles
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: 42596c8adf1b8b27f250fa7a3cf6cc173a63e2eb
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459446"
---
# <a name="controls"></a>Contrôles
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] est livré avec un grand nombre de composants d’interface utilisateur courants qui sont utilisés dans presque toutes les applications Windows, comme <xref:System.Windows.Controls.Button>, <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.TextBox>, <xref:System.Windows.Controls.Menu>et <xref:System.Windows.Controls.ListBox>. Par le passé, ces objets étaient connus sous le nom de contrôles. Tandis que le kit de développement logiciel (SDK) [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] continue à utiliser le terme « contrôle » pour signifier faiblement toute classe représentant un objet visible dans une application, il est important de noter qu’une classe n’a pas besoin d’hériter de la classe <xref:System.Windows.Controls.Control> pour avoir une présence visible. Les classes qui héritent de la classe <xref:System.Windows.Controls.Control> contiennent un <xref:System.Windows.Controls.ControlTemplate>, qui permet au consommateur d’un contrôle de changer radicalement l’apparence du contrôle sans avoir à créer une sous-classe.  Cette rubrique explique comment les contrôles (à la fois ceux qui héritent de la classe <xref:System.Windows.Controls.Control> et ceux qui ne le sont pas) sont couramment utilisés dans les [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  

<a name="creating_an_instance_of_a_control"></a>   
## <a name="creating-an-instance-of-a-control"></a>Création d’une instance d’un contrôle  
 Vous pouvez ajouter un contrôle à une application à l’aide de l' [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou du code.  L’exemple suivant montre comment créer une application simple qui demande à un utilisateur d’entrer son nom et son prénom.  Cet exemple crée six contrôles : deux étiquettes, deux zones de texte et deux boutons dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. Tous les contrôles peuvent être créés de la même façon.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 L’exemple suivant crée la même application dans le code. Par souci de concision, la création de l' <xref:System.Windows.Controls.Grid>, `grid1`, a été exclue de l’exemple. `grid1` a les mêmes définitions de colonne et de ligne, comme indiqué dans l’exemple précédent [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>   
## <a name="changing-the-appearance-of-a-control"></a>Changement de l’apparence d’un contrôle  
 Vous pouvez couramment être amené à changer l’apparence d’un contrôle pour ajuster l’aspect de votre application. Vous pouvez changer l’apparence d’un contrôle en effectuant l’une des opérations suivantes, selon ce que vous souhaitez accomplir :  
  
- Modifier la valeur d’une propriété du contrôle  
  
- Créez un <xref:System.Windows.Style> pour le contrôle.  
  
- Créez un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle.  
  
### <a name="changing-a-controls-property-value"></a>Changement de la valeur de propriété d’un contrôle  
 De nombreux contrôles ont des propriétés qui vous permettent de modifier le mode d’affichage du contrôle, comme le <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button>. Vous pouvez définir les propriétés de valeur dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et dans le code. L’exemple suivant définit les propriétés <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>et <xref:System.Windows.Controls.Control.FontWeight%2A> sur un <xref:System.Windows.Controls.Button> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 L’exemple suivant définit les mêmes propriétés dans le code.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Création d’un style pour un contrôle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vous donne la possibilité de spécifier l’apparence des contrôles grossistes, au lieu de définir des propriétés sur chaque instance de l’application, en créant une <xref:System.Windows.Style>. L’exemple suivant crée un <xref:System.Windows.Style> qui est appliqué à chaque <xref:System.Windows.Controls.Button> de l’application. les définitions de <xref:System.Windows.Style> sont généralement définies dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans un <xref:System.Windows.ResourceDictionary>, tel que la propriété <xref:System.Windows.FrameworkElement.Resources%2A> de l' <xref:System.Windows.FrameworkElement>.  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Vous pouvez également appliquer un style à certains contrôles d’un type spécifique en affectant une clé au style et en spécifiant cette clé dans la propriété `Style` de votre contrôle.  Pour plus d’informations sur les styles, consultez [stylisation et création de modèles](styling-and-templating.md).  
  
### <a name="creating-a-controltemplate"></a>Création d’un ControlTemplate  
 Une <xref:System.Windows.Style> vous permet de définir des propriétés sur plusieurs contrôles à la fois, mais il peut arriver que vous souhaitiez personnaliser l’apparence d’un <xref:System.Windows.Controls.Control> au-delà de ce que vous pouvez faire en créant un <xref:System.Windows.Style>. Les classes qui héritent de la classe <xref:System.Windows.Controls.Control> ont un <xref:System.Windows.Controls.ControlTemplate>, qui définit la structure et l’apparence d’un <xref:System.Windows.Controls.Control>. La propriété <xref:System.Windows.Controls.Control.Template%2A> d’un <xref:System.Windows.Controls.Control> étant publique, vous pouvez attribuer à un <xref:System.Windows.Controls.Control> une <xref:System.Windows.Controls.ControlTemplate> différente de sa valeur par défaut. Vous pouvez souvent spécifier un nouveau <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Control> au lieu d’hériter d’un contrôle pour personnaliser l’apparence d’un <xref:System.Windows.Controls.Control>.  
  
 Considérez le contrôle très courant, <xref:System.Windows.Controls.Button>.  Le comportement principal d’un <xref:System.Windows.Controls.Button> consiste à permettre à une application de prendre des mesures quand l’utilisateur clique dessus.  Par défaut, le <xref:System.Windows.Controls.Button> dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apparaît comme un rectangle en relief.  Lors du développement d’une application, vous souhaiterez peut-être tirer parti du comportement d’un <xref:System.Windows.Controls.Button>, en gérant l’événement Click du bouton, mais vous pouvez modifier l’apparence du bouton au-delà de ce que vous pouvez faire en modifiant les propriétés du bouton.  Dans ce cas, vous pouvez créer un <xref:System.Windows.Controls.ControlTemplate>.  
  
 L’exemple suivant crée une <xref:System.Windows.Controls.ControlTemplate> pour une <xref:System.Windows.Controls.Button>.  L' <xref:System.Windows.Controls.ControlTemplate> crée un <xref:System.Windows.Controls.Button> avec des angles arrondis et un arrière-plan dégradé.  Le <xref:System.Windows.Controls.ControlTemplate> contient une <xref:System.Windows.Controls.Border> dont <xref:System.Windows.Controls.Border.Background%2A> est un <xref:System.Windows.Media.LinearGradientBrush> avec deux objets <xref:System.Windows.Media.GradientStop>.  La première <xref:System.Windows.Media.GradientStop> utilise la liaison de données pour lier la propriété <xref:System.Windows.Media.GradientStop.Color%2A> de l' <xref:System.Windows.Media.GradientStop> à la couleur de l’arrière-plan du bouton.  Lorsque vous définissez la propriété <xref:System.Windows.Controls.Control.Background%2A> de la <xref:System.Windows.Controls.Button>, la couleur de cette valeur est utilisée comme premier <xref:System.Windows.Media.GradientStop>. Pour plus d’informations sur la liaison de données, consultez [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md). L’exemple crée également un <xref:System.Windows.Trigger> qui modifie l’apparence du <xref:System.Windows.Controls.Button> lorsque <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> est `true`.  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> Pour que l’exemple fonctionne correctement, la propriété <xref:System.Windows.Controls.Control.Background%2A> du <xref:System.Windows.Controls.Button> doit être définie sur un <xref:System.Windows.Media.SolidColorBrush>.  
  
<a name="subscribing_to_events"></a>   
## <a name="subscribing-to-events"></a>Abonnement à des événements  
 Vous pouvez vous abonner à l’événement d’un contrôle à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code, mais vous ne pouvez gérer qu’un événement dans le code.  L’exemple suivant montre comment s’abonner à l’événement `Click` d’une <xref:System.Windows.Controls.Button>.  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 L’exemple suivant gère l’événement `Click` d’une <xref:System.Windows.Controls.Button>.  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>   
## <a name="rich-content-in-controls"></a>Contenu riche dans les contrôles  
 La plupart des classes qui héritent de la classe <xref:System.Windows.Controls.Control> ont la capacité de contenir du contenu riche. Par exemple, un <xref:System.Windows.Controls.Label> peut contenir tout objet, tel qu’une chaîne, une <xref:System.Windows.Controls.Image>ou un <xref:System.Windows.Controls.Panel>.  Les classes suivantes fournissent la prise en charge du contenu riche et agissent comme des classes de base pour la plupart des contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
- <xref:System.Windows.Controls.ContentControl>--Voici quelques exemples de classes qui héritent de cette classe : <xref:System.Windows.Controls.Label>, <xref:System.Windows.Controls.Button>et <xref:System.Windows.Controls.ToolTip>.  
  
- <xref:System.Windows.Controls.ItemsControl>--Voici quelques exemples de classes qui héritent de cette classe : <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.Menu>et <xref:System.Windows.Controls.Primitives.StatusBar>.  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--Voici quelques exemples de classes qui héritent de cette classe : <xref:System.Windows.Controls.TabItem>, <xref:System.Windows.Controls.GroupBox>et <xref:System.Windows.Controls.Expander>.  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Voici quelques exemples de classes qui héritent de cette classe : <xref:System.Windows.Controls.MenuItem>, <xref:System.Windows.Controls.TreeViewItem>et <xref:System.Windows.Controls.ToolBar>.  

 Pour plus d’informations sur ces classes de base, consultez [modèle de contenu WPF](wpf-content-model.md).  
  
## <a name="see-also"></a>Voir aussi

- [Application d’un style et création de modèles](styling-and-templating.md)
- [Contrôles par catégorie](controls-by-category.md)
- [Bibliothèque de contrôles](control-library.md)
- [Vue d’ensemble des modèles de données](../data/data-templating-overview.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Entrée](../advanced/input-wpf.md)
- [Activer une commande](../advanced/how-to-enable-a-command.md)
- [Procédures pas à pas : création d’un bouton animé personnalisé](walkthroughs-create-a-custom-animated-button.md)
- [Personnalisation des contrôles](control-customization.md)
