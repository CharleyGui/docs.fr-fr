---
title: Ajouter des colonnes au contrôle ListView à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- ListView control [Windows Forms], adding column headers
- columns [Windows Forms], adding to ListView controls
ms.assetid: 5b1a8b4d-587e-479a-95c1-f9b90884f13a
ms.openlocfilehash: 627f8627aac861877a05c13def07427199807754
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744610"
---
# <a name="how-to-add-columns-to-the-windows-forms-listview-control-using-the-designer"></a>Comment : ajouter des colonnes au contrôle ListView Windows Forms à l'aide du concepteur

Le contrôle Windows Forms <xref:System.Windows.Forms.ListView> peut afficher plusieurs colonnes pour chaque élément de liste en mode **Détails** . Vous pouvez utiliser les colonnes pour afficher plusieurs types d’informations sur chaque élément de liste. Par exemple, une liste de fichiers peut afficher le nom du fichier, le type de fichier, la taille et la date de la dernière modification du fichier. Pour plus d’informations sur le remplissage des colonnes une fois qu’elles sont créées, consultez [Comment : afficher des sous-éléments dans des colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md).

La procédure suivante requiert un projet d' **application Windows** avec un formulaire contenant un contrôle de <xref:System.Windows.Forms.ListView>. Pour plus d’informations sur la configuration d’un tel projet, consultez [Comment : créer un projet d’application Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) et [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md).

### <a name="to-add-columns-in-the-designer"></a>Pour ajouter des colonnes dans le concepteur

1. Dans la fenêtre **Propriétés** , affectez à la propriété <xref:System.Windows.Forms.ListView.View%2A> du contrôle la valeur <xref:System.Windows.Forms.View.Details>.

2. Dans la fenêtre **Propriétés** , cliquez sur le bouton de **sélection** (![le bouton de sélection (...) dans la fenêtre Propriétés de Visual Studio.](./media/visual-studio-ellipsis-button.png)) en regard de la propriété <xref:System.Windows.Forms.ListView.Columns%2A>.

     L' **éditeur de collections ColumnHeader** s’affiche.

3. Utilisez le bouton **Ajouter** pour ajouter de nouvelles colonnes. Vous pouvez ensuite sélectionner l’en-tête de colonne et définir son texte (la légende de la colonne), l’alignement du texte et la largeur.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du contrôle ListView](listview-control-overview-windows-forms.md)
- [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Guide pratique pour afficher des sous-éléments en colonnes avec le contrôle ListView Windows Forms](how-to-display-subitems-in-columns-with-the-windows-forms-listview-control.md)
- [Guide pratique pour afficher des icônes pour le contrôle ListView Windows Forms](how-to-display-icons-for-the-windows-forms-listview-control.md)
- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)
