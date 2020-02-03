---
title: 'Procédure pas à pas : valider des données dans le contrôle DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating data [Windows Forms], Windows Forms
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: a4f1d015-2969-430c-8ea2-b612d179c290
ms.openlocfilehash: 45753fb206ad58616c9a727bd81bd2458db6053e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740100"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms

Lorsque vous affichez la fonctionnalité de saisie de données pour les utilisateurs, vous devez souvent valider les données entrées dans votre formulaire. La classe <xref:System.Windows.Forms.DataGridView> offre un moyen pratique d’effectuer la validation avant que les données ne soient validées dans le magasin de données. Vous pouvez valider les données en gérant l’événement <xref:System.Windows.Forms.DataGridView.CellValidating>, déclenché par l' <xref:System.Windows.Forms.DataGridView> lorsque la cellule active est modifiée.

Dans cette procédure pas à pas, vous allez extraire des lignes de la table `Customers` de l’exemple de base de données Northwind et les afficher dans un contrôle <xref:System.Windows.Forms.DataGridView>. Lorsqu’un utilisateur modifie une cellule dans la colonne `CompanyName` et tente de conserver la cellule, le gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.CellValidating> examine la nouvelle chaîne de nom de société pour s’assurer qu’elle n’est pas vide. Si la nouvelle valeur est une chaîne vide, le <xref:System.Windows.Forms.DataGridView> empêchera le curseur de l’utilisateur de quitter la cellule jusqu’à ce qu’une chaîne non vide soit entrée.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : valider des données dans le contrôle DataGridView Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md).

## <a name="prerequisites"></a>Composants requis

Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- Accès à un serveur doté de l’exemple de base de données Northwind SQL Server.

## <a name="creating-the-form"></a>Création du formulaire

#### <a name="to-validate-data-entered-in-a-datagridview"></a>Pour valider les données entrées dans un DataGridView

1. Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un contrôle <xref:System.Windows.Forms.DataGridView> et un composant <xref:System.Windows.Forms.BindingSource>.

    L’exemple de code suivant fournit l’initialisation de base et inclut une méthode `Main`.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.

    Cet exemple de code utilise une méthode `GetData` qui retourne un objet <xref:System.Data.DataTable> rempli. Veillez à définir la variable `connectionString` sur une valeur appropriée pour votre base de données.

    > [!IMPORTANT]
    > Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L’utilisation de l’authentification Windows, également appelée sécurité intégrée, est un moyen plus sûr de contrôler l’accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise l' <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.BindingSource> et configure la liaison de données.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. Implémentez des gestionnaires pour les événements <xref:System.Windows.Forms.DataGridView.CellValidating> et <xref:System.Windows.Forms.DataGridView.CellEndEdit> du contrôle de <xref:System.Windows.Forms.DataGridView>.

    Le gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.CellValidating> vous permet de déterminer si la valeur d’une cellule dans la colonne `CompanyName` est vide. Si la validation de la valeur de la cellule échoue, définissez la propriété <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> de la classe <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> sur `true`. Ainsi, le contrôle <xref:System.Windows.Forms.DataGridView> empêche le curseur de quitter la cellule. Affectez à la propriété <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> sur la ligne une chaîne explicative. Une icône d’erreur s’affiche avec une info-bulle contenant le texte de l’erreur. Dans le gestionnaire d’événements <xref:System.Windows.Forms.DataGridView.CellEndEdit>, définissez la propriété <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> sur la ligne sur la chaîne vide. L’événement <xref:System.Windows.Forms.DataGridView.CellEndEdit> se produit uniquement lorsque la cellule quitte le mode édition, ce qu’elle ne peut pas faire en cas d’échec de la validation.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Test de l'application

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

- Compilez et exécutez l'application.

  Vous verrez un <xref:System.Windows.Forms.DataGridView> rempli avec les données de la table `Customers`. Lorsque vous double-cliquez sur une cellule dans la colonne `CompanyName`, vous pouvez modifier la valeur. Si vous supprimez tous les caractères et appuyez sur la touche TAB pour quitter la cellule, la <xref:System.Windows.Forms.DataGridView> vous empêche de quitter. Quand vous tapez une chaîne non vide dans la cellule, le contrôle <xref:System.Windows.Forms.DataGridView> vous permet de quitter la cellule.

## <a name="next-steps"></a>Étapes suivantes

Cette application vous offre une compréhension de base des fonctionnalités du contrôle <xref:System.Windows.Forms.DataGridView>. Vous pouvez personnaliser l’apparence et le comportement du contrôle <xref:System.Windows.Forms.DataGridView> de plusieurs façons :

- Modifiez les styles de bordure et d’en-tête. Pour plus d’informations, consultez [Comment : modifier les styles de bordure et de quadrillage dans le contrôle DataGridView Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Activez ou restreignez l’entrée utilisateur dans le contrôle <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations, consultez [Comment : empêcher l’ajout et la suppression de lignes dans le contrôle datagridview Windows Forms](prevent-row-addition-and-deletion-datagridview.md), et [Comment : créer des colonnes en lecture seule dans le contrôle DataGridView Windows Forms](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Vérifiez les entrées d’utilisateur pour les erreurs liées aux bases de données. Pour plus d’informations, consultez [procédure pas à pas : gestion des erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).

- Gérer des jeux de données très volumineux en mode virtuel. Pour plus d’informations, consultez [procédure pas à pas : implémentation du mode virtuel dans le Windows Forms contrôle DataGridView](implementing-virtual-mode-wf-datagridview-control.md).

- Personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Comment : personnaliser l’apparence des cellules dans le Windows Forms contrôle DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : définir des styles de police et de couleur dans le contrôle DataGridView Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Saisie de données dans le contrôle DataGridView Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour valider des données dans le contrôle DataGridView Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Procédure pas à pas : gestion des erreurs qui se produisent lors de la saisie de données dans le contrôle DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
