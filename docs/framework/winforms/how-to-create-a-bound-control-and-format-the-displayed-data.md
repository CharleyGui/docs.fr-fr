---
title: 'Procédure : créer un contrôle lié et mettre en forme les données affichées'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 052e619acb23fb2e25f42daf7b4eaaacb0688f31
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039422"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Procédure : créer un contrôle lié et mettre en forme les données affichées

Avec Windows Forms la liaison de données, vous pouvez mettre en forme les données affichées dans un contrôle lié aux données à l’aide de la boîte de dialogue **mise en forme et liaison avancée** .


### <a name="to-bind-a-control-and-format-the-displayed-data"></a>Pour lier un contrôle et mettre en forme les données affichées

1. Connectez-vous à une source de données.

     Pour plus d’informations, consultez [connexion à une source de données](../data/adonet/connecting-to-a-data-source.md).

2. Dans le formulaire, sélectionnez le contrôle, puis ouvrez la fenêtre Propriétés.

3. Développez la propriété **(DataBindings)** , puis dans la zone **(avancé)** , cliquez sur le bouton de![sélection (le bouton de sélection (...) dans le fenêtre Propriétés de](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)Visual Studio.) pour afficher les **options de mise en forme et avancé** La boîte de dialogue liaison, qui contient la liste complète des propriétés de ce contrôle.

4. Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur la flèche **liaison** .

     Une liste des sources de données disponibles s'affiche.

5. Développez la source de données avec laquelle vous voulez établir une liaison jusqu’à trouver l’élément de données souhaité.

     Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.

6. Cliquez sur le nom d'un élément avec lequel établir une liaison.

7. Dans la zone **type de format** , cliquez sur le format que vous souhaitez appliquer aux données affichées dans le contrôle.

     Dans tous les cas, vous pouvez spécifier la valeur affichée dans le contrôle si la source de données contient <xref:System.DBNull>. Sinon, les options varient légèrement en fonction du type de format que vous choisissez. Le tableau suivant présente les options et les types de format.

    |Type de format|Option de mise en forme|
    |-----------------|-----------------------|
    |Aucune mise en forme|Aucune option.|
    |Numeric|Spécifiez le nombre de décimales à l’aide du contrôle de nombre de décimales.|
    |Devise|Spécifiez le nombre de décimales à l’aide du contrôle de nombre de décimales.|
    |Date et heure|Sélectionnez le mode d’affichage de la date et de l’heure en sélectionnant l’un des éléments dans la zone de sélection **type** .|
    |Scientifique|Spécifiez le nombre de décimales à l’aide du contrôle de nombre de décimales.|
    |Personnalisé|Spécifiez une chaîne de format personnalisée.<br /><br /> Pour plus d’informations, consultez [Mise en forme des types](../../standard/base-types/formatting-types.md). **Remarque :**  Il n'est pas garanti que les chaînes de format personnalisées puissent effectuer un aller-retour entre la source de données et le contrôle dépendant. Gérez plutôt l'événement <xref:System.Windows.Forms.Binding.Parse> ou <xref:System.Windows.Forms.Binding.Format> pour la liaison et appliquez la mise en forme personnalisée dans le code de gestion d'événements.|

8. Cliquez sur **OK** pour fermer la boîte de dialogue **mise en forme et liaison avancée** et revenir au fenêtre Propriétés.

## <a name="see-also"></a>Voir aussi

- [Guide pratique : Créer un contrôle à liaison simple dans un Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Validation des entrées d’utilisateur dans les Windows Forms](user-input-validation-in-windows-forms.md)
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
