---
title: Modification des propriétés de préfixe d'espace de noms
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
ms.openlocfilehash: b1df520d00d3a98b2e518092d4eff51b5d0b7741
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78158023"
---
# <a name="changing-namespace-prefix-properties"></a>Modification des propriétés de préfixe d'espace de noms
La classe **XmlNode** vous permet de modifier le préfixe d'espace de noms associé à un nœud précis. Par exemple, le code suivant montre la modification du préfixe d'un élément.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Sortie**  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 La modification du préfixe d'un nœud n'entraîne pas la modification de son espace de noms. Ce dernier peut être défini uniquement au moment de la création du nœud. Lorsque vous rendez persistante l’arborescence, de nouveaux attributs d’espace de noms peuvent ne plus être persistants pour satisfaire le préfixe défini. Si le nouvel espace de noms ne peut pas être créé, le préfixe est modifié de telle sorte que le nœud préserve son nom local et son espace de noms. L'exemple suivant illustre l'ajout d'un attribut d'espace de noms.  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 **Sortie**  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 Quand l’arborescence a été rendue persistante sous la forme d’une chaîne à la suite de l’appel à **doc.InnerXml**, l’attribut `xmlns:a='123'` a été ajouté pour préserver l’espace de noms de l’élément `test`. Sa valeur était `'123'` et est restée `'123'`.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
