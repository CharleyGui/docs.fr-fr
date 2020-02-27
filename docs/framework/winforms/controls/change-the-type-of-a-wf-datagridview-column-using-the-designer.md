---
title: Modifier le type d’une colonne DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], types
- DataGridView control [Windows Forms], changing column type
- data [Windows Forms], displaying
ms.assetid: 7f994d45-600d-4190-a187-35803214b40c
ms.openlocfilehash: 470f350a4791a3db39d08ab7992d86eb7b2e270a
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628616"
---
# <a name="how-to-change-the-type-of-a-windows-forms-datagridview-column-using-the-designer"></a>Comment : modifier le type d'une colonne DataGridView Windows Forms à l'aide du concepteur
Parfois, vous souhaiterez modifier le type d’une colonne qui a déjà été ajoutée à un contrôle Windows Forms <xref:System.Windows.Forms.DataGridView>. Par exemple, vous souhaiterez peut-être modifier les types de certaines colonnes générées automatiquement lorsque vous liez le contrôle à une source de données. Cela est utile lorsque la table que vous affichez contient des colonnes contenant des clés étrangères sur les lignes d’une table associée. Dans ce cas, vous souhaiterez peut-être remplacer les colonnes de zone de texte qui affichent ces clés étrangères par des colonnes de zone de liste déroulante qui affichent des valeurs plus explicites de la table associée.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-change-the-type-of-a-column-using-the-designer"></a>Pour modifier le type d’une colonne à l’aide du concepteur

1. Cliquez sur le glyphe actions du concepteur (![petite flèche noire](./media/designer-actions-glyph.gif)) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **modifier les colonnes**.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Dans la grille Propriétés de la **colonne** , définissez la propriété `ColumnType` sur le nouveau type de colonne.

    > [!NOTE]
    > La propriété `ColumnType` est une propriété au moment du design qui indique la classe représentant le type de colonne. Il ne s’agit pas d’une propriété réelle définie dans une classe Column.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md)
