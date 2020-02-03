---
title: Implémenter le mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
ms.openlocfilehash: bbe98d3c317a7625b36b729f0be23ea20f65dec0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745427"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a>Comment : implémenter le mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms
L'exemple de code suivant montre comment utiliser le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView> avec un cache de données qui charge des données à partir d'un serveur uniquement en cas de nécessité. Cet exemple est décrit en détail dans [implémentation du mode virtuel avec le chargement de données juste-à-temps dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System.Data, System.Xml et System.Windows.Forms ;  
  
- l'accès à un serveur sur lequel est installé l'exemple de base de données SQL Server Northwind.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [Implémentation du mode virtuel avec le chargement immédiat des données dans le contrôle DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [Réglage des performances dans le contrôle DataGridView Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Mode virtuel dans le contrôle DataGridView Windows Forms](virtual-mode-in-the-windows-forms-datagridview-control.md)
