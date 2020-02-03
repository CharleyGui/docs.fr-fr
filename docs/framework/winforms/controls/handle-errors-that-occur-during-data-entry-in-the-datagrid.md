---
title: Gérer les erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: 03a13957c80b0ab62afb11efc57cf31e059e5942
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745612"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Comment : gérer les erreurs qui se produisent lors de l'entrée de données dans le contrôle DataGridView Windows Forms
L'exemple de code suivant montre comment utiliser le contrôle <xref:System.Windows.Forms.DataGridView> pour signaler des erreurs de saisie de données à l'utilisateur.  
  
 Pour obtenir une explication complète de cet exemple de code, consultez [procédure pas à pas : gestion des erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System, System.Data, System.Windows.Forms et System.XML.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Saisie de données dans le contrôle DataGridView Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
