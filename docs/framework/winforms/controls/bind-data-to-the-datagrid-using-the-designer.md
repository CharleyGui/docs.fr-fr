---
title: 'Procédure : lier des données au contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 609878416be26786ce865168c996c78e18b1897f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917880"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : lier des données au contrôle DataGridView Windows Forms à l’aide du concepteur
Vous pouvez utiliser le concepteur pour connecter un <xref:System.Windows.Forms.DataGridView> contrôle à des sources de données de différentes variétés, notamment des bases de données, des objets métier ou des services Web. Quand vous liez le contrôle à une source de données à l’aide du concepteur, le contrôle est automatiquement <xref:System.Windows.Forms.BindingSource> lié à un composant qui représente la source de données. En outre, les colonnes sont générées automatiquement dans le contrôle pour faire correspondre les informations de schéma fournies par la source de données.

 Après avoir généré les colonnes, vous pouvez les modifier pour répondre à vos besoins. Par exemple, vous pouvez supprimer ou masquer des colonnes qui ne vous intéressent pas dans l’affichage, vous pouvez réorganiser les colonnes, ou vous pouvez modifier les types de colonnes. Pour plus d’informations sur la modification des colonnes, consultez les rubriques répertoriées dans la section Voir aussi.

 Vous pouvez également lier plusieurs <xref:System.Windows.Forms.DataGridView> contrôles à des tables associées pour créer des relations maître/détail. Dans cette configuration, un contrôle affiche une table parent et un autre contrôle affiche uniquement les lignes d’une table enfant qui sont liées à la ligne actuelle dans la table parent. Pour plus d’informations, consultez [Guide pratique pour Affichez les données associées dans une](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))application Windows Forms.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire qui contient <xref:System.Windows.Forms.DataGridView> un contrôle ou deux contrôles pour une relation maître/détail. Pour plus d’informations sur le démarrage d’un [projet de ce type, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

## <a name="to-bind-the-control-to-a-data-source"></a>Pour lier le contrôle à une source de données

1. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle.

2. Cliquez sur la flèche déroulante correspondant à l’option **Choisir la Source de données**.

3. Si votre projet ne dispose pas déjà d’une source de données, cliquez **Ajouter la source de données projet** et suivez les étapes indiquées par l’Assistant.

     Pour plus d’informations, consultez la page [Assistant Configuration de source de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). Votre nouvelle source de données s’affiche dans la liste déroulante **Choisir la source de données**. Si votre nouvelle source de données contient un seul membre, comme une table de base de données unique, le contrôle est automatiquement lié à ce membre. Sinon, passez à l'étape suivante.

4. Développez les nœuds **Autres sources de données** et **Sources de données du projet** si cela n’est pas déjà fait, puis sélectionnez la source de données à laquelle lier le contrôle.

5. Si votre source de données contient plusieurs membres, par exemple si vous avez créé un <xref:System.Data.DataSet?displayProperty=nameWithType> qui contient plusieurs tables, développez la source de données, puis sélectionnez le membre spécifique à lier.

6. Pour créer une relation maître/détail, dans la fenêtre déroulante **choisir une source de données** pour <xref:System.Windows.Forms.DataGridView> un deuxième contrôle, <xref:System.Windows.Forms.BindingSource> développez le créé pour la table parente, puis sélectionnez la table enfant associée dans la liste affichée.

    > [!NOTE]
    > Si votre projet a déjà une source de données, vous pouvez également utiliser la fenêtre **Sources de données** pour créer un formulaire de données. Pour plus d’informations, consultez la page [Fenêtre Sources de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Guide pratique : Se connecter aux données d’une base de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Guide pratique pour Ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique pour Modifier l’ordre des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique pour Modifier le type d’une Windows Forms colonne DataGridView à l’aide du concepteur](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Guide pratique : Figer les colonnes du contrôle DataGridView Windows Forms à l’aide du concepteur](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique pour Masquer les colonnes du contrôle DataGridView Windows Forms à l’aide du concepteur](hide-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique : Définir des colonnes en lecture seule dans le contrôle DataGridView Windows Forms à l’aide du concepteur](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Guide pratique : Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique pour Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Fenêtre sources de données](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Guide pratique : Afficher les données associées dans une application Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
