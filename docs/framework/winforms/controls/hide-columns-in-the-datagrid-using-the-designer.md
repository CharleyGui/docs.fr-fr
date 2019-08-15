---
title: 'Procédure : masquer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], hiding
- DataGridView control [Windows Forms], column hiding
- data [Windows Forms], displaying
ms.assetid: a81c38e6-2527-426a-bcb1-be691403be04
ms.openlocfilehash: d502a89913e108254848151e9058ac6ae83a9638
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039777"
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : masquer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur
Parfois, vous souhaiterez afficher uniquement quelques-unes des colonnes qui sont disponibles dans un contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms. Par exemple, vous souhaiterez peut-être afficher une colonne salaire employé pour les utilisateurs disposant d’informations d’identification de gestion, tout en les masquant aux autres utilisateurs. Vous pouvez également lier le contrôle à une source de données qui contient de nombreuses colonnes, dont vous souhaitez afficher uniquement certaines. Dans ce cas, vous supprimez généralement les colonnes que vous ne souhaitez pas afficher au lieu de les masquer. Pour plus d'informations, voir [Procédure : Ajoutez et supprimez des colonnes dans le contrôle DataGridView Windows Forms à](add-and-remove-columns-in-the-datagrid-using-the-designer.md)l’aide du concepteur.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

## <a name="to-hide-a-column-using-the-designer"></a>Pour masquer une colonne à l’aide du concepteur

1. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Dans la grille Propriétés de la **colonne** , <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> affectez `false`à la propriété la valeur.

    > [!NOTE]
    >  Vous pouvez également masquer une colonne lors de son ajout en désactivant la case à cocher **visible** dans la boîte de dialogue **Ajouter une colonne** .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>
- [Guide pratique : Ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique : Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique pour Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
