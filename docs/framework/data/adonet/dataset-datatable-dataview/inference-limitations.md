---
title: Limitations des inférences
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 9d8191be137661200e1a6b84d68328c1202880ca
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172773"
---
# <a name="inference-limitations"></a>Limitations des inférences

Le processus d'inférence d'un schéma de l'objet <xref:System.Data.DataSet> à partir de XML peut aboutir à des schémas différents en fonction des éléments XML figurant dans chaque document. Examinons, par exemple, les documents XML suivants.  
  
 Document1 :  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2 :  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 Pour « Document1 », le processus d’inférence produit un **DataSet** nommé « DocumentElement » et une table nommée « Element1 », car « Element1 » est un élément répétitif.  
  
 **Jeu de données :** DocumentElement  
  
 **Table :** Élément1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 Toutefois, pour « document2 », le processus d’inférence produit un **jeu de données** nommé « NewDataSet » et une table nommée « documentElement ». « Element1 » est déduit en tant que colonne car il n'a ni attribut, ni élément enfant.  
  
 **Jeu de données :** NewDataSet  
  
 **Table :** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 Ces deux documents XML peuvent avoir été conçus de manière à produire le même schéma, mais le processus d'inférence donne des résultats très différents en fonction des éléments contenus dans chaque document.  
  
 Pour éviter les incohérences qui peuvent se produire lors de la génération d’un schéma à partir d’un document XML, nous vous recommandons de spécifier explicitement un schéma à l’aide du langage XSD (XML Schema Definition) ou XDR (XML-Data Reduced) lors du chargement d’un **DataSet** à partir de XML. Pour plus d’informations sur la spécification explicite d’un schéma de **DataSet** à l’aide d’un schéma XML, consultez [dérivation de la structure relationnelle d’un DataSet à partir d’un schéma XML (XSD)](deriving-dataset-relational-structure-from-xml-schema-xsd.md).  
  
## <a name="see-also"></a>Voir aussi

- [Déduction de la structure relationnelle des DataSet à partir de XML](inferring-dataset-relational-structure-from-xml.md)
- [Chargement d'un DataSet à partir de XML](loading-a-dataset-from-xml.md)
- [Chargement des informations de schéma de DataSet à partir de XML](loading-dataset-schema-information-from-xml.md)
- [Utilisation de XML dans un DataSet](using-xml-in-a-dataset.md)
- [DataSets, DataTables et DataViews](index.md)
- [Vue d'ensemble d’ADO.NET](../ado-net-overview.md)
