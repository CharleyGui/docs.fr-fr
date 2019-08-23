---
title: 'Procédure : Manipuler les groupes de lignes d’un tableau avec la propriété RowGroups'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- row groups [WPF], manipulating through RowGroups property
- RowGroups property [WPF], manipulating row groups
- documents [WPF], manipulating row groups through RowGroups property
- properties [WPF], RowGroups [WPF], manipulating row groups
ms.assetid: ea61440f-08ae-44ed-b314-5716aaaae3ed
ms.openlocfilehash: 195920af64888bd3671b45befc0fe4cde463ae7b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913559"
---
# <a name="how-to-manipulate-a-tables-row-groups-through-the-rowgroups-property"></a><span data-ttu-id="03a96-102">Procédure : Manipuler les groupes de lignes d’un tableau avec la propriété RowGroups</span><span class="sxs-lookup"><span data-stu-id="03a96-102">How to: Manipulate a Table's Row Groups through the RowGroups Property</span></span>
<span data-ttu-id="03a96-103">Cet exemple montre quelques-unes des opérations les plus courantes qui peuvent être effectuées sur les groupes de lignes d' <xref:System.Windows.Documents.Table.RowGroups%2A> une table par le biais de la propriété.</span><span class="sxs-lookup"><span data-stu-id="03a96-103">This example demonstrates some of the more common operations that can be performed on a table's row groups through the <xref:System.Windows.Documents.Table.RowGroups%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03a96-104">Exemples</span><span class="sxs-lookup"><span data-stu-id="03a96-104">Example</span></span>  
 <span data-ttu-id="03a96-105">L’exemple suivant crée une table, puis utilise la <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> méthode pour ajouter des colonnes à la collection de <xref:System.Windows.Documents.Table.RowGroups%2A> la table.</span><span class="sxs-lookup"><span data-stu-id="03a96-105">The following example creates a new table and then uses the <xref:System.Windows.Documents.TableRowGroupCollection.Add%2A> method to add columns to the table's <xref:System.Windows.Documents.Table.RowGroups%2A> collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_add)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Add](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_add)]  
  
## <a name="example"></a><span data-ttu-id="03a96-106">Exemples</span><span class="sxs-lookup"><span data-stu-id="03a96-106">Example</span></span>  
 <span data-ttu-id="03a96-107">L’exemple suivant insère un nouveau <xref:System.Windows.Documents.TableRowGroup>.</span><span class="sxs-lookup"><span data-stu-id="03a96-107">The following example inserts a new <xref:System.Windows.Documents.TableRowGroup>.</span></span>  <span data-ttu-id="03a96-108">La nouvelle colonne est insérée à la position d’index 0, ce qui en fait le nouveau groupe de la première ligne dans la table.</span><span class="sxs-lookup"><span data-stu-id="03a96-108">The new column is inserted at index position 0, making it the new first row group in the table.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03a96-109">La <xref:System.Windows.Documents.TableRowGroupCollection> collection utilise l’indexation standard de base zéro.</span><span class="sxs-lookup"><span data-stu-id="03a96-109">The <xref:System.Windows.Documents.TableRowGroupCollection> collection uses standard zero-based indexing.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_insert)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Insert](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_insert)]  
  
## <a name="example"></a><span data-ttu-id="03a96-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="03a96-110">Example</span></span>  
 <span data-ttu-id="03a96-111">L’exemple suivant ajoute plusieurs lignes à un particulier <xref:System.Windows.Documents.TableRowGroup> (spécifié par index) dans la table.</span><span class="sxs-lookup"><span data-stu-id="03a96-111">The following example adds several rows to a particular <xref:System.Windows.Documents.TableRowGroup> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addrows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addrows)]  
  
## <a name="example"></a><span data-ttu-id="03a96-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="03a96-112">Example</span></span>  
 <span data-ttu-id="03a96-113">L’exemple suivant accède à des propriétés arbitraires sur les lignes du premier groupe de lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="03a96-113">The following example accesses some arbitrary properties on rows in the first row group in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_maniprows)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipRows](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_maniprows)]  
  
## <a name="example"></a><span data-ttu-id="03a96-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="03a96-114">Example</span></span>  
 <span data-ttu-id="03a96-115">L’exemple suivant ajoute plusieurs cellules à un particulier <xref:System.Windows.Documents.TableRow> (spécifié par index) dans la table.</span><span class="sxs-lookup"><span data-stu-id="03a96-115">The following example adds several cells to a particular <xref:System.Windows.Documents.TableRow> (specified by index) in the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_addcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_AddCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_addcells)]  
  
## <a name="example"></a><span data-ttu-id="03a96-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="03a96-116">Example</span></span>  
 <span data-ttu-id="03a96-117">L’exemple suivant accède à des méthodes et des propriétés arbitraires sur les cellules de la première ligne dans le premier groupe de lignes.</span><span class="sxs-lookup"><span data-stu-id="03a96-117">The following example access some arbitrary methods and properties on cells in the first row in the first row group.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_manipcells)]
 [!code-vb[TableSnippets2#_Table_RowGroups_ManipCells](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_manipcells)]  
  
## <a name="example"></a><span data-ttu-id="03a96-118">Exemple</span><span class="sxs-lookup"><span data-stu-id="03a96-118">Example</span></span>  
 <span data-ttu-id="03a96-119">L’exemple suivant retourne le nombre d' <xref:System.Windows.Documents.TableRowGroup> éléments hébergés par la table.</span><span class="sxs-lookup"><span data-stu-id="03a96-119">The following example returns the number of <xref:System.Windows.Documents.TableRowGroup> elements hosted by the table.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_count)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Count](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_count)]  
  
## <a name="example"></a><span data-ttu-id="03a96-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="03a96-120">Example</span></span>  
 <span data-ttu-id="03a96-121">L’exemple suivant supprime un groupe de lignes particulier par référence.</span><span class="sxs-lookup"><span data-stu-id="03a96-121">The following example removes a particular row group by reference.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delref)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelRef](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delref)]  
  
## <a name="example"></a><span data-ttu-id="03a96-122">Exemples</span><span class="sxs-lookup"><span data-stu-id="03a96-122">Example</span></span>  
 <span data-ttu-id="03a96-123">L’exemple suivant supprime un groupe de lignes particulier par index.</span><span class="sxs-lookup"><span data-stu-id="03a96-123">The following example removes a particular row group by index.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_delindex)]
 [!code-vb[TableSnippets2#_Table_RowGroups_DelIndex](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_delindex)]  
  
## <a name="example"></a><span data-ttu-id="03a96-124">Exemples</span><span class="sxs-lookup"><span data-stu-id="03a96-124">Example</span></span>  
 <span data-ttu-id="03a96-125">L’exemple suivant supprime tous les groupes de lignes de la collection de groupes de lignes de la table.</span><span class="sxs-lookup"><span data-stu-id="03a96-125">The following example removes all row groups from the table's row groups collection.</span></span>  
  
 [!code-csharp[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/csharp/VS_Snippets_Wpf/TableSnippets2/CSharp/Window1.xaml.cs#_table_rowgroups_clear)]
 [!code-vb[TableSnippets2#_Table_RowGroups_Clear](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TableSnippets2/visualbasic/window1.xaml.vb#_table_rowgroups_clear)]  
  
## <a name="see-also"></a><span data-ttu-id="03a96-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="03a96-126">See also</span></span>

- [<span data-ttu-id="03a96-127">Guide pratique : Manipuler des éléments de contenu de Flow par le biais de la propriété Inlines</span><span class="sxs-lookup"><span data-stu-id="03a96-127">How-to: Manipulate Flow Content Elements through the Inlines Property</span></span>](how-to-manipulate-table-row-groups-through-the-rowgroups-property.md)
- [<span data-ttu-id="03a96-128">Manipuler un FlowDocument avec la propriété Blocks</span><span class="sxs-lookup"><span data-stu-id="03a96-128">Manipulate a FlowDocument through the Blocks Property</span></span>](how-to-manipulate-a-flowdocument-through-the-blocks-property.md)
- [<span data-ttu-id="03a96-129">Manipuler les colonnes d’un tableau avec la propriété Columns</span><span class="sxs-lookup"><span data-stu-id="03a96-129">Manipulate a Table's Columns through the Columns Property</span></span>](how-to-manipulate-table-columns-through-the-columns-property.md)
