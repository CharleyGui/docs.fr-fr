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
# <a name="walkthrough-updating-status-bar-information-at-run-time"></a><span data-ttu-id="44c35-102">Procédure pas à pas : mise à jour des informations de barre d’état au moment de l’exécution</span><span class="sxs-lookup"><span data-stu-id="44c35-102">Walkthrough: Updating Status Bar Information at Run Time</span></span>
> [!IMPORTANT]
> <span data-ttu-id="44c35-103">Les <xref:System.Windows.Forms.StatusStrip> contrôles <xref:System.Windows.Forms.ToolStripStatusLabel> et <xref:System.Windows.Forms.StatusBar> remplacent et ajoutent des fonctionnalités <xref:System.Windows.Forms.StatusBarPanel> aux contrôles et; toutefois <xref:System.Windows.Forms.StatusBar> , <xref:System.Windows.Forms.StatusBarPanel> les contrôles et sont conservés pour la compatibilité descendante et l’utilisation future, si vous Choisissez.</span><span class="sxs-lookup"><span data-stu-id="44c35-103">The <xref:System.Windows.Forms.StatusStrip> and <xref:System.Windows.Forms.ToolStripStatusLabel> controls replace and add functionality to the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls; however, the <xref:System.Windows.Forms.StatusBar> and <xref:System.Windows.Forms.StatusBarPanel> controls are retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="44c35-104">Il arrive souvent qu’un programme vous demande de mettre à jour dynamiquement le contenu des panneaux de la barre d’état au moment de l’exécution en cas de modification de l’état de l’application ou de toute autre interaction utilisateur.</span><span class="sxs-lookup"><span data-stu-id="44c35-104">Often, a program will call for you to update the contents of status bar panels dynamically at run time, based on changes to application state or other user interaction.</span></span> <span data-ttu-id="44c35-105">Il s’agit d’un moyen couramment utilisé pour indiquer aux utilisateurs que des touches telles que Verr. maj, Verr. num ou Arrêt défil sont activées, ou pour fournir la date ou une horloge pour référence.</span><span class="sxs-lookup"><span data-stu-id="44c35-105">This is a common way to signal users that keys such as the CAPS LOCK, NUM LOCK, or SCROLL LOCK are enabled, or to provide the date or a clock as a convenient reference.</span></span>  
  
 <span data-ttu-id="44c35-106">Dans l’exemple suivant, vous allez utiliser une instance de la <xref:System.Windows.Forms.StatusBarPanel> classe pour héberger une horloge.</span><span class="sxs-lookup"><span data-stu-id="44c35-106">In the following example, you will use an instance of the <xref:System.Windows.Forms.StatusBarPanel> class to host a clock.</span></span>  
  
### <a name="to-get-the-status-bar-ready-for-updating"></a><span data-ttu-id="44c35-107">Pour préparer la mise à jour de la barre d’état</span><span class="sxs-lookup"><span data-stu-id="44c35-107">To get the status bar ready for updating</span></span>  
  
1. <span data-ttu-id="44c35-108">Créez un nouveau Windows Form.</span><span class="sxs-lookup"><span data-stu-id="44c35-108">Create a new Windows form.</span></span>  
  
2. <span data-ttu-id="44c35-109">Ajoutez un contrôle <xref:System.Windows.Forms.StatusBar> à votre formulaire.</span><span class="sxs-lookup"><span data-stu-id="44c35-109">Add a <xref:System.Windows.Forms.StatusBar> control to your form.</span></span> <span data-ttu-id="44c35-110">Pour plus d’informations, consultez [Guide pratique pour Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="44c35-110">For details, see [How to: Add Controls to Windows Forms](how-to-add-controls-to-windows-forms.md).</span></span>  
  
3. <span data-ttu-id="44c35-111">Ajoutez un panneau de barre d’état <xref:System.Windows.Forms.StatusBar> à votre contrôle.</span><span class="sxs-lookup"><span data-stu-id="44c35-111">Add a status bar panel to your <xref:System.Windows.Forms.StatusBar> control.</span></span> <span data-ttu-id="44c35-112">Pour plus d’informations, consultez [Guide pratique pour Ajoutez des panneaux à un contrôle](how-to-add-panels-to-a-statusbar-control.md)StatusBar.</span><span class="sxs-lookup"><span data-stu-id="44c35-112">For details, see [How to: Add Panels to a StatusBar Control](how-to-add-panels-to-a-statusbar-control.md).</span></span>  
  
4. <span data-ttu-id="44c35-113">Pour le <xref:System.Windows.Forms.StatusBar> contrôle que vous avez ajouté à votre formulaire, <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> affectez `true`à la propriété la valeur.</span><span class="sxs-lookup"><span data-stu-id="44c35-113">For the <xref:System.Windows.Forms.StatusBar> control you added to your form, set the <xref:System.Windows.Forms.StatusBar.ShowPanels%2A> property to `true`.</span></span>  
  
5. <span data-ttu-id="44c35-114">Ajoutez un composant <xref:System.Windows.Forms.Timer> Windows Forms au formulaire.</span><span class="sxs-lookup"><span data-stu-id="44c35-114">Add a Windows Forms <xref:System.Windows.Forms.Timer> component to the form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="44c35-115">Le composant <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> Windows Forms est conçu pour un environnement Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="44c35-115">The Windows Forms <xref:System.Windows.Forms.Timer?displayProperty=nameWithType> component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="44c35-116">Si vous avez besoin d’un minuteur adapté à un environnement de serveur, consultez l’article [Introduction aux minuteurs serveur](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="44c35-116">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
6. <span data-ttu-id="44c35-117">Affectez à la propriété <xref:System.Windows.Forms.Timer.Enabled%2A> la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="44c35-117">Set the <xref:System.Windows.Forms.Timer.Enabled%2A> property to `true`.</span></span>  
  
7. <span data-ttu-id="44c35-118">Affectez <xref:System.Windows.Forms.Timer.Interval%2A> à la propriété <xref:System.Windows.Forms.Timer> de la valeur 30000.</span><span class="sxs-lookup"><span data-stu-id="44c35-118">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> to 30000.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="44c35-119">La <xref:System.Windows.Forms.Timer.Interval%2A> propriété<xref:System.Windows.Forms.Timer> du composant est définie sur 30 secondes (30 000 millisecondes) pour garantir qu’une heure précise est reflétée dans l’heure affichée.</span><span class="sxs-lookup"><span data-stu-id="44c35-119">The <xref:System.Windows.Forms.Timer.Interval%2A> property of the <xref:System.Windows.Forms.Timer> component is set to 30 seconds (30,000 milliseconds) to ensure that an accurate time is reflected in the time displayed.</span></span>  
  
### <a name="to-implement-the-timer-to-update-the-status-bar"></a><span data-ttu-id="44c35-120">Pour implémenter la minuterie afin de mettre à jour la barre d’état</span><span class="sxs-lookup"><span data-stu-id="44c35-120">To implement the timer to update the status bar</span></span>  
  
1. <span data-ttu-id="44c35-121">Insérez le code suivant dans le gestionnaire d’événements du <xref:System.Windows.Forms.Timer> composant pour mettre à jour le panneau <xref:System.Windows.Forms.StatusBar> du contrôle.</span><span class="sxs-lookup"><span data-stu-id="44c35-121">Insert the following code into the event handler of the <xref:System.Windows.Forms.Timer> component to update the panel of the <xref:System.Windows.Forms.StatusBar> control.</span></span>  
  
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
  
     <span data-ttu-id="44c35-122">À ce stade, vous êtes prêt à exécuter l’application et à voir apparaître l’horloge dans le panneau de la barre d’état.</span><span class="sxs-lookup"><span data-stu-id="44c35-122">At this point, you are ready to run the application and observe the clock running in the status bar panel.</span></span>  
  
### <a name="to-test-the-application"></a><span data-ttu-id="44c35-123">Pour tester l'application</span><span class="sxs-lookup"><span data-stu-id="44c35-123">To test the application</span></span>  
  
1. <span data-ttu-id="44c35-124">Déboguez l’application et appuyez sur la touche F5 pour l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="44c35-124">Debug the application and press F5 to run it.</span></span> <span data-ttu-id="44c35-125">Pour plus d’informations sur le débogage, consultez l’article [Débogage dans Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="44c35-125">For details about debugging, see [Debugging in Visual Studio](/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="44c35-126">L’horloge apparaîtra dans la barre d’état au bout de 30 secondes environ.</span><span class="sxs-lookup"><span data-stu-id="44c35-126">It will take approximately 30 seconds for the clock to appear in the status bar.</span></span> <span data-ttu-id="44c35-127">Cela permet d’obtenir l’heure la plus précise possible.</span><span class="sxs-lookup"><span data-stu-id="44c35-127">This is to get the most accurate time possible.</span></span> <span data-ttu-id="44c35-128">À l’inverse, pour que l’horloge apparaisse plus tôt, vous pouvez réduire la valeur <xref:System.Windows.Forms.Timer.Interval%2A> de la propriété que vous avez définie à l’étape 7 de la procédure précédente.</span><span class="sxs-lookup"><span data-stu-id="44c35-128">Conversely, to make the clock appear sooner, you can reduce the value of the <xref:System.Windows.Forms.Timer.Interval%2A> property you set in step 7 in the previous procedure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c35-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="44c35-129">See also</span></span>

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [<span data-ttu-id="44c35-130">Guide pratique : Ajouter des panneaux à un contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="44c35-130">How to: Add Panels to a StatusBar Control</span></span>](how-to-add-panels-to-a-statusbar-control.md)
- [<span data-ttu-id="44c35-131">Guide pratique pour Déterminer le panneau du contrôle Windows Forms StatusBar sur lequel l’utilisateur a cliqué</span><span class="sxs-lookup"><span data-stu-id="44c35-131">How to: Determine Which Panel in the Windows Forms StatusBar Control Was Clicked</span></span>](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [<span data-ttu-id="44c35-132">Vue d’ensemble du contrôle StatusBar</span><span class="sxs-lookup"><span data-stu-id="44c35-132">StatusBar Control Overview</span></span>](statusbar-control-overview-windows-forms.md)
