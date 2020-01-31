---
title: Créer des listes maître/détails avec le contrôle DataGrid à l’aide du concepteur
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 0dea3dd88a8c6c2aceb894789ace8ef3b5c83632
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743387"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Comment : créer des listes maître/détails avec le contrôle DataGrid Windows Forms à l'aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Si votre <xref:System.Data.DataSet> contient une série de tables associées, vous pouvez utiliser deux contrôles <xref:System.Windows.Forms.DataGrid> pour afficher les données dans un format maître/détail. Un <xref:System.Windows.Forms.DataGrid> est désigné comme grille principale et le second est désigné comme grille de détails. Lorsque vous sélectionnez une entrée dans la liste principale, toutes les entrées enfants associées s’affichent dans la liste des détails. Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table Orders associée, vous devez spécifier la table Customers comme grille principale et la table Orders comme grille de détails. Lorsqu’un client est sélectionné dans la grille principale, toutes les commandes associées à ce client dans la table Orders s’affichent dans la grille de détails.

 La procédure suivante nécessite un projet d' **application Windows** (**fichier** > nouveau **projet** de >  >  **C# Visual** ou **Visual Basic** > **application** > **de** **Bureau classique** ).

## <a name="to-create-a-master-details-list-in-the-designer"></a>Pour créer une liste Master-Details dans le concepteur

1. Ajoutez deux contrôles <xref:System.Windows.Forms.DataGrid> au formulaire. Pour plus d’informations, consultez [Comment : ajouter des contrôles à des Windows Forms](how-to-add-controls-to-windows-forms.md). Dans Visual Studio 2005, le contrôle <xref:System.Windows.Forms.DataGrid> ne se trouve pas dans la **boîte à outils** par défaut. Pour plus d’informations, consultez [Comment : ajouter des éléments à la boîte à outils](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100)).

    > [!NOTE]
    > Les étapes suivantes ne s’appliquent pas à Visual Studio 2005, qui utilise la fenêtre **sources de données** pour la liaison de données au moment du Design. Pour plus d’informations, consultez [lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) et [Comment : afficher des données connexes dans une application Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).

2. Faites glisser deux tables ou plus de **Explorateur de serveurs** vers le formulaire.

3. Dans le menu données, sélectionnez **générer le jeu**de **données** .

4. Définissez les relations entre les tables à l’aide du concepteur XML. Pour plus d’informations, consultez « Procédure : créer des relations un-à-plusieurs dans les schémas XML et les datasets » sur MSDN.

5. Enregistrez les relations en sélectionnant **enregistrer tout** dans le menu **fichier** .

6. Configurez le contrôle de <xref:System.Windows.Forms.DataGrid> que vous souhaitez désigner comme grille principale, comme suit :

    1. Sélectionnez la <xref:System.Data.DataSet> dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A>.

    2. Sélectionnez la table principale (par exemple, « Customers ») dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A>.

7. Configurez le contrôle de <xref:System.Windows.Forms.DataGrid> que vous souhaitez désigner comme grille des détails, comme suit :

    1. Sélectionnez la <xref:System.Data.DataSet> dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGrid.DataSource%2A>.

    2. Sélectionnez la relation (par exemple, « Customers. CustOrd ») entre les tables maître et détails dans la liste déroulante de la propriété <xref:System.Windows.Forms.DataGrid.DataMember%2A>. Pour afficher la relation, développez le nœud en cliquant sur le signe plus ( **+** ) en regard de la table principale dans la liste déroulante.

## <a name="see-also"></a>Voir aussi

- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Vue d’ensemble du contrôle DataGrid](datagrid-control-overview-windows-forms.md)
- [Guide pratique pour lier le contrôle DataGrid Windows Forms à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
