---
title: 'Procédure : créer un participant de suivi de personnalisé'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1b612c7e-2381-4a7c-b07a-77030415f2a3
ms.openlocfilehash: 5f00997b059d7ea6f6ac6fb6d7bd83e4515ac02a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275799"
---
# <a name="how-to-create-a-custom-tracking-participant"></a><span data-ttu-id="e1ed3-102">Procédure : créer un participant de suivi de personnalisé</span><span class="sxs-lookup"><span data-stu-id="e1ed3-102">How to: Create a Custom Tracking Participant</span></span>

<span data-ttu-id="e1ed3-103">Le suivi de workflow offre une visibilité dans l'état d'exécution de workflow.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-103">Workflow tracking provides visibility into the status of workflow execution.</span></span> <span data-ttu-id="e1ed3-104">L'exécution de workflow émet des enregistrements de suivi qui décrivent les événements de cycle de vie du workflow, les événements de cycle de vie de l'activité, la reprise de signet et les erreurs.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-104">The workflow runtime emits tracking records that describe workflow lifecycle events, activity lifecycle events, bookmark resumptions, and faults.</span></span> <span data-ttu-id="e1ed3-105">Ces enregistrements de suivi sont consommés par les participants de suivi.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-105">These tracking records are consumed by tracking participants.</span></span> <span data-ttu-id="e1ed3-106">Windows Workflow Foundation (WF) comprend un participant de suivi standard qui écrit des enregistrements de suivi en tant qu’événements de Suivi d’v nements pour Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="e1ed3-106">Windows Workflow Foundation (WF) includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="e1ed3-107">Si cela ne répond pas à vos besoins, vous pouvez également écrire un participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-107">If that does not meet your requirements, you can also write a custom tracking participant.</span></span> <span data-ttu-id="e1ed3-108">Cette étape du didacticiel décrit comment créer un participant de suivi et un modèle de suivi qui capturent la sortie des activités de `WriteLine` afin qu'elles puissent être affichées à l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-108">This tutorial step describes how to create a custom tracking participant and tracking profile that capture the output of `WriteLine` activities so that they can be displayed to the user.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e1ed3-109">Chaque rubrique du didacticiel de mise en route dépend des rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="e1ed3-110">Pour effectuer cette rubrique, vous devez d'abord terminer les rubriques précédentes.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-110">To complete this topic, you must first complete the previous topics.</span></span> <span data-ttu-id="e1ed3-111">Pour télécharger une version complète ou afficher une vidéo pas à pas du didacticiel, consultez [Windows Workflow Foundation (WF45)-prise en main didacticiel](https://go.microsoft.com/fwlink/?LinkID=248976).</span><span class="sxs-lookup"><span data-stu-id="e1ed3-111">To download a completed version or view a video walkthrough of the tutorial, see [Windows Workflow Foundation (WF45) - Getting Started Tutorial](https://go.microsoft.com/fwlink/?LinkID=248976).</span></span>  
  
## <a name="to-create-the-custom-tracking-participant"></a><span data-ttu-id="e1ed3-112">Pour créer le participant de suivi personnalisé</span><span class="sxs-lookup"><span data-stu-id="e1ed3-112">To create the custom tracking participant</span></span>  
  
1. <span data-ttu-id="e1ed3-113">Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans **Explorateur de solutions** , puis choisissez **Ajouter**, **classe**.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-113">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Add**, **Class**.</span></span> <span data-ttu-id="e1ed3-114">Tapez `StatusTrackingParticipant` dans la zone **nom** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-114">Type `StatusTrackingParticipant` into the **Name** box, and click **Add**.</span></span>  
  
2. <span data-ttu-id="e1ed3-115">Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="e1ed3-115">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    Imports System.IO  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    using System.IO;  
    ```  
  
3. <span data-ttu-id="e1ed3-116">Modifiez la classe `StatusTrackingParticipant` afin qu'elle hérite de `TrackingParticipant`.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-116">Modify the `StatusTrackingParticipant` class so that it inherits from `TrackingParticipant`.</span></span>  
  
    ```vb  
    Public Class StatusTrackingParticipant  
        Inherits TrackingParticipant  
  
    End Class  
    ```  
  
    ```csharp  
    class StatusTrackingParticipant : TrackingParticipant  
    {  
    }  
    ```  
  
4. <span data-ttu-id="e1ed3-117">Ajoutez la substitution de méthode `Track` suivante.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-117">Add the following `Track` method override.</span></span> <span data-ttu-id="e1ed3-118">Il existe plusieurs types différents d'enregistrements de suivi.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-118">There are several different types of tracking records.</span></span> <span data-ttu-id="e1ed3-119">Nous sommes intéressés par la sortie des activités `WriteLine`, qui sont contenues dans les enregistrements de suivi d'activité.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-119">We are interested in the output of `WriteLine` activities, which are contained in activity tracking records.</span></span> <span data-ttu-id="e1ed3-120">Si `TrackingRecord` est un `ActivityTrackingRecord` d'une activité `WriteLine`, la propriété `Text` de l'activité `WriteLine` est ajoutée à un fichier nommé après le `InstanceId` du workflow.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-120">If the `TrackingRecord` is an `ActivityTrackingRecord` for a `WriteLine` activity, the `Text` of the `WriteLine` is appended to a file named after the `InstanceId` of the workflow.</span></span> <span data-ttu-id="e1ed3-121">Dans ce didacticiel, le fichier est enregistré dans le dossier actif de l’application hôte.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-121">In this tutorial, the file is saved to the current folder of the host application.</span></span>  
  
    ```vb  
    Protected Overrides Sub Track(record As TrackingRecord, timeout As TimeSpan)  
        Dim asr As ActivityStateRecord = TryCast(record, ActivityStateRecord)  
  
        If Not asr Is Nothing Then  
            If asr.State = ActivityStates.Executing And _  
            asr.Activity.TypeName = "System.Activities.Statements.WriteLine" Then  
  
                'Append the WriteLine output to the tracking  
                'file for this instance.  
                Using writer As StreamWriter = File.AppendText(record.InstanceId.ToString())  
                    writer.WriteLine(asr.Arguments("Text"))  
                    writer.Close()  
                End Using  
            End If  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        ActivityStateRecord asr = record as ActivityStateRecord;  
  
        if (asr != null)  
        {  
            if (asr.State == ActivityStates.Executing &&  
                asr.Activity.TypeName == "System.Activities.Statements.WriteLine")  
            {  
                // Append the WriteLine output to the tracking  
                // file for this instance  
                using (StreamWriter writer = File.AppendText(record.InstanceId.ToString()))  
                {  
                    writer.WriteLine(asr.Arguments["Text"]);  
                    writer.Close();  
                }  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="e1ed3-122">Si aucun modèle de suivi n'est spécifié, le modèle de suivi par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-122">When no tracking profile is specified, the default tracking profile is used.</span></span> <span data-ttu-id="e1ed3-123">Lorsque le modèle de suivi par défaut est utilisé, les enregistrements de suivi sont émis pour tous les `ActivityStates`.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-123">When the default tracking profile is used, tracking records are emitted for all `ActivityStates`.</span></span> <span data-ttu-id="e1ed3-124">Étant donné que nous devons uniquement capturer le texte une seule fois pendant le cycle de vie de l'activité `WriteLine`, nous extrayons uniquement le texte de l'état `ActivityStates.Executing`.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-124">Because we only need to capture the text one time during the lifecycle of the `WriteLine` activity, we only extract the text from the `ActivityStates.Executing` state.</span></span> <span data-ttu-id="e1ed3-125">Dans [pour créer le modèle de suivi et inscrire le participant de suivi](#to-create-the-tracking-profile-and-register-the-tracking-participant), un modèle de suivi est créé, qui spécifie que seuls les `WriteLine` `ActivityStates.Executing` enregistrements de suivi sont émis.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-125">In [To create the tracking profile and register the tracking participant](#to-create-the-tracking-profile-and-register-the-tracking-participant), a tracking profile is created that specifies that only `WriteLine` `ActivityStates.Executing` tracking records are emitted.</span></span>  
  
## <a name="to-create-the-tracking-profile-and-register-the-tracking-participant"></a><span data-ttu-id="e1ed3-126">Pour créer le modèle de suivi et inscrire le participant de suivi</span><span class="sxs-lookup"><span data-stu-id="e1ed3-126">To create the tracking profile and register the tracking participant</span></span>  
  
1. <span data-ttu-id="e1ed3-127">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur **WorkflowHostForm** , puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-127">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="e1ed3-128">Ajoutez l'instruction `using` (ou `Imports`) suivante au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="e1ed3-128">Add the following `using` (or `Imports`) statement at the top of the file with the other `using` (or `Imports`) statements.</span></span>  
  
    ```vb  
    Imports System.Activities.Tracking  
    ```  
  
    ```csharp  
    using System.Activities.Tracking;  
    ```  
  
3. <span data-ttu-id="e1ed3-129">Ajoutez le code suivant à `ConfigureWorkflowApplication` juste après le code qui ajoute `StringWriter` aux extensions de workflow et avant les gestionnaires de cycle de vie de workflow.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-129">Add the following code to `ConfigureWorkflowApplication` just after the code that adds the `StringWriter` to the workflow extensions and before the workflow lifecycle handlers.</span></span>  
  
    ```vb  
    'Add the custom tracking participant with a tracking profile  
    'that only emits tracking records for WriteLine activities.  
    Dim query As New ActivityStateQuery()  
    query.ActivityName = "WriteLine"  
    query.States.Add(ActivityStates.Executing)  
    query.Arguments.Add("Text")  
  
    Dim profile As New TrackingProfile()  
    profile.Queries.Add(query)  
  
    Dim stp As New StatusTrackingParticipant()  
    stp.TrackingProfile = profile  
  
    wfApp.Extensions.Add(stp)  
    ```  
  
    ```csharp  
    // Add the custom tracking participant with a tracking profile  
    // that only emits tracking records for WriteLine activities.  
    StatusTrackingParticipant stp = new StatusTrackingParticipant  
    {  
        TrackingProfile = new TrackingProfile  
        {  
            Queries =
            {  
                new ActivityStateQuery  
                {  
                    ActivityName = "WriteLine",  
                    States = { ActivityStates.Executing },  
                    Arguments = { "Text" }  
                }  
            }  
        }  
    };  
  
    wfApp.Extensions.Add(stp);  
    ```  
  
     <span data-ttu-id="e1ed3-130">Ce modèle de suivi spécifie que seuls les enregistrements d'état d'activité des activités `WriteLine` dans l'état `Executing` sont émis au participant de suivi personnalisé.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-130">This tracking profile specifies that only activity state records for `WriteLine` activities in the `Executing` state are emitted to the custom tracking participant.</span></span>  
  
     <span data-ttu-id="e1ed3-131">Après avoir ajouté le code, le début de `ConfigureWorkflowApplication` sera semblable à l'exemple ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-131">After adding the code, the start of `ConfigureWorkflowApplication` will look like the following example.</span></span>  
  
    ```vb  
    Private Sub ConfigureWorkflowApplication(wfApp As WorkflowApplication)  
        'Configure the persistence store.  
        wfApp.InstanceStore = store  
  
        'Add a StringWriter to the extensions. This captures the output  
        'from the WriteLine activities so we can display it in the form.  
        Dim sw As New StringWriter()  
        wfApp.Extensions.Add(sw)  
  
        'Add the custom tracking participant with a tracking profile  
        'that only emits tracking records for WriteLine activities.  
        Dim query As New ActivityStateQuery()  
        query.ActivityName = "WriteLine"  
        query.States.Add(ActivityStates.Executing)  
        query.Arguments.Add("Text")  
  
        Dim profile As New TrackingProfile()  
        profile.Queries.Add(query)  
  
        Dim stp As New StatusTrackingParticipant()  
        stp.TrackingProfile = profile  
  
        wfApp.Extensions.Add(stp)  
  
        'Workflow lifecycle handlers...  
    ```  
  
    ```csharp  
    private void ConfigureWorkflowApplication(WorkflowApplication wfApp)  
    {  
        // Configure the persistence store.  
        wfApp.InstanceStore = store;  
  
        // Add a StringWriter to the extensions. This captures the output  
        // from the WriteLine activities so we can display it in the form.  
        StringWriter sw = new StringWriter();  
        wfApp.Extensions.Add(sw);  
  
        // Add the custom tracking participant with a tracking profile  
        // that only emits tracking records for WriteLine activities.  
        StatusTrackingParticipant stp = new StatusTrackingParticipant  
        {  
            TrackingProfile = new TrackingProfile  
            {  
                Queries =
                {  
                    new ActivityStateQuery  
                    {  
                        ActivityName = "WriteLine",  
                        States = { ActivityStates.Executing },  
                        Arguments = { "Text" }  
                    }  
                }  
            }  
        };  
  
        wfApp.Extensions.Add(stp);  
  
        // Workflow lifecycle handlers...  
    ```  
  
## <a name="to-display-the-tracking-information"></a><span data-ttu-id="e1ed3-132">Pour afficher les informations de suivi</span><span class="sxs-lookup"><span data-stu-id="e1ed3-132">To display the tracking information</span></span>  
  
1. <span data-ttu-id="e1ed3-133">Dans **Explorateur de solutions** , cliquez avec le bouton droit sur **WorkflowHostForm** , puis choisissez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-133">Right-click **WorkflowHostForm** in **Solution Explorer** and choose **View Code**.</span></span>  
  
2. <span data-ttu-id="e1ed3-134">Dans le gestionnaire `InstanceId_SelectedIndexChanged`, ajoutez le code suivant immédiatement après le code qui supprime la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-134">In the `InstanceId_SelectedIndexChanged` handler, add the following code immediately after the code that clears the status window.</span></span>  
  
    ```vb  
    'If there is tracking data for this workflow, display it  
    'in the status window.  
    If File.Exists(WorkflowInstanceId.ToString()) Then  
        Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
        UpdateStatus(status)  
    End If  
    ```  
  
    ```csharp  
    // If there is tracking data for this workflow, display it  
    // in the status window.  
    if (File.Exists(WorkflowInstanceId.ToString()))  
    {  
        string status = File.ReadAllText(WorkflowInstanceId.ToString());  
        UpdateStatus(status);  
    }  
    ```  
  
     <span data-ttu-id="e1ed3-135">Lorsqu'un nouveau workflow est sélectionné dans la liste de workflow, les enregistrements de suivi pour ce workflow sont chargés et affichés dans la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-135">When a new workflow is selected in the workflow list, the tracking records for that workflow are loaded and displayed in the status window.</span></span> <span data-ttu-id="e1ed3-136">Cet exemple est le gestionnaire `InstanceId_SelectedIndexChanged` terminé.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-136">The following example is the completed `InstanceId_SelectedIndexChanged` handler.</span></span>  
  
    ```vb  
    Private Sub InstanceId_SelectedIndexChanged(sender As Object, e As EventArgs) Handles InstanceId.SelectedIndexChanged  
        If InstanceId.SelectedIndex = -1 Then  
            Return  
        End If  
  
        'Clear the status window.  
        WorkflowStatus.Clear()  
  
        'If there is tracking data for this workflow, display it  
        'in the status window.  
        If File.Exists(WorkflowInstanceId.ToString()) Then  
            Dim status As String = File.ReadAllText(WorkflowInstanceId.ToString())  
            UpdateStatus(status)  
        End If  
  
        'Get the workflow version and display it.  
        'If the workflow is just starting then this info will not  
        'be available in the persistence store so do not try and retrieve it.  
        If Not WorkflowStarting Then  
            Dim instance As WorkflowApplicationInstance = _  
                WorkflowApplication.GetInstance(WorkflowInstanceId, store)  
  
            WorkflowVersion.Text = _  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity)  
  
            'Unload the instance.  
            instance.Abandon()  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void InstanceId_SelectedIndexChanged(object sender, EventArgs e)  
    {  
        if (InstanceId.SelectedIndex == -1)  
        {  
            return;  
        }  
  
        // Clear the status window.  
        WorkflowStatus.Clear();  
  
        // If there is tracking data for this workflow, display it  
        // in the status window.  
        if (File.Exists(WorkflowInstanceId.ToString()))  
        {  
            string status = File.ReadAllText(WorkflowInstanceId.ToString());  
            UpdateStatus(status);  
        }  
  
        // Get the workflow version and display it.  
        // If the workflow is just starting then this info will not  
        // be available in the persistence store so do not try and retrieve it.  
        if (!WorkflowStarting)  
        {  
            WorkflowApplicationInstance instance =  
                WorkflowApplication.GetInstance(this.WorkflowInstanceId, store);  
  
            WorkflowVersion.Text =  
                WorkflowVersionMap.GetIdentityDescription(instance.DefinitionIdentity);  
  
            // Unload the instance.  
            instance.Abandon();  
        }  
    }  
    ```  
  
## <a name="to-build-and-run-the-application"></a><span data-ttu-id="e1ed3-137">Pour générer et exécuter l'application</span><span class="sxs-lookup"><span data-stu-id="e1ed3-137">To build and run the application</span></span>  
  
1. <span data-ttu-id="e1ed3-138">Appuyez sur Ctrl+Maj+B pour générer l'application.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-138">Press Ctrl+Shift+B to build the application.</span></span>  
  
2. <span data-ttu-id="e1ed3-139">Appuyez sur Ctrl+F5 pour démarrer l'application.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-139">Press Ctrl+F5 to start the application.</span></span>  
  
3. <span data-ttu-id="e1ed3-140">Sélectionnez une plage pour le jeu d’estimation et le type de flux de travail à démarrer, puis cliquez sur **nouveau jeu**.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-140">Select a range for the guessing game and the type of workflow to start, and click **New Game**.</span></span> <span data-ttu-id="e1ed3-141">Entrez une estimation dans la zone **deviner** , puis cliquez sur **OK** pour envoyer votre estimation.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-141">Enter a guess in the **Guess** box and click **Go** to submit your guess.</span></span> <span data-ttu-id="e1ed3-142">Notez que l'état du workflow est affiché dans la fenêtre d'état.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-142">Note that the status of the workflow is displayed in the status window.</span></span> <span data-ttu-id="e1ed3-143">Cette sortie est capturée à partir des activités `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-143">This output is captured from the `WriteLine` activities.</span></span> <span data-ttu-id="e1ed3-144">Basculez vers un autre workflow en le sélectionnant dans la zone de liste déroulante **ID d’instance de workflow** et notez que l’état du flux de travail actuel est supprimé.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-144">Switch to a different workflow by selecting one from the **Workflow Instance Id** combo box and note that the status of the current workflow is removed.</span></span> <span data-ttu-id="e1ed3-145">Revenez au workflow précédent et notez que le mode est restauré, semblable à l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-145">Switch back to the previous workflow and note that the status is restored, similar to the following example.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e1ed3-146">Si vous basculez vers un workflow démarré avant activation du suivi, aucun état ne s'affiche.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-146">If you switch to a workflow that was started before tracking was enabled no status is displayed.</span></span> <span data-ttu-id="e1ed3-147">Mais si vous effectuez des propositions supplémentaires, leur état est enregistré, car le suivi est maintenant activé.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-147">However if you make additional guesses, their status is saved because tracking is now enabled.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    > [!NOTE]
    > <span data-ttu-id="e1ed3-148">Ces informations sont utiles pour déterminer la plage de nombres aléatoires, mais elles ne contiennent aucune information sur les propositions précédemment effectuées.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-148">This information is useful for determining the range of the random number, but it does not contain any information about what guesses have been previously made.</span></span> <span data-ttu-id="e1ed3-149">Ces informations se trouvent à l’étape suivante, [Comment : héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="e1ed3-149">This information is in the next step, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    <span data-ttu-id="e1ed3-150">Notez l'ID d'instance de workflow, et exécutez le jeu jusqu'à son achèvement.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-150">Make a note of the workflow instance id, and play the game through to its completion.</span></span>
  
4. <span data-ttu-id="e1ed3-151">Ouvrez l’Explorateur Windows et accédez au dossier **NumberGuessWorkflowHost\bin\debug** (ou **bin\Release** selon les paramètres de votre projet).</span><span class="sxs-lookup"><span data-stu-id="e1ed3-151">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings).</span></span> <span data-ttu-id="e1ed3-152">Notez qu'en plus des fichiers exécutables du projet, il existe des fichiers avec les noms de fichiers GUID.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-152">Note that in addition to the project executable files there are files with guid filenames.</span></span> <span data-ttu-id="e1ed3-153">Identifiez celui qui correspond à l'identificateur d'instance du workflow effectué à l'étape précédente et ouvrez-le dans le Bloc-notes.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-153">Identify the one that corresponds to the workflow instance id from the completed workflow in the previous step and open it in Notepad.</span></span> <span data-ttu-id="e1ed3-154">Les informations de suivi contiennent des informations semblables à celles qui suivent.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-154">The tracking information contains information similar to the following.</span></span>  
  
    ```output
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    Your guess is too high.
    Please enter a number between 1 and 10
    ```

    <span data-ttu-id="e1ed3-155">Outre l'absence de propositions de l'utilisateur, les données de suivi ne contiennent pas d'informations sur la proposition finale du workflow.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-155">In addition to the absence of the user's guesses, this tracking data does not contain information about the final guess of the workflow.</span></span> <span data-ttu-id="e1ed3-156">C'est parce que les informations de suivi contiennent uniquement la sortie `WriteLine` du workflow, et le dernier message qui s'affiche est généré à partir du gestionnaire `Completed` après que le workflow est terminé.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-156">That is because the tracking information consists only of the `WriteLine` output from the workflow, and the final message that is displayed is done so from the `Completed` handler after the workflow completes.</span></span> <span data-ttu-id="e1ed3-157">Dans l’étape suivante du didacticiel, [Comment : héberger plusieurs versions d’un workflow côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), les `WriteLine` activités existantes sont modifiées pour afficher les hypothèses de l’utilisateur, et une activité supplémentaire `WriteLine` qui affiche les résultats finaux est ajoutée.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-157">In next step of the tutorial, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), the existing `WriteLine` activities are modified to display the user's guesses, and an additional `WriteLine` activity is added that displays the final results.</span></span> <span data-ttu-id="e1ed3-158">Une fois ces modifications intégrées, [l’hébergement de plusieurs versions d’un workflow côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) montre comment héberger plusieurs versions d’un workflow en même temps.</span><span class="sxs-lookup"><span data-stu-id="e1ed3-158">After these changes are integrated, [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) demonstrates how to host multiple versions of a workflow at the same time.</span></span>
