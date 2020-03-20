---
title: Déterminer quel panneau dans statusBar Contrôle a été cliqué
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: eb3b10d515ba5b62236594e063ca7f060b34b73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182362"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="4ae0c-102">Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="4ae0c-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="4ae0c-103">Les <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> commandes et les commandes <xref:System.Windows.Forms.StatusBar> remplacent et ajoutent des fonctionnalités à la fonctionnalité et <xref:System.Windows.Forms.StatusBarPanel> les contrôles; cependant, <xref:System.Windows.Forms.StatusBar> les <xref:System.Windows.Forms.StatusBarPanel> contrôles et les contrôles sont conservés à la fois pour la compatibilité vers l’arrière et l’utilisation future, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="4ae0c-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="4ae0c-104">Pour programmer le contrôle [StatusBar pour](statusbar-control-windows-forms.md) répondre aux clics <xref:System.Windows.Forms.StatusBar.PanelClick> de l’utilisateur, utilisez une déclaration de cas dans l’événement.</span><span class="sxs-lookup"><span data-stu-id="4ae0c-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="4ae0c-105">L’événement contient un argument (l’argument du panel), qui contient une référence à la cliqué <xref:System.Windows.Forms.StatusBarPanel>.</span><span class="sxs-lookup"><span data-stu-id="4ae0c-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="4ae0c-106">À l’aide de cette référence, vous pouvez déterminer l’index du panneau cliqué et programmer en conséquence.</span><span class="sxs-lookup"><span data-stu-id="4ae0c-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ae0c-107">Assurez-vous <xref:System.Windows.Forms.StatusBar> que <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> la propriété `true`du contrôle est réglée à .</span><span class="sxs-lookup"><span data-stu-id="4ae0c-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="4ae0c-108">Pour déterminer quel panneau a été cliqué</span><span class="sxs-lookup"><span data-stu-id="4ae0c-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="4ae0c-109">Dans <xref:System.Windows.Forms.StatusBar.PanelClick> le gestionnaire d’événements, utilisez `Select Case` `switch case` une déclaration (dans Visual Basic) ou (Visual CMD ou Visual CMD) pour déterminer quel panneau a été cliqué en examinant l’index du panneau cliqué dans les arguments de l’événement.</span><span class="sxs-lookup"><span data-stu-id="4ae0c-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="4ae0c-110">L’exemple de code suivant exige la <xref:System.Windows.Forms.StatusBar> présence, `StatusBar1`sur <xref:System.Windows.Forms.StatusBarPanel> le `StatusBarPanel1` formulaire, d’un contrôle, , et deux objets, et `StatusBarPanel2`.</span><span class="sxs-lookup"><span data-stu-id="4ae0c-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     <span data-ttu-id="4ae0c-111">(Visual C, Visual CMMD) Placez le code suivant dans le constructeur du formulaire pour enregistrer le gestionnaire de l’événement.</span><span class="sxs-lookup"><span data-stu-id="4ae0c-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.statusBar1.PanelClick += new
       System.Windows.Forms.StatusBarPanelClickEventHandler
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4ae0c-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ae0c-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="4ae0c-113">Guide pratique pour définir la taille des panneaux de la barre d'état</span><span class="sxs-lookup"><span data-stu-id="4ae0c-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="4ae0c-114">Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="4ae0c-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="4ae0c-115">Vue d'ensemble du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="4ae0c-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
