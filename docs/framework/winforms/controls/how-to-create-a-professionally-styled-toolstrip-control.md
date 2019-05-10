---
title: 'Procédure : créer un contrôle ToolStrip de style professionnel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c208b2f6-8105-474b-9075-d582e1792870
ms.openlocfilehash: 6ba5d948b99889e26f620363b7fefbe2e63ffd2d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615993"
---
# <a name="how-to-create-a-professionally-styled-toolstrip-control"></a>Procédure : créer un contrôle ToolStrip de style professionnel
Vous pouvez donner aux contrôles <xref:System.Windows.Forms.ToolStrip> de votre application une apparence et un comportement professionnels en écrivant votre propre classe dérivée du type <xref:System.Windows.Forms.ToolStripProfessionalRenderer>.  
  
 Il existe une prise en charge étendue pour cette fonctionnalité dans Visual Studio.  
  
 Consultez [Procédure pas à pas : Création d’un contrôle ToolStrip de style professionnel](walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant montre comment utiliser <xref:System.Windows.Forms.ToolStrip> contrôles pour créer un contrôle composite qui reproduit le **volet de Navigation** fourni par Microsoft® Outlook®.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StackView#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Références aux assemblys System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.  Consultez également [procédure pas à pas : Création d’un contrôle ToolStrip de style professionnel](walkthrough-creating-a-professionally-styled-toolstrip-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.StatusStrip>
- [Contrôle ToolStrip](toolstrip-control-windows-forms.md)
- [Guide pratique pour Fournir des éléments de Menu Standard à un formulaire](how-to-provide-standard-menu-items-to-a-form.md)
