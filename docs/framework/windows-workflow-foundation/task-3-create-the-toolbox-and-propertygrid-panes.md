---
title: 'Tâche 3 : créer les volets de PropertyGrid et boîte à outils'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 402a25c1cb82c245afa94f58cefc180515622ea9
ms.sourcegitcommit: 992f80328b51b165051c42ff5330788627abe973
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/11/2019
ms.locfileid: "72275861"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a><span data-ttu-id="04986-102">Tâche 3 : créer les volets de PropertyGrid et boîte à outils</span><span class="sxs-lookup"><span data-stu-id="04986-102">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>

<span data-ttu-id="04986-103">Dans cette tâche, vous allez créer les volets **boîte à outils** et **PropertyGrid** et les ajouter au [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]réhébergé.</span><span class="sxs-lookup"><span data-stu-id="04986-103">In this task, you will create the **Toolbox** and **PropertyGrid** panes and add them to the rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span>

<span data-ttu-id="04986-104">Pour référence, le code qui doit se trouver dans le fichier MainWindow.xaml.cs après avoir effectué les trois tâches du [réhébergement de la série concepteur de flux de travail](rehosting-the-workflow-designer.md) de rubriques est fourni à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="04986-104">For reference, the code that should be in the MainWindow.xaml.cs file after completing the three tasks in the [Rehosting the Workflow Designer](rehosting-the-workflow-designer.md) series of topics is provided at the end of this topic.</span></span>

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a><span data-ttu-id="04986-105">Pour créer la boîte à outils et l'ajouter à la grille</span><span class="sxs-lookup"><span data-stu-id="04986-105">To create the Toolbox and add it to the grid</span></span>

1. <span data-ttu-id="04986-106">Ouvrez le projet HostingApplication que vous avez obtenu en suivant la procédure décrite dans [tâche 2 : héberger le concepteur de flux de travail](task-2-host-the-workflow-designer.md).</span><span class="sxs-lookup"><span data-stu-id="04986-106">Open the HostingApplication project you obtained by following the procedure described in [Task 2: Host the Workflow Designer](task-2-host-the-workflow-designer.md).</span></span>

2. <span data-ttu-id="04986-107">Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier *MainWindow. Xaml* et sélectionnez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="04986-107">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

3. <span data-ttu-id="04986-108">Ajoutez une méthode `GetToolboxControl` à la classe `MainWindow` qui crée un <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, ajoute une nouvelle catégorie de **boîte à** outils à la **boîte à outils**et affecte les types d’activité <xref:System.Activities.Statements.Assign> et <xref:System.Activities.Statements.Sequence> à cette catégorie.</span><span class="sxs-lookup"><span data-stu-id="04986-108">Add a `GetToolboxControl` method to the `MainWindow` class that creates a <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, adds a new **Toolbox** category to the **Toolbox**, and assigns the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activity types to that category.</span></span>

    ```csharp
    private ToolboxControl GetToolboxControl()
    {
        // Create the ToolBoxControl.
        var ctrl = new ToolboxControl();

        // Create a category.
        var category = new ToolboxCategory("category1");

        // Create Toolbox items.
        var tool1 =
            new ToolboxItemWrapper("System.Activities.Statements.Assign",
            typeof(Assign).Assembly.FullName, null, "Assign");

        var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
            typeof(Sequence).Assembly.FullName, null, "Sequence");

        // Add the Toolbox items to the category.
        category.Add(tool1);
        category.Add(tool2);

        // Add the category to the ToolBox control.
        ctrl.Categories.Add(category);
        return ctrl;
    }
    ```

4. <span data-ttu-id="04986-109">Ajoutez une méthode de `AddToolbox` privée à la classe `MainWindow` qui place la **boîte à outils** dans la colonne de gauche de la grille.</span><span class="sxs-lookup"><span data-stu-id="04986-109">Add a private `AddToolbox` method to the `MainWindow` class that places the **Toolbox** in the left column on the grid.</span></span>

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. <span data-ttu-id="04986-110">Ajoutez un appel à la méthode `AddToolBox` dans le `MainWindow()` constructeur de classe, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="04986-110">Add a call to the `AddToolBox` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. <span data-ttu-id="04986-111">Appuyez sur <kbd>F5</kbd> pour générer et exécuter votre solution.</span><span class="sxs-lookup"><span data-stu-id="04986-111">Press <kbd>F5</kbd> to build and run your solution.</span></span> <span data-ttu-id="04986-112">La **boîte à outils** contenant les activités <xref:System.Activities.Statements.Assign> et <xref:System.Activities.Statements.Sequence> doit être affichée.</span><span class="sxs-lookup"><span data-stu-id="04986-112">The **Toolbox** containing the <xref:System.Activities.Statements.Assign> and <xref:System.Activities.Statements.Sequence> activities should be displayed.</span></span>

## <a name="to-create-the-propertygrid"></a><span data-ttu-id="04986-113">Pour créer PropertyGrid</span><span class="sxs-lookup"><span data-stu-id="04986-113">To create the PropertyGrid</span></span>

1. <span data-ttu-id="04986-114">Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier *MainWindow. Xaml* et sélectionnez **afficher le code**.</span><span class="sxs-lookup"><span data-stu-id="04986-114">In the **Solution Explorer** pane, right-click the *MainWindow.xaml* file and select **View Code**.</span></span>

2. <span data-ttu-id="04986-115">Ajoutez la méthode `AddPropertyInspector` à la classe `MainWindow` pour placer le volet **PropertyGrid** dans la colonne la plus à droite de la grille :</span><span class="sxs-lookup"><span data-stu-id="04986-115">Add the `AddPropertyInspector` method to the `MainWindow` class to place the **PropertyGrid** pane in the rightmost column on the grid:</span></span>

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. <span data-ttu-id="04986-116">Ajoutez un appel à la méthode `AddPropertyInspector` dans le `MainWindow()` constructeur de classe, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="04986-116">Add a call to the `AddPropertyInspector` method in the `MainWindow()` class constructor as shown in the following code:</span></span>

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();
        this.AddToolBox();

        this.AddPropertyInspector();
    }
    ```

4. <span data-ttu-id="04986-117">Appuyez sur <kbd>F5</kbd> pour générer et exécuter la solution.</span><span class="sxs-lookup"><span data-stu-id="04986-117">Press <kbd>F5</kbd> to build and run the solution.</span></span> <span data-ttu-id="04986-118">La **boîte à outils**, la zone de conception de workflow et les volets **PropertyGrid** doivent tous être affichés, et lorsque vous faites glisser une activité de <xref:System.Activities.Statements.Assign> ou une activité de <xref:System.Activities.Statements.Sequence> sur la zone de conception, la grille des propriétés doit être mise à jour en fonction de l’activité en surbrillance.</span><span class="sxs-lookup"><span data-stu-id="04986-118">The **Toolbox**, workflow design canvas, and **PropertyGrid** panes should all be displayed, and when you drag an <xref:System.Activities.Statements.Assign> activity or a <xref:System.Activities.Statements.Sequence> activity onto the design canvas, the property grid should update depending on the highlighted activity.</span></span>

## <a name="example"></a><span data-ttu-id="04986-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="04986-119">Example</span></span>

<span data-ttu-id="04986-120">Le fichier *MainWindow.Xaml.cs* doit maintenant contenir le code suivant :</span><span class="sxs-lookup"><span data-stu-id="04986-120">The *MainWindow.xaml.cs* file should now contain the following code:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Documents;
using System.Windows.Input;
using System.Windows.Media;
using System.Windows.Media.Imaging;
using System.Windows.Navigation;
using System.Windows.Shapes;
// dlls added.
using System.Activities;
using System.Activities.Core.Presentation;
using System.Activities.Presentation;
using System.Activities.Presentation.Metadata;
using System.Activities.Presentation.Toolbox;
using System.Activities.Statements;
using System.ComponentModel;

namespace HostingApplication
{
    /// <summary>
    /// Interaction logic for MainWindow.xaml
    /// </summary>
    public partial class MainWindow : Window
    {
        private WorkflowDesigner wd;

        public MainWindow()
        {
            InitializeComponent();
            RegisterMetadata();
            AddDesigner();
            this.AddToolBox();
            this.AddPropertyInspector();
        }

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

        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }

        private ToolboxControl GetToolboxControl()
        {
            // Create the ToolBoxControl.
            var ctrl = new ToolboxControl();

            // Create a category.
            var category = new ToolboxCategory("category1");

            // Create Toolbox items.
            var tool1 =
                new ToolboxItemWrapper("System.Activities.Statements.Assign",
                typeof(Assign).Assembly.FullName, null, "Assign");

            var tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",
                typeof(Sequence).Assembly.FullName, null, "Sequence");

            // Add the Toolbox items to the category.
            category.Add(tool1);
            category.Add(tool2);

            // Add the category to the ToolBox control.
            ctrl.Categories.Add(category);
            return ctrl;
        }

        private void AddToolBox()
        {
            ToolboxControl tc = GetToolboxControl();
            Grid.SetColumn(tc, 0);
            grid1.Children.Add(tc);
        }

        private void AddPropertyInspector()
        {
            Grid.SetColumn(wd.PropertyInspectorView, 2);
            grid1.Children.Add(wd.PropertyInspectorView);
        }

    }
}
```

## <a name="see-also"></a><span data-ttu-id="04986-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04986-121">See also</span></span>

- [<span data-ttu-id="04986-122">Réhébergement du concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="04986-122">Rehosting the Workflow Designer</span></span>](rehosting-the-workflow-designer.md)
- [<span data-ttu-id="04986-123">Tâche 1 : Créer une nouvelle application Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="04986-123">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)
- [<span data-ttu-id="04986-124">Tâche 2 : Héberger le concepteur de flux de travail</span><span class="sxs-lookup"><span data-stu-id="04986-124">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)
