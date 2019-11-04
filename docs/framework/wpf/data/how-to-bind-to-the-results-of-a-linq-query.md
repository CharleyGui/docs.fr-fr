---
title: "Comment : effectuer une liaison avec les résultats d'une requête LINQ"
ms.date: 03/30/2017
helpviewer_keywords:
- running a LINQ query [WPF], bind to results
- binding to LINQ query results [WPF]
ms.assetid: ff2844d9-17ed-4ea6-aab1-5111af0bc684
ms.openlocfilehash: d21ac5f366e001ea76d6eda64ed62583248796f6
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454413"
---
# <a name="how-to-bind-to-the-results-of-a-linq-query"></a>Comment : effectuer une liaison avec les résultats d'une requête LINQ

Cet exemple montre comment exécuter une requête LINQ, puis établir une liaison avec les résultats.

## <a name="example"></a>Exemple

L’exemple suivant crée deux zones de liste. La première zone de liste contient trois éléments de liste.

[!code-xaml[LinqExample#UI](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml#ui)]

La sélection d’un élément de la première zone de liste appelle le gestionnaire d’événements suivant. Dans cet exemple, `Tasks` est une collection d’objets `Task`. La classe `Task` a une propriété nommée `Priority`. Ce gestionnaire d’événements exécute une requête LINQ qui retourne la collection d’objets `Task` ayant la valeur de priorité sélectionnée, puis le définit comme <xref:System.Windows.FrameworkElement.DataContext%2A>:

[!code-csharp[LinqExample#Using](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#using)]
[!code-csharp[LinqExample#Tasks](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#tasks)]
[!code-csharp[LinqExample#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/LinqExample/CSharp/Window1.xaml.cs#handler)]

La deuxième zone de liste est liée à cette collection, car sa valeur <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> est définie sur `{Binding}`. En conséquence, il affiche la collection retournée (selon le `myTaskTemplate` <xref:System.Windows.DataTemplate>).

## <a name="see-also"></a>Voir aussi

- [Rendre des données disponibles pour la liaison en XAML](how-to-make-data-available-for-binding-in-xaml.md)
- [Effectuer une liaison à une collection et afficher des informations basées sur la sélection](how-to-bind-to-a-collection-and-display-information-based-on-selection.md)
- [Nouveautés de WPF version 4.5](../getting-started/whats-new.md)
- [Vue d’ensemble de la liaison de données](../../../desktop-wpf/data/data-binding-overview.md)
