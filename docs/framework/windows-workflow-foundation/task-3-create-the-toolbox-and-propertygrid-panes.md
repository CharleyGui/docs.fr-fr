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
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Tâche 3 : créer les volets de PropertyGrid et boîte à outils

Dans cette tâche, vous allez créer les volets **boîte à outils** et **PropertyGrid** et les ajouter au [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]réhébergé.

Pour référence, le code qui doit se trouver dans le fichier MainWindow.xaml.cs après avoir effectué les trois tâches du [réhébergement de la série concepteur de flux de travail](rehosting-the-workflow-designer.md) de rubriques est fourni à la fin de cette rubrique.

## <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Pour créer la boîte à outils et l'ajouter à la grille

1. Ouvrez le projet HostingApplication que vous avez obtenu en suivant la procédure décrite dans [tâche 2 : héberger le concepteur de flux de travail](task-2-host-the-workflow-designer.md).

2. Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier *MainWindow. Xaml* et sélectionnez **afficher le code**.

3. Ajoutez une méthode `GetToolboxControl` à la classe `MainWindow` qui crée un <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, ajoute une nouvelle catégorie de **boîte à** outils à la **boîte à outils**et affecte les types d’activité <xref:System.Activities.Statements.Assign> et <xref:System.Activities.Statements.Sequence> à cette catégorie.

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

4. Ajoutez une méthode de `AddToolbox` privée à la classe `MainWindow` qui place la **boîte à outils** dans la colonne de gauche de la grille.

    ```csharp
    private void AddToolBox()
    {
        ToolboxControl tc = GetToolboxControl();
        Grid.SetColumn(tc, 0);
        grid1.Children.Add(tc);
    }
    ```

5. Ajoutez un appel à la méthode `AddToolBox` dans le `MainWindow()` constructeur de classe, comme indiqué dans le code suivant :

    ```csharp
    public MainWindow()
    {
        InitializeComponent();
        this.RegisterMetadata();
        this.AddDesigner();

        this.AddToolBox();
    }
    ```

6. Appuyez sur <kbd>F5</kbd> pour générer et exécuter votre solution. La **boîte à outils** contenant les activités <xref:System.Activities.Statements.Assign> et <xref:System.Activities.Statements.Sequence> doit être affichée.

## <a name="to-create-the-propertygrid"></a>Pour créer PropertyGrid

1. Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier *MainWindow. Xaml* et sélectionnez **afficher le code**.

2. Ajoutez la méthode `AddPropertyInspector` à la classe `MainWindow` pour placer le volet **PropertyGrid** dans la colonne la plus à droite de la grille :

    ```csharp
    private void AddPropertyInspector()
    {
        Grid.SetColumn(wd.PropertyInspectorView, 2);
        grid1.Children.Add(wd.PropertyInspectorView);
    }
    ```

3. Ajoutez un appel à la méthode `AddPropertyInspector` dans le `MainWindow()` constructeur de classe, comme indiqué dans le code suivant :

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

4. Appuyez sur <kbd>F5</kbd> pour générer et exécuter la solution. La **boîte à outils**, la zone de conception de workflow et les volets **PropertyGrid** doivent tous être affichés, et lorsque vous faites glisser une activité de <xref:System.Activities.Statements.Assign> ou une activité de <xref:System.Activities.Statements.Sequence> sur la zone de conception, la grille des propriétés doit être mise à jour en fonction de l’activité en surbrillance.

## <a name="example"></a>Exemple

Le fichier *MainWindow.Xaml.cs* doit maintenant contenir le code suivant :

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

## <a name="see-also"></a>Voir aussi

- [Réhébergement du concepteur de flux de travail](rehosting-the-workflow-designer.md)
- [Tâche 1 : Créer une nouvelle application Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Tâche 2 : Héberger le concepteur de flux de travail](task-2-host-the-workflow-designer.md)
