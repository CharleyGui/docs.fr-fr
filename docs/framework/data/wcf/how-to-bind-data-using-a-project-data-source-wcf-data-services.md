---
title: 'Procédure : Lier des données à l’aide d’une source de données de projet (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: 85d5974f43349d91d56a1ab41b314521a6ee7348
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780169"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Procédure : Lier des données à l’aide d’une source de données de projet (WCF Data Services)

Vous pouvez créer des sources de données basées sur les objets de données générés dans une application cliente WCF Data Services. Lorsque vous ajoutez une référence à un service de données à l’aide de la boîte de dialogue **Ajouter une référence de service** , une source de données de projet est créée avec les classes de données clientes générées. Une source de données est créée pour chaque jeu d'entités exposé par le service de données. Vous pouvez créer des formulaires qui affichent des données du service en les faisant glisser de la fenêtre **sources de données** vers le concepteur. Ces éléments deviennent des contrôles liés à la source de données. Pendant l’exécution, cette source de données est liée à une instance <xref:System.Data.Services.Client.DataServiceCollection%601> de la classe, qui est remplie avec les objets retournés par une requête au service de données. Pour plus d’informations, consultez [liaison de données à des contrôles](binding-data-to-controls-wcf-data-services.md).

 Les exemples dans cette rubrique utilisent l'exemple de service de données Northwind et des classes de service de données client générées automatiquement. Ce service et les classes de données clientes sont créés lorsque vous terminez le [démarrage rapide WCF Data Services](quickstart-wcf-data-services.md).

## <a name="use-a-project-data-source-in-a-wpf-window"></a>Utiliser une source de données de projet dans une fenêtre WPF

1. Dans Visual Studio, dans un projet WPF, ajoutez une référence au service de données Northwind. Pour plus d’informations, consultez [Guide pratique pour Ajoutez une référence](how-to-add-a-data-service-reference-wcf-data-services.md)de service de données.

2. Dans la fenêtre **sources de données** , développez le `Customers` nœud dans la source de données du projet **NorthwindEntities** .

3. Cliquez sur l’élément **CustomerID** , sélectionnez **ComboBox** dans la liste, puis faites glisser l’élément **CustomerID** du nœud **Customers** vers le concepteur.

     Cela crée les éléments objet suivants dans le fichier XAML pour la fenêtre :

    - Un élément <xref:System.Windows.Data.CollectionViewSource> nommé `customersViewSource`. La propriété <xref:System.Windows.FrameworkElement.DataContext%2A> de l'élément objet <xref:System.Windows.Controls.Grid> de niveau supérieur est définie sur cette nouvelle <xref:System.Windows.Data.CollectionViewSource>.

    - Un <xref:System.Windows.Controls.ComboBox> lié aux données nommé  `CustomerID`.

    - <xref:System.Windows.Controls.Label>

4. Faites glisser la propriété de navigation **Orders** vers le concepteur.

     Cela crée les éléments objet supplémentaires suivants dans le fichier XAML pour la fenêtre :

    - Un deuxième élément <xref:System.Windows.Data.CollectionViewSource> nommé `customersOrdersViewSource`, dont la source est `customerViewSource`.

    - Un contrôle <xref:System.Windows.Controls.DataGrid> lié aux données nommé  `ordersDataGrid`.

5. Facultatif Faites glisser des éléments supplémentaires du nœud **Customers** vers le concepteur.

6. Ouvrez la page de codes du formulaire et ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. Dans la classe partielle qui définit le formulaire, ajoutez le code suivant, qui crée une instance d'<xref:System.Data.Objects.ObjectContext> et définit la constante `customerID`.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. Dans le concepteur, sélectionnez la fenêtre.

    > [!NOTE]
    > Assurez-vous que vous sélectionnez la fenêtre elle-même, plutôt que de sélectionner le contenu qui est dans la fenêtre. Si la fenêtre est sélectionnée, la zone de texte **nom** située en haut de la fenêtre **Propriétés** doit contenir le nom de la fenêtre.

9. Dans la fenêtre **Propriétés** , sélectionnez le bouton **événements** .

10. Recherchez l’événement **Loaded** , puis double-cliquez sur la liste déroulante en regard de cet événement.

     Visual Studio ouvre le fichier code-behind pour la fenêtre et génère un gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded>.

11. Dans la méthode de gestionnaire d'événements <xref:System.Windows.FrameworkElement.Loaded> récemment créé, copiez et collez le code suivant.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. Ce code crée une instance de <xref:System.Data.Services.Client.DataServiceCollection%601> pour le type `Customers` basé sur l'exécution d'une requête LINQ qui retourne un <xref:System.Collections.Generic.IEnumerable%601> de `Customers` avec des objets `Orders` connexes du service de données Northwind et le lie à `customersViewSource`.

## <a name="use-a-project-data-source-in-a-windows-form"></a>Utiliser une source de données de projet dans un Windows Form

1. Dans la fenêtre **sources de données** , développez le nœud **Customers** dans la source de données du projet **NorthwindEntities** .

2. Cliquez sur l’élément **CustomerID** , sélectionnez **ComboBox** dans la liste, puis faites glisser l’élément **CustomerID** du nœud **Customers** vers le concepteur.

     Cette opération crée les contrôles suivants dans le formulaire :

    - Instance de <xref:System.Windows.Forms.BindingSource> nommée `customersBindingSource`.

    - Instance de <xref:System.Windows.Forms.BindingNavigator> nommée `customersBindingNavigator`. Vous pouvez supprimer ce contrôle qui ne sera pas nécessaire.

    - Un <xref:System.Windows.Forms.ComboBox> lié aux données nommé  `CustomerID`.

    - <xref:System.Windows.Forms.Label>

3. Faites glisser la propriété de navigation **Orders** vers le formulaire.

4. Cette opération crée le contrôle `ordersBindingSource` dont la propriété <xref:System.Windows.Forms.BindingSource.DataSource%2A> a la valeur `customersBindingSource` et la propriété <xref:System.Windows.Forms.BindingSource.DataMember%2A> la valeur `Customers`. Elle crée également dans le formulaire le contrôle lié aux données `ordersDataGridView` et son contrôle label avec le titre approprié.

5. Facultatif Faites glisser des éléments supplémentaires du nœud **Customers** vers le concepteur.

6. Ouvrez la page de codes du formulaire et ajoutez les instructions `using` (`Imports` en Visual Basic) suivantes :

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersusing)]

7. Dans la classe partielle qui définit le formulaire, ajoutez le code suivant, qui crée une instance d'<xref:System.Data.Objects.ObjectContext> et définit la constante `customerID`.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdefinition)]

8. Dans le concepteur de formulaires, double-cliquez sur le formulaire.

     La page de codes du formulaire s'ouvre et la méthode qui gère l'événement `Load` du formulaire est créée.

9. Dans la méthode de gestionnaire d'événements `Load`, copiez et collez le code suivant.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabinding)]

10. Ce code crée une instance de <xref:System.Data.Services.Client.DataServiceCollection%601> pour le type `Customers` basé sur l'exécution d'un <xref:System.Data.Services.Client.DataServiceQuery%601> qui retourne un <xref:System.Collections.Generic.IEnumerable%601> de `Customers` du service de données Northwind et le lie à `customersBindingSource`.

## <a name="see-also"></a>Voir aussi

- [Bibliothèque cliente WCF Data Services](wcf-data-services-client-library.md)
- [Guide pratique pour Lier des données à des éléments Windows Presentation Foundation](bind-data-to-wpf-elements-wcf-data-services.md)
