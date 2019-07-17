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
ms.openlocfilehash: 96f846db3f705972a4749460bf2c410483258572
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238427"
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="37e47-102">Procédure : Effectuer une liaison à une source de données ADO.NET</span><span class="sxs-lookup"><span data-stu-id="37e47-102">How to: Bind to an ADO.NET Data Source</span></span>

<span data-ttu-id="37e47-103">Cet exemple montre comment lier un [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> contrôle à un élément ADO.NET `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="37e47-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an ADO.NET `DataSet`.</span></span>

## <a name="example"></a><span data-ttu-id="37e47-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="37e47-104">Example</span></span>

<span data-ttu-id="37e47-105">Dans cet exemple, un objet `OleDbConnection` est utilisé pour se connecter à la source de données qui est un fichier `Access MDB` spécifié dans la chaîne de connexion.</span><span class="sxs-lookup"><span data-stu-id="37e47-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="37e47-106">Une fois la connexion établie, un objet `OleDbDataAdapter` est créé.</span><span class="sxs-lookup"><span data-stu-id="37e47-106">After the connection is established, an `OleDbDataAdapter` object is created.</span></span> <span data-ttu-id="37e47-107">L’objet `OleDbDataAdapter` exécute une instruction select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] pour extraire le recordset de la base de données.</span><span class="sxs-lookup"><span data-stu-id="37e47-107">The `OleDbDataAdapter` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="37e47-108">Les résultats de la commande [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] sont stockés dans une `DataTable` du `DataSet` en appelant la méthode `Fill` de l’`OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="37e47-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="37e47-109">Dans cet exemple, la `DataTable` est nommée `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="37e47-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="37e47-110">L’exemple définit ensuite la <xref:System.Windows.FrameworkElement.DataContext%2A> propriété de la <xref:System.Windows.Controls.ListBox> à la `DataSet` objet.</span><span class="sxs-lookup"><span data-stu-id="37e47-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>

[!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
[!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]

<span data-ttu-id="37e47-111">Vous pouvez ensuite lier le <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> propriété de la <xref:System.Windows.Controls.ListBox> à `BookTable` de la `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="37e47-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>

[!code-xaml[ADODataSet#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]

<span data-ttu-id="37e47-112">`BookItemTemplate` est le <xref:System.Windows.DataTemplate> qui définit comment les données s’affichent :</span><span class="sxs-lookup"><span data-stu-id="37e47-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>

[!code-xaml[ADODataSet#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]

<span data-ttu-id="37e47-113">`IntColorConverter` convertit un `int` en une couleur.</span><span class="sxs-lookup"><span data-stu-id="37e47-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="37e47-114">Avec l’utilisation de ce convertisseur, le <xref:System.Windows.Controls.TextBlock.Background%2A> couleur du troisième <xref:System.Windows.Controls.TextBlock> apparaît en vert si la valeur de `NumPages` est inférieure à 350 et rouge dans le cas contraire.</span><span class="sxs-lookup"><span data-stu-id="37e47-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="37e47-115">L’implémentation du convertisseur n’est pas décrite ici.</span><span class="sxs-lookup"><span data-stu-id="37e47-115">The implementation of the converter is not shown here.</span></span>

## <a name="see-also"></a><span data-ttu-id="37e47-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="37e47-116">See also</span></span>

- <xref:System.Windows.Data.BindingListCollectionView>
- [<span data-ttu-id="37e47-117">Vue d’ensemble de la liaison de données</span><span class="sxs-lookup"><span data-stu-id="37e47-117">Data Binding Overview</span></span>](data-binding-overview.md)
- [<span data-ttu-id="37e47-118">Rubriques de guide pratique</span><span class="sxs-lookup"><span data-stu-id="37e47-118">How-to Topics</span></span>](data-binding-how-to-topics.md)
