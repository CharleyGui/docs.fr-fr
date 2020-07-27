---
title: Contrôles
description: En savoir plus sur les Windows Presentation Foundation les composants d’interface utilisateur communs, appelés contrôles, mais qui ne peuvent pas hériter de la classe de contrôle.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], about WPF controls
ms.assetid: 3f255a8a-35a8-4712-9065-472ff7d75599
ms.openlocfilehash: c3d9d3a38cf5f84e21df195e113e264e5a4ac025
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165850"
---
# <a name="controls"></a>Contrôles
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]est fourni avec la plupart des composants d’interface utilisateur courants qui sont utilisés dans presque toutes les applications Windows, telles que,,, <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Label> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.Menu> et <xref:System.Windows.Controls.ListBox> . Par le passé, ces objets étaient connus sous le nom de contrôles. Tandis que le [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Kit de développement logiciel continue à utiliser le terme « contrôle » pour signifier faiblement toute classe représentant un objet visible dans une application, il est important de noter qu’une classe n’a pas besoin d’hériter de la <xref:System.Windows.Controls.Control> classe pour avoir une présence visible. Les classes qui héritent de la <xref:System.Windows.Controls.Control> classe contiennent un <xref:System.Windows.Controls.ControlTemplate> , ce qui permet au consommateur d’un contrôle de changer radicalement l’apparence du contrôle sans devoir créer une sous-classe.  Cette rubrique explique comment les contrôles (à la fois ceux qui héritent de la <xref:System.Windows.Controls.Control> classe et ceux qui ne le sont pas) sont couramment utilisés dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  

<a name="creating_an_instance_of_a_control"></a>
## <a name="creating-an-instance-of-a-control"></a>Création d’une instance d’un contrôle  
 Vous pouvez ajouter un contrôle à une application à l’aide de [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou du code.  L’exemple suivant montre comment créer une application simple qui demande à un utilisateur d’entrer son nom et son prénom.  Cet exemple crée six contrôles : deux étiquettes, deux zones de texte et deux boutons dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] . Tous les contrôles peuvent être créés de la même façon.  
  
 [!code-xaml[ControlsOverview#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#1)]  
  
 L’exemple suivant crée la même application dans le code. Par souci de concision, la création de <xref:System.Windows.Controls.Grid> , `grid1` , a été exclue de l’exemple. `grid1`a les mêmes définitions de colonne et de ligne, comme indiqué dans l' [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] exemple précédent.  
  
 [!code-csharp[ControlsOverview#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#2)]
 [!code-vb[ControlsOverview#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#2)]  
  
<a name="changing_the_appearance_of_a_control"></a>
## <a name="changing-the-appearance-of-a-control"></a>Changement de l’apparence d’un contrôle  
 Vous pouvez couramment être amené à changer l’apparence d’un contrôle pour ajuster l’aspect de votre application. Vous pouvez changer l’apparence d’un contrôle en effectuant l’une des opérations suivantes, selon ce que vous souhaitez accomplir :  
  
- Modifier la valeur d’une propriété du contrôle  
  
- Créez un <xref:System.Windows.Style> pour le contrôle.  
  
- Créez un <xref:System.Windows.Controls.ControlTemplate> pour le contrôle.  
  
### <a name="changing-a-controls-property-value"></a>Changement de la valeur de propriété d’un contrôle  
 De nombreux contrôles ont des propriétés qui vous permettent de modifier le mode d’affichage du contrôle, tel que le <xref:System.Windows.Controls.Control.Background%2A> d’un <xref:System.Windows.Controls.Button> . Vous pouvez définir les propriétés de valeur dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] et dans le code. L’exemple suivant définit les <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.FontSize%2A> Propriétés, et <xref:System.Windows.Controls.Control.FontWeight%2A> sur un <xref:System.Windows.Controls.Button> dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .  
  
 [!code-xaml[ControlsOverview#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#3)]  
  
 L’exemple suivant définit les mêmes propriétés dans le code.  
  
 [!code-csharp[ControlsOverview#4](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#4)]
 [!code-vb[ControlsOverview#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#4)]  
  
### <a name="creating-a-style-for-a-control"></a>Création d’un style pour un contrôle  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vous donne la possibilité de spécifier l’apparence des contrôles en grossiste au lieu de définir des propriétés sur chaque instance de l’application, en créant un <xref:System.Windows.Style> . L’exemple suivant crée un <xref:System.Windows.Style> qui est appliqué à chaque <xref:System.Windows.Controls.Button> dans l’application. <xref:System.Windows.Style>les définitions sont généralement définies dans [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dans un <xref:System.Windows.ResourceDictionary> , tel que la <xref:System.Windows.FrameworkElement.Resources%2A> propriété de <xref:System.Windows.FrameworkElement> .  
  
 [!code-xaml[ControlsOverview#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#5)]  
  
 Vous pouvez également appliquer un style à certains contrôles d’un type spécifique en affectant une clé au style et en spécifiant cette clé dans la `Style` propriété de votre contrôle.  Pour plus d’informations sur les styles, consultez [stylisation et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md).  
  
### <a name="creating-a-controltemplate"></a>Création d’un ControlTemplate  
 Un vous <xref:System.Windows.Style> permet de définir des propriétés sur plusieurs contrôles à la fois, mais il peut arriver que vous souhaitiez personnaliser l’apparence d’un <xref:System.Windows.Controls.Control> au delà de ce que vous pouvez faire en créant un <xref:System.Windows.Style> . Les classes qui héritent de la <xref:System.Windows.Controls.Control> classe ont un <xref:System.Windows.Controls.ControlTemplate> , qui définit la structure et l’apparence d’un <xref:System.Windows.Controls.Control> . La <xref:System.Windows.Controls.Control.Template%2A> propriété d’un <xref:System.Windows.Controls.Control> est publique, ce qui signifie que vous pouvez attribuer un <xref:System.Windows.Controls.Control> <xref:System.Windows.Controls.ControlTemplate> qui est différent de sa valeur par défaut. Vous pouvez souvent spécifier un nouveau <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Control> au lieu d’hériter d’un contrôle pour personnaliser l’apparence d’un <xref:System.Windows.Controls.Control> .  
  
 Considérez le contrôle très courant, <xref:System.Windows.Controls.Button> .  Le comportement principal d’un <xref:System.Windows.Controls.Button> consiste à permettre à une application de prendre des mesures quand l’utilisateur clique dessus.  Par défaut, <xref:System.Windows.Controls.Button> dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] apparaît comme un rectangle en relief.  Lors du développement d’une application, vous souhaiterez peut-être tirer parti du comportement d’un <xref:System.Windows.Controls.Button> --autrement dit, en gérant l’événement Click du bouton, mais vous pouvez modifier l’apparence du bouton au-delà de ce que vous pouvez faire en modifiant les propriétés du bouton.  Dans ce cas, vous pouvez créer un nouveau <xref:System.Windows.Controls.ControlTemplate> .  
  
 L’exemple suivant crée un <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.Button> .  <xref:System.Windows.Controls.ControlTemplate>Crée un <xref:System.Windows.Controls.Button> avec des angles arrondis et un arrière-plan dégradé.  Le <xref:System.Windows.Controls.ControlTemplate> contient un <xref:System.Windows.Controls.Border> dont <xref:System.Windows.Controls.Border.Background%2A> est un <xref:System.Windows.Media.LinearGradientBrush> avec deux <xref:System.Windows.Media.GradientStop> objets.  La première <xref:System.Windows.Media.GradientStop> utilise la liaison de données pour lier la <xref:System.Windows.Media.GradientStop.Color%2A> propriété de <xref:System.Windows.Media.GradientStop> à la couleur de l’arrière-plan du bouton.  Lorsque vous définissez la <xref:System.Windows.Controls.Control.Background%2A> propriété du <xref:System.Windows.Controls.Button> , la couleur de cette valeur sera utilisée comme première <xref:System.Windows.Media.GradientStop> . Pour plus d’informations sur la liaison de données, consultez [vue d’ensemble](../../../desktop-wpf/data/data-binding-overview.md)de la liaison de données. L’exemple crée également un <xref:System.Windows.Trigger> qui modifie l’apparence du <xref:System.Windows.Controls.Button> lorsque <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> est `true` .  
  
 [!code-xaml[ControlsOverview#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#6)]  
[!code-xaml[ControlsOverview#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml#7)]  
  
> [!NOTE]
> La <xref:System.Windows.Controls.Control.Background%2A> propriété de <xref:System.Windows.Controls.Button> doit avoir la valeur pour <xref:System.Windows.Media.SolidColorBrush> que l’exemple fonctionne correctement.  
  
<a name="subscribing_to_events"></a>
## <a name="subscribing-to-events"></a>Abonnement à des événements  
 Vous pouvez vous abonner à l’événement d’un contrôle à l’aide de [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ou du code, mais vous ne pouvez gérer qu’un événement dans le code.  L’exemple suivant montre comment s’abonner à l' `Click` événement d’un <xref:System.Windows.Controls.Button> .  
  
 [!code-xaml[ControlsOverview#10](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/Window1.xaml#10)]  
  
 [!code-csharp[ControlsOverview#8](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#8)]
 [!code-vb[ControlsOverview#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#8)]  
  
 L’exemple suivant gère l' `Click` événement d’un <xref:System.Windows.Controls.Button> .  
  
 [!code-csharp[ControlsOverview#9](~/samples/snippets/csharp/VS_Snippets_Wpf/ControlsOverview/CSharp/AppInCode.xaml.cs#9)]
 [!code-vb[ControlsOverview#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ControlsOverview/VisualBasic/AppInCode.xaml.vb#9)]  
  
<a name="rich_content_in_controls"></a>
## <a name="rich-content-in-controls"></a>Contenu riche dans les contrôles  
 La plupart des classes qui héritent de la <xref:System.Windows.Controls.Control> classe ont la capacité de contenir du contenu riche. Par exemple, un <xref:System.Windows.Controls.Label> peut contenir n’importe quel objet, tel qu’une chaîne, un <xref:System.Windows.Controls.Image> ou un <xref:System.Windows.Controls.Panel> .  Les classes suivantes fournissent la prise en charge du contenu riche et agissent comme des classes de base pour la plupart des contrôles dans [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] .  
  
- <xref:System.Windows.Controls.ContentControl>--Voici quelques exemples de classes qui héritent de cette classe : <xref:System.Windows.Controls.Label> , <xref:System.Windows.Controls.Button> et <xref:System.Windows.Controls.ToolTip> .  
  
- <xref:System.Windows.Controls.ItemsControl>--Voici quelques exemples de classes qui héritent de cette classe : <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.Menu> et <xref:System.Windows.Controls.Primitives.StatusBar> .  
  
- <xref:System.Windows.Controls.HeaderedContentControl>--Voici quelques exemples de classes qui héritent de cette classe : <xref:System.Windows.Controls.TabItem> , <xref:System.Windows.Controls.GroupBox> et <xref:System.Windows.Controls.Expander> .  
  
- <xref:System.Windows.Controls.HeaderedItemsControl>--Voici quelques exemples de classes qui héritent de cette classe : <xref:System.Windows.Controls.MenuItem> , <xref:System.Windows.Controls.TreeViewItem> et <xref:System.Windows.Controls.ToolBar> .  

 Pour plus d’informations sur ces classes de base, consultez [modèle de contenu WPF](wpf-content-model.md).  
  
## <a name="see-also"></a>Voir aussi

- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Contrôles par catégorie](controls-by-category.md)
- [Bibliothèque de contrôles](control-library.md)
- [Vue d'ensemble des modèles de données](../data/data-templating-overview.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Input](../advanced/input-wpf.md)
- [Activer une commande](../advanced/how-to-enable-a-command.md)
- [Procédures pas à pas : Créer un bouton animé personnalisé](walkthroughs-create-a-custom-animated-button.md)
- [Personnalisation des contrôles](control-customization.md)
