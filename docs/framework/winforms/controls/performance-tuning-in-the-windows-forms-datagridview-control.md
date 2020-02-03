---
title: Réglage des performances dans le contrôle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], performance tuning
- performance [Windows Forms], DataGridView control
- performance tuning [Windows Forms], data grids
ms.assetid: 6ccbff28-a0ff-41e4-b601-61b31b61851d
ms.openlocfilehash: 77ad86c4cd606bcf074473c97371ec27bcc5605b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744277"
---
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="6256e-102">Réglage des performances dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6256e-102">Performance Tuning in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="6256e-103">Lorsque vous travaillez avec de grandes quantités de données, le contrôle `DataGridView` peut consommer une grande quantité de mémoire en surcharge, à moins que vous ne l’utilisiez avec prudence.</span><span class="sxs-lookup"><span data-stu-id="6256e-103">When working with large amounts of data, the `DataGridView` control can consume a large amount of memory in overhead, unless you use it carefully.</span></span> <span data-ttu-id="6256e-104">Sur les clients disposant d’une mémoire limitée, vous pouvez éviter une certaine surcharge en évitant les fonctionnalités qui présentent un coût de mémoire élevé.</span><span class="sxs-lookup"><span data-stu-id="6256e-104">On clients with limited memory, you can avoid some of this overhead by avoiding features that have a high memory cost.</span></span> <span data-ttu-id="6256e-105">Vous pouvez également gérer une partie ou l’ensemble des tâches de maintenance et de récupération des données vous-même en utilisant le mode virtuel afin de personnaliser l’utilisation de la mémoire pour votre scénario.</span><span class="sxs-lookup"><span data-stu-id="6256e-105">You can also manage some or all of the data maintenance and retrieval tasks yourself using virtual mode in order to customize the memory usage for your scenario.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6256e-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="6256e-106">In This Section</span></span>  
 [<span data-ttu-id="6256e-107">Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6256e-107">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6256e-108">Décrit comment utiliser le contrôle `DataGridView` d’une manière qui évite des pénalités de performances et d’utilisation de la mémoire inutiles Lorsque vous travaillez avec de grandes quantités de données.</span><span class="sxs-lookup"><span data-stu-id="6256e-108">Describes how to use the `DataGridView` control in a way that avoids unnecessary memory usage and performance penalties when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="6256e-109">Mode virtuel dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6256e-109">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6256e-110">Décrit comment utiliser le mode virtuel pour compléter ou remplacer le mécanisme de liaison de données standard.</span><span class="sxs-lookup"><span data-stu-id="6256e-110">Describes how to use virtual mode to supplement or replace the standard data-binding mechanism.</span></span>  
  
 [<span data-ttu-id="6256e-111">Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6256e-111">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-wf-datagridview-control.md)  
 <span data-ttu-id="6256e-112">Décrit comment implémenter des gestionnaires pour plusieurs événements en mode virtuel.</span><span class="sxs-lookup"><span data-stu-id="6256e-112">Describes how to implement handlers for several virtual-mode events.</span></span> <span data-ttu-id="6256e-113">Montre également comment implémenter une restauration et une validation au niveau des lignes pour les modifications de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="6256e-113">Also demonstrates how to implement row-level rollback and commit for user edits.</span></span>  
  
 [<span data-ttu-id="6256e-114">Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6256e-114">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 <span data-ttu-id="6256e-115">Explique comment charger des données à la demande, ce qui est utile lorsque vous avez plus de données à afficher que la mémoire disponible du client.</span><span class="sxs-lookup"><span data-stu-id="6256e-115">Describes how to load data on demand, which is useful when you have more data to display than the available client memory can store.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6256e-116">Référence</span><span class="sxs-lookup"><span data-stu-id="6256e-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="6256e-117">Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="6256e-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <span data-ttu-id="6256e-118">Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="6256e-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6256e-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6256e-119">See also</span></span>

- [<span data-ttu-id="6256e-120">DataGridView, contrôle</span><span class="sxs-lookup"><span data-stu-id="6256e-120">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="6256e-121">Modes d’affichage des données dans le contrôle DataGridView Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6256e-121">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)
