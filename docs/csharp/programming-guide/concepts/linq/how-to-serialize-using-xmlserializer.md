---
title: 'Procédure : Sérialiser à l’aide de XmlSerializer (C#)'
ms.date: 07/20/2015
ms.assetid: 2e0a0bbc-c548-4fe2-8741-be5a9ccd0cbb
ms.openlocfilehash: a3b9976dc4aaf132e8c3c8f03c678724db2b6989
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253332"
---
# <a name="how-to-serialize-using-xmlserializer-c"></a><span data-ttu-id="d8d2f-102">Procédure : Sérialiser à l’aide de XmlSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="d8d2f-102">How to: Serialize Using XmlSerializer (C#)</span></span>
<span data-ttu-id="d8d2f-103">Cette rubrique présente un exemple qui sérialise et désérialise à l'aide de <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="d8d2f-103">This topic shows an example that serializes and deserializes using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8d2f-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="d8d2f-104">Example</span></span>  
 <span data-ttu-id="d8d2f-105">L'exemple suivant crée plusieurs objets qui contiennent des objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="d8d2f-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="d8d2f-106">Il les sérialise ensuite dans un flux mémoire, puis les désérialise du flux mémoire.</span><span class="sxs-lookup"><span data-stu-id="d8d2f-106">It then serializes them to a memory stream, and then deserializes them from the memory stream.</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Linq;  
using System.Xml;  
using System.Xml.Serialization;  
using System.Xml.Linq;  
  
public class XElementContainer  
{  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
  
    public override string ToString()  
    {  
        return member.ToString();  
    }  
}  
  
public class XElementNullContainer  
{  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
    }  
}  
  
class XLinqTest  
{  
    static void Main(string[] args)  
    {  
        Test<XElementNullContainer>(new XElementNullContainer());  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
    }  
  
    public static XElement CreateXElement()  
    {  
        XNamespace ns = "http://www.adventure-works.com";  
        return new XElement(ns + "aw");  
    }  
  
    static void Test<T>(T obj)  
    {  
        using (MemoryStream stream = new MemoryStream())  
        {  
            XmlSerializer s = new XmlSerializer(typeof(T));  
            Console.WriteLine("Testing for type: {0}", typeof(T));  
            s.Serialize(XmlWriter.Create(stream), obj);  
            stream.Flush();  
            stream.Seek(0, SeekOrigin.Begin);  
            object o = s.Deserialize(XmlReader.Create(stream));  
            Console.WriteLine("  Deserialized type: {0}", o.GetType());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="d8d2f-107">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="d8d2f-107">This example produces the following output:</span></span>  
  
```output  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
```  
