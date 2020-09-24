---
title: Déduction des relations
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: ee691eee95c34afdb6374cdd7448d4b44ece3055
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177564"
---
# <a name="inferring-relationships"></a>Déduction des relations

Si un élément déduit en tant que table comporte un élément enfant également déduit en tant que table, un objet <xref:System.Data.DataRelation> sera créé entre les deux tables. Une nouvelle colonne portant le nom **ParentTableName_Id** sera ajoutée à la fois à la table créée pour l’élément parent et à la table créée pour l’élément enfant. La propriété **ColumnMapping** de cette colonne d’identité aura pour valeur **MappingType. Hidden**. La colonne sera une clé primaire auto-incrémentée pour la table parente et sera utilisée pour le **DataRelation** entre les deux tables. Le type de données de la colonne d’identité ajoutée sera **System. Int32**, contrairement au type de données de toutes les autres colonnes déduites, qui est **System. String**. Une <xref:System.Data.ForeignKeyConstraint> opération **DeleteRule**en  =  **cascade** DeleteRule est également créée à l’aide de la nouvelle colonne dans les tables parent et enfant.  
  
 Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Le processus d’inférence produira deux tables : **element1** et **ChildElement1**.  
  
 La table **element1** aura deux colonnes : **Element1_Id** et **ChildElement2**. La propriété **ColumnMapping** de la colonne **Element1_Id** aura pour valeur **MappingType. Hidden**. La propriété **ColumnMapping** de la colonne **ChildElement2** est définie sur **MappingType. Element**. La **Element1_Id** colonne sera définie en tant que clé primaire de la table **element1** .  
  
 La table **ChildElement1** comporte trois colonnes : **attr1**, **attr2** et **Element1_Id**. La propriété **ColumnMapping** des colonnes **attr1** et **attr2** aura pour valeur **MappingType. Attribute**. La propriété **ColumnMapping** de la colonne **Element1_Id** aura pour valeur **MappingType. Hidden**.  
  
 Un **DataRelation** et un **ForeignKeyConstraint** seront créés à l’aide des colonnes **Element1_Id** des deux tables.  
  
 **Jeu de données :** DocumentElement  
  
 **Table :** Élément1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Table :** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|valeur1|valeur2|0|  
  
 **DataRelation :** Element1_ChildElement1  
  
 **ParentTable :** Élément1  
  
 **ParentColumn :** Element1_Id  
  
 **ChildTable :** ChildElement1  
  
 **ChildColumn :** Element1_Id  
  
 **Imbriqué :** :  
  
 **ForeignKeyConstraint :** Element1_ChildElement1  
  
 **Colonne :** Element1_Id  
  
 **ParentTable :** Élément1  
  
 **ChildTable :** ChildElement1  
  
 **DeleteRule :** Répercuté  
  
 **AcceptRejectRule :** None  
  
## <a name="see-also"></a>Voir aussi

- [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement d'un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [Imbrication de DataRelations](nesting-datarelations.md)
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
