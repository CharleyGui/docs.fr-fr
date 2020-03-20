---
title: Vue d'ensemble de l'expanseur
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], Expander
- Expander control [WPF], about Expander control
ms.assetid: 877bf425-0e54-49ec-8fd2-13a211377abb
ms.openlocfilehash: 892d972a5704d50e91d04e05d6fdea7180a3155d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187108"
---
# <a name="expander-overview"></a>Vue d'ensemble de l'expanseur
Un <xref:System.Windows.Controls.Expander> contrôle fournit un moyen de fournir du contenu dans une zone extensible qui ressemble à une fenêtre et comprend un en-tête.  

<a name="CreatinganExpanderinXAML"></a>
## <a name="creating-a-simple-expander"></a>Créer un Expander simple  
 L’exemple suivant montre comment <xref:System.Windows.Controls.Expander> créer un contrôle simple. Cet exemple <xref:System.Windows.Controls.Expander> crée un qui ressemble à l’illustration précédente.  
  
 [!code-xaml[ExpanderExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderExample/CSharp/Page1.xaml#2)]  
  
 Le <xref:System.Windows.Controls.ContentControl.Content%2A> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> et <xref:System.Windows.Controls.Expander> d’un peut également <xref:System.Windows.Controls.RadioButton> contenir <xref:System.Windows.Controls.Image> du contenu complexe, tels que et des objets.  
  
<a name="SettingtheDirectionoftheExpandingWindow"></a>
## <a name="setting-the-direction-of-the-expanding-content-area"></a>Définir la direction de la zone de contenu extensible  
 Vous pouvez définir la <xref:System.Windows.Controls.Expander> zone de contenu d’un<xref:System.Windows.Controls.ExpandDirection.Down> <xref:System.Windows.Controls.ExpandDirection.Up>contrôle <xref:System.Windows.Controls.ExpandDirection.Left>pour <xref:System.Windows.Controls.ExpandDirection.Right>étendre dans <xref:System.Windows.Controls.ExpandDirection> l’une des quatre directions ( , , ou ) en utilisant la propriété. Lorsque la zone de contenu <xref:System.Windows.Controls.Expander> <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> est effondrée, seul le bouton et son bouton de bascule apparaissent. Un <xref:System.Windows.Controls.Button> contrôle qui affiche une flèche directionnelle est utilisé comme un bouton de bascule pour étendre ou effondrer la zone de contenu. Une fois <xref:System.Windows.Controls.Expander> élargi, le tente d’afficher tout son contenu dans une zone de fenêtre.  
  
<a name="SettingSizeDimensionsonanExpanderinaPanel"></a>
## <a name="controlling-the-size-of-an-expander-in-a-panel"></a>Contrôler la taille d’un Expander dans un panneau  
 Si <xref:System.Windows.Controls.Expander> un contrôle est à l’intérieur d’un contrôle de <xref:System.Windows.Controls.Expander> mise <xref:System.Windows.Controls.Expander.ExpandDirection%2A> en page <xref:System.Windows.Controls.ExpandDirection.Down> qui <xref:System.Windows.Controls.ExpandDirection.Up>hérite <xref:System.Windows.Controls.Panel>de , tels que <xref:System.Windows.Controls.StackPanel>, ne spécifiez pas un <xref:System.Windows.FrameworkElement.Height%2A> sur le moment où la propriété est réglée à ou . De même, ne <xref:System.Windows.FrameworkElement.Width%2A> pas <xref:System.Windows.Controls.Expander> spécifier un sur le moment où la <xref:System.Windows.Controls.Expander.ExpandDirection%2A> propriété est réglée ou <xref:System.Windows.Controls.ExpandDirection.Left> <xref:System.Windows.Controls.ExpandDirection.Right>.  
  
 Lorsque vous définissez une <xref:System.Windows.Controls.Expander> dimension de taille sur un contrôle <xref:System.Windows.Controls.Expander> dans la direction où le contenu élargi est affiché, le contrôle de la zone qui est utilisée par le contenu et affiche une bordure autour d’elle. La bordure s’affiche même lorsque le contenu est réduit. Pour définir la taille de la zone de contenu <xref:System.Windows.Controls.Expander>élargie, définissez les dimensions de <xref:System.Windows.Controls.ScrollViewer> taille sur le contenu de la , ou si vous voulez faire défiler la capacité, sur le contenu qui entoure le contenu.  
  
 Lorsqu’un <xref:System.Windows.Controls.Expander> contrôle est le <xref:System.Windows.Controls.DockPanel> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] dernier élément <xref:System.Windows.Controls.Expander> d’un , définit <xref:System.Windows.Controls.DockPanel>automatiquement les dimensions pour égaler la zone restante de la . Pour éviter ce comportement <xref:System.Windows.Controls.DockPanel.LastChildFill%2A> par défaut, `false`définissez la propriété <xref:System.Windows.Controls.Expander> sur l’objet <xref:System.Windows.Controls.DockPanel> <xref:System.Windows.Controls.DockPanel>à , ou assurez-vous que le n’est pas le dernier élément dans un .  
  
<a name="CreatingScrollableContent"></a>
## <a name="creating-scrollable-content"></a>Créer du contenu déroulant  
 Si le contenu est trop grand pour la taille de la <xref:System.Windows.Controls.Expander> zone <xref:System.Windows.Controls.ScrollViewer> de contenu, vous pouvez envelopper le contenu d’un dans un afin de fournir du contenu défilement. Le <xref:System.Windows.Controls.Expander> contrôle ne fournit pas automatiquement la capacité de défilement. L’illustration suivante <xref:System.Windows.Controls.Expander> montre un <xref:System.Windows.Controls.ScrollViewer> contrôle qui contient un contrôle.  
  
 **Expander dans un ScrollViewer**  
  
 ![Capture d’écran qui montre un expandeur avec ScrollBar.](./media/expander-overview/expander-scrollbar-control.jpg)  
  
 Lorsque vous <xref:System.Windows.Controls.Expander> placez <xref:System.Windows.Controls.ScrollViewer>un contrôle <xref:System.Windows.Controls.ScrollViewer> dans un , définissez la <xref:System.Windows.Controls.Expander> propriété dimension qui <xref:System.Windows.Controls.Expander> correspond à la direction dans laquelle le contenu s’ouvre à la taille de la zone de contenu. Par exemple, si <xref:System.Windows.Controls.Expander.ExpandDirection%2A> vous définissez la propriété sur <xref:System.Windows.Controls.Expander> le à <xref:System.Windows.Controls.ExpandDirection.Down> (la zone de contenu s’ouvre), définissez la <xref:System.Windows.FrameworkElement.Height%2A> propriété sur le <xref:System.Windows.Controls.ScrollViewer> contrôle à la hauteur requise pour la zone de contenu. Si vous définissez plutôt la dimension <xref:System.Windows.Controls.ScrollViewer> de hauteur sur le contenu lui-même, ne reconnaît pas ce paramètre et, par conséquent, ne fournit pas de contenu défilement.  
  
 L’exemple suivant montre <xref:System.Windows.Controls.Expander> comment créer un contrôle qui <xref:System.Windows.Controls.ScrollViewer> a un contenu complexe et qui contient un contrôle. Cet exemple <xref:System.Windows.Controls.Expander> crée un qui est comme l’illustration au début de cette section.  
  
 [!code-csharp[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ExpanderRichContent#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ExpanderRichContent/VisualBasic/Window1.xaml.vb#1)]
 [!code-xaml[ExpanderRichContent#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#1)]  
  
<a name="UsingtheAlignmentProperties"></a>
## <a name="using-the-alignment-properties"></a>Utiliser les propriétés d’alignement  
 Vous pouvez aligner le <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> contenu en <xref:System.Windows.Controls.Expander> définissant le et les propriétés sur le contrôle. Lorsque vous définissez ces propriétés, l’alignement s’applique à l’en-tête ainsi qu’au contenu développé.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Expander>
- <xref:System.Windows.Controls.ExpandDirection>
- [Sujets comment se passer](expander-how-to-topics.md)
