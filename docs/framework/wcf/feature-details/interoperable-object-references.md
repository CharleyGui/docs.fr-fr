---
title: Références d’objets interopérables
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 0927f217a1666f8f27ca9c3e68f80a96b9c0f2b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184706"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="83e03-102">Références d’objets interopérables</span><span class="sxs-lookup"><span data-stu-id="83e03-102">Interoperable object references</span></span>
<span data-ttu-id="83e03-103">Par défaut, <xref:System.Runtime.Serialization.DataContractSerializer> sérialis les objets par valeur.</span><span class="sxs-lookup"><span data-stu-id="83e03-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="83e03-104">Vous pouvez <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> utiliser la propriété pour instruire le sérialisateur contrat de données afin de préserver les références d’objets lors de la sérialisation d’objets.</span><span class="sxs-lookup"><span data-stu-id="83e03-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="83e03-105">XML généré</span><span class="sxs-lookup"><span data-stu-id="83e03-105">Generated XML</span></span>  
 <span data-ttu-id="83e03-106">À titre d'exemple, considérez l'objet suivant :</span><span class="sxs-lookup"><span data-stu-id="83e03-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="83e03-107">Lorsque <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> a la valeur `false` (valeur par défaut), le code XML suivant est généré :</span><span class="sxs-lookup"><span data-stu-id="83e03-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="83e03-108">Lorsque <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> a la valeur `true`, le code XML suivant est généré :</span><span class="sxs-lookup"><span data-stu-id="83e03-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="83e03-109">Cependant, <xref:System.Runtime.Serialization.XsdDataContractExporter> ne décrit `id` pas `ref` le et les attributs `preserveObjectReferences` dans son `true`schéma, même lorsque la propriété est réglée à .</span><span class="sxs-lookup"><span data-stu-id="83e03-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="83e03-110">Utilisation d'IsReference</span><span class="sxs-lookup"><span data-stu-id="83e03-110">Using IsReference</span></span>  
 <span data-ttu-id="83e03-111">Pour générer des informations de référence d’objet qui sont valides selon le schéma qui les décrit, appliquez l’attribut <xref:System.Runtime.Serialization.DataContractAttribute> à un type, et définissez le <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> drapeau à `true`.</span><span class="sxs-lookup"><span data-stu-id="83e03-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="83e03-112">L’exemple suivant `X` modifie la classe `IsReference`dans l’exemple précédent en ajoutant :</span><span class="sxs-lookup"><span data-stu-id="83e03-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="83e03-113">Le XML généré est le suivant :</span><span class="sxs-lookup"><span data-stu-id="83e03-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="83e03-114">L'utilisation d'`IsReference` garantit la conformité dans l'aller-retour du message.</span><span class="sxs-lookup"><span data-stu-id="83e03-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="83e03-115">Sans elle, quand un type est généré à partir de schéma, la sortie XML pour ce type n’est pas nécessairement compatible avec le schéma initialement supposé.</span><span class="sxs-lookup"><span data-stu-id="83e03-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="83e03-116">En d'autres termes, bien que les attributs `id` et `ref` aient été sérialisés, le schéma d'origine aurait pu empêcher ces attributs (ou tous les attributs) d'apparaître dans le XML.</span><span class="sxs-lookup"><span data-stu-id="83e03-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="83e03-117">Avec `IsReference` une demande à un membre de données, le membre continue d’être reconnu comme *référencé* lorsqu’il est trébuché.</span><span class="sxs-lookup"><span data-stu-id="83e03-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83e03-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83e03-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
