---
title: 'Procédure : Intercepter les erreurs d’analyse (C#)'
ms.date: 07/20/2015
ms.assetid: bfb612d4-5605-48ef-8c93-915cf9d5dcfb
ms.openlocfilehash: 4195ff50d1b4d23cd9eb07fc27f20861d1504672
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204149"
---
# <a name="how-to-catch-parsing-errors-c"></a><span data-ttu-id="0ca7c-102">Procédure : Intercepter les erreurs d’analyse (C#)</span><span class="sxs-lookup"><span data-stu-id="0ca7c-102">How to: Catch Parsing Errors (C#)</span></span>
<span data-ttu-id="0ca7c-103">Cette rubrique montre comment détecter du code XML incorrect ou non valide.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-103">This topic shows how to detect badly formed or invalid XML.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <span data-ttu-id="0ca7c-104">est implémenté avec <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-104">is implemented using <xref:System.Xml.XmlReader>.</span></span> <span data-ttu-id="0ca7c-105">Si du code XML incorrect ou non valide est passé à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], la classe sous-jacente <xref:System.Xml.XmlReader> ève une exception.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-105">If badly formed or invalid XML is passed to [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], the underlying <xref:System.Xml.XmlReader> class will throw an exception.</span></span> <span data-ttu-id="0ca7c-106">Les différentes méthodes qui analysent le code XML, telles que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, n’interceptent pas l’exception. Celle-ci peut donc être interceptée par votre application.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-106">The various methods that parse XML, such as <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, do not catch the exception; the exception can then be caught by your application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ca7c-107">Exemples</span><span class="sxs-lookup"><span data-stu-id="0ca7c-107">Example</span></span>  
 <span data-ttu-id="0ca7c-108">Le code suivant tente d'analyser du code XML non valide :</span><span class="sxs-lookup"><span data-stu-id="0ca7c-108">The following code tries to parse invalid XML:</span></span>  
  
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
  
 <span data-ttu-id="0ca7c-109">Lorsque vous exécutez ce code, l'exception suivante est levée :</span><span class="sxs-lookup"><span data-stu-id="0ca7c-109">When you run this code, it throws the following exception:</span></span>  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 <span data-ttu-id="0ca7c-110">Pour plus d'informations sur les exceptions que les méthodes <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> peuvent lever, consultez la documentation <xref:System.Xml.XmlReader>.</span><span class="sxs-lookup"><span data-stu-id="0ca7c-110">For information about the exceptions that you can expect the <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>, and <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> methods to throw, see the <xref:System.Xml.XmlReader> documentation.</span></span>  
  