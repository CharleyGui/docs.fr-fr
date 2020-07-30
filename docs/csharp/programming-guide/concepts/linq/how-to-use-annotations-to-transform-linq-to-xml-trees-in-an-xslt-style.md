---
title: Comment utiliser des annotations pour transformer des arborescences de LINQ to XML dans un style XSLT (C#)
description: Découvrez comment utiliser des annotations pour transformer des arbres LINQ to XML dans un style XSLT. Consultez un exemple de transformation d’une arborescence à l’aide de la fonction XForm.
ms.date: 07/20/2015
ms.assetid: 12a95902-a6b7-4a1e-ad52-04a518db226f
ms.openlocfilehash: 844ca08cb2c6b47f7803d388663daeacb65bdb68
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302878"
---
# <a name="how-to-use-annotations-to-transform-linq-to-xml-trees-in-an-xslt-style-c"></a>Comment utiliser des annotations pour transformer des arborescences de LINQ to XML dans un style XSLT (C#)
Les annotations peuvent servir à faciliter les transformations d’une arborescence XML.  
  
 Certains documents XML sont « centrés sur les documents avec du contenu mixte ». Avec ces documents, vous ne connaissez pas nécessairement la forme des enfants nœuds d'un élément. Par exemple, un nœud qui contient du texte peut se présenter comme suit :  
  
```xml  
<text>A phrase with <b>bold</b> and <i>italic</i> text.</text>  
```  
  
 Pour tout nœud de texte donné, il peut exister une quantité quelconque d'éléments enfants `<b>` et `<i>`. Cette approche s’étend à plusieurs autres situations, par exemple à des pages qui contiennent une variété d’éléments enfants, tels que des paragraphes normaux, des paragraphes à puces et des bitmaps. Les cellules d’un tableau peuvent contenir du texte, des listes déroulantes ou des bitmaps. L'une des principales caractéristiques du code XML centré sur les documents est que vous ne savez pas quel élément enfant un élément particulier aura.  
  
 Si vous souhaitez transformer des éléments d'une arborescence dans laquelle vous ne connaissez pas forcément grand chose des enfants des éléments que vous souhaitez transformer, cette approche qui utilise des annotations est une approche efficace.  
  
 La synthèse de l'approche est la suivante :  
  
- Tout d'abord, annotez les éléments de l'arborescence avec un élément de remplacement.  
  
- Ensuite, itérez l'ensemble de l'arborescence et créez une nouvelle arborescence où vous remplacez chaque élément par son annotation. Cet exemple implémente l'itération et la création de la nouvelle arborescence dans une fonction nommée `XForm`.  
  
 En détail, l'approche se compose des étapes suivantes :  
  
- Exécutez une ou plusieurs requêtes LINQ to XML qui retournent l'ensemble d'éléments que vous souhaitez transformer d'une forme à une autre. Pour chaque élément dans la requête, ajoutez un nouvel objet <xref:System.Xml.Linq.XElement> en tant qu'annotation de l'élément. Ce nouvel élément remplacera l’élément annoté dans la nouvelle arborescence transformée. Ce code est simple à écrire, comme illustré dans l'exemple.  
  
- Le nouvel élément ajouté en tant qu'annotation peut contenir de nouveaux nœuds enfants ; il peut former une sous-arborescence de toute forme souhaitée.  
  
- Il existe une règle spéciale : si un nœud enfant du nouvel élément est dans un espace de noms différent, un espace de noms créé à cet effet (dans cet exemple, l'espace de noms est `http://www.microsoft.com/LinqToXmlTransform/2007`), cet élément enfant n'est pas copié dans la nouvelle arborescence. Au lieu de cela, si l'espace de noms est l'espace de noms spécial mentionné ci-dessus et que le nom local de l'élément est `ApplyTransforms`, les nœuds enfants de l'élément dans l'arborescence source sont itérés et copiés dans la nouvelle arborescence (hormis le fait que les éléments enfants annotés sont eux-mêmes transformés conformément à ces règles).  
  
- Cela est quelque peu analogue à la spécification des transformations en XSL. La requête qui sélectionne un ensemble de nœuds est analogue à l'expression XPath pour un modèle. Le code permettant de créer le nouvel objet <xref:System.Xml.Linq.XElement> qui est enregistré en tant qu'annotation est analogue au constructeur de séquence en XSL et l'élément `ApplyTransforms` est analogue en termes de fonction à l'élément `xsl:apply-templates` en XSL.  
  
- L’un des avantages offerts par cette approche est que lorsque vous formulez des requêtes, vous écrivez toujours des requêtes sur l’arborescence source non modifiée. Vous n'avez pas à vous soucier de l'impact des modifications apportées à l'arborescence sur les requêtes que vous écrivez.  
  
## <a name="transforming-a-tree"></a>Transformation d'une arborescence  
 Ce premier exemple renomme tous les nœuds `Paragraph` à `para`.  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement root = XElement.Parse(@"  
<Root>  
    <Paragraph>This is a sentence with <b>bold</b> and <i>italic</i> text.</Paragraph>  
    <Paragraph>More text.</Paragraph>  
</Root>");  
  
// replace Paragraph with para  
foreach (var el in root.Descendants("Paragraph"))  
    el.AddAnnotation(  
        new XElement("para",  
            // same idea as xsl:apply-templates  
            new XElement(xf + "ApplyTransforms")  
        )  
    );  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newRoot = XForm(root);  
  
Console.WriteLine(newRoot);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```xml  
<Root>  
  <para>This is a sentence with <b>bold</b> and <i>italic</i> text.</para>  
  <para>More text.</para>  
</Root>  
```  
  
## <a name="a-more-complicated-transform"></a>Une transformation plus compliquée  
 L'exemple suivant interroge l'arborescence et calcule la moyenne et la somme des éléments `Data`, puis les ajoute à l'arborescence en tant que nouveaux éléments.  
  
```csharp  
XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
XName at = xf + "ApplyTransforms";  
  
XElement data = new XElement("Root",  
    new XElement("Data", 20),  
    new XElement("Data", 10),  
    new XElement("Data", 3)  
);  
  
// while adding annotations, you can query the source tree all you want,  
// as the tree is not mutated while annotating.
var avg = data.Elements("Data").Select(z => (Decimal)z).Average();
data.AddAnnotation(  
    new XElement("Root",  
        new XElement(xf + "ApplyTransforms"),  
        new XElement("Average", $"{avg:F4}"),
        new XElement("Sum",  
            data  
            .Elements("Data")  
            .Select(z => (int)z)  
            .Sum()  
        )  
    )  
);  
  
Console.WriteLine("Before Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(data);  
Console.WriteLine();  
Console.WriteLine();  
  
// The XForm method, shown later in this topic, accomplishes the transform  
XElement newData = XForm(data);  
  
Console.WriteLine("After Transform");  
Console.WriteLine("----------------");  
Console.WriteLine(newData);  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
Before Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
</Root>  
  
After Transform  
----------------  
<Root>  
  <Data>20</Data>  
  <Data>10</Data>  
  <Data>3</Data>  
  <Average>11.0000</Average>  
  <Sum>33</Sum>  
</Root>  
```  
  
## <a name="effecting-the-transform"></a>Réalisation de la transformation  
 Une petite fonction, `XForm`, crée une nouvelle arborescence transformée à partir de l'arborescence d'origine annotée.  
  
- Le pseudo code de la fonction est assez simple :  
  
```text  
The function takes an XElement as an argument and returns an XElement.
If an element has an XElement annotation, then  
    Return a new XElement  
        The name of the new XElement is the annotation element's name.  
        All attributes are copied from the annotation to the new node.  
        All child nodes are copied from the annotation, with the  
            exception that the special node xf:ApplyTransforms is  
            recognized, and the source element's child nodes are  
            iterated. If the source child node is not an XElement, it  
            is copied to the new tree. If the source child is an  
            XElement, then it is transformed by calling this function  
            recursively.  
If an element is not annotated  
    Return a new XElement  
        The name of the new XElement is the source element's name  
        All attributes are copied from the source element to the  
            destination's element.  
        All child nodes are copied from the source element.  
        If the source child node is not an XElement, it is copied to  
            the new tree. If the source child is an XElement, then it  
            is transformed by calling this function recursively.  
```  
  
 Voici l'implémentation de cette fonction :  
  
```csharp  
// Build a transformed XML tree per the annotations  
static XElement XForm(XElement source)  
{  
    XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    XName at = xf + "ApplyTransforms";  
  
    if (source.Annotation<XElement>() != null)  
    {  
        XElement anno = source.Annotation<XElement>();  
        return new XElement(anno.Name,  
            anno.Attributes(),  
            anno  
            .Nodes()  
            .Select(  
                (XNode n) =>  
                {  
                    XElement annoEl = n as XElement;  
                    if (annoEl != null)  
                    {  
                        if (annoEl.Name == at)  
                            return (object)(  
                                source.Nodes()  
                                .Select(  
                                    (XNode n2) =>  
                                    {  
                                        XElement e2 = n2 as XElement;  
                                        if (e2 == null)  
                                            return n2;  
                                        else  
                                            return XForm(e2);  
                                    }  
                                )  
                            );  
                        else  
                            return n;  
                    }  
                    else  
                        return n;  
                }  
            )  
        );  
    }  
    else  
    {  
        return new XElement(source.Name,  
            source.Attributes(),  
            source  
                .Nodes()  
                .Select(n =>  
                {  
                    XElement el = n as XElement;  
                    if (el == null)  
                        return n;  
                    else  
                        return XForm(el);  
                }  
                )  
        );  
    }  
}
```  
  
## <a name="complete-example"></a>Exemple complet  
 Le code suivant est un exemple complet qui inclut la fonction `XForm`. Il comprend certaines des utilisations courantes de ce type de transformation :  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Xml;  
using System.Xml.Linq;  
  
class Program  
{  
    static XNamespace xf = "http://www.microsoft.com/LinqToXmlTransform/2007";  
    static XName at = xf + "ApplyTransforms";  
  
    // Build a transformed XML tree per the annotations  
    static XElement XForm(XElement source)  
    {  
        if (source.Annotation<XElement>() != null)  
        {  
            XElement anno = source.Annotation<XElement>();  
            return new XElement(anno.Name,  
                anno.Attributes(),  
                anno  
                .Nodes()  
                .Select(  
                    (XNode n) =>  
                    {  
                        XElement annoEl = n as XElement;  
                        if (annoEl != null)  
                        {  
                            if (annoEl.Name == at)  
                                return (object)(  
                                    source.Nodes()  
                                    .Select(  
                                        (XNode n2) =>  
                                        {  
                                            XElement e2 = n2 as XElement;  
                                            if (e2 == null)  
                                                return n2;  
                                            else  
                                                return XForm(e2);  
                                        }  
                                    )  
                                );  
                            else  
                                return n;  
                        }  
                        else  
                            return n;  
                    }  
                )  
            );  
        }  
        else  
        {  
            return new XElement(source.Name,  
                source.Attributes(),  
                source  
                    .Nodes()  
                    .Select(n =>  
                    {  
                        XElement el = n as XElement;  
                        if (el == null)  
                            return n;  
                        else  
                            return XForm(el);  
                    }  
                    )  
            );  
        }  
    }  
  
    static void Main(string[] args)  
    {  
        XElement root = new XElement("Root",  
            new XComment("A comment"),  
            new XAttribute("Att1", 123),  
            new XElement("Child", 1),  
            new XElement("Child", 2),  
            new XElement("Other",  
                new XElement("GC", 3),  
                new XElement("GC", 4)  
            ),  
            XElement.Parse(  
              "<SomeMixedContent>This is <i>an</i> element that " +  
              "<b>has</b> some mixed content</SomeMixedContent>"),  
            new XElement("AnUnchangedElement", 42)  
        );  
  
        // each of the following serves the same semantic purpose as  
        // XSLT templates and sequence constructors  
  
        // replace Child with NewChild  
        foreach (var el in root.Elements("Child"))  
            el.AddAnnotation(new XElement("NewChild", (string)el));  
  
        // replace first GC with GrandChild, add an attribute  
        foreach (var el in root.Descendants("GC").Take(1))  
            el.AddAnnotation(  
                new XElement("GrandChild",  
                    new XAttribute("ANewAttribute", 999),  
                    (string)el  
                )  
            );  
  
        // replace Other with NewOther, add new child elements around original content  
        foreach (var el in root.Elements("Other"))  
            el.AddAnnotation(  
                new XElement("NewOther",  
                    new XElement("MyNewChild", 1),  
                    // same idea as xsl:apply-templates  
                    new XElement(xf + "ApplyTransforms"),  
                    new XElement("ChildThatComesAfter")  
                )  
            );  
  
        // change name of element that has mixed content  
        root.Descendants("SomeMixedContent").First().AddAnnotation(  
            new XElement("MixedContent",  
                new XElement(xf + "ApplyTransforms")  
            )  
        );  
  
        // replace <b> with <Bold>  
        foreach (var el in root.Descendants("b"))  
            el.AddAnnotation(  
                new XElement("Bold",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        // replace <i> with <Italic>  
        foreach (var el in root.Descendants("i"))  
            el.AddAnnotation(  
                new XElement("Italic",  
                    new XElement(xf + "ApplyTransforms")  
                )  
            );  
  
        Console.WriteLine("Before Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(root);  
        Console.WriteLine();  
        Console.WriteLine();  
        XElement newRoot = XForm(root);  
  
        Console.WriteLine("After Transform");  
        Console.WriteLine("----------------");  
        Console.WriteLine(newRoot);  
    }  
}  
```  
  
 Cet exemple produit la sortie suivante :  
  
```output  
Before Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <Child>1</Child>  
  <Child>2</Child>  
  <Other>  
    <GC>3</GC>  
    <GC>4</GC>  
  </Other>  
  <SomeMixedContent>This is <i>an</i> element that <b>has</b> some mixed content</SomeMixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
  
After Transform  
----------------  
<Root Att1="123">  
  <!--A comment-->  
  <NewChild>1</NewChild>  
  <NewChild>2</NewChild>  
  <NewOther>  
    <MyNewChild>1</MyNewChild>  
    <GrandChild ANewAttribute="999">3</GrandChild>  
    <GC>4</GC>  
    <ChildThatComesAfter />  
  </NewOther>  
  <MixedContent>This is <Italic>an</Italic> element that <Bold>has</Bold> some mixed content</MixedContent>  
  <AnUnchangedElement>42</AnUnchangedElement>  
</Root>  
```  
  