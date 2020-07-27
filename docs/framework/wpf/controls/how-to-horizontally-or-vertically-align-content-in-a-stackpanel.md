---
title: 'Comment : aligner horizontalement ou verticalement le contenu dans un StackPanel'
description: Découvrez comment ajuster l’orientation du contenu dans un Windows Presentation Foundation StackPanel et la valeur HorizontalAlignment et VerticalAlignment du contenu enfant.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167624"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Comment : aligner horizontalement ou verticalement le contenu dans un StackPanel
Cet exemple montre comment ajuster le <xref:System.Windows.Controls.StackPanel.Orientation%2A> de contenu dans un <xref:System.Windows.Controls.StackPanel> élément et comment ajuster le <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> du contenu enfant.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant crée trois <xref:System.Windows.Controls.ListBox> éléments dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Chaque <xref:System.Windows.Controls.ListBox> représente les valeurs possibles des <xref:System.Windows.Controls.StackPanel.Orientation%2A> Propriétés, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> et <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> d’un <xref:System.Windows.Controls.StackPanel> . Quand un utilisateur sélectionne une valeur dans l’un des <xref:System.Windows.Controls.ListBox> éléments, la propriété associée du <xref:System.Windows.Controls.StackPanel> et de ses <xref:System.Windows.Controls.Button> éléments enfants changent.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Le fichier code-behind suivant définit les modifications apportées aux événements associés aux <xref:System.Windows.Controls.ListBox> modifications de sélection. <xref:System.Windows.Controls.StackPanel>est identifié par le <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Vue d'ensemble de Panel](panels-overview.md)
