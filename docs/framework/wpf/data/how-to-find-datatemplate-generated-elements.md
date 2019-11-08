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
ms.openlocfilehash: 2cb3d73574cd207c0e06abe15f6a953a67cd5c78
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73733427"
---
# <a name="how-to-find-datatemplate-generated-elements"></a>Comment : rechercher des éléments générés par DataTemplate
Cet exemple montre comment rechercher des éléments générés par un <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, il existe un <xref:System.Windows.Controls.ListBox> lié à des données XML :  
  
 [!code-xaml[FindGeneratedItems#LB](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#lb)]  
  
 Le <xref:System.Windows.Controls.ListBox> utilise les <xref:System.Windows.DataTemplate>suivantes :  
  
 [!code-xaml[FindGeneratedItems#DT](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml#dt)]  
  
 Si vous souhaitez récupérer l’élément <xref:System.Windows.Controls.TextBlock> généré par le <xref:System.Windows.DataTemplate> d’un certain <xref:System.Windows.Controls.ListBoxItem>, vous devez obtenir le <xref:System.Windows.Controls.ListBoxItem>, Rechercher le <xref:System.Windows.Controls.ContentPresenter> dans ce <xref:System.Windows.Controls.ListBoxItem>, puis appeler <xref:System.Windows.FrameworkTemplate.FindName%2A> sur le <xref:System.Windows.DataTemplate> qui est défini sur ce <xref:System.Windows.Controls.ContentPresenter>. L’exemple suivant montre comment effectuer ces étapes. À des fins de démonstration, cet exemple crée une boîte de message qui montre le contenu textuel du bloc de texte généré par <xref:System.Windows.DataTemplate>.  
  
 [!code-csharp[FindGeneratedItems#DTFindElement](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#dtfindelement)]
 [!code-vb[FindGeneratedItems#DTFindElement](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#dtfindelement)]  
  
 Voici l’implémentation de `FindVisualChild`, qui utilise les méthodes <xref:System.Windows.Media.VisualTreeHelper> :  
  
 [!code-csharp[FindGeneratedItems#FVC](~/samples/snippets/csharp/VS_Snippets_Wpf/FindGeneratedItems/CSharp/Window1.xaml.cs#fvc)]
 [!code-vb[FindGeneratedItems#FVC](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FindGeneratedItems/VisualBasic/Window1.xaml.vb#fvc)]  
  
## <a name="see-also"></a>Voir aussi

- [Guide pratique pour rechercher des éléments générés par ControlTemplate](../controls/how-to-find-controltemplate-generated-elements.md)
- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
- [Application d’un style et création de modèles](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Portées de nom XAML WPF](../advanced/wpf-xaml-namescopes.md)
- [Arborescences dans WPF](../advanced/trees-in-wpf.md)
