---
title: Ajouter et supprimer des colonnes dans le contrôle DataGridView à l’aide du concepteur
ms.date: 03/30/2017
f1_keywords:
- vs.DataGridViewAddColumnDialog
helpviewer_keywords:
- DataGridView control [Windows Forms], adding columns
- DataGridView control [Windows Forms], removing columns
ms.assetid: 9e709f35-0a8c-4e7e-b4c4-bacb7a834077
ms.openlocfilehash: 717a0074f0750352a23b90a9b6e5eab1dc6c925a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732350"
---
# <a name="how-to-add-and-remove-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Comment : ajouter et supprimer des colonnes dans le contrôle DataGridView Windows Forms à l'aide du concepteur
Le contrôle de <xref:System.Windows.Forms.DataGridView> Windows Forms doit contenir des colonnes pour afficher les données. Si vous envisagez de remplir le contrôle manuellement, vous devez ajouter les colonnes vous-même. Vous pouvez également lier le contrôle à une source de données, qui génère et remplit automatiquement les colonnes. Si la source de données contient plus de colonnes que vous ne souhaitez afficher, vous pouvez supprimer les colonnes indésirables.

 Les procédures suivantes requièrent un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-add-a-column-using-the-designer"></a>Pour ajouter une colonne à l’aide du concepteur

1. Cliquez sur le glyphe de balise active (![glyphe de balise active](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) dans le coin supérieur droit du contrôle <xref:System.Windows.Forms.DataGridView>, puis sélectionnez **Ajouter une colonne**.

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
- [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md)
