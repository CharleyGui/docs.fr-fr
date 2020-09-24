---
title: Définition de schéma de DataTable
ms.date: 03/30/2017
ms.assetid: efbcdda4-f5a9-421d-8be2-4c194c74552f
ms.openlocfilehash: 0c14c6012c65039e1e2e7e2d2d8c38c4202b45a7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153246"
---
# <a name="datatable-schema-definition"></a>Définition de schéma de DataTable

Le schéma, ou structure, d'une table est représenté par des colonnes et des contraintes. Vous définissez le schéma d'un objet <xref:System.Data.DataTable> à l'aide d'objets <xref:System.Data.DataColumn> ainsi que d'objets <xref:System.Data.ForeignKeyConstraint> et <xref:System.Data.UniqueConstraint>. Les colonnes d'une table peuvent mapper aux colonnes d'une source de données. Elles contiennent des valeurs calculées à partir d'expressions, incrémentent automatiquement leurs valeurs ou contiennent des valeurs de clé primaire.  
  
 Les références par nom aux colonnes, relations et contraintes d'une table respectent la casse. Une table peut donc contenir plusieurs colonnes, relations ou contraintes dont les noms ne diffèrent que par la casse. Par exemple, vous pouvez avoir **col1** et **col1**. Dans ce cas, une référence par nom à l'une des colonnes doit correspondre exactement à la casse du nom de colonne. Sinon, une exception est levée. Par exemple, si la table **MyTable** contient les colonnes **col1** et **col1**, vous devez référencer **col1** par nom comme **MyTable. Columns ["col1"]** et **col1** comme **MyTable. Columns ["col1"]**. Toute tentative de référence à l’une des colonnes comme **MyTable. Columns ["col1"]** générerait une exception.  
  
 La règle de respect de la casse ne s'applique pas s'il n'existe qu'une seule colonne, relation ou contrainte ayant un nom particulier. En d'autres termes, si aucun autre objet de colonne, relation ou contrainte de la table ne correspond au nom de cet objet de colonne, relation ou contrainte, vous pouvez référencer l'objet par son nom sans respecter la casse, sans qu'une exception ne soit levée. Par exemple, si la table n’a que **col1**, vous pouvez la référencer à l’aide de **My. Columns ["COL1"]**.  
  
> [!NOTE]
> La <xref:System.Data.DataTable.CaseSensitive%2A> propriété du **DataTable** n’affecte pas ce comportement. La propriété **CaseSensitive** s’applique aux données d’une table et affecte les contraintes de tri, de recherche, de filtrage, d’application, etc., mais pas les références aux colonnes, relations et contraintes.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Ajout de colonnes à un DataTable](adding-columns-to-a-datatable.md)  
 Décrit comment définir les colonnes d’une table à l’aide d’objets **DataColumn** .  
  
 [Création de colonnes d'expressions](creating-expression-columns.md)  
 Explique comment la propriété **expression** d’une colonne peut être utilisée pour calculer des valeurs en fonction des valeurs d’autres colonnes de la ligne.  
  
 [Création de colonnes AutoIncrement](creating-autoincrement-columns.md)  
 Décrit comment définir une colonne afin qu'elle incrémente automatiquement des valeurs numériques de façon à garantir le caractère unique des valeurs de colonne d'une ligne.  
  
 [Définition des clés primaires](defining-primary-keys.md)  
 Décrit comment spécifier la clé primaire d’une table à partir d’un ou de plusieurs objets **DataColumn** .  
  
 [Contraintes de DataTable](datatable-constraints.md)  
 Décrit comment définir des contraintes uniques et de clé étrangère pour les colonnes d'une table.  
  
## <a name="see-also"></a>Voir aussi

- [DataTables](datatables.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
