---
title: 'Comment : appliquer un style à une ligne dans un ListView implémentant un GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 150988aab368e3ffef0107d29bea5ebc53163946
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459319"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Comment : appliquer un style à une ligne dans un ListView implémentant un GridView
Cet exemple montre comment appliquer un style à une ligne dans un contrôle de <xref:System.Windows.Controls.ListView> qui implémente un mode de <xref:System.Windows.Controls.ListView.View%2A> <xref:System.Windows.Controls.GridView>.  
  
## <a name="example"></a>Exemple  
 Vous pouvez affecter un style à une ligne dans un contrôle <xref:System.Windows.Controls.ListView> en définissant une <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> sur le contrôle <xref:System.Windows.Controls.ListView>. Définissez le style de ses éléments représentés en tant qu’objets <xref:System.Windows.Controls.ListViewItem>. Le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> référence les objets <xref:System.Windows.Controls.ControlTemplate> utilisés pour afficher le contenu de la ligne.  
  
 L’exemple complet, dont sont extraits les exemples suivants, affiche une collection d’informations sur des chansons, stockée dans une base de données [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. Chaque chanson de la base de données est associée à un champ d’évaluation. La valeur de ce champ spécifie comment afficher une ligne d’informations sur la chanson.  
  
 L’exemple suivant montre comment définir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour les objets <xref:System.Windows.Controls.ListViewItem> qui représentent les chansons de la collection de chansons. Le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> référence <xref:System.Windows.Controls.ControlTemplate> objets qui spécifient comment afficher une ligne d’informations de chanson.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 L’exemple suivant montre une <xref:System.Windows.Controls.ControlTemplate> qui ajoute la chaîne de texte `"Strongly Recommended"` à la ligne. Ce modèle est référencé dans le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> et s’affiche lorsque l’évaluation de la chanson a une valeur de 5 (cinq). Le <xref:System.Windows.Controls.ControlTemplate> comprend un objet <xref:System.Windows.Controls.GridViewRowPresenter> qui présente le contenu de la ligne dans les colonnes, comme défini par le mode d’affichage <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 L’exemple suivant définit <xref:System.Windows.Controls.GridView>.  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Rubriques de guide pratique](listview-how-to-topics.md)
- [Vue d’ensemble de ListView](listview-overview.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
