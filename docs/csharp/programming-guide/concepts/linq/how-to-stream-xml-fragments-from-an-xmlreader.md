---
title: Comment diffuser des fragments de XML à partir d’un XmlReader (C)
ms.date: 07/20/2015
ms.assetid: 4a8f0e45-768a-42e2-bc5f-68bdf0e0a726
ms.openlocfilehash: f7914d33622518f983a685dd2e844a25fd3ca15f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714655"
---
# <a name="how-to-stream-xml-fragments-from-an-xmlreader-c"></a>Comment diffuser des fragments de XML à partir d’un XmlReader (C)

Lorsque vous devez traiter de grands fichiers XML, il peut être impossible de charger l’intégralité de l’arborescence XML en mémoire. Cette rubrique montre comment diffuser des fragments en continu à l'aide d'un objet <xref:System.Xml.XmlReader>.  
  
 L'une des manières les plus efficaces d'utiliser un objet <xref:System.Xml.XmlReader> pour lire des objets <xref:System.Xml.Linq.XElement> consiste à écrire votre propre méthode d'axe personnalisée. Une méthode d'axe retourne généralement une collection telle que <xref:System.Collections.Generic.IEnumerable%601> de <xref:System.Xml.Linq.XElement>, comme illustré dans l'exemple de cette rubrique. Dans la méthode d'axe personnalisée, après avoir créé le fragment XML en appelant la méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A>, retournez la collection à l'aide de `yield return`. Cela fournit une sémantique d'exécution différée à votre méthode d'axe personnalisée.  
  
 Lorsque vous créez une arborescence XML à partir d'un objet <xref:System.Xml.XmlReader>, l'objet <xref:System.Xml.XmlReader> doit être positionné sur un élément. La méthode <xref:System.Xml.Linq.XNode.ReadFrom%2A> ne retourne que lorsqu'elle a lu la balise de fermeture de l'élément.  
  
 Si vous souhaitez créer une arborescence partielle, vous pouvez instancier un objet <xref:System.Xml.XmlReader>, positionner le lecteur sur le nœud que vous souhaitez convertir en une arborescence <xref:System.Xml.Linq.XElement>, puis créer l'objet <xref:System.Xml.Linq.XElement>.  
  
Le sujet [Comment diffuser des fragments de XML avec accès à des informations d’en-tête (C)](./how-to-stream-xml-fragments-with-access-to-header-information.md) contient des informations et un exemple sur la façon de diffuser un document plus complexe.
  
 Le sujet [Comment effectuer la transformation en continu de grands documents XML (C)](./how-to-perform-streaming-transform-of-large-xml-documents.md) contient un exemple d’utilisation de LINQ à XML pour transformer des documents XML extrêmement grands tout en maintenant une petite empreinte mémoire.  
  
## <a name="example"></a> Exemple  
 Cet exemple crée une méthode d'axe personnalisée. Vous pouvez l’interroger en utilisant une requête LINQ. La méthode d'axe personnalisée, `StreamRootChildDoc`, est une méthode conçue spécifiquement pour lire un document qui possède un élément `Child` à répétition.  
  
```csharp  
static IEnumerable<XElement> StreamRootChildDoc(StringReader stringReader)  
{  
    using (XmlReader reader = XmlReader.Create(stringReader))  
    {  
        reader.MoveToContent();  
        // Parse the file and display each of the nodes.  
        while (reader.Read())  
        {  
            switch (reader.NodeType)  
            {  
                case XmlNodeType.Element:  
                    if (reader.Name == "Child") {  
                        XElement el = XElement.ReadFrom(reader) as XElement;  
                        if (el != null)  
                            yield return el;  
                    }  
                    break;  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    string markup = @"<Root>  
      <Child Key=""01"">  
        <GrandChild>aaa</GrandChild>  
      </Child>  
      <Child Key=""02"">  
        <GrandChild>bbb</GrandChild>  
      </Child>  
      <Child Key=""03"">  
        <GrandChild>ccc</GrandChild>  
      </Child>  
    </Root>";  
  
    IEnumerable<string> grandChildData =  
        from el in StreamRootChildDoc(new StringReader(markup))  
        where (int)el.Attribute("Key") > 1  
        select (string)el.Element("GrandChild");  
  
    foreach (string str in grandChildData) {  
        Console.WriteLine(str);  
    }  
}  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
bbb  
ccc  
```  
  
 Dans cet exemple, le document source est très petit. Toutefois, cet exemple aurait un faible encombrement mémoire même s'il y avait des millions d'éléments `Child`.  
