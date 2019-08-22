---
title: 'Procédure : ajouter des colonnes au contrôle ListView Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 10963fcb6d87ed74f73ecf4f1831a56eae5a392d
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658455"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Procédure : ajouter des colonnes au contrôle ListView Windows Forms à l’aide du concepteur

Le contrôle <xref:System.Windows.Forms.ListView> Windows Forms peut afficher plusieurs colonnes pour chaque élément de liste en mode **Détails** . Vous pouvez utiliser les colonnes pour afficher plusieurs types d’informations sur chaque élément de liste. Par exemple, une liste de fichiers peut afficher le nom du fichier, le type de fichier, la taille et la date de la dernière modification du fichier. Pour plus d’informations sur le remplissage des colonnes une fois qu' [elles sont créées, consultez Procédure: Affichez des sous-éléments en colonnes avec le](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)contrôle ListView Windows Forms.

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant <xref:System.Windows.Forms.ListView> un contrôle. Pour plus d’informations sur la configuration d’un tel [projet, consultez Procédure: Créez un projet](/visualstudio/ide/step-1-create-a-windows-forms-application-project) d’application Windows Forms [et procédez comme suit: Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms.

### <a name="to-add-columns-in-the-designer"></a>Pour ajouter des colonnes dans le concepteur

1. Dans la fenêtre **Propriétés** , affectez à <xref:System.Windows.Forms.ListView.View%2A> <xref:System.Windows.Forms.View.Details>la propriété du contrôle la valeur.

2. Dans la fenêtre **Propriétés** , cliquez sur le bouton de![ **sélection** (le bouton de sélection (...) dans le fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) <xref:System.Windows.Forms.ListView.Columns%2A> en regard de la propriété.

     L' **éditeur de collections ColumnHeader** s’affiche.

3. Utilisez le bouton **Ajouter** pour ajouter de nouvelles colonnes. Vous pouvez ensuite sélectionner l’en-tête de colonne et définir son texte (la légende de la colonne), l’alignement du texte et la largeur.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique : Ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Guide pratique : Afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Guide pratique pour Afficher les icônes pour le contrôle ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Guide pratique pour Ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
