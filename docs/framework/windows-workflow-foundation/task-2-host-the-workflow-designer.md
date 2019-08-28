---
title: 'Tâche 2 : héberger le concepteur de flux de travail'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 92c5fa347cc7a2c0088ab8f4fbdfddf25ffb83c1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70037868"
---
# <a name="task-2-host-the-workflow-designer"></a>Tâche 2 : héberger le concepteur de flux de travail

Cette rubrique décrit la procédure d’hébergement d’une instance de [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] dans une application Windows Presentation Foundation (WPF).

La procédure configure le contrôle **Grid** qui contient le concepteur, crée par programmation une instance du <xref:System.Activities.Presentation.WorkflowDesigner> qui contient une activité par défaut <xref:System.Activities.Statements.Sequence> , inscrit les métadonnées du concepteur pour fournir une prise en charge du concepteur pour toutes les les activités intégrées et héberge le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] dans l’application WPF.

### <a name="to-host-the-workflow-designer"></a>Pour héberger le concepteur de workflow

1. Ouvrez le projet HostingApplication que vous avez [créé dans la tâche 1: Créez une application](task-1-create-a-new-wpf-app.md)de Windows Presentation Foundation.

2. Pour faciliter l'utilisation du [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], ajustez la taille de la fenêtre. Pour ce faire, sélectionnez **MainWindow** dans le concepteur, appuyez sur F4 pour afficher la fenêtre **Propriétés** , puis, dans la section **disposition** , affectez à la **largeur** la valeur 600 et à la **hauteur** la valeur 350.

3. Définissez le nom de la grille en sélectionnant le panneau **grille** dans le concepteur (cliquez sur la zone à l’intérieur de **MainWindow**) et en définissant la propriété **Name** en haut de la fenêtre **Propriétés** sur «grid1».

4. Dans la fenêtre **Propriétés** , cliquez sur le bouton de sélection ( **...** ) `ColumnDefinitions` en regard de la propriété pour ouvrir la boîte de dialogue **éditeur de collection** .

5. Dans la boîte de dialogue **éditeur de collection** , cliquez trois fois sur le bouton **Ajouter** pour insérer trois colonnes dans la mise en page. La première colonne contient la **boîte à outils**, la deuxième héberge la [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], et la troisième colonne est utilisée pour l’inspecteur de propriété.

6. Affectez `Width` à la propriété de la colonne Middle la valeur «4 *».

7. Cliquez sur **OK** pour enregistrer les modifications. Le XAML suivant est ajouté à votre fichier MainWindow.xaml :

    ```xml
    <Grid Name="grid1">
        <Grid.ColumnDefinitions>
            <ColumnDefinition />
            <ColumnDefinition Width="4*" />
            <ColumnDefinition />
        </Grid.ColumnDefinitions>
    </Grid>
    ```

8. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur MainWindow. xaml et sélectionnez **afficher le code**. Modifiez le code en procédant comme suit :

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

    2. Pour déclarer un champ de membre privé devant contenir une instance de <xref:System.Activities.Presentation.WorkflowDesigner>, ajoutez le code suivant à la classe `MainWindow`.

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

    3. Ajoutez la méthode `AddDesigner` suivante à la classe `MainWindow`. L’implémentation crée une instance du <xref:System.Activities.Presentation.WorkflowDesigner>, lui ajoute une activité et la <xref:System.Activities.Statements.Sequence> place dans la colonne centrale de la **grille**grid1.

        ```csharp
        private void AddDesigner()
        {
            //Create an instance of WorkflowDesigner class.
            this.wd = new WorkflowDesigner();

            //Place the designer canvas in the middle column of the grid.
            Grid.SetColumn(this.wd.View, 1);

            //Load a new Sequence as default.
            this.wd.Load(new Sequence());

            //Add the designer canvas to the grid.
            grid1.Children.Add(this.wd.View);
        }
        ```

    4. Pour ajouter la prise en charge du concepteur pour toutes les activités intégrées, enregistrez les métadonnées du concepteur. Cela vous permet de déplacer des activités, de la boîte à outils vers l'activité <xref:System.Activities.Statements.Sequence> d'origine dans le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)]. Pour ce faire, ajoutez la méthode `RegisterMetadata` à la classe `MainWindow`.

        ```csharp
        private void RegisterMetadata()
        {
            DesignerMetadata dm = new DesignerMetadata();
            dm.Register();
        }
        ```

        Pour plus d’informations sur l’inscription des concepteurs d’activités, consultez [procédure: Créez un concepteur](how-to-create-a-custom-activity-designer.md)d’activités personnalisées.

    5. Dans le constructeur de classes `MainWindow`, ajoutez des appels aux méthodes précédemment déclarées pour enregistrer les métadonnées dans le but de la prise en charge du concepteur et pour créer l'objet <xref:System.Activities.Presentation.WorkflowDesigner>.

        ```csharp
        public MainWindow()
        {
            InitializeComponent();

            // Register the metadata
            RegisterMetadata();

            // Add the WFF Designer
            AddDesigner();
        }
        ```

        > [!NOTE]
        > La méthode `RegisterMetadata` enregistre les métadonnées du concepteur relatives aux activités intégrées, dont l'activité <xref:System.Activities.Statements.Sequence>. Étant donné que la méthode `AddDesigner` utilise l'activité <xref:System.Activities.Statements.Sequence>, la méthode `RegisterMetadata` doit être appelée en premier.

9. Pour générer et exécuter la solution, appuyez sur F5.

10. Voir [tâche 3: Créez les volets](task-3-create-the-toolbox-and-propertygrid-panes.md) boîte à outils et PropertyGrid pour savoir comment ajouter la prise en charge de la **boîte à outils** et de **PropertyGrid** à votre concepteur de workflow réhébergé.

## <a name="see-also"></a>Voir aussi

- [Réhébergement du concepteur de flux de travail](rehosting-the-workflow-designer.md)
- [Tâche 1: Créer une application de Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Tâche 3: Créer les volets boîte à outils et PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md)
