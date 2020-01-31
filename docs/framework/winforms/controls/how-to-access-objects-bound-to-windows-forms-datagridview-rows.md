---
title: accéder à des objets liés à des lignes DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- object binding [Windows Forms], accessing bound objects
- data grids [Windows Forms], accessing bound objects
- DataGridView control [Windows Forms], accessing objects bound to rows
ms.assetid: 0e05748f-4403-4eb8-8b2f-b098108181b5
ms.openlocfilehash: 0b9a4becb78ae817141728467c1e9ea5b693476d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743166"
---
# <a name="how-to-access-objects-bound-to-windows-forms-datagridview-rows"></a><span data-ttu-id="6c361-102">Comment : accéder à des objets liés à des lignes DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c361-102">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>
<span data-ttu-id="6c361-103">Il est parfois utile d’afficher une table d’informations stockée dans une collection d’objets métier.</span><span class="sxs-lookup"><span data-stu-id="6c361-103">Sometimes it is useful to display a table of information stored in a collection of business objects.</span></span> <span data-ttu-id="6c361-104">Quand vous liez un contrôle <xref:System.Windows.Forms.DataGridView> à une telle collection, chaque propriété publique est affichée dans sa propre colonne, à moins que la propriété n'ait été marquée comme non consultable avec un <xref:System.ComponentModel.BrowsableAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6c361-104">When you bind a <xref:System.Windows.Forms.DataGridView> control to such a collection, each public property is displayed in its own column unless the property has been marked non-browsable with a <xref:System.ComponentModel.BrowsableAttribute>.</span></span> <span data-ttu-id="6c361-105">Par exemple, une collection d’objets `Customer` aurait des colonnes telles que **Nom** et **Adresse**.</span><span class="sxs-lookup"><span data-stu-id="6c361-105">For example, a collection of `Customer` objects would have columns such as **Name** and **Address**.</span></span>  
  
 <span data-ttu-id="6c361-106">Si ces objets contiennent des informations supplémentaires et du code auquel vous souhaitez accéder, vous pouvez l'atteindre via des objets de ligne.</span><span class="sxs-lookup"><span data-stu-id="6c361-106">If these objects contain additional information and code that you want to access, you can reach it through row objects.</span></span> <span data-ttu-id="6c361-107">Dans l'exemple de code suivant, les utilisateurs peuvent sélectionner plusieurs lignes et cliquer sur un bouton pour envoyer une facture à chacun des clients correspondants.</span><span class="sxs-lookup"><span data-stu-id="6c361-107">In the following code example, users can select multiple rows and click a button to send an invoice to each of the corresponding customers.</span></span>  
  
### <a name="to-access-row-bound-objects"></a><span data-ttu-id="6c361-108">Pour accéder à des objets liés à une ligne</span><span class="sxs-lookup"><span data-stu-id="6c361-108">To access row-bound objects</span></span>  
  
- <span data-ttu-id="6c361-109">Utilisez la propriété <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6c361-109">Use the <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#10)]  
  
## <a name="example"></a><span data-ttu-id="6c361-110">Exemple</span><span class="sxs-lookup"><span data-stu-id="6c361-110">Example</span></span>  
 <span data-ttu-id="6c361-111">L'exemple de code complet comprend une implémentation `Customer` simple et lie le <xref:System.Windows.Forms.DataGridView> à un <xref:System.Collections.ArrayList> contenant quelques objets `Customer`.</span><span class="sxs-lookup"><span data-stu-id="6c361-111">The complete code example includes a simple `Customer` implementation and binds the <xref:System.Windows.Forms.DataGridView> to an <xref:System.Collections.ArrayList> containing a few `Customer` objects.</span></span> <span data-ttu-id="6c361-112">Le gestionnaire d’événements <xref:System.Windows.Forms.Control.Click> du <xref:System.Windows.Forms.Button?displayProperty=nameWithType> doit accéder aux objets `Customer` par l’intermédiaire des lignes, car la collection de clients n’est pas accessible en dehors du gestionnaire d’événements <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6c361-112">The <xref:System.Windows.Forms.Control.Click> event handler of the <xref:System.Windows.Forms.Button?displayProperty=nameWithType> must access the `Customer` objects through the rows, because the customer collection is not accessible outside the <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> event handler.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/CS/datagridviewobjectbinding.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewObjectBinding#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewObjectBinding/VB/datagridviewobjectbinding.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c361-113">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6c361-113">Compiling the Code</span></span>  
 <span data-ttu-id="6c361-114">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="6c361-114">This example requires:</span></span>  
  
- <span data-ttu-id="6c361-115">des références aux assemblys System et System.Windows.Forms ;</span><span class="sxs-lookup"><span data-stu-id="6c361-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c361-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6c361-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewRow>
- <xref:System.Windows.Forms.DataGridViewRow.DataBoundItem%2A?displayProperty=nameWithType>
- [<span data-ttu-id="6c361-117">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c361-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6c361-118">Comment : lier des objets aux contrôles DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6c361-118">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)
