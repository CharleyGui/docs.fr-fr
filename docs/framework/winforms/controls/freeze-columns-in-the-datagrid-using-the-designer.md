---
title: 'Procédure : figer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: d38c8d73bc70e7e521b476ca78c8f102d003c538
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040333"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : figer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur
Quand des utilisateurs consultent des données affichées dans un contrôle Windows Forms <xref:System.Windows.Forms.DataGridView>, ils doivent parfois faire fréquemment référence à une même colonne ou un même ensemble de colonnes. Par exemple, lorsque vous affichez une table d’informations client qui contient de nombreuses colonnes, il est utile d’afficher le nom du client à tout moment, tout en permettant à d’autres colonnes de faire défiler la région visible.

 Pour obtenir ce comportement, vous pouvez figer des colonnes dans le contrôle. Quand vous figez une colonne, toutes les colonnes à sa gauche (ou à sa droite dans les scripts de droite à gauche) sont aussi figées. Les colonnes figées restent en place, tandis que toutes les autres colonnes peuvent défiler. Si la réorganisation des colonnes est activée, les colonnes figées sont traitées comme un groupe distinct des colonnes non figées. Les utilisateurs peuvent repositionner des colonnes dans l'un ou l'autre groupe, mais ils ne peuvent pas déplacer une colonne d'un groupe à l'autre.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

## <a name="to-freeze-a-column-using-the-designer"></a>Pour figer une colonne à l’aide du concepteur

1. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Modifier les **colonnes**.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Dans la grille Propriétés de la **colonne** , <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> affectez `true`à la propriété la valeur.

    > [!NOTE]
    >  Vous pouvez également geler une colonne quand vous l’ajoutez en sélectionnant la zone figée dans la boîte de dialogue **Ajouter une colonne** .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Guide pratique pour Ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Guide pratique pour Activer la réorganisation des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Guide pratique pour Afficher le texte de droite à gauche dans Windows Forms pour la globalisation](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [Guide pratique : Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique : Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
