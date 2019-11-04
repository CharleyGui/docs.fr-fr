---
title: 'Comment : implémenter une classe CompositeCollection'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], CompositeCollection class
ms.assetid: 0d8fc84c-7920-427f-8ad7-d55ca656c170
ms.openlocfilehash: b3450cdc476b7090251a06b5b2b2718d29e18209
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454029"
---
# <a name="how-to-implement-a-compositecollection"></a>Comment : implémenter une classe CompositeCollection
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment afficher plusieurs collections et éléments sous la forme d’une liste à l’aide de la classe <xref:System.Windows.Data.CompositeCollection>. Dans cet exemple, `GreekGods` est une <xref:System.Collections.ObjectModel.ObservableCollection%601> d' `GreekGod` objets personnalisés. Les modèles de données sont définis de façon à ce que `GreekGod` objets et les objets de `GreekHero` apparaissent respectivement avec une couleur d’arrière-plan jaune et cyan.  
  
 [!code-xaml[CompositeCollections#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CompositeCollections/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.CollectionContainer>
- <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>
- <xref:System.Windows.Data.XmlDataProvider>
- <xref:System.Windows.DataTemplate>
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
