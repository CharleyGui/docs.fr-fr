---
title: 'Comment : imprimer un fichier texte de plusieurs pages'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740662"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a>Comment : imprimer un fichier texte composé de plusieurs pages dans les Windows Forms
Il est très courant que les applications Windows impriment du texte. La classe <xref:System.Drawing.Graphics> fournit des méthodes pour dessiner des objets (graphismes ou texte) sur un périphérique, tel qu'un écran ou une imprimante.  
  
> [!NOTE]
> Le méthodes <xref:System.Windows.Forms.TextRenderer.DrawText%2A> de <xref:System.Windows.Forms.TextRenderer> ne sont pas prises en charge pour l'impression. Vous devez toujours utiliser les méthodes <xref:System.Drawing.Graphics.DrawString%2A> de <xref:System.Drawing.Graphics>, comme illustré dans l'exemple de code suivant, pour dessiner du texte pour l'impression.  
  
### <a name="to-print-text"></a>Pour imprimer du texte  
  
1. Ajoutez un composant <xref:System.Drawing.Printing.PrintDocument> et une chaîne à votre formulaire.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. Si vous imprimez un document, affectez comme valeur de la propriété <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> le document que vous souhaitez imprimer, puis ouvrez et lisez le contenu du document dans la chaîne que vous avez ajoutée précédemment.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. Dans le gestionnaire d'événements <xref:System.Drawing.Printing.PrintDocument.PrintPage>, utilisez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> de la classe <xref:System.Drawing.Printing.PrintPageEventArgs> et le contenu du document pour calculer la longueur de ligne et le nombre de lignes par page. Après chaque dessin de page, vérifiez s'il s'agit de la dernière page et définissez la propriété <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> de <xref:System.Drawing.Printing.PrintPageEventArgs> en conséquence. L'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est déclenché jusqu'à ce que <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> soit `false`. Assurez-vous aussi que l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage> est associé à sa méthode de gestion d'événements.  
  
     Dans l'exemple de code suivant, le gestionnaire d'événements est utilisé pour imprimer le contenu du fichier « testPage.txt » avec la même police que celle utilisée sur le formulaire.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. Appelez la méthode <xref:System.Drawing.Printing.PrintDocument.Print%2A> pour déclencher l'événement <xref:System.Drawing.Printing.PrintDocument.PrintPage>.  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a>Exemple  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- Un fichier texte nommé testPage.txt contenant le texte à imprimer, situé à la racine du lecteur C:\\. Modifiez le code pour imprimer un fichier différent.  
  
- Références aux assemblys System, System.Windows.Forms, System.Drawing.  
  
- Pour plus d’informations sur la création de cet exemple à partir de la C#ligne de commande pour Visual Basic ou visuel, consultez [génération à partir de la ligne de commande](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou génération à partir de la [ligne de commande avec CSC. exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également générer cet exemple dans Visual Studio en collant le code dans un nouveau projet.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Prise en charge de l’impression dans les Windows Forms](windows-forms-print-support.md)
