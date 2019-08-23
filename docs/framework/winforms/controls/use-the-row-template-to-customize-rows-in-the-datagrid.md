---
title: 'Procédure : utiliser le modèle de ligne pour personnaliser des lignes dans le contrôle DataGridView Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], customizing rows
- DataGridView control [Windows Forms], customizing rows
ms.assetid: 6db61607-7e57-4a84-8d63-9d6a7ed7f9ff
ms.openlocfilehash: 0dba318e6aa35761f4e9471fdb13b65644747b57
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966502"
---
# <a name="how-to-use-the-row-template-to-customize-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="20d73-102">Procédure : utiliser le modèle de ligne pour personnaliser des lignes dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20d73-102">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="20d73-103">Le <xref:System.Windows.Forms.DataGridView> contrôle utilise le modèle de ligne comme base pour toutes les lignes qu’il ajoute au contrôle via une liaison de données ou lorsque vous appelez <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> la méthode sans spécifier de ligne existante à utiliser.</span><span class="sxs-lookup"><span data-stu-id="20d73-103">The <xref:System.Windows.Forms.DataGridView> control uses the row template as a basis for all rows that it adds to the control either through data binding or when you call the <xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A?displayProperty=nameWithType> method without specifying an existing row to use.</span></span>  
  
 <span data-ttu-id="20d73-104">Le modèle de ligne vous donne un meilleur contrôle sur l’apparence et le comportement des <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> lignes que la propriété fournit.</span><span class="sxs-lookup"><span data-stu-id="20d73-104">The row template gives you greater control over the appearance and behavior of rows than the <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> property provides.</span></span> <span data-ttu-id="20d73-105">Avec le modèle de ligne, vous pouvez définir <xref:System.Windows.Forms.DataGridViewRow> toutes les propriétés <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>, y compris.</span><span class="sxs-lookup"><span data-stu-id="20d73-105">With the row template, you can set any <xref:System.Windows.Forms.DataGridViewRow> properties, including <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A>.</span></span>  
  
 <span data-ttu-id="20d73-106">Dans certains cas, vous devez utiliser le modèle de ligne pour obtenir un effet particulier.</span><span class="sxs-lookup"><span data-stu-id="20d73-106">There are some situations where you must use the row template to achieve a particular effect.</span></span> <span data-ttu-id="20d73-107">Par exemple, les informations de hauteur de ligne ne peuvent <xref:System.Windows.Forms.DataGridViewCellStyle>pas être stockées dans un. vous devez donc utiliser un modèle de ligne pour modifier la hauteur par défaut utilisée par toutes les lignes.</span><span class="sxs-lookup"><span data-stu-id="20d73-107">For example, row height information cannot be stored in a <xref:System.Windows.Forms.DataGridViewCellStyle>, so you must use a row template to change the default height used by all rows.</span></span> <span data-ttu-id="20d73-108">Le modèle de ligne est également utile lorsque vous créez vos propres classes dérivées de <xref:System.Windows.Forms.DataGridViewRow> et que vous souhaitez que votre type personnalisé soit utilisé lorsque de nouvelles lignes sont ajoutées au contrôle.</span><span class="sxs-lookup"><span data-stu-id="20d73-108">The row template is also useful when you create your own classes derived from <xref:System.Windows.Forms.DataGridViewRow> and you want your custom type used when new rows are added to the control.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20d73-109">Le modèle de ligne est utilisé uniquement lors de l’ajout de lignes.</span><span class="sxs-lookup"><span data-stu-id="20d73-109">The row template is used only when rows are added.</span></span> <span data-ttu-id="20d73-110">Vous ne pouvez pas modifier les lignes existantes en modifiant le modèle de ligne.</span><span class="sxs-lookup"><span data-stu-id="20d73-110">You cannot change existing rows by changing the row template.</span></span>  
  
### <a name="to-use-the-row-template"></a><span data-ttu-id="20d73-111">Pour utiliser le modèle de ligne</span><span class="sxs-lookup"><span data-stu-id="20d73-111">To use the row template</span></span>  
  
- <span data-ttu-id="20d73-112">Définissez les propriétés sur l’objet récupéré à <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> partir de la propriété.</span><span class="sxs-lookup"><span data-stu-id="20d73-112">Set properties on the object retrieved from the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CPP/datagridviewrowtemplate.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/CS/datagridviewrowtemplate.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridView.RowTemplate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.RowTemplate/VB/datagridviewrowtemplate.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="20d73-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="20d73-113">Compiling the Code</span></span>  
 <span data-ttu-id="20d73-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="20d73-114">This example requires:</span></span>  
  
- <span data-ttu-id="20d73-115">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="20d73-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="20d73-116">des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="20d73-116">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20d73-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="20d73-117">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>
- [<span data-ttu-id="20d73-118">Mises en forme et styles de base dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20d73-118">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="20d73-119">Styles de cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="20d73-119">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
