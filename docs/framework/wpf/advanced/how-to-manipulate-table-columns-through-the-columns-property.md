---
title: 'Procédure : Manipuler les colonnes d’un tableau avec la propriété Columns'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- documents [WPF], manipulating table columns
- properties [WPF], Columns [WPF], manipulating table columns
- tables [WPF], manipulating columns
- Columns property [WPF]
ms.assetid: 3f8884f4-7e1f-456b-be06-fbd3cf469bf3
ms.openlocfilehash: 18a26c76688ebf668293cb1254404d6d2cf15208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913591"
---
# <a name="how-to-manipulate-a-tables-columns-through-the-columns-property"></a><span data-ttu-id="d0342-102">Procédure : Manipuler les colonnes d’un tableau avec la propriété Columns</span><span class="sxs-lookup"><span data-stu-id="d0342-102">How to: Manipulate a Table's Columns through the Columns Property</span></span>
<span data-ttu-id="d0342-103">Cet exemple montre quelques-unes des opérations les plus courantes qui peuvent être effectuées sur les colonnes d’une <xref:System.Windows.Documents.Table.Columns%2A> table par le biais de la propriété.</span><span class="sxs-lookup"><span data-stu-id="d0342-103">This example demonstrates some of the more common operations that can be performed on a table's columns through the <xref:System.Windows.Documents.Table.Columns%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0342-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="d0342-104">Example</span></span>  
 <span data-ttu-id="d0342-105">L’exemple suivant crée une table, puis utilise la <xref:System.Windows.Documents.TableColumnCollection.Add%2A> méthode pour ajouter des colonnes à la collection de <xref:System.Windows.Documents.Table.Columns%2A> la table.</span><span class="sxs-lookup"><span data-stu-id="d0342-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableColumnCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.Columns%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_add)]
 [!code-vb[TableSnippets2#_Table_Columns_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_add)]  
  
## <a name="example"></a><span data-ttu-id="d0342-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="d0342-106">Example</span></span>  
 <span data-ttu-id="d0342-107">L’exemple suivant insère un nouveau <xref:System.Windows.Documents.TableColumn>.</span><span class="sxs-lookup"><span data-stu-id="d0342-107">The following example inserts a new <xref:System.Windows.Documents.TableColumn>.</span></span>  <span data-ttu-id="d0342-108">La nouvelle colonne est insérée à la position d’index 0, ce qui en fait la nouvelle première colonne dans la table.</span><span class="sxs-lookup"><span data-stu-id="d0342-108">The new column is inserted at index position 0, making it the new first column in the table.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0342-109">La <xref:System.Windows.Documents.TableColumnCollection> collection utilise l’indexation standard de base zéro.</span><span class="sxs-lookup"><span data-stu-id="d0342-109">The <xref:System.Windows.Documents.TableColumnCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_insert)]
 [!code-vb[TableSnippets2#_Table_Columns_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_insert)]  
  
## <a name="example"></a><span data-ttu-id="d0342-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="d0342-110">Example</span></span>  
 <span data-ttu-id="d0342-111">L’exemple suivant accède à des propriétés arbitraires sur les colonnes <xref:System.Windows.Documents.TableColumnCollection> de la collection, en faisant référence à des colonnes spécifiques par index.</span><span class="sxs-lookup"><span data-stu-id="d0342-111">The following example accesses some arbitrary properties on columns in the <xref:System.Windows.Documents.TableColumnCollection> collection, referring to particular columns by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_manip)]
 [!code-vb[TableSnippets2#_Table_Columns_Manip](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_manip)]  
  
## <a name="example"></a><span data-ttu-id="d0342-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="d0342-112">Example</span></span>  
 <span data-ttu-id="d0342-113">L’exemple suivant obtient le nombre de colonnes actuellement hébergées par la table.</span><span class="sxs-lookup"><span data-stu-id="d0342-113">The following example gets the number of columns currently hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_count)]
 [!code-vb[TableSnippets2#_Table_Columns_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_count)]  
  
## <a name="example"></a><span data-ttu-id="d0342-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="d0342-114">Example</span></span>  
 <span data-ttu-id="d0342-115">L’exemple suivant supprime une colonne particulière par référence.</span><span class="sxs-lookup"><span data-stu-id="d0342-115">The following example removes a particular column by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delref)]
 [!code-vb[TableSnippets2#_Table_Columns_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delref)]  
  
## <a name="example"></a><span data-ttu-id="d0342-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="d0342-116">Example</span></span>  
 <span data-ttu-id="d0342-117">L’exemple suivant supprime une colonne particulière par index.</span><span class="sxs-lookup"><span data-stu-id="d0342-117">The following example removes a particular column by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_delindex)]
 [!code-vb[TableSnippets2#_Table_Columns_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_delindex)]  
  
## <a name="example"></a><span data-ttu-id="d0342-118">Exemples</span><span class="sxs-lookup"><span data-stu-id="d0342-118">Example</span></span>  
 <span data-ttu-id="d0342-119">L’exemple suivant supprime toutes les colonnes de la collection Columns de la table.</span><span class="sxs-lookup"><span data-stu-id="d0342-119">The following example removes all columns from the table's columns collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_columns_clear)]
 [!code-vb[TableSnippets2#_Table_Columns_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_columns_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="d0342-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d0342-120">See also</span></span>

- [<span data-ttu-id="d0342-121">Vue d’ensemble de Table</span><span class="sxs-lookup"><span data-stu-id="d0342-121">Table Overview</span></span>](table-overview.md)
- [<span data-ttu-id="d0342-122">Définir une table avec XAML</span><span class="sxs-lookup"><span data-stu-id="d0342-122">Define a Table with XAML</span></span>](how-to-define-a-table-with-xaml.md)
- [<span data-ttu-id="d0342-123">Générer une table par programmation</span><span class="sxs-lookup"><span data-stu-id="d0342-123">Build a Table Programmatically</span></span>](how-to-build-a-table-programmatically.md)
- [<span data-ttu-id="d0342-124">Manipuler les groupes de lignes d’un tableau avec la propriété RowGroups</span><span class="sxs-lookup"><span data-stu-id="d0342-124">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="d0342-125">Manipuler un FlowDocument avec la propriété Blocks</span><span class="sxs-lookup"><span data-stu-id="d0342-125">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="d0342-126">Manipuler les groupes de lignes d’un tableau avec la propriété RowGroups</span><span class="sxs-lookup"><span data-stu-id="d0342-126">Manipulate a Table's Row Groups through the RowGroups Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
