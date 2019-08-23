---
title: 'Procédure : déterminer sur quel panneau l’utilisateur a cliqué dans le contrôle StatusBar Windows Forms'
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
ms.openlocfilehash: 6229d8965949641105cd0e9708474c3249d52d1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965722"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a><span data-ttu-id="ace38-102">Procédure : déterminer sur quel panneau l’utilisateur a cliqué dans le contrôle StatusBar Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ace38-102">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>
> [!IMPORTANT]
> <span data-ttu-id="ace38-103">Les <xref:System.Windows.Forms.StatusStrip> contrôles <xref:System.Windows.Forms.ToolStripStatusLabel> et <xref:System.Windows.Forms.StatusBar> remplacent et ajoutent des fonctionnalités <xref:System.Windows.Forms.StatusBarPanel> aux contrôles et; toutefois <xref:System.Windows.Forms.StatusBar> , <xref:System.Windows.Forms.StatusBarPanel> les contrôles et sont conservés pour la compatibilité descendante et l’utilisation future, si vous Choisissez.</span><span class="sxs-lookup"><span data-stu-id="ace38-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="ace38-104">Pour programmer le contrôle [StatusBar](statusbar-control-windows-forms.md) pour répondre aux clics de l’utilisateur, utilisez une instruction case au <xref:System.Windows.Forms.StatusBar.PanelClick> sein de l’événement.</span><span class="sxs-lookup"><span data-stu-id="ace38-104">To program the [StatusBar Control](statusbar-control-windows-forms.md) control to respond to user clicks, use a case statement within the <xref:System.Windows.Forms.StatusBar.PanelClick> event.</span></span> <span data-ttu-id="ace38-105">L’événement contient un argument (l’argument Panel), qui contient une référence à l’utilisateur sur <xref:System.Windows.Forms.StatusBarPanel>lequel l’utilisateur a cliqué.</span><span class="sxs-lookup"><span data-stu-id="ace38-105">The event contains an argument (the panel argument), which contains a reference to the clicked <xref:System.Windows.Forms.StatusBarPanel>.</span></span> <span data-ttu-id="ace38-106">À l’aide de cette référence, vous pouvez déterminer l’index du panneau cliqué et programmer en conséquence.</span><span class="sxs-lookup"><span data-stu-id="ace38-106">Using this reference, you can determine the index of the clicked panel, and program accordingly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ace38-107">Vérifiez que la <xref:System.Windows.Forms.StatusBar> propriété du <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> contrôle a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="ace38-107">Ensure that the <xref:System.Windows.Forms.StatusBar> control's <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property is set to `true`.</span></span>  
  
### <a name="to-determine-which-panel-was-clicked"></a><span data-ttu-id="ace38-108">Pour déterminer le panneau sur lequel l’utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="ace38-108">To determine which panel was clicked</span></span>  
  
1. <span data-ttu-id="ace38-109">Dans le <xref:System.Windows.Forms.StatusBar.PanelClick> gestionnaire d’événements, utilisez `Select Case` une instruction (en Visual Basic `switch case` ) ou C# (visuel C++ou visuel) pour déterminer le volet sur lequel l’utilisateur a cliqué en examinant l’index du panneau cliqué dans les arguments de l’événement.</span><span class="sxs-lookup"><span data-stu-id="ace38-109">In the <xref:System.Windows.Forms.StatusBar.PanelClick> event handler, use a `Select Case` (in Visual Basic) or `switch case` (Visual C# or Visual C++) statement to determine which panel was clicked by examining the index of the clicked panel in the event arguments.</span></span>  
  
     <span data-ttu-id="ace38-110">L’exemple de code suivant requiert la présence, sur le formulaire, d' <xref:System.Windows.Forms.StatusBar> un contrôle `StatusBar1`, et de <xref:System.Windows.Forms.StatusBarPanel> deux objets `StatusBarPanel1` , `StatusBarPanel2`et.</span><span class="sxs-lookup"><span data-stu-id="ace38-110">The following code example requires the presence, on the form, of a <xref:System.Windows.Forms.StatusBar> control, `StatusBar1`, and two <xref:System.Windows.Forms.StatusBarPanel> objects, `StatusBarPanel1` and `StatusBarPanel2`.</span></span>  
  
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
  
     <span data-ttu-id="ace38-111">(Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="ace38-111">(Visual C#, Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ace38-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ace38-112">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="ace38-113">Guide pratique pour Définir la taille des panneaux de la barre d’État</span><span class="sxs-lookup"><span data-stu-id="ace38-113">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="ace38-114">Procédure pas à pas : Mise à jour des informations de la barre d’État au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="ace38-114">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="ace38-115">Vue d’ensemble du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="ace38-115">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
