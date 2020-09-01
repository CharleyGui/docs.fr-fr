---
title: 'Comment : styliser une ligne dans un ListView qui utilise un GridView'
ms.date: 03/30/2017
helpviewer_keywords:
- GridView controls [WPF], styling rows
- styling rows in ListViews implementing GridViews [WPF]
- ListView controls [WPF], styling rows with GridViews
ms.assetid: 2e406ba2-70a0-4e62-841f-0934859de76e
ms.openlocfilehash: 4b8b8e2f1b2d7207a37205d981bf2dab3f65122e
ms.sourcegitcommit: e0803b8975d3eb12e735a5d07637020dd6dac5ef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89271943"
---
# <a name="how-to-style-a-row-in-a-listview-that-implements-a-gridview"></a>Comment : appliquer un style à une ligne dans un ListView implémentant un GridView
Cet exemple montre comment définir le style d’une ligne dans un <xref:System.Windows.Controls.ListView> contrôle qui utilise un <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.ListView.View%2A> mode.  
  
## <a name="example"></a>Exemple  
 Vous pouvez affecter un style à une ligne dans un <xref:System.Windows.Controls.ListView> contrôle en définissant un <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> sur le <xref:System.Windows.Controls.ListView> contrôle. Définissez le style de ses éléments représentés en tant qu' <xref:System.Windows.Controls.ListViewItem> objets. Le <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> référence les <xref:System.Windows.Controls.ControlTemplate> objets utilisés pour afficher le contenu de la ligne.  
  
 L’exemple complet, qui extrait les exemples suivants, affiche une collection d’informations de chanson stockées dans une base de données XML. Chaque chanson de la base de données est associée à un champ d’évaluation. La valeur de ce champ spécifie comment afficher une ligne d’informations sur la chanson.  
  
 L’exemple suivant montre comment définir <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pour les <xref:System.Windows.Controls.ListViewItem> objets qui représentent les chansons de la collection de chansons. Les <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> <xref:System.Windows.Controls.ControlTemplate> objets de référence qui spécifient comment afficher une ligne d’informations de chanson.  
  
 [!code-xaml[ListViewItemStyleSnippet#ItemContainerStyle](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#itemcontainerstyle)]  
  
 L’exemple suivant montre un <xref:System.Windows.Controls.ControlTemplate> qui ajoute la chaîne `"Strongly Recommended"` de texte à la ligne. Ce modèle est référencé dans <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> et s’affiche lorsque l’évaluation de la chanson a une valeur de 5 (cinq). Le <xref:System.Windows.Controls.ControlTemplate> comprend un <xref:System.Windows.Controls.GridViewRowPresenter> objet qui dispose le contenu de la ligne dans les colonnes, comme défini par le <xref:System.Windows.Controls.GridView> mode d’affichage.  
  
 [!code-xaml[ListViewItemStyleSnippet#ControlTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#controltemplate)]  
  
 L’exemple suivant définit <xref:System.Windows.Controls.GridView> .  
  
 [!code-xaml[ListViewItemStyleSnippet#GridView](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewItemStyleSnippet/CS/Window1.xaml#gridview)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.GridView>
- [Rubriques de procédures](listview-how-to-topics.md)
- [Vue d'ensemble de ListView](listview-overview.md)
- [Application d'un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
