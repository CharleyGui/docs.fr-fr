---
title: Comment diffuser en continu des fragments XML avec accès aux informations d’en-tête (C#)
description: Découvrez comment diffuser en continu des fragments XML avec accès aux informations d’en-tête. Les techniques de streaming permettent d’éviter une utilisation excessive de la mémoire.
ms.date: 07/20/2015
ms.assetid: 7f242770-b0c7-418d-894b-643215e1f8aa
ms.openlocfilehash: 8bfded96ea1fa6b096d56ae0736002b9062d58b6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303216"
---
# <a name="how-to-stream-xml-fragments-with-access-to-header-information-c"></a>Comment diffuser en continu des fragments XML avec accès aux informations d’en-tête (C#)
Vous devez parfois lire des fichiers XML arbitrairement volumineux et écrire votre application de sorte que son encombrement mémoire soit prévisible. Si vous tentez de remplir une arborescence XML avec un grand fichier XML, l'utilisation de la mémoire sera proportionnelle à la taille du fichier (c'est-à-dire excessive). Par conséquent, vous devez utiliser une technique de diffusion en continu à la place.  
  
L'une des options consiste à écrire votre application à l'aide de <xref:System.Xml.XmlReader>. Toutefois, vous souhaiterez peut-être utiliser LINQ pour interroger l’arborescence XML. Si tel est le cas, vous pouvez écrire votre propre méthode d'axe personnalisée. Pour plus d’informations, consultez [Comment écrire une méthode d’axe LINQ to XML (C#)](./how-to-write-a-linq-to-xml-axis-method.md).
  
 Pour écrire votre propre méthode d'axe personnalisée, vous écrivez une petite méthode qui utilise l'objet <xref:System.Xml.XmlReader> pour lire les nœuds jusqu'à atteindre l'un des nœuds qui vous intéressent. La méthode appelle ensuite <xref:System.Xml.Linq.XNode.ReadFrom%2A>, qui lit à partir de l'objet <xref:System.Xml.XmlReader> et instancie un fragment XML. Elle produit ensuite chaque fragment via `yield return` à la méthode qui énumère votre méthode d'axe personnalisée. Vous pouvez ensuite écrire des requêtes LINQ sur votre méthode d'axe personnalisée.  
  
 Il est préférable d'appliquer des techniques de diffusion en continu dans les situations où vous devez traiter le document source une seule fois et où vous pouvez traiter les éléments dans l'ordre du document. Certains opérateurs de requête standard, tels que <xref:System.Linq.Enumerable.OrderBy%2A>, itèrent au sein de leur source, recueillent toutes les données, les trient, puis produisent le premier élément de la séquence. Si vous utilisez un opérateur de requête qui matérialise sa source avant de produire le premier élément, vous ne conserverez pas un faible encombrement mémoire.  
  
## <a name="example"></a>Exemple  

Le problème peut parfois être un peu plus épineux. Dans le document XML suivant, le consommateur de votre méthode d'axe personnalisée doit également connaître le nom du client auquel appartient chaque élément.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root>  
  <Customer>  
    <Name>A. Datum Corporation</Name>  
    <Item>  
      <Key>0001</Key>  
    </Item>  
    <Item>  
      <Key>0002</Key>  
    </Item>  
    <Item>  
      <Key>0003</Key>  
    </Item>  
    <Item>  
      <Key>0004</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Fabrikam, Inc.</Name>  
    <Item>  
      <Key>0005</Key>  
    </Item>  
    <Item>  
      <Key>0006</Key>  
    </Item>  
    <Item>  
      <Key>0007</Key>  
    </Item>  
    <Item>  
      <Key>0008</Key>  
    </Item>  
  </Customer>  
  <Customer>  
    <Name>Southridge Video</Name>  
    <Item>  
      <Key>0009</Key>  
    </Item>  
    <Item>  
      <Key>0010</Key>  
    </Item>  
  </Customer>  
</Root>  
```  
  
 L'approche utilisée dans cet exemple consiste à rechercher ces informations d'en-tête, à les enregistrer, puis à générer une petite arborescence XML qui contient à la fois les informations d'en-tête et le détail que vous énumérez. La méthode d'axe produit ensuite cette nouvelle petite arborescence XML. La requête a alors accès aux informations d'en-tête et aux informations de détail.  
  
 Cette approche présente un faible encombrement mémoire. À mesure que chaque fragment XML de détail est produit, aucune référence au fragment précédent n'est conservée et il est disponible pour le garbage collection. Cette technique crée de nombreux objets éphémères sur le tas.  
  
 L'exemple suivant montre comment implémenter et utiliser une méthode d'axe personnalisée qui diffuse en continu des fragments XML à partir du fichier spécifié par l'URI. Cet axe personnalisé est écrit de façon à ce qu’il attende un document contenant des `Customer` éléments, et `Name` `Item` , et que ces éléments soient disposés comme dans le document ci-dessus `Source.xml` . Il s'agit d'une implémentation simpliste. Une implémentation plus robuste serait préparée à analyser un document non valide.  
  
```csharp  
static IEnumerable<XElement> StreamCustomerItem(string uri)  
{  
    using (XmlReader reader = XmlReader.Create(uri))  
    {  
        XElement name = null;  
        XElement item = null;  
  
        reader.MoveToContent();  
  
        // Parse the file, save header information when encountered, and yield the  
        // Item XElement objects as they are created.  
  
        // loop through Customer elements  
        while (reader.Read())  
        {  
            if (reader.NodeType == XmlNodeType.Element  
                && reader.Name == "Customer")  
            {  
                // move to Name element  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.Element &&  
                        reader.Name == "Name")  
                    {  
                        name = XElement.ReadFrom(reader) as XElement;  
                        break;  
                    }  
                }  
  
                // loop through Item elements  
                while (reader.Read())  
                {  
                    if (reader.NodeType == XmlNodeType.EndElement)  
                        break;  
                    if (reader.NodeType == XmlNodeType.Element  
                        && reader.Name == "Item")  
                    {  
                        item = XElement.ReadFrom(reader) as XElement;  
                        if (item != null) {  
                            XElement tempRoot = new XElement("Root",  
                                new XElement(name)  
                            );  
                            tempRoot.Add(item);  
                            yield return item;  
                        }  
                    }  
                }  
            }  
        }  
    }  
}  
  
static void Main(string[] args)  
{  
    XElement xmlTree = new XElement("Root",  
        from el in StreamCustomerItem("Source.xml")  
        where (int)el.Element("Key") >= 3 && (int)el.Element("Key") <= 7  
        select new XElement("Item",  
            new XElement("Customer", (string)el.Parent.Element("Name")),  
            new XElement(el.Element("Key"))  
        )  
    );  
    Console.WriteLine(xmlTree);  
}  
```  
  
 Ce code génère la sortie suivante :  
  
```xml  
<Root>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0003</Key>  
  </Item>  
  <Item>  
    <Customer>A. Datum Corporation</Customer>  
    <Key>0004</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0005</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0006</Key>  
  </Item>  
  <Item>  
    <Customer>Fabrikam, Inc.</Customer>  
    <Key>0007</Key>  
  </Item>  
</Root>  
```  
