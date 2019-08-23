---
title: 'Procédure : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 7a3029192ab0da4a954dfd7d3d258a00b154924e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957111"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Procédure : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l’aide du concepteur
Le contrôle <xref:System.Windows.Forms.DataGridView> Windows Forms doit contenir des colonnes afin d’afficher les données. Si vous envisagez de remplir le contrôle manuellement, vous devez ajouter les colonnes vous-même. Vous pouvez également lier le contrôle à une source de données, qui génère et remplit automatiquement les colonnes. Si la source de données contient plus de colonnes que vous ne souhaitez afficher, vous pouvez supprimer les colonnes indésirables.

 Les procédures suivantes requièrent un projet d' **application Windows** avec un formulaire <xref:System.Windows.Forms.DataGridView> contenant un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

## <a name="to-add-a-column-using-the-designer"></a>Pour ajouter une colonne à l’aide du concepteur

1. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le <xref:System.Windows.Forms.DataGridView> coin supérieur droit du contrôle, puis sélectionnez Ajouter une **colonne**.

2. Dans la boîte de dialogue **Ajouter une colonne** , choisissez l’option de **colonne DataBound** et sélectionnez une colonne dans la source de données, ou choisissez l’option **colonne indépendante** et définissez la colonne à l’aide des champs fournis.

3. Cliquez sur le bouton **Ajouter** pour ajouter la colonne, provoquant son affichage dans le concepteur si les colonnes existantes ne remplissent pas encore la zone d’affichage du contrôle.

    > [!NOTE]
    > Vous pouvez modifier les propriétés des colonnes dans la boîte de dialogue **modifier les colonnes** , à laquelle vous pouvez accéder à partir de la balise active du contrôle.

## <a name="to-remove-a-column-using-the-designer"></a>Pour supprimer une colonne à l’aide du concepteur

1. Choisissez **modifier les colonnes** à partir de la balise active du contrôle.

2. Sélectionnez une colonne dans la liste **colonnes sélectionnées** .

3. Cliquez sur le bouton **supprimer** pour supprimer la colonne, provoquant sa disparition du concepteur.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- [Guide pratique pour Créer un projet Application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Guide pratique pour Ajouter des contrôles à Windows Forms](how-to-add-controls-to-windows-forms.md)
