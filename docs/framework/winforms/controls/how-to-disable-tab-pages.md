---
title: "Comment : désactiver les pages d'onglets"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tab pages [Windows Forms], hiding in forms
- TabControl control [Windows Forms], disabling pages
ms.assetid: adcc6618-8a34-4ee1-bbe3-47e732de6a59
ms.openlocfilehash: 9074aedb81a485267dc4faff92e0fe8d0d3b467f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182169"
---
# <a name="how-to-disable-tab-pages"></a>Comment : désactiver les pages d'onglets
À certaines occasions, vous voudrez restreindre l’accès aux données disponibles dans votre application Windows Forms. Un exemple de ceci peut être quand vous avez des données affichées dans les pages d’onglet d’un contrôle d’onglet ; les administrateurs pourraient avoir des informations sur une page d’onglet que vous voudriez restreindre des utilisateurs d’invités ou de niveau inférieur.  
  
### <a name="to-disable-tab-pages-programmatically"></a>Désactiver les pages d’onglets programmatiquement  
  
1. Écrivez du code pour <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> gérer l’événement du contrôle de l’onglet. C’est l’événement qui est soulevé lorsque l’utilisateur passe d’un onglet à l’autre.  
  
2. Vérifiez les informations d’identification. Selon les informations présentées, vous pouvez vérifier le nom d’utilisateur que l’utilisateur a connecté avec ou une autre forme d’informations d’identification avant de permettre à l’utilisateur de voir l’onglet.  
  
3. Si l’utilisateur dispose d’informations d’identification appropriées, affichez l’onglet qui a été cliqué. Si l’utilisateur n’a pas les informations d’identification appropriées, affichez une boîte de message ou une autre interface utilisateur indiquant qu’il n’y a pas d’accès et retournez à l’onglet initial.  
  
    > [!NOTE]
    > Lorsque vous implémentez cette fonctionnalité dans vos applications de production, vous pouvez effectuer cette vérification d’informations lors de l’événement du <xref:System.Windows.Forms.Form.Load> formulaire. Cela vous permettra de masquer l’onglet avant toute interface utilisateur est affiché, qui est une approche beaucoup plus propre de la programmation. La méthodologie utilisée ci-dessous (vérification des informations <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> d’identification et désactivation de l’onglet pendant l’événement) est à des fins d’illustration.  
  
4. Optionnellement, si vous avez plus de deux pages d’onglets, affichez une page d’onglet différente de l’original.  
  
     Dans l’exemple <xref:System.Windows.Forms.CheckBox> ci-dessous, un contrôle est utilisé au lieu de vérifier les informations d’identification, car les critères d’accès à l’onglet varient selon l’application. Lorsque <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> l’événement est soulevé, si la vérification des informations d’identification est `TabPage2` vraie (c’est-à-dire que `TabPage2` la case à cocher est cochée) et que l’onglet sélectionné est (l’onglet avec les informations confidentielles, dans cet exemple), est alors affiché. Dans `TabPage3` le cas contraire, est affiché et une boîte de message est montrée à l’utilisateur, indiquant qu’ils n’avaient pas les privilèges d’accès appropriés. Le code ci-dessous suppose <xref:System.Windows.Forms.CheckBox> un`CredentialCheck`formulaire <xref:System.Windows.Forms.TabControl> avec un contrôle ( ) et un contrôle avec trois pages d’onglet.  
  
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
  
     (Visual C, Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a>Voir aussi

- [Vue d'ensemble du contrôle TabControl](tabcontrol-control-overview-windows-forms.md)
- [Comment : ajouter un contrôle à une page d'onglet](how-to-add-a-control-to-a-tab-page.md)
- [Guide pratique pour ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [Comment : modifier l'apparence du contrôle TabControl Windows Forms](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
