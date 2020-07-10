---
title: Différences entre les contrôles DataGridView et DataGrid
description: Découvrez les différentes différences entre les fonctionnalités des contrôles DataGridView et DataGrid Windows Forms, ainsi que les différences dans leur architecture.
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms
- DataGrid control [Windows Forms], DataGridView control compared
- DataGridView control [Windows Forms], DataGrid control compared
ms.assetid: d412c786-140e-4210-8a56-a68467530a55
ms.openlocfilehash: 1438182d764097ae4f8fd7df046ad72c9213da19
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174586"
---
# <a name="differences-between-the-windows-forms-datagridview-and-datagrid-controls"></a>Différences entre les contrôles DataGridView et DataGrid Windows Forms
Le <xref:System.Windows.Forms.DataGridView> contrôle est un nouveau contrôle qui remplace le <xref:System.Windows.Forms.DataGrid> contrôle. Le <xref:System.Windows.Forms.DataGridView> contrôle fournit de nombreuses fonctionnalités de base et avancées qui manquent dans le <xref:System.Windows.Forms.DataGrid> contrôle. En outre, l’architecture du <xref:System.Windows.Forms.DataGridView> contrôle facilite grandement l’extension et la personnalisation par rapport au <xref:System.Windows.Forms.DataGrid> contrôle.  
  
 Le tableau suivant décrit quelques-unes des principales fonctionnalités disponibles dans le <xref:System.Windows.Forms.DataGridView> contrôle qui sont absentes du <xref:System.Windows.Forms.DataGrid> contrôle.  
  
|Fonctionnalité du contrôle DataGridView|Description|  
|----------------------------------|-----------------|  
|Types de colonnes multiples|Le <xref:System.Windows.Forms.DataGridView> contrôle fournit plus de types de colonne intégrés que le <xref:System.Windows.Forms.DataGrid> contrôle. Ces types de colonnes répondent aux besoins de la plupart des scénarios courants, mais ils sont également plus faciles à étendre ou à remplacer que les types de colonnes dans le <xref:System.Windows.Forms.DataGrid> contrôle. Pour plus d’informations, consultez [types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs manières d’afficher des données|Le <xref:System.Windows.Forms.DataGrid> contrôle est limité à l’affichage des données d’une source de données externe. <xref:System.Windows.Forms.DataGridView>Toutefois, le contrôle peut afficher les données indépendantes stockées dans le contrôle, les données d’une source de données liée, ou les données liées et non liées. Vous pouvez également implémenter le mode virtuel dans le <xref:System.Windows.Forms.DataGridView> contrôle pour fournir une gestion des données personnalisée. Pour plus d’informations, consultez [modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs manières de personnaliser l’affichage des données|Le <xref:System.Windows.Forms.DataGridView> contrôle fournit un grand nombre de propriétés et d’événements qui vous permettent de spécifier la façon dont les données sont mises en forme et affichées. Par exemple, vous pouvez modifier l’apparence des cellules, des lignes et des colonnes en fonction des données qu’elles contiennent, ou vous pouvez remplacer les données d’un type de données par des données équivalentes d’un autre type. Pour plus d’informations, consultez [mise en forme des données dans le contrôle DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md).|  
|Plusieurs options pour modifier l’apparence et le comportement des cellules, des lignes, des colonnes et des en-têtes|Le <xref:System.Windows.Forms.DataGridView> contrôle vous permet de travailler avec des composants de grille individuels de plusieurs façons. Par exemple, vous pouvez figer des lignes et des colonnes pour les empêcher de faire défiler. masquer les lignes, les colonnes et les en-têtes ; modifier la façon dont les tailles de ligne, de colonne et d’en-tête sont ajustées ; modifier la façon dont les utilisateurs effectuent des sélections ; et fournissent des info-bulles et des menus contextuels pour des cellules, des lignes et des colonnes.|  
  
 Le <xref:System.Windows.Forms.DataGrid> contrôle est conservé pour la compatibilité descendante et pour des besoins particuliers. Dans presque tous les cas, vous devez utiliser le <xref:System.Windows.Forms.DataGridView> contrôle. La seule fonctionnalité disponible dans le <xref:System.Windows.Forms.DataGrid> contrôle qui n’est pas disponible dans le <xref:System.Windows.Forms.DataGridView> contrôle est l’affichage hiérarchique des informations de deux tables connexes dans un contrôle unique. Vous devez utiliser deux <xref:System.Windows.Forms.DataGridView> contrôles pour afficher les informations de deux tables qui sont dans une relation maître/détail.  
  
## <a name="upgrading-to-the-datagridview-control"></a>Mise à niveau vers le contrôle DataGridView  
 Si vous avez des applications existantes qui utilisent le <xref:System.Windows.Forms.DataGrid> contrôle dans un scénario simple lié aux données sans personnalisation, vous pouvez simplement remplacer l’ancien contrôle par le nouveau contrôle. Les deux contrôles utilisent l’architecture de liaison de données standard Windows Forms, de sorte que le <xref:System.Windows.Forms.DataGridView> contrôle affiche vos données liées sans aucune configuration supplémentaire. Toutefois, vous pouvez envisager de tirer parti des améliorations de la liaison de données en liant vos données à un <xref:System.Windows.Forms.BindingSource> composant, que vous pouvez ensuite lier au <xref:System.Windows.Forms.DataGridView> contrôle. Pour plus d’informations, consultez [composant BindingSource](bindingsource-component.md).  
  
 Étant donné que le <xref:System.Windows.Forms.DataGridView> contrôle a une architecture entièrement nouvelle, il n’existe pas de chemin de conversion simple qui vous permettra d’utiliser <xref:System.Windows.Forms.DataGrid> des personnalisations avec le <xref:System.Windows.Forms.DataGridView> contrôle. <xref:System.Windows.Forms.DataGrid>Toutefois, de nombreuses personnalisations ne sont pas nécessaires avec le contrôle, en <xref:System.Windows.Forms.DataGridView> raison des fonctionnalités intégrées disponibles dans le nouveau contrôle. Si vous avez créé des types de colonnes personnalisés pour le <xref:System.Windows.Forms.DataGrid> contrôle que vous souhaitez utiliser avec le <xref:System.Windows.Forms.DataGridView> contrôle, vous devez les implémenter à nouveau à l’aide de la nouvelle architecture. Pour plus d’informations, consultez [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGrid>
- <xref:System.Windows.Forms.BindingSource>
- [Contrôle DataGridView](datagridview-control-windows-forms.md)
- [DataGrid, contrôle](datagrid-control-windows-forms.md)
- [Composant BindingSource](bindingsource-component.md)
- [Types de colonnes dans le contrôle DataGridView Windows Forms](column-types-in-the-windows-forms-datagridview-control.md)
- [Styles de cellules dans le contrôle DataGridView Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Modes d’affichage des données dans le contrôle DataGridView Windows Forms](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Mise en forme de données dans le contrôle DataGridView Windows Forms](data-formatting-in-the-windows-forms-datagridview-control.md)
- [Sizing Options in the Windows Forms DataGridView Control](sizing-options-in-the-windows-forms-datagridview-control.md)
- [Modes de tri des colonnes du contrôle DataGridView Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Modes de sélection dans le contrôle DataGridView Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md)
- [Personnalisation du contrôle DataGridView Windows Forms](customizing-the-windows-forms-datagridview-control.md)
