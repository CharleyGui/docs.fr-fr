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
# <a name="how-to-disable-tab-pages"></a><span data-ttu-id="46a5f-102">Comment : désactiver les pages d'onglets</span><span class="sxs-lookup"><span data-stu-id="46a5f-102">How to: Disable Tab Pages</span></span>
<span data-ttu-id="46a5f-103">À certaines occasions, vous voudrez restreindre l’accès aux données disponibles dans votre application Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="46a5f-103">On some occasions, you will want to restrict access to data that is available within your Windows Forms application.</span></span> <span data-ttu-id="46a5f-104">Un exemple de ceci peut être quand vous avez des données affichées dans les pages d’onglet d’un contrôle d’onglet ; les administrateurs pourraient avoir des informations sur une page d’onglet que vous voudriez restreindre des utilisateurs d’invités ou de niveau inférieur.</span><span class="sxs-lookup"><span data-stu-id="46a5f-104">One example of this might be when you have data displayed in the tab pages of a tab control; administrators could have information on a tab page that you would want to restrict from guest or lower-level users.</span></span>  
  
### <a name="to-disable-tab-pages-programmatically"></a><span data-ttu-id="46a5f-105">Désactiver les pages d’onglets programmatiquement</span><span class="sxs-lookup"><span data-stu-id="46a5f-105">To disable tab pages programmatically</span></span>  
  
1. <span data-ttu-id="46a5f-106">Écrivez du code pour <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> gérer l’événement du contrôle de l’onglet.</span><span class="sxs-lookup"><span data-stu-id="46a5f-106">Write code to handle the tab control's <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event.</span></span> <span data-ttu-id="46a5f-107">C’est l’événement qui est soulevé lorsque l’utilisateur passe d’un onglet à l’autre.</span><span class="sxs-lookup"><span data-stu-id="46a5f-107">This is the event that is raised when the user switches from one tab to the next.</span></span>  
  
2. <span data-ttu-id="46a5f-108">Vérifiez les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="46a5f-108">Check credentials.</span></span> <span data-ttu-id="46a5f-109">Selon les informations présentées, vous pouvez vérifier le nom d’utilisateur que l’utilisateur a connecté avec ou une autre forme d’informations d’identification avant de permettre à l’utilisateur de voir l’onglet.</span><span class="sxs-lookup"><span data-stu-id="46a5f-109">Depending upon the information presented, you may want to check the user name the user has logged in with or some other form of credentials before allowing the user to view the tab.</span></span>  
  
3. <span data-ttu-id="46a5f-110">Si l’utilisateur dispose d’informations d’identification appropriées, affichez l’onglet qui a été cliqué.</span><span class="sxs-lookup"><span data-stu-id="46a5f-110">If the user has appropriate credentials, display the tab that was clicked.</span></span> <span data-ttu-id="46a5f-111">Si l’utilisateur n’a pas les informations d’identification appropriées, affichez une boîte de message ou une autre interface utilisateur indiquant qu’il n’y a pas d’accès et retournez à l’onglet initial.</span><span class="sxs-lookup"><span data-stu-id="46a5f-111">If the user does not have appropriate credentials, display a message box or some other user interface indicating that they do not have access, and return to the initial tab.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="46a5f-112">Lorsque vous implémentez cette fonctionnalité dans vos applications de production, vous pouvez effectuer cette vérification d’informations lors de l’événement du <xref:System.Windows.Forms.Form.Load> formulaire.</span><span class="sxs-lookup"><span data-stu-id="46a5f-112">When you implement this functionality in your production applications, you can perform this credential check during the form's <xref:System.Windows.Forms.Form.Load> event.</span></span> <span data-ttu-id="46a5f-113">Cela vous permettra de masquer l’onglet avant toute interface utilisateur est affiché, qui est une approche beaucoup plus propre de la programmation.</span><span class="sxs-lookup"><span data-stu-id="46a5f-113">This will allow you to hide the tab before any user interface is shown, which is a much cleaner approach to programming.</span></span> <span data-ttu-id="46a5f-114">La méthodologie utilisée ci-dessous (vérification des informations <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> d’identification et désactivation de l’onglet pendant l’événement) est à des fins d’illustration.</span><span class="sxs-lookup"><span data-stu-id="46a5f-114">The methodology used below (checking credentials and disabling the tab during the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event) is for illustrative purposes.</span></span>  
  
4. <span data-ttu-id="46a5f-115">Optionnellement, si vous avez plus de deux pages d’onglets, affichez une page d’onglet différente de l’original.</span><span class="sxs-lookup"><span data-stu-id="46a5f-115">Optionally, if you have more than two tab pages, display a tab page different from the original.</span></span>  
  
     <span data-ttu-id="46a5f-116">Dans l’exemple <xref:System.Windows.Forms.CheckBox> ci-dessous, un contrôle est utilisé au lieu de vérifier les informations d’identification, car les critères d’accès à l’onglet varient selon l’application.</span><span class="sxs-lookup"><span data-stu-id="46a5f-116">In the example below, a <xref:System.Windows.Forms.CheckBox> control is used in lieu of checking the credentials, as the criteria for access to the tab will vary by application.</span></span> <span data-ttu-id="46a5f-117">Lorsque <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> l’événement est soulevé, si la vérification des informations d’identification est `TabPage2` vraie (c’est-à-dire que `TabPage2` la case à cocher est cochée) et que l’onglet sélectionné est (l’onglet avec les informations confidentielles, dans cet exemple), est alors affiché.</span><span class="sxs-lookup"><span data-stu-id="46a5f-117">When the <xref:System.Windows.Forms.TabControl.SelectedIndexChanged> event is raised, if the credential check is true (that is, the check box is checked) and the selected tab is `TabPage2` (the tab with the confidential information, in this example), then `TabPage2` is displayed.</span></span> <span data-ttu-id="46a5f-118">Dans `TabPage3` le cas contraire, est affiché et une boîte de message est montrée à l’utilisateur, indiquant qu’ils n’avaient pas les privilèges d’accès appropriés.</span><span class="sxs-lookup"><span data-stu-id="46a5f-118">Otherwise, `TabPage3` is displayed and a message box is shown to the user, indicating they did not have appropriate access privileges.</span></span> <span data-ttu-id="46a5f-119">Le code ci-dessous suppose <xref:System.Windows.Forms.CheckBox> un`CredentialCheck`formulaire <xref:System.Windows.Forms.TabControl> avec un contrôle ( ) et un contrôle avec trois pages d’onglet.</span><span class="sxs-lookup"><span data-stu-id="46a5f-119">The code below assumes a form with a <xref:System.Windows.Forms.CheckBox> control (`CredentialCheck`) and a <xref:System.Windows.Forms.TabControl> control with three tab pages.</span></span>  
  
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
  
     <span data-ttu-id="46a5f-120">(Visual C, Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.</span><span class="sxs-lookup"><span data-stu-id="46a5f-120">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.tabControl1.SelectedIndexChanged +=
       new System.EventHandler(this.tabControl1_SelectedIndexChanged);  
    ```  
  
    ```cpp  
    this->tabControl1->SelectedIndexChanged +=  
       gcnew System::EventHandler(this, &Form1::tabControl1_SelectedIndexChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="46a5f-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46a5f-121">See also</span></span>

- [<span data-ttu-id="46a5f-122">Vue d'ensemble du contrôle TabControl</span><span class="sxs-lookup"><span data-stu-id="46a5f-122">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="46a5f-123">Comment : ajouter un contrôle à une page d'onglet</span><span class="sxs-lookup"><span data-stu-id="46a5f-123">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="46a5f-124">Guide pratique pour ajouter et supprimer des onglets avec le contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46a5f-124">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
- [<span data-ttu-id="46a5f-125">Comment : modifier l'apparence du contrôle TabControl Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46a5f-125">How to: Change the Appearance of the Windows Forms TabControl</span></span>](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
