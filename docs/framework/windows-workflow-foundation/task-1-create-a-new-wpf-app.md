---
title: 'Tâche 1 : créer une application Windows Presentation Foundation'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 3205840da575041b449eb841fc8084e89937fca7
ms.sourcegitcommit: 10db6551ea3c971470cf5d2cc21ba1cbcefe5c55
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2019
ms.locfileid: "72031899"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a><span data-ttu-id="dd169-102">Tâche 1 : créer une application Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="dd169-102">Task 1: Create a New Windows Presentation Foundation Application</span></span>

<span data-ttu-id="dd169-103">Dans cette tâche, vous allez créer une application Windows Presentation Foundatione (WPF) vide à l’aide du modèle Visual Studio d’application WPF et ajouter des références aux assemblys de workflow [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] appropriés.</span><span class="sxs-lookup"><span data-stu-id="dd169-103">In this task, you will create an empty Windows Presentation Foundation (WPF) application by using the WPF Application Visual Studio template and add references to the appropriate [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] workflow assemblies.</span></span>  
  
## <a name="to-create-the-wpf-application-project"></a><span data-ttu-id="dd169-104">Pour créer le projet d'application WPF</span><span class="sxs-lookup"><span data-stu-id="dd169-104">To create the WPF Application project</span></span>

1. <span data-ttu-id="dd169-105">Ouvrez Visual Studio et, dans le menu **fichier** , pointez sur **nouveau**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="dd169-105">Open Visual Studio and on the **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="dd169-106">Dans la boîte de dialogue **nouveau projet** , sélectionnez **Visual C#**  ou **Visual Basic** dans le volet **modèles installés** sur le côté gauche de la zone.</span><span class="sxs-lookup"><span data-stu-id="dd169-106">In the **New Project** dialog box, select either **Visual C#** or **Visual Basic** from the **Installed Templates** pane on the left side of the box.</span></span> <span data-ttu-id="dd169-107">Si la langue de votre choix n’apparaît pas, recherchez dans **autres langues**.</span><span class="sxs-lookup"><span data-stu-id="dd169-107">If the language of your choice does not appear, look under **Other Languages**.</span></span>

3. <span data-ttu-id="dd169-108">Sélectionnez **Windows** dans le volet **modèles installés** .</span><span class="sxs-lookup"><span data-stu-id="dd169-108">Select **Windows** in the **Installed Templates** pane.</span></span>

4. <span data-ttu-id="dd169-109">Dans le volet supérieur, vérifiez que (la valeur par défaut) **.NET Framework 4** a été sélectionné dans la zone de liste déroulante, puis sélectionnez **application WPF**.</span><span class="sxs-lookup"><span data-stu-id="dd169-109">In the top pane, confirm that (the default value) **.NET Framework 4** has been selected in the drop-down list box, and then select **WPF Application**.</span></span>

5. <span data-ttu-id="dd169-110">Définissez le nom du projet sur **HostingApplication** en bas de la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="dd169-110">Set the name of the project to **HostingApplication** at the bottom of the window.</span></span>

6. <span data-ttu-id="dd169-111">Définissez le nom de la solution sur **RehostingTheDesigner**.</span><span class="sxs-lookup"><span data-stu-id="dd169-111">Set the solution name to **RehostingTheDesigner**.</span></span>

7. <span data-ttu-id="dd169-112">Cliquez sur **OK** pour créer le projet d’application.</span><span class="sxs-lookup"><span data-stu-id="dd169-112">Click **OK** to create the application project.</span></span> <span data-ttu-id="dd169-113">Visual Studio crée une interface utilisateur WPF de base pour votre application et comprend les fichiers XAML et code-behind appropriés.</span><span class="sxs-lookup"><span data-stu-id="dd169-113">Visual Studio creates a basic WPF UI for your application and includes the appropriate XAML and code-behind files.</span></span>

8. <span data-ttu-id="dd169-114">Ajoutez des références aux assemblys **WorkflowModel** .</span><span class="sxs-lookup"><span data-stu-id="dd169-114">Add references to **WorkflowModel** assemblies.</span></span> <span data-ttu-id="dd169-115">Pour ce faire, dans **Explorateur de solutions**, cliquez avec le bouton droit sur le projet **HostingApplication** , puis sélectionnez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="dd169-115">To do this, in **Solution Explorer**, right-click the **HostingApplication** project and select **Add Reference**.</span></span>

9. <span data-ttu-id="dd169-116">Dans la boîte de dialogue **Ajouter une référence** , cliquez sur l’onglet **.net** , maintenez la touche CTRL enfoncée, sélectionnez les assemblys suivants, puis cliquez sur **OK**:</span><span class="sxs-lookup"><span data-stu-id="dd169-116">In the **Add Reference** dialog box, click the **.NET** tab, hold down the CTRL key, select the following assemblies, and then click **OK**:</span></span>

    - <span data-ttu-id="dd169-117">System.Activities</span><span class="sxs-lookup"><span data-stu-id="dd169-117">System.Activities</span></span>
    - <span data-ttu-id="dd169-118">System.Activities.Presentation</span><span class="sxs-lookup"><span data-stu-id="dd169-118">System.Activities.Presentation</span></span>
    - <span data-ttu-id="dd169-119">System.Activities.Core.Presentation</span><span class="sxs-lookup"><span data-stu-id="dd169-119">System.Activities.Core.Presentation</span></span>

10. <span data-ttu-id="dd169-120">Voir [Task 2 : Hébergez le Concepteur de flux de travail @ no__t-0 pour apprendre à héberger la zone de conception du concepteur de Workflow.</span><span class="sxs-lookup"><span data-stu-id="dd169-120">See [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md) to learn how to host the workflow designer design canvas.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd169-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd169-121">See also</span></span>

- [<span data-ttu-id="dd169-122">Réhébergement du concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="dd169-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- <span data-ttu-id="dd169-123">@no__t 0Task 2 : Héberger le Concepteur de flux de travail @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="dd169-123">[Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md)</span></span>
