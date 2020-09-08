---
title: Sérialisation avec une déclaration XML-LINQ to XML
description: Vous pouvez contrôler si une déclaration XML est générée quand vous sérialisez du code XML en C# ou Visual Basic.
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: c237fa4a-a042-40fd-886f-17b54c66bb75
ms.openlocfilehash: 8d25d199b149ac6aeb2aa37dc248523e79847220
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552409"
---
# <a name="serialize-with-an-xml-declaration-linq-to-xml"></a>Sérialiser avec une déclaration XML (LINQ to XML)

Cet article explique comment contrôler si une déclaration XML est générée lors de la sérialisation de XML en C# ou Visual Basic.

La sérialisation vers un objet <xref:System.IO.File> ou <xref:System.IO.TextWriter> à l'aide de la méthode <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType> ou <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>génère une déclaration XML. Lorsque vous sérialisez vers un <xref:System.Xml.XmlWriter> , les paramètres du writer (spécifiés dans un <xref:System.Xml.XmlWriterSettings> objet) déterminent si une déclaration XML est générée.

Si vous sérialisez vers une chaîne à l’aide de la `ToString` méthode, le code XML résultant n’inclura pas de déclaration XML.

## <a name="example-serialize-with-an-xml-declaration"></a>Exemple : Serialize avec une déclaration XML

L'exemple suivant crée un objet <xref:System.Xml.Linq.XElement>, enregistre le document dans un fichier, puis imprime le fichier sur la console :

```csharp
XElement root = new XElement("Root",
    new XElement("Child", "child content")
);
root.Save("Root.xml");
string str = File.ReadAllText("Root.xml");
Console.WriteLine(str);
```

```vb
Dim root As XElement = <Root>
                           <Child>child content</Child>
                       </Root>
root.Save("Root.xml")
Dim str As String = File.ReadAllText("Root.xml")
Console.WriteLine(str)
```

Cet exemple produit la sortie suivante :

```xml
<?xml version="1.0" encoding="utf-8"?>
<Root>
  <Child>child content</Child>
</Root>
```

## <a name="example-serialize-without-an-xml-declaration"></a>Exemple : sérialisation sans déclaration XML

L'exemple suivant montre comment enregistrer un objet <xref:System.Xml.Linq.XElement> dans un objet <xref:System.Xml.XmlWriter>.

```csharp
StringBuilder sb = new StringBuilder();
XmlWriterSettings xws = new XmlWriterSettings();
xws.OmitXmlDeclaration = true;

using (XmlWriter xw = XmlWriter.Create(sb, xws)) {
    XElement root = new XElement("Root",
        new XElement("Child", "child content")
    );
    root.Save(xw);
}
Console.WriteLine(sb.ToString());
```

```vb
Dim sb As StringBuilder = New StringBuilder()
Dim xws As XmlWriterSettings = New XmlWriterSettings()
xws.OmitXmlDeclaration = True

Using xw As XmlWriter = XmlWriter.Create(sb, xws)
    Dim root = <Root>
                   <Child>child content</Child>
               </Root>
    root.Save(xw)
End Using
Console.WriteLine(sb.ToString())
```

Cet exemple produit la sortie suivante :

```xml
<Root><Child>child content</Child></Root>
```
