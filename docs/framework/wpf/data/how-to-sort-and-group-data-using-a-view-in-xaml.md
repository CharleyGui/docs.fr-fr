---
title: "Comment : trier et grouper des données à l'aide d'une vue en XAML"
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 9e42dd330535f71438ab7af3dca9d078e9dfd8d3
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460128"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>Comment : trier et grouper des données à l'aide d'une vue en XAML
Cet exemple montre comment créer une vue d’une collection de données dans [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Les vues permettent les fonctionnalités de regroupement, de tri, de filtrage et la notion d’un élément actuel.  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la ressource statique nommée *places* est définie comme une collection d’objets *place* , dans laquelle chaque objet *place* est constitué d’un nom de ville et de l’État. Le préfixe *src* est mappé à l’espace de noms dans lequel *la source de* données est définie. Le préfixe *SCM* est mappé à `"clr-namespace:System.ComponentModel;assembly=WindowsBase"` et les *fichiers DAT* sont mappés à `"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`.  
  
 L’exemple suivant crée une vue de la collection de données qui est triée par nom de ville et regroupée par État.  
  
 [!code-xaml[CollectionViewSource#1](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 La vue peut ensuite être une source de liaison, comme dans l’exemple suivant :  
  
 [!code-xaml[CollectionViewSource#2](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 Pour les liaisons aux données XML définies dans une ressource <xref:System.Windows.Data.XmlDataProvider>, faites précéder le nom XML d’un symbole @.  
  
 [!code-xaml[CollectionViewSource#XDPChunk](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.CollectionViewSource>
- [Obtenir la vue par défaut d'une collection de données](how-to-get-the-default-view-of-a-data-collection.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
