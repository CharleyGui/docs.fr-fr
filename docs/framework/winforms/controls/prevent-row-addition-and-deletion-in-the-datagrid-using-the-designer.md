---
title: 'Procédure : empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], preventing row addition or deletion
ms.assetid: a17722bd-9400-41e6-8dcc-c9c151f0a749
ms.openlocfilehash: 20f9b85dc48ccd634468d0fed000120723f8ee5c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038191"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : empêcher l’ajout et la suppression de lignes dans le contrôle DataGridView Windows Forms à l’aide du concepteur
Vous pouvez vouloir empêcher les utilisateurs d'ajouter de nouvelles lignes de données à votre contrôle <xref:System.Windows.Forms.DataGridView> ou d'en supprimer des lignes existantes. Les nouvelles lignes sont entrées dans la ligne spéciale pour les nouveaux enregistrements en bas du contrôle. Lorsque vous désactivez l’ajout de lignes, la ligne des nouveaux enregistrements n’est pas affichée. Vous pouvez ensuite rendre le contrôle entièrement en lecture seule en désactivant la suppression de ligne et la modification de cellule.

 La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.DataGridView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

## <a name="to-prevent-row-addition-and-deletion"></a>Pour empêcher l’ajout et la suppression de lignes

- Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis désactivez les cases à cocher Activer l' **Ajout** et **activer la suppression** .

    > [!NOTE]
    >  Pour rendre le contrôle entièrement en lecture seule, désactivez également la case à cocher **activer la modification** .

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- [Guide pratique pour Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique pour Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
