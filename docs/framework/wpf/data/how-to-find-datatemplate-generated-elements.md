---
title: 'Comment : rechercher des éléments générés par DataTemplate'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- finding DataTemplate elements [WPF]
- DataTemplate [WPF]
ms.assetid: bfcd564e-5e9e-451e-8641-a9b5c3cfac90
ms.openlocfilehash: 3b222880aa4eda32502e3dcece2fa5c0b57b7a51
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646434"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Comment : rechercher des éléments générés par DataTemplate
Cet exemple montre comment trouver des <xref:System.Windows.DataTemplate>éléments qui sont générés par un .  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, <xref:System.Windows.Controls.ListBox> il ya un qui est lié à certaines données XML:  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 Les <xref:System.Windows.Controls.ListBox> utilisations <xref:System.Windows.DataTemplate>suivantes :  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Si vous voulez <xref:System.Windows.Controls.TextBlock> récupérer l’élément généré <xref:System.Windows.DataTemplate> par le <xref:System.Windows.Controls.ListBoxItem>d’un certain , vous devez obtenir le <xref:System.Windows.Controls.ListBoxItem>, trouver l’intérieur <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.ListBoxItem>de cela , puis faire appel <xref:System.Windows.FrameworkTemplate.FindName%2A> à ce <xref:System.Windows.DataTemplate> qui est fixé sur ce <xref:System.Windows.Controls.ContentPresenter>. L’exemple suivant montre comment effectuer ces étapes. À des fins de démonstration, cet exemple crée <xref:System.Windows.DataTemplate>une boîte de message qui affiche le contenu texte du bloc de texte généré.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Ce qui suit `FindVisualChild`est la <xref:System.Windows.Media.VisualTreeHelper> mise en œuvre de , qui utilise les méthodes:  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour rechercher des éléments générés par ControlTemplate](../controls/how-to-find-controltemplate-generated-elements.md)
- [Aperçu de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de procédures](data-binding-how-to-topics.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Portées de nom XAML WPF](../advanced/wpf-xaml-namescopes.md)
- [Arborescences dans WPF](../advanced/trees-in-wpf.md)
