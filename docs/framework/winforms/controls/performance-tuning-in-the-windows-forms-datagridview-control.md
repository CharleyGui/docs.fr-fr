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
# <a name="performance-tuning-in-the-windows-forms-datagridview-control"></a>Réglage des performances dans le contrôle DataGridView Windows Forms
Lorsque vous travaillez avec de grandes quantités de données, le contrôle `DataGridView` peut consommer une grande quantité de mémoire en surcharge, à moins que vous ne l’utilisiez avec prudence. Sur les clients disposant d’une mémoire limitée, vous pouvez éviter une certaine surcharge en évitant les fonctionnalités qui présentent un coût de mémoire élevé. Vous pouvez également gérer une partie ou l’ensemble des tâches de maintenance et de récupération des données vous-même en utilisant le mode virtuel afin de personnaliser l’utilisation de la mémoire pour votre scénario.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Meilleures pratiques pour la mise à l'échelle du contrôle DataGridView Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 Décrit comment utiliser le contrôle `DataGridView` d’une manière qui évite des pénalités de performances et d’utilisation de la mémoire inutiles Lorsque vous travaillez avec de grandes quantités de données.  
  
 [Mode virtuel dans le contrôle DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)  
 Décrit comment utiliser le mode virtuel pour compléter ou remplacer le mécanisme de liaison de données standard.  
  
 [Procédure pas à pas : implémentation du mode virtuel dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-wf-datagridview-control.md)  
 Décrit comment implémenter des gestionnaires pour plusieurs événements en mode virtuel. Montre également comment implémenter une restauration et une validation au niveau des lignes pour les modifications de l’utilisateur.  
  
 [Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 Explique comment charger des données à la demande, ce qui est utile lorsque vous avez plus de données à afficher que la mémoire disponible du client.  
  
## <a name="reference"></a>Référence  
 <xref:System.Windows.Forms.DataGridView>  
 Fournit une documentation de référence pour le contrôle <xref:System.Windows.Forms.DataGridView>.  
  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 Fournit une documentation de référence pour la propriété <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>.  
  
## <a name="see-also"></a>Voir aussi

- [DataGridView, contrôle](datagridview-control-windows-forms.md)
- [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
