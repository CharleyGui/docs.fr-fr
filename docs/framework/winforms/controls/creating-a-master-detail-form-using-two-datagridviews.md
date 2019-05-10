---
title: 'Procédure pas à pas : Création d’un formulaire maître / détail utilisant deux contrôles de DataGridView Windows Forms'
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
ms.openlocfilehash: 774151efb136207a1c4f7a2f8f812bbbaefbf9e1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648209"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Procédure pas à pas : création d’un formulaire maître/détails qui utilise deux contrôles DataGridView Windows Forms
Un des scénarios plus courants pour l’utilisation de la <xref:System.Windows.Forms.DataGridView> contrôle est le *maître/détail* formulaire, dans lequel une relation parent/enfant entre deux tables de base de données est affichée. Sélection de lignes dans la table maîtresse provoque la table secondaire pour mettre à jour avec les données enfants correspondantes.  
  
 Implémentation d’un formulaire maître/détail est facile à l’aide de l’interaction entre le <xref:System.Windows.Forms.DataGridView> contrôle et le <xref:System.Windows.Forms.BindingSource> composant. Dans cette procédure pas à pas, vous allez créer le formulaire à l’aide de deux <xref:System.Windows.Forms.DataGridView> contrôles et deux <xref:System.Windows.Forms.BindingSource> composants. L’écran affiche deux tables connexes dans la base de données Northwind SQL Server : `Customers` et `Orders`. Lorsque vous avez terminé, avoir un formulaire qui affiche tous les clients dans la base de données dans le maître <xref:System.Windows.Forms.DataGridView> et toutes les commandes du client sélectionné dans le détail <xref:System.Windows.Forms.DataGridView>.  
  
 Pour copier le code dans cette rubrique sous la forme d’une liste unique, consultez [Guide pratique pour Créer un formulaire maître/détail utilisant deux contrôles de DataGridView Windows Forms](create-a-master-detail-form-using-two-datagridviews.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour exécuter cette procédure pas à pas, vous avez besoin des éléments suivants :  
  
- Accès à un serveur doté de la base de données Northwind SQL Server.  
  
## <a name="creating-the-form"></a>Création du formulaire  
  
#### <a name="to-create-a-masterdetail-form"></a>Pour créer un formulaire maître/détail  
  
1. Créez une classe qui dérive de <xref:System.Windows.Forms.Form> et contient deux <xref:System.Windows.Forms.DataGridView> contrôles et deux <xref:System.Windows.Forms.BindingSource> composants. Le code suivant fournit l’initialisation de base et inclut un `Main` (méthode). Si vous utilisez le concepteur Visual Studio pour créer votre formulaire, vous pouvez utiliser le code concepteur généré au lieu de ce code, mais veillez à utiliser les noms indiqués dans les déclarations de variable.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]  
  
2. Implémenter une méthode dans la définition de classe de votre formulaire pour gérer les détails de la connexion à la base de données. Cet exemple utilise un `GetData` méthode qui remplit une <xref:System.Data.DataSet> d’objet, ajoute un <xref:System.Data.DataRelation> objet au jeu de données et lie le <xref:System.Windows.Forms.BindingSource> composants. Veillez à définir la variable `connectionString` avec une valeur appropriée pour votre base de données.  
  
    > [!IMPORTANT]
    >  Le stockage d'informations sensibles (telles qu'un mot de passe) dans la chaîne de connexion peut affecter la sécurité de votre application. L'utilisation de l'authentification Windows (également appelée sécurité intégrée) offre un moyen plus sûr de contrôler l'accès à une base de données. Pour plus d’informations, consultez [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md).  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]  
  
3. Implémenter un gestionnaire pour votre formulaire <xref:System.Windows.Forms.Form.Load> les événements qui lie la <xref:System.Windows.Forms.DataGridView> de contrôles à la <xref:System.Windows.Forms.BindingSource> composants et appelle le `GetData` (méthode). L’exemple suivant inclut le code qui redimensionne <xref:System.Windows.Forms.DataGridView> colonnes pour correspondre les données affichées.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]  
  
## <a name="testing-the-application"></a>Test de l'application  
 Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.  
  
#### <a name="to-test-the-form"></a>Pour tester le formulaire  
  
- Compilez et exécutez l'application.  
  
     Vous verrez deux <xref:System.Windows.Forms.DataGridView> des contrôles, un au-dessus de l’autre. En haut, sont les clients de Northwind `Customers` table et en bas sont le `Orders` correspondant au client sélectionné. Lorsque vous sélectionnez des lignes différentes dans le coin supérieur <xref:System.Windows.Forms.DataGridView>, le contenu du plus faible <xref:System.Windows.Forms.DataGridView> modifier en conséquence.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Cette application vous donne une connaissance élémentaire de la <xref:System.Windows.Forms.DataGridView> fonctionnalités du contrôle. Vous pouvez personnaliser l’apparence et le comportement de la <xref:System.Windows.Forms.DataGridView> contrôle de plusieurs manières :  
  
- Modifier les styles de bordure et en-tête. Pour plus d'informations, voir [Procédure : Modifier la bordure et de Styles de quadrillage dans les Windows Forms DataGridView Control](change-the-border-and-gridline-styles-in-the-datagrid.md).  
  
- Activer ou restreindre l’entrée utilisateur et le <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d'informations, voir [Procédure : Empêcher l’ajout de ligne et de suppression dans les Windows Forms DataGridView Control](prevent-row-addition-and-deletion-datagridview.md), et [Comment : Définir une colonne en lecture seule dans les Windows Forms DataGridView Control](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).  
  
- Valider l’entrée utilisateur pour le <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations, consultez [Procédure pas à pas : Validation des données dans les Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).  
  
- Gérer des jeux de données très volumineux à l’aide du mode virtuel. Pour plus d’informations, consultez [Procédure pas à pas : Implémentation du Mode virtuel dans les Windows Forms DataGridView Control](implementing-virtual-mode-wf-datagridview-control.md).  
  
- Personnaliser l’apparence des cellules. Pour plus d'informations, voir [Procédure : Personnaliser l’apparence des cellules dans le contrôle de DataGridView Windows Forms](customize-the-appearance-of-cells-in-the-datagrid.md) et [Comment : Définir des Styles de cellules par défaut pour les Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Guide pratique pour Créer un formulaire maître/détail utilisant deux contrôles de DataGridView Windows Forms](create-a-master-detail-form-using-two-datagridviews.md)
- [Protection des informations de connexion](../../data/adonet/protecting-connection-information.md)
