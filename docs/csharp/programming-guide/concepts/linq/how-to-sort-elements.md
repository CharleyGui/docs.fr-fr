---
title: Comment trier des éléments (C#)
description: Découvrez comment trier les éléments. Consultez des exemples d’écriture d’une requête qui trie ses résultats dans un document XML.
ms.date: 07/20/2015
ms.assetid: aee6fbbc-81fd-4b3e-b40f-6ed7b3bd3fee
ms.openlocfilehash: 669d9cf583e6ab70c93be39ad271eaf104f88718
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301435"
---
# <a name="how-to-sort-elements-c"></a>Comment trier des éléments (C#)
Cet exemple montre comment écrire une requête qui trie ses résultats.  
  
## <a name="example"></a>Exemple  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques (LINQ to XML)](./sample-xml-file-numerical-data-linq-to-xml.md).  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
IEnumerable<decimal> prices =  
    from el in root.Elements("Data")  
    let price = (decimal)el.Element("Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 Ce code génère la sortie suivante :  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="example"></a>Exemple  
 L'exemple suivant illustre la même requête pour du code XML qui est dans un espace de noms. Pour plus d’informations, consultez [Vue d’ensemble des espaces de noms (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Cet exemple utilise le document XML suivant : [Exemple de fichier XML : Données numériques dans un espace de noms](./sample-xml-file-numerical-data-in-a-namespace.md).  
  
```csharp  
XElement root = XElement.Load("DataInNamespace.xml");  
XNamespace aw = "http://www.adatum.com";  
IEnumerable<decimal> prices =  
    from el in root.Elements(aw + "Data")  
    let price = (decimal)el.Element(aw + "Price")  
    orderby price  
    select price;  
foreach (decimal el in prices)  
    Console.WriteLine(el);  
```  
  
 Ce code génère la sortie suivante :  
  
```output  
0.99  
4.95  
6.99  
24.50  
29.00  
66.00  
89.99  
```  
  
## <a name="see-also"></a>Voir aussi

- [Tri des données (C#)](./sorting-data.md)
