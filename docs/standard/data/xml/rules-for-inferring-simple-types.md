---
title: Règles relatives à l'inférence de types simples
ms.date: 03/30/2017
ms.assetid: 394624d6-4da0-430a-8a88-46efe40f14de
ms.openlocfilehash: 817a35c607f810da0a3e2dc681d27ea997c5fcc7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823548"
---
# <a name="rules-for-inferring-simple-types"></a>Règles relatives à l'inférence de types simples
Décrit comment la classe <xref:System.Xml.Schema.XmlSchemaInference> déduit le type de données pour les attributs et les éléments.  
  
 La classe <xref:System.Xml.Schema.XmlSchemaInference> déduit les types de données pour les attributs et les éléments comme types simples. Cette section décrit les types déduits possibles, la manière dont plusieurs valeurs différentes sont rapprochées en un type simple et la manière dont les attributs de définition de schéma `xsi` sont gérés.  
  
## <a name="inferred-types"></a>Types déduits  
 La classe <xref:System.Xml.Schema.XmlSchemaInference> déduit des valeurs d'éléments et d'attributs comme des types simples et inclut un type d'attribut dans le schéma qui en résulte. Tous les types déduits sont des types simples. Aucun type de base ni aucune facette n'est inclus dans le schéma résultant.  
  
 Les valeurs sont examinées individuellement, au fur et à mesure qu'elles sont rencontrées dans le document XML. Le type est déduit pour une valeur au moment de son examen. Si un type a été déduit pour un attribut ou un élément et si une valeur pour l'attribut ou l'élément est rencontrée, qui ne correspond pas au type actuellement déduit, la classe <xref:System.Xml.Schema.XmlSchemaInference> promeut le type pour chaque ensemble de règles. Ces règles sont présentées dans la section Promotion de type, plus loin dans cette rubrique.  
  
 Le tableau suivant répertorie les types déduits possibles pour le schéma résultant.  
  
|Type simple|Description|  
|-----------------|-----------------|  
|boolean|True, false, 0, 1.|  
|byte|Nombres entiers dans la plage comprise entre -128 et 127.|  
|unsignedByte|Nombres entiers dans la plage comprise entre 0 et 255.|  
|short|Nombres entiers dans la plage comprise entre -32768 et 32767.|  
|unsignedShort|Nombres entiers dans la plage comprise entre 0 et 65535.|  
|int|Nombres entiers dans la plage comprise entre -2147483648 et 2147483647.|  
|unsignedInt|Nombres entiers dans la plage comprise entre 0 et 4294967295.|  
|long|Nombres entiers dans la plage comprise entre -9223372036854775808 et 9223372036854775807.|  
|unsignedLong|Nombres entiers dans la plage comprise entre 0 et 18446744073709551615.|  
|entier|Nombre de chiffres fini éventuellement précédé du préfixe « - ».|  
|Décimal|Valeurs numériques avec une précision de 0 à 28 chiffres.|  
|float|Décimales éventuellement suivies de « E » ou « e » et d'une valeur entière représentant l'exposant. Les valeurs décimales peuvent s'inscrire dans la plage comprise entre -16777216 et 16777216. Les valeurs d'exposant peuvent s'inscrire dans la plage comprise entre –149 et 104.<br /><br /> Float permet d'utiliser des valeurs spéciales pour représenter des valeurs d'infinité et non numériques. Les valeurs spéciales pour float sont : 0, -0, INF, -INF, NaN.|  
|double|Comme pour float, sinon que les valeurs décimales peuvent s'inscrire dans la plage comprise entre -9007199254740992 et 9007199254740992. Les valeurs d'exposant peuvent s'inscrire dans la plage comprise entre –1075 et 970.<br /><br /> Double permet d'utiliser des valeurs spéciales pour représenter des valeurs d'infinité et non numériques. Les valeurs spéciales pour float sont : 0, -0, INF, -INF, NaN.|  
|duration|Format de durée de W3C.|  
|dateTime|Le format de date et d'heure de W3C.|  
|time|Le format d'heure de W3C.|  
|Date|Les valeurs d'année doivent être comprises entre 0001 et 9999.|  
|gYearMonth|Format d'année et de mois du calendrier grégorien de W3C.|  
|string|Un ou plusieurs caractères Unicode.|  
  
## <a name="type-promotion"></a>Promotion de type  
 La classe <xref:System.Xml.Schema.XmlSchemaInference> examine les valeurs d'attributs et d'éléments l'une après l'autre. Au fur et à mesure que des valeurs sont rencontrées, le type non signé le plus restrictif est déduit. Si un type a été déduit pour un attribut ou un élément et si une nouvelle valeur est rencontrée, qui ne correspond pas au type actuellement déduit, le type déduit est promu au rang de nouveau type qui s'applique au type actuellement déduit et à la nouvelle valeur. La classe <xref:System.Xml.Schema.XmlSchemaInference> ne considère pas les valeurs précédentes lors de la promotion du type déduit.  
  
 Examinons, par exemple, les fragments XML suivants de deux documents XML :  
  
 `<MyElement1 attr1="12" />`  
  
 `<MyElement1 attr1="52344" />`  
  
 Lorsque la première valeur `attr1` est rencontrée, le type de `attr1` est déduit comme `unsignedByte` sur la base de la valeur `12`. Lorsque la seconde valeur `attr1` est rencontrée, le type est promu au rang de `unsignedShort` sur la base du type actuellement déduit de `unsignedByte` et de la valeur actuelle `52344`.  
  
 Examinons, à présent, le code XML suivant de deux documents XML :  
  
 `<MyElement2 attr2="0" />`  
  
 `<MyElement2 attr2="true" />`  
  
 Lorsque la première valeur `attr2` est rencontrée, le type de `attr2` est déduit comme `unsignedByte` sur la base de la valeur `0`. Lorsque la seconde valeur `attr2` est rencontrée, le type est promu au rang de `string` sur la base du type actuellement déduit de `unsignedByte` et de la valeur actuelle `true` parce que la classe <xref:System.Xml.Schema.XmlSchemaInference> prend en considération les valeurs précédents lors de la promotion du type déduit. Toutefois, si les deux instances de `attr2` avaient été rencontrées dans le même document XML et pas dans deux documents XML différents, comme illustré ci-avant, `attr2` aurait été déduit comme `boolean`.  
  
### <a name="ignored-attributes-from-the-httpswwww3org2001xmlschema-instance-namespace"></a>Attributs ignorés dans l’espace de noms <https://www.w3.org/2001/XMLSchema-instance>

Vous trouverez ci-après les attributs de définition du schéma qui sont ignorés durant l'inférence de schéma.  
  
|Attribut|Description|  
|---------------|-----------------|  
|`xsi:type`|Si un élément est rencontré avec un `xsi:type` spécifié, le `xsi:type` est ignoré.|  
|`xsi:nil`|Si un élément avec un attribut `xsi:nil` est rencontré, sa déclaration d'élément dans le schéma déduit a la valeur `nillable="true"`. Un élément dont un attribut `xsi:nil` a la valeur `true` ne peut pas avoir d'éléments enfants.|  
|`xsi:schemaLocation`|Si `xsi:schemaLocation` est rencontré, il est ignoré.|  
|`xsi:noNamespaceSchemaLocation`|Si `xsi:noNamespaceSchemaLocation` est rencontré, il est ignoré.|  
  
## <a name="see-also"></a>Voir aussi

- [Modèle Objet du schéma (SOM) XML](xml-schema-object-model-som.md)
- [Inférence de schémas à partir de documents XML](inferring-schemas-from-xml-documents.md)
- [Règles pour l'inférence de types et de structure de nœud de schéma](rules-for-inferring-schema-node-types-and-structure.md)
