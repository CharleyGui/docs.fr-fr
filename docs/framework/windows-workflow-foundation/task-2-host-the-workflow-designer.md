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
# <a name="task-2-host-the-workflow-designer"></a>Tâche 2 : héberger le Workflow Designer

Cette rubrique décrit la procédure d’hébergement d’une instance de Windows Concepteur de flux de travail dans une application Windows Presentation Foundation (WPF).

La procédure configure le contrôle de **grille** qui contient le concepteur, crée par programmation une instance du <xref:System.Activities.Presentation.WorkflowDesigner> qui contient une activité de <xref:System.Activities.Statements.Sequence> par défaut, inscrit les métadonnées du concepteur pour fournir la prise en charge du concepteur pour toutes les activités intégrées et héberge les concepteur de flux de travail dans l’application WPF.

## <a name="to-host-the-workflow-designer"></a>Pour héberger le concepteur de workflow

1. Ouvrez le projet HostingApplication que vous avez créé dans [tâche 1 : créer une application de Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).

2. Ajustez la taille de la fenêtre pour faciliter l’utilisation de la Concepteur de flux de travail. Pour ce faire, sélectionnez **MainWindow** dans le concepteur, appuyez sur F4 pour afficher la fenêtre **Propriétés** , puis, dans la section **disposition** , affectez à la **largeur** la valeur 600 et à la **hauteur** la valeur 350.

3. Définissez le nom de la grille en sélectionnant le panneau **grille** dans le concepteur (cliquez sur la zone à l’intérieur de **MainWindow**) et en définissant la propriété **Name** en haut de la fenêtre **Propriétés** sur « grid1 ».

4. Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection ( **...** ) en regard de la propriété `ColumnDefinitions` pour ouvrir la boîte de dialogue **éditeur de collections** .

5. Dans la boîte de dialogue **éditeur de collection** , cliquez trois fois sur le bouton **Ajouter** pour insérer trois colonnes dans la mise en page. La première colonne contient la **boîte à outils**, la deuxième héberge la concepteur de flux de travail, et la troisième colonne est utilisée pour l’inspecteur de propriété.

6. Affectez à la propriété `Width` de la colonne Middle la valeur « 4 * ».

7. Cliquez sur **OK** pour enregistrer les modifications. Le code XAML suivant est ajouté à votre fichier *MainWindow. Xaml* :

    ```xaml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur *MainWindow. Xaml* et sélectionnez **afficher le code**. Modifiez le code en procédant comme suit :

    1. Ajoutez les espaces de noms suivants :

        ```csharp
        using System.Activities;
        using System.Activities.Core.Presentation;
        using System.Activities.Presentation;
        using System.Activities.Presentation.Metadata;
        using System.Activities.Presentation.Toolbox;
        using System.Activities.Statements;
        using System.ComponentModel;
        ```

    2. Pour déclarer un champ de membre privé pour contenir une instance du <xref:System.Activities.Presentation.WorkflowDesigner>, ajoutez le code suivant à la classe `MainWindow` :

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

    3. Ajoutez la méthode `AddDesigner` suivante à la classe `MainWindow`. L’implémentation crée une instance du <xref:System.Activities.Presentation.WorkflowDesigner>, y ajoute une activité de <xref:System.Activities.Statements.Sequence> et la place dans la colonne centrale de la **grille**grid1.

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

    4. Pour ajouter la prise en charge du concepteur pour toutes les activités intégrées, enregistrez les métadonnées du concepteur. Cela vous permet de déplacer des activités de la boîte à outils vers l’activité d' <xref:System.Activities.Statements.Sequence> d’origine dans le Concepteur de flux de travail. Pour ce faire, ajoutez la méthode `RegisterMetadata` à la classe `MainWindow` :

        ```csharp
        private void RegisterMetadata()
        {
            var dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Pour plus d’informations sur l’inscription des concepteurs d’activités, consultez [Comment : créer un concepteur d’activités personnalisées](how-to-create-a-custom-activity-designer.md).

    5. Dans le constructeur de classes `MainWindow`, ajoutez des appels aux méthodes précédemment déclarées pour enregistrer les métadonnées dans le but de la prise en charge du concepteur et pour créer l'objet <xref:System.Activities.Presentation.WorkflowDesigner>.

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
        > La méthode `RegisterMetadata` enregistre les métadonnées du concepteur relatives aux activités intégrées, dont l'activité <xref:System.Activities.Statements.Sequence>. Étant donné que la méthode `AddDesigner` utilise l'activité <xref:System.Activities.Statements.Sequence>, la méthode `RegisterMetadata` doit être appelée en premier.

9. Appuyez sur <kbd>F5</kbd> pour générer et exécuter la solution.

10. Consultez [tâche 3 : créer les volets boîte à outils et PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) pour savoir comment ajouter la prise en charge de la **boîte à outils** et de **PropertyGrid** à votre concepteur de workflow réhébergé.

## <a name="see-also"></a>Voir aussi

- [Réhébergement du concepteur de flux de travail](rehosting-the-workflow-designer.md)
- [Tâche 1 : Créer une nouvelle application Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Tâche 3 : Créer les volets Toolbox et PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md)
