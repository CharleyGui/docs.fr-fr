---
title: Déduction des relations
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 92a4953dc7f5119ffbf171ff2a7bf5b58e896638
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204774"
---
# <a name="inferring-relationships"></a>Déduction des relations
Si un élément déduit en tant que table comporte un élément enfant également déduit en tant que table, un objet <xref:System.Data.DataRelation> sera créé entre les deux tables. Une nouvelle colonne portant le nom **ParentTableName_Id** sera ajoutée à la fois à la table créée pour l’élément parent et à la table créée pour l’élément enfant. La propriété **ColumnMapping** de cette colonne d’identité aura pour valeur **MappingType. Hidden**. La colonne sera une clé primaire auto-incrémentée pour la table parente et sera utilisée pour le **DataRelation** entre les deux tables. Le type de données de la colonne d’identité ajoutée sera **System. Int32**, contrairement au type de données de toutes les autres colonnes déduites, qui est **System. String**. Une <xref:System.Data.ForeignKeyConstraint> opération en**cascade** **DeleteRule** = est également créée à l’aide de la nouvelle colonne dans les tables parent et enfant.  
  
 Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produira deux tables :  **Element1** et **ChildElement1**.  
  
 La table **element1** aura deux colonnes: **Element1_Id** et **ChildElement2**. La propriété **ColumnMapping** de la colonne **Element1_Id** aura pour valeur **MappingType. Hidden**. La propriété **ColumnMapping** de la colonne **ChildElement2** est définie sur **MappingType. Element**. La colonne **Element1_Id** est définie en tant que clé primaire de la table **element1** .  
  
 La table **ChildElement1** aura trois colonnes: **attr1**, **attr2** et **Element1_Id**. La propriété **ColumnMapping** des colonnes **attr1** et **attr2** aura pour valeur **MappingType. Attribute**. La propriété **ColumnMapping** de la colonne **Element1_Id** aura pour valeur **MappingType. Hidden**.  
  
 Un **DataRelation** et un **ForeignKeyConstraint** seront créés à l’aide des colonnes **Element1_Id** des deux tables.  
  
 **Ensemble** DocumentElement  
  
 **Table :** Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **Table :** ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|valeur1|valeur2|0|  
  
 **DataRelation** Element1_ChildElement1  
  
 **ParentTable:** Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable** ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **Imbriquée** True  
  
 **ForeignKeyConstraint** Element1_ChildElement1  
  
 **Chronique** Element1_Id  
  
 **ParentTable:** Element1  
  
 **ChildTable** ChildElement1  
  
 **DeleteRule** Cascade  
  
 **AcceptRejectRule** Aucun  
  
## <a name="see-also"></a>Voir aussi

- [Inférence de la structure relationnelle d’un DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement d’un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [Imbrication de DataRelations](nesting-datarelations.md)
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DataSets, DataTables et DataViews](index.md)
- [Fournisseurs managés ADO.NET et centre de développement DataSet](https://go.microsoft.com/fwlink/?LinkId=217917)
