---
title: 'Comment : ajouter des panneaux à un contrôle StatusBar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- panels [Windows Forms], status bars
- status bars [Windows Forms], adding panels
- StatusBar control [Windows Forms], adding panels
ms.assetid: 835e3902-288c-4c38-9d69-0696d8695009
ms.openlocfilehash: 386c8cae425c458ddf4c446a454ae4213761e651
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142197"
---
# <a name="how-to-add-panels-to-a-statusbar-control"></a><span data-ttu-id="4394f-102">Comment : ajouter des panneaux à un contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="4394f-102">How to: Add Panels to a StatusBar Control</span></span>
> [!IMPORTANT]
> <span data-ttu-id="4394f-103">Les <xref:System.Windows.Forms.StatusStrip> <xref:System.Windows.Forms.ToolStripStatusLabel> commandes et les commandes <xref:System.Windows.Forms.StatusBar> remplacent et ajoutent des fonctionnalités à la fonctionnalité et <xref:System.Windows.Forms.StatusBarPanel> les contrôles; cependant, <xref:System.Windows.Forms.StatusBar> les <xref:System.Windows.Forms.StatusBarPanel> contrôles et les contrôles sont conservés à la fois pour la compatibilité vers l’arrière et l’utilisation future, si vous le souhaitez.</span><span class="sxs-lookup"><span data-stu-id="4394f-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="4394f-104">La zone programmable dans un contrôle [StatusBar](statusbar-control-windows-forms.md) se compose d’instances de la <xref:System.Windows.Forms.StatusBarPanel> classe.</span><span class="sxs-lookup"><span data-stu-id="4394f-104">The programmable area within a [StatusBar Control](statusbar-control-windows-forms.md) control consists of instances of the <xref:System.Windows.Forms.StatusBarPanel> class.</span></span> <span data-ttu-id="4394f-105">Ceux-ci sont ajoutés <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> par des ajouts à la classe.</span><span class="sxs-lookup"><span data-stu-id="4394f-105">These are added through additions to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> class.</span></span>  
  
### <a name="to-add-panels-to-a-status-bar"></a><span data-ttu-id="4394f-106">Ajouter des panneaux à une barre d’état</span><span class="sxs-lookup"><span data-stu-id="4394f-106">To add panels to a status bar</span></span>  
  
1. <span data-ttu-id="4394f-107">Dans une procédure, créer des panneaux de <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>barre d’état en les ajoutant à la .</span><span class="sxs-lookup"><span data-stu-id="4394f-107">In a procedure, create status-bar panels by adding them to the <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection>.</span></span> <span data-ttu-id="4394f-108">Spécifier les paramètres de propriété pour <xref:System.Windows.Forms.StatusBar.Panels%2A> les panneaux individuels en utilisant son index passé par la propriété.</span><span class="sxs-lookup"><span data-stu-id="4394f-108">Specify property settings for individual panels by using its index passed through the <xref:System.Windows.Forms.StatusBar.Panels%2A> property.</span></span>  
  
     <span data-ttu-id="4394f-109">Dans l’exemple de code suivant, le chemin défini pour l’emplacement de l’icône est le dossier **Mes Documents.**</span><span class="sxs-lookup"><span data-stu-id="4394f-109">In the following code example, the path set for the location of the icon is the **My Documents** folder.</span></span> <span data-ttu-id="4394f-110">Cet emplacement est utilisé parce que vous pouvez supposer que la plupart des ordinateurs exécutant le système d’exploitation Windows inclura ce dossier.</span><span class="sxs-lookup"><span data-stu-id="4394f-110">This location is used because you can assume that most computers running the Windows operating system will include this folder.</span></span> <span data-ttu-id="4394f-111">Le choix de cet emplacement permet également aux utilisateurs ayant un minimum de niveaux d’accès au système d’exécuter l’application en toute sécurité.</span><span class="sxs-lookup"><span data-stu-id="4394f-111">Choosing this location also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="4394f-112">L’exemple suivant nécessite <xref:System.Windows.Forms.StatusBar> un formulaire avec un contrôle déjà ajouté.</span><span class="sxs-lookup"><span data-stu-id="4394f-112">The following example requires a form with a <xref:System.Windows.Forms.StatusBar> control already added.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4394f-113">Il <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> s’agit d’une collection zéro, donc le code devrait être mis en œuvre en conséquence.</span><span class="sxs-lookup"><span data-stu-id="4394f-113">The <xref:System.Windows.Forms.StatusBar.StatusBarPanelCollection> is a zero-based collection, so code should proceed accordingly.</span></span>  
  
    ```vb  
    Public Sub CreateStatusBarPanels()  
    ' Create panels and set text property.  
       StatusBar1.Panels.Add("One")  
       StatusBar1.Panels.Add("Two")  
       StatusBar1.Panels.Add("Three")  
    ' Set properties of StatusBar panels.  
    ' Set AutoSize property of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(1).AutoSize = StatusBarPanelAutoSize.Contents  
       StatusBar1.Panels(2).AutoSize = StatusBarPanelAutoSize.Contents  
    ' Set BorderStyle property of panels.  
       StatusBar1.Panels(0).BorderStyle = StatusBarPanelBorderStyle.Raised  
       StatusBar1.Panels(1).BorderStyle = StatusBarPanelBorderStyle.Sunken  
       StatusBar1.Panels(2).BorderStyle = StatusBarPanelBorderStyle.Raised  
    ' Set Icon property of third panel. You should replace the bolded  
    ' icon in the sample below with an icon of your own choosing.  
       StatusBar1.Panels(2).Icon = New _
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
       StatusBar1.ShowPanels = True  
    End Sub  
    ```  
  
    ```csharp  
    public void CreateStatusBarPanels()  
    {  
       // Create panels and set text property.  
       statusBar1.Panels.Add("One");  
       statusBar1.Panels.Add("Two");  
       statusBar1.Panels.Add("Three");  
       // Set properties of StatusBar panels.  
       // Set AutoSize property of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[1].AutoSize = StatusBarPanelAutoSize.Contents;  
       statusBar1.Panels[2].AutoSize = StatusBarPanelAutoSize.Contents;  
       // Set BorderStyle property of panels.  
       statusBar1.Panels[0].BorderStyle =  
          StatusBarPanelBorderStyle.Raised;  
       statusBar1.Panels[1].BorderStyle = StatusBarPanelBorderStyle.Sunken;  
       statusBar1.Panels[2].BorderStyle = StatusBarPanelBorderStyle.Raised;  
       // Set Icon property of third panel. You should replace the bolded  
       // icon in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       statusBar1.Panels[2].Icon =
          new System.Drawing.Icon (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       + @"\Icon.ico");  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void CreateStatusBarPanels()  
       {  
          // Create panels and set text property.  
          statusBar1->Panels->Add("One");  
          statusBar1->Panels->Add("Two");  
          statusBar1->Panels->Add("Three");  
          // Set properties of StatusBar panels.  
          // Set AutoSize property of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[1]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          statusBar1->Panels[2]->AutoSize =  
             StatusBarPanelAutoSize::Contents;  
          // Set BorderStyle property of panels.  
          statusBar1->Panels[0]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          statusBar1->Panels[1]->BorderStyle =  
             StatusBarPanelBorderStyle::Sunken;  
          statusBar1->Panels[2]->BorderStyle =  
             StatusBarPanelBorderStyle::Raised;  
          // Set Icon property of third panel.  
          // You should replace the bolded image
          // in the sample below with an icon of your own choosing.  
          statusBar1->Panels[2]->Icon =  
             gcnew System::Drawing::Icon(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Icon.ico"));  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4394f-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4394f-114">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- <span data-ttu-id="4394f-115">[Boîte de dialogue Éditeur de collection](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="4394f-115">[Collection Editor Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/xc4yyekt(v=vs.100))</span></span>
- [<span data-ttu-id="4394f-116">Guide pratique pour définir la taille des panneaux de la barre d'état</span><span class="sxs-lookup"><span data-stu-id="4394f-116">How to: Set the Size of Status-Bar Panels</span></span>](how-to-set-the-size-of-status-bar-panels.md)
- [<span data-ttu-id="4394f-117">Procédure pas à pas : mise à jour des informations de barre d'état au moment de l'exécution</span><span class="sxs-lookup"><span data-stu-id="4394f-117">Walkthrough: Updating Status Bar Information at Run Time</span></span>](walkthrough-updating-status-bar-information-at-run-time.md)
- [<span data-ttu-id="4394f-118">Comment : déterminer le panneau du contrôle StatusBar Windows Forms sur lequel l’utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="4394f-118">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="4394f-119">Vue d'ensemble du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="4394f-119">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
