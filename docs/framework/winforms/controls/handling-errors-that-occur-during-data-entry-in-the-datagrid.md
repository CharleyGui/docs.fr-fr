---
title: 'Procédure pas à pas : gestion des erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView Windows Forms'
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
ms.openlocfilehash: cee6fe3b049378fa7bbe2585a3607049eaf231bc
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046078"
---
# <a name="walkthrough-handling-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a>Procédure pas à pas : gestion des erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView Windows Forms

La gestion des erreurs à partir du magasin de données sous-jacent est une fonctionnalité requise pour une application de saisie de données. Le contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms facilite ce travail en exposant l' <xref:System.Windows.Forms.DataGridView.DataError> événement, qui est déclenché quand le magasin de données détecte une violation de contrainte ou une règle d’entreprise rompue.

Dans cette procédure pas à pas, vous allez extraire `Customers` des lignes de la table dans l’exemple de base de <xref:System.Windows.Forms.DataGridView> données Northwind et les afficher dans un contrôle. Lorsqu’une valeur `CustomerID` dupliquée est détectée dans une nouvelle ligne ou une ligne existante modifiée <xref:System.Windows.Forms.DataGridView.DataError> , l’événement se produit, qui est géré en affichant <xref:System.Windows.Forms.MessageBox> un qui décrit l’exception.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Gérer les erreurs qui se produisent lors de l’entrée de données](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)dans le contrôle DataGridView Windows Forms.

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- Accès à un serveur doté de l’exemple de base de données Northwind SQL Server.

## <a name="creating-the-form"></a>Création du formulaire

#### <a name="to-handle-data-entry-errors-in-the-datagridview-control"></a>Pour gérer les erreurs d’entrée de données dans le contrôle DataGridView

1. Créer une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un <xref:System.Windows.Forms.DataGridView> contrôle et un <xref:System.Windows.Forms.BindingSource> composant.

    L’exemple de code suivant fournit l’initialisation de base et `Main` inclut une méthode.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#02)]

2. Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.

    Cet exemple de code utilise `GetData` une méthode qui retourne un <xref:System.Data.DataTable> objet rempli. Veillez à affecter à la `connectionString` variable une valeur appropriée pour votre base de données.

    > [!IMPORTANT]
    > Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#30)]

3. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.BindingSource> et définit la liaison de données.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#10)]

4. Gérez l' <xref:System.Windows.Forms.DataGridView.DataError> événement sur le <xref:System.Windows.Forms.DataGridView>.

    Si le contexte de l’erreur est une opération de validation, affichez l’erreur <xref:System.Windows.Forms.MessageBox>dans.

    [!code-csharp[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridView.DataError#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#20)]

## <a name="testing-the-application"></a>Test de l'application

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

- Appuyez sur F5 pour exécuter l'application.

  Vous verrez un <xref:System.Windows.Forms.DataGridView> contrôle rempli avec les données de la table Customers. Si vous entrez une valeur dupliquée `CustomerID` pour et que vous validez la modification, la valeur de la cellule est automatiquement rétablie et un qui affiche l’erreur d' <xref:System.Windows.Forms.MessageBox> entrée de données s’affiche.

## <a name="next-steps"></a>Étapes suivantes

Cette application vous offre une compréhension de base des <xref:System.Windows.Forms.DataGridView> fonctionnalités du contrôle. Vous pouvez personnaliser l’apparence et le comportement du <xref:System.Windows.Forms.DataGridView> contrôle de plusieurs façons:

- Modifiez les styles de bordure et d’en-tête. Pour plus d’informations, consultez [Guide pratique pour Modifiez les styles de bordure et de quadrillage dans le contrôle](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView Windows Forms.

- Active ou restreint l' <xref:System.Windows.Forms.DataGridView> entrée utilisateur au contrôle. Pour plus d’informations, consultez [Guide pratique pour Empêcher l’ajout et la suppression de lignes dans le](prevent-row-addition-and-deletion-datagridview.md)contrôle DataGridView [Windows Forms, et comment: Définissez les colonnes en lecture seule dans le contrôle](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Validez l’entrée d' <xref:System.Windows.Forms.DataGridView> utilisateur pour le contrôle. Pour plus d’informations, consultez [Procédure pas à pas : Validation des données dans le contrôle](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Gérer des jeux de données très volumineux en mode virtuel. Pour plus d’informations, consultez [Procédure pas à pas : Implémentation du mode virtuel dans le contrôle](implementing-virtual-mode-wf-datagridview-control.md)DataGridView Windows Forms.

- Personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Guide pratique pour Personnalisez l’apparence des cellules dans le contrôle](customize-the-appearance-of-cells-in-the-datagrid.md) DataGridView Windows Forms et [Comment: Définissez les styles de cellules par défaut pour le](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)contrôle DataGridView Windows Forms.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Saisie de données dans le contrôle DataGridView Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Gérer les erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView Windows Forms](handle-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Procédure pas à pas : Validation des données dans le contrôle DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
