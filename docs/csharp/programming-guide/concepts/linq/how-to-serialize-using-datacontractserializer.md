---
title: 'Procédure : Sérialiser à l’aide de DataContractSerializer (C#)'
ms.date: 07/20/2015
ms.assetid: 3320ecbf-cdbe-480e-979c-2c14bbef9988
ms.openlocfilehash: 2b4800e2c6d210d62ab3093b673898a147c1f92d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253342"
---
# <a name="how-to-serialize-using-datacontractserializer-c"></a><span data-ttu-id="36c66-102">Procédure : Sérialiser à l’aide de DataContractSerializer (C#)</span><span class="sxs-lookup"><span data-stu-id="36c66-102">How to: Serialize Using DataContractSerializer (C#)</span></span>
<span data-ttu-id="36c66-103">Cette rubrique présente un exemple qui sérialise et désérialise à l'aide de <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="36c66-103">This topic shows an example that serializes and deserializes using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36c66-104">Exemple</span><span class="sxs-lookup"><span data-stu-id="36c66-104">Example</span></span>  
 <span data-ttu-id="36c66-105">L'exemple suivant crée plusieurs objets qui contiennent des objets <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="36c66-105">The following example creates a number of objects that contain <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="36c66-106">Il les sérialise ensuite dans des fichiers texte, puis les désérialise à partir des fichiers texte.</span><span class="sxs-lookup"><span data-stu-id="36c66-106">It then serializes them to text files, and then deserializes them from the text files.</span></span>  
  
```csharp  
using System;  
using System.Xml;  
using System.Xml.Linq;  
using System.IO;  
using System.Runtime.Serialization;  
  
public class XLinqTest  
{  
    public static void Main()  
    {  
        Test<XElement>(CreateXElement());  
        Test<XElementContainer>(new XElementContainer());  
        Test<XElementNullContainer>(new XElementNullContainer());  
    }  
  
    public static void Test<T>(T obj)  
    {  
        DataContractSerializer s = new DataContractSerializer(typeof(T));  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Create))  
        {  
            Console.WriteLine("Testing for type: {0}", typeof(T));   
            s.WriteObject(fs, obj);  
        }  
        using (FileStream fs = File.Open("test" + typeof(T).Name + ".xml", FileMode.Open))  
        {  
            object s2 = s.ReadObject(fs);  
            if (s2 == null)  
                Console.WriteLine("  Deserialized object is null (Nothing in VB)");  
            else  
                Console.WriteLine("  Deserialized type: {0}", s2.GetType());  
        }  
    }  
  
    public static XElement CreateXElement()  
    {  
        return new XElement(XName.Get("NameInNamespace", "http://www.adventure-works.org"));  
    }  
}  
  
[DataContract]  
public class XElementContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementContainer()  
    {  
        member = XLinqTest.CreateXElement();  
    }  
}  
  
[DataContract]  
public class XElementNullContainer  
{  
    [DataMember]  
    public XElement member;  
  
    public XElementNullContainer()  
    {  
        member = null;  
    }  
}  
```  
  
 <span data-ttu-id="36c66-107">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="36c66-107">This example produces the following output:</span></span>  
  
```output  
Testing for type: System.Xml.Linq.XElement  
  Deserialized type: System.Xml.Linq.XElement  
Testing for type: XElementContainer  
  Deserialized type: XElementContainer  
Testing for type: XElementNullContainer  
  Deserialized type: XElementNullContainer  
```  
