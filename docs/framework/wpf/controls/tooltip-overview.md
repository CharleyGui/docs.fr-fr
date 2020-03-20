---
title: Vue d'ensemble de l'info-bulle
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181947"
---
# <a name="tooltip-overview"></a>Vue d'ensemble de l'info-bulle
Un tooltip est une petite fenêtre pop-up qui apparaît quand un utilisateur met <xref:System.Windows.Controls.Button>en pause le pointeur de la souris sur un élément, comme sur un . Cette rubrique présente l’info-bulle et explique comment créer et personnaliser son contenu.  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a>Qu’est-ce qu’une info-bulle ?  
 Lorsqu’un utilisateur déplace le pointeur de la souris sur un élément qui contient une info-bulle, une fenêtre qui renferme le contenu de l’info-bulle (par exemple, le contenu texte qui décrit la fonction d’un contrôle) apparaît pendant un laps de temps spécifié. Si l’utilisateur éloigne le pointeur de la souris du contrôle, la fenêtre disparaît car le contenu de l’info-bulle ne peut pas recevoir le focus.  
  
 Une info-bulle peut contenir une ou plusieurs lignes de texte, des images, des formes ou un autre contenu visuel. Pour définir une info-bulle pour un contrôle, vous devez définir l’une des propriétés suivantes pour le contenu de l’info-bulle.  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 La propriété que vous utilisez dépend du fait que le <xref:System.Windows.FrameworkContentElement> contrôle <xref:System.Windows.FrameworkElement> qui définit l’outil hérite de la classe ou de la classe.  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a>Création d’une info-bulle  
 L’exemple suivant montre comment créer un outil <xref:System.Windows.FrameworkElement.ToolTip%2A> simple <xref:System.Windows.Controls.Button> en définissant la propriété pour un contrôle à une chaîne de texte.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 Vous pouvez également définir un <xref:System.Windows.Controls.ToolTip> tooltip comme un objet. L’exemple [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] suivant sert <xref:System.Windows.Controls.ToolTip> à spécifier <xref:System.Windows.Controls.TextBox> un objet comme outil d’un élément. Notez que l’exemple <xref:System.Windows.Controls.ToolTip> spécifie le par la mise en place de la <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> propriété.  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 L’exemple suivant utilise <xref:System.Windows.Controls.ToolTip> le code pour générer un objet. L’exemple <xref:System.Windows.Controls.ToolTip> crée`tt`un ( ) <xref:System.Windows.Controls.Button>et l’associe à un .  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 Vous pouvez également créer du contenu tooltip qui n’est pas défini comme un <xref:System.Windows.Controls.ToolTip> objet <xref:System.Windows.Controls.DockPanel>en enfermant le contenu de la pointe d’outil dans un élément de mise en page, tel qu’un . L’exemple suivant montre <xref:System.Windows.FrameworkElement.ToolTip%2A> comment définir <xref:System.Windows.Controls.TextBox> la propriété d’un <xref:System.Windows.Controls.DockPanel> contenu qui est inclus dans un contrôle.  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a>Utilisation des propriétés de l’info-bulle et des classes ToolTipService  
 Vous pouvez personnaliser le contenu de l’info-bulle en définissant des propriétés visuelles et en appliquant des styles. Si vous définissez le contenu <xref:System.Windows.Controls.ToolTip> de l’outil comme un <xref:System.Windows.Controls.ToolTip> objet, vous pouvez définir les propriétés visuelles de l’objet. Sinon, vous devez définir des <xref:System.Windows.Controls.ToolTipService> propriétés équivalentes attachées sur la classe.  
  
 Pour un exemple de la façon de définir les propriétés afin <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> de spécifier la position du contenu de l’outiltip en utilisant le et les propriétés, voir [Position un ToolTip](how-to-position-a-tooltip.md).  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a>Application d’un style à une info-bulle  
 Vous pouvez <xref:System.Windows.Controls.ToolTip> coiffer <xref:System.Windows.Style>un en définissant une coutume . L’exemple suivant <xref:System.Windows.Style> définit `Simple` un appelé qui montre <xref:System.Windows.Controls.ToolTip> comment compenser le placement <xref:System.Windows.Controls.Control.Background%2A> <xref:System.Windows.Controls.Control.Foreground%2A>de <xref:System.Windows.Controls.Control.FontSize%2A>la <xref:System.Windows.Controls.Control.FontWeight%2A>et de changer son apparence en fixant le , , , et .  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a>Utilisation des propriétés d’intervalle de temps de ToolTipService  
 La <xref:System.Windows.Controls.ToolTipService> classe fournit les propriétés suivantes pour vous <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>de <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>définir les temps d’affichage tooltip: , , et .  
  
 Utilisez <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> les <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> propriétés et les propriétés <xref:System.Windows.Controls.ToolTip> pour spécifier un <xref:System.Windows.Controls.ToolTip> délai, généralement bref, avant qu’un n’apparaisse et aussi pour spécifier combien de temps un reste visible. Pour plus d’informations, consultez la page [Comment : différer l’affichage d’une info-bulle](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).  
  
 La <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriété détermine si les outils pour différents contrôles apparaissent sans un délai initial lorsque vous déplacez le pointeur de souris rapidement entre eux. Pour plus d’informations sur la <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> propriété, voir Utilisez la propriété [BetweenShowDelay](how-to-use-the-betweenshowdelay-property.md).  
  
 L’exemple suivant montre comment définir ces propriétés pour une info-bulle.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [Sujets comment se passer](tooltip-how-to-topics.md)
