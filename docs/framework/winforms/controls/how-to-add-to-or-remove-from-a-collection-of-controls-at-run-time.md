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
ms.openlocfilehash: a868632d6868e6a82c4fa135444279b8ef4dc7af
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301413"
---
# <a name="how-to-add-to-or-remove-from-a-collection-of-controls-at-run-time"></a>Procédure : ajouter des contrôles ou en supprimer dans une collection de contrôles au moment de l’exécution
Tâches courantes dans le développement d’applications sont l’ajout et la suppression de contrôles à partir de n’importe quel contrôle conteneur sur vos formulaires (comme le <xref:System.Windows.Forms.Panel> ou <xref:System.Windows.Forms.GroupBox> contrôle, ou même le formulaire lui-même). Au moment de la conception, vous pouvez faire glisser les contrôles directement vers un panneau ou une zone de groupe. Au moment de l’exécution, ces contrôles gèrent une collection `Controls`, qui assure le suivi des contrôles qui y sont placés.  
  
> [!NOTE]
>  L’exemple de code suivant s’applique à n’importe quel contrôle qui gère une collection de contrôles qu’il contient.  
  
### <a name="to-add-a-control-to-a-collection-programmatically"></a>Pour ajouter un contrôle à une collection par programme  
  
1. Créez une instance du contrôle à ajouter.  
  
2. Définissez les propriétés du nouveau contrôle.  
  
3. Ajoutez le contrôle à la collection `Controls` du contrôle parent.  
  
     L’exemple de code suivant montre comment créer une instance de la <xref:System.Windows.Forms.Button> contrôle. Il nécessite un formulaire avec un <xref:System.Windows.Forms.Panel> contrôle et que la méthode de gestion d’événements pour le bouton en cours de création, `NewPanelButton_Click`, existe déjà.  
  
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
  
1. Supprimez le gestionnaire d’événements de l’événement. Dans Visual Basic, utilisez la [RemoveHandler, instruction](~/docs/visual-basic/language-reference/statements/removehandler-statement.md) mot clé ; dans C#, utilisez le [opérateur-=](~/docs/csharp/language-reference/operators/subtraction-operator.md).  
  
2. Utilisez la méthode `Remove` pour supprimer le contrôle souhaité dans la collection `Controls` du panneau.  
  
3. Appelez le <xref:System.Windows.Forms.Control.Dispose%2A> méthode pour libérer toutes les ressources utilisées par le contrôle.  
  
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
