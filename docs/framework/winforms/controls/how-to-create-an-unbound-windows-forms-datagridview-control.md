---
title: Créer un contrôle DataGridView indépendant
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: 0b477eba6d8455554d72dc7ec8cfce68a91add38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76730994"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="7f396-102">Comment : créer un contrôle DataGridView Windows Forms indépendant</span><span class="sxs-lookup"><span data-stu-id="7f396-102">How to: Create an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7f396-103">L'exemple de code suivant montre comment remplir un contrôle <xref:System.Windows.Forms.DataGridView> par programmation sans le lier à une source de données.</span><span class="sxs-lookup"><span data-stu-id="7f396-103">The following code example demonstrates how to populate a <xref:System.Windows.Forms.DataGridView> control programmatically without binding it to a data source.</span></span> <span data-ttu-id="7f396-104">Cela est utile quand vous souhaitez afficher une petite quantité de données sous forme de tableau.</span><span class="sxs-lookup"><span data-stu-id="7f396-104">This is useful when you have a small amount of data that you want to display in a table format.</span></span>  
  
 <span data-ttu-id="7f396-105">Pour obtenir une explication complète de cet exemple de code, consultez [Procédure pas à pas : création d’un contrôle DataGridView Windows Forms non lié](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7f396-105">For a complete explanation of this code example, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f396-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="7f396-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7f396-107">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="7f396-107">Compiling the Code</span></span>  
 <span data-ttu-id="7f396-108">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="7f396-108">This example requires:</span></span>  
  
- <span data-ttu-id="7f396-109">Références aux assemblys System, System.Drawing et System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7f396-109">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f396-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f396-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="7f396-111">Procédure pas à pas : création d’un contrôle DataGridView Windows Forms non lié</span><span class="sxs-lookup"><span data-stu-id="7f396-111">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7f396-112">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f396-112">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7f396-113">Modes d’affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7f396-113">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
