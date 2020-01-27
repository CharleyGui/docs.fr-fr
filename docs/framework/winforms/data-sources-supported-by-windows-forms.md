---
title: Sources de données prises en charge
ms.date: 03/30/2017
helpviewer_keywords:
- collections [Windows Forms], binding to
- OLE DB providers [Windows Forms], Windows Forms
- DataTable class [Windows Forms], binding and Windows Forms
- Windows Forms, data binding
- DataView class [Windows Forms], binding and Windows Forms
- DataViewManager class [Windows Forms], binding and Windows Forms
- Windows Forms, source data
- arrays [Windows Forms]
- data sources [Windows Forms]
- data providers [Windows Forms]
- DataSet class [Windows Forms], binding and Windows Forms
- data [Windows Forms], data providers
ms.assetid: 3d2c43f6-462b-4d35-9c86-13e9afe012e1
ms.openlocfilehash: 83ce4bb0d6f0bf81bcad4e38af212dccc3483ca5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742313"
---
# <a name="data-sources-supported-by-windows-forms"></a>Sources de données prises en charge par les Windows Forms
Traditionnellement, la liaison de données a été utilisée dans les applications pour tirer parti des données stockées dans les bases de données. Avec Windows Forms la liaison de données, vous pouvez accéder aux données des bases de données ainsi qu’aux données d’autres structures, telles que les tableaux et les collections, tant que certaines exigences minimales ont été respectées.  
  
## <a name="structures-to-bind-to"></a>Structures à lier  
 Dans Windows Forms, vous pouvez lier à une grande variété de structures, à partir d’objets simples (liaison simple) à des listes complexes, telles que des tables de données ADO.NET (liaison complexe). Pour une liaison simple, Windows Forms prend en charge la liaison aux propriétés publiques sur l’objet simple. Windows Forms la liaison basée sur une liste requiert généralement que l’objet prenne en charge l’interface <xref:System.Collections.IList> ou l’interface <xref:System.ComponentModel.IListSource>. En outre, si vous effectuez une liaison avec via un composant <xref:System.Windows.Forms.BindingSource>, vous pouvez effectuer une liaison à un objet qui prend en charge l’interface <xref:System.Collections.IEnumerable>. Pour plus d’informations sur les interfaces associées à la liaison de données, consultez [interfaces associées à la liaison de données](interfaces-related-to-data-binding.md).  
  
 La liste suivante répertorie les structures auxquelles vous pouvez établir une liaison dans Windows Forms.  
  
 <xref:System.Windows.Forms.BindingSource>  
 Une <xref:System.Windows.Forms.BindingSource> est la source de données Windows Forms la plus courante et agit un proxy entre une source de données et les contrôles de Windows Forms. Le modèle d’utilisation générale <xref:System.Windows.Forms.BindingSource> consiste à lier vos contrôles à la <xref:System.Windows.Forms.BindingSource> et à lier les <xref:System.Windows.Forms.BindingSource> à la source de données (par exemple, une table de données ADO.NET ou un objet métier). Le <xref:System.Windows.Forms.BindingSource> fournit des services qui activent et améliorent le niveau de prise en charge de la liaison de données. Par exemple, Windows Forms des contrôles basés sur la liste, tels que les <xref:System.Windows.Forms.DataGridView> et les <xref:System.Windows.Forms.ComboBox> ne prennent pas directement en charge la liaison à des sources de données <xref:System.Collections.IEnumerable>, vous pouvez activer ce scénario par liaison à l’aide d’une <xref:System.Windows.Forms.BindingSource>. Dans ce cas, le <xref:System.Windows.Forms.BindingSource> convertira la source de données en <xref:System.Collections.IList>.  
  
 Objets simples  
 Windows Forms prend en charge les propriétés de contrôle de liaison de données dans les propriétés publiques de l’instance d’un objet à l’aide du type de <xref:System.Windows.Forms.Binding>. Windows Forms prend également en charge la liaison de contrôles basés sur des listes, tels qu’un <xref:System.Windows.Forms.ListControl> à une instance d’objet lorsqu’un <xref:System.Windows.Forms.BindingSource> est utilisé.  
  
 tableau ou collection  
 Pour agir en tant que source de données, une liste doit implémenter l’interface <xref:System.Collections.IList> ; un tableau qui est une instance de la classe <xref:System.Array> en est un exemple. Pour plus d’informations sur les tableaux, consultez [Comment : créer un tableau d’objets (Visual Basic)](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/487y7874(v=vs.100)).  
  
 En général, vous devez utiliser <xref:System.ComponentModel.BindingList%601> lorsque vous créez des listes d’objets pour la liaison de données. <xref:System.ComponentModel.BindingList%601> est une version générique de l’interface <xref:System.ComponentModel.IBindingList>. L’interface <xref:System.ComponentModel.IBindingList> étend l’interface <xref:System.Collections.IList> en ajoutant des propriétés, des méthodes et des événements nécessaires pour la liaison de données bidirectionnelle.  
  
 <xref:System.Collections.IEnumerable>  
 Windows Forms contrôles peuvent être liés à des sources de données qui ne prennent en charge que l’interface <xref:System.Collections.IEnumerable> si elles sont liées via un composant <xref:System.Windows.Forms.BindingSource>.  
  
 Objets de données ADO.NET  
 ADO.NET fournit un certain nombre de structures de données adaptées à la liaison. Chacun varie en fonction de sa complexité et de son sophistication.  
  
- <xref:System.Data.DataColumn>. Un <xref:System.Data.DataColumn> est le bloc de construction essentiel d’un <xref:System.Data.DataTable>, dans le fait qu’un certain nombre de colonnes comportent une table. Chaque <xref:System.Data.DataColumn> a une propriété <xref:System.Data.DataColumn.DataType%2A> qui détermine le type de données que contient la colonne (par exemple, la marque d’une automobile dans une table décrivant des voitures). Vous pouvez facilement lier un contrôle (par exemple, la propriété <xref:System.Windows.Forms.Control.Text%2A> d’un contrôle <xref:System.Windows.Forms.TextBox>) à une colonne dans une table de données.  
  
- <xref:System.Data.DataTable>. Une <xref:System.Data.DataTable> est la représentation d’une table, avec des lignes et des colonnes, dans ADO.NET. Une table de données contient deux collections : <xref:System.Data.DataColumn>, représentant les colonnes de données d’une table donnée (qui déterminent en fin de compte les types de données qui peuvent être entrées dans cette table) et <xref:System.Data.DataRow>, représentant les lignes de données d’une table donnée. Vous pouvez lier un contrôle de manière complexe aux informations contenues dans une table de données (par exemple, en liant le contrôle <xref:System.Windows.Forms.DataGridView> à une table de données). Toutefois, lorsque vous effectuez une liaison à une <xref:System.Data.DataTable>, vous êtes véritablement lié à la vue par défaut de la table.  
  
- <xref:System.Data.DataView>. Une <xref:System.Data.DataView> est une vue personnalisée d’une table de données qui peut être filtrée ou triée. Une vue de données est l’instantané de données utilisé par les contrôles liés complexes. Vous pouvez effectuer une liaison simple ou une liaison complexe aux données d’une vue de données, mais sachez que vous êtes lié à une « image » fixe des données plutôt qu’à une source de données propre et en cours de mise à jour.  
  
- <xref:System.Data.DataSet>. Une <xref:System.Data.DataSet> est une collection de tables, de relations et de contraintes de données dans une base de données. Vous pouvez effectuer une liaison simple ou une liaison complexe aux données d’un DataSet, mais sachez que vous êtes lié au <xref:System.Data.DataViewManager> par défaut pour le <xref:System.Data.DataSet> (voir le point à puce suivant).  
  
- <xref:System.Data.DataViewManager>. Une <xref:System.Data.DataViewManager> est une vue personnalisée du <xref:System.Data.DataSet>entier, analogue à un <xref:System.Data.DataView>, mais avec des relations incluses. Avec une collection <xref:System.Data.DataViewManager.DataViewSettings%2A>, vous pouvez définir des filtres et des options de tri par défaut pour toutes les vues que l' <xref:System.Data.DataViewManager> a pour une table donnée.  
  
## <a name="see-also"></a>Voir aussi

- [Notification de modifications dans la liaison de données Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Liaison de données et Windows Forms](data-binding-and-windows-forms.md)
- [Liaison de données Windows Forms](windows-forms-data-binding.md)
