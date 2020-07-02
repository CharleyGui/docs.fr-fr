---
title: Mettre en forme des données dans le contrôle DataGridView
description: Découvrez comment mettre en forme des valeurs de cellule à l’aide de la propriété DefaultCellStyle d’un contrôle DataGridView Windows Forms et de colonnes spécifiques dans un contrôle.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: d6105c1d1120876f854332e7a10106cc1caf6276
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622807"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="076d2-103">Comment : mettre en forme des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="076d2-103">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="076d2-104">Les procédures suivantes illustrent la mise en forme de base des valeurs de cellule à l’aide <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> de la propriété d’un <xref:System.Windows.Forms.DataGridView> contrôle et de colonnes spécifiques dans un contrôle.</span><span class="sxs-lookup"><span data-stu-id="076d2-104">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="076d2-105">Pour plus d’informations sur la mise en forme de données avancée, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="076d2-105">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="076d2-106">Pour mettre en forme des valeurs de devise et de date</span><span class="sxs-lookup"><span data-stu-id="076d2-106">To format currency and date values</span></span>  
  
- <span data-ttu-id="076d2-107">Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="076d2-107">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="076d2-108">L’exemple de code suivant définit le format des colonnes spécifiques à l’aide <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de la propriété des colonnes.</span><span class="sxs-lookup"><span data-stu-id="076d2-108">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="076d2-109">Les valeurs de la `UnitPrice` colonne s’affichent dans le format monétaire propre à la culture actuel, avec des valeurs négatives placées entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="076d2-109">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="076d2-110">Les valeurs de la `ShipDate` colonne s’affichent dans le format de date abrégé propre à la culture actuel.</span><span class="sxs-lookup"><span data-stu-id="076d2-110">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="076d2-111">Pour plus d’informations sur les <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> valeurs, consultez [mise en forme des types](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="076d2-111">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="076d2-112">Pour personnaliser l’affichage de valeurs de base de données null</span><span class="sxs-lookup"><span data-stu-id="076d2-112">To customize the display of null database values</span></span>  
  
- <span data-ttu-id="076d2-113">Définissez la propriété <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> d'un <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="076d2-113">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="076d2-114">L’exemple de code suivant utilise la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriété pour afficher « aucune entrée » dans toutes les cellules contenant des valeurs égales à <xref:System.DBNull.Value?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="076d2-114">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="076d2-115">Pour activer la fonction de retour automatique à la cellule dans des cellules textuelles</span><span class="sxs-lookup"><span data-stu-id="076d2-115">To enable wordwrap in text-based cells</span></span>  
  
- <span data-ttu-id="076d2-116">Affectez <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> à la propriété d’un <xref:System.Windows.Forms.DataGridViewCellStyle> la valeur de l’une des <xref:System.Windows.Forms.DataGridViewTriState> valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="076d2-116">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="076d2-117">L’exemple de code suivant utilise la <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriété pour définir le mode de retour à la ligne pour l’ensemble du contrôle.</span><span class="sxs-lookup"><span data-stu-id="076d2-117">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="076d2-118">Pour spécifier l’alignement du texte des cellules DataGridView</span><span class="sxs-lookup"><span data-stu-id="076d2-118">To specify the text alignment of DataGridView cells</span></span>  
  
- <span data-ttu-id="076d2-119">Affectez <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> à la propriété d’un <xref:System.Windows.Forms.DataGridViewCellStyle> la valeur de l’une des <xref:System.Windows.Forms.DataGridViewContentAlignment> valeurs d’énumération.</span><span class="sxs-lookup"><span data-stu-id="076d2-119">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="076d2-120">L’exemple de code suivant définit l’alignement d’une colonne spécifique à l’aide <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> de la propriété de la colonne.</span><span class="sxs-lookup"><span data-stu-id="076d2-120">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="076d2-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="076d2-121">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="076d2-122">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="076d2-122">Compiling the Code</span></span>  
 <span data-ttu-id="076d2-123">Ces exemples requièrent les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="076d2-123">These examples require:</span></span>  
  
- <span data-ttu-id="076d2-124">Un <xref:System.Windows.Forms.DataGridView> contrôle nommé `dataGridView1` qui contient une colonne nommée `UnitPrice` , une colonne nommée `ShipDate` et une colonne nommée `CustomerName` .</span><span class="sxs-lookup"><span data-stu-id="076d2-124">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
- <span data-ttu-id="076d2-125">des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="076d2-125">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="076d2-126">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="076d2-126">Robust Programming</span></span>  
 <span data-ttu-id="076d2-127">Pour une extensibilité maximale, vous devez partager des <xref:System.Windows.Forms.DataGridViewCellStyle> objets sur plusieurs lignes, colonnes ou cellules qui utilisent les mêmes styles plutôt que de définir séparément les propriétés de style de chaque élément.</span><span class="sxs-lookup"><span data-stu-id="076d2-127">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="076d2-128">Pour plus d'informations, consultez [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="076d2-128">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="076d2-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="076d2-129">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="076d2-130">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="076d2-130">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="076d2-131">Styles de cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="076d2-131">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="076d2-132">Mise en forme de données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="076d2-132">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="076d2-133">Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="076d2-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="076d2-134">Mise en forme des types</span><span class="sxs-lookup"><span data-stu-id="076d2-134">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
