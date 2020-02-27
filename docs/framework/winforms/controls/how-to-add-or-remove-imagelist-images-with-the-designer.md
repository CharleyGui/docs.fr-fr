---
title: 'Comment : ajouter ou supprimer des images ImageList avec le concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ImageList component [Windows Forms], adding images
- ImageList component [Windows Forms], removing images
- images [Windows Forms], adding to ImageList component
ms.assetid: 5699b244-e37c-4d20-bc35-7441e55c1e3a
ms.openlocfilehash: cdc7b563a0ee4f8779b99b4e9a6786e78f8d500f
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628720"
---
# <a name="how-to-add-or-remove-imagelist-images-with-the-designer"></a>Comment : ajouter ou supprimer des images ImageList avec le concepteur

Vous pouvez ajouter des images à un composant <xref:System.Windows.Forms.ImageList> de plusieurs façons différentes. Vous pouvez ajouter des images très rapidement à l’aide de la balise active associée au <xref:System.Windows.Forms.ImageList>ou, si vous définissez plusieurs autres propriétés sur le <xref:System.Windows.Forms.ImageList>, il peut s’avérer plus pratique d’ajouter des images avec le Fenêtre Propriétés. Vous pouvez également ajouter des images à l’aide de code. Pour plus d’informations sur l’ajout d’images avec du code, consultez [Comment : ajouter ou supprimer des images avec le composant Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md). En général, vous remplissez le composant <xref:System.Windows.Forms.ImageList> avec des images avant qu’il ne soit associé à un contrôle, mais cela n’est pas obligatoire.

### <a name="to-add-or-remove-images-by-using-the-properties-window"></a>Pour ajouter ou supprimer des images à l’aide de l’Fenêtre Propriétés

1. Sélectionnez le composant <xref:System.Windows.Forms.ImageList> ou ajoutez-en un au formulaire.

2. Dans l’Fenêtre Propriétés, cliquez sur le bouton de sélection (![le bouton de sélection (...) dans le Fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ImageList.Images%2A>.

3. Dans l' **éditeur de collections d’images**, cliquez sur **Ajouter** ou **supprimer** pour ajouter ou supprimer des images dans la liste.

### <a name="to-add-or-remove-images-using-the-smart-tag"></a>Pour ajouter ou supprimer des images à l’aide de la balise active

1. Sélectionnez le composant <xref:System.Windows.Forms.ImageList> ou ajoutez-en un au formulaire.

2. Cliquez sur le glyphe actions du concepteur (![Petite flèche noire](./media/designer-actions-glyph.gif))

3. Dans la boîte de dialogue **tâches ImageList** , sélectionnez **choisir les images**.

4. Dans l **'éditeur de collections images** , cliquez sur **Ajouter** ou sur **supprimer** pour ajouter ou supprimer des images dans la liste.

## <a name="see-also"></a>Voir aussi

- [Images, bitmaps et métafichiers](../advanced/images-bitmaps-and-metafiles.md)
- [Procédure pas à pas : effectuer des tâches courantes à l’aide d’actions de concepteur](perform-common-tasks-design-actions.md)
- [ImageList, composant](imagelist-component-windows-forms.md)
