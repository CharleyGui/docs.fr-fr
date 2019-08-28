---
title: 'Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms'
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
ms.openlocfilehash: 89569feb0cb741f56d09f4e58154b4eecb5a89d4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046380"
---
# <a name="walkthrough-validating-data-in-the-windows-forms-datagridview-control"></a>Procédure pas à pas : validation des données dans le contrôle DataGridView Windows Forms

Lorsque vous affichez la fonctionnalité de saisie de données pour les utilisateurs, vous devez souvent valider les données entrées dans votre formulaire. La <xref:System.Windows.Forms.DataGridView> classe offre un moyen pratique d’effectuer la validation avant que les données ne soient validées dans le magasin de données. Vous pouvez valider les données en gérant <xref:System.Windows.Forms.DataGridView.CellValidating> l’événement, qui est déclenché <xref:System.Windows.Forms.DataGridView> par lorsque la cellule active est modifiée.

Dans cette procédure pas à pas, vous allez extraire `Customers` des lignes de la table dans l’exemple de base de <xref:System.Windows.Forms.DataGridView> données Northwind et les afficher dans un contrôle. Lorsqu’un utilisateur modifie une cellule dans la `CompanyName` colonne et tente de la conserver, le <xref:System.Windows.Forms.DataGridView.CellValidating> gestionnaire d’événements examine la nouvelle chaîne de nom de société pour s’assurer qu’elle n’est pas vide. Si la nouvelle valeur est une chaîne <xref:System.Windows.Forms.DataGridView> vide, le empêche le curseur de l’utilisateur. de quitter la cellule jusqu’à ce qu’une chaîne non vide soit entrée.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Validez les données dans le contrôle](how-to-validate-data-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- Accès à un serveur doté de l’exemple de base de données Northwind SQL Server.

## <a name="creating-the-form"></a>Création du formulaire

#### <a name="to-validate-data-entered-in-a-datagridview"></a>Pour valider les données entrées dans un DataGridView

1. Créer une classe qui dérive de <xref:System.Windows.Forms.Form> et contient un <xref:System.Windows.Forms.DataGridView> contrôle et un <xref:System.Windows.Forms.BindingSource> composant.

    L’exemple de code suivant fournit l’initialisation de base et `Main` inclut une méthode.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#02)]

2. Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données.

    Cet exemple de code utilise `GetData` une méthode qui retourne un <xref:System.Data.DataTable> objet rempli. Veillez à affecter à la `connectionString` variable une valeur appropriée pour votre base de données.

    > [!IMPORTANT]
    > Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L’utilisation de l’authentification Windows, également appelée sécurité intégrée, est un moyen plus sûr de contrôler l’accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#30)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#30)]

3. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui initialise <xref:System.Windows.Forms.DataGridView> et <xref:System.Windows.Forms.BindingSource> et définit la liaison de données.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#10)]

4. Implémentez des gestionnaires pour <xref:System.Windows.Forms.DataGridView> les événements <xref:System.Windows.Forms.DataGridView.CellValidating> et <xref:System.Windows.Forms.DataGridView.CellEndEdit> du contrôle.

    Le <xref:System.Windows.Forms.DataGridView.CellValidating> gestionnaire d’événements permet de déterminer si la valeur d’une cellule de la `CompanyName` colonne est vide. Si la validation de la valeur de la cellule <xref:System.ComponentModel.CancelEventArgs.Cancel%2A> échoue, affectez la `true`valeur à la propriété de la <xref:System.Windows.Forms.DataGridViewCellValidatingEventArgs?displayProperty=nameWithType> classe. Cela amène le <xref:System.Windows.Forms.DataGridView> contrôle à empêcher le curseur de quitter la cellule. Affectez <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> à la propriété de la ligne une chaîne explicative. Une icône d’erreur s’affiche avec une info-bulle contenant le texte de l’erreur. Dans le <xref:System.Windows.Forms.DataGridView.CellEndEdit> gestionnaire d’événements, définissez <xref:System.Windows.Forms.DataGridViewRow.ErrorText%2A> la propriété sur la ligne sur la chaîne vide. L' <xref:System.Windows.Forms.DataGridView.CellEndEdit> événement se produit uniquement lorsque la cellule quitte le mode édition, ce qu’elle ne peut pas faire en cas d’échec de la validation.

    [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewDataValidation#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#20)]

## <a name="testing-the-application"></a>Test de l'application

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

- Compilez et exécutez l'application.

  Vous verrez <xref:System.Windows.Forms.DataGridView> des données remplies à partir de `Customers` la table. Lorsque vous double-cliquez sur une cellule dans `CompanyName` la colonne, vous pouvez modifier la valeur. Si vous supprimez tous les caractères et appuyez sur la touche Tab pour quitter la cellule <xref:System.Windows.Forms.DataGridView> , le vous empêche de quitter. Quand vous tapez une chaîne non vide dans la cellule, le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de quitter la cellule.

## <a name="next-steps"></a>Étapes suivantes

Cette application vous offre une compréhension de base des <xref:System.Windows.Forms.DataGridView> fonctionnalités du contrôle. Vous pouvez personnaliser l’apparence et le comportement du <xref:System.Windows.Forms.DataGridView> contrôle de plusieurs façons:

- Modifiez les styles de bordure et d’en-tête. Pour plus d’informations, consultez [Guide pratique pour Modifiez les styles de bordure et de quadrillage dans le contrôle](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView Windows Forms.

- Active ou restreint l' <xref:System.Windows.Forms.DataGridView> entrée utilisateur au contrôle. Pour plus d’informations, consultez [Guide pratique pour Empêcher l’ajout et la suppression de lignes dans le](prevent-row-addition-and-deletion-datagridview.md)contrôle DataGridView [Windows Forms, et comment: Définissez les colonnes en lecture seule dans le contrôle](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Vérifiez les entrées d’utilisateur pour les erreurs liées aux bases de données. Pour plus d’informations, consultez [Procédure pas à pas : Gestion des erreurs qui se produisent lors de l’entrée de données](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)dans le contrôle DataGridView Windows Forms.

- Gérer des jeux de données très volumineux en mode virtuel. Pour plus d’informations, consultez [Procédure pas à pas : Implémentation du mode virtuel dans le contrôle](implementing-virtual-mode-wf-datagridview-control.md)DataGridView Windows Forms.

- Personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Guide pratique pour Personnalisez l’apparence des cellules dans le contrôle](customize-the-appearance-of-cells-in-the-datagrid.md) DataGridView Windows Forms et [Comment: Définissez les styles de police et de couleur dans le](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)contrôle DataGridView Windows Forms.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Saisie de données dans le contrôle DataGridView Windows Forms](data-entry-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Valider les données dans le contrôle DataGridView Windows Forms](how-to-validate-data-in-the-windows-forms-datagridview-control.md)
- [Procédure pas à pas : Gestion des erreurs qui se produisent lors de l’entrée de données dans le contrôle DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
