---
title: 'Procédure : créer un contrôle lié et mettre en forme les données affichées'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: d81995840aa4df4610d5b6e880b9cdbbc717f2e5
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66690387"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Procédure : créer un contrôle lié et mettre en forme les données affichées

Avec la liaison de données Windows Forms, vous pouvez mettre en forme les données affichées dans un contrôle lié aux données à l’aide de la **mise en forme et liaison avancée** boîte de dialogue.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-bind-a-control-and-format-the-displayed-data"></a>Pour lier un contrôle et mettre en forme les données affichées

1. Connectez-vous à une source de données.

     Pour plus d’informations, consultez [connexion à une Source de données](../data/adonet/connecting-to-a-data-source.md).

2. Dans le formulaire, sélectionnez le contrôle, puis ouvrez la fenêtre Propriétés.

3. Développez le **(DataBindings)** propriété, puis, dans le **(Avancé)** , cliquez sur le bouton de sélection (![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) Pour afficher le **mise en forme et liaison avancée** boîte de dialogue qui présente une liste complète des propriétés pour ce contrôle.

4. Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur le **liaison** flèche.

     Une liste des sources de données disponibles s'affiche.

5. Développez la source de données avec laquelle vous voulez établir une liaison jusqu’à trouver l’élément de données souhaité.

     Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.

6. Cliquez sur le nom d'un élément avec lequel établir une liaison.

7. Dans le **mettre en forme type** , cliquez sur le format à appliquer aux données affichées dans le contrôle.

     Dans tous les cas, vous pouvez spécifier la valeur affichée dans le contrôle si la source de données contient <xref:System.DBNull>. Sinon, les options varient légèrement en fonction du type de format que vous choisissez. Le tableau suivant présente les options et les types de format.

    |Type de format|Option de mise en forme|
    |-----------------|-----------------------|
    |Aucune mise en forme|Aucune option.|
    |Numérique|Spécifiez le nombre de décimales à l’aide de **décimales** contrôle up-down.|
    |Devise|Spécifiez le nombre de décimales à l’aide de **décimales** contrôle up-down.|
    |Date et heure|Sélectionnez comment la date et l’heure doivent être affichées en sélectionnant un des éléments dans le **Type** zone de sélection.|
    |Scientifique|Spécifiez le nombre de décimales à l’aide de **décimales** contrôle up-down.|
    |Personnalisé|Spécifiez une chaîne de format personnalisée.<br /><br /> Pour plus d’informations, consultez [Mise en forme des types](../../standard/base-types/formatting-types.md). **Remarque :**  Il n'est pas garanti que les chaînes de format personnalisées puissent effectuer un aller-retour entre la source de données et le contrôle dépendant. Gérez plutôt l'événement <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> pour la liaison et appliquez la mise en forme personnalisée dans le code de gestion d'événements.|

8. Cliquez sur **OK** pour fermer la **mise en forme et liaison avancée** boîte de dialogue et revenir à la fenêtre Propriétés.

## <a name="see-also"></a>Voir aussi

- [Guide pratique pour Créer un contrôle de liaison Simple dans un formulaire Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Validation des entrées d’utilisateur dans les Windows Forms](user-input-validation-in-windows-forms.md)
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
