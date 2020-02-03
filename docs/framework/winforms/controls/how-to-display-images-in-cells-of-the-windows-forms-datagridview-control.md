---
title: Afficher des images dans les cellules du contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
ms.openlocfilehash: e0e125c816877875b80e0f20887d9beee443577a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740277"
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="b2c81-102">Comment : afficher des images dans les cellules du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2c81-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="b2c81-103">Une image ou un graphique est l’une des valeurs que vous pouvez afficher dans une ligne de données.</span><span class="sxs-lookup"><span data-stu-id="b2c81-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="b2c81-104">Souvent, ces graphiques prennent la forme de la photographie d’un employé ou d’un logo d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="b2c81-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="b2c81-105">L’incorporation d’images est simple lorsque vous affichez des données dans le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="b2c81-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="b2c81-106">Le contrôle <xref:System.Windows.Forms.DataGridView> gère en mode natif tout format d’image pris en charge par la classe <xref:System.Drawing.Image>, ainsi que le format d’image OLE utilisé par certaines bases de données.</span><span class="sxs-lookup"><span data-stu-id="b2c81-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="b2c81-107">Si la source de données du contrôle <xref:System.Windows.Forms.DataGridView> possède une colonne d’images, elles sont automatiquement affichées par le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="b2c81-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="b2c81-108">L’exemple de code suivant montre comment extraire une icône d’une ressource incorporée et la convertir en bitmap pour l’afficher dans chaque cellule d’une colonne d’image.</span><span class="sxs-lookup"><span data-stu-id="b2c81-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="b2c81-109">Pour obtenir un autre exemple qui remplace les valeurs de cellules textuelles par les images correspondantes, consultez [Comment : personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="b2c81-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2c81-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="b2c81-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2c81-111">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="b2c81-111">Compiling the Code</span></span>  
 <span data-ttu-id="b2c81-112">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="b2c81-112">This example requires:</span></span>  
  
- <span data-ttu-id="b2c81-113">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="b2c81-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="b2c81-114">Une ressource icône incorporée nommée `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="b2c81-114">An embedded icon resource named `tree.ico`.</span></span>  
  
- <span data-ttu-id="b2c81-115">des références aux assemblys <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType> et <xref:System.Drawing?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b2c81-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c81-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2c81-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="b2c81-117">Fonctionnalités de base liées aux colonnes, lignes et cellules dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2c81-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="b2c81-118">Guide pratique pour personnaliser la mise en forme des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b2c81-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
