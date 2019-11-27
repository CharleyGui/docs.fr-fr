---
title: "Comment : intercepter des erreurs d'analyse"
ms.date: 07/20/2015
ms.assetid: 22e9068e-ea58-447b-816e-cd1852c11787
ms.openlocfilehash: 14c4f76c5f10616f9346084cda276e2862b2b41d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353342"
---
# <a name="how-to-catch-parsing-errors-visual-basic"></a><span data-ttu-id="ed23d-102">Comment : intercepter des erreurs d’analyse (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed23d-102">How to: Catch Parsing Errors (Visual Basic)</span></span>
<span data-ttu-id="ed23d-103">Cette rubrique montre comment détecter du code XML incorrect ou non valide.</span><span class="sxs-lookup"><span data-stu-id="ed23d-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="ed23d-104">est implémenté avec <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="ed23d-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="ed23d-105">Si du code XML incorrect ou non valide est passé à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], la classe sous-jacente <xref:System.Xml.XmlReader> ève une exception.</span><span class="sxs-lookup"><span data-stu-id="ed23d-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="ed23d-106">Les différentes méthodes qui analysent le code XML, telles que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, n’interceptent pas l’exception. Celle-ci peut donc être interceptée par votre application.</span><span class="sxs-lookup"><span data-stu-id="ed23d-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
 <span data-ttu-id="ed23d-107">Notez que vous ne pouvez pas obtenir d'erreurs d'analyse si vous utilisez des littéraux XML.</span><span class="sxs-lookup"><span data-stu-id="ed23d-107">Note that you cannot get parse errors if you use XML literals.</span></span> <span data-ttu-id="ed23d-108">Le compilateur Visual Basic intercepte les erreurs de code XML incorrect ou non valide.</span><span class="sxs-lookup"><span data-stu-id="ed23d-108">The Visual Basic compiler will catch errors of badly formed or invalid XML.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed23d-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed23d-109">Example</span></span>  
 <span data-ttu-id="ed23d-110">Le code suivant tente d'analyser du code XML non valide :</span><span class="sxs-lookup"><span data-stu-id="ed23d-110">The following code tries to parse invalid XML:</span></span>  
  
```vb  
Try  
    Dim contacts As XElement = XElement.Parse("<Contacts>" & vbCrLf & _  
        "    <Contact>" & vbCrLf & _  
        "        <Name>Jim Wilson</Name>" & vbCrLf & _  
        "    </Contact>" & vbCrLf & _  
        "</Contcts>")  
  
    Console.WriteLine(contacts)  
Catch e As System.Xml.XmlException  
    Console.WriteLine(e.Message)  
End Try  
```  
  
 <span data-ttu-id="ed23d-111">Lorsque vous exécutez ce code, l'exception suivante est levée :</span><span class="sxs-lookup"><span data-stu-id="ed23d-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="ed23d-112">Pour plus d'informations sur les exceptions que les méthodes <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> peuvent lever, consultez la documentation <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="ed23d-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed23d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed23d-113">See also</span></span>

- [<span data-ttu-id="ed23d-114">Analyse XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed23d-114">Parsing XML (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
