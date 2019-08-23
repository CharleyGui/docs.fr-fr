---
title: 'Procédure : définir la taille des panneaux de barre d’état'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
ms.openlocfilehash: 4ba0f7f02b548a5d9ea1a99605a668f449b3e4a9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923628"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>Procédure : définir la taille des panneaux de barre d’état
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.ToolStripStatusLabel> remplace le contrôle <xref:System.Windows.Forms.StatusBar> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.StatusBar> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix.  
  
 Chaque instance de la <xref:System.Windows.Forms.StatusBarPanel> classe dans un contrôle de [contrôle StatusBar](statusbar-control-windows-forms.md) a un certain nombre de propriétés dynamiques qui déterminent sa largeur et son comportement de redimensionnement au moment de l’exécution.  
  
### <a name="to-set-the-size-of-a-panel"></a>Pour définir la taille d’un panneau  
  
1. Dans une procédure, définissez les <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>propriétés <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>, et <xref:System.Windows.Forms.StatusBarPanel.Width%2A> (ou n’importe quel sous-ensemble) des panneaux de la barre d’État à l’aide <xref:System.Windows.Forms.StatusBar.Panels%2A> de leur index <xref:System.Windows.Forms.StatusBarPanel> transmis via la propriété de la collection.  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [Procédure pas à pas : Mise à jour des informations de la barre d’État au moment de l’exécution](walkthrough-updating-status-bar-information-at-run-time.md)
- [Guide pratique : Déterminer le panneau du contrôle Windows Forms StatusBar sur lequel l’utilisateur a cliqué](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [Vue d’ensemble du contrôle StatusBar](statusbar-control-overview-windows-forms.md)
