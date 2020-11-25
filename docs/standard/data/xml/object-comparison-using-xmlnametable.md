---
title: Comparaison d'objets à l'aide de XmlNameTable
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8d94e041-d340-4ddf-9a2c-d7319e3f4f86
ms.openlocfilehash: 5e0f5de6fd956bcaaf30b592e04c432a5f824c52
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734099"
---
# <a name="object-comparison-using-xmlnametable"></a>Comparaison d'objets à l'aide de XmlNameTable

Durant la création d'un objet **XmlDocument**, une table de noms est spécialement créée à l'intention de ce document. Quand les données XML sont chargées dans le document ou que de nouveaux éléments ou attributs sont créés, les noms d'attributs et d'éléments sont placés dans **XmlNameTable**. Vous pouvez également créer un **XmlDocument** en utilisant un **NameTable** existant issu d'un autre document. Quand des **XmlDocument** sont créés avec le constructeur qui prend un paramètre **XmlNameTable**, le document a accès aux préfixes, aux espaces de noms et aux noms de nœud déjà stockés dans **XmlNameTable**. Quelle que soit la manière dont les noms sont chargés dans la table de noms, une fois les noms stockés dans la table, ils peuvent être comparés rapidement par la comparaison d'objets et non au moyen de la comparaison de chaînes. Des chaînes peuvent également être ajoutées à la table de noms à l'aide de la <xref:System.Xml.NameTable.Add%2A>. L'exemple de code suivant illustre la création d'une table de noms et l'ajout de la chaîne **MyString** à cette table. Un **XmlDocument** est ensuite créé au moyen de cette table, et les noms d'éléments et d'attributs de **Myfile.xml** sont ajoutés à la table de noms existante.  
  
```vb  
Dim nt As New NameTable()  
nt.Add("MyString")  
Dim doc As New XmlDocument(nt)  
doc.Load("Myfile.xml")  
```  
  
```csharp  
NameTable nt = new NameTable();  
nt.Add("MyString");  
XmlDocument doc = new XmlDocument(nt);  
doc.Load("Myfile.xml");  
```  
  
 L'exemple de code suivant illustre la création d'un document, l'ajout de deux nouveaux éléments au document, qui les ajoute par ailleurs à sa table de noms, et l'exécution d'une comparaison d'objets sur les noms.  
  
```vb  
Dim doc1 As XmlDocument = imp.CreateDocument()  
Dim node1 As XmlElement = doc.CreateElement("node1")  
Dim doc2 As XmlDocument = imp.CreateDocument()  
Dim node2 As XmlElement = doc.CreateElement("node2")  
if (CType(node1.Name, object) = CType(node2.Name, object))  
```  
  
```csharp  
XmlDocument doc1 = imp.CreateDocument();  
node1 = doc1.CreateElement ("node1");  
XmlDocument doc2 = imp.CreateDocument();  
node2 = doc2.CreateElement ("node1");  
if (((object)node1.Name) == ((object)node2.Name))  
{ ...  
```  
  
 Le scénario ci-avant, qui montre une table de noms passée entre deux documents, est courant lorsque le même type de document est traité de façon répétée (tel que des documents de commande sur un site de commerce électronique), ces documents étant conformes à un schéma en langage XSD (XML Schema Definition) ou une définition de type de document (DTD) et contenant une répétition des mêmes chaînes. L'utilisation de la même table de noms permet d'améliorer les performances puisque le même nom d'élément se retrouve dans plusieurs documents.  
  
## <a name="see-also"></a>Voir aussi

- [DOM (Document Object Model) XML](xml-document-object-model-dom.md)
