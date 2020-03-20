---
title: 'Procédure pas à pas : utilisation du contrôle MaskedTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- input [Windows Forms], controlling to ensure validity
- MaskedTextBox control [Windows Forms], walkthroughs
- MaskedTextBox control [Windows Forms], validation
- user input [Windows Forms], controlling
- text [Windows Forms], controls for input
ms.assetid: df60565e-5447-4110-92a6-be1f6ff5faa3
ms.openlocfilehash: db32b3ec88a07747ea3e286af9f04edce3f1ba3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182055"
---
# <a name="walkthrough-working-with-the-maskedtextbox-control"></a>Procédure pas à pas : utilisation du contrôle MaskedTextBox
Cette procédure pas à pas décrit notamment les tâches suivantes :  
  
- Initialiser <xref:System.Windows.Forms.MaskedTextBox> le contrôle  
  
- Utilisation <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> du gestionnaire d’événements pour alerter l’utilisateur lorsqu’un personnage ne se conforme pas au masque  
  
- L’affectation d’un type à la <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> propriété et l’utilisation du <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> gestionnaire d’événements pour alerter l’utilisateur lorsque la valeur qu’il tente de valider n’est pas valide pour le type  
  
## <a name="creating-the-project-and-adding-a-control"></a>Créer le projet et ajouter un contrôle  
  
#### <a name="to-add-a-maskedtextbox-control-to-your-form"></a>Pour ajouter un contrôle MaskedTextBox à votre formulaire  
  
1. Ouvrez le formulaire sur lequel <xref:System.Windows.Forms.MaskedTextBox> vous voulez placer le contrôle.  
  
2. Faites <xref:System.Windows.Forms.MaskedTextBox> glisser un contrôle de la boîte à **outils** à votre formulaire.  
  
3. Cliquez à droite sur le contrôle et choisissez **propriétés**. Dans la fenêtre **Propriétés,** sélectionnez la propriété **Masque** et cliquez sur le bouton **...** (ellipsis) à côté du nom de la propriété.  
  
4. Dans la boîte de dialogue **de masque d’entrée,** sélectionnez le masque **Short Date** et cliquez **sur OK**.  
  
5. Dans la fenêtre <xref:System.Windows.Forms.MaskedTextBox.BeepOnError%2A> **Propriétés** définir la propriété à `true`. Cette propriété provoque un bip court de sonner chaque fois que l’utilisateur tente d’entrer un personnage qui viole la définition du masque.  
  
 Pour un résumé des caractères que la propriété Masque <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> prend en charge, voir la section Remarques de la propriété.  
  
## <a name="alert-the-user-to-input-errors"></a>Alerter l’utilisateur des erreurs d’entrée  
  
#### <a name="add-a-balloon-tip-for-rejected-mask-input"></a>Ajouter une pointe de ballon pour l’entrée de masque rejeté  
  
1. Retournez à la boîte <xref:System.Windows.Forms.ToolTip> à **outils** et ajoutez un à votre formulaire.  
  
2. Créez un gestionnaire <xref:System.Windows.Forms.MaskedTextBox.MaskInputRejected> d’événements <xref:System.Windows.Forms.ToolTip> pour l’événement qui soulève le moment où une erreur d’entrée se produit. La pointe du ballon reste visible pendant cinq secondes, ou jusqu’à ce que l’utilisateur la clique.  
  
    ```csharp  
    public void Form1_Load(Object sender, EventArgs e)
    {  
        ... // Other initialization code  
        maskedTextBox1.Mask = "00/00/0000";  
        maskedTextBox1.MaskInputRejected += new MaskInputRejectedEventHandler(maskedTextBox1_MaskInputRejected)  
    }  
  
    void maskedTextBox1_MaskInputRejected(object sender, MaskInputRejectedEventArgs e)  
    {  
        toolTip1.ToolTipTitle = "Invalid Input";  
        toolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", maskedTextBox1, maskedTextBox1.Location, 5000);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles MyBase.Load  
        Me.ToolTip1.IsBalloon = True  
        Me.MaskedTextBox1.Mask = "00/00/0000"  
    End Sub  
  
    Private Sub MaskedTextBox1_MaskInputRejected(sender as Object, e as MaskInputRejectedEventArgs) Handles MaskedTextBox1.MaskInputRejected  
        ToolTip1.ToolTipTitle = "Invalid Input"  
        ToolTip1.Show("We're sorry, but only digits (0-9) are allowed in dates.", MaskedTextBox1, 5000)  
    End Sub  
    ```  
  
## <a name="alert-the-user-to-a-type-that-is-not-valid"></a>Alerter l’utilisateur d’un type qui n’est pas valide  
  
#### <a name="add-a-balloon-tip-for-invalid-data-types"></a>Ajouter une pointe de ballon pour les types de données non valides  
  
1. Dans le gestionnaire <xref:System.Windows.Forms.Form.Load> d’événements <xref:System.Type> de votre <xref:System.DateTime> formulaire, <xref:System.Windows.Forms.MaskedTextBox> assignez <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> un objet représentant le type à la propriété du contrôle :  
  
    ```csharp  
    private void Form1_Load(Object sender, EventArgs e)  
    {  
        // Other code  
        maskedTextBox1.ValidatingType = typeof(System.DateTime);  
        maskedTextBox1.TypeValidationCompleted += new TypeValidationEventHandler(maskedTextBox1_TypeValidationCompleted);  
    }  
    ```  
  
    ```vb  
    Private Sub Form1_Load(sender as Object, e as EventArgs)  
        // Other code  
        MaskedTextBox1.ValidatingType = GetType(System.DateTime)  
    End Sub  
    ```  
  
2. Ajoutez un gestionnaire d'événements pour l'événement <xref:System.Windows.Forms.MaskedTextBox.TypeValidationCompleted> :  
  
    ```csharp  
    public void maskedTextBox1_TypeValidationCompleted(object sender, TypeValidationEventArgs e)  
    {  
        if (!e.IsValidInput)  
        {  
           toolTip1.ToolTipTitle = "Invalid Date Value";  
           toolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000);  
           e.Cancel = true;  
        }  
    }  
    ```  
  
    ```vb  
    Public Sub MaskedTextBox1_TypeValidationCompleted(sender as Object, e as TypeValidationEventArgs)  
        If Not e.IsValidInput Then  
           ToolTip1.ToolTipTitle = "Invalid Date Value"  
           ToolTip1.Show("We're sorry, but the value you entered is not a valid date. Please change the value.", maskedTextBox1, 5000)  
           e.Cancel = True  
        End If  
    End Sub  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.MaskedTextBox>
- [MaskedTextBox, contrôle](maskedtextbox-control-windows-forms.md)
