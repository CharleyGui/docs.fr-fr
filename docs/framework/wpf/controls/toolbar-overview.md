---
title: Vue d'ensemble de ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], ToolBar
- ToolBar control [WPF]
ms.assetid: a8edb32c-118d-4f31-b6e6-8899082b504b
ms.openlocfilehash: 460d4420d5faf849a8d05a94e0170aea384f69b4
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452693"
---
# <a name="toolbar-overview"></a>Vue d'ensemble de ToolBar
les contrôles <xref:System.Windows.Controls.ToolBar> sont des conteneurs pour un groupe de commandes ou de contrôles qui sont généralement liés dans leur fonction. Une <xref:System.Windows.Controls.ToolBar> contient généralement des boutons qui appellent des commandes.  

<a name="ToolBarControl"></a>   
## <a name="toolbar-control"></a>ToolBar, contrôle  
 Le contrôle de <xref:System.Windows.Controls.ToolBar> prend son nom de la disposition sous forme de barre des boutons ou autres contrôles dans une seule ligne ou colonne. les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> fournissent un mécanisme de dépassement de capacité qui place tous les éléments qui ne tiennent pas naturellement dans une <xref:System.Windows.Controls.ToolBar> à taille restreinte dans une zone de débordement spéciale. En outre, les contrôles [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.ToolBar> sont généralement utilisés avec le contrôle <xref:System.Windows.Controls.ToolBarTray> connexe, qui fournit un comportement de disposition spécial, ainsi que la prise en charge du dimensionnement et de l’Organisation des barres d’outils initiées par l’utilisateur.  
  
<a name="Creating_ToolBars"></a>   
## <a name="specifying-the-position-of-toolbars-in-a-toolbartray"></a>Spécifier la position des contrôles ToolBar dans un ToolBarTray  
 Utilisez les propriétés <xref:System.Windows.Controls.ToolBar.Band%2A> et <xref:System.Windows.Controls.ToolBar.BandIndex%2A> pour positionner le <xref:System.Windows.Controls.ToolBar> dans le <xref:System.Windows.Controls.ToolBarTray>. <xref:System.Windows.Controls.ToolBar.Band%2A> indique la position dans laquelle la <xref:System.Windows.Controls.ToolBar> est placée dans son <xref:System.Windows.Controls.ToolBarTray>parent. <xref:System.Windows.Controls.ToolBar.BandIndex%2A> indique l’ordre dans lequel la <xref:System.Windows.Controls.ToolBar> est placée dans sa bande. L’exemple suivant montre comment utiliser cette propriété pour placer <xref:System.Windows.Controls.ToolBar> contrôles à l’intérieur d’une <xref:System.Windows.Controls.ToolBarTray>.  
  
 [!code-xaml[ToolBarExample#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#2)]  
  
<a name="ToolBars_with_Overflow_Items"></a>   
## <a name="toolbars-with-overflow-items"></a>Contrôles ToolBar avec éléments de dépassement  
 Souvent <xref:System.Windows.Controls.ToolBar> contrôles contiennent plus d’éléments que la taille de la barre d’outils ne peut l’être. Dans ce cas, le <xref:System.Windows.Controls.ToolBar> affiche un bouton de dépassement de capacité. Pour afficher les éléments de dépassement de capacité, un utilisateur clique sur le bouton de dépassement de capacité et les éléments s’affichent dans une fenêtre contextuelle sous le <xref:System.Windows.Controls.ToolBar>. Le graphique suivant montre un <xref:System.Windows.Controls.ToolBar> avec des éléments de dépassement de capacité :  
  
 ![Capture d’écran montrant une barre d’outils avec des éléments de dépassement de capacité.](./media/toolbar-overview/toolbar-overflow-items.png)  
  
 Vous pouvez spécifier quand un élément d’une barre d’outils est placé dans le panneau de dépassement de capacité en affectant à la propriété jointe <xref:System.Windows.Controls.ToolBar.OverflowMode%2A?displayProperty=nameWithType> la valeur <xref:System.Windows.Controls.OverflowMode.Always?displayProperty=nameWithType>, <xref:System.Windows.Controls.OverflowMode.Never?displayProperty=nameWithType>ou <xref:System.Windows.Controls.OverflowMode.AsNeeded?displayProperty=nameWithType>. L’exemple suivant spécifie que les quatre derniers boutons de la barre d’outils doivent toujours se trouver sur le panneau de dépassement.  
  
 [!code-xaml[ToolBarExample#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBarExample/CS/Pane1.xaml#3)]  
  
 Le <xref:System.Windows.Controls.ToolBar> utilise un <xref:System.Windows.Controls.Primitives.ToolBarPanel> et un <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> dans son <xref:System.Windows.Controls.ControlTemplate>.  La <xref:System.Windows.Controls.Primitives.ToolBarPanel> est responsable de la disposition des éléments dans la barre d’outils.  La <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel> est responsable de la disposition des éléments qui ne tiennent pas sur le <xref:System.Windows.Controls.ToolBar>. Pour obtenir un exemple de <xref:System.Windows.Controls.ControlTemplate> pour un <xref:System.Windows.Controls.ToolBar>, consultez.  
  
 [Styles et modèles ToolBar](toolbar-styles-and-templates.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Primitives.ToolBarPanel>
- <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>
- [Donner un style aux contrôles d'une barre d'outils](how-to-style-controls-on-a-toolbar.md)
- [Exemple de galerie de contrôles WPF](https://github.com/Microsoft/WPF-Samples/tree/master/Getting%20Started/ControlsAndLayout)
