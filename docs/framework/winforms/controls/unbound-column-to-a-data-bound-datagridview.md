---
title: Ajouter une colonne indépendante à un contrôle DataGridView lié aux données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747065"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="6696c-102">Comment : ajouter une colonne indépendante à un contrôle DataGridView Windows Forms lié aux données</span><span class="sxs-lookup"><span data-stu-id="6696c-102">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6696c-103">Les données que vous affichez dans le contrôle <xref:System.Windows.Forms.DataGridView> proviennent normalement d'une source de données quelconque. Vous pouvez toutefois vouloir afficher une colonne de données qui ne provienne pas de la source de données.</span><span class="sxs-lookup"><span data-stu-id="6696c-103">The data you display in the <xref:System.Windows.Forms.DataGridView> control will normally come from a data source of some kind, but you might want to display a column of data that does not come from the data source.</span></span> <span data-ttu-id="6696c-104">Ce type de colonne est appelé colonne indépendante.</span><span class="sxs-lookup"><span data-stu-id="6696c-104">This kind of column is called an unbound column.</span></span> <span data-ttu-id="6696c-105">Les colonnes indépendantes peuvent prendre de nombreuses formes.</span><span class="sxs-lookup"><span data-stu-id="6696c-105">Unbound columns can take many forms.</span></span> <span data-ttu-id="6696c-106">Souvent, elles sont utilisées pour fournir un accès aux détails d'une ligne de données.</span><span class="sxs-lookup"><span data-stu-id="6696c-106">Frequently, they are used to provide access to the details of a data row.</span></span>  
  
 <span data-ttu-id="6696c-107">L’exemple de code suivant montre comment créer une colonne indépendante de boutons **Détails** pour afficher une table enfant associée à une ligne particulière dans une table parente quand vous implémentez un scénario maître/détail.</span><span class="sxs-lookup"><span data-stu-id="6696c-107">The following code example demonstrates how to create an unbound column of **Details** buttons to display a child table related to a particular row in a parent table when you implement a master/detail scenario.</span></span> <span data-ttu-id="6696c-108">Pour répondre aux clics de bouton, implémentez un gestionnaire d'événements <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> qui affiche un formulaire contenant la table enfant.</span><span class="sxs-lookup"><span data-stu-id="6696c-108">To respond to button clicks, implement a <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> event handler that displays a form containing the child table.</span></span>  
  
 <span data-ttu-id="6696c-109">Cette tâche est prise en charge dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6696c-109">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="6696c-110">Consultez également [Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="6696c-110">Also see [How to: Add and Remove Columns in the Windows Forms DataGridView Control Using the Designer](add-and-remove-columns-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6696c-111">Exemple</span><span class="sxs-lookup"><span data-stu-id="6696c-111">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6696c-112">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="6696c-112">Compiling the Code</span></span>  
 <span data-ttu-id="6696c-113">Cet exemple nécessite :</span><span class="sxs-lookup"><span data-stu-id="6696c-113">This example requires:</span></span>  
  
- <span data-ttu-id="6696c-114">un contrôle <xref:System.Windows.Forms.DataGridView> nommé `dataGridView1` ;</span><span class="sxs-lookup"><span data-stu-id="6696c-114">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="6696c-115">des références aux assemblys <xref:System?displayProperty=nameWithType> et <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6696c-115">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6696c-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6696c-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="6696c-117">Affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6696c-117">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6696c-118">Modes d’affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6696c-118">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
