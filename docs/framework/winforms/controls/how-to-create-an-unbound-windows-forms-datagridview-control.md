---
title: 'Procédure : créer un contrôle DataGridView Windows Forms non lié'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: 193e5228df8587dfc384d8ed97ee5e4e6c005215
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611993"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a>Procédure : créer un contrôle DataGridView Windows Forms non lié
L'exemple de code suivant montre comment remplir un contrôle <xref:System.Windows.Forms.DataGridView> par programmation sans le lier à une source de données. Cela est utile quand vous souhaitez afficher une petite quantité de données sous forme de tableau.  
  
 Pour obtenir une explication complète de cet exemple de code, consultez [procédure pas à pas : Création d’un indépendant Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.  

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Procédure pas à pas : Création d’un indépendant Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
