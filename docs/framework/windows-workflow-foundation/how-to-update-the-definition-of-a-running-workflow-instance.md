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
# <a name="how-to-update-the-definition-of-a-running-workflow-instance"></a>Procédure : mettre à jour la définition d’une instance de workflow en cours d’exécution

La mise à jour dynamique fournit un mécanisme pour permettre aux développeurs d'applications de workflow de mettre à jour la définition de workflow d'une instance de workflow persistante. Il peut s’agit de l’implémentation d’une résolution de bogue, de nouvelles exigences ou de l’adaptation à des modifications inattendues. Cette étape du didacticiel montre comment utiliser la mise à jour dynamique pour modifier des instances persistantes du flux de travail de recherche de `v1` nombres afin qu’elles correspondent aux nouvelles fonctionnalités introduites dans Guide pratique [pour héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

## <a name="in-this-topic"></a>Dans cette rubrique

- [Pour créer le projet CreateUpdateMaps](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateProject)

- [Pour mettre à jour StateMachineNumberGuessWorkflow](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StateMachine)

- [Pour mettre à jour FlowchartNumberGuessWorkflow](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Flowchart)

- [Pour mettre à jour SequentialNumberGuessWorkflow](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_Sequential)

- [Pour générer et exécuter l'application CreateUpdateMaps](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_CreateUpdateMaps)

- [Pour générer l'assembly de workflow mis à jour](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAssembly)

- [Pour mettre à jour WorkflowVersionMap avec les nouvelles versions](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_UpdateWorkflowVersionMap)

- [Pour appliquer des mises à jour dynamiques](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_ApplyUpdate)

- [Pour exécuter l'application avec les workflows mis à jour](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_BuildAndRun)

- [Pour activer le démarrage des versions antérieures des workflows](how-to-update-the-definition-of-a-running-workflow-instance.md#BKMK_StartPreviousVersions)

### <a name="to-create-the-createupdatemaps-project"></a><a name="BKMK_CreateProject"></a> Pour créer le projet CreateUpdateMaps

1. Cliquez avec le bouton droit sur **WF45GettingStartedTutorial** dans **Explorateur de solutions** , puis choisissez **Ajouter**, **nouveau projet**.

2. Dans le nœud **installé** , sélectionnez **Visual C#**, **Windows** (ou **Visual Basic**, **Windows**).

    > [!NOTE]
    > Selon le langage de programmation configuré comme langage principal dans Visual Studio, le nœud **Visual C#** ou **Visual Basic** peut se trouver sous le nœud **Autres langages** dans le nœud **Installé**.

     Assurez-vous que **.NET Framework 4.5** est sélectionné dans la liste déroulante de la version .NET Framework. Sélectionnez **application console** dans la liste **Windows** . Tapez **CreateUpdateMaps** dans la zone **nom** , puis cliquez sur **OK**.

3. Cliquez avec le bouton droit sur **CreateUpdateMaps** dans **Explorateur de solutions** , puis choisissez **Ajouter une référence**.

4. Sélectionnez **Framework** dans le nœud **assemblys** de la liste **Ajouter une référence** . Tapez **System. Activities** dans la zone Rechercher dans les **assemblys** pour filtrer les assemblys et faciliter la sélection des références souhaitées.

5. Activez la case à cocher en regard de **System. Activities** dans la liste des **résultats de recherche** .

6. Tapez **Serialization** dans la zone **Rechercher** dans les assemblys, puis activez la case à cocher en regard de **System. Runtime. Serialization** dans la liste des résultats de la **recherche** .

7. Tapez **System. Xaml** dans la zone Rechercher dans les **assemblys** , puis activez la case à cocher en regard de **System. Xaml** dans la liste des résultats de la **recherche** .

8. Cliquez sur **OK** pour fermer le **Gestionnaire** de références et ajouter les références.

9. Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).

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

10. Ajoutez les deux membres de chaîne suivants à la classe `Program` (ou `Module1`).

    ```vb
    Const mapPath = "..\..\..\PreviousVersions"
    Const definitionPath = "..\..\..\NumberGuessWorkflowActivities_du"
    ```

    ```csharp
    const string mapPath = @"..\..\..\PreviousVersions";
    const string definitionPath = @"..\..\..\NumberGuessWorkflowActivities_du";
    ```

11. Ajoutez la méthode `StartUpdate` suivante à la classe `Program` (ou `Module1`). Cette méthode charge la définition spécifiée de workflow XAML dans `ActivityBuilder`, puis appelle `DynamicUpdate.PrepareForUpdate`. `PrepareForUpdate` effectue une copie de la définition de workflow à l'intérieur de `ActivityBuilder`. Une fois la définition de workflow modifiée, cette copie est utilisée parallèlement à la définition modifiée de workflow pour créer la mise à jour de la carte.

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

12. Ensuite, ajoutez la méthode `CreateUpdateMethod` à la classe `Program` (ou `Module1`). Cela crée une carte de mise à jour dynamique en appelant DynamicUpdateServices.CreateUpdateMap, puis enregistre la carte de mise à jour à l'aide du nom spécifié. Cette carte de mise à jour contient les informations nécessaires à l'exécution du workflow pour mettre à jour une instance persistante de workflow démarrée en utilisant la définition d'origine de workflow contenue dans `ActivityBuilder` afin qu'il se termine en utilisant la définition mise à jour de workflow.

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

13. Ajoutez la méthode `SaveUpdatedDefinition` suivante à la classe `Program` (ou `Module1`). Cette méthode enregistre la définition mise à jour de workflow une fois la carte de mise à jour créée.

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

### <a name="to-update-statemachinenumberguessworkflow"></a><a name="BKMK_StateMachine"></a> Pour mettre à jour StateMachineNumberGuessWorkflow

1. Ajoutez une méthode `CreateStateMachineUpdateMap` à la classe `Program` (ou `Module1`).

    ```vb
    Private Sub CreateStateMachineUpdateMap()

    End Sub
    ```

    ```csharp
    private static void CreateStateMachineUpdateMap()
    {
    }
    ```

2. Effectuez un appel à `StartUpdate`, puis obtenez une référence à l'activité `StateMachine` racine du workflow.

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

3. Ensuite, mettez à jour les expressions des deux `WriteLine` activités qui indiquent si l’estimation de l’utilisateur est trop élevée ou trop faible afin qu’elles correspondent aux mises à jour apportées dans [Comment : héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

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

4. Ensuite, ajoutez la nouvelle activité `WriteLine` qui affiche le message de fermeture.

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

5. Une fois que le workflow a été mis à jour, appelez `CreateUpdateMaps` et `SaveUpdatedDefinition`. `CreateUpdateMaps` crée et enregistre `DynamicUpdateMap`, et `SaveUpdatedDefinition` enregistre la définition mise à jour de workflow.

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

    L'exemple suivant illustre la méthode `CreateStateMachineUpdateMap` complète.

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

### <a name="to-update-flowchartnumberguessworkflow"></a><a name="BKMK_Flowchart"></a> Pour mettre à jour FlowchartNumberGuessWorkflow

1. Ajoutez la méthode `CreateFlowchartUpdateMethod` suivante à la classe `Program` (ou `Module1`). Cette méthode est semblable à `CreateStateMachineUpdateMap`. Elle commence par un appel à `StartUpdate`, met à jour la définition de workflow de l'organigramme, et se termine en enregistrant la carte de mise à jour et la définition mise à jour de workflow.

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

### <a name="to-update-sequentialnumberguessworkflow"></a><a name="BKMK_Sequential"></a> Pour mettre à jour SequentialNumberGuessWorkflow

1. Ajoutez la méthode `CreateSequentialUpdateMethod` suivante à la classe `Program` (ou `Module1`). Cette méthode est similaire aux deux autres méthodes. Elle commence par un appel à `StartUpdate`, met à jour la définition de workflow séquentiel, et se termine en enregistrant la carte de mise à jour et la définition mise à jour de workflow.

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

### <a name="to-build-and-run-the-createupdatemaps-application"></a><a name="BKMK_CreateUpdateMaps"></a> Pour générer et exécuter l’application CreateUpdateMaps

1. Ajoutez la méthode `Main` suivante, puis les trois appels de méthodes suivants. Ces méthodes sont ajoutées dans les sections suivantes. Chaque méthode met à jour le workflow d'estimation de nombre correspondant et crée un `DynamicUpdateMap` qui décrit les mises à jour.

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

2. Cliquez avec le bouton droit sur **CreateUpdateMaps** dans **Explorateur de solutions** , puis choisissez **définir comme projet de démarrage**.

3. Appuyez sur Ctrl+Maj+B pour générer la solution, puis appuyez sur Ctrl+F5 pour exécuter l'application `CreateUpdateMaps`.

    > [!NOTE]
    > L' `CreateUpdateMaps` application n’affiche pas d’informations d’État pendant l’exécution, mais si vous regardez dans le dossier **NumberGuessWorkflowActivities_du** et le dossier **PreviousVersions** , vous verrez les fichiers de définition de workflow mis à jour et les mappages de mise à jour.

    Une fois les cartes de mise à jour créées et les définitions de workflow mises à jour, l'étape suivante consiste à générer un assembly mis à jour de workflow contenant les définitions mises à jour.

### <a name="to-build-the-updated-workflow-assembly"></a><a name="BKMK_BuildAssembly"></a> Pour générer l’assembly de flux de travail mis à jour

1. Ouvrez une deuxième instance de Visual Studio 2012.

2. Dans le menu **fichier** , choisissez **ouvrir**, **projet/solution** .

3. Accédez au dossier **NumberGuessWorkflowActivities_du** que vous avez créé dans Guide pratique [pour héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md), sélectionnez **NumberGuessWorkflowActivities. csproj** (ou **vbproj**), puis cliquez sur **ouvrir**.

4. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur **SequentialNumberGuessWorkflow. Xaml** , puis choisissez **exclure du projet**. Effectuez la même opération pour **FlowchartNumberGuessWorkflow. Xaml** et **StateMachineNumberGuessWorkflow. Xaml**. Cette étape supprime les versions antérieures des définitions de workflow du projet.

5. Choisissez **Ajouter un élément existant** dans le menu **projet** .

6. Accédez au dossier **NumberGuessWorkflowActivities_du** que vous avez créé dans Guide pratique [pour héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

7. Choisissez **fichiers XAML ( \* . XAML ; \* . xoml)** dans la liste déroulante **types de fichiers** .

8. Sélectionnez **SequentialNumberGuessWorkflow_du. Xaml**, **FlowchartNumberGuessWorkflow_du. Xaml** et **StateMachineNumberGuessWorkflow_du. Xaml** , puis cliquez sur **Ajouter**.

    > [!NOTE]
    > Pour sélectionner plusieurs éléments à la fois, appuyez sur la touche Ctrl pendant que vous cliquez dessus.

    Cette étape ajoute les versions mises à jour des définitions de workflow au projet.

9. Appuyez sur CTRL+MAJ+B pour générer le projet.

10. Choisissez **Fermer la solution** dans le menu **fichier** . Un fichier solution pour le projet n’est pas obligatoire. par conséquent, cliquez sur **non** pour fermer Visual Studio sans enregistrer un fichier solution. Choisissez **quitter** dans le menu **fichier** pour fermer Visual Studio.

11. Ouvrez l’Explorateur Windows et accédez au dossier **NumberGuessWorkflowActivities_du \bin\debug** (ou **bin\Release** selon les paramètres de votre projet).

12. Renommez **NumberGuessWorkflowActivities.dll** en **NumberGuessWorkflowActivities_v15.dll**, puis copiez-le dans le dossier **PreviousVersions** que vous avez créé dans Guide pratique [pour héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md).

### <a name="to-update-workflowversionmap-with-the-new-versions"></a><a name="BKMK_UpdateWorkflowVersionMap"></a> Pour mettre à jour WorkflowVersionMap avec les nouvelles versions

1. Revenez à l’instance initiale de Visual Studio 2012.

2. Double-cliquez sur **WorkflowVersionMap.cs** (ou **WorkflowVersionMap. vb**) sous le projet **NumberGuessWorkflowHost** pour l’ouvrir.

3. Ajoutez trois nouvelles identités de workflow juste au-dessous des six déclarations d'identité de workflow existantes. Dans ce didacticiel, `1.5.0.0` est utilisé comme `WorkflowIdentity.Version` pour les identités de mise à jour dynamique. Ces nouvelles identités de workflow `v15` seront utilisées pour fournir la définition appropriée de workflow aux instances de workflow persistantes mises à jour dynamiquement.

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

4. À la fin du constructeur, ajoutez le code suivant. Ce code initialise les identités de workflow de mise à jour dynamique, charge les définitions correspondantes de workflow, et les ajoute au dictionnaire de version de workflow.

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

     L'exemple suivant illustre la classe `WorkflowVersionMap` complète.

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

5. Appuyez sur CTRL+MAJ+B pour générer le projet.

### <a name="to-apply-the-dynamic-updates"></a><a name="BKMK_ApplyUpdate"></a> Pour appliquer les mises à jour dynamiques

1. Cliquez avec le bouton droit sur **WF45GettingStartedTutorial** dans **Explorateur de solutions** , puis choisissez **Ajouter**, **nouveau projet**.

2. Dans le nœud **installé** , sélectionnez **Visual C#**, **Windows** (ou **Visual Basic**, **Windows**).

    > [!NOTE]
    > Selon le langage de programmation configuré comme langage principal dans Visual Studio, le nœud **Visual C#** ou **Visual Basic** peut se trouver sous le nœud **Autres langages** dans le nœud **Installé**.

    Assurez-vous que **.NET Framework 4.5** est sélectionné dans la liste déroulante de la version .NET Framework. Sélectionnez **application console** dans la liste **Windows** . Tapez **ApplyDynamicUpdate** dans la zone **nom** , puis cliquez sur **OK**.

3. Cliquez avec le bouton droit sur **ApplyDynamicUpdate** dans **Explorateur de solutions** , puis choisissez **Ajouter une référence**.

4. Cliquez sur **solution** et activez la case à cocher en regard de **NumberGuessWorkflowHost**. Cette référence est nécessaire afin que `ApplyDynamicUpdate` puisse utiliser la classe `NumberGuessWorkflowHost.WorkflowVersionMap`.

5. Sélectionnez **Framework** dans le nœud **assemblys** de la liste **Ajouter une référence** . Tapez **System. Activities** dans la zone Rechercher dans les **assemblys** . Cette opération filtrera les assemblys et facilitera la sélection des références souhaitées.

6. Activez la case à cocher en regard de **System. Activities** dans la liste des **résultats de recherche** .

7. Tapez **Serialization** dans la zone **Rechercher** dans les assemblys, puis activez la case à cocher en regard de **System. Runtime. Serialization** dans la liste des résultats de la **recherche** .

8. Tapez **DurableInstancing** dans la zone Rechercher dans les **assemblys** et cochez la case en regard de **System. Activities. DurableInstancing** et **System. Runtime. DurableInstancing** dans la liste des résultats de la **recherche** .

9. Cliquez sur **OK** pour fermer le **Gestionnaire** de références et ajouter les références.

10. Cliquez avec le bouton droit sur **ApplyDynamicUpdate** dans Explorateur de solutions, puis choisissez **Ajouter**, **classe**. Tapez `DynamicUpdateInfo` dans la zone **nom** , puis cliquez sur **Ajouter**.

11. Ajoutez les deux membres suivants à la classe `DynamicUpdateInfo`. L'exemple suivant illustre la classe `DynamicUpdateInfo` complète. Cette classe contient des informations sur la carte de mise à jour et la nouvelle identité de workflow utilisée lorsqu'une instance du workflow est mise à jour.

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

12. Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).

    ```vb
    Imports System.Activities
    Imports System.Activities.DynamicUpdate
    ```

    ```csharp
    using System.Activities;
    using System.Activities.DynamicUpdate;
    ```

13. Double-cliquez sur **Program.cs** (ou **Module1. vb**) dans Explorateur de solutions.

14. Ajoutez les instructions `using` (ou `Imports`) suivantes au début du fichier avec les autres instructions `using` (ou `Imports`).

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

15. Ajoutez le membre de chaîne de connexion suivant à la classe `Program` (ou `Module1`).

    ```vb
    Const connectionString = "Server=.\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI"
    ```

    ```csharp
    const string connectionString = "Server=.\\SQLEXPRESS;Initial Catalog=WF45GettingStartedTutorial;Integrated Security=SSPI";
    ```

    > [!NOTE]
    > Selon votre édition de SQL Server, le nom du serveur de chaîne de connexion peut être différent.

16. Ajoutez la méthode `GetIDs` suivante à la classe `Program` (ou `Module1`). Cette méthode retourne une liste d'ID d'instance persistante de workflow.

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

17. Ajoutez la méthode `LoadMap` suivante à la classe `Program` (ou `Module1`). Cette méthode crée un dictionnaire qui mappe les identités de workflow `v1` aux cartes de mise à jour et nouvelles identités de workflow utilisées pour mettre à jour les instances persistantes correspondantes de workflow.

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

18. Ajoutez la méthode `LoadMaps` suivante à la classe `Program` (ou `Module1`). Cette méthode charge les trois cartes de mise à jour et crée un dictionnaire qui mappe les identités de workflow `v1` aux cartes de mise à jour.

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

19. Ajoutez le code suivant à `Main`. Ce code itère les instances persistantes de workflow et examine chaque `WorkflowIdentity`. Si `WorkflowIdentity` mappe à une instance de workflow `v1`, un `WorkflowApplication` est configuré avec la définition mise à jour de workflow et une identité mise à jour de workflow. Ensuite, `WorkflowApplication.Load` est appelé avec l'instance et la carte de mise à jour, ce qui implémente la carte de mise à jour dynamique. Une fois la mise à jour appliquée, l'instance mise à jour est rendue persistante par un appel à `Unload`.

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

20. Cliquez avec le bouton droit sur **ApplyDynamicUpdate** dans **Explorateur de solutions** , puis choisissez **définir comme projet de démarrage**.

21. Appuyez sur Ctrl+Maj+B pour générer la solution, puis appuyez sur Ctrl+F5 pour exécuter l'application `ApplyDynamicUpdate` et mettre à jour les instances de workflow rendues persistantes. Vous devez voir une sortie semblable à la suivante. Les workflow version 1.0.0.0 sont mis à jour vers la version 1.5.0.0, alors que les workflow version 2.0.0.0 ne sont pas mis à jour.

    **Inspection : StateMachineNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : StateMachineNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : StateMachineNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : StateMachineNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : FlowchartNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : FlowchartNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : FlowchartNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : FlowchartNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : SequentialNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : SequentialNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : SequentialNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : SequentialNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : SequentialNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : SequentialNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : StateMachineNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : StateMachineNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : FlowchartNumberGuessWorkflow ; Version = 1.0.0.0**\
    **Mise à jour vers : FlowchartNumberGuessWorkflow ; Version = 1.5.0.0**\
    **Inspection : StateMachineNumberGuessWorkflow ; Version = 2.0.0.0**\
    **Inspection : StateMachineNumberGuessWorkflow ; Version = 2.0.0.0**\
    **Inspection : FlowchartNumberGuessWorkflow ; Version = 2.0.0.0**\
    **Inspection : FlowchartNumberGuessWorkflow ; Version = 2.0.0.0**\
    **Inspection : SequentialNumberGuessWorkflow ; Version = 2.0.0.0**\
    **Inspection : SequentialNumberGuessWorkflow ; Version = 2.0.0.0**\
    **Appuyez sur une touche pour continuer...**

### <a name="to-run-the-application-with-the-updated-workflows"></a><a name="BKMK_BuildAndRun"></a> Pour exécuter l’application avec les flux de travail mis à jour

1. Cliquez avec le bouton droit sur **NumberGuessWorkflowHost** dans **Explorateur de solutions** , puis choisissez **définir comme projet de démarrage**.

2. Appuyez sur Ctrl+F5 pour exécuter l’application.

3. Cliquez sur **nouveau jeu** pour démarrer un nouveau flux de travail et notez les informations de version sous la fenêtre d’État qui indique que le flux de travail est un `v2` flux de travail.

4. Sélectionnez l’un des `v1` flux de travail que vous avez démarrés au début de la rubrique [Comment : héberger plusieurs versions d’un flux de travail côte à côte](how-to-host-multiple-versions-of-a-workflow-side-by-side.md) . Notez que les informations de version dans la fenêtre d’État indiquent que le flux de travail est un flux de travail de version **1.5.0.0** . Notez qu'il n'y a aucune information sur les estimations précédentes autres que celles indiquant si elles étaient trop élevées ou faibles.

    **Entrez un nombre compris entre 1 et 10**\
    **Your guess is too low.**

5. Notez `InstanceId` puis entrez des estimations jusqu'à ce que le workflow se termine. La fenêtre d'état affiche des informations sur le contenu de l'estimation, car les activités `WriteLine` ont été mises à jour par la mise à jour dynamique.

    **Entrez un nombre compris entre 1 et 10**\
    **Votre estimation est trop faible.**\
    **Entrez un nombre compris entre 1 et 10**\
    **5 est trop faible.**\
    **Entrez un nombre compris entre 1 et 10**\
    **7 est trop élevé.**\
    **Entrez un nombre compris entre 1 et 10**\
    **Félicitations, vous avez deviné le nombre en 4 tours.**

6. Ouvrez l’Explorateur Windows et accédez au dossier **NumberGuessWorkflowHost\bin\debug** (ou **bin\Release** selon les paramètres de votre projet), puis ouvrez le fichier de suivi à l’aide du bloc-notes qui correspond au workflow terminé. Si vous n’avez pas noté le `InstanceId` , vous pourrez peut-être identifier le fichier de suivi approprié à l’aide des informations de **Date de modification** dans l’Explorateur Windows. La dernière ligne d'informations de suivi contient la sortie de l'activité `WriteLine` récemment ajoutée.

    **Entrez un nombre compris entre 1 et 10**\
    **Votre estimation est trop faible.**\
    **Entrez un nombre compris entre 1 et 10**\
    **5 est trop faible.**\
    **Entrez un nombre compris entre 1 et 10**\
    **7 est trop élevé.**\
    **Entrez un nombre compris entre 1 et 10**\
    **6 est correct. Vous l’avez deviné en 4 tours.**

### <a name="to-enable-starting-previous-versions-of-the-workflows"></a><a name="BKMK_StartPreviousVersions"></a> Pour activer le démarrage des versions antérieures des flux de travail

Si vous ne disposez pas de workflow à mettre jour, modifiez l'application `NumberGuessWorkflowHost` afin d'activer le démarrage des versions antérieures des workflows.

1. Double-cliquez sur **WorkflowHostForm** dans **Explorateur de solutions**, puis sélectionnez la zone de liste déroulante **WorkflowType** .

2. Dans la fenêtre **Propriétés** , sélectionnez la propriété **Items** , puis cliquez sur le bouton de sélection pour modifier la collection **Items** .

3. Ajoutez les trois éléments suivants à la collection :

    ```
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

    La collection `Items` terminée contiendra six éléments.

    ```
    StateMachineNumberGuessWorkflow
    FlowchartNumberGuessWorkflow
    SequentialNumberGuessWorkflow
    StateMachineNumberGuessWorkflow v1
    FlowchartNumberGuessWorkflow v1
    SequentialNumberGuessWorkflow v1
    ```

4. Double-cliquez sur **WorkflowHostForm** dans **Explorateur de solutions**, puis sélectionnez **afficher le code**.

5. Ajoutez trois nouveaux cas à l' `switch` instruction (ou `Select Case` ) dans le `NewGame_Click` Gestionnaire pour mapper les nouveaux éléments de la zone de liste déroulante **WorkflowType** aux identités de workflow correspondantes.

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

    L'exemple suivant contient l'instruction `switch` (ou `Select Case`) complète.

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

6. Appuyez sur Ctrl+F5 pour générer et exécuter l'application. Vous pouvez maintenant démarrer la version `v1` des workflows, ainsi que les versions actuelles. Pour mettre à jour dynamiquement ces nouvelles instances, exécutez l’application **ApplyDynamicUpdate** .
