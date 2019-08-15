---
title: 'Procédure : modifier l’ordre des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], order of
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- data [Windows Forms], displaying
ms.assetid: 7fe52a98-75d6-448c-97a5-65ca2c568c1a
ms.openlocfilehash: bf77cf3705a470bbe00be383f6a5cb2d28bda34d
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039631"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : modifier l’ordre des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur

Lorsque vous liez un contrôle <xref:System.Windows.Forms.DataGridView> de Windows Forms à une source de données, l’ordre d’affichage des colonnes générées automatiquement est dicté par la source de données. Si cet ordre n’est pas celui que vous préférez, vous pouvez modifier l’ordre des colonnes à l’aide du concepteur. Vous pouvez également ajouter des colonnes indépendantes au contrôle et modifier leur ordre d’affichage. Pour plus d’informations sur la modification de l’ordre des colonnes par programme [, consultez Procédure: Modifiez l’ordre des colonnes dans le contrôle](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)DataGridView Windows Forms.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

## <a name="to-change-the-column-order-using-the-designer"></a>Pour modifier l’ordre des colonnes à l’aide du concepteur

1. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Cliquez sur la flèche vers le haut ou vers le bas à droite de la liste **colonnes sélectionnées** jusqu’à ce que la colonne sélectionnée soit à la position de votre choix.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Guide pratique pour Ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique pour Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique : Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
