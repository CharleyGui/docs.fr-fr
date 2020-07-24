---
title: Comment intercepter les erreurs d’analyse (C#)
description: Cet exemple de LINQ to XML en C# détecte un code XML incorrect ou non valide. LINQ to XML utilise XmlReader, qui lève une exception pour un code XML incorrect ou non valide.
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 0a891097322ef6acce062ea927692b01cc425e6c
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105416"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="c36d7-104">Comment intercepter les erreurs d’analyse (C#)</span><span class="sxs-lookup"><span data-stu-id="c36d7-104">How to catch parsing errors (C#)</span></span>
<span data-ttu-id="c36d7-105">Cette rubrique montre comment détecter du code XML incorrect ou non valide.</span><span class="sxs-lookup"><span data-stu-id="c36d7-105">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="c36d7-106">est implémenté avec <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c36d7-106">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="c36d7-107">Si du code XML incorrect ou non valide est passé à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], la classe sous-jacente <xref:System.Xml.XmlReader> ève une exception.</span><span class="sxs-lookup"><span data-stu-id="c36d7-107">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="c36d7-108">Les différentes méthodes qui analysent le code XML, telles que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, n’interceptent pas l’exception. Celle-ci peut donc être interceptée par votre application.</span><span class="sxs-lookup"><span data-stu-id="c36d7-108">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c36d7-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="c36d7-109">Example</span></span>  
 <span data-ttu-id="c36d7-110">Le code suivant tente d'analyser du code XML non valide :</span><span class="sxs-lookup"><span data-stu-id="c36d7-110">The following code tries to parse invalid XML:</span></span>  
  
```csharp  
try {  
    XElement contacts = XElement.Parse(  
        @"<Contacts>  
            <Contact>  
                <Name>Jim Wilson</Name>  
            </Contact>  
          </Contcts>");  
  
    Console.WriteLine(contacts);  
}  
catch (System.Xml.XmlException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
 <span data-ttu-id="c36d7-111">Lorsque vous exécutez ce code, l'exception suivante est levée :</span><span class="sxs-lookup"><span data-stu-id="c36d7-111">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="c36d7-112">Pour plus d'informations sur les exceptions que les méthodes <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> peuvent lever, consultez la documentation <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="c36d7-112">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  