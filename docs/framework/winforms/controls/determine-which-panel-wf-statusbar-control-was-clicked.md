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
ms.openlocfilehash: a659de62965d17e965eee2f750337a08ae1801e0
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053719"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Procédure : déterminer sur quel panneau l’utilisateur a cliqué dans le contrôle StatusBar Windows Forms
> [!IMPORTANT]
>  Le <xref:System.Windows.Forms.StatusStrip> et <xref:System.Windows.Forms.ToolStripStatusLabel> contrôles remplacent et ajoutent des fonctionnalités à la <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôle ; Toutefois, le <xref:System.Windows.Forms.StatusBar> et <xref:System.Windows.Forms.StatusBarPanel> contrôles ont été conservés pour la compatibilité descendante et une utilisation ultérieure, si vous Choisissez.  
  
 Au programme le [du contrôle StatusBar](statusbar-control-windows-forms.md) contrôle à répondre aux clics de l’utilisateur, utilisez une instruction case dans la <xref:System.Windows.Forms.StatusBar.PanelClick> événement. L’événement contient un argument (l’argument panel), qui contient une référence à l’utilisateur a cliqué dessus <xref:System.Windows.Forms.StatusBarPanel>. À l’aide de cette référence, vous pouvez déterminer l’index du panneau et programmer en conséquence.  
  
> [!NOTE]
>  Vérifiez que le <xref:System.Windows.Forms.StatusBar> du contrôle <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> propriété est définie sur `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Pour déterminer l’utilisateur a cliqué sur le panneau  
  
1. Dans le <xref:System.Windows.Forms.StatusBar.PanelClick> Gestionnaire d’événements, utilisez un `Select Case` (en Visual Basic) ou `switch case` (Visual C# ou Visual C++) pour déterminer le panneau qui a été utilisé en examinant l’index du panneau dans les arguments d’événement.  
  
     L’exemple de code suivant nécessite la présence, dans le formulaire, d’un <xref:System.Windows.Forms.StatusBar> contrôle, `StatusBar1`et deux <xref:System.Windows.Forms.StatusBarPanel> objets, `StatusBarPanel1` et `StatusBarPanel2`.  
  
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
  
     (Visual C#, Visual C++) Placez le code suivant dans le constructeur du formulaire pour inscrire le Gestionnaire d’événements.  
  
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
- [Guide pratique pour Définir la taille des panneaux de barre d’état](how-to-set-the-size-of-status-bar-panels.md)
- [Procédure pas à pas : La mise à jour des informations de barre d’état en cours d’exécution](walkthrough-updating-status-bar-information-at-run-time.md)
- [Vue d’ensemble du contrôle StatusBar](statusbar-control-overview-windows-forms.md)
