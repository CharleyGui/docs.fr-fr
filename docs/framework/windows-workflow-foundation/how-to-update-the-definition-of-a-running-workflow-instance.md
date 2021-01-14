---
title: 'Procédure : mettre à jour la définition d’une instance de workflow en cours d’exécution'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 26dfac36-ae23-4909-9867-62495b55fb5e
ms.openlocfilehash: b94c7564b1ce87695f82f28eb6daf7686203b41f
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190427"
---
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a><span data-ttu-id="9b2e5-102">Procédure : mettre à jour la définition d’une instance de workflow en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="9b2e5-102">How to: Update the Definition of a Running Workflow Instance</span></span>

<span data-ttu-id="9b2e5-103">La mise à jour dynamique fournit un mécanisme pour permettre aux développeurs d'applications de workflow de mettre à jour la définition de workflow d'une instance de workflow persistante.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-103">Dynamic update provides a mechanism for workflow application developers to update the workflow definition of a persisted workflow instance.</span></span> <span data-ttu-id="9b2e5-104">Il peut s’agit de l’implémentation d’une résolution de bogue, de nouvelles exigences ou de l’adaptation à des modifications inattendues.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-104">The required change can be to implement a bug fix, new requirements, or to accommodate unexpected changes.</span></span> <span data-ttu-id="9b2e5-105">Cette étape du didacticiel montre comment utiliser la mise à jour dynamique pour modifier des instances persistantes du flux de travail de recherche de `v1` nombres afin qu’elles correspondent aux nouvelles fonctionnalités introduites dans Guide pratique [pour héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-105">This step in the tutorial demonstrates how to use dynamic update to modify  persisted instances of the `v1` number guessing workflow to match the new functionality introduced in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

## <a name="in-this-topic"></a><span data-ttu-id="9b2e5-106">Dans cette rubrique</span><span class="sxs-lookup"><span data-stu-id="9b2e5-106">In this topic</span></span>

- [<span data-ttu-id="9b2e5-107">Pour créer le projet CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="9b2e5-107">To create the CreateUpdateMaps project</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [<span data-ttu-id="9b2e5-108">Pour mettre à jour StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="9b2e5-108">To update StateMachineNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [<span data-ttu-id="9b2e5-109">Pour mettre à jour FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="9b2e5-109">To update FlowchartNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [<span data-ttu-id="9b2e5-110">Pour mettre à jour SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="9b2e5-110">To update SequentialNumberGuessWorkflow</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [<span data-ttu-id="9b2e5-111">Pour générer et exécuter l'application CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="9b2e5-111">To build and run the CreateUpdateMaps application</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [<span data-ttu-id="9b2e5-112">Pour générer l'assembly de workflow mis à jour</span><span class="sxs-lookup"><span data-stu-id="9b2e5-112">To build the updated workflow assembly</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [<span data-ttu-id="9b2e5-113">Pour mettre à jour WorkflowVersionMap avec les nouvelles versions</span><span class="sxs-lookup"><span data-stu-id="9b2e5-113">To update WorkflowVersionMap with the new versions</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [<span data-ttu-id="9b2e5-114">Pour appliquer des mises à jour dynamiques</span><span class="sxs-lookup"><span data-stu-id="9b2e5-114">To apply the dynamic updates</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [<span data-ttu-id="9b2e5-115">Pour exécuter l'application avec les workflows mis à jour</span><span class="sxs-lookup"><span data-stu-id="9b2e5-115">To run the application with the updated workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [<span data-ttu-id="9b2e5-116">Pour activer le démarrage des versions antérieures des workflows</span><span class="sxs-lookup"><span data-stu-id="9b2e5-116">To enable starting previous versions of the workflows</span></span>](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="to-create-the-createupdatemaps-project"></a><a name="BKMK_CreateProject"></a> <span data-ttu-id="9b2e5-117">Pour créer le projet CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="9b2e5-117">To create the CreateUpdateMaps project</span></span>

1. <span data-ttu-id="9b2e5-118">Cliquez avec le bouton droit sur **WF45GettingStartedTutorial** dans **Explorateur de solutions** , puis choisissez **Ajouter**, **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-118">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="9b2e5-119">Dans le nœud **installé** , sélectionnez **Visual C#**, **Windows** (ou **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-119">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="9b2e5-120">Selon le langage de programmation configuré comme langage principal dans Visual Studio, le nœud **Visual C#** ou **Visual Basic** peut se trouver sous le nœud **Autres langages** dans le nœud **Installé**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-120">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

     <span data-ttu-id="9b2e5-121">Assurez-vous que **.NET Framework 4.5** est sélectionné dans la liste déroulante de la version .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-121">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="9b2e5-122">Sélectionnez **application console** dans la liste **Windows** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-122">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="9b2e5-123">Tapez **CreateUpdateMaps** dans la zone **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-123">Type **CreateUpdateMaps** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="9b2e5-124">Cliquez avec le bouton droit sur **CreateUpdateMaps** dans **Explorateur de solutions** , puis choisissez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-124">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="9b2e5-125">Sélectionnez **Framework** dans le nœud **assemblys** de la liste **Ajouter une référence** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-125">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="9b2e5-126">Tapez **System. Activities** dans la zone Rechercher dans les **assemblys** pour filtrer les assemblys et faciliter la sélection des références souhaitées.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-126">Type **System.Activities** into the **Search Assemblies** box to filter the assemblies and make the desired references easier to select.</span></span>

5. <span data-ttu-id="9b2e5-127">Activez la case à cocher en regard de **System. Activities** dans la liste des **résultats de recherche** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-127">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

6. <span data-ttu-id="9b2e5-128">Tapez **Serialization** dans la zone **Rechercher** dans les assemblys, puis activez la case à cocher en regard de **System. Runtime. Serialization** dans la liste des résultats de la **recherche** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-128">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

7. <span data-ttu-id="9b2e5-129">Tapez **System. Xaml** dans la zone Rechercher dans les **assemblys** , puis activez la case à cocher en regard de **System. Xaml** dans la liste des résultats de la **recherche** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-129">Type **System.Xaml** into the **Search Assemblies** box, and check the checkbox beside **System.Xaml** from the **Search Results** list.</span></span>

8. <span data-ttu-id="9b2e5-130">Cliquez sur **OK** pour fermer le **Gestionnaire** de références et ajouter les références.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-130">Click **OK** to close **Reference Manager** and add the references.</span></span>

9. <span data-ttu-id="9b2e5-131">Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-131">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.Statements
    Imports System.Xaml
    Imports System.Reflection
    Imports System.IO
    Imports System.Activities.XamlIntegration
    Imports System.Activities.DynamicUpdate
    Imports System.Runtime.Serialization
    Imports Microsoft.VisualBasic.Activities
    ```

    ```csharp
    using System.Activities;
    using System.Activities.Statements;
    using System.IO;
    using System.Xaml;
    using System.Reflection;
    using System.Activities.XamlIntegration;
    using System.Activities.DynamicUpdate;
    using System.Runtime.Serialization;
    using Microsoft.CSharp.Activities;
    ```

10. <span data-ttu-id="9b2e5-132">Ajoutez les deux membres de chaîne suivants à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-132">Add the following two string members to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. <span data-ttu-id="9b2e5-133">Ajoutez la méthode `StartUpdate` suivante à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-133">Add the following `StartUpdate` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="9b2e5-134">Cette méthode charge la définition spécifiée de workflow XAML dans `ActivityBuilder`, puis appelle `DynamicUpdate.PrepareForUpdate`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-134">This method loads up the specified xaml workflow definition into an `ActivityBuilder`, and then calls `DynamicUpdate.PrepareForUpdate`.</span></span> <span data-ttu-id="9b2e5-135">`PrepareForUpdate` effectue une copie de la définition de workflow à l'intérieur de `ActivityBuilder`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-135">`PrepareForUpdate` makes a copy of the workflow definition inside the `ActivityBuilder`.</span></span> <span data-ttu-id="9b2e5-136">Une fois la définition de workflow modifiée, cette copie est utilisée parallèlement à la définition modifiée de workflow pour créer la mise à jour de la carte.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-136">After the workflow definition is modified, this copy is used along with the modified workflow definition to create the update map.</span></span>

    ```vb
    Private Function StartUpdate(name As String) As ActivityBuilder
        'Create the XamlXmlReaderSettings.
        Dim readerSettings As XamlReaderSettings = New XamlXmlReaderSettings()
        'In the XAML the "local" namespace refers to artifacts that come from
        'the same project as the XAML. When loading XAML if the currently executing
        'assembly is not the same assembly that was referred to as "local" in the XAML
        'LocalAssembly must be set to the assembly containing the artifacts.
        'Assembly.LoadFile requires an absolute path so convert this relative path
        'to an absolute path.
        readerSettings.LocalAssembly = Assembly.LoadFile(
            Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))

        Dim fullPath As String = Path.Combine(definitionPath, name)
        Dim xamlReader As XamlXmlReader = New XamlXmlReader(fullPath, readerSettings)

        'Load the workflow definition into an ActivityBuilder.
        Dim wf As ActivityBuilder = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))

        'PrepareForUpdate makes a copy of the workflow definition in the
        'ActivityBuilder that is used for comparison when the update
        'map is created.
        DynamicUpdateServices.PrepareForUpdate(wf)

        Return wf
    End Function
    ```

    ```csharp
    private static ActivityBuilder StartUpdate(string name)
    {
        // Create the XamlXmlReaderSettings.
        XamlXmlReaderSettings readerSettings = new XamlXmlReaderSettings()
        {
            // In the XAML the "local" namespace refers to artifacts that come from
            // the same project as the XAML. When loading XAML if the currently executing
            // assembly is not the same assembly that was referred to as "local" in the XAML
            // LocalAssembly must be set to the assembly containing the artifacts.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            LocalAssembly = Assembly.LoadFile(
                Path.GetFullPath(Path.Combine(mapPath, "NumberGuessWorkflowActivities_v1.dll")))
        };

        string path = Path.Combine(definitionPath, name);
        XamlXmlReader xamlReader = new XamlXmlReader(path, readerSettings);

        // Load the workflow definition into an ActivityBuilder.
        ActivityBuilder wf = XamlServices.Load(
            ActivityXamlServices.CreateBuilderReader(xamlReader))
            as ActivityBuilder;

        // PrepareForUpdate makes a copy of the workflow definition in the
        // ActivityBuilder that is used for comparison when the update
        // map is created.
        DynamicUpdateServices.PrepareForUpdate(wf);

        return wf;
    }
    ```

12. <span data-ttu-id="9b2e5-137">Ensuite, ajoutez la méthode `CreateUpdateMethod` à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-137">Next, add the following `CreateUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="9b2e5-138">Cela crée une carte de mise à jour dynamique en appelant DynamicUpdateServices.CreateUpdateMap, puis enregistre la carte de mise à jour à l'aide du nom spécifié.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-138">This creates a dynamic update map by calling DynamicUpdateServices.CreateUpdateMap, and then saves the update map using the specified name.</span></span> <span data-ttu-id="9b2e5-139">Cette carte de mise à jour contient les informations nécessaires à l'exécution du workflow pour mettre à jour une instance persistante de workflow démarrée en utilisant la définition d'origine de workflow contenue dans `ActivityBuilder` afin qu'il se termine en utilisant la définition mise à jour de workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-139">This update map contains the information needed by the workflow runtime to update a persisted workflow instance that was started using the original workflow definition contained in the `ActivityBuilder` so that it completes using the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateUpdateMaps(wf As ActivityBuilder, name As String)
        'Create the UpdateMap.
        Dim map As DynamicUpdateMap =
            DynamicUpdateServices.CreateUpdateMap(wf)

        'Serialize it to a file.
        Dim mapFullPath As String = Path.Combine(mapPath, name)
        Dim sz As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
        Using fs As FileStream = File.Open(mapFullPath, FileMode.Create)
            sz.WriteObject(fs, map)
        End Using
    End Sub
    ```

    ```csharp
    private static void CreateUpdateMaps(ActivityBuilder wf, string name)
    {
        // Create the UpdateMap.
        DynamicUpdateMap map =
            DynamicUpdateServices.CreateUpdateMap(wf);

        // Serialize it to a file.
        string path = Path.Combine(mapPath, name);
        DataContractSerializer sz = new DataContractSerializer(typeof(DynamicUpdateMap));
        using (FileStream fs = System.IO.File.Open(path, FileMode.Create))
        {
            sz.WriteObject(fs, map);
        }
    }
    ```

13. <span data-ttu-id="9b2e5-140">Ajoutez la méthode `SaveUpdatedDefinition` suivante à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-140">Add the following `SaveUpdatedDefinition` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="9b2e5-141">Cette méthode enregistre la définition mise à jour de workflow une fois la carte de mise à jour créée.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-141">This method saves the updated workflow definition once the update map is created.</span></span>

    ```vb
    Private Sub SaveUpdatedDefinition(wf As ActivityBuilder, name As String)
        Dim xamlPath As String = Path.Combine(definitionPath, name)
        Dim sw As StreamWriter = File.CreateText(xamlPath)
        Dim xw As XamlWriter = ActivityXamlServices.CreateBuilderWriter(
            New XamlXmlWriter(sw, New XamlSchemaContext()))
        XamlServices.Save(xw, wf)
        sw.Close()
    End Sub
    ```

    ```csharp
    private static void SaveUpdatedDefinition(ActivityBuilder wf, string name)
    {
        string xamlPath = Path.Combine(definitionPath, name);
        StreamWriter sw = File.CreateText(xamlPath);
        XamlWriter xw = ActivityXamlServices.CreateBuilderWriter(
            new XamlXmlWriter(sw, new XamlSchemaContext()));
        XamlServices.Save(xw, wf);
        sw.Close();
    }
    ```

### <a name="to-update-statemachinenumberguessworkflow"></a><a name="BKMK_StateMachine"></a> <span data-ttu-id="9b2e5-142">Pour mettre à jour StateMachineNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="9b2e5-142">To update StateMachineNumberGuessWorkflow</span></span>

1. <span data-ttu-id="9b2e5-143">Ajoutez une méthode `CreateStateMachineUpdateMap` à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-143">Add a `CreateStateMachineUpdateMap` to the `Program` class (or `Module1`).</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. <span data-ttu-id="9b2e5-144">Effectuez un appel à `StartUpdate`, puis obtenez une référence à l'activité `StateMachine` racine du workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-144">Make a call to `StartUpdate` and then get a reference to the root `StateMachine` activity of the workflow.</span></span>

    ```vb
    Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

    'Get a reference to the root StateMachine activity.
    Dim sm As StateMachine = wf.Implementation
    ```

    ```csharp
    ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

    // Get a reference to the root StateMachine activity.
    StateMachine sm = wf.Implementation as StateMachine;
    ```

3. <span data-ttu-id="9b2e5-145">Ensuite, mettez à jour les expressions des deux `WriteLine` activités qui indiquent si l’estimation de l’utilisateur est trop élevée ou trop faible afin qu’elles correspondent aux mises à jour apportées dans [Comment : héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-145">Next, update the expressions of the two `WriteLine` activities that display whether the user's guess is too high or too low so that they match the updates made in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

    ```vb
    'Update the Text of the two WriteLine activities that write the
    'results of the user's guess. They are contained in the workflow as the
    'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

    'Update the "too low" message.
    Dim tooLow As WriteLine = guessLow.Then
    tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

    'Update the "too high" message.
    Dim tooHigh As WriteLine = guessLow.Else
    tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")
    ```

    ```csharp
    // Update the Text of the two WriteLine activities that write the
    // results of the user's guess. They are contained in the workflow as the
    // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
    If guessLow = sm.States[1].Transitions[1].Action as If;

    // Update the "too low" message.
    WriteLine tooLow = guessLow.Then as WriteLine;
    tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

    // Update the "too high" message.
    WriteLine tooHigh = guessLow.Else as WriteLine;
    tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");
    ```

4. <span data-ttu-id="9b2e5-146">Ensuite, ajoutez la nouvelle activité `WriteLine` qui affiche le message de fermeture.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-146">Next, add the new `WriteLine` activity that displays the closing message.</span></span>

    ```vb
    'Create the new WriteLine that displays the closing message.
    Dim wl As New WriteLine() With
    {
        .Text = New VisualBasicValue(Of String) _
            ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
    }

    'Add it as the Action for the Guess Correct transition. The Guess Correct
    'transition is the first transition of States[1]. The transitions are listed
    'at the bottom of the State activity designer.
    sm.States(1).Transitions(0).Action = wl
    ```

    ```csharp
    // Create the new WriteLine that displays the closing message.
    WriteLine wl = new WriteLine
    {
        Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
    };

    // Add it as the Action for the Guess Correct transition. The Guess Correct
    // transition is the first transition of States[1]. The transitions are listed
    // at the bottom of the State activity designer.
    sm.States[1].Transitions[0].Action = wl;
    ```

5. <span data-ttu-id="9b2e5-147">Une fois que le workflow a été mis à jour, appelez `CreateUpdateMaps` et `SaveUpdatedDefinition`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-147">After the workflow is updated, call `CreateUpdateMaps` and `SaveUpdatedDefinition`.</span></span> <span data-ttu-id="9b2e5-148">`CreateUpdateMaps` crée et enregistre `DynamicUpdateMap`, et `SaveUpdatedDefinition` enregistre la définition mise à jour de workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-148">`CreateUpdateMaps` creates and saves the `DynamicUpdateMap`, and `SaveUpdatedDefinition` saves the updated workflow definition.</span></span>

    ```vb
    'Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

    'Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    ```

    ```csharp
    // Create the update map.
    CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

    // Save the updated workflow definition.
    SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    ```

    <span data-ttu-id="9b2e5-149">L'exemple suivant illustre la méthode `CreateStateMachineUpdateMap` complète.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-149">The following example is the completed `CreateStateMachineUpdateMap` method.</span></span>

    ```vb
    Private Sub CreateStateMachineUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("StateMachineNumberGuessWorkflow.xaml")

        'Get a reference to the root StateMachine activity.
        Dim sm As StateMachine = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        Dim guessLow As Statements.If = sm.States(1).Transitions(1).Action

        'Update the "too low" message.
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Add it as the Action for the Guess Correct transition. The Guess Correct
        'transition is the first transition of States[1]. The transitions are listed
        'at the bottom of the State activity designer.
        sm.States(1).Transitions(0).Action = wl

        'Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("StateMachineNumberGuessWorkflow.xaml");

        // Get a reference to the root StateMachine activity.
        StateMachine sm = wf.Implementation as StateMachine;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the If activity in sm.States[1].Transitions[1].Action.
        If guessLow = sm.States[1].Transitions[1].Action as If;

        // Update the "too low" message.
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Create the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Add it as the Action for the Guess Correct transition. The Guess Correct
        // transition is the first transition of States[1]. The transitions are listed
        // at the bottom of the State activity designer.
        sm.States[1].Transitions[0].Action = wl;

        // Create the update map.
        CreateUpdateMaps(wf, "StateMachineNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "StateMachineNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-update-flowchartnumberguessworkflow"></a><a name="BKMK_Flowchart"></a> <span data-ttu-id="9b2e5-150">Pour mettre à jour FlowchartNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="9b2e5-150">To update FlowchartNumberGuessWorkflow</span></span>

1. <span data-ttu-id="9b2e5-151">Ajoutez la méthode `CreateFlowchartUpdateMethod` suivante à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-151">Add the following `CreateFlowchartUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="9b2e5-152">Cette méthode est semblable à `CreateStateMachineUpdateMap`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-152">This method is similar to `CreateStateMachineUpdateMap`.</span></span> <span data-ttu-id="9b2e5-153">Elle commence par un appel à `StartUpdate`, met à jour la définition de workflow de l'organigramme, et se termine en enregistrant la carte de mise à jour et la définition mise à jour de workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-153">It starts with a call to `StartUpdate`, updates the flowchart workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateFlowchartUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("FlowchartNumberGuessWorkflow.xaml")

        'Get a reference to the root Flowchart activity.
        Dim fc As Flowchart = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'True and False action of the "Guess < Target" FlowDecision, which is
        'Nodes[4].
        Dim guessLow As FlowDecision = fc.Nodes(4)

        'Update the "too low" message.
        Dim trueStep As FlowStep = guessLow.True
        Dim tooLow As WriteLine = trueStep.Action
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")

        'Update the "too high" message.
        Dim falseStep As FlowStep = guessLow.False
        Dim tooHigh As WriteLine = falseStep.Action
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Create a FlowStep to hold the WriteLine.
        Dim closingStep As New FlowStep() With
        {
            .Action = wl
        }

        'Add this new FlowStep to the True action of the
        '"Guess = Guess" FlowDecision
        Dim guessCorrect As FlowDecision = fc.Nodes(3)
        guessCorrect.True = closingStep

        'Add the new FlowStep to the Nodes collection.
        'If closingStep was replacing an existing node then
        'we would need to remove that Step from the collection.
        'In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep)

        'Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateFlowchartUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("FlowchartNumberGuessWorkflow.xaml");

        // Get a reference to the root Flowchart activity.
        Flowchart fc = wf.Implementation as Flowchart;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // True and False action of the "Guess < Target" FlowDecision, which is
        // Nodes[4].
        FlowDecision guessLow = fc.Nodes[4] as FlowDecision;

        // Update the "too low" message.
        FlowStep trueStep = guessLow.True as FlowStep;
        WriteLine tooLow = trueStep.Action as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");

        // Update the "too high" message.
        FlowStep falseStep = guessLow.False as FlowStep;
        WriteLine tooHigh = falseStep.Action as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Create a FlowStep to hold the WriteLine.
        FlowStep closingStep = new FlowStep
        {
            Action = wl
        };

        // Add this new FlowStep to the True action of the
        // "Guess == Guess" FlowDecision
        FlowDecision guessCorrect = fc.Nodes[3] as FlowDecision;
        guessCorrect.True = closingStep;

        // Add the new FlowStep to the Nodes collection.
        // If closingStep was replacing an existing node then
        // we would need to remove that Step from the collection.
        // In this example there was no existing True step to remove.
        fc.Nodes.Add(closingStep);

        // Create the update map.
        CreateUpdateMaps(wf, "FlowchartNumberGuessWorkflow.map");

        //  Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "FlowchartNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-update-sequentialnumberguessworkflow"></a><a name="BKMK_Sequential"></a> <span data-ttu-id="9b2e5-154">Pour mettre à jour SequentialNumberGuessWorkflow</span><span class="sxs-lookup"><span data-stu-id="9b2e5-154">To update SequentialNumberGuessWorkflow</span></span>

1. <span data-ttu-id="9b2e5-155">Ajoutez la méthode `CreateSequentialUpdateMethod` suivante à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-155">Add the following `CreateSequentialUpdateMethod` to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="9b2e5-156">Cette méthode est similaire aux deux autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-156">This method is similar to the other two methods.</span></span> <span data-ttu-id="9b2e5-157">Elle commence par un appel à `StartUpdate`, met à jour la définition de workflow séquentiel, et se termine en enregistrant la carte de mise à jour et la définition mise à jour de workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-157">It starts with a call to `StartUpdate`, updates the sequential workflow definition, and finishes by saving the update map and the updated workflow definition.</span></span>

    ```vb
    Private Sub CreateSequentialUpdateMap()
        Dim wf As ActivityBuilder = StartUpdate("SequentialNumberGuessWorkflow.xaml")

        'Get a reference to the root activity in the workflow.
        Dim rootSequence As Sequence = wf.Implementation

        'Update the Text of the two WriteLine activities that write the
        'results of the user's guess. They are contained in the workflow as the
        'Then and Else action of the "Guess < Target" If activity.
        'Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        Dim gameLoop As Statements.DoWhile = rootSequence.Activities(1)
        Dim gameBody As Sequence = gameLoop.Body
        Dim guessCorrect As Statements.If = gameBody.Activities(2)
        Dim guessLow As Statements.If = guessCorrect.Then
        Dim tooLow As WriteLine = guessLow.Then
        tooLow.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too low.""")
        Dim tooHigh As WriteLine = guessLow.Else
        tooHigh.Text = New VisualBasicValue(Of String)("Guess.ToString() & "" is too high.""")

        'Create the new WriteLine that displays the closing message.
        Dim wl As New WriteLine() With
        {
            .Text = New VisualBasicValue(Of String) _
                ("Guess.ToString() + "" is correct. You guessed it in "" & Turns.ToString() & "" turns.""")
        }

        'Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl)

        'Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map")

        'Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml")
    End Sub
    ```

    ```csharp
    private static void CreateSequentialUpdateMap()
    {
        ActivityBuilder wf = StartUpdate("SequentialNumberGuessWorkflow.xaml");

        // Get a reference to the root activity in the workflow.
        Sequence rootSequence = wf.Implementation as Sequence;

        // Update the Text of the two WriteLine activities that write the
        // results of the user's guess. They are contained in the workflow as the
        // Then and Else action of the "Guess < Target" If activity.
        // Sequence[1]->DoWhile->Body->Sequence[2]->If->Then->If
        DoWhile gameLoop = rootSequence.Activities[1] as DoWhile;
        Sequence gameBody = gameLoop.Body as Sequence;
        If guessCorrect = gameBody.Activities[2] as If;
        If guessLow = guessCorrect.Then as If;
        WriteLine tooLow = guessLow.Then as WriteLine;
        tooLow.Text = new CSharpValue<string>("Guess.ToString() + \" is too low.\"");
        WriteLine tooHigh = guessLow.Else as WriteLine;
        tooHigh.Text = new CSharpValue<string>("Guess.ToString() + \" is too high.\"");

        // Add the new WriteLine that displays the closing message.
        WriteLine wl = new WriteLine
        {
            Text = new CSharpValue<string>("Guess.ToString() + \" is correct. You guessed it in \" + Turns.ToString() + \" turns.\"")
        };

        // Insert it as the third activity in the root sequence
        rootSequence.Activities.Insert(2, wl);

        // Create the update map.
        CreateUpdateMaps(wf, "SequentialNumberGuessWorkflow.map");

        // Save the updated workflow definition.
        SaveUpdatedDefinition(wf, "SequentialNumberGuessWorkflow_du.xaml");
    }
    ```

### <a name="to-build-and-run-the-createupdatemaps-application"></a><a name="BKMK_CreateUpdateMaps"></a> <span data-ttu-id="9b2e5-158">Pour générer et exécuter l’application CreateUpdateMaps</span><span class="sxs-lookup"><span data-stu-id="9b2e5-158">To build and run the CreateUpdateMaps application</span></span>

1. <span data-ttu-id="9b2e5-159">Ajoutez la méthode `Main` suivante, puis les trois appels de méthodes suivants.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-159">Update the `Main` method and add the following three method calls.</span></span> <span data-ttu-id="9b2e5-160">Ces méthodes sont ajoutées dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-160">These methods are added in the following sections.</span></span> <span data-ttu-id="9b2e5-161">Chaque méthode met à jour le workflow d'estimation de nombre correspondant et crée un `DynamicUpdateMap` qui décrit les mises à jour.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-161">Each method updates the corresponding number guess workflow and creates a `DynamicUpdateMap` that describes the updates.</span></span>

    ```vb
    Sub Main()
        'Create the update maps for the changes needed to the v1 activities
        'so they match the v2 activities.
        CreateSequentialUpdateMap()
        CreateFlowchartUpdateMap()
        CreateStateMachineUpdateMap()
    End Sub
    ```

    ```csharp
    static void Main(string[] args)
    {
        // Create the update maps for the changes needed to the v1 activities
        // so they match the v2 activities.
        CreateSequentialUpdateMap();
        CreateFlowchartUpdateMap();
        CreateStateMachineUpdateMap();
    }
    ```

2. <span data-ttu-id="9b2e5-162">Cliquez avec le bouton droit sur **CreateUpdateMaps** dans **Explorateur de solutions** , puis choisissez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-162">Right-click **CreateUpdateMaps** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

3. <span data-ttu-id="9b2e5-163">Appuyez sur Ctrl+Maj+B pour générer la solution, puis appuyez sur Ctrl+F5 pour exécuter l'application `CreateUpdateMaps`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-163">Press CTRL+SHIFT+B to build the solution, and then CTRL+F5 to run the `CreateUpdateMaps` application.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9b2e5-164">L' `CreateUpdateMaps` application n’affiche pas d’informations d’État pendant l’exécution, mais si vous regardez dans le dossier **NumberGuessWorkflowActivities_du** et le dossier **PreviousVersions** , vous verrez les fichiers de définition de workflow mis à jour et les mappages de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-164">The `CreateUpdateMaps` application does not display any status information while running, but if you look in the **NumberGuessWorkflowActivities_du** folder and the **PreviousVersions** folder you will see the updated workflow definition files and the update maps.</span></span>

    <span data-ttu-id="9b2e5-165">Une fois les cartes de mise à jour créées et les définitions de workflow mises à jour, l'étape suivante consiste à générer un assembly mis à jour de workflow contenant les définitions mises à jour.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-165">Once the update maps are created and the workflow definitions updated, the next step is to build an updated workflow assembly containing the updated definitions.</span></span>

### <a name="to-build-the-updated-workflow-assembly"></a><a name="BKMK_BuildAssembly"></a> <span data-ttu-id="9b2e5-166">Pour générer l’assembly de flux de travail mis à jour</span><span class="sxs-lookup"><span data-stu-id="9b2e5-166">To build the updated workflow assembly</span></span>

1. <span data-ttu-id="9b2e5-167">Ouvrez une deuxième instance de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-167">Open a second instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="9b2e5-168">Dans le menu **fichier** , choisissez **ouvrir**, **projet/solution** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-168">Choose **Open**, **Project/Solution** from the **File** menu.</span></span>

3. <span data-ttu-id="9b2e5-169">Accédez au dossier **NumberGuessWorkflowActivities_du** que vous avez créé dans Guide pratique [pour héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), sélectionnez **NumberGuessWorkflowActivities. csproj** (ou **vbproj**), puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-169">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), select **NumberGuessWorkflowActivities.csproj** (or **vbproj**), and click **Open**.</span></span>

4. <span data-ttu-id="9b2e5-170">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **SequentialNumberGuessWorkflow. Xaml** , puis choisissez **exclure du projet**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-170">In **Solution Explorer**, right click **SequentialNumberGuessWorkflow.xaml** and choose **Exclude From Project**.</span></span> <span data-ttu-id="9b2e5-171">Effectuez la même opération pour **FlowchartNumberGuessWorkflow. Xaml** et **StateMachineNumberGuessWorkflow. Xaml**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-171">Do the same thing for **FlowchartNumberGuessWorkflow.xaml** and **StateMachineNumberGuessWorkflow.xaml**.</span></span> <span data-ttu-id="9b2e5-172">Cette étape supprime les versions antérieures des définitions de workflow du projet.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-172">This step removes the previous versions of the workflow definitions from the project.</span></span>

5. <span data-ttu-id="9b2e5-173">Choisissez **Ajouter un élément existant** dans le menu **projet** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-173">Choose **Add Existing Item** from the **Project** menu.</span></span>

6. <span data-ttu-id="9b2e5-174">Accédez au dossier **NumberGuessWorkflowActivities_du** que vous avez créé dans Guide pratique [pour héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-174">Navigate to the **NumberGuessWorkflowActivities_du** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

7. <span data-ttu-id="9b2e5-175">Choisissez **fichiers XAML ( \* . XAML ; \* . xoml)** dans la liste déroulante **types de fichiers** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-175">Choose **XAML Files (\*.xaml;\*.xoml)** from the **Files of type** drop-down list.</span></span>

8. <span data-ttu-id="9b2e5-176">Sélectionnez **SequentialNumberGuessWorkflow_du. Xaml**, **FlowchartNumberGuessWorkflow_du. Xaml** et **StateMachineNumberGuessWorkflow_du. Xaml** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-176">Select **SequentialNumberGuessWorkflow_du.xaml**, **FlowchartNumberGuessWorkflow_du.xaml**, and **StateMachineNumberGuessWorkflow_du.xaml** and click **Add**.</span></span>

    > [!NOTE]
    > <span data-ttu-id="9b2e5-177">Pour sélectionner plusieurs éléments à la fois, appuyez sur la touche Ctrl pendant que vous cliquez dessus.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-177">CTRL+Click to select multiple items at a time.</span></span>

    <span data-ttu-id="9b2e5-178">Cette étape ajoute les versions mises à jour des définitions de workflow au projet.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-178">This step adds the updated versions of the workflow definitions to the project.</span></span>

9. <span data-ttu-id="9b2e5-179">Appuyez sur CTRL+MAJ+B pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-179">Press CTRL+SHIFT+B to build the project.</span></span>

10. <span data-ttu-id="9b2e5-180">Choisissez **Fermer la solution** dans le menu **fichier** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-180">Choose **Close Solution** from the **File** menu.</span></span> <span data-ttu-id="9b2e5-181">Un fichier solution pour le projet n’est pas obligatoire. par conséquent, cliquez sur **non** pour fermer Visual Studio sans enregistrer un fichier solution.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-181">A solution file for the project is not required, so click **No** to close Visual Studio without saving a solution file.</span></span> <span data-ttu-id="9b2e5-182">Choisissez **quitter** dans le menu **fichier** pour fermer Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-182">Choose **Exit** from the **File** menu to close Visual Studio.</span></span>

11. <span data-ttu-id="9b2e5-183">Ouvrez l’Explorateur Windows et accédez au dossier **NumberGuessWorkflowActivities_du \bin\debug** (ou **bin\Release** selon les paramètres de votre projet).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-183">Open Windows Explorer and navigate to the **NumberGuessWorkflowActivities_du\bin\Debug** folder (or **bin\Release** depending on your project settings).</span></span>

12. <span data-ttu-id="9b2e5-184">Renommez **NumberGuessWorkflowActivities.dll** en **NumberGuessWorkflowActivities_v15.dll**, puis copiez-le dans le dossier **PreviousVersions** que vous avez créé dans Guide pratique [pour héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-184">Rename **NumberGuessWorkflowActivities.dll** to **NumberGuessWorkflowActivities_v15.dll**, and copy it to the **PreviousVersions** folder you created in [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).</span></span>

### <a name="to-update-workflowversionmap-with-the-new-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> <span data-ttu-id="9b2e5-185">Pour mettre à jour WorkflowVersionMap avec les nouvelles versions</span><span class="sxs-lookup"><span data-stu-id="9b2e5-185">To update WorkflowVersionMap with the new versions</span></span>

1. <span data-ttu-id="9b2e5-186">Revenez à l’instance initiale de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-186">Switch back to the initial instance of Visual Studio 2012.</span></span>

2. <span data-ttu-id="9b2e5-187">Double-cliquez sur **WorkflowVersionMap.cs** (ou **WorkflowVersionMap. vb**) sous le projet **NumberGuessWorkflowHost** pour l’ouvrir.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-187">Double-click **WorkflowVersionMap.cs** (or **WorkflowVersionMap.vb**) under the **NumberGuessWorkflowHost** project to open it.</span></span>

3. <span data-ttu-id="9b2e5-188">Ajoutez trois nouvelles identités de workflow juste au-dessous des six déclarations d'identité de workflow existantes.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-188">Add three new workflow identities just below the six existing workflow identity declarations.</span></span> <span data-ttu-id="9b2e5-189">Dans ce didacticiel, `1.5.0.0` est utilisé comme `WorkflowIdentity.Version` pour les identités de mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-189">In this tutorial, `1.5.0.0` is used as the `WorkflowIdentity.Version` for the dynamic update identities.</span></span> <span data-ttu-id="9b2e5-190">Ces nouvelles identités de workflow `v15` seront utilisées pour fournir la définition appropriée de workflow aux instances de workflow persistantes mises à jour dynamiquement.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-190">These new `v15` workflow identities will be used provide the correct workflow definition for the dynamically updated persisted workflow instances.</span></span>

    ```vb
    'Current version identities.
    Public StateMachineNumberGuessIdentity As WorkflowIdentity
    Public FlowchartNumberGuessIdentity As WorkflowIdentity
    Public SequentialNumberGuessIdentity As WorkflowIdentity

    'v1 identities.
    Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

    'v1.5 (Dynamic Update) identities.
    Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
    Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
    Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity
    ```

    ```csharp
    // Current version identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity;
    static public WorkflowIdentity FlowchartNumberGuessIdentity;
    static public WorkflowIdentity SequentialNumberGuessIdentity;

    // v1 identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

    // v1.5 (Dynamic Update) identities.
    static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
    static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
    static public WorkflowIdentity SequentialNumberGuessIdentity_v15;
    ```

4. <span data-ttu-id="9b2e5-191">À la fin du constructeur, ajoutez le code suivant.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-191">Add the following code at the end of the constructor.</span></span> <span data-ttu-id="9b2e5-192">Ce code initialise les identités de workflow de mise à jour dynamique, charge les définitions correspondantes de workflow, et les ajoute au dictionnaire de version de workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-192">This code initializes the dynamic update workflow identities, loads the corresponding workflow definitions, and adds them to the workflow version dictionary.</span></span>

    ```vb
    'Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "StateMachineNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "FlowchartNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
    {
        .Name = "SequentialNumberGuessWorkflow",
        .Version = New Version(1, 5, 0, 0)
    }

    'Add the dynamic update workflow identities to the dictionary along with
    'the corresponding workflow definitions loaded from the v15 assembly.
    'Assembly.LoadFile requires an absolute path so convert this relative path
    'to an absolute path.
    Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
    Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
    ```

    ```csharp
    // Initialize the dynamic update workflow identities.
    StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "StateMachineNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "FlowchartNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
    {
        Name = "SequentialNumberGuessWorkflow",
        Version = new Version(1, 5, 0, 0)
    };

    // Add the dynamic update workflow identities to the dictionary along with
    // the corresponding workflow definitions loaded from the v15 assembly.
    // Assembly.LoadFile requires an absolute path so convert this relative path
    // to an absolute path.
    string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
    v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
    Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

    map.Add(StateMachineNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

    map.Add(SequentialNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

    map.Add(FlowchartNumberGuessIdentity_v15,
        v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
    ```

     <span data-ttu-id="9b2e5-193">L'exemple suivant illustre la classe `WorkflowVersionMap` complète.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-193">The following example is the completed `WorkflowVersionMap` class.</span></span>

    ```vb
    Public Module WorkflowVersionMap
        Dim map As Dictionary(Of WorkflowIdentity, Activity)

        'Current version identities.
        Public StateMachineNumberGuessIdentity As WorkflowIdentity
        Public FlowchartNumberGuessIdentity As WorkflowIdentity
        Public SequentialNumberGuessIdentity As WorkflowIdentity

        'v1 identities.
        Public StateMachineNumberGuessIdentity_v1 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v1 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v1 As WorkflowIdentity

        'v1.5 (Dynamic Update) identities.
        Public StateMachineNumberGuessIdentity_v15 As WorkflowIdentity
        Public FlowchartNumberGuessIdentity_v15 As WorkflowIdentity
        Public SequentialNumberGuessIdentity_v15 As WorkflowIdentity

        Sub New()
            map = New Dictionary(Of WorkflowIdentity, Activity)

            'Add the current workflow version identities.
            StateMachineNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            SequentialNumberGuessIdentity = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(2, 0, 0, 0)
            }

            map.Add(StateMachineNumberGuessIdentity, New StateMachineNumberGuessWorkflow())
            map.Add(FlowchartNumberGuessIdentity, New FlowchartNumberGuessWorkflow())
            map.Add(SequentialNumberGuessIdentity, New SequentialNumberGuessWorkflow())

            'Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            FlowchartNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            SequentialNumberGuessIdentity_v1 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 0, 0, 0)
            }

            'Add the previous version workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v1 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v1AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll"
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath)
            Dim v1Assembly As Assembly = Assembly.LoadFile(v1AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))

            'Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "StateMachineNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            FlowchartNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "FlowchartNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            SequentialNumberGuessIdentity_v15 = New WorkflowIdentity With
            {
                .Name = "SequentialNumberGuessWorkflow",
                .Version = New Version(1, 5, 0, 0)
            }

            'Add the dynamic update workflow identities to the dictionary along with
            'the corresponding workflow definitions loaded from the v15 assembly.
            'Assembly.LoadFile requires an absolute path so convert this relative path
            'to an absolute path.
            Dim v15AssemblyPath As String = "..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll"
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath)
            Dim v15Assembly As Assembly = Assembly.LoadFile(v15AssemblyPath)

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow"))

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow"))

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow"))
        End Sub

        Public Function GetWorkflowDefinition(identity As WorkflowIdentity) As Activity
            Return map(identity)
        End Function

        Public Function GetIdentityDescription(identity As WorkflowIdentity) As String
            Return identity.ToString()
        End Function
    End Module
    ```

    ```csharp
    public static class WorkflowVersionMap
    {
        static Dictionary<WorkflowIdentity, Activity> map;

        // Current version identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity;
        static public WorkflowIdentity FlowchartNumberGuessIdentity;
        static public WorkflowIdentity SequentialNumberGuessIdentity;

        // v1 identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v1;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v1;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v1;

        // v1.5 (Dynamic Update) identities.
        static public WorkflowIdentity StateMachineNumberGuessIdentity_v15;
        static public WorkflowIdentity FlowchartNumberGuessIdentity_v15;
        static public WorkflowIdentity SequentialNumberGuessIdentity_v15;

        static WorkflowVersionMap()
        {
            map = new Dictionary<WorkflowIdentity, Activity>();

            // Add the current workflow version identities.
            StateMachineNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            SequentialNumberGuessIdentity = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                // Version = new Version(1, 0, 0, 0),
                Version = new Version(2, 0, 0, 0)
            };

            map.Add(StateMachineNumberGuessIdentity, new StateMachineNumberGuessWorkflow());
            map.Add(FlowchartNumberGuessIdentity, new FlowchartNumberGuessWorkflow());
            map.Add(SequentialNumberGuessIdentity, new SequentialNumberGuessWorkflow());

            // Initialize the previous workflow version identities.
            StateMachineNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            FlowchartNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            SequentialNumberGuessIdentity_v1 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 0, 0, 0)
            };

            // Add the previous version workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v1 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v1AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v1.dll";
            v1AssemblyPath = Path.GetFullPath(v1AssemblyPath);
            Assembly v1Assembly = Assembly.LoadFile(v1AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v1,
                v1Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);

            // Initialize the dynamic update workflow identities.
            StateMachineNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "StateMachineNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            FlowchartNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "FlowchartNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            SequentialNumberGuessIdentity_v15 = new WorkflowIdentity
            {
                Name = "SequentialNumberGuessWorkflow",
                Version = new Version(1, 5, 0, 0)
            };

            // Add the dynamic update workflow identities to the dictionary along with
            // the corresponding workflow definitions loaded from the v15 assembly.
            // Assembly.LoadFile requires an absolute path so convert this relative path
            // to an absolute path.
            string v15AssemblyPath = @"..\..\..\PreviousVersions\NumberGuessWorkflowActivities_v15.dll";
            v15AssemblyPath = Path.GetFullPath(v15AssemblyPath);
            Assembly v15Assembly = Assembly.LoadFile(v15AssemblyPath);

            map.Add(StateMachineNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.StateMachineNumberGuessWorkflow") as Activity);

            map.Add(SequentialNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.SequentialNumberGuessWorkflow") as Activity);

            map.Add(FlowchartNumberGuessIdentity_v15,
                v15Assembly.CreateInstance("NumberGuessWorkflowActivities.FlowchartNumberGuessWorkflow") as Activity);
        }

        public static Activity GetWorkflowDefinition(WorkflowIdentity identity)
        {
            return map[identity];
        }

        public static string GetIdentityDescription(WorkflowIdentity identity)
        {
            return identity.ToString();
        }
    }
    ```

5. <span data-ttu-id="9b2e5-194">Appuyez sur CTRL+MAJ+B pour générer le projet.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-194">Press CTRL+SHIFT+B to build the project.</span></span>

### <a name="to-apply-the-dynamic-updates"></a><a name="BKMK_ApplyUpdate"></a> <span data-ttu-id="9b2e5-195">Pour appliquer les mises à jour dynamiques</span><span class="sxs-lookup"><span data-stu-id="9b2e5-195">To apply the dynamic updates</span></span>

1. <span data-ttu-id="9b2e5-196">Cliquez avec le bouton droit sur **WF45GettingStartedTutorial** dans **Explorateur de solutions** , puis choisissez **Ajouter**, **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-196">Right-click **WF45GettingStartedTutorial** in **Solution Explorer** and choose **Add**, **New Project**.</span></span>

2. <span data-ttu-id="9b2e5-197">Dans le nœud **installé** , sélectionnez **Visual C#**, **Windows** (ou **Visual Basic**, **Windows**).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-197">In the **Installed** node, select **Visual C#**, **Windows** (or **Visual Basic**, **Windows**).</span></span>

    > [!NOTE]
    > <span data-ttu-id="9b2e5-198">Selon le langage de programmation configuré comme langage principal dans Visual Studio, le nœud **Visual C#** ou **Visual Basic** peut se trouver sous le nœud **Autres langages** dans le nœud **Installé**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-198">Depending on which programming language is configured as the primary language in Visual Studio, the **Visual C#** or **Visual Basic** node may be under the **Other Languages** node in the **Installed** node.</span></span>

    <span data-ttu-id="9b2e5-199">Assurez-vous que **.NET Framework 4.5** est sélectionné dans la liste déroulante de la version .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-199">Ensure that **.NET Framework 4.5** is selected in the .NET Framework version drop-down list.</span></span> <span data-ttu-id="9b2e5-200">Sélectionnez **application console** dans la liste **Windows** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-200">Select **Console Application** from the **Windows** list.</span></span> <span data-ttu-id="9b2e5-201">Tapez **ApplyDynamicUpdate** dans la zone **nom** , puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-201">Type **ApplyDynamicUpdate** into the **Name** box and click **OK**.</span></span>

3. <span data-ttu-id="9b2e5-202">Cliquez avec le bouton droit sur **ApplyDynamicUpdate** dans **Explorateur de solutions** , puis choisissez **Ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-202">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Add Reference**.</span></span>

4. <span data-ttu-id="9b2e5-203">Cliquez sur **solution** et activez la case à cocher en regard de **NumberGuessWorkflowHost**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-203">Click **Solution** and check the box next to **NumberGuessWorkflowHost**.</span></span> <span data-ttu-id="9b2e5-204">Cette référence est nécessaire afin que `ApplyDynamicUpdate` puisse utiliser la classe `NumberGuessWorkflowHost.WorkflowVersionMap`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-204">This reference is needed so that `ApplyDynamicUpdate` can use the `NumberGuessWorkflowHost.WorkflowVersionMap` class.</span></span>

5. <span data-ttu-id="9b2e5-205">Sélectionnez **Framework** dans le nœud **assemblys** de la liste **Ajouter une référence** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-205">Select **Framework** from the **Assemblies** node in the **Add Reference** list.</span></span> <span data-ttu-id="9b2e5-206">Tapez **System. Activities** dans la zone Rechercher dans les **assemblys** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-206">Type **System.Activities** into the **Search Assemblies** box.</span></span> <span data-ttu-id="9b2e5-207">Cette opération filtrera les assemblys et facilitera la sélection des références souhaitées.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-207">This will filter the assemblies and make the desired references easier to select.</span></span>

6. <span data-ttu-id="9b2e5-208">Activez la case à cocher en regard de **System. Activities** dans la liste des **résultats de recherche** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-208">Check the checkbox beside **System.Activities** from the **Search Results** list.</span></span>

7. <span data-ttu-id="9b2e5-209">Tapez **Serialization** dans la zone **Rechercher** dans les assemblys, puis activez la case à cocher en regard de **System. Runtime. Serialization** dans la liste des résultats de la **recherche** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-209">Type **Serialization** into the **Search Assemblies** box, and check the checkbox beside **System.Runtime.Serialization** from the **Search Results** list.</span></span>

8. <span data-ttu-id="9b2e5-210">Tapez **DurableInstancing** dans la zone Rechercher dans les **assemblys** et cochez la case en regard de **System. Activities. DurableInstancing** et **System. Runtime. DurableInstancing** dans la liste des résultats de la **recherche** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-210">Type **DurableInstancing** into the **Search Assemblies** box, and check the checkbox beside **System.Activities.DurableInstancing** and **System.Runtime.DurableInstancing** from the **Search Results** list.</span></span>

9. <span data-ttu-id="9b2e5-211">Cliquez sur **OK** pour fermer le **Gestionnaire** de références et ajouter les références.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-211">Click **OK** to close **Reference Manager** and add the references.</span></span>

10. <span data-ttu-id="9b2e5-212">Cliquez avec le bouton droit sur **ApplyDynamicUpdate** dans Explorateur de solutions, puis choisissez **Ajouter**, **classe**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-212">Right-click **ApplyDynamicUpdate** in Solution Explorer and choose **Add**, **Class**.</span></span> <span data-ttu-id="9b2e5-213">Tapez `DynamicUpdateInfo` dans la zone **nom** , puis cliquez sur **Ajouter**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-213">Type `DynamicUpdateInfo` into the **Name** box and click **Add**.</span></span>

11. <span data-ttu-id="9b2e5-214">Ajoutez les deux membres suivants à la classe `DynamicUpdateInfo`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-214">Add the following two members to the `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="9b2e5-215">L'exemple suivant illustre la classe `DynamicUpdateInfo` complète.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-215">The following example is the completed `DynamicUpdateInfo` class.</span></span> <span data-ttu-id="9b2e5-216">Cette classe contient des informations sur la carte de mise à jour et la nouvelle identité de workflow utilisée lorsqu'une instance du workflow est mise à jour.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-216">This class contains information on the update map and new workflow identity used when a workflow instance is updated.</span></span>

    ```vb
    Public Class DynamicUpdateInfo
        Public updateMap As DynamicUpdateMap
        Public newIdentity As WorkflowIdentity
    End Class
    ```

    ```csharp
    class DynamicUpdateInfo
    {
        public DynamicUpdateMap updateMap;
        public WorkflowIdentity newIdentity;
    }
    ```

12. <span data-ttu-id="9b2e5-217">Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-217">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. <span data-ttu-id="9b2e5-218">Double-cliquez sur **Program.cs** (ou **Module1. vb**) dans Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-218">Double-click **Program.cs** (or **Module1.vb**) in Solution Explorer.</span></span>

14. <span data-ttu-id="9b2e5-219">Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-219">Add the following `using` (or `Imports`) statements at the top of the file with the other `using` (or `Imports`) statements.</span></span>

    ```vb
    Imports NumberGuessWorkflowHost
    Imports System.Data.SqlClient
    Imports System.Activities.DynamicUpdate
    Imports System.IO
    Imports System.Runtime.Serialization
    Imports System.Activities
    Imports System.Activities.DurableInstancing
    ```

    ```csharp
    using NumberGuessWorkflowHost;
    using System.Data;
    using System.Data.SqlClient;
    using System.Activities;
    using System.Activities.DynamicUpdate;
    using System.IO;
    using System.Runtime.Serialization;
    using System.Activities.DurableInstancing;
    ```

15. <span data-ttu-id="9b2e5-220">Ajoutez le membre de chaîne de connexion suivant à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-220">Add the following connection string member to the `Program` class (or `Module1`).</span></span>

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > <span data-ttu-id="9b2e5-221">Selon votre édition de SQL Server, le nom du serveur de chaîne de connexion peut être différent.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-221">Depending on your edition of SQL Server, the connection string server name may be different.</span></span>

16. <span data-ttu-id="9b2e5-222">Ajoutez la méthode `GetIDs` suivante à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-222">Add the following `GetIDs` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="9b2e5-223">Cette méthode retourne une liste d'ID d'instance persistante de workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-223">This method returns a list of persisted workflow instance ids.</span></span>

    ```vb
    Function GetIds() As IList(Of Guid)
        Dim Ids As New List(Of Guid)
        Dim localCmd = _
            String.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]")
        Using localCon = New SqlConnection(connectionString)
            Dim cmd As SqlCommand = localCon.CreateCommand()
            cmd.CommandText = localCmd
            localCon.Open()
            Using reader = cmd.ExecuteReader(CommandBehavior.CloseConnection)
                While reader.Read()
                    'Get the InstanceId of the persisted Workflow
                    Dim id As Guid = Guid.Parse(reader(0).ToString())

                    'Add it to the list.
                    Ids.Add(id)
                End While
            End Using
        End Using

        Return Ids
    End Function
    ```

    ```csharp
    static IList<Guid> GetIds()
    {
        List<Guid> Ids = new List<Guid>();
        string localCmd = string.Format("Select [InstanceId] from [System.Activities.DurableInstancing].[Instances] Order By [CreationTime]");
        using (SqlConnection localCon = new SqlConnection(connectionString))
        {
            SqlCommand cmd = localCon.CreateCommand();
            cmd.CommandText = localCmd;
            localCon.Open();
            using (SqlDataReader reader = cmd.ExecuteReader(CommandBehavior.CloseConnection))
            {
                while (reader.Read())
                {
                    // Get the InstanceId of the persisted Workflow
                    Guid id = Guid.Parse(reader[0].ToString());

                    // Add it to the list.
                    Ids.Add(id);
                }
            }
        }

        return Ids;
    }
    ```

17. <span data-ttu-id="9b2e5-224">Ajoutez la méthode `LoadMap` suivante à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-224">Add the following `LoadMap` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="9b2e5-225">Cette méthode crée un dictionnaire qui mappe les identités de workflow `v1` aux cartes de mise à jour et nouvelles identités de workflow utilisées pour mettre à jour les instances persistantes correspondantes de workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-225">This method creates a dictionary that maps `v1` workflow identities to the update maps and new workflow identities used to update the corresponding persisted workflow instances.</span></span>

    ```vb
    Function LoadMap(mapName As String) As DynamicUpdateMap
        Dim mapPath As String = Path.Combine("..\..\..\PreviousVersions", mapName)

        Dim map As DynamicUpdateMap
        Using fs As FileStream = File.Open(mapPath, FileMode.Open)
            Dim serializer As DataContractSerializer = New DataContractSerializer(GetType(DynamicUpdateMap))
            Dim updateMap = serializer.ReadObject(fs)
            If updateMap Is Nothing Then
                Throw New ApplicationException("DynamicUpdateMap is null.")
            End If

            map = updateMap
        End Using

        Return map
    End Function
    ```

    ```csharp
    static DynamicUpdateMap LoadMap(string mapName)
    {
        string path = Path.Combine(@"..\..\..\PreviousVersions", mapName);

        DynamicUpdateMap map;
        using (FileStream fs = File.Open(path, FileMode.Open))
        {
            DataContractSerializer serializer = new DataContractSerializer(typeof(DynamicUpdateMap));
            object updateMap = serializer.ReadObject(fs);
            if (updateMap == null)
            {
                throw new ApplicationException("DynamicUpdateMap is null.");
            }

            map = updateMap as DynamicUpdateMap;
        }

        return map;
    }
    ```

18. <span data-ttu-id="9b2e5-226">Ajoutez la méthode `LoadMaps` suivante à la classe `Program` (ou `Module1`).</span><span class="sxs-lookup"><span data-stu-id="9b2e5-226">Add the following `LoadMaps` method to the `Program` class (or `Module1`).</span></span> <span data-ttu-id="9b2e5-227">Cette méthode charge les trois cartes de mise à jour et crée un dictionnaire qui mappe les identités de workflow `v1` aux cartes de mise à jour.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-227">This method loads the three update maps and creates a dictionary that maps `v1` workflow identities to the update maps.</span></span>

    ```vb
    Function LoadMaps() As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo)
        'There are 3 update maps to describe the changes to update v1 workflows,
        'one for reach of the 3 workflow types in the tutorial.
        Dim maps = New Dictionary(Of WorkflowIdentity, DynamicUpdateInfo)()

        Dim sequentialMap As DynamicUpdateMap = LoadMap("SequentialNumberGuessWorkflow.map")
        Dim sequentialInfo = New DynamicUpdateInfo With
        {
            .updateMap = sequentialMap,
            .newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo)

        Dim stateMap As DynamicUpdateMap = LoadMap("StateMachineNumberGuessWorkflow.map")
        Dim stateInfo = New DynamicUpdateInfo With
        {
            .updateMap = stateMap,
            .newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo)

        Dim flowchartMap As DynamicUpdateMap = LoadMap("FlowchartNumberGuessWorkflow.map")
        Dim flowchartInfo = New DynamicUpdateInfo With
        {
            .updateMap = flowchartMap,
            .newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        }
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo)

        Return maps
    End Function
    ```

    ```csharp
    static IDictionary<WorkflowIdentity, DynamicUpdateInfo> LoadMaps()
    {
        // There are 3 update maps to describe the changes to update v1 workflows,
        // one for reach of the 3 workflow types in the tutorial.
        Dictionary<WorkflowIdentity, DynamicUpdateInfo> maps =
            new Dictionary<WorkflowIdentity, DynamicUpdateInfo>();

        DynamicUpdateMap sequentialMap = LoadMap("SequentialNumberGuessWorkflow.map");
        DynamicUpdateInfo sequentialInfo = new DynamicUpdateInfo
        {
            updateMap = sequentialMap,
            newIdentity = WorkflowVersionMap.SequentialNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.SequentialNumberGuessIdentity_v1, sequentialInfo);

        DynamicUpdateMap stateMap = LoadMap("StateMachineNumberGuessWorkflow.map");
        DynamicUpdateInfo stateInfo = new DynamicUpdateInfo
        {
            updateMap = stateMap,
            newIdentity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.StateMachineNumberGuessIdentity_v1, stateInfo);

        DynamicUpdateMap flowchartMap = LoadMap("FlowchartNumberGuessWorkflow.map");
        DynamicUpdateInfo flowchartInfo = new DynamicUpdateInfo
        {
            updateMap = flowchartMap,
            newIdentity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v15
        };
        maps.Add(WorkflowVersionMap.FlowchartNumberGuessIdentity_v1, flowchartInfo);

        return maps;
    }
    ```

19. <span data-ttu-id="9b2e5-228">Ajoutez le code suivant à `Main`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-228">Add the following code to `Main`.</span></span> <span data-ttu-id="9b2e5-229">Ce code itère les instances persistantes de workflow et examine chaque `WorkflowIdentity`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-229">This code iterates the persisted workflow instances and examines each `WorkflowIdentity`.</span></span> <span data-ttu-id="9b2e5-230">Si `WorkflowIdentity` mappe à une instance de workflow `v1`, un `WorkflowApplication` est configuré avec la définition mise à jour de workflow et une identité mise à jour de workflow.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-230">If the `WorkflowIdentity` maps to a `v1` workflow instance, a `WorkflowApplication` is configured with the updated workflow definition and an updated workflow identity.</span></span> <span data-ttu-id="9b2e5-231">Ensuite, `WorkflowApplication.Load` est appelé avec l'instance et la carte de mise à jour, ce qui implémente la carte de mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-231">Next, `WorkflowApplication.Load` is called with the instance and the update map, which applies the dynamic update map.</span></span> <span data-ttu-id="9b2e5-232">Une fois la mise à jour appliquée, l'instance mise à jour est rendue persistante par un appel à `Unload`.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-232">Once the update is applied, the updated instance is persisted with a call to `Unload`.</span></span>

    ```vb
    Dim store = New SqlWorkflowInstanceStore(connectionString)
    WorkflowApplication.CreateDefaultInstanceOwner(store, Nothing, WorkflowIdentityFilter.Any)

    Dim updateMaps As IDictionary(Of WorkflowIdentity, DynamicUpdateInfo) = LoadMaps()

    For Each id As Guid In GetIds()
        'Get a proxy to the instance.
        Dim instance As WorkflowApplicationInstance = WorkflowApplication.GetInstance(id, store)

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity)

        'Only update v1 workflows.
        If Not instance.DefinitionIdentity Is Nothing AndAlso _
            instance.DefinitionIdentity.Version.Equals(New Version(1, 0, 0, 0)) Then

            Dim info As DynamicUpdateInfo = updateMaps(instance.DefinitionIdentity)

            'Associate the persisted WorkflowApplicationInstance with
            'a WorkflowApplication that is configured with the updated
            'definition and updated WorkflowIdentity.
            Dim wf As Activity = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity)
            Dim wfApp = New WorkflowApplication(wf, info.newIdentity)

            'Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap)

            'Persist the updated instance.
            wfApp.Unload()

            Console.WriteLine("Updated to: {0}", info.newIdentity)
        Else
            'Not updating this instance, so unload it.
            instance.Abandon()
        End If
    Next
    ```

    ```csharp
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);
    WorkflowApplication.CreateDefaultInstanceOwner(store, null, WorkflowIdentityFilter.Any);

    IDictionary<WorkflowIdentity, DynamicUpdateInfo> updateMaps = LoadMaps();

    foreach (Guid id in GetIds())
    {
        // Get a proxy to the instance.
        WorkflowApplicationInstance instance =
            WorkflowApplication.GetInstance(id, store);

        Console.WriteLine("Inspecting: {0}", instance.DefinitionIdentity);

        // Only update v1 workflows.
        if (instance.DefinitionIdentity != null &&
            instance.DefinitionIdentity.Version.Equals(new Version(1, 0, 0, 0)))
        {
            DynamicUpdateInfo info = updateMaps[instance.DefinitionIdentity];

            // Associate the persisted WorkflowApplicationInstance with
            // a WorkflowApplication that is configured with the updated
            // definition and updated WorkflowIdentity.
            Activity wf = WorkflowVersionMap.GetWorkflowDefinition(info.newIdentity);
            WorkflowApplication wfApp =
                new WorkflowApplication(wf, info.newIdentity);

            // Apply the Dynamic Update.
            wfApp.Load(instance, info.updateMap);

            // Persist the updated instance.
            wfApp.Unload();

            Console.WriteLine("Updated to: {0}", info.newIdentity);
        }
        else
        {
            // Not updating this instance, so unload it.
            instance.Abandon();
        }
    }
    ```

20. <span data-ttu-id="9b2e5-233">Cliquez avec le bouton droit sur **ApplyDynamicUpdate** dans **Explorateur de solutions** , puis choisissez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-233">Right-click **ApplyDynamicUpdate** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

21. <span data-ttu-id="9b2e5-234">Appuyez sur Ctrl+Maj+B pour générer la solution, puis appuyez sur Ctrl+F5 pour exécuter l'application `ApplyDynamicUpdate` et mettre à jour les instances de workflow rendues persistantes.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-234">Press CTRL+SHIFT+B to build the solution, and then press CTRL+F5 to run the `ApplyDynamicUpdate` application and update the persisted workflow instances.</span></span> <span data-ttu-id="9b2e5-235">Vous devez voir une sortie semblable à la suivante.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-235">You should see output similar to the following.</span></span> <span data-ttu-id="9b2e5-236">Les workflow version 1.0.0.0 sont mis à jour vers la version 1.5.0.0, alors que les workflow version 2.0.0.0 ne sont pas mis à jour.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-236">The version 1.0.0.0 workflows are updated to version 1.5.0.0, while the version 2.0.0.0 workflows are not updated.</span></span>

    <span data-ttu-id="9b2e5-237">**Inspection : StateMachineNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-237">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-238">**Mise à jour vers : StateMachineNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-238">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-239">**Inspection : StateMachineNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-239">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-240">**Mise à jour vers : StateMachineNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-240">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-241">**Inspection : FlowchartNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-241">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-242">**Mise à jour vers : FlowchartNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-242">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-243">**Inspection : FlowchartNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-243">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-244">**Mise à jour vers : FlowchartNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-244">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-245">**Inspection : SequentialNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-245">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-246">**Mise à jour vers : SequentialNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-246">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-247">**Inspection : SequentialNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-247">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-248">**Mise à jour vers : SequentialNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-248">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-249">**Inspection : SequentialNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-249">**Inspecting: SequentialNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-250">**Mise à jour vers : SequentialNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-250">**Updated to: SequentialNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-251">**Inspection : StateMachineNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-251">**Inspecting: StateMachineNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-252">**Mise à jour vers : StateMachineNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-252">**Updated to: StateMachineNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-253">**Inspection : FlowchartNumberGuessWorkflow ; Version = 1.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-253">**Inspecting: FlowchartNumberGuessWorkflow; Version=1.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-254">**Mise à jour vers : FlowchartNumberGuessWorkflow ; Version = 1.5.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-254">**Updated to: FlowchartNumberGuessWorkflow; Version=1.5.0.0**</span></span>\
    <span data-ttu-id="9b2e5-255">**Inspection : StateMachineNumberGuessWorkflow ; Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-255">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-256">**Inspection : StateMachineNumberGuessWorkflow ; Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-256">**Inspecting: StateMachineNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-257">**Inspection : FlowchartNumberGuessWorkflow ; Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-257">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-258">**Inspection : FlowchartNumberGuessWorkflow ; Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-258">**Inspecting: FlowchartNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-259">**Inspection : SequentialNumberGuessWorkflow ; Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-259">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-260">**Inspection : SequentialNumberGuessWorkflow ; Version = 2.0.0.0**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-260">**Inspecting: SequentialNumberGuessWorkflow; Version=2.0.0.0**</span></span>\
    <span data-ttu-id="9b2e5-261">**Appuyez sur une touche pour continuer...**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-261">**Press any key to continue . . .**</span></span>

### <a name="to-run-the-application-with-the-updated-workflows"></a><a name="BKMK_BuildAndRun"></a> <span data-ttu-id="9b2e5-262">Pour exécuter l’application avec les flux de travail mis à jour</span><span class="sxs-lookup"><span data-stu-id="9b2e5-262">To run the application with the updated workflows</span></span>

1. <span data-ttu-id="9b2e5-263">Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans **Explorateur de solutions** , puis choisissez **définir comme projet de démarrage**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-263">Right-click **NumberGuessWorkflowHost** in **Solution Explorer** and choose **Set as StartUp Project**.</span></span>

2. <span data-ttu-id="9b2e5-264">Appuyez sur Ctrl+F5 pour exécuter l’application.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-264">Press CTRL+F5 to run the application.</span></span>

3. <span data-ttu-id="9b2e5-265">Cliquez sur **nouveau jeu** pour démarrer un nouveau flux de travail et notez les informations de version sous la fenêtre d’État qui indique que le flux de travail est un `v2` flux de travail.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-265">Click **New Game** to start a new workflow and note the version information below the status window that indicates the workflow is a `v2` workflow.</span></span>

4. <span data-ttu-id="9b2e5-266">Sélectionnez l’un des `v1` flux de travail que vous avez démarrés au début de la rubrique [Comment : héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-266">Select one of the `v1` workflows you started at the beginning of the [How to: Host Multiple Versions of a Workflow Side-by-Side](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) topic.</span></span> <span data-ttu-id="9b2e5-267">Notez que les informations de version dans la fenêtre d’État indiquent que le flux de travail est un flux de travail de version **1.5.0.0** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-267">Note that the version information under the status window indicates that the workflow is a version **1.5.0.0** workflow.</span></span> <span data-ttu-id="9b2e5-268">Notez qu'il n'y a aucune information sur les estimations précédentes autres que celles indiquant si elles étaient trop élevées ou faibles.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-268">Note that there is no information indicated about previous guesses other than whether they were too high or too low.</span></span>

    <span data-ttu-id="9b2e5-269">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-269">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-270">**Your guess is too low.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-270">**Your guess is too low.**</span></span>

5. <span data-ttu-id="9b2e5-271">Notez `InstanceId` puis entrez des estimations jusqu'à ce que le workflow se termine.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-271">Make a note of the `InstanceId` and then enter guesses until the workflow completes.</span></span> <span data-ttu-id="9b2e5-272">La fenêtre d'état affiche des informations sur le contenu de l'estimation, car les activités `WriteLine` ont été mises à jour par la mise à jour dynamique.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-272">The status window displays information about the content of the guess because the `WriteLine` activities were updated by the dynamic update.</span></span>

    <span data-ttu-id="9b2e5-273">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-273">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-274">**Votre estimation est trop faible.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-274">**Your guess is too low.**</span></span>\
    <span data-ttu-id="9b2e5-275">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-275">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-276">**5 est trop faible.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-276">**5 is too low.**</span></span>\
    <span data-ttu-id="9b2e5-277">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-277">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-278">**7 est trop élevé.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-278">**7 is too high.**</span></span>\
    <span data-ttu-id="9b2e5-279">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-279">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-280">**Félicitations, vous avez deviné le nombre en 4 tours.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-280">**Congratulations, you guessed the number in 4 turns.**</span></span>

6. <span data-ttu-id="9b2e5-281">Ouvrez l’Explorateur Windows et accédez au dossier **NumberGuessWorkflowHost\bin\debug** (ou **bin\Release** selon les paramètres de votre projet), puis ouvrez le fichier de suivi à l’aide du bloc-notes qui correspond au workflow terminé.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-281">Open Windows Explorer and navigate to the **NumberGuessWorkflowHost\bin\debug** folder (or **bin\release** depending on your project settings) and open the tracking file using Notepad that corresponds to the completed workflow.</span></span> <span data-ttu-id="9b2e5-282">Si vous n’avez pas noté le `InstanceId` , vous pourrez peut-être identifier le fichier de suivi approprié à l’aide des informations de **Date de modification** dans l’Explorateur Windows.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-282">If you did not make a note of the `InstanceId` you may be able to identify the correct tracking file by using the **Date modified** information in Windows Explorer.</span></span> <span data-ttu-id="9b2e5-283">La dernière ligne d'informations de suivi contient la sortie de l'activité `WriteLine` récemment ajoutée.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-283">The last line of the tracking information contains the output of the newly added `WriteLine` activity.</span></span>

    <span data-ttu-id="9b2e5-284">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-284">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-285">**Votre estimation est trop faible.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-285">**Your guess is too low.**</span></span>\
    <span data-ttu-id="9b2e5-286">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-286">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-287">**5 est trop faible.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-287">**5 is too low.**</span></span>\
    <span data-ttu-id="9b2e5-288">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-288">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-289">**7 est trop élevé.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-289">**7 is too high.**</span></span>\
    <span data-ttu-id="9b2e5-290">**Entrez un nombre compris entre 1 et 10**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-290">**Please enter a number between 1 and 10**</span></span>\
    <span data-ttu-id="9b2e5-291">**6 est correct. Vous l’avez deviné en 4 tours.**</span><span class="sxs-lookup"><span data-stu-id="9b2e5-291">**6 is correct. You guessed it in 4 turns.**</span></span>

### <a name="to-enable-starting-previous-versions-of-the-workflows"></a><a name="BKMK_StartPreviousVersions"></a> <span data-ttu-id="9b2e5-292">Pour activer le démarrage des versions antérieures des flux de travail</span><span class="sxs-lookup"><span data-stu-id="9b2e5-292">To enable starting previous versions of the workflows</span></span>

<span data-ttu-id="9b2e5-293">Si vous ne disposez pas de workflow à mettre jour, modifiez l'application `NumberGuessWorkflowHost` afin d'activer le démarrage des versions antérieures des workflows.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-293">If you run out of workflows to update, you can modify the `NumberGuessWorkflowHost` application to enable starting previous versions of the workflows.</span></span>

1. <span data-ttu-id="9b2e5-294">Double-cliquez sur **WorkflowHostForm** dans **Explorateur de solutions**, puis sélectionnez la zone de liste déroulante **WorkflowType** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-294">Double-click **WorkflowHostForm** in **Solution Explorer**, and select the **WorkflowType** combo box.</span></span>

2. <span data-ttu-id="9b2e5-295">Dans la fenêtre **Propriétés** , sélectionnez la propriété **Items** , puis cliquez sur le bouton de sélection pour modifier la collection **Items** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-295">In the **Properties** window, select the **Items** property and click the ellipsis button to edit the **Items** collection.</span></span>

3. <span data-ttu-id="9b2e5-296">Ajoutez les trois éléments suivants à la collection :</span><span class="sxs-lookup"><span data-stu-id="9b2e5-296">Add the following three items to the collection.</span></span>

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    <span data-ttu-id="9b2e5-297">La collection `Items` terminée contiendra six éléments.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-297">The completed `Items` collection will have six items.</span></span>

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. <span data-ttu-id="9b2e5-298">Double-cliquez sur **WorkflowHostForm** dans **Explorateur de solutions**, puis sélectionnez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-298">Double-click **WorkflowHostForm** in **Solution Explorer**, and select **View Code**.</span></span>

5. <span data-ttu-id="9b2e5-299">Ajoutez trois nouveaux cas à l' `switch` instruction (ou `Select Case` ) dans le `NewGame_Click` Gestionnaire pour mapper les nouveaux éléments de la zone de liste déroulante **WorkflowType** aux identités de workflow correspondantes.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-299">Add three new cases to the `switch` (or `Select Case`) statement in the `NewGame_Click` handler to map the new items in the **WorkflowType** combo box to the matching workflow identities.</span></span>

    ```vb
    Case "SequentialNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

    Case "StateMachineNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

    Case "FlowchartNumberGuessWorkflow v1"
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    ```

    ```csharp
    case "SequentialNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
        break;

    case "StateMachineNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
        break;

    case "FlowchartNumberGuessWorkflow v1":
        identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
        break;
    ```

    <span data-ttu-id="9b2e5-300">L'exemple suivant contient l'instruction `switch` (ou `Select Case`) complète.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-300">The following example contains the complete `switch` (or `Select Case`) statement.</span></span>

    ```vb
    Select Case WorkflowType.SelectedItem.ToString()
        Case "SequentialNumberGuessWorkflow"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity

        Case "StateMachineNumberGuessWorkflow"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity

        Case "FlowchartNumberGuessWorkflow"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity

        Case "SequentialNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1

        Case "StateMachineNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1

        Case "FlowchartNumberGuessWorkflow v1"
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1
    End Select
    ```

    ```csharp
    switch (WorkflowType.SelectedItem.ToString())
    {
        case "SequentialNumberGuessWorkflow":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity;
            break;

        case "StateMachineNumberGuessWorkflow":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity;
            break;

        case "FlowchartNumberGuessWorkflow":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity;
            break;

        case "SequentialNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.SequentialNumberGuessIdentity_v1;
            break;

        case "StateMachineNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.StateMachineNumberGuessIdentity_v1;
            break;

        case "FlowchartNumberGuessWorkflow v1":
            identity = WorkflowVersionMap.FlowchartNumberGuessIdentity_v1;
            break;
    };
    ```

6. <span data-ttu-id="9b2e5-301">Appuyez sur Ctrl+F5 pour générer et exécuter l'application.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-301">Press CTRL+F5 to build and run the application.</span></span> <span data-ttu-id="9b2e5-302">Vous pouvez maintenant démarrer la version `v1` des workflows, ainsi que les versions actuelles.</span><span class="sxs-lookup"><span data-stu-id="9b2e5-302">You can now start the `v1` versions of the workflow as well as the current versions.</span></span> <span data-ttu-id="9b2e5-303">Pour mettre à jour dynamiquement ces nouvelles instances, exécutez l’application **ApplyDynamicUpdate** .</span><span class="sxs-lookup"><span data-stu-id="9b2e5-303">To dynamically update these new instances, run the **ApplyDynamicUpdate** application.</span></span>
