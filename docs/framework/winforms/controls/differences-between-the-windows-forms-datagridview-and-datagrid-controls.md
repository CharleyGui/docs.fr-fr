---
title: Différences entre les contrôles DataGridView et DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 3552abe55d8e2c1cb4ae372ca64c7ca21f1fed0e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745960"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Différences entre les contrôles DataGridView et DataGrid Windows Forms
Le contrôle <xref:System.Windows.Forms.DataGridView> est un nouveau contrôle qui remplace le contrôle <xref:System.Windows.Forms.DataGrid>. Le contrôle <xref:System.Windows.Forms.DataGridView> fournit de nombreuses fonctionnalités de base et avancées qui manquent dans le contrôle <xref:System.Windows.Forms.DataGrid>. En outre, l’architecture du contrôle de <xref:System.Windows.Forms.DataGridView> facilite l’extension et la personnalisation du contrôle <xref:System.Windows.Forms.DataGrid>.  
  
 Le tableau suivant décrit quelques-unes des principales fonctionnalités disponibles dans le contrôle <xref:System.Windows.Forms.DataGridView> qui manquent dans le contrôle <xref:System.Windows.Forms.DataGrid>.  
  
|Fonctionnalité du contrôle DataGridView|Description|  
|----------------------------------|-----------------|  
|Types de colonnes multiples|Le contrôle <xref:System.Windows.Forms.DataGridView> fournit plus de types de colonne intégrés que le contrôle <xref:System.Windows.Forms.DataGrid>. Ces types de colonnes répondent aux besoins de la plupart des scénarios courants, mais ils sont également plus faciles à étendre ou à remplacer que les types de colonnes dans le contrôle <xref:System.Windows.Forms.DataGrid>. Pour plus d’informations, consultez [types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs manières d’afficher des données|Le contrôle <xref:System.Windows.Forms.DataGrid> est limité à l’affichage des données d’une source de données externe. Toutefois, le contrôle <xref:System.Windows.Forms.DataGridView> peut afficher des données indépendantes stockées dans le contrôle, des données provenant d’une source de données liée ou des données dépendantes et dépendantes. Vous pouvez également implémenter le mode virtuel dans le contrôle <xref:System.Windows.Forms.DataGridView> pour fournir une gestion des données personnalisée. Pour plus d’informations, consultez [modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs manières de personnaliser l’affichage des données|Le contrôle <xref:System.Windows.Forms.DataGridView> fournit un grand nombre de propriétés et d’événements qui vous permettent de spécifier la façon dont les données sont mises en forme et affichées. Par exemple, vous pouvez modifier l’apparence des cellules, des lignes et des colonnes en fonction des données qu’elles contiennent, ou vous pouvez remplacer les données d’un type de données par des données équivalentes d’un autre type. Pour plus d’informations, consultez [mise en forme des données dans le contrôle DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs options pour modifier l’apparence et le comportement des cellules, des lignes, des colonnes et des en-têtes|Le contrôle <xref:System.Windows.Forms.DataGridView> vous permet de travailler avec des composants de grille individuels de plusieurs façons. Par exemple, vous pouvez figer des lignes et des colonnes pour les empêcher de faire défiler. masquer les lignes, les colonnes et les en-têtes ; modifier la façon dont les tailles de ligne, de colonne et d’en-tête sont ajustées ; modifier la façon dont les utilisateurs effectuent des sélections ; et fournissent des info-bulles et des menus contextuels pour des cellules, des lignes et des colonnes.|  
  
 Le contrôle de <xref:System.Windows.Forms.DataGrid> est conservé pour la compatibilité descendante et pour des besoins particuliers. Dans presque tous les cas, vous devez utiliser le contrôle <xref:System.Windows.Forms.DataGridView>. La seule fonctionnalité disponible dans le contrôle <xref:System.Windows.Forms.DataGrid> qui n’est pas disponible dans le contrôle <xref:System.Windows.Forms.DataGridView> est l’affichage hiérarchique des informations de deux tables connexes dans un contrôle unique. Vous devez utiliser deux contrôles <xref:System.Windows.Forms.DataGridView> pour afficher les informations de deux tables qui sont dans une relation maître/détail.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Mise à niveau vers le contrôle DataGridView  
 Si vous avez des applications existantes qui utilisent le contrôle <xref:System.Windows.Forms.DataGrid> dans un scénario simple lié aux données sans personnalisation, vous pouvez simplement remplacer l’ancien contrôle par le nouveau contrôle. Les deux contrôles utilisent l’architecture de liaison de données standard Windows Forms, de sorte que le contrôle <xref:System.Windows.Forms.DataGridView> affiche vos données liées sans aucune configuration supplémentaire. Toutefois, vous pouvez envisager de tirer parti des améliorations de la liaison de données en liant vos données à un composant <xref:System.Windows.Forms.BindingSource>, que vous pouvez ensuite lier au contrôle <xref:System.Windows.Forms.DataGridView>. Pour plus d’informations, consultez [composant BindingSource](bindingsource-component.md).  
  
 Étant donné que le contrôle de <xref:System.Windows.Forms.DataGridView> a une architecture entièrement nouvelle, il n’existe pas de chemin de conversion simple qui vous permettra d’utiliser des personnalisations de <xref:System.Windows.Forms.DataGrid> avec le contrôle <xref:System.Windows.Forms.DataGridView>. Toutefois, de nombreuses personnalisations de <xref:System.Windows.Forms.DataGrid> ne sont pas nécessaires avec le contrôle <xref:System.Windows.Forms.DataGridView>, en raison des fonctionnalités intégrées disponibles dans le nouveau contrôle. Si vous avez créé des types de colonnes personnalisées pour le contrôle <xref:System.Windows.Forms.DataGrid> que vous souhaitez utiliser avec le contrôle <xref:System.Windows.Forms.DataGridView>, vous devez les implémenter à nouveau à l’aide de la nouvelle architecture. Pour plus d’informations, consultez [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [DataGridView, contrôle](datagridview-control-windows-forms.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [BindingSource, composant](bindingsource-component.md)
- [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Mise en forme de données dans le contrôle DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Options de dimensionnement dans le contrôle DataGridView Windows Forms](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Modes de tri des colonnes du contrôle DataGridView Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)
