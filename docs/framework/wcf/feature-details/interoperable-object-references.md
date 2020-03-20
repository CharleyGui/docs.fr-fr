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
# <a name="interoperable-object-references"></a>Références d’objets interopérables
Par défaut, <xref:System.Runtime.Serialization.DataContractSerializer> sérialis les objets par valeur. Vous pouvez <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> utiliser la propriété pour instruire le sérialisateur contrat de données afin de préserver les références d’objets lors de la sérialisation d’objets.  
  
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
  
 Cependant, <xref:System.Runtime.Serialization.XsdDataContractExporter> ne décrit `id` pas `ref` le et les attributs `preserveObjectReferences` dans son `true`schéma, même lorsque la propriété est réglée à .  
  
## <a name="using-isreference"></a>Utilisation d'IsReference  
 Pour générer des informations de référence d’objet qui sont valides selon le schéma qui les décrit, appliquez l’attribut <xref:System.Runtime.Serialization.DataContractAttribute> à un type, et définissez le <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> drapeau à `true`. L’exemple suivant `X` modifie la classe `IsReference`dans l’exemple précédent en ajoutant :  
  
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
  
 L'utilisation d'`IsReference` garantit la conformité dans l'aller-retour du message. Sans elle, quand un type est généré à partir de schéma, la sortie XML pour ce type n’est pas nécessairement compatible avec le schéma initialement supposé. En d'autres termes, bien que les attributs `id` et `ref` aient été sérialisés, le schéma d'origine aurait pu empêcher ces attributs (ou tous les attributs) d'apparaître dans le XML. Avec `IsReference` une demande à un membre de données, le membre continue d’être reconnu comme *référencé* lorsqu’il est trébuché.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
