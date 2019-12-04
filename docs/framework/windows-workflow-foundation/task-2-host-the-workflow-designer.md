---
title: 'Tâche 2 : héberger le Workflow Designer'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 8e4c17ed182cec7748b9a1f11f76ff90aa60c39e
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715789"
---
# <a name="task-2-host-the-workflow-designer"></a><span data-ttu-id="9d3c1-102">Tâche 2 : héberger le Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="9d3c1-102">Task 2: Host the Workflow Designer</span></span>

<span data-ttu-id="9d3c1-103">Cette rubrique décrit la procédure d’hébergement d’une instance de Windows Concepteur de flux de travail dans une application Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="9d3c1-103">This topic describes the procedure for hosting an instance of the Windows Workflow Designer in a Windows Presentation Foundation (WPF) application.</span></span>

<span data-ttu-id="9d3c1-104">La procédure configure le contrôle de **grille** qui contient le concepteur, crée par programmation une instance du <xref:System.Activities.Presentation.WorkflowDesigner> qui contient une activité de <xref:System.Activities.Statements.Sequence> par défaut, inscrit les métadonnées du concepteur pour fournir la prise en charge du concepteur pour toutes les activités intégrées et héberge les concepteur de flux de travail dans l’application WPF.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-104">The procedure configures the **Grid** control that contains the designer, programmatically creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner> that contains a default <xref:System.Activities.Statements.Sequence> activity, registers the designer metadata to provide designer support for all built-in activities, and hosts the Workflow Designer in the WPF application.</span></span>

## <a name="to-host-the-workflow-designer"></a><span data-ttu-id="9d3c1-105">Pour héberger le concepteur de workflow</span><span class="sxs-lookup"><span data-stu-id="9d3c1-105">To host the workflow designer</span></span>

1. <span data-ttu-id="9d3c1-106">Ouvrez le projet HostingApplication que vous avez créé dans [tâche 1 : créer une application de Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).</span><span class="sxs-lookup"><span data-stu-id="9d3c1-106">Open the HostingApplication project you created in [Task 1: Create a New Windows Presentation Foundation Application](task-1-create-a-new-wpf-app.md).</span></span>

2. <span data-ttu-id="9d3c1-107">Ajustez la taille de la fenêtre pour faciliter l’utilisation de la Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-107">Adjust the size of the window to make it easier to use the Workflow Designer.</span></span> <span data-ttu-id="9d3c1-108">Pour ce faire, sélectionnez **MainWindow** dans le concepteur, appuyez sur F4 pour afficher la fenêtre **Propriétés** , puis, dans la section **disposition** , affectez à la **largeur** la valeur 600 et à la **hauteur** la valeur 350.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-108">To do this, select **MainWindow** in the designer, press F4 to display the **Properties** window, and, in the **Layout** section there, set the **Width** to a value of 600 and the **Height** to a value of 350.</span></span>

3. <span data-ttu-id="9d3c1-109">Définissez le nom de la grille en sélectionnant le panneau **grille** dans le concepteur (cliquez sur la zone à l’intérieur de **MainWindow**) et en définissant la propriété **Name** en haut de la fenêtre **Propriétés** sur « grid1 ».</span><span class="sxs-lookup"><span data-stu-id="9d3c1-109">Set the grid name by selecting the **Grid** panel in the designer (click the box inside the **MainWindow**) and setting the **Name** property at the top of the **Properties** window to "grid1".</span></span>

4. <span data-ttu-id="9d3c1-110">Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection ( **...** ) en regard de la propriété `ColumnDefinitions` pour ouvrir la boîte de dialogue **éditeur de collections** .</span><span class="sxs-lookup"><span data-stu-id="9d3c1-110">In the **Properties** window, click the ellipsis (**…**) next to the `ColumnDefinitions` property to open the **Collection Editor** dialog box.</span></span>

5. <span data-ttu-id="9d3c1-111">Dans la boîte de dialogue **éditeur de collection** , cliquez trois fois sur le bouton **Ajouter** pour insérer trois colonnes dans la mise en page.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-111">In the **Collection Editor** dialog box, click the **Add** button three times to insert three columns into the layout.</span></span> <span data-ttu-id="9d3c1-112">La première colonne contient la **boîte à outils**, la deuxième héberge la concepteur de flux de travail, et la troisième colonne est utilisée pour l’inspecteur de propriété.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-112">The first column will contain the **Toolbox**, the second column will host the Workflow Designer, and the third column will be used for the property inspector.</span></span>

6. <span data-ttu-id="9d3c1-113">Affectez à la propriété `Width` de la colonne Middle la valeur « 4 \* ».</span><span class="sxs-lookup"><span data-stu-id="9d3c1-113">Set the `Width` property of the middle column to the value "4\*".</span></span>

7. <span data-ttu-id="9d3c1-114">Cliquez sur **OK** pour enregistrer les modifications.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-114">Click **OK** to save the changes.</span></span> <span data-ttu-id="9d3c1-115">Le code XAML suivant est ajouté à votre fichier *MainWindow. Xaml* :</span><span class="sxs-lookup"><span data-stu-id="9d3c1-115">The following XAML is added to your *MainWindow.xaml* file:</span></span>

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. <span data-ttu-id="9d3c1-116">Dans **Explorateur de solutions**, cliquez avec le bouton droit sur *MainWindow. Xaml* et sélectionnez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-116">In **Solution Explorer**, right-click *MainWindow.xaml* and select **View Code**.</span></span> <span data-ttu-id="9d3c1-117">Modifiez le code en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="9d3c1-117">Modify the code by following these steps:</span></span>

    1. <span data-ttu-id="9d3c1-118">Ajoutez les espaces de noms suivants :</span><span class="sxs-lookup"><span data-stu-id="9d3c1-118">Add the following namespaces:</span></span>

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. <span data-ttu-id="9d3c1-119">Pour déclarer un champ de membre privé pour contenir une instance du <xref:System.Activities.Presentation.WorkflowDesigner>, ajoutez le code suivant à la classe `MainWindow` :</span><span class="sxs-lookup"><span data-stu-id="9d3c1-119">To declare a private member field to hold an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, add the following code to the `MainWindow` class:</span></span>

        ```csharp
        public partial class MainWindow : Window
        {
            private WorkflowDesigner wd;

            public MainWindow()
            {
                InitializeComponent();
            }
        }
        ```

    3. <span data-ttu-id="9d3c1-120">Ajoutez la méthode `AddDesigner` suivante à la classe `MainWindow`.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-120">Add the following `AddDesigner` method to the `MainWindow` class.</span></span> <span data-ttu-id="9d3c1-121">L’implémentation crée une instance du <xref:System.Activities.Presentation.WorkflowDesigner>, y ajoute une activité de <xref:System.Activities.Statements.Sequence> et la place dans la colonne centrale de la **grille**grid1.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-121">The implementation creates an instance of the <xref:System.Activities.Presentation.WorkflowDesigner>, adds a <xref:System.Activities.Statements.Sequence> activity to it, and places it in middle column of the grid1 **Grid**.</span></span>

        ```csharp
        private void AddDesigner()
        {
            // Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            // Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            // Load a new Sequence as default.
            this.wd.Load(new Sequence());

            // Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. <span data-ttu-id="9d3c1-122">Pour ajouter la prise en charge du concepteur pour toutes les activités intégrées, enregistrez les métadonnées du concepteur.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-122">Register the designer metadata to add designer support for all the  built-in activities.</span></span> <span data-ttu-id="9d3c1-123">Cela vous permet de déplacer des activités de la boîte à outils vers l’activité d' <xref:System.Activities.Statements.Sequence> d’origine dans le Concepteur de flux de travail.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-123">This enables you to drop activities from the toolbox onto the original <xref:System.Activities.Statements.Sequence> activity in the Workflow Designer.</span></span> <span data-ttu-id="9d3c1-124">Pour ce faire, ajoutez la méthode `RegisterMetadata` à la classe `MainWindow` :</span><span class="sxs-lookup"><span data-stu-id="9d3c1-124">To do this, add the `RegisterMetadata` method to the `MainWindow` class:</span></span>

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        <span data-ttu-id="9d3c1-125">Pour plus d’informations sur l’inscription des concepteurs d’activités, consultez [Comment : créer un concepteur d’activités personnalisées](how-to-create-a-custom-activity-designer.md).</span><span class="sxs-lookup"><span data-stu-id="9d3c1-125">For more information about registering activity designers, see [How to: Create a Custom Activity Designer](how-to-create-a-custom-activity-designer.md).</span></span>

    5. <span data-ttu-id="9d3c1-126">Dans le constructeur de classes `MainWindow`, ajoutez des appels aux méthodes précédemment déclarées pour enregistrer les métadonnées dans le but de la prise en charge du concepteur et pour créer l'objet <xref:System.Activities.Presentation.WorkflowDesigner>.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-126">In the `MainWindow` class constructor, add calls to the methods declared previously to register the metadata for designer support and to create the <xref:System.Activities.Presentation.WorkflowDesigner>.</span></span>

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata.
            RegisterMetadata();

            // Add the WFF Designer.
            AddDesigner();
        }
        ```

        > [!NOTE]
        > <span data-ttu-id="9d3c1-127">La méthode `RegisterMetadata` enregistre les métadonnées du concepteur relatives aux activités intégrées, dont l'activité <xref:System.Activities.Statements.Sequence>.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-127">The `RegisterMetadata` method registers the designer metadata of built-in activities including the <xref:System.Activities.Statements.Sequence> activity.</span></span> <span data-ttu-id="9d3c1-128">Étant donné que la méthode `AddDesigner` utilise l'activité <xref:System.Activities.Statements.Sequence>, la méthode `RegisterMetadata` doit être appelée en premier.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-128">Because the `AddDesigner` method uses the <xref:System.Activities.Statements.Sequence> activity, the `RegisterMetadata` method must be called first.</span></span>

9. <span data-ttu-id="9d3c1-129">Appuyez sur <kbd>F5</kbd> pour générer et exécuter la solution.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-129">Press <kbd>F5</kbd> to build and run the solution.</span></span>

10. <span data-ttu-id="9d3c1-130">Consultez [tâche 3 : créer les volets boîte à outils et PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) pour savoir comment ajouter la prise en charge de la **boîte à outils** et de **PropertyGrid** à votre concepteur de workflow réhébergé.</span><span class="sxs-lookup"><span data-stu-id="9d3c1-130">See [Task 3: Create the Toolbox and PropertyGrid Panes](task-3-create-the-toolbox-and-propertygrid-panes.md) to learn how to add **Toolbox** and **PropertyGrid** support to your rehosted workflow designer.</span></span>

## <a name="see-also"></a><span data-ttu-id="9d3c1-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d3c1-131">See also</span></span>

- [<span data-ttu-id="9d3c1-132">Réhébergement du concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="9d3c1-132">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="9d3c1-133">Tâche 1 : Créer une nouvelle application Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="9d3c1-133">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="9d3c1-134">Tâche 3 : Créer les volets Toolbox et PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="9d3c1-134">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)
