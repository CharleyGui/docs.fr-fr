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
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>Procédure : déterminer sur quel panneau l’utilisateur a cliqué dans le contrôle StatusBar Windows Forms
> [!IMPORTANT]
> Les <xref:System.Windows.Forms.StatusStrip> contrôles <xref:System.Windows.Forms.ToolStripStatusLabel> et <xref:System.Windows.Forms.StatusBar> remplacent et ajoutent des fonctionnalités <xref:System.Windows.Forms.StatusBarPanel> aux contrôles et; toutefois <xref:System.Windows.Forms.StatusBar> , <xref:System.Windows.Forms.StatusBarPanel> les contrôles et sont conservés pour la compatibilité descendante et l’utilisation future, si vous Choisissez.  
  
 Pour programmer le contrôle [StatusBar](statusbar-control-windows-forms.md) pour répondre aux clics de l’utilisateur, utilisez une instruction case au <xref:System.Windows.Forms.StatusBar.PanelClick> sein de l’événement. L’événement contient un argument (l’argument Panel), qui contient une référence à l’utilisateur sur <xref:System.Windows.Forms.StatusBarPanel>lequel l’utilisateur a cliqué. À l’aide de cette référence, vous pouvez déterminer l’index du panneau cliqué et programmer en conséquence.  
  
> [!NOTE]
> Vérifiez que la <xref:System.Windows.Forms.StatusBar> propriété du <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> contrôle a la valeur `true`.  
  
### <a name="to-determine-which-panel-was-clicked"></a>Pour déterminer le panneau sur lequel l’utilisateur a cliqué  
  
1. Dans le <xref:System.Windows.Forms.StatusBar.PanelClick> gestionnaire d’événements, utilisez `Select Case` une instruction (en Visual Basic `switch case` ) ou C# (visuel C++ou visuel) pour déterminer le volet sur lequel l’utilisateur a cliqué en examinant l’index du panneau cliqué dans les arguments de l’événement.  
  
     L’exemple de code suivant requiert la présence, sur le formulaire, d' <xref:System.Windows.Forms.StatusBar> un contrôle `StatusBar1`, et de <xref:System.Windows.Forms.StatusBarPanel> deux objets `StatusBarPanel1` , `StatusBarPanel2`et.  
  
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
- [Guide pratique pour Définir la taille des panneaux de la barre d’État](how-to-set-the-size-of-status-bar-panels.md)
- [Procédure pas à pas : Mise à jour des informations de la barre d’État au moment de l’exécution](walkthrough-updating-status-bar-information-at-run-time.md)
- [Vue d’ensemble du contrôle StatusBar](statusbar-control-overview-windows-forms.md)
