---
title: 'Procédure : Effectuer une liaison à une source de données ADO.NET'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
ms.openlocfilehash: dbe34cba8f01320fbf37beea65ed95656e09395c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697142"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a>Procédure : Effectuer une liaison à une source de données ADO.NET

Cet exemple montre comment lier un contrôle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> à un ADO.NET `DataSet`.

## <a name="example"></a>Exemple

Dans cet exemple, un objet `OleDbConnection` est utilisé pour se connecter à la source de données qui est un fichier `Access MDB` spécifié dans la chaîne de connexion. Une fois la connexion établie, un objet `OleDbDataAdapter` est créé. L’objet `OleDbDataAdapter` exécute une instruction SELECT langage SQL (SQL) pour récupérer le jeu d’enregistrements de la base de données. Les résultats de la commande SQL sont stockés dans un `DataTable` du `DataSet` en appelant la méthode `Fill` de l' `OleDbDataAdapter`. Dans cet exemple, la `DataTable` est nommée `BookTable`. L’exemple définit ensuite la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> de la <xref:System.Windows.Controls.ListBox> sur l’objet `DataSet`.

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

Nous pouvons ensuite lier la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de la <xref:System.Windows.Controls.ListBox> à `BookTable` du `DataSet` :

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

`BookItemTemplate` est la <xref:System.Windows.DataTemplate> qui définit la façon dont les données s’affichent :

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

`IntColorConverter` convertit un `int` en une couleur. Avec l’utilisation de ce convertisseur, la couleur <xref:System.Windows.Controls.TextBlock.Background%2A> du troisième <xref:System.Windows.Controls.TextBlock> s’affiche en vert si la valeur de `NumPages` est inférieure à 350 et rouge dans le cas contraire. L’implémentation du convertisseur n’est pas décrite ici.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Data.BindingListCollectionView>
- [Vue d’ensemble de la liaison de données](data-binding-overview.md)
- [Rubriques de guide pratique](data-binding-how-to-topics.md)
