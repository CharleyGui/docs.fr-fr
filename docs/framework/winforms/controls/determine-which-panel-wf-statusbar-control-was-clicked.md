---
title: Déterminer le panneau dans le contrôle StatusBar sur lequel l’utilisateur a cliqué
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
ms.openlocfilehash: 94619f8bd426a42e5dafa0db99880e20d24f9963
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746014"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l'utilisateur a cliqué
> [!IMPORTANT]
> Les contrôles <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> remplacent et ajoutent des fonctionnalités aux contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> ; Toutefois, les contrôles <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> sont conservés pour la compatibilité descendante et l’utilisation future, si vous le souhaitez.  
  
 Pour programmer le contrôle [StatusBar](statusbar-control-windows-forms.md) pour répondre aux clics de l’utilisateur, utilisez une instruction case au sein de l’événement <xref:System.Windows.Forms.StatusBar.PanelClick>. L’événement contient un argument (l’argument Panel), qui contient une référence à l' <xref:System.Windows.Forms.StatusBarPanel>sur lequel l’utilisateur a cliqué. À l’aide de cette référence, vous pouvez déterminer l’index du panneau cliqué et programmer en conséquence.  
  
> [!NOTE]
> Vérifiez que la propriété <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> du contrôle <xref:System.Windows.Forms.StatusBar> est définie sur `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Pour déterminer le panneau sur lequel l’utilisateur a cliqué  
  
1. Dans le gestionnaire d’événements <xref:System.Windows.Forms.StatusBar.PanelClick>, utilisez une instruction `Select Case` (dans Visual Basic) ou `switch case` C# (visuel C++ou visuel) pour déterminer le volet sur lequel l’utilisateur a cliqué en examinant l’index du panneau sur lequel l’utilisateur a cliqué dans les arguments de l’événement.  
  
     L’exemple de code suivant requiert la présence, sur le formulaire, d’un contrôle <xref:System.Windows.Forms.StatusBar>, `StatusBar1`et deux objets <xref:System.Windows.Forms.StatusBarPanel>, `StatusBarPanel1` et `StatusBarPanel2`.  
  
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
  
     (Visuel C#, visuel C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le gestionnaire d’événements.  
  
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
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Guide pratique pour définir la taille des panneaux de la barre d'état](how-to-set-the-size-of-status-bar-panels.md)
- [Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution](walkthrough-updating-status-bar-information-at-run-time.md)
- [Vue d’ensemble du contrôle StatusBar](statusbar-control-overview-windows-forms.md)
