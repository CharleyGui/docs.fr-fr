---
title: Vue d'ensemble du contrôle DataGridView
description: Découvrez comment utiliser le contrôle DataGridView Windows Forms pour afficher et modifier des données tabulaires à partir de nombreux types de sources de données différents.
ms.date: 03/30/2017
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174612"
---
# <a name="datagridview-control-overview-windows-forms"></a>Vue d'ensemble du contrôle DataGridView (Windows Forms)
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Avec le <xref:System.Windows.Forms.DataGridView> contrôle, vous pouvez afficher et modifier des données tabulaires à partir de nombreux types de sources de données différents.  
  
 La liaison de données au <xref:System.Windows.Forms.DataGridView> contrôle est simple et intuitive, et dans de nombreux cas, c’est aussi simple que de définir la <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriété. Quand vous créez une liaison à une source de données qui contient plusieurs listes ou tables, affectez <xref:System.Windows.Forms.DataGridView.DataMember%2A> à la propriété une chaîne qui spécifie la liste ou la table à lier.  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge le modèle de liaison de données standard Windows Forms. il est donc lié aux instances de classes décrites dans la liste suivante :  
  
- Toute classe qui implémente l' <xref:System.Collections.IList> interface, y compris les tableaux unidimensionnels.  
  
- Toute classe qui implémente l' <xref:System.ComponentModel.IListSource> interface, telle que les <xref:System.Data.DataTable> <xref:System.Data.DataSet> classes et.  
  
- Toute classe qui implémente l' <xref:System.ComponentModel.IBindingList> interface, telle que la <xref:System.ComponentModel.BindingList%601> classe.  
  
- Toute classe qui implémente l' <xref:System.ComponentModel.IBindingListView> interface, telle que la <xref:System.Windows.Forms.BindingSource> classe.  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge la liaison de données aux propriétés publiques des objets retournés par ces interfaces ou à la collection de propriétés retournée par une <xref:System.ComponentModel.ICustomTypeDescriptor> interface, si elle est implémentée sur les objets retournés.  
  
 En règle générale, vous allez créer une liaison <xref:System.Windows.Forms.BindingSource> avec un composant et lier le <xref:System.Windows.Forms.BindingSource> composant à une autre source de données ou le remplir avec des objets métier. Le <xref:System.Windows.Forms.BindingSource> composant est la source de données par défaut, car il peut être lié à une grande variété de sources de données et peut résoudre automatiquement de nombreux problèmes de liaison de données. Pour plus d’informations, consultez [composant BindingSource](bindingsource-component.md).  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle peut également être utilisé en mode *indépendant* , sans magasin de données sous-jacent. Pour obtenir un exemple de code qui utilise un <xref:System.Windows.Forms.DataGridView> contrôle indépendant, consultez [procédure pas à pas : création d’un contrôle DataGridView Windows Forms indépendant](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle est hautement configurable et extensible, et fournit de nombreuses propriétés, méthodes et événements pour personnaliser son apparence et son comportement. Lorsque vous souhaitez que votre application Windows Forms affiche des données tabulaires, envisagez d’utiliser le <xref:System.Windows.Forms.DataGridView> contrôle avant d’autres (par exemple, <xref:System.Windows.Forms.DataGrid> ). Si vous affichez une petite grille de valeurs en lecture seule, ou si vous permettez à un utilisateur de modifier une table avec des millions d’enregistrements, le <xref:System.Windows.Forms.DataGridView> contrôle vous fournira une solution économe en mémoire et facilement programmable.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Résumé de la technologie du contrôle DataGridView](datagridview-control-technology-summary-windows-forms.md)  
 Résume <xref:System.Windows.Forms.DataGridView> les concepts des contrôles et l’utilisation des classes associées.  
  
 [Architecture du contrôle DataGridView](datagridview-control-architecture-windows-forms.md)  
 Décrit l’architecture du <xref:System.Windows.Forms.DataGridView> contrôle, en expliquant sa hiérarchie de types et sa structure d’héritage.  
  
 [Scénarios du contrôle DataGridView](datagridview-control-scenarios-windows-forms.md)  
 Décrit les scénarios les plus courants dans lesquels les <xref:System.Windows.Forms.DataGridView> contrôles sont utilisés.  
  
 [Répertoire de code du contrôle DataGridView](datagridview-control-code-directory-windows-forms.md)  
 Fournit des liens vers des exemples de code dans la documentation relative à différentes <xref:System.Windows.Forms.DataGridView> tâches. Ces exemples sont classés par type de tâche.  
  
## <a name="related-sections"></a>Sections connexes  
 [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)  
 Décrit les types de colonnes dans le <xref:System.Windows.Forms.DataGridView> contrôle Windows Forms utilisé pour afficher des informations et permettre aux utilisateurs de modifier ou d’ajouter des informations.  
  
 [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent comment remplir le contrôle de données manuellement ou à partir d'une source de données externe.  
  
 [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent la peinture personnalisée des cellules et des lignes <xref:System.Windows.Forms.DataGridView> et la création de types de lignes, de colonnes et de cellules dérivés.  
  
 [Réglage des performances dans le contrôle DataGridView Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui expliquent comment utiliser efficacement le contrôle pour éviter les problèmes de performances lors de l'utilisation de grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Contrôle DataGridView](datagridview-control-windows-forms.md)
- [Fonctionnalités par défaut du contrôle DataGridView Windows Forms](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Gestion par défaut du clavier et de la souris dans le contrôle DataGridView Windows Forms](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
