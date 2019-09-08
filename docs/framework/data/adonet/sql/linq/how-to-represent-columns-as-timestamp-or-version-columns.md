---
title: 'Procédure : Représenter des colonnes en tant que colonnes timestamp ou version'
ms.date: 03/30/2017
ms.assetid: 5afd5ce8-1d20-4bc3-a34f-49d95449f493
ms.openlocfilehash: ef99e0420b328f94686e08256ecf229000467810
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793500"
---
# <a name="how-to-represent-columns-as-timestamp-or-version-columns"></a>Procédure : Représenter des colonnes en tant que colonnes timestamp ou version
Utilisez la [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> propriété de l' <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner un champ ou une propriété comme représentant une colonne de base de données qui contient les horodateurs de base de données ou les numéros de version.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A>.  
  
### <a name="to-designate-a-field-or-property-as-representing-a-timestamp-or-version-column"></a>Pour désigner un champ ou une propriété comme représentant d'une colonne timestamp ou version  
  
1. Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.  
  
2. Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.IsVersion%2A> à la propriété `true`.  
  
## <a name="see-also"></a>Voir aussi

- [Modèle objet LINQ to SQL](the-linq-to-sql-object-model.md)
- [Guide pratique pour Spécifier les membres qui sont testés pour les conflits d’accès concurrentiel](how-to-specify-which-members-are-tested-for-concurrency-conflicts.md)
- [Guide pratique : Personnaliser des classes d’entité à l’aide de l’éditeur de code](how-to-customize-entity-classes-by-using-the-code-editor.md)
