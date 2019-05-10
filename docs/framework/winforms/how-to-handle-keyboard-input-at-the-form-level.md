---
title: 'Procédure : gérer l’entrée de clavier au niveau du formulaire'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input [Windows Forms], at form level
- Windows Forms, handling keyboard input
- keyboards [Windows Forms], form-level input
ms.assetid: d7f8b390-dc91-42d2-ae0f-2ffa388127ad
ms.openlocfilehash: 8e346c5b69c507307d459f6246e26a6a96bb9e24
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64591294"
---
# <a name="how-to-handle-keyboard-input-at-the-form-level"></a>Procédure : gérer l’entrée de clavier au niveau du formulaire
Windows Forms offre la possibilité de gérer les messages de clavier au niveau du formulaire, avant que les messages n'atteignent un contrôle. Cette rubrique montre comment procéder.  
  
### <a name="to-handle-a-keyboard-message-at-the-form-level"></a>Pour gérer un message de clavier au niveau du formulaire  
  
- Gérez l'événement <xref:System.Windows.Forms.Control.KeyPress> ou <xref:System.Windows.Forms.Control.KeyDown> du formulaire de démarrage et affectez la valeur `true` à la propriété <xref:System.Windows.Forms.Form.KeyPreview%2A> du formulaire pour que les messages de clavier soient reçus par le formulaire avant qu'ils atteignent les contrôles sur le formulaire. L'exemple de code suivant gère l'événement <xref:System.Windows.Forms.Control.KeyPress> en détectant toutes les touches numériques et en consommant « 1 », « 4 » et « 7 ».  
  
     [!code-cpp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#10)]
     [!code-csharp[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#10)]
     [!code-vb[System.Windows.Forms.KeyboardInputForm#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#10)]  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant est l'application complète pour l'exemple ci-dessus. L'application comprend un <xref:System.Windows.Forms.TextBox> avec plusieurs autres contrôles qui vous permettent de déplacer le focus hors du <xref:System.Windows.Forms.TextBox>. L'événement <xref:System.Windows.Forms.Control.KeyPress> du <xref:System.Windows.Forms.Form> principal consomme « 1 », « 4 » et « 7 » et l'événement <xref:System.Windows.Forms.Control.KeyPress> du <xref:System.Windows.Forms.TextBox> consomme « 2 », « 5 » et « 8 » tout en affichant les touches restantes. Comparez la sortie de <xref:System.Windows.Forms.MessageBox> quand vous appuyez sur une touche numérique pendant que le <xref:System.Windows.Forms.TextBox> a le focus avec la sortie de <xref:System.Windows.Forms.MessageBox> quand vous appuyez sur une touche numérique pendant que le focus est sur l'un des autres contrôles.  
  
 [!code-cpp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.KeyBoardInputForm#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.KeyboardInputForm/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
- des références aux assemblys System, System.Drawing et System.Windows.Forms.  
  
 Pour plus d’informations sur la création de cet exemple à partir de la ligne de commande pour Visual Basic ou Visual c#, consultez [génération à partir de la ligne de commande](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [de ligne de commande avec csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Vous pouvez également créer cet exemple dans Visual Studio en collant le code dans un nouveau projet.  

## <a name="see-also"></a>Voir aussi

- [Entrée au clavier dans une application Windows Forms](keyboard-input-in-a-windows-forms-application.md)
