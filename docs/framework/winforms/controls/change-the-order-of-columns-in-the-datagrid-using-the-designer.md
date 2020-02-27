---
title: Modifier l’ordre des colonnes dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: 7540203fb1c0465caeb045275734d1a7c6f25ee8
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628746"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Comment : modifier l'ordre des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur

Lorsque vous liez un contrôle Windows Forms <xref:System.Windows.Forms.DataGridView> à une source de données, l’ordre d’affichage des colonnes générées automatiquement est dicté par la source de données. Si cet ordre n’est pas celui que vous préférez, vous pouvez modifier l’ordre des colonnes à l’aide du concepteur. Vous pouvez également ajouter des colonnes indépendantes au contrôle et modifier leur ordre d’affichage. Pour plus d’informations sur la modification de l’ordre des colonnes par programme, consultez [Comment : modifier l’ordre des colonnes dans le contrôle DataGridView Windows Forms](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md).

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-change-the-column-order-using-the-designer"></a>Pour modifier l’ordre des colonnes à l’aide du concepteur

1. Cliquez sur le glyphe actions du concepteur (![petite flèche noire](./media/designer-actions-glyph.gif)) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **modifier les colonnes**.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Cliquez sur la flèche vers le haut ou vers le bas à droite de la liste **colonnes sélectionnées** jusqu’à ce que la colonne sélectionnée soit à la position de votre choix.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Guide pratique pour ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md)
