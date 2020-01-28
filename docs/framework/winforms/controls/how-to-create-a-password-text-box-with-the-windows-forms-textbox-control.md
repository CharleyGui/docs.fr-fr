---
title: Créer une zone de texte de mot de passe avec le contrôle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], entering passwords
- password boxes [Windows Forms], creating
- PasswordChar property in text boxes
- passwords [Windows Forms], input mask
- passwords [Windows Forms], password text box
ms.assetid: d105d6b9-3d50-44cd-80d8-2c0e2f486727
ms.openlocfilehash: ff4706a736d15f14cf437c808219e9088773dc6d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731283"
---
# <a name="how-to-create-a-password-text-box-with-the-windows-forms-textbox-control"></a>Comment : créer une zone de texte pour mot de passe avec le contrôle TextBox Windows Forms

Une zone de mot de passe est une zone de texte Windows Forms qui affiche des espaces réservés lorsqu’un utilisateur tape une chaîne.

### <a name="to-create-a-password-text-box"></a>Pour créer une zone de texte de mot de passe

1. Affectez à la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> du contrôle <xref:System.Windows.Forms.TextBox> la valeur d’un caractère spécifique.

    La propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> spécifie le caractère affiché dans la zone de texte. Par exemple, si vous souhaitez que les astérisques s’affichent dans la zone mot de passe, spécifiez * pour la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> dans le Fenêtre Propriétés. Ensuite, quel que soit le caractère qu’un utilisateur tape dans la zone de texte, un astérisque s’affiche.

2. Facultatif Définissez la propriété <xref:System.Windows.Forms.TextBoxBase.MaxLength%2A>. La propriété détermine le nombre de caractères pouvant être tapés dans la zone de texte. Si la longueur maximale est dépassée, le système émet un signal sonore et la zone de texte n’accepte plus de caractères. Notez que vous n’avez peut-être pas besoin d’effectuer cette opération, car la longueur maximale d’un mot de passe peut être utilisée par les pirates qui essaient de deviner le mot de passe.

    L’exemple de code suivant montre comment initialiser une zone de texte qui accepte une chaîne d’une longueur maximale de 14 caractères et afficher des astérisques à la place de la chaîne. La procédure `InitializeMyControl` ne s’exécute pas automatiquement ; elle doit être appelée.

    > [!IMPORTANT]
    > L’utilisation de la propriété <xref:System.Windows.Forms.TextBox.PasswordChar%2A> sur une zone de texte permet de s’assurer que les autres utilisateurs ne seront pas en mesure de déterminer le mot de passe d’un utilisateur s’ils observent la saisie de l’utilisateur. Cette mesure de sécurité ne couvre pas le type de stockage ou la transmission du mot de passe qui peut se produire en raison de la logique de votre application. Étant donné que le texte entré n’est pas chiffré, vous devez le traiter comme n’importe quelle autre donnée confidentielle. Même s’il n’apparaît pas comme tel, le mot de passe est toujours traité comme une chaîne de texte brut (sauf si vous avez implémenté une mesure de sécurité supplémentaire).

    ```vb
    Private Sub InitializeMyControl()
       ' Set to no text.
       TextBox1.Text = ""
       ' The password character is an asterisk.
       TextBox1.PasswordChar = "*"
       ' The control will allow no more than 14 characters.
       TextBox1.MaxLength = 14
    End Sub
    ```

    ```csharp
    private void InitializeMyControl()
    {
       // Set to no text.
       textBox1.Text = "";
       // The password character is an asterisk.
       textBox1.PasswordChar = '*';
       // The control will allow no more than 14 characters.
       textBox1.MaxLength = 14;
    }
    ```

    ```cpp
    private:
       void InitializeMyControl()
       {
          // Set to no text.
          textBox1->Text = "";
          // The password character is an asterisk.
          textBox1->PasswordChar = '*';
          // The control will allow no more than 14 characters.
          textBox1->MaxLength = 14;
       }
    ```

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.TextBox>
- [Vue d’ensemble du contrôle TextBox](textbox-control-overview-windows-forms.md)
- [Guide pratique pour contrôler le point d’insertion dans un contrôle TextBox Windows Forms](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [Guide pratique pour créer une zone de texte en lecture seule](how-to-create-a-read-only-text-box-windows-forms.md)
- [Guide pratique pour insérer des guillemets dans une chaîne](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [Guide pratique pour sélectionner du texte dans le contrôle TextBox Windows Forms](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [Guide pratique pour afficher des lignes multiples dans le contrôle TextBox Windows Forms](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [TextBox, contrôle](textbox-control-windows-forms.md)
