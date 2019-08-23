---
title: 'Procédure : modifier le type d’une colonne DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: e0b0b01a3c6da0680a3ec5fcd591344e04658a37
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917619"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Procédure : modifier le type d’une colonne DataGridView Windows Forms à l’aide du concepteur
Parfois, vous souhaiterez modifier le type d’une colonne qui a déjà été ajoutée à un contrôle <xref:System.Windows.Forms.DataGridView> de Windows Forms. Par exemple, vous souhaiterez peut-être modifier les types de certaines colonnes générées automatiquement lorsque vous liez le contrôle à une source de données. Cela est utile lorsque la table que vous affichez contient des colonnes contenant des clés étrangères sur les lignes d’une table associée. Dans ce cas, vous souhaiterez peut-être remplacer les colonnes de zone de texte qui affichent ces clés étrangères par des colonnes de zone de liste déroulante qui affichent des valeurs plus explicites de la table associée.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Pour modifier le type d’une colonne à l’aide du concepteur

1. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Dans la grille Propriétés de la **colonne** , `ColumnType` définissez la propriété sur le nouveau type de colonne.

    > [!NOTE]
    > La `ColumnType` propriété est une propriété au moment du design qui indique la classe représentant le type de colonne. Il ne s’agit pas d’une propriété réelle définie dans une classe Column.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Guide pratique : Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique pour Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
