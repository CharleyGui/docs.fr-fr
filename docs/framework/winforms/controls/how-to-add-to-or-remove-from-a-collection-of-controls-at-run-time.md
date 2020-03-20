---
title: 'Comment : ajouter des contrôles dans une collection au moment de l’exécution, ou comment les supprimer'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- run time [Windows Forms], removing controls
- controls [Windows Forms], adding using collections
- controls collections
- collections [Windows Forms], adding items
- run time [Windows Forms], adding controls
- controls [Windows Forms], removing using collections
ms.assetid: 771bf895-3d5f-469b-a324-3528f343657e
ms.openlocfilehash: 369946581847b4bdcf8bc658aeb94b14c529061c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182289"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Comment : ajouter des contrôles dans une collection au moment de l’exécution, ou comment les supprimer
Les tâches courantes dans le développement d’applications sont l’ajout de <xref:System.Windows.Forms.Panel> contrôles <xref:System.Windows.Forms.GroupBox> et la suppression des contrôles de tout contrôle de conteneur sur vos formulaires (tels que le ou le contrôle, ou même le formulaire lui-même). Au moment de la conception, vous pouvez faire glisser les contrôles directement vers un panneau ou une zone de groupe. Au moment de l’exécution, ces contrôles gèrent une collection `Controls`, qui assure le suivi des contrôles qui y sont placés.  
  
> [!NOTE]
> L’exemple de code suivant s’applique à n’importe quel contrôle qui gère une collection de contrôles qu’il contient.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Pour ajouter un contrôle à une collection par programme  
  
1. Créez une instance du contrôle à ajouter.  
  
2. Définissez les propriétés du nouveau contrôle.  
  
3. Ajoutez le contrôle à la collection `Controls` du contrôle parent.  
  
     L’exemple de code suivant montre <xref:System.Windows.Forms.Button> comment créer une instance du contrôle. Il nécessite un <xref:System.Windows.Forms.Panel> formulaire avec un contrôle et que la `NewPanelButton_Click`méthode de manipulation d’événements pour le bouton en cours de création, , existe déjà.  
  
    ```vb  
    Public NewPanelButton As New Button()  
  
    Public Sub AddNewControl()  
       ' The Add method will accept as a parameter any object that derives  
       ' from the Control class. In this case, it is a Button control.  
       Panel1.Controls.Add(NewPanelButton)  
       ' The event handler indicated for the Click event in the code
       ' below is used as an example. Substite the appropriate event  
       ' handler for your application.  
       AddHandler NewPanelButton.Click, AddressOf NewPanelButton_Click  
    End Sub  
    ```  
  
    ```csharp  
    public Button newPanelButton = new Button();  
  
    public void addNewControl()  
    {
       // The Add method will accept as a parameter any object that derives  
       // from the Control class. In this case, it is a Button control.  
       panel1.Controls.Add(newPanelButton);  
       // The event handler indicated for the Click event in the code
       // below is used as an example. Substitute the appropriate event  
       // handler for your application.  
       this.newPanelButton.Click += new System.EventHandler(this. NewPanelButton_Click);  
    }  
    ```  
  
### <a name="to-remove-controls-from-a-collection-programmatically"></a>Pour supprimer des contrôles d’une collection par programme  
  
1. Supprimez le gestionnaire d’événements de l’événement. Dans Visual Basic, utilisez le mot-clé [De l’énoncé RemoveHandler;](../../../visual-basic/language-reference/statements/removehandler-statement.md) dans C, utilisez [l’opérateur .](../../../csharp/language-reference/operators/subtraction-operator.md)  
  
2. Utilisez la méthode `Remove` pour supprimer le contrôle souhaité dans la collection `Controls` du panneau.  
  
3. Appelez <xref:System.Windows.Forms.Control.Dispose%2A> la méthode pour libérer toutes les ressources utilisées par le contrôle.  
  
    ```vb  
    Public Sub RemoveControl()  
    ' NOTE: The code below uses the instance of
    ' the button (NewPanelButton) from the previous example.  
       If Panel1.Controls.Contains(NewPanelButton) Then  
          RemoveHandler NewPanelButton.Click, AddressOf _
             NewPanelButton_Click  
          Panel1.Controls.Remove(NewPanelButton)  
          NewPanelButton.Dispose()  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void removeControl(object sender, System.EventArgs e)  
    {  
    // NOTE: The code below uses the instance of
    // the button (newPanelButton) from the previous example.  
       if(panel1.Controls.Contains(newPanelButton))  
       {  
          this.newPanelButton.Click -= new System.EventHandler(this.
             NewPanelButton_Click);  
          panel1.Controls.Remove(newPanelButton);  
          newPanelButton.Dispose();  
       }  
    }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Panel>
- [Panel, contrôle](panel-control-windows-forms.md)
