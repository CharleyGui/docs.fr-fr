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
# <a name="how-to-catch-parsing-errors-c"></a>Procédure : Intercepter les erreurs d’analyse (C#)
Cette rubrique montre comment détecter du code XML incorrect ou non valide.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] est implémenté avec <xref:System.Xml.XmlReader>. Si du code XML incorrect ou non valide est passé à [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], la classe sous-jacente <xref:System.Xml.XmlReader> ève une exception. Les différentes méthodes qui analysent le code XML, telles que <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, n’interceptent pas l’exception. Celle-ci peut donc être interceptée par votre application.  
  
## <a name="example"></a>Exemples  
 Le code suivant tente d'analyser du code XML non valide :  
  
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
  
 Lorsque vous exécutez ce code, l'exception suivante est levée :  
  
```console  
The 'Contacts' start tag on line 1 does not match the end tag of 'Contcts'. Line 5, position 13.  
```  
  
 Pour plus d'informations sur les exceptions que les méthodes <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>, <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType> et <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType> peuvent lever, consultez la documentation <xref:System.Xml.XmlReader>.  
  