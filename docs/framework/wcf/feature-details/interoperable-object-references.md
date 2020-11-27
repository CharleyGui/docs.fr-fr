---
title: Références d’objets interopérables
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: bf395c187c46e88406bfb81798c7e359b48255e3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263228"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="7c438-102">Références d’objets interopérables</span><span class="sxs-lookup"><span data-stu-id="7c438-102">Interoperable object references</span></span>

<span data-ttu-id="7c438-103">Par défaut, <xref:System.Runtime.Serialization.DataContractSerializer> sérialise les objets par valeur.</span><span class="sxs-lookup"><span data-stu-id="7c438-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="7c438-104">Vous pouvez utiliser la <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> propriété pour indiquer au sérialiseur de contrat de données de conserver les références d’objet lors de la sérialisation d’objets.</span><span class="sxs-lookup"><span data-stu-id="7c438-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="7c438-105">XML généré</span><span class="sxs-lookup"><span data-stu-id="7c438-105">Generated XML</span></span>  

 <span data-ttu-id="7c438-106">À titre d'exemple, considérez l'objet suivant :</span><span class="sxs-lookup"><span data-stu-id="7c438-106">As an example, consider the following object:</span></span>  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass
{  
}  
```  
  
 <span data-ttu-id="7c438-107">Lorsque <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> a la valeur `false` (valeur par défaut), le code XML suivant est généré :</span><span class="sxs-lookup"><span data-stu-id="7c438-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="7c438-108">Lorsque <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> a la valeur `true`, le code XML suivant est généré :</span><span class="sxs-lookup"><span data-stu-id="7c438-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="7c438-109">Toutefois, <xref:System.Runtime.Serialization.XsdDataContractExporter> ne décrit pas `id` les `ref` attributs et dans son schéma, même lorsque la `preserveObjectReferences` propriété a la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="7c438-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="7c438-110">Utilisation d'IsReference</span><span class="sxs-lookup"><span data-stu-id="7c438-110">Using IsReference</span></span>  

 <span data-ttu-id="7c438-111">Pour générer des informations de référence d’objet qui sont valides selon le schéma qui les décrit, appliquez l' <xref:System.Runtime.Serialization.DataContractAttribute> attribut à un type et affectez à l’indicateur la valeur <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="7c438-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="7c438-112">L’exemple suivant modifie la classe `X` dans l’exemple précédent en ajoutant `IsReference` :</span><span class="sxs-lookup"><span data-stu-id="7c438-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
```csharp
[DataContract(IsReference=true)]
public class X
{  
     SomeClass someInstance = new SomeClass();
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember]
     public SomeClass B = someInstance;
}
  
public class SomeClass
{
}  
````

 <span data-ttu-id="7c438-113">Le XML généré est le suivant :</span><span class="sxs-lookup"><span data-stu-id="7c438-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="7c438-114">L'utilisation d'`IsReference` garantit la conformité dans l'aller-retour du message.</span><span class="sxs-lookup"><span data-stu-id="7c438-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="7c438-115">Sans lui, lorsqu’un type est généré à partir du schéma, la sortie XML de ce type n’est pas nécessairement compatible avec le schéma initialement utilisé.</span><span class="sxs-lookup"><span data-stu-id="7c438-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="7c438-116">En d'autres termes, bien que les attributs `id` et `ref` aient été sérialisés, le schéma d'origine aurait pu empêcher ces attributs (ou tous les attributs) d'apparaître dans le XML.</span><span class="sxs-lookup"><span data-stu-id="7c438-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="7c438-117">`IsReference`Lorsqu’il est appliqué à un membre de données, le membre continue d’être reconnu comme étant *référençable* lors d’un aller-retour.</span><span class="sxs-lookup"><span data-stu-id="7c438-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c438-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7c438-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
