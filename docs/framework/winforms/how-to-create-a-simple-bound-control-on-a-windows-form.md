---
title: 'Procédure : créer un contrôle à liaison simple dans un formulaire Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 5c92b7bfd5026b0569397dc05cca216fbdab0753
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689304"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Procédure : créer un contrôle à liaison simple dans un formulaire Windows

Avec *liaison simple*, vous pouvez afficher un seul élément de données, telle qu’une valeur de colonne à partir d’une table de dataset dans un contrôle. Vous pouvez créer une liaison simple n’importe quelle propriété d’un contrôle à une valeur de données.

> [!NOTE]
> Les boîtes de dialogue et les commandes de menu qui s'affichent peuvent être différentes de celles qui sont décrites dans l'aide, en fonction de vos paramètres actifs ou de l'édition utilisée. Pour modifier vos paramètres, choisissez **Importation et exportation de paramètres** dans le menu **Outils** . Pour plus d’informations, consultez [Personnaliser l’IDE Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).

### <a name="to-simple-bind-a-control"></a>Pour un contrôle à liaison simple

1. Connectez-vous à une source de données. Pour plus d’informations, consultez [connexion à une Source de données](../data/adonet/connecting-to-a-data-source.md).

2. Dans le formulaire, sélectionnez le contrôle et affichez la **propriétés** fenêtre.

3. Développez le **(DataBindings)** propriété.

     Les propriétés les plus souvent liées sont affichées sous la **(DataBindings)** propriété. Par exemple, dans la plupart des contrôles, le **texte** propriété est liée plus fréquemment.

4. Si la propriété dont vous souhaitez lier ne fait pas partie des propriétés couramment liées, cliquez sur le **points de suspension** bouton (![bouton les points de suspension (...) dans la fenêtre Propriétés de Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) dans le **() Avancé)** à cocher pour afficher le **mise en forme et liaison avancée** boîte de dialogue avec une liste complète des propriétés pour ce contrôle.

5. Sélectionnez la propriété que vous souhaitez lier, puis cliquez sur la flèche déroulante sous **liaison**.

     Une liste des sources de données disponibles s'affiche.

6. Développez la source de données avec laquelle vous voulez établir une liaison jusqu’à trouver l’élément de données souhaité. Par exemple, si vous établissez une liaison à une valeur de colonne dans une table de dataset, développez le nom du dataset, puis développez le nom de la table pour afficher les noms des colonnes.

7. Cliquez sur le nom d'un élément avec lequel établir une liaison.

8. Si vous travailliez le **mise en forme et liaison avancée** boîte de dialogue, cliquez sur **OK** pour revenir à la **propriétés** fenêtre.

9. Si vous souhaitez lier d’autres propriétés du contrôle, répétez les étapes 3 à 7.

    > [!NOTE]
    > Étant donné que les contrôles de liaison simple affichent uniquement un seul élément de données, il est très courant d’inclure une logique de navigation dans un formulaire Windows avec des contrôles de liaison simple.

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.Binding>
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
- [Liaison de données et Windows Forms](data-binding-and-windows-forms.md)
