---
title: Vue d'ensemble de ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: b5498b8b88c7403ffe51256a57544261de3ace08
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186617"
---
# <a name="toolbar-overview"></a>Vue d'ensemble de ToolBar
<xref:System.Windows.Controls.ToolBar>sont des conteneurs pour un groupe de commandes ou de contrôles qui sont généralement liés dans leur fonction. A <xref:System.Windows.Controls.ToolBar> contient généralement des boutons qui invoquent des commandes.  

<a name="ToolBarControl"></a>
## <a name="toolbar-control"></a>ToolBar, contrôle  
 Le <xref:System.Windows.Controls.ToolBar> contrôle tire son nom de l’arrangement de barre-comme des boutons ou d’autres contrôles dans une seule rangée ou colonne. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.ToolBar> les contrôles fournissent un mécanisme de débordement qui place tous <xref:System.Windows.Controls.ToolBar> les éléments qui ne s’adaptent pas naturellement dans une zone de taille limitée dans une zone de débordement spéciale. En [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> outre, les contrôles <xref:System.Windows.Controls.ToolBarTray> sont généralement utilisés avec le contrôle connexe, qui fournit un comportement de mise en page spécial ainsi que le soutien pour l’utilisateur initié dimensionnement et l’organisation des barres d’outils.  
  
<a name="Creating_ToolBars"></a>
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Spécifier la position des contrôles ToolBar dans un ToolBarTray  
 Utilisez <xref:System.Windows.Controls.ToolBar.Band%2A> le <xref:System.Windows.Controls.ToolBar.BandIndex%2A> et les <xref:System.Windows.Controls.ToolBar> propriétés pour positionner le dans le <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A>indique la position <xref:System.Windows.Controls.ToolBar> dans laquelle le <xref:System.Windows.Controls.ToolBarTray>est placé dans son parent . <xref:System.Windows.Controls.ToolBar.BandIndex%2A>indique l’ordre <xref:System.Windows.Controls.ToolBar> dans lequel le est placé dans sa bande. L’exemple suivant montre comment <xref:System.Windows.Controls.ToolBar> utiliser cette <xref:System.Windows.Controls.ToolBarTray>propriété pour placer des contrôles à l’intérieur d’un .  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>
## <a name="toolbars-with-overflow-items"></a>Contrôles ToolBar avec éléments de dépassement  
 Souvent, <xref:System.Windows.Controls.ToolBar> les commandes contiennent plus d’éléments que peut s’insérer dans la taille de la barre d’outils. Lorsque cela se <xref:System.Windows.Controls.ToolBar> produit, le bouton de débordement affiche un bouton de débordement. Pour voir les éléments de débordement, un utilisateur clique sur le bouton de <xref:System.Windows.Controls.ToolBar>débordement et les éléments sont affichés dans une fenêtre pop-up en dessous de la . Le graphique suivant <xref:System.Windows.Controls.ToolBar> montre un avec des éléments de débordement:  
  
 ![Capture d’écran qui montre une barre d’outils avec des éléments de débordement.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Vous pouvez spécifier quand un élément sur une <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> barre d’outils est placé sur le panneau de débordement en définissant la propriété ci-jointe à <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>, ou <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. L’exemple suivant spécifie que les quatre derniers boutons de la barre d’outils doivent toujours se trouver sur le panneau de dépassement.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 Les <xref:System.Windows.Controls.ToolBar> utilisations <xref:System.Windows.Controls.Primitives.ToolBarPanel> <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> a <xref:System.Windows.Controls.ControlTemplate>et a dans son .  Le <xref:System.Windows.Controls.Primitives.ToolBarPanel> est responsable de la disposition des éléments sur la barre d’outils.  Le <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> est responsable de la disposition des éléments <xref:System.Windows.Controls.ToolBar>qui ne correspondent pas sur le . Par exemple <xref:System.Windows.Controls.ControlTemplate> d’un <xref:System.Windows.Controls.ToolBar>pour un , voir  
  
 [Styles et modèles ToolBar](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Donner un style aux contrôles d'une barre d'outils](how-to-style-controls-on-a-toolbar.md)
- [Exemple de galerie de contrôles WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
