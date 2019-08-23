---
title: 'Procédure : ajouter des contrôles ou en supprimer dans une collection de contrôles au moment de l’exécution'
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
ms.openlocfilehash: 87ad4c957ac5b99438684d398a0c5ad7d126c406
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925042"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Procédure : ajouter des contrôles ou en supprimer dans une collection de contrôles au moment de l’exécution
Les tâches courantes dans le développement d’applications sont l’ajout et la suppression de contrôles dans n’importe quel contrôle conteneur de <xref:System.Windows.Forms.Panel> vos <xref:System.Windows.Forms.GroupBox> formulaires (tels que le contrôle ou, ou même le formulaire lui-même). Au moment de la conception, vous pouvez faire glisser les contrôles directement vers un panneau ou une zone de groupe. Au moment de l’exécution, ces contrôles gèrent une collection `Controls`, qui assure le suivi des contrôles qui y sont placés.  
  
> [!NOTE]
> L’exemple de code suivant s’applique à n’importe quel contrôle qui gère une collection de contrôles qu’il contient.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Pour ajouter un contrôle à une collection par programme  
  
1. Créez une instance du contrôle à ajouter.  
  
2. Définissez les propriétés du nouveau contrôle.  
  
3. Ajoutez le contrôle à la collection `Controls` du contrôle parent.  
  
     L’exemple de code suivant montre comment créer une instance du <xref:System.Windows.Forms.Button> contrôle. Elle requiert un formulaire avec un <xref:System.Windows.Forms.Panel> contrôle et que la méthode de gestion des événements pour le bouton en cours `NewPanelButton_Click`de création,, existe déjà.  
  
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
  
1. Supprimez le gestionnaire d’événements de l’événement. Dans Visual Basic, utilisez le mot clé [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md) . dans C#, utilisez l' [opérateur-=](../../../csharp/language-reference/operators/subtraction-operator.md).  
  
2. Utilisez la méthode `Remove` pour supprimer le contrôle souhaité dans la collection `Controls` du panneau.  
  
3. Appelez la <xref:System.Windows.Forms.Control.Dispose%2A> méthode pour libérer toutes les ressources utilisées par le contrôle.  
  
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
