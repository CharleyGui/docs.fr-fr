---
title: 'Procédure : déclencher des événements de menu pour des boutons de barre d’outils'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], click event handlers
- ToolBar control [Windows Forms], coding button click events
- toolbars [Windows Forms], click event handlers
ms.assetid: 98374f70-993d-4ca4-89fb-48fea6ce5b45
ms.openlocfilehash: 381b8ba08db6ff5bb817c9c89008dacb1085ac1b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956037"
---
# <a name="how-to-trigger-menu-events-for-toolbar-buttons"></a>Procédure : déclencher des événements de menu pour des boutons de barre d’outils
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.ToolStrip> remplace le contrôle <xref:System.Windows.Forms.ToolBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.ToolBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Si votre Windows Form comporte un <xref:System.Windows.Forms.ToolBar> contrôle avec des boutons de barre d’outils, vous devez connaître le bouton sur lequel l’utilisateur clique.  
  
 Sur l' <xref:System.Windows.Forms.ToolBar.ButtonClick> <xref:System.Windows.Forms.ToolBar> événement du contrôle, vous pouvez évaluer la <xref:System.Windows.Forms.ToolBarButtonClickEventArgs.Button%2A> propriété de la <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> classe. Dans l’exemple ci-dessous, une boîte de message s’affiche, indiquant sur quel bouton l’utilisateur a cliqué. Pour plus d'informations, consultez <xref:System.Windows.Forms.MessageBox>.  
  
 L’exemple ci-dessous suppose <xref:System.Windows.Forms.ToolBar> qu’un contrôle a été ajouté à un Windows Form.  
  
### <a name="to-handle-the-click-event-on-a-toolbar"></a>Pour gérer l’événement de clic sur une barre d’outils  
  
1. Dans une procédure, ajoutez des boutons de barre <xref:System.Windows.Forms.ToolBar> d’outils au contrôle.  
  
    ```vb  
    Public Sub ToolBarConfig()  
    ' Instantiate the toolbar buttons, set their Text properties  
    ' and add them to the ToolBar control.  
       ToolBar1.Buttons.Add(New ToolBarButton("One"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Two"))  
       ToolBar1.Buttons.Add(New ToolBarButton("Three"))  
    ' Add the event handler delegate.  
       AddHandler ToolBar1.ButtonClick, AddressOf Me.ToolBar1_ButtonClick  
    End Sub  
    ```  
  
    ```csharp  
    public void ToolBarConfig()   
    {  
       toolBar1.Buttons.Add(new ToolBarButton("One"));  
       toolBar1.Buttons.Add(new ToolBarButton("Two"));  
       toolBar1.Buttons.Add(new ToolBarButton("Three"));  
  
       toolBar1.ButtonClick +=   
          new ToolBarButtonClickEventHandler(this.toolBar1_ButtonClick);  
    }  
    ```  
  
    ```cpp  
    public:  
       void ToolBarConfig()  
       {  
          toolBar1->Buttons->Add(gcnew ToolBarButton("One"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Two"));  
          toolBar1->Buttons->Add(gcnew ToolBarButton("Three"));  
  
          toolBar1->ButtonClick +=   
             gcnew ToolBarButtonClickEventHandler(this,  
             &Form1::toolBar1_ButtonClick);  
       }  
    ```  
  
2. Ajoutez un gestionnaire d’événements pour <xref:System.Windows.Forms.ToolBar> l’événement <xref:System.Windows.Forms.ToolBar.ButtonClick> du contrôle. Utilisez une instruction de basculement de <xref:System.Windows.Forms.ToolBarButtonClickEventArgs> cas et la classe pour déterminer le bouton de barre d’outils sur lequel l’utilisateur a cliqué. Sur cette base, affichez une boîte de message appropriée.  
  
    > [!NOTE]
    > Dans cet exemple, une boîte de message est utilisée seulement en tant qu’espace réservé. Vous pouvez ajouter tout autre code à exécuter quand l’utilisateur clique sur les boutons de la barre d’outils.  
  
    ```vb  
    Protected Sub ToolBar1_ButtonClick(ByVal sender As Object, _  
    ByVal e As ToolBarButtonClickEventArgs)  
    ' Evaluate the Button property of the ToolBarButtonClickEventArgs  
    ' to determine which button was clicked.  
       Select Case ToolBar1.Buttons.IndexOf(e.Button)  
         Case 0  
           MessageBox.Show("First toolbar button clicked")  
         Case 1  
           MessageBox.Show("Second toolbar button clicked")  
         Case 2  
           MessageBox.Show("Third toolbar button clicked")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    protected void toolBar1_ButtonClick(object sender,  
    ToolBarButtonClickEventArgs e)  
    {  
       // Evaluate the Button property of the ToolBarButtonClickEventArgs  
       // to determine which button was clicked.  
       switch (toolBar1.Buttons.IndexOf(e.Button))  
       {  
          case 0 :  
             MessageBox.Show("First toolbar button clicked");  
             break;  
          case 1 :  
             MessageBox.Show("Second toolbar button clicked");  
             break;  
          case 2 :  
             MessageBox.Show("Third toolbar button clicked");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    protected:  
       void toolBar1_ButtonClick(System::Object ^ sender,  
          ToolBarButtonClickEventArgs ^ e)  
       {  
         // Evaluate the Button property of the ToolBarButtonClickEventArgs  
         // to determine which button was clicked.  
          switch (toolBar1->Buttons->IndexOf(e->Button))  
          {  
             case 0 :  
                MessageBox::Show("First toolbar button clicked");  
                break;  
             case 1 :  
                MessageBox::Show("Second toolbar button clicked");  
                break;  
             case 2 :  
                MessageBox::Show("Third toolbar button clicked");  
                break;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ToolBar>
- [Guide pratique : Ajouter des boutons à un contrôle ToolBar](how-to-add-buttons-to-a-toolbar-control.md)
- [Guide pratique pour Définir une icône pour un bouton de barre d’outils](how-to-define-an-icon-for-a-toolbar-button.md)
- [ToolBar, contrôle](toolbar-control-windows-forms.md)
