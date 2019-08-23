---
title: 'Procédure : créer des listes maître/détails avec le contrôle DataGrid Windows Forms à l’aide du concepteur'
ms.date: 03/30/2017
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 19438ba2-f687-4417-a2fb-ab1cd69d4ded
ms.openlocfilehash: 3962b671176ad158b338889140181834e05bbeee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69929722"
---
# <a name="how-to-create-master-details-lists-with-the-windows-forms-datagrid-control-using-the-designer"></a>Procédure : créer des listes maître/détails avec le contrôle DataGrid Windows Forms à l’aide du concepteur

> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).

 Si votre <xref:System.Data.DataSet> contient une série de tables associées, vous pouvez utiliser deux <xref:System.Windows.Forms.DataGrid> contrôles pour afficher les données dans un format maître/détail. L' <xref:System.Windows.Forms.DataGrid> un est désigné comme grille principale et le second est désigné comme grille de détails. Lorsque vous sélectionnez une entrée dans la liste principale, toutes les entrées enfants associées s’affichent dans la liste des détails. Par exemple, si votre <xref:System.Data.DataSet> contient une table Customers et une table Orders associée, vous devez spécifier la table Customers comme grille principale et la table Orders comme grille de détails. Lorsqu’un client est sélectionné dans la grille principale, toutes les commandes associées à ce client dans la table Orders s’affichent dans la grille de détails.

 La procédure suivante requiert un projet d' **application Windows** (**fichier** > **nouveau** > **projet** > **Visual C#**  ou **Visual Basic**  >  > **Application Windows Forms**de bureau classique).

## <a name="to-create-a-master-details-list-in-the-designer"></a>Pour créer une liste Master-Details dans le concepteur

1. Ajoutez deux <xref:System.Windows.Forms.DataGrid> contrôles au formulaire. Pour plus d’informations, consultez [Guide pratique pour Ajoutez des contrôles à](how-to-add-controls-to-windows-forms.md)Windows Forms. Dans Visual Studio 2005, le <xref:System.Windows.Forms.DataGrid> contrôle ne se trouve pas dans la **boîte à outils** par défaut. Pour plus d’informations, consultez [Guide pratique pour Ajoutez des éléments à la](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))boîte à outils.

    > [!NOTE]
    > Les étapes suivantes ne s’appliquent pas à Visual Studio 2005, qui utilise la fenêtre **sources de données** pour la liaison de données au moment du Design. Pour plus d’informations, consultez [lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio) et [procédure: Affichez les données associées dans une](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))application Windows Forms.

2. Faites glisser deux tables ou plus de **Explorateur de serveurs** vers le formulaire.

3. Dans le menu données, sélectionnez **générer le jeu**de **données** .

4. Définissez les relations entre les tables à l’aide du concepteur XML. Pour plus d’informations, consultez la rubrique «Procédure: Créer des relations un-à-plusieurs dans des schémas XML et des datasets sur MSDN.

5. Enregistrez les relations en sélectionnant **enregistrer tout** dans le menu **fichier** .

6. Configurez le <xref:System.Windows.Forms.DataGrid> contrôle que vous souhaitez désigner comme grille principale, comme suit:

    1. Sélectionnez dans la liste déroulante de la <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété. <xref:System.Data.DataSet>

    2. Sélectionnez la table principale (par exemple, «Customers») dans la liste déroulante de <xref:System.Windows.Forms.DataGrid.DataMember%2A> la propriété.

7. Configurez le <xref:System.Windows.Forms.DataGrid> contrôle dont vous souhaitez désigner la grille de détails, comme suit:

    1. Sélectionnez dans la liste déroulante de la <xref:System.Windows.Forms.DataGrid.DataSource%2A> propriété. <xref:System.Data.DataSet>

    2. Sélectionnez la relation (par exemple, «Customers. CustOrd») entre les tables maître et détails dans la liste déroulante de <xref:System.Windows.Forms.DataGrid.DataMember%2A> la propriété. Pour afficher la relation, développez le nœud en cliquant sur le signe plus ( **+** ) en regard de la table principale dans la liste déroulante.

## <a name="see-also"></a>Voir aussi

- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Vue d’ensemble du contrôle DataGrid](datagrid-control-overview-windows-forms.md)
- [Guide pratique : Lier le contrôle Windows Forms DataGrid à une source de données](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
- [Lier des contrôles à des données dans Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
