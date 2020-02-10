---
title: 'Procédure pas à pas : liaison de données dans des applications hybrides'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hybrid applications [WPF interoperability]
- data binding [WPF interoperability]
ms.assetid: 18997e71-745a-4425-9c69-2cbce1d8669e
ms.openlocfilehash: 0d1e66a1277e6a04d2f49ac91691160f70fb56e4
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095071"
---
# <a name="walkthrough-binding-to-data-in-hybrid-applications"></a>Procédure pas à pas : liaison de données dans des applications hybrides

La liaison d’une source de données à un contrôle est essentielle pour permettre aux utilisateurs d’accéder aux données sous-jacentes, que vous utilisiez Windows Forms ou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Cette procédure pas à pas montre comment vous pouvez utiliser la liaison de données dans des applications hybrides qui incluent à la fois des contrôles Windows Forms et [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Cette procédure pas à pas décrit notamment les tâches suivantes :

- Création du projet

- Définition du modèle de données.

- Spécification de la disposition du formulaire.

- Spécification des liaisons de données.

- Affichage des données à l’aide de l’interopérabilité.

- Ajout de la source de données au projet.

- Liaison à la source de données.

Pour obtenir le code complet des tâches illustrées dans cette procédure pas à pas, consultez la rubrique [exemple de liaison de données dans des applications hybrides](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFWithWFAndDatabinding).

À l’issue de cette procédure, vous aurez une meilleure compréhension des fonctionnalités de liaison de données dans les applications hybrides.

## <a name="prerequisites"></a>Conditions préalables requises

Vous devez disposer des éléments suivants pour exécuter cette procédure pas à pas :

- Visual Studio.

- Accès à l’exemple de base de données Northwind s’exécutant sur Microsoft SQL Server.

## <a name="creating-the-project"></a>Création du projet

### <a name="to-create-and-set-up-the-project"></a>Pour créer et configurer le projet

1. Créez un projet d’application WPF nommé `WPFWithWFAndDatabinding`.

2. Dans l’Explorateur de solutions, ajoutez des références aux assemblys suivants.

    - WindowsFormsIntegration

    - System.Windows.Forms

3. Ouvrez MainWindow. xaml dans le Concepteur WPF.

4. Dans l’élément <xref:System.Windows.Window>, ajoutez le mappage d’espaces de noms Windows Forms suivant.

    ```xaml
    xmlns:wf="clr-namespace:System.Windows.Forms;assembly=System.Windows.Forms"
    ```

5. Nommez l’élément <xref:System.Windows.Controls.Grid> par défaut `mainGrid` en affectant la propriété <xref:System.Windows.FrameworkElement.Name%2A>.

     [!code-xaml[WPFWithWFAndDatabinding#8](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#8)]

## <a name="defining-the-data-template"></a>Définition du modèle de données

La liste principale des clients s’affiche dans un contrôle de <xref:System.Windows.Controls.ListBox>. L’exemple de code suivant définit un objet <xref:System.Windows.DataTemplate> nommé `ListItemsTemplate` qui contrôle l’arborescence d’éléments visuels du contrôle <xref:System.Windows.Controls.ListBox>. Cette <xref:System.Windows.DataTemplate> est assignée à la propriété <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> du contrôle <xref:System.Windows.Controls.ListBox>.

### <a name="to-define-the-data-template"></a>Pour définir le modèle de données

- Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#3)]

## <a name="specifying-the-form-layout"></a>Spécification de la disposition du formulaire

La disposition du formulaire est définie par une grille de trois lignes et trois colonnes. des contrôles de <xref:System.Windows.Controls.Label> sont fournis pour identifier chaque colonne dans la table Customers.

### <a name="to-set-up-the-grid-layout"></a>Pour configurer la disposition de la grille

- Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#4](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#4)]

### <a name="to-set-up-the-label-controls"></a>Pour configurer les contrôles Label

- Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#5](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#5)]

## <a name="specifying-data-bindings"></a>Spécification des liaisons de données

La liste principale des clients s’affiche dans un contrôle de <xref:System.Windows.Controls.ListBox>. Le `ListItemsTemplate` attaché lie un contrôle <xref:System.Windows.Controls.TextBlock> au champ `ContactName` de la base de données.

Les détails de chaque enregistrement de client s’affichent dans plusieurs contrôles de <xref:System.Windows.Controls.TextBox>.

### <a name="to-specify-data-bindings"></a>Pour spécifier des liaisons de données

- Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.

     La classe <xref:System.Windows.Data.Binding> lie les contrôles <xref:System.Windows.Controls.TextBox> aux champs appropriés dans la base de données.

     [!code-xaml[WPFWithWFAndDatabinding#6](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#6)]

## <a name="displaying-data-by-using-interoperation"></a>Affichage des données à l’aide de l’interopérabilité

Les commandes correspondant au client sélectionné s’affichent dans un contrôle de <xref:System.Windows.Forms.DataGridView?displayProperty=nameWithType> nommé `dataGridView1`. Le contrôle `dataGridView1` est lié à la source de données dans le fichier code-behind. Un contrôle <xref:System.Windows.Forms.Integration.WindowsFormsHost> est le parent de ce contrôle Windows Forms.

### <a name="to-display-data-in-the-datagridview-control"></a>Pour afficher des données dans le contrôle DataGridView

- Copiez le code XAML suivant dans la déclaration de l’élément <xref:System.Windows.Controls.Grid>.

     [!code-xaml[WPFWithWFAndDatabinding#7](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml#7)]

## <a name="adding-the-data-source-to-the-project"></a>Ajout de la source de données au projet

Avec Visual Studio, vous pouvez facilement ajouter une source de données à votre projet. Cette procédure ajoute un jeu de données fortement typé à votre projet. Plusieurs autres classes de prise en charge, comme les adaptateurs de table pour chacune des tables choisies, sont également ajoutées.

### <a name="to-add-the-data-source"></a>Pour ajouter la source de données

1. Dans le menu **données** , sélectionnez **Ajouter une nouvelle source de données**.

2. Dans l **'Assistant Configuration de source de données**, créez une connexion à la base de données Northwind à l’aide d’un jeu de données. Pour plus d'informations, consultez [How to: Connect to Data in a Database](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120)).

3. Lorsque l' **Assistant Configuration de source de données**vous y invite, enregistrez la chaîne de connexion en tant que `NorthwindConnectionString`.

4. Lorsque vous êtes invité à choisir vos objets de base de données, sélectionnez les tables `Customers` et `Orders`, puis nommez le jeu de données généré `NorthwindDataSet`.

## <a name="binding-to-the-data-source"></a>Liaison à la source de données

Le composant <xref:System.Windows.Forms.BindingSource?displayProperty=nameWithType> fournit une interface uniforme pour la source de données de l’application. La liaison à la source de données est implémentée dans le fichier code-behind.

### <a name="to-bind-to-the-data-source"></a>Pour effectuer la liaison à la source de données

1. Ouvrez le fichier code-behind nommé MainWindow.xaml.vb ou MainWindow.xaml.cs.

2. Copiez le code suivant dans la définition de classe `MainWindow`.

     Ce code déclare le composant <xref:System.Windows.Forms.BindingSource> et les classes d’assistance associées qui se connectent à la base de données.

     [!code-csharp[WPFWithWFAndDatabinding#11](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#11)]
     [!code-vb[WPFWithWFAndDatabinding#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#11)]

3. Copiez le code suivant dans le constructeur.

     Ce code crée et initialise le composant <xref:System.Windows.Forms.BindingSource>.

     [!code-csharp[WPFWithWFAndDatabinding#12](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#12)]
     [!code-vb[WPFWithWFAndDatabinding#12](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#12)]

4. Ouvrez MainWindow.xaml.

5. En Mode Création ou en mode XAML, sélectionnez l’élément <xref:System.Windows.Window>.

6. Dans l’Fenêtre Propriétés, cliquez sur l’onglet **événements** .

7. Double-cliquez sur l’événement <xref:System.Windows.FrameworkElement.Loaded>.

8. Copiez le code suivant dans le gestionnaire d’événements <xref:System.Windows.FrameworkElement.Loaded>.

     Ce code assigne le composant <xref:System.Windows.Forms.BindingSource> comme contexte de données et remplit les objets `Customers` et `Orders` adaptateur.

     [!code-csharp[WPFWithWFAndDatabinding#13](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#13)]
     [!code-vb[WPFWithWFAndDatabinding#13](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#13)]

9. Copiez le code suivant dans la définition de classe `MainWindow`.

     Cette méthode gère l’événement <xref:System.Windows.Data.CollectionView.CurrentChanged> et met à jour l’élément actuel de la liaison de données.

     [!code-csharp[WPFWithWFAndDatabinding#14](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFWithWFAndDatabinding/CSharp/WPFWithWFAndDatabinding/Window1.xaml.cs#14)]
     [!code-vb[WPFWithWFAndDatabinding#14](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFWithWFAndDatabinding/VisualBasic/WPFWithWFAndDatabinding/Window1.xaml.vb#14)]

10. Appuyez sur F5 pour générer et exécuter l’application.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Concevoir en XAML dans Visual Studio](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
- [Exemple de liaison de données dans des applications hybrides](https://github.com/microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/WPFWithWFAndDatabinding)
- [Procédure pas à pas : hébergement d'un contrôle composite Windows Forms dans WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Procédure pas à pas : Hébergement d'un contrôle composite WPF dans Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
