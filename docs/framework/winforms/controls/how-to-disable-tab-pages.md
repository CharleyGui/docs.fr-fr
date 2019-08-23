---
title: 'Procédure : désactiver des onglets'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 888228c28dce591b237be16b6a321afee0105208
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967151"
---
# <a name="how-to-disable-tab-pages"></a>Procédure : désactiver des onglets
Dans certains cas, vous voudrez restreindre l’accès aux données disponibles dans votre application Windows Forms. C’est le cas, par exemple, lorsque des données sont affichées dans les pages d’onglets d’un contrôle onglet; les administrateurs peuvent avoir des informations sur une page d’onglets que vous souhaiteriez empêcher des utilisateurs invités ou de niveau inférieur.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Pour désactiver les pages d’onglets par programmation  
  
1. Écrivez du code pour gérer l’événement du <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> contrôle onglet. Il s’agit de l’événement qui est déclenché lorsque l’utilisateur passe d’un onglet à l’autre.  
  
2. Vérifiez les informations d’identification. Selon les informations présentées, vous pouvez vérifier le nom d’utilisateur avec lequel l’utilisateur s’est connecté ou une autre forme d’informations d’identification avant de permettre à l’utilisateur d’afficher l’onglet.  
  
3. Si l’utilisateur possède les informations d’identification appropriées, affichez l’onglet sur lequel l’utilisateur a cliqué. Si l’utilisateur ne dispose pas des informations d’identification appropriées, affichez une boîte de message ou une autre interface utilisateur indiquant qu’il n’y a pas d’accès, puis revenez à l’onglet initial.  
  
    > [!NOTE]
    > Lorsque vous implémentez cette fonctionnalité dans vos applications de production, vous pouvez effectuer cette vérification des informations d' <xref:System.Windows.Forms.Form.Load> identification pendant l’événement du formulaire. Cela vous permettra de masquer l’onglet avant l’affichage d’une interface utilisateur, ce qui constitue une approche bien plus propre à la programmation. La méthodologie utilisée ci-dessous (vérification des informations d’identification et désactivation <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> de l’onglet pendant l’événement) est à titre indicatif.  
  
4. Si vous avez plus de deux pages d’onglets, affichez éventuellement une page d’onglets différente de celle d’origine.  
  
     Dans l’exemple ci-dessous <xref:System.Windows.Forms.CheckBox> , un contrôle est utilisé à la place de la vérification des informations d’identification, car les critères d’accès à l’onglet varient en fonction de l’application. Lorsque l' <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> événement est déclenché, si la vérification des informations d’identification a la valeur true (autrement dit, si la case à cocher `TabPage2` est activée) et si l’onglet sélectionné est (l’onglet avec les `TabPage2` informations confidentielles, dans cet exemple), est affiché. Sinon, `TabPage3` est affiché et une boîte de message s’affiche pour l’utilisateur, indiquant qu’il ne dispose pas des privilèges d’accès appropriés. Le code ci-dessous suppose un formulaire avec <xref:System.Windows.Forms.CheckBox> un contrôle`CredentialCheck`() et <xref:System.Windows.Forms.TabControl> un contrôle avec trois pages d’onglets.  
  
    ```vb  
    Private Sub TabControl1_SelectedIndexChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles TabControl1.SelectedIndexChanged  
       ' Check Credentials Here  
  
       If CredentialCheck.Checked = True And _   
       TabControl1.SelectedTab Is TabPage2 Then  
          TabControl1.SelectedTab = TabPage2  
       ElseIf CredentialCheck.Checked = False _   
       And TabControl1.SelectedTab Is TabPage2 Then  
          MessageBox.Show _   
         ("Unable to load tab. You have insufficient access privileges.")  
          TabControl1.SelectedTab = TabPage3  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void tabControl1_SelectedIndexChanged(object sender, System.EventArgs e)  
    {  
        // Check Credentials Here  
  
        if ((CredentialCheck.Checked == true) && (tabControl1.SelectedTab == tabPage2))   
        {  
            tabControl1.SelectedTab = tabPage2;  
        }  
        else if ((CredentialCheck.Checked == false) && (tabControl1.SelectedTab == tabPage2))  
        {  
            MessageBox.Show("Unable to load tab. You have insufficient access privileges.");  
            tabControl1.SelectedTab = tabPage3;  
        }  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void tabControl1_SelectedIndexChanged(  
          System::Object ^ sender,  
          System::EventArgs ^  e)  
       {  
          // Check Credentials Here  
          if ((CredentialCheck->Checked == true) &&  
              (tabControl1->SelectedTab == tabPage2))  
          {  
             tabControl1->SelectedTab = tabPage2;  
          }  
          else if ((CredentialCheck->Checked == false) &&  
                   (tabControl1->SelectedTab == tabPage2))  
          {  
             MessageBox::Show(String::Concat("Unable to load tab. ",  
                "You have insufficient access privileges."));  
             tabControl1->SelectedTab = tabPage3;  
          }  
       }  
    ```  
  
     (Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle TabControl](tabcontrol-control-overview-windows-forms.md)
- [Guide pratique pour Ajouter un contrôle à une page d’onglets](how-to-add-a-control-to-a-tab-page.md)
- [Guide pratique pour Ajouter et supprimer des onglets avec le TabControl Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Guide pratique pour Modifier l’apparence du Windows Forms TabControl](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
