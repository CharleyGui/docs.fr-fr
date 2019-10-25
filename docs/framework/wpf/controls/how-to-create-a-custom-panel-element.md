---
title: 'Comment : créer un élément Panel personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Panel control [WPF]
- custom Panel elements [WPF]
ms.assetid: e0df4f1e-8c07-4e86-89a3-e22acfffdc2a
ms.openlocfilehash: 31edc75114c5dad613e5b65e7d8b051e2c3713af
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799149"
---
# <a name="how-to-create-a-custom-panel-element"></a>Comment : créer un élément Panel personnalisé
## <a name="example"></a>Exemple  
 Cet exemple montre comment substituer le comportement de disposition par défaut de l’élément <xref:System.Windows.Controls.Panel> et créer des éléments de disposition personnalisés dérivés de <xref:System.Windows.Controls.Panel>.  
  
 L’exemple définit un élément <xref:System.Windows.Controls.Panel> personnalisé simple appelé `PlotPanel`, qui positionne des éléments enfants en fonction de deux coordonnées x et y codées en dur. Dans cet exemple, `x` et `y` ont tous les deux la valeur `50`; par conséquent, tous les éléments enfants sont positionnés à cet emplacement sur les axes x et y.  
  
 Pour implémenter des comportements de <xref:System.Windows.Controls.Panel> personnalisés, l’exemple utilise les méthodes <xref:System.Windows.FrameworkElement.MeasureOverride%2A> et <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>. Chaque méthode retourne les données <xref:System.Windows.Size> nécessaires pour positionner et restituer les éléments enfants.  
  
 [!code-cpp[PlotPanel#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PlotPanel/CPP/PlotPanel.cpp#1)]
 [!code-csharp[PlotPanel#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PlotPanel/CSharp/PlotPanel.cs#1)]
 [!code-vb[PlotPanel#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PlotPanel/VisualBasic/PlotPanel.vb#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.Panel>
- [Vue d’ensemble de Panel](panels-overview.md)
