---
title: 'Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data collections [WPF], selecting data for views
- data binding [WPF], creating views of data collections
- data binding [WPF], selecting data for views
- data binding [WPF], binding to collections
ms.assetid: 952a7d76-dd29-49e5-86f5-32c4530e70eb
ms.openlocfilehash: 032a1d98e1aa80ea755f5922f79d43a796e9697e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459146"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection
Dans un scénario maître-détail simple, vous avez un <xref:System.Windows.Controls.ItemsControl> lié aux données, tel qu’une <xref:System.Windows.Controls.ListBox>. En fonction de la sélection de l’utilisateur, vous pouvez afficher plus d’informations sur l’élément sélectionné. Cet exemple montre comment implémenter ce scénario.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, `People` est une <xref:System.Collections.ObjectModel.ObservableCollection%601> de `Person` classes. Cette classe `Person` contient trois propriétés : `FirstName`, `LastName`et `HomeTown`, tout type `string`.  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 L' <xref:System.Windows.Controls.ContentControl> utilise les <xref:System.Windows.DataTemplate> suivantes qui définissent le mode de présentation des informations d’un `Person` :  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 La capture d’écran suivante illustre ce que produit l’exemple. Le <xref:System.Windows.Controls.ContentControl> affiche les autres propriétés de la personne sélectionnée.  
  
 ![Liaison à une collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Les deux points à noter dans cet exemple sont les suivants :  
  
1. Le <xref:System.Windows.Controls.ListBox> et le <xref:System.Windows.Controls.ContentControl> être liés à la même source. Les propriétés <xref:System.Windows.Data.Binding.Path%2A> des deux liaisons ne sont pas spécifiées, car les deux contrôles sont en liaison avec l’objet de collection entier.  
  
2. Vous devez définir la propriété <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> sur `true` pour que cela fonctionne. La définition de cette propriété permet de s’assurer que l’élément sélectionné est toujours défini en tant que <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A>. Sinon, si le <xref:System.Windows.Controls.ListBox> obtient des données à partir d’un <xref:System.Windows.Data.CollectionViewSource>, il synchronise automatiquement la sélection et la devise.  
  
 Notez que la classe `Person` remplace la méthode `ToString` de la façon suivante. Par défaut, le <xref:System.Windows.Controls.ListBox> appelle `ToString` et affiche une représentation sous forme de chaîne de chaque objet de la collection liée. C’est pourquoi chaque `Person` apparaît en tant que prénom dans le <xref:System.Windows.Controls.ListBox>.  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Voir aussi

- [Utiliser le modèle maître/détail avec des données hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Utiliser le modèle maître/détail avec des données XML hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d’ensemble des modèles de données](data-templating-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
