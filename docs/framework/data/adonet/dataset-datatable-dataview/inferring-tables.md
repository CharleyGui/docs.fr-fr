---
title: Déduction de tables
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 4a3d7b239dbc405cf2acae967b5be401dc772e38
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177551"
---
# <a name="inferring-tables"></a>Déduction de tables

Lors de l'inférence du schéma d'un objet <xref:System.Data.DataSet> à partir d'un document XML, ADO.NET identifie d'abord les éléments XML qui représentent des tables. Les structures XML suivantes aboutissent à une table pour le schéma du **DataSet** :  
  
- éléments avec attributs ;  
  
- éléments avec éléments enfants ;  
  
- éléments qui se répètent.  
  
## <a name="elements-with-attributes"></a>Éléments avec attributs  

 Les éléments contenant des attributs spécifiés donnent des tables déduites. Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit une table nommée « Element1 ».  
  
 **Jeu de données :** DocumentElement  
  
 **Table :** Élément1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|valeur1||  
|valeur2|Text1|  
  
## <a name="elements-with-child-elements"></a>Éléments avec éléments enfants  

 Les éléments possédant des éléments enfants donnent des tables déduites. Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit une table nommée « Element1 ».  
  
 **Jeu de données :** DocumentElement  
  
 **Table :** Élément1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 L'élément document, ou racine, donne une table déduite s'il comporte des attributs ou des éléments enfants qui sont inférés en tant que colonnes. Si l’élément de document n’a pas d’attributs ni d’éléments enfants qui seraient déduits en tant que colonnes, l’élément est déduit en tant que **DataSet**. Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit une table nommée « DocumentElement ».  
  
 **Jeu de données :** NewDataSet  
  
 **Table :** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 Examinons également le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 Le processus d’inférence produit un **DataSet** nommé « DocumentElement » qui contient une table nommée « Element1 ».  
  
 **Jeu de données :** DocumentElement  
  
 **Table :** Élément1  
  
|attr1|attr2|  
|-----------|-----------|  
|valeur1|valeur2|  
  
## <a name="repeating-elements"></a>Éléments qui se répètent  

 Les éléments qui se répètent donnent une seule table déduite. Examinons, par exemple, le code XML suivant :  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Le processus d'inférence produit une table nommée « Element1 ».  
  
 **Jeu de données :** DocumentElement  
  
 **Table :** Élément1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## <a name="see-also"></a>Voir aussi

- [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement d'un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
