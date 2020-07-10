---
title: 'Comment : imprimer un Windows Form'
description: Découvrez comment imprimer par programmation une copie du Windows Form actuel à l’aide de la méthode CopyFromScreen.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174690"
---
# <a name="how-to-print-a-windows-form"></a>Comment : imprimer un Windows Form
Dans le cadre du processus de développement, vous voudrez généralement imprimer une copie de votre Windows Form. L’exemple de code suivant montre comment imprimer une copie du formulaire actuel à l’aide de la <xref:System.Drawing.Graphics.CopyFromScreen%2A> méthode.  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
- Vous n’êtes pas autorisé à accéder à l’imprimante.  
  
- Aucune imprimante n’est installée.  
  
## <a name="net-framework-security"></a>Sécurité du .NET Framework  
 Pour exécuter cet exemple de code, vous devez avoir l’autorisation d’accéder à l’imprimante que vous utilisez avec votre ordinateur.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Printing.PrintDocument>
- [Guide pratique pour rendre des images avec GDI+](how-to-render-images-with-gdi.md)
- [Comment : imprimer des graphiques dans Windows Forms](how-to-print-graphics-in-windows-forms.md)
