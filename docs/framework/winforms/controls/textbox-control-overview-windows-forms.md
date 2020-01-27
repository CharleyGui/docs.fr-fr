---
title: Vue d'ensemble du contrôle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TextBox
helpviewer_keywords:
- TextBox control [Windows Forms], about TextBox controls
- text boxes [Windows Forms], adding
ms.assetid: d1a9c7f5-fa53-480a-a75c-158f8649ea2f
ms.openlocfilehash: 06ab460d720d17331881b5ba653263160eaf3cb3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742809"
---
# <a name="textbox-control-overview-windows-forms"></a>Vue d'ensemble du contrôle TextBox (Windows Forms)
Les zones de texte Windows Forms sont utilisées pour obtenir l’entrée de l’utilisateur ou pour afficher du texte. Le contrôle <xref:System.Windows.Forms.TextBox> est généralement utilisé pour le texte modifiable, bien qu’il puisse également être mis en lecture seule. Les zones de texte peuvent afficher plusieurs lignes, ajuster le texte à la taille du contrôle et ajouter une mise en forme de base. Le contrôle <xref:System.Windows.Forms.TextBox> fournit un style de mise en forme unique pour le texte affiché ou entré dans le contrôle. Pour afficher plusieurs types de texte mis en forme, utilisez le contrôle <xref:System.Windows.Forms.RichTextBox>. Pour plus d’informations, consultez [vue d’ensemble du contrôle RichTextBox](richtextbox-control-overview-windows-forms.md).  
  
## <a name="working-with-the-textbox-control"></a>Utilisation du contrôle TextBox  
 Le texte affiché par le contrôle est contenu dans la propriété <xref:System.Windows.Forms.TextBox.Text%2A>. Par défaut, vous pouvez entrer jusqu’à 2048 caractères dans une zone de texte. Si vous affectez à la propriété <xref:System.Windows.Forms.TextBox.Multiline%2A> la valeur `true`, vous pouvez entrer jusqu’à 32 Ko de texte. La propriété <xref:System.Windows.Forms.TextBox.Text%2A> peut être définie au moment du design à l’aide de la fenêtre Propriétés, au moment de l’exécution dans le code ou par l’entrée d’utilisateur au moment de l’exécution. Le contenu actuel d’une zone de texte peut être récupéré au moment de l’exécution en lisant la propriété <xref:System.Windows.Forms.TextBox.Text%2A>.  
  
 L’exemple de code suivant définit le texte dans le contrôle au moment de l’exécution. La procédure `InitializeMyControl` ne s’exécute pas automatiquement ; elle doit être appelée.  
  
```vb  
Private Sub InitializeMyControl()  
   ' Put some text into the control first.  
   TextBox1.Text = "This is a TextBox control."  
End Sub  
```  
  
```csharp  
private void InitializeMyControl() {  
   // Put some text into the control first.  
   textBox1.Text = "This is a TextBox control.";  
}  
```  
  
```cpp  
private:  
   void InitializeMyControl()  
   {  
      // Put some text into the control first.  
      textBox1->Text = "This is a TextBox control.";  
   }  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte en lecture seule](how-to-create-a-read-only-text-box-windows-forms.md)
- [Guide pratique pour insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
