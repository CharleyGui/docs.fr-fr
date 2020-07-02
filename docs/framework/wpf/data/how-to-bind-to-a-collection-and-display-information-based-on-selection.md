---
title: 'Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection'
description: Suivez cet exemple pour savoir comment effectuer une liaison à une collection et afficher des informations basées sur la sélection dans le Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: fb8757ee6818a2812308a0a132fa9d06951ad52e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619609"
---
# <a name="how-to-bind-to-a-collection-and-display-information-based-on-selection"></a>Comment : effectuer une liaison à une collection et afficher des informations basées sur la sélection
Dans un scénario maître-détail simple, vous avez une liaison de données <xref:System.Windows.Controls.ItemsControl> telle que <xref:System.Windows.Controls.ListBox> . En fonction de la sélection de l’utilisateur, vous pouvez afficher plus d’informations sur l’élément sélectionné. Cet exemple montre comment implémenter ce scénario.  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, `People` est un <xref:System.Collections.ObjectModel.ObservableCollection%601> de `Person` classes. Cette `Person` classe contient trois propriétés : `FirstName` , `LastName` et `HomeTown` , tout type `string` .  
  
 [!code-xaml[CollectionBinding#Source](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#source)]  
[!code-xaml[CollectionBinding#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#ui)]  
  
 Le <xref:System.Windows.Controls.ContentControl> utilise les éléments suivants <xref:System.Windows.DataTemplate> qui définissent le mode de présentation des informations d’un `Person` :  
  
 [!code-xaml[CollectionBinding#DetailTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Window1.xaml#detailtemplate)]  
  
 La capture d’écran suivante illustre ce que produit l’exemple. La <xref:System.Windows.Controls.ContentControl> affiche les autres propriétés de la personne sélectionnée.  
  
 ![Liaison à une collection](./media/databinding-collectionbindingsample.png "DataBinding_CollectionBindingSample")  
  
 Les deux points à noter dans cet exemple sont les suivants :  
  
1. <xref:System.Windows.Controls.ListBox>Et la <xref:System.Windows.Controls.ContentControl> liaison à la même source. Les <xref:System.Windows.Data.Binding.Path%2A> Propriétés des deux liaisons ne sont pas spécifiées, car les deux contrôles sont en liaison avec l’objet de collection entier.  
  
2. Vous devez affecter la valeur à la propriété pour que <xref:System.Windows.Controls.Primitives.Selector.IsSynchronizedWithCurrentItem%2A> `true` cela fonctionne. La définition de cette propriété permet de s’assurer que l’élément sélectionné est toujours défini en tant que <xref:System.Windows.Controls.ItemCollection.CurrentItem%2A> . Sinon, si le <xref:System.Windows.Controls.ListBox> récupère les données à partir d’un <xref:System.Windows.Data.CollectionViewSource> , il synchronise automatiquement la sélection et la devise.  
  
 Notez que la `Person` classe substitue la `ToString` méthode de la façon suivante. Par défaut, le <xref:System.Windows.Controls.ListBox> appelle `ToString` et affiche une représentation sous forme de chaîne de chaque objet de la collection liée. C’est pourquoi chaque `Person` apparaît comme un prénom dans le <xref:System.Windows.Controls.ListBox> .  
  
 [!code-csharp[CollectionBinding#ToString](~/samples/snippets/csharp/VS_Snippets_Wpf/CollectionBinding/CSharp/Data.cs#tostring)]
 [!code-vb[CollectionBinding#ToString](~/samples/snippets/visualbasic/VS_Snippets_Wpf/CollectionBinding/VisualBasic/Person.vb#tostring)]  
  
## <a name="see-also"></a>Voir aussi

- [Utiliser le modèle maître/détail avec des données hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-data.md)
- [Utiliser le modèle maître/détail avec des données XML hiérarchiques](how-to-use-the-master-detail-pattern-with-hierarchical-xml-data.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
- [Vue d'ensemble des modèles de données](data-templating-overview.md)
- [Rubriques de procédures](data-binding-how-to-topics.md)
