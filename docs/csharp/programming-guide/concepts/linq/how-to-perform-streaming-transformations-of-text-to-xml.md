---
title: 'Procédure : Effectuer des transformations de streaming de texte au format XML (C#)'
ms.date: 07/20/2015
ms.assetid: 9b3bd941-d0ff-4f2d-ae41-7c3b81d8fae6
ms.openlocfilehash: d37ea5167576098d4ea343e49ae4ff6bac20d4ba
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485248"
---
# <a name="how-to-perform-streaming-transformations-of-text-to-xml-c"></a>Procédure : Effectuer des transformations de streaming de texte au format XML (C#)
L'une des façons de traiter un fichier texte consiste à écrire une méthode d'extension qui diffuse en continu le fichier texte une ligne à la fois à l'aide de la construction `yield return`. Vous pouvez alors écrire une requête LINQ qui traite le fichier texte de manière différée. Si vous utilisez ensuite <xref:System.Xml.Linq.XStreamingElement> pour diffuser la sortie en continu, vous pouvez créer une transformation du fichier texte en XML qui utilise une quantité minimale de mémoire, quelle que soit la taille du fichier texte source.  
  
 Il existe certains points à noter concernant les transformations de diffusion en continu. Il est préférable d'appliquer une transformation de streaming dans les situations où vous pouvez traiter l'intégralité du fichier une seule fois et si vous pouvez traiter les lignes dans l'ordre dans lequel elles apparaissent dans le document source. Si vous devez traiter le fichier à plusieurs reprises, ou si vous devez trier les lignes avant de les traiter, vous perdez une grande partie des avantages offerts par l'utilisation d'une technique de streaming.  
  
## <a name="example"></a>Exemple  
 Le fichier texte suivant, People.txt, est la source pour cet exemple.  
  
```  
#This is a comment  
1,Tai,Yee,Writer  
2,Nikolay,Grachev,Programmer  
3,David,Wright,Inventor  
```  
  
 Le code suivant contient une méthode d'extension qui diffuse en continu les lignes du fichier texte de manière différée.  
  
```csharp  
public static class StreamReaderSequence  
{  
    public static IEnumerable<string> Lines(this StreamReader source)  
    {  
        String line;  
  
        if (source == null)  
            throw new ArgumentNullException("source");  
        while ((line = source.ReadLine()) != null)  
        {  
            yield return line;  
        }  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        StreamReader sr = new StreamReader("People.txt");  
        XStreamingElement xmlTree = new XStreamingElement("Root",  
            from line in sr.Lines()  
            let items = line.Split(',')  
            where !line.StartsWith("#")  
            select new XElement("Person",  
                       new XAttribute("ID", items[0]),  
                       new XElement("First", items[1]),  
                       new XElement("Last", items[2]),  
                       new XElement("Occupation", items[3])  
                   )  
        );  
        Console.WriteLine(xmlTree);  
        sr.Close();  
    }  
}  
```  
  
 Cet exemple génère la sortie suivante :  
  
```xml  
<Root>  
  <Person ID="1">  
    <First>Tai</First>  
    <Last>Yee</Last>  
    <Occupation>Writer</Occupation>  
  </Person>  
  <Person ID="2">  
    <First>Nikolay</First>  
    <Last>Grachev</Last>  
    <Occupation>Programmer</Occupation>  
  </Person>  
  <Person ID="3">  
    <First>David</First>  
    <Last>Wright</Last>  
    <Occupation>Inventor</Occupation>  
  </Person>  
</Root>  
```  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Xml.Linq.XStreamingElement>
