---
title: Vue d'ensemble du contrôle DataGridView (Windows Forms)
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
ms.openlocfilehash: 4db2a8b0e30a6bb3db0c5c629d868bc01dc15a8c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648082"
---
# <a name="datagridview-control-overview-windows-forms"></a>Vue d'ensemble du contrôle DataGridView (Windows Forms)
> [!NOTE]
>  Le contrôle <xref:System.Windows.Forms.DataGridView> remplace le contrôle <xref:System.Windows.Forms.DataGrid> et lui ajoute des fonctionnalités ; toutefois, le contrôle <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et l'utilisation future si tel est votre choix. Pour plus d’informations, consultez [Différences entre les contrôles DataGridView et DataGrid Windows Forms](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).  
  
 Avec la <xref:System.Windows.Forms.DataGridView> contrôle, vous pouvez afficher et modifier des données tabulaires à partir de différents types de sources de données.  
  
 Liaison de données à la <xref:System.Windows.Forms.DataGridView> contrôle est simple et intuitive, et dans de nombreux cas, il est aussi simple que le paramètre le <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriété. Lorsque vous liez à une source de données qui contient plusieurs listes ou tables, définissez la <xref:System.Windows.Forms.DataGridView.DataMember%2A> en une chaîne qui spécifie la liste ou la table à lier.  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge le modèle de liaison de données Windows Forms standard, il crée une liaison à des instances des classes décrites dans la liste suivante :  
  
- Toute classe qui implémente le <xref:System.Collections.IList> interface, y compris les tableaux unidimensionnels.  
  
- Toute classe qui implémente le <xref:System.ComponentModel.IListSource> d’interface, tel que le <xref:System.Data.DataTable> et <xref:System.Data.DataSet> classes.  
  
- Toute classe qui implémente le <xref:System.ComponentModel.IBindingList> d’interface, tel que le <xref:System.ComponentModel.BindingList%601> classe.  
  
- Toute classe qui implémente le <xref:System.ComponentModel.IBindingListView> d’interface, tel que le <xref:System.Windows.Forms.BindingSource> classe.  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle prend en charge la liaison de données pour les propriétés publiques des objets retournés par ces interfaces ou à la collection de propriétés retourné par un <xref:System.ComponentModel.ICustomTypeDescriptor> interface, si implémentée sur les objets retournés.  
  
 En règle générale, vous allez lier à un <xref:System.Windows.Forms.BindingSource> composant et lier le <xref:System.Windows.Forms.BindingSource> composant vers un autre source de données ou le remplir avec des objets métier. Le <xref:System.Windows.Forms.BindingSource> composant est la source de données par défaut, car elle peut lier à un large éventail de sources de données et que vous pouvez résoudre de nombreux problèmes de liaison de données automatiquement. Pour plus d’informations, consultez [composant BindingSource](bindingsource-component.md).  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle peut également être utilisé dans *indépendant* mode, sans magasin de données sous-jacent. Pour obtenir un exemple de code qui utilise un indépendant <xref:System.Windows.Forms.DataGridView> du contrôle, consultez [procédure pas à pas : Création d’un indépendant Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
 Le <xref:System.Windows.Forms.DataGridView> contrôle est hautement configurable et extensible, et il fournit de nombreuses propriétés, méthodes et événements pour personnaliser son apparence et son comportement. Lorsque vous souhaitez que votre application Windows Forms pour afficher des données tabulaires, envisagez d’utiliser le <xref:System.Windows.Forms.DataGridView> contrôle avant d’autres (par exemple, <xref:System.Windows.Forms.DataGrid>). Si vous affichez une petite grille de valeurs en lecture seule, ou si vous activez un utilisateur modifier une table avec des millions d’enregistrements, le <xref:System.Windows.Forms.DataGridView> contrôle vous fournira une solution économe en mémoire facilement programmable.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Résumé de la technologie du contrôle DataGridView](datagridview-control-technology-summary-windows-forms.md)  
 Résume <xref:System.Windows.Forms.DataGridView> contrôler les concepts et l’utilisation de classes connexes.  
  
 [Architecture du contrôle DataGridView](datagridview-control-architecture-windows-forms.md)  
 Décrit l’architecture de la <xref:System.Windows.Forms.DataGridView> contrôle, en expliquant sa structure de hiérarchie et l’héritage de type.  
  
 [Scénarios du contrôle DataGridView](datagridview-control-scenarios-windows-forms.md)  
 Décrit les scénarios les plus courants dans lesquels <xref:System.Windows.Forms.DataGridView> les contrôles sont utilisés.  
  
 [Répertoire du code du contrôle DataGridView](datagridview-control-code-directory-windows-forms.md)  
 Fournit des liens vers des exemples de code dans la documentation pour différentes <xref:System.Windows.Forms.DataGridView> tâches. Ces exemples sont classés par type de tâche.  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)  
 Décrit les types de colonne dans les formulaires Windows <xref:System.Windows.Forms.DataGridView> contrôle utilisé pour afficher des informations et permettre aux utilisateurs de modifier ou ajouter des informations.  
  
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
