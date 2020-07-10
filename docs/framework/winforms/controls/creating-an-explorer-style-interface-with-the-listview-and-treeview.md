---
title: 'Procédure pas à pas : création d’une interface de style Explorateur avec les contrôles ListView et TreeView à l’aide du concepteur'
description: Découvrez comment créer une interface de style Explorateur avec les contrôles Windows Forms ListView et TreeView à l’aide du concepteur.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Explorer-style applications [Windows Forms], walkthroughs
- TreeView control [Windows Forms], ListView controls used with
- ListView control [Windows Forms], TreeView controls used with
- Explorer-style applications
- TreeView control [Windows Forms], using for explorer-style interface
- ListView control [Windows Forms], explorer style interface
- ListView control [Windows Forms], explorer-style interface
ms.assetid: 9e5e7721-19e2-4890-b273-a43589fe99ff
ms.openlocfilehash: 44d4db1ef3da85dbf411498f486882b86a05c140
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174625"
---
# <a name="walkthrough-creating-an-explorer-style-interface-with-the-listview-and-treeview-controls-using-the-designer"></a>Procédure pas à pas : création d’une interface de style Explorateur avec les contrôles ListView et TreeView à l’aide du concepteur

L’un des avantages de Visual Studio est la possibilité de créer des applications de Windows Forms de qualité professionnelle dans un laps de temps limité. Un scénario courant consiste à créer une interface utilisateur avec des <xref:System.Windows.Forms.ListView> contrôles et <xref:System.Windows.Forms.TreeView> qui ressemble à la fonctionnalité de l’Explorateur Windows des systèmes d’exploitation Windows. L’Explorateur Windows affiche une structure hiérarchique des fichiers et dossiers sur l’ordinateur d’un utilisateur.

### <a name="to-create-the-form-containing-a-listview-and-treeview-control"></a>Pour créer le formulaire contenant un contrôle ListView et TreeView

1. Dans le menu **Fichier** , pointez sur **Nouveau**, puis cliquez sur **Projet**.

2. Dans la boîte de dialogue **Nouveau projet** , procédez comme suit :

    1. Dans les catégories, choisissez **Visual Basic** ou **Visual C#**.

    2. Dans la liste des modèles, choisissez **Windows Forms application**.

3. Cliquez sur **OK**. Un nouveau projet de Windows Forms est créé.

4. Ajoutez un <xref:System.Windows.Forms.SplitContainer> contrôle au formulaire et affectez à sa propriété la valeur <xref:System.Windows.Forms.SplitContainer.Dock%2A> <xref:System.Windows.Forms.DockStyle.Fill> .

5. Ajoutez un <xref:System.Windows.Forms.ImageList> nommé `imageList1` au formulaire et utilisez la fenêtre Propriétés pour ajouter deux images : une image de dossier et une image de document, dans cet ordre.

6. Ajoutez un <xref:System.Windows.Forms.TreeView> contrôle nommé `treeview1` au formulaire et positionnez-le sur le côté gauche du <xref:System.Windows.Forms.SplitContainer> contrôle. Dans le Fenêtre Propriétés pour, `treeView1` procédez comme suit :

    1. Attribuez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.

    2. Affectez à la propriété <xref:System.Windows.Forms.TreeView.ImageList%2A> la valeur `imagelist1.`

7. Ajoutez un <xref:System.Windows.Forms.ListView> contrôle nommé `listView1` au formulaire et positionnez-le sur le côté droit du <xref:System.Windows.Forms.SplitContainer> contrôle. Dans le Fenêtre Propriétés pour, `listview1` procédez comme suit :

    1. Attribuez à la propriété <xref:System.Windows.Forms.Control.Dock%2A> la valeur <xref:System.Windows.Forms.DockStyle.Fill>.

    2. Attribuez à la propriété <xref:System.Windows.Forms.ListView.View%2A> la valeur <xref:System.Windows.Forms.View.Details>.

    3. Ouvrez l’éditeur de collections ColumnHeader en cliquant sur les points de ![ suspension (bouton de sélection (...) dans le fenêtre Propriétés de Visual Studio. ](./media/visual-studio-ellipsis-button.png) ) dans la <xref:System.Windows.Forms.ListView.Columns%2A> propriété **.** Ajoutez trois colonnes et affectez <xref:System.Windows.Forms.ColumnHeader.Text%2A> à leur propriété la valeur `Name` , `Type` et `Last Modified` , respectivement. Cliquez sur **OK** pour fermer la boîte de dialogue.

    4. Affectez à la propriété <xref:System.Windows.Forms.ListView.SmallImageList%2A> la valeur `imageList1.`

8. Implémentez le code pour remplir le <xref:System.Windows.Forms.TreeView> avec des nœuds et des sous-nœuds. Ajoutez ce code à la `Form1` classe.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#1)]

9. Étant donné que le code précédent utilise l’espace de noms System.IO, ajoutez l’instruction using ou import appropriée en haut du formulaire.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#4)]

10. Appelez la méthode de configuration à partir de l’étape précédente dans le constructeur du formulaire ou la <xref:System.Windows.Forms.Form.Load> méthode de gestion d’événements. Ajoutez ce code au constructeur de formulaire.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#2)]

11. Gérez l' <xref:System.Windows.Forms.TreeView.NodeMouseClick> événement pour `treeview1` **,** et implémentez le code pour remplir le `listview1` contenu d’un nœud lorsqu’un utilisateur clique sur un nœud. Ajoutez ce code à la `Form1` classe.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ExplorerStyleInterface#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/VB/Form1.vb#3)]

     Si vous utilisez C#, assurez-vous que l' <xref:System.Windows.Forms.TreeView.NodeMouseClick> événement est associé à sa méthode de gestion d’événements. Ajoutez ce code au constructeur de formulaire.

     [!code-csharp[System.Windows.Forms.ExplorerStyleInterface#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ExplorerStyleInterface/CS/Form1.cs#5)]

## <a name="testing-the-application"></a>Test de l’application

Vous pouvez maintenant tester le formulaire pour vous assurer qu’il se comporte comme prévu.

#### <a name="to-test-the-form"></a>Pour tester le formulaire

- Appuyez sur F5 pour exécuter l'application.

     Vous verrez un formulaire fractionné contenant un <xref:System.Windows.Forms.TreeView> contrôle qui affiche le répertoire de votre projet sur le côté gauche, et un <xref:System.Windows.Forms.ListView> contrôle situé à droite avec trois colonnes. Vous pouvez parcourir le <xref:System.Windows.Forms.TreeView> en sélectionnant des nœuds de répertoire, et le <xref:System.Windows.Forms.ListView> est rempli avec le contenu du répertoire sélectionné.

## <a name="next-steps"></a>Étapes suivantes

Cette application vous donne un exemple de la façon dont vous pouvez utiliser <xref:System.Windows.Forms.TreeView> et les <xref:System.Windows.Forms.ListView> contrôles ensemble. Pour plus d’informations sur ces contrôles, consultez les rubriques suivantes :

- [Guide pratique pour ajouter des informations personnalisées à un contrôle TreeView ou ListView (Windows Forms)](add-custom-information-to-a-treeview-or-listview-control-wf.md)

- [Comment : ajouter des fonctions de recherche à un contrôle ListView](how-to-add-search-capabilities-to-a-listview-control.md)

- [Guide pratique pour attacher un menu contextuel à un nœud TreeView](how-to-attach-a-shortcut-menu-to-a-treeview-node.md)

## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.TreeView>
- [Contrôle ListView](listview-control-windows-forms.md)
- [Comment : ajouter et supprimer des nœuds avec le contrôle TreeView Windows Forms](how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control.md)
- [Guide pratique pour ajouter et supprimer des éléments avec le contrôle ListView Windows Forms](how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)
- [Comment : ajouter des colonnes au contrôle ListView Windows Forms](how-to-add-columns-to-the-windows-forms-listview-control.md)
