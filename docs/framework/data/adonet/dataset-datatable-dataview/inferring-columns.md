---
title: Déduction des colonnes
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 45d27b78b5d83d333c16192e172e7b7e3dd88c10
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164699"
---
# <a name="inferring-columns"></a>Déduction des colonnes

Après avoir déterminé les éléments à déduire en tant que tables pour un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET déduit les colonnes pour ces tables. ADO.NET 2,0 a introduit un nouveau moteur d’inférence de schéma qui déduit un type de données fortement typé pour chaque élément **simpleType** . Dans les versions précédentes, le type de données d’un élément **simpleType** inféré était toujours **xsd : String**.  
  
## <a name="migration-and-backward-compatibility"></a>Migration et compatibilité ascendante  

 La méthode **ReadXml** accepte un argument de type **InferSchema**. Cet argument vous permet de spécifier un comportement d’inférence compatible avec les versions précédentes. Les valeurs disponibles pour l’énumération **InferSchema** sont indiquées dans le tableau suivant.  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 Assure la compatibilité ascendante en déduisant toujours un type simple comme l'objet <xref:System.String>.  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 Déduit un type de données fortement typées. Lève une exception s'il est utilisé avec un objet <xref:System.Data.DataTable>.  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 Ignore tout schéma inline et lit les données dans le schéma <xref:System.Data.DataSet> existant.  
  
## <a name="attributes"></a>Attributs  

 Comme défini dans l' [inférence des tables](inferring-tables.md), un élément avec des attributs est déduit en tant que table. Les attributs de cet élément seront ensuite déduits en tant que colonnes de cette table. La propriété **ColumnMapping** des colonnes aura pour valeur **MappingType. Attribute**afin de s’assurer que les noms de colonne seront écrits comme des attributs si le schéma est réécrit en XML. Les valeurs des attributs sont stockées dans une ligne de la table. Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Le processus d’inférence produira une table nommée **element1** avec deux colonnes, **attr1** et **attr2**. La propriété **ColumnMapping** des deux colonnes aura pour valeur **MappingType. Attribute**.  
  
 **Jeu de données :** DocumentElement  
  
 **Table :** Élément1  
  
|attr1|attr2|  
|-----------|-----------|  
|valeur1|valeur2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>Éléments dépourvus d'attributs ou d'éléments enfants  

 Si un élément ne comporte ni éléments enfants, ni attributs, il sera déduit en tant que colonne. La propriété **ColumnMapping** de la colonne sera définie sur **MappingType. Element**. Le texte des éléments enfants est stocké dans une ligne de la table. Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 Le processus d’inférence produira une table nommée **element1** avec deux colonnes **ChildElement1** et **ChildElement2**. La propriété **ColumnMapping** des deux colonnes aura pour valeur **MappingType. Element**.  
  
 **Jeu de données :** DocumentElement  
  
 **Table :** Élément1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>Voir aussi

- [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement d'un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
