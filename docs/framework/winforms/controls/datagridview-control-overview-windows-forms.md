---
title: Vue d'ensemble du contrôle DataGridView
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
ms.openlocfilehash: 74de5b449525be9ff93fcbef0ddabd041470177c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742492"
---
# <a name="datagridview-control-overview-windows-forms"></a>Vue d'ensemble du contrôle DataGridView (Windows Forms)
> [!NOTE]
> Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous pouvez afficher et modifier des données tabulaires à partir de nombreux types de sources de données différents.  
  
 La liaison de données au contrôle <xref:System.Windows.Forms.DataGridView> est simple et intuitive, et dans de nombreux cas, c’est aussi simple que de définir la propriété <xref:System.Windows.Forms.DataGridView.DataSource%2A>. Lorsque vous créez une liaison à une source de données qui contient plusieurs listes ou tables, définissez la propriété <xref:System.Windows.Forms.DataGridView.DataMember%2A> sur une chaîne qui spécifie la liste ou la table à lier.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge le modèle de liaison de données standard Windows Forms. il est donc lié aux instances de classes décrites dans la liste suivante :  
  
- Toute classe qui implémente l’interface <xref:System.Collections.IList>, y compris les tableaux unidimensionnels.  
  
- Toute classe qui implémente l’interface <xref:System.ComponentModel.IListSource>, telle que les classes <xref:System.Data.DataTable> et <xref:System.Data.DataSet>.  
  
- Toute classe qui implémente l’interface <xref:System.ComponentModel.IBindingList>, telle que la classe <xref:System.ComponentModel.BindingList%601>.  
  
- Toute classe qui implémente l’interface <xref:System.ComponentModel.IBindingListView>, telle que la classe <xref:System.Windows.Forms.BindingSource>.  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> prend en charge la liaison de données aux propriétés publiques des objets retournés par ces interfaces ou à la collection de propriétés retournée par une interface <xref:System.ComponentModel.ICustomTypeDescriptor>, si elle est implémentée sur les objets retournés.  
  
 En règle générale, vous allez créer une liaison avec un composant <xref:System.Windows.Forms.BindingSource> et lier le composant <xref:System.Windows.Forms.BindingSource> à une autre source de données ou le remplir avec des objets métier. Le composant <xref:System.Windows.Forms.BindingSource> est la source de données par défaut, car il peut être lié à une grande variété de sources de données et peut résoudre automatiquement de nombreux problèmes de liaison de données. Pour plus d’informations, consultez [composant BindingSource](bindingsource-component.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> peut également être utilisé en mode *indépendant* , sans magasin de données sous-jacent. Pour obtenir un exemple de code qui utilise un contrôle de <xref:System.Windows.Forms.DataGridView> indépendant, consultez [procédure pas à pas : création d’un contrôle DataGridView Windows Forms indépendant](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 Le contrôle <xref:System.Windows.Forms.DataGridView> est hautement configurable et extensible, et fournit de nombreuses propriétés, méthodes et événements pour personnaliser son apparence et son comportement. Lorsque vous souhaitez que votre application Windows Forms affiche des données tabulaires, envisagez d’utiliser le contrôle <xref:System.Windows.Forms.DataGridView> avant d’autres (par exemple, <xref:System.Windows.Forms.DataGrid>). Si vous affichez une petite grille de valeurs en lecture seule, ou si vous permettez à un utilisateur de modifier une table avec des millions d’enregistrements, le contrôle <xref:System.Windows.Forms.DataGridView> vous fournira une solution économe en mémoire et facilement programmable.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Résumé de la technologie du contrôle DataGridView](datagridview-control-technology-summary-windows-forms.md)  
 Résume les concepts de contrôle <xref:System.Windows.Forms.DataGridView> et l’utilisation de classes associées.  
  
 [Architecture du contrôle DataGridView](datagridview-control-architecture-windows-forms.md)  
 Décrit l’architecture du contrôle <xref:System.Windows.Forms.DataGridView>, en expliquant sa hiérarchie de types et sa structure d’héritage.  
  
 [Scénarios du contrôle DataGridView](datagridview-control-scenarios-windows-forms.md)  
 Décrit les scénarios les plus courants dans lesquels les contrôles <xref:System.Windows.Forms.DataGridView> sont utilisés.  
  
 [Répertoire du code du contrôle DataGridView](datagridview-control-code-directory-windows-forms.md)  
 Fournit des liens vers des exemples de code dans la documentation pour différentes tâches de <xref:System.Windows.Forms.DataGridView>. Ces exemples sont classés par type de tâche.  
  
## <a name="related-sections"></a>Sections connexes  
 [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)  
 Décrit les types de colonnes dans le contrôle Windows Forms <xref:System.Windows.Forms.DataGridView> utilisé pour afficher des informations et permettre aux utilisateurs de modifier ou d’ajouter des informations.  
  
 [Affichage des données dans le contrôle DataGridView Windows Forms](displaying-data-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent comment remplir le contrôle de données manuellement ou à partir d'une source de données externe.  
  
 [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui décrivent la peinture personnalisée des cellules et des lignes <xref:System.Windows.Forms.DataGridView> et la création de types de lignes, de colonnes et de cellules dérivés.  
  
 [Réglage des performances dans le contrôle DataGridView Windows Forms](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 Fournit des rubriques qui expliquent comment utiliser efficacement le contrôle pour éviter les problèmes de performances lors de l'utilisation de grandes quantités de données.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView, contrôle](datagridview-control-windows-forms.md)
- [Fonctionnalités par défaut du contrôle DataGridView Windows Forms](default-functionality-in-the-windows-forms-datagridview-control.md)
- [Gestion par défaut du clavier et de la souris dans le contrôle DataGridView Windows Forms](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
