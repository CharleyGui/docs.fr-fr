---
title: 'Procédure pas à pas : création d’un formulaire maître/détail à l’aide de deux contrôles DataGridView'
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
ms.openlocfilehash: bb3da36430c7493b941f3711cb584b4517d5bd54
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740586"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Procédure pas à pas : création d'un formulaire maître/détail qui utilise deux contrôles DataGridView Windows Forms

L’un des scénarios les plus courants pour l’utilisation du contrôle de <xref:System.Windows.Forms.DataGridView> est le formulaire *maître/détail* , dans lequel une relation parent/enfant entre deux tables de base de données est affichée. La sélection de lignes dans la table principale entraîne la mise à jour de la table de détails avec les données enfants correspondantes.

Il est facile d’implémenter un formulaire maître/détail à l’aide de l’interaction entre le contrôle <xref:System.Windows.Forms.DataGridView> et le composant <xref:System.Windows.Forms.BindingSource>. Dans cette procédure pas à pas, vous allez générer le formulaire à l’aide de deux contrôles de <xref:System.Windows.Forms.DataGridView> et de deux composants de <xref:System.Windows.Forms.BindingSource>. Le formulaire affiche deux tables associées dans l’exemple de base de données Northwind SQL Server : `Customers` et `Orders`. Lorsque vous aurez terminé, vous disposerez d’un formulaire qui affiche tous les clients de la base de données dans le <xref:System.Windows.Forms.DataGridView> maître et toutes les commandes du client sélectionné dans le <xref:System.Windows.Forms.DataGridView>de détails.

Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Comment : créer un formulaire maître/détail à l’aide de deux Windows Forms contrôles DataGridView](create-a-master-detail-form-using-two-datagridviews.md).

## <a name="prerequisites"></a>Prerequisites

Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :

- Accès à un serveur doté de l’exemple de base de données Northwind SQL Server.

## <a name="creating-the-form"></a>Création du formulaire

#### <a name="to-create-a-masterdetail-form"></a>Pour créer un formulaire maître/détail

1. Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient deux contrôles <xref:System.Windows.Forms.DataGridView> et deux composants <xref:System.Windows.Forms.BindingSource>. Le code suivant fournit l’initialisation de base des formulaires et inclut une méthode `Main`. Si vous utilisez le concepteur Visual Studio pour créer votre formulaire, vous pouvez utiliser le code généré par le concepteur au lieu de ce code, mais veillez à utiliser les noms indiqués dans les déclarations de variable ici.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Implémentez une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données. Cet exemple utilise une méthode `GetData` qui remplit un objet <xref:System.Data.DataSet>, ajoute un objet <xref:System.Data.DataRelation> au jeu de données et lie les composants <xref:System.Windows.Forms.BindingSource>. Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.

    > [!IMPORTANT]
    > Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Implémentez un gestionnaire pour l’événement <xref:System.Windows.Forms.Form.Load> de votre formulaire qui lie les contrôles <xref:System.Windows.Forms.DataGridView> aux composants <xref:System.Windows.Forms.BindingSource> et appelle la méthode `GetData`. L’exemple suivant comprend du code qui redimensionne <xref:System.Windows.Forms.DataGridView> colonnes pour les adapter aux données affichées.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Test de l'application

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

- Compilez et exécutez l'application.

  Vous verrez deux contrôles de <xref:System.Windows.Forms.DataGridView>, l’un au-dessus de l’autre. En premier, les clients de la table Northwind `Customers`, et en bas, sont les `Orders` correspondant au client sélectionné. Lorsque vous sélectionnez des lignes différentes dans la <xref:System.Windows.Forms.DataGridView>supérieure, le contenu de la <xref:System.Windows.Forms.DataGridView> inférieure change en conséquence.

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
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour créer un formulaire maître/détail utilisant deux contrôles DataGridView Windows Form](create-a-master-detail-form-using-two-datagridviews.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
