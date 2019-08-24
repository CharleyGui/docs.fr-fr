---
title: 'Procédure : créer un contrôle à liaison simple dans un formulaire Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: df87f00e6e03de67c3fb1adc28472c96f4a47ef4
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015632"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Procédure : Créer un contrôle à liaison simple dans un Windows Form

Avec une *liaison simple*, vous pouvez afficher un élément de données unique, tel qu’une valeur de colonne à partir d’une table de DataSet, dans un contrôle. Vous pouvez facilement lier n’importe quelle propriété d’un contrôle à une valeur de données.

## <a name="to-simple-bind-a-control"></a>Pour lier un contrôle de façon simple

1. Connectez-vous à une source de données. Pour plus d’informations, consultez [connexion à une source de données](../data/adonet/connecting-to-a-data-source.md).

2. Dans Visual Studio, sélectionnez le contrôle dans le formulaire et affichez la fenêtre **Propriétés** .

3. Développez la propriété **(DataBindings)** .

     Les propriétés les plus souvent liées sont affichées sous la propriété **(DataBindings)** . Par exemple, dans la plupart des contrôles, la propriété **Text** est la plus souvent liée.

4. Si la propriété que vous souhaitez lier ne fait pas partie des propriétés couramment liées, cliquez sur le bouton de![sélection (le bouton de sélection (...) dans la fenêtre Propriétés de](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)Visual Studio). dans la zone **(avancé)** pour afficher la  **Boîte de dialogue mise en forme et liaison avancée** avec la liste complète des propriétés de ce contrôle.

5. Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur la flèche déroulante sous **liaison**.

     Une liste des sources de données disponibles s'affiche.

6. Développez la source de données avec laquelle vous voulez établir une liaison jusqu’à trouver l’élément de données souhaité. Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.

7. Cliquez sur le nom d'un élément avec lequel établir une liaison.

8. Si vous travailliez dans la boîte de dialogue **mise en forme et liaison avancée** , cliquez sur **OK** pour revenir à la fenêtre **Propriétés** .

9. Si vous souhaitez lier des propriétés supplémentaires du contrôle, répétez les étapes 3 à 7.

    > [!NOTE]
    > Étant donné que les contrôles à liaison simple n’affichent qu’un seul élément de données, il est très courant d’inclure la logique de navigation dans un Windows Form avec des contrôles à liaison simple.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Binding>
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
- [Liaison de données et Windows Forms](data-binding-and-windows-forms.md)
