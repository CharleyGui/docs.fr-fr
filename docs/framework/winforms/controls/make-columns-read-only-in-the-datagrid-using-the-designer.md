---
title: 'Procédure : mettre les colonnes en lecture seule dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- DataGridView control [Windows Forms], read-only columns
- data [Windows Forms], displaying
- columns [Windows Forms], read-only
ms.assetid: b4ef7a75-ab33-4ee3-b2cf-201530e454e9
ms.openlocfilehash: 6bdd561c863a461f43a5a7aac025fead1f971bb0
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039808"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : mettre les colonnes en lecture seule dans le contrôle DataGridView Windows Forms à l’aide du concepteur
Par défaut, les utilisateurs peuvent modifier les données numériques et de texte affichées <xref:System.Windows.Forms.DataGridView> dans le contrôle Windows Forms. Si vous souhaitez afficher des données qui ne sont pas destinées à être modifiées, vous devez faire en sorte que les colonnes qui contiennent les données soient en lecture seule. Pour plus d’informations sur la façon de rendre le contrôle entièrement accessible en [lecture seule, consultez Procédure: Empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)à l’aide du concepteur.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

## <a name="to-make-a-column-read-only-by-using-the-designer"></a>Pour définir une colonne en lecture seule à l’aide du concepteur

1. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Dans la grille Propriétés de la **colonne** , <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> affectez `true`à la propriété la valeur.

    > [!NOTE]
    >  Vous pouvez également définir une colonne en lecture seule lorsque vous l’ajoutez en activant la case à cocher **lecture seule** dans la boîte de dialogue **Ajouter une colonne** .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Guide pratique pour Ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique : Empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md)
- [Guide pratique pour Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique pour Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
