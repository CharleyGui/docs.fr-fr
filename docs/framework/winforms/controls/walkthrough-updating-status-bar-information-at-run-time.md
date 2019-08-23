---
title: 'Procédure pas à pas : mise à jour des informations de barre d’état au moment de l’exécution'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], updating at run time
- status bars [Windows Forms], refreshing panels
- StatusBar control [Windows Forms], refreshing panels
- panels [Windows Forms], refreshing status bar
ms.assetid: cc2abb06-c082-49f7-a5a3-2fd1bbcb58d1
ms.openlocfilehash: 670746a1b964a85bc5136d976d831c6848466797
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930982"
---
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a>Procédure pas à pas : mise à jour des informations de barre d’état au moment de l’exécution
> [!IMPORTANT]
> Les <xref:System.Windows.Forms.StatusStrip> contrôles <xref:System.Windows.Forms.ToolStripStatusLabel> et <xref:System.Windows.Forms.StatusBar> remplacent et ajoutent des fonctionnalités <xref:System.Windows.Forms.StatusBarPanel> aux contrôles et; toutefois <xref:System.Windows.Forms.StatusBar> , <xref:System.Windows.Forms.StatusBarPanel> les contrôles et sont conservés pour la compatibilité descendante et l’utilisation future, si vous Choisissez.  
  
 Il arrive souvent qu’un programme vous demande de mettre à jour dynamiquement le contenu des panneaux de la barre d’état au moment de l’exécution en cas de modification de l’état de l’application ou de toute autre interaction utilisateur. Il s’agit d’un moyen couramment utilisé pour indiquer aux utilisateurs que des touches telles que Verr. maj, Verr. num ou Arrêt défil sont activées, ou pour fournir la date ou une horloge pour référence.  
  
 Dans l’exemple suivant, vous allez utiliser une instance de la <xref:System.Windows.Forms.StatusBarPanel> classe pour héberger une horloge.  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a>Pour préparer la mise à jour de la barre d’état  
  
1. Créez un nouveau Windows Form.  
  
2. Ajoutez un contrôle <xref:System.Windows.Forms.StatusBar> à votre formulaire. Pour plus d’informations, consultez [Guide pratique pour Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.  
  
3. Ajoutez un panneau de barre d’état <xref:System.Windows.Forms.StatusBar> à votre contrôle. Pour plus d’informations, consultez [Guide pratique pour Ajoutez des panneaux à un contrôle](how-to-add-panels-to-a-statusbar-control.md)StatusBar.  
  
4. Pour le <xref:System.Windows.Forms.StatusBar> contrôle que vous avez ajouté à votre formulaire, <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> affectez `true`à la propriété la valeur.  
  
5. Ajoutez un composant <xref:System.Windows.Forms.Timer> Windows Forms au formulaire.  
  
    > [!NOTE]
    > Le composant <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Windows Forms est conçu pour un environnement Windows Forms. Si vous avez besoin d’un minuteur adapté à un environnement de serveur, consultez l’article [Introduction aux minuteurs serveur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).  
  
6. Affectez à la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> la valeur `true`.  
  
7. Affectez <xref:System.Windows.Forms.Timer.Interval%2A> à la propriété <xref:System.Windows.Forms.Timer> de la valeur 30000.  
  
    > [!NOTE]
    > La <xref:System.Windows.Forms.Timer.Interval%2A> propriété<xref:System.Windows.Forms.Timer> du composant est définie sur 30 secondes (30 000 millisecondes) pour garantir qu’une heure précise est reflétée dans l’heure affichée.  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a>Pour implémenter la minuterie afin de mettre à jour la barre d’état  
  
1. Insérez le code suivant dans le gestionnaire d’événements du <xref:System.Windows.Forms.Timer> composant pour mettre à jour le panneau <xref:System.Windows.Forms.StatusBar> du contrôle.  
  
    ```vb  
    Private Sub Timer1_Tick(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Timer1.Tick  
       StatusBar1.Panels(0).Text = Now.ToShortTimeString  
    End Sub  
    ```  
  
    ```csharp  
    private void timer1_Tick(object sender, System.EventArgs e)  
    {  
       statusBar1.Panels[0].Text = DateTime.Now.ToShortTimeString();  
    }  
    ```  
  
    ```cpp  
    private:  
      System::Void timer1_Tick(System::Object ^ sender,  
        System::EventArgs ^ e)  
      {  
        statusBar1->Panels[0]->Text =  
          DateTime::Now.ToShortTimeString();  
      }  
    ```  
  
     À ce stade, vous êtes prêt à exécuter l’application et à voir apparaître l’horloge dans le panneau de la barre d’état.  
  
### <a name="to-test-the-application"></a>Pour tester l'application  
  
1. Déboguez l’application et appuyez sur la touche F5 pour l’exécuter. Pour plus d’informations sur le débogage, consultez l’article [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).  
  
    > [!NOTE]
    > L’horloge apparaîtra dans la barre d’état au bout de 30 secondes environ. Cela permet d’obtenir l’heure la plus précise possible. À l’inverse, pour que l’horloge apparaisse plus tôt, vous pouvez réduire la valeur <xref:System.Windows.Forms.Timer.Interval%2A> de la propriété que vous avez définie à l’étape 7 de la procédure précédente.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Guide pratique : Ajouter des panneaux à un contrôle StatusBar](how-to-add-panels-to-a-statusbar-control.md)
- [Guide pratique pour Déterminer le panneau du contrôle Windows Forms StatusBar sur lequel l’utilisateur a cliqué](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Vue d’ensemble du contrôle StatusBar](statusbar-control-overview-windows-forms.md)
