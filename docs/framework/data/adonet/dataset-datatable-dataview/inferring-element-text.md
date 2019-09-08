---
title: Déduction du texte d'un élément
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 3fdd110a14ddfd6065ed552171a8d76ef64e2fb5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784540"
---
# <a name="inferring-element-text"></a>Déduction du texte d'un élément
Si un élément contient du texte et qu’il n’a aucun élément enfant à déduire en tant que tables (comme des éléments avec des attributs ou des éléments répétés), une nouvelle colonne portant le nom **TableName_Text** sera ajoutée à la table déduite pour l’élément. Le texte contenu dans l'élément sera ajouté à une ligne de la table et stocké dans la nouvelle colonne. La propriété **ColumnMapping** de la nouvelle colonne sera définie sur **MappingType. SimpleContent**.  
  
 Examinons, par exemple, le code XML suivant.  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 Le processus d’inférence produira une table nommée **element1** avec deux colonnes : **attr1** et **Element1_Text**. La propriété **ColumnMapping** de la colonne **attr1** aura pour valeur **MappingType. Attribute**. La propriété **ColumnMapping** de la colonne **Element1_Text** aura pour valeur **MappingType. SimpleContent**.  
  
 **Ensemble** DocumentElement  
  
 **Table :** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|valeur1|Text1|  
  
 Si un élément contient du texte, mais possède également des éléments enfants contenant du texte, une colonne ne sera pas ajoutée à la table pour stocker le texte contenu dans l'élément. Ce texte sera ignoré, alors que le texte des éléments enfants sera inclus dans une ligne de la table. Examinons, par exemple, le code XML suivant.  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 Le processus d’inférence produira une table nommée **element1** avec une colonne nommée **ChildElement1**. Le texte de l’élément **ChildElement1** sera inclus dans une ligne de la table. L'autre texte sera ignoré. La propriété **ColumnMapping** de la colonne **ChildElement1** sera définie sur **MappingType. Element**.  
  
 **Ensemble** DocumentElement  
  
 **Table :** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>Voir aussi

- [Inférence de la structure relationnelle d’un DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement d’un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d’ensemble d’ADO.NET](../ado-net-overview.md)
