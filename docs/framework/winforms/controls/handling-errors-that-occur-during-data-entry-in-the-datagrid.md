---
title: 'Procédure pas à pas : gestion des erreurs qui se produisent pendant l’entrée de données dans le contrôle DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 30a68b85-d3af-4946-83c1-1e2d010d0511
ms.openlocfilehash: 77a4dcd9cf069ed8bbee6c49aa41db619c8e12ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738737"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms

La gestion des erreurs à partir du magasin de données sous-jacent est une fonctionnalité requise pour une application de saisie de données. Le contrôle Windows Forms <xref:System.Windows.Forms.DataGridView> facilite ce travail en exposant l’événement <xref:System.Windows.Forms.DataGridView.DataError>, qui est déclenché quand le magasin de données détecte une violation de contrainte ou une règle d’entreprise rompue.

Dans cette procédure pas à pas, vous allez extraire des lignes de la table `Customers` de l’exemple de base de données Northwind et les afficher dans un contrôle <xref:System.Windows.Forms.DataGridView>. Lorsqu’une valeur de `CustomerID` dupliquée est détectée dans une nouvelle ligne ou une ligne existante modifiée, l’événement <xref:System.Windows.Forms.DataGridView.DataError> se produit, qui est géré en affichant un <xref:System.Windows.Forms.MessageBox> qui décrit l’exception.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : gérer les erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md).

## <a name="prerequisites"></a>Composants requis

Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- Accès à un serveur doté de l’exemple de base de données Northwind SQL Server.

## <a name="creating-the-form"></a>Création du formulaire

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Pour gérer les erreurs d’entrée de données dans le contrôle DataGridView

1. Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un contrôle <xref:System.Windows.Forms.DataGridView> et un composant <xref:System.Windows.Forms.BindingSource>.

    L’exemple de code suivant fournit l’initialisation de base et inclut une méthode `Main`.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.

    Cet exemple de code utilise une méthode `GetData` qui retourne un objet <xref:System.Data.DataTable> rempli. Veillez à définir la variable `connectionString` sur une valeur appropriée pour votre base de données.

    > [!IMPORTANT]
    > Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise l' <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.BindingSource> et configure la liaison de données.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. Gérez l’événement <xref:System.Windows.Forms.DataGridView.DataError> sur le <xref:System.Windows.Forms.DataGridView>.

    Si le contexte de l’erreur est une opération de validation, affichez l’erreur dans un <xref:System.Windows.Forms.MessageBox>.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Test de l'application

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

- Appuyez sur F5 pour exécuter l'application.

  Vous verrez un contrôle <xref:System.Windows.Forms.DataGridView> rempli avec les données de la table Customers. Si vous entrez une valeur dupliquée pour `CustomerID` et que vous validez la modification, la valeur de la cellule est automatiquement rétablie et un <xref:System.Windows.Forms.MessageBox> s’affiche pour afficher l’erreur d’entrée de données.

## <a name="next-steps"></a>Étapes suivantes

Cette application vous offre une compréhension de base des fonctionnalités du contrôle <xref:System.Windows.Forms.DataGridView>. Vous pouvez personnaliser l’apparence et le comportement du contrôle <xref:System.Windows.Forms.DataGridView> de plusieurs façons :

- Modifiez les styles de bordure et d’en-tête. Pour plus d’informations, consultez [Comment : modifier les styles de bordure et de quadrillage dans le contrôle DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Activez ou restreignez l’entrée utilisateur dans le contrôle <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations, consultez [Comment : empêcher l’ajout et la suppression de lignes dans le contrôle datagridview Windows Forms](prevent-row-addition-and-deletion-datagridview.md), et [Comment : créer des colonnes en lecture seule dans le contrôle DataGridView Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Validez l’entrée utilisateur dans le contrôle <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations, consultez [procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).

- Gérer des jeux de données très volumineux en mode virtuel. Pour plus d’informations, consultez [procédure pas à pas : implémentation du mode virtuel dans le Windows Forms contrôle DataGridView](implementing-virtual-mode-wf-datagridview-control.md).

- Personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le Windows Forms contrôle DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir des styles de cellules par défaut pour le contrôle DataGridView Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Saisie de données dans le contrôle DataGridView Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour gérer les erreurs qui se produisent lors de l'entrée de données dans le contrôle DataGridView Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
