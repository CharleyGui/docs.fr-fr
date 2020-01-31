---
title: Tri des données dans le contrôle DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742946"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d655b-102">Tri des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d655b-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="d655b-103">Par défaut, les utilisateurs peuvent trier les données d’un contrôle <xref:System.Windows.Forms.DataGridView> en cliquant sur l’en-tête d’une colonne de zone de texte (ou en appuyant sur F3 quand une cellule de zone de texte est axée sur .NET Framework 4.7.2 et versions ultérieures).</span><span class="sxs-lookup"><span data-stu-id="d655b-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="d655b-104">Vous pouvez modifier la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode> de colonnes spécifiques pour permettre aux utilisateurs de trier par d’autres types de colonnes lorsqu’il est logique de le faire.</span><span class="sxs-lookup"><span data-stu-id="d655b-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="d655b-105">Vous pouvez également trier les données par programmation par n’importe quelle colonne ou par plusieurs colonnes.</span><span class="sxs-lookup"><span data-stu-id="d655b-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d655b-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="d655b-106">In this section</span></span>

[<span data-ttu-id="d655b-107">Modes de tri des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d655b-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="d655b-108">Décrit les options de tri des données dans le contrôle.</span><span class="sxs-lookup"><span data-stu-id="d655b-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="d655b-109">Comment : définir les modes de tri des colonnes du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d655b-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="d655b-110">Décrit comment permettre aux utilisateurs de trier par par défaut des colonnes qui ne peuvent pas être triées.</span><span class="sxs-lookup"><span data-stu-id="d655b-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="d655b-111">Guide pratique pour personnaliser le tri dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d655b-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="d655b-112">Décrit comment trier des données par programmation et comment personnaliser le tri à l’aide de l’événement <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> ou en implémentant l’interface <xref:System.Collections.IComparer>.</span><span class="sxs-lookup"><span data-stu-id="d655b-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="d655b-113">Reference</span><span class="sxs-lookup"><span data-stu-id="d655b-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="d655b-114">Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="d655b-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="d655b-115">Fournit une documentation de référence pour la méthode <xref:System.Windows.Forms.DataGridView.Sort%2A>.</span><span class="sxs-lookup"><span data-stu-id="d655b-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="d655b-116">Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="d655b-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="d655b-117">Fournit une documentation de référence pour l’énumération <xref:System.Windows.Forms.DataGridViewColumnSortMode>.</span><span class="sxs-lookup"><span data-stu-id="d655b-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="d655b-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d655b-118">See also</span></span>

- [<span data-ttu-id="d655b-119">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="d655b-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="d655b-120">Types de colonnes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d655b-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
