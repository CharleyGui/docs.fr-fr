---
title: 'Tâche 2 : héberger le concepteur de flux de travail'
ms.date: 03/30/2017
ms.assetid: 0a29b138-270d-4846-b78e-2b875e34e501
ms.openlocfilehash: 553a02732e08fa148ffdee250df0305deb8e63b7
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169998"
---
# <a name="task-2-host-the-workflow-designer"></a>Tâche 2 : héberger le concepteur de flux de travail
Cette rubrique décrit la procédure pour l’hébergement d’une instance de la [!INCLUDE[wfd1](../../../includes/wfd1-md.md)] dans une application Windows Presentation Foundation (WPF).  
  
 La procédure configure le **grille** contrôle qui contient le concepteur, crée par programmation une instance de la <xref:System.Activities.Presentation.WorkflowDesigner> qui contient une valeur par défaut <xref:System.Activities.Statements.Sequence> activité, enregistre les métadonnées de concepteur pour fournir prise en charge de concepteur pour des hôtes et des activités intégrées tout le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)] dans l’application WPF.  
  
### <a name="to-host-the-workflow-designer"></a>Pour héberger le concepteur de workflow  
  
1. Ouvrez le projet hostingapplication que vous avez créé dans [tâche 1 : Créer une nouvelle Application Windows Presentation Foundation](task-1-create-a-new-wpf-app.md).  
  
2. Pour faciliter l'utilisation du [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], ajustez la taille de la fenêtre. Pour ce faire, sélectionnez **MainWindow** dans le concepteur, appuyez sur F4 pour afficher la **propriétés** fenêtre, puis, dans le **disposition** section il, définissez le **delalargeur** à une valeur de 600 et la **hauteur** à une valeur de 350.  
  
3. Définir le nom de la grille en sélectionnant le **grille** panneau dans le concepteur (cliquez sur la zone à l’intérieur de la **MainWindow**) et en définissant le **nom** propriété en haut de la  **Propriétés** fenêtre valeur « grid1 ».  
  
4. Dans le **propriétés** fenêtre, cliquez sur le bouton de sélection ( **...** ) à côté du `ColumnDefinitions` propriété pour ouvrir le **éditeur de collections** boîte de dialogue.  
  
5. Dans le **éditeur de collections** boîte de dialogue, cliquez sur le **ajouter** bouton trois fois pour insérer trois colonnes dans la disposition. La première colonne contiendra la **boîte à outils**, la deuxième colonne hébergera le [!INCLUDE[wfd2](../../../includes/wfd2-md.md)], et la troisième colonne sera utilisée pour l’inspecteur de propriété.  
  
6. Définir le `Width` propriété de la colonne du milieu à la valeur « 4 * ».  
  
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
  
8. Dans **l’Explorateur de solutions**, cliquez sur MainWindow.xaml et sélectionnez **afficher le Code**. Modifiez le code en procédant comme suit :  
  
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
  
    3. Ajoutez la méthode `AddDesigner` suivante à la classe `MainWindow`. L’implémentation crée une instance de la <xref:System.Activities.Presentation.WorkflowDesigner>, ajoute un <xref:System.Activities.Statements.Sequence> activité et le place dans la colonne du milieu de la grid1 **grille**.  
  
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
  
         Pour plus d’informations sur l’inscription des concepteurs d’activités, consultez [Comment : Créer un concepteur d’activités personnalisées](how-to-create-a-custom-activity-designer.md).  
  
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
        >  La méthode `RegisterMetadata` enregistre les métadonnées du concepteur relatives aux activités intégrées, dont l'activité <xref:System.Activities.Statements.Sequence>. Étant donné que la méthode `AddDesigner` utilise l'activité <xref:System.Activities.Statements.Sequence>, la méthode `RegisterMetadata` doit être appelée en premier.  
  
9. Pour générer et exécuter la solution, appuyez sur F5.  
  
10. Consultez [tâche 3 : Créer les volets Toolbox et PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md) pour savoir comment ajouter **boîte à outils** et **PropertyGrid** prennent en charge à votre Concepteur de workflow réhébergé.  
  
## <a name="see-also"></a>Voir aussi

- [Réhébergement du concepteur de flux de travail](rehosting-the-workflow-designer.md)
- [Tâche 1 : Créer une nouvelle Application Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Tâche 3 : Créer les volets Toolbox et PropertyGrid](task-3-create-the-toolbox-and-propertygrid-panes.md)
