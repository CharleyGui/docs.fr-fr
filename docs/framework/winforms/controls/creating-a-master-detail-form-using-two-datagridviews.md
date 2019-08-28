---
title: 'Procédure pas à pas : Création d’un formulaire maître/détail à l’aide de deux Windows Forms contrôles DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 4212c7223aca6a5e7de3189d5f6b2757453cc438
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046096"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Procédure pas à pas : création d’un formulaire maître/détails qui utilise deux contrôles DataGridView Windows Forms

L’un des scénarios les plus courants pour l' <xref:System.Windows.Forms.DataGridView> utilisation du contrôle est le formulaire *maître/détail* , dans lequel une relation parent/enfant entre deux tables de base de données est affichée. La sélection de lignes dans la table principale entraîne la mise à jour de la table de détails avec les données enfants correspondantes.

Il est facile d’implémenter un formulaire maître/détail à l' <xref:System.Windows.Forms.DataGridView> aide de l' <xref:System.Windows.Forms.BindingSource> interaction entre le contrôle et le composant. Dans cette procédure pas à pas, vous allez générer le <xref:System.Windows.Forms.DataGridView> formulaire à l' <xref:System.Windows.Forms.BindingSource> aide de deux contrôles et deux composants. Le formulaire affiche deux tables associées dans l’exemple de base de données Northwind `Customers` SQL Server `Orders`: et. Lorsque vous aurez terminé, vous disposerez d’un formulaire qui affiche tous les clients dans la base de données <xref:System.Windows.Forms.DataGridView> du maître et toutes les commandes du client sélectionné dans le <xref:System.Windows.Forms.DataGridView>détail.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Créez un formulaire maître/détail à l’aide de deux](create-a-master-detail-form-using-two-datagridviews.md)contrôles Windows Forms DataGridView.

## <a name="prerequisites"></a>Prérequis

Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- Accès à un serveur doté de l’exemple de base de données Northwind SQL Server.

## <a name="creating-the-form"></a>Création du formulaire

#### <a name="to-create-a-masterdetail-form"></a>Pour créer un formulaire maître/détail

1. Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient deux <xref:System.Windows.Forms.DataGridView> contrôles et deux <xref:System.Windows.Forms.BindingSource> composants. Le code suivant fournit l’initialisation de base des formulaires et `Main` inclut une méthode. Si vous utilisez le concepteur Visual Studio pour créer votre formulaire, vous pouvez utiliser le code généré par le concepteur au lieu de ce code, mais veillez à utiliser les noms indiqués dans les déclarations de variable ici.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données. Cet exemple utilise une `GetData` méthode qui remplit un <xref:System.Data.DataSet> objet, ajoute un <xref:System.Data.DataRelation> objet au jeu de données et lie les <xref:System.Windows.Forms.BindingSource> composants. Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.

    > [!IMPORTANT]
    > Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui lie <xref:System.Windows.Forms.DataGridView> les contrôles aux <xref:System.Windows.Forms.BindingSource> composants et appelle la `GetData` méthode. L’exemple suivant comprend du code qui redimensionne <xref:System.Windows.Forms.DataGridView> les colonnes pour les adapter aux données affichées.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Test de l'application

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

- Compilez et exécutez l'application.

  Vous verrez deux <xref:System.Windows.Forms.DataGridView> contrôles, l’un au-dessus de l’autre. En plus, les clients de la table `Customers` Northwind sont en bas `Orders` de la table correspondant au client sélectionné. À mesure que vous sélectionnez des lignes différentes <xref:System.Windows.Forms.DataGridView>dans la partie supérieure, le <xref:System.Windows.Forms.DataGridView> contenu de la modification la plus basse est modifié en conséquence.

## <a name="next-steps"></a>Étapes suivantes

Cette application vous offre une compréhension de base des <xref:System.Windows.Forms.DataGridView> fonctionnalités du contrôle. Vous pouvez personnaliser l’apparence et le comportement du <xref:System.Windows.Forms.DataGridView> contrôle de plusieurs façons:

- Modifiez les styles de bordure et d’en-tête. Pour plus d'informations, voir [Procédure : Modifiez les styles de bordure et de quadrillage dans le contrôle](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView Windows Forms.

- Active ou restreint l' <xref:System.Windows.Forms.DataGridView> entrée utilisateur au contrôle. Pour plus d’informations, consultez [Guide pratique pour Empêcher l’ajout et la suppression de lignes dans le](prevent-row-addition-and-deletion-datagridview.md)contrôle DataGridView [Windows Forms, et comment: Définissez les colonnes en lecture seule dans le contrôle](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Validez l’entrée d' <xref:System.Windows.Forms.DataGridView> utilisateur pour le contrôle. Pour plus d’informations, consultez [Procédure pas à pas : Validation des données dans le contrôle](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

- Gérer des jeux de données très volumineux en mode virtuel. Pour plus d’informations, consultez [Procédure pas à pas : Implémentation du mode virtuel dans le contrôle](implementing-virtual-mode-wf-datagridview-control.md)DataGridView Windows Forms.

- Personnaliser l’apparence des cellules. Pour plus d’informations, consultez [Guide pratique pour Personnalisez l’apparence des cellules dans le contrôle](customize-the-appearance-of-cells-in-the-datagrid.md) DataGridView Windows Forms et [Comment: Définissez les styles de cellules par défaut pour le](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)contrôle DataGridView Windows Forms.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Créer un formulaire maître/détail à l’aide de deux Windows Forms contrôles DataGridView](create-a-master-detail-form-using-two-datagridviews.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
