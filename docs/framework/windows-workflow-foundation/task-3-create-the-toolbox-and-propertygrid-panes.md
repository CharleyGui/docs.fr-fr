---
title: 'Tâche 3 : créer les volets Toolbox et PropertyGrid'
ms.date: 03/30/2017
ms.assetid: 72c1546a-eed5-4f0f-a616-719a163414f4
ms.openlocfilehash: 6339969c52a5c4eedfb0e89eebdc982ca3fe6686
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988709"
---
# <a name="task-3-create-the-toolbox-and-propertygrid-panes"></a>Tâche 3 : créer les volets Toolbox et PropertyGrid
Dans cette tâche, vous allez créer les volets **boîte à outils** et **PropertyGrid** et les ajouter au réhébergement [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].  
  
 Pour référence, le code qui doit se trouver dans le fichier MainWindow.xaml.cs après avoir effectué les trois tâches du [réhébergement de la série concepteur de flux de travail](rehosting-the-workflow-designer.md) de rubriques est fourni à la fin de cette rubrique.  
  
### <a name="to-create-the-toolbox-and-add-it-to-the-grid"></a>Pour créer la boîte à outils et l'ajouter à la grille  
  
1. Ouvrez le projet HostingApplication que vous avez obtenu en suivant la procédure [décrite dans tâche 2 : Hébergez le](task-2-host-the-workflow-designer.md)concepteur de flux de travail.  
  
2. Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier MainWindow. xaml et sélectionnez **afficher le code**.  
  
3. Ajoutez une `GetToolboxControl` méthode à la `MainWindow` classe qui crée un <xref:System.Activities.Presentation.Toolbox.ToolboxControl>, ajoute une nouvelle catégorie de **boîte à** outils à la **boîte à outils**et <xref:System.Activities.Statements.Sequence> assigne les <xref:System.Activities.Statements.Assign> types d’activité et à cette catégorie.  
  
    ```csharp  
    private ToolboxControl GetToolboxControl()  
    {  
        // Create the ToolBoxControl.  
        ToolboxControl ctrl = new ToolboxControl();  
  
        // Create a category.  
        ToolboxCategory category = new ToolboxCategory("category1");  
  
        // Create Toolbox items.  
        ToolboxItemWrapper tool1 =   
            new ToolboxItemWrapper("System.Activities.Statements.Assign",   
            typeof(Assign).Assembly.FullName, null, "Assign");  
  
        ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",   
            typeof(Sequence).Assembly.FullName, null, "Sequence");  
  
        // Add the Toolbox items to the category.  
        category.Add(tool1);  
        category.Add(tool2);  
  
        // Add the category to the ToolBox control.  
        ctrl.Categories.Add(category);  
        return ctrl;  
    }  
    ```  
  
4. Ajoutez une méthode `AddToolbox` privée à la `MainWindow` classe qui place la **boîte à outils** dans la colonne de gauche de la grille.  
  
    ```csharp  
    private void AddToolBox()  
    {  
        ToolboxControl tc = GetToolboxControl();  
        Grid.SetColumn(tc, 0);  
        grid1.Children.Add(tc);  
    }  
    ```  
  
5. Ajoutez un appel à la méthode `AddToolBox` dans le constructeur de classe `MainWindow()`, comme illustré dans le code suivant.  
  
    ```csharp  
    public MainWindow()  
    {  
        InitializeComponent();  
        this.RegisterMetadata();  
        this.AddDesigner();  
  
        this.AddToolBox();  
    }  
    ```  
  
6. Appuyez sur F5 pour générer et exécuter votre solution. La **boîte à outils** <xref:System.Activities.Statements.Assign> contenant <xref:System.Activities.Statements.Sequence> les activités et doit être affichée.  
  
### <a name="to-create-the-propertygrid"></a>Pour créer PropertyGrid  
  
1. Dans le volet **Explorateur de solutions** , cliquez avec le bouton droit sur le fichier MainWindow. xaml et sélectionnez **afficher le code**.  
  
2. Ajoutez la `AddPropertyInspector` méthode à la `MainWindow` classe pour placer le volet **PropertyGrid** dans la colonne la plus à droite sur la grille.  
  
    ```csharp  
    private void AddPropertyInspector()  
    {  
        Grid.SetColumn(wd.PropertyInspectorView, 2);  
        grid1.Children.Add(wd.PropertyInspectorView);              
    }  
    ```  
  
3. Ajoutez un appel à la méthode `AddPropertyInspector` dans le constructeur de classe `MainWindow()`, comme illustré dans le code suivant.  
  
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
  
4. Pour générer et exécuter la solution, appuyez sur F5. La **boîte à outils**, la zone de conception de workflow et les volets **PropertyGrid** doivent tous être affichés et <xref:System.Activities.Statements.Assign> , lorsque vous <xref:System.Activities.Statements.Sequence> faites glisser une activité ou une activité sur la zone de conception, la grille des propriétés doit être mise à jour en fonction de activité en surbrillance.  
  
## <a name="example"></a>Exemples  
 Le fichier MainWindow.xaml.cs doit maintenant contenir le code suivant.  
  
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
//dlls added  
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
            //Create an instance of WorkflowDesigner class.  
            this.wd = new WorkflowDesigner();  
  
            //Place the designer canvas in the middle column of the grid.  
            Grid.SetColumn(this.wd.View, 1);  
  
            //Load a new Sequence as default.  
            this.wd.Load(new Sequence());  
  
            //Add the designer canvas to the grid.  
            grid1.Children.Add(this.wd.View);  
        }  
  
        private void RegisterMetadata()  
        {  
            DesignerMetadata dm = new DesignerMetadata();  
            dm.Register();  
        }  
  
        private ToolboxControl GetToolboxControl()  
        {  
            // Create the ToolBoxControl.  
            ToolboxControl ctrl = new ToolboxControl();  
  
            // Create a category.  
            ToolboxCategory category = new ToolboxCategory("category1");  
  
            // Create Toolbox items.  
            ToolboxItemWrapper tool1 =  
                new ToolboxItemWrapper("System.Activities.Statements.Assign",  
                typeof(Assign).Assembly.FullName, null, "Assign");  
  
            ToolboxItemWrapper tool2 = new ToolboxItemWrapper("System.Activities.Statements.Sequence",  
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
- [Tâche 1 : Créer une application de Windows Presentation Foundation](task-1-create-a-new-wpf-app.md)
- [Tâche 2 : Héberger le Concepteur de flux de travail](task-2-host-the-workflow-designer.md)
