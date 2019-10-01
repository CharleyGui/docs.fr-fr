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
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="87215-102">Procédure : Effectuer une liaison à une source de données ADO.NET</span><span class="sxs-lookup"><span data-stu-id="87215-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="87215-103">Cet exemple montre comment lier un contrôle [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> à un ADO.NET `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="87215-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="87215-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="87215-104">Example</span></span>

<span data-ttu-id="87215-105">Dans cet exemple, un objet `OleDbConnection` est utilisé pour se connecter à la source de données qui est un fichier `Access MDB` spécifié dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="87215-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="87215-106">Une fois la connexion établie, un objet `OleDbDataAdapter` est créé.</span><span class="sxs-lookup"><span data-stu-id="87215-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="87215-107">L’objet `OleDbDataAdapter` exécute une instruction SELECT langage SQL (SQL) pour récupérer le jeu d’enregistrements de la base de données.</span><span class="sxs-lookup"><span data-stu-id="87215-107">The `OleDbDataAdapter` object executes a select Structured Query Language (SQL) statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="87215-108">Les résultats de la commande SQL sont stockés dans un `DataTable` du `DataSet` en appelant la méthode `Fill` de l' `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="87215-108">The results from the SQL command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="87215-109">Dans cet exemple, la `DataTable` est nommée `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="87215-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="87215-110">L’exemple définit ensuite la propriété <xref:System.Windows.FrameworkElement.DataContext%2A> de la <xref:System.Windows.Controls.ListBox> sur l’objet `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="87215-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="87215-111">Nous pouvons ensuite lier la propriété <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> de la <xref:System.Windows.Controls.ListBox> à `BookTable` du `DataSet` :</span><span class="sxs-lookup"><span data-stu-id="87215-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="87215-112">`BookItemTemplate` est la <xref:System.Windows.DataTemplate> qui définit la façon dont les données s’affichent :</span><span class="sxs-lookup"><span data-stu-id="87215-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="87215-113">`IntColorConverter` convertit un `int` en une couleur.</span><span class="sxs-lookup"><span data-stu-id="87215-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="87215-114">Avec l’utilisation de ce convertisseur, la couleur <xref:System.Windows.Controls.TextBlock.Background%2A> du troisième <xref:System.Windows.Controls.TextBlock> s’affiche en vert si la valeur de `NumPages` est inférieure à 350 et rouge dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="87215-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="87215-115">L’implémentation du convertisseur n’est pas décrite ici.</span><span class="sxs-lookup"><span data-stu-id="87215-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="87215-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="87215-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="87215-117">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="87215-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="87215-118">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="87215-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
