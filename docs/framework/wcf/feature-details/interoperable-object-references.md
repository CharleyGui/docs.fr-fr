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
# <a name="interoperable-object-references"></a>Références d’objets interopérables

Par défaut, <xref:System.Runtime.Serialization.DataContractSerializer> sérialise les objets par valeur. Vous pouvez utiliser la <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> propriété pour indiquer au sérialiseur de contrat de données de conserver les références d’objet lors de la sérialisation d’objets.  
  
## <a name="generated-xml"></a>XML généré  

 À titre d'exemple, considérez l'objet suivant :  
  
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
  
 Lorsque <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> a la valeur `false` (valeur par défaut), le code XML suivant est généré :  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 Lorsque <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> a la valeur `true`, le code XML suivant est généré :  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 Toutefois, <xref:System.Runtime.Serialization.XsdDataContractExporter> ne décrit pas `id` les `ref` attributs et dans son schéma, même lorsque la `preserveObjectReferences` propriété a la valeur `true` .  
  
## <a name="using-isreference"></a>Utilisation d'IsReference  

 Pour générer des informations de référence d’objet qui sont valides selon le schéma qui les décrit, appliquez l' <xref:System.Runtime.Serialization.DataContractAttribute> attribut à un type et affectez à l’indicateur la valeur <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> `true` . L’exemple suivant modifie la classe `X` dans l’exemple précédent en ajoutant `IsReference` :  
  
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

 Le XML généré est le suivant :  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 L'utilisation d'`IsReference` garantit la conformité dans l'aller-retour du message. Sans lui, lorsqu’un type est généré à partir du schéma, la sortie XML de ce type n’est pas nécessairement compatible avec le schéma initialement utilisé. En d'autres termes, bien que les attributs `id` et `ref` aient été sérialisés, le schéma d'origine aurait pu empêcher ces attributs (ou tous les attributs) d'apparaître dans le XML. `IsReference`Lorsqu’il est appliqué à un membre de données, le membre continue d’être reconnu comme étant *référençable* lors d’un aller-retour.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
