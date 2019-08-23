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
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="91fd5-102">Procédure : désactiver des onglets</span><span class="sxs-lookup"><span data-stu-id="91fd5-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="91fd5-103">Dans certains cas, vous voudrez restreindre l’accès aux données disponibles dans votre application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="91fd5-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="91fd5-104">C’est le cas, par exemple, lorsque des données sont affichées dans les pages d’onglets d’un contrôle onglet; les administrateurs peuvent avoir des informations sur une page d’onglets que vous souhaiteriez empêcher des utilisateurs invités ou de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="91fd5-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="91fd5-105">Pour désactiver les pages d’onglets par programmation</span><span class="sxs-lookup"><span data-stu-id="91fd5-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="91fd5-106">Écrivez du code pour gérer l’événement du <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> contrôle onglet.</span><span class="sxs-lookup"><span data-stu-id="91fd5-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="91fd5-107">Il s’agit de l’événement qui est déclenché lorsque l’utilisateur passe d’un onglet à l’autre.</span><span class="sxs-lookup"><span data-stu-id="91fd5-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="91fd5-108">Vérifiez les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="91fd5-108">Check credentials.</span></span> <span data-ttu-id="91fd5-109">Selon les informations présentées, vous pouvez vérifier le nom d’utilisateur avec lequel l’utilisateur s’est connecté ou une autre forme d’informations d’identification avant de permettre à l’utilisateur d’afficher l’onglet.</span><span class="sxs-lookup"><span data-stu-id="91fd5-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="91fd5-110">Si l’utilisateur possède les informations d’identification appropriées, affichez l’onglet sur lequel l’utilisateur a cliqué.</span><span class="sxs-lookup"><span data-stu-id="91fd5-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="91fd5-111">Si l’utilisateur ne dispose pas des informations d’identification appropriées, affichez une boîte de message ou une autre interface utilisateur indiquant qu’il n’y a pas d’accès, puis revenez à l’onglet initial.</span><span class="sxs-lookup"><span data-stu-id="91fd5-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="91fd5-112">Lorsque vous implémentez cette fonctionnalité dans vos applications de production, vous pouvez effectuer cette vérification des informations d' <xref:System.Windows.Forms.Form.Load> identification pendant l’événement du formulaire.</span><span class="sxs-lookup"><span data-stu-id="91fd5-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="91fd5-113">Cela vous permettra de masquer l’onglet avant l’affichage d’une interface utilisateur, ce qui constitue une approche bien plus propre à la programmation.</span><span class="sxs-lookup"><span data-stu-id="91fd5-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="91fd5-114">La méthodologie utilisée ci-dessous (vérification des informations d’identification et désactivation <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> de l’onglet pendant l’événement) est à titre indicatif.</span><span class="sxs-lookup"><span data-stu-id="91fd5-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="91fd5-115">Si vous avez plus de deux pages d’onglets, affichez éventuellement une page d’onglets différente de celle d’origine.</span><span class="sxs-lookup"><span data-stu-id="91fd5-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="91fd5-116">Dans l’exemple ci-dessous <xref:System.Windows.Forms.CheckBox> , un contrôle est utilisé à la place de la vérification des informations d’identification, car les critères d’accès à l’onglet varient en fonction de l’application.</span><span class="sxs-lookup"><span data-stu-id="91fd5-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="91fd5-117">Lorsque l' <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> événement est déclenché, si la vérification des informations d’identification a la valeur true (autrement dit, si la case à cocher `TabPage2` est activée) et si l’onglet sélectionné est (l’onglet avec les `TabPage2` informations confidentielles, dans cet exemple), est affiché.</span><span class="sxs-lookup"><span data-stu-id="91fd5-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="91fd5-118">Sinon, `TabPage3` est affiché et une boîte de message s’affiche pour l’utilisateur, indiquant qu’il ne dispose pas des privilèges d’accès appropriés.</span><span class="sxs-lookup"><span data-stu-id="91fd5-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="91fd5-119">Le code ci-dessous suppose un formulaire avec <xref:System.Windows.Forms.CheckBox> un contrôle`CredentialCheck`() et <xref:System.Windows.Forms.TabControl> un contrôle avec trois pages d’onglets.</span><span class="sxs-lookup"><span data-stu-id="91fd5-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="91fd5-120">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="91fd5-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=   
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="91fd5-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="91fd5-121">See also</span></span>

- [<span data-ttu-id="91fd5-122">Vue d’ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="91fd5-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="91fd5-123">Guide pratique pour Ajouter un contrôle à une page d’onglets</span><span class="sxs-lookup"><span data-stu-id="91fd5-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="91fd5-124">Guide pratique pour Ajouter et supprimer des onglets avec le TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="91fd5-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="91fd5-125">Guide pratique pour Modifier l’apparence du Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="91fd5-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
