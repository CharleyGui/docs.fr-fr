---
title: Valeurs par défaut des membres de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data members [WCF], default values
- data members [WCF]
ms.assetid: 53a3b505-4b27-444b-b079-0eb84a97cfd8
ms.openlocfilehash: af8fff9d034f8dea4ce9f24a2bda042b5b9708a9
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881264"
---
# <a name="data-member-default-values"></a>Valeurs par défaut des membres de données
Dans le .NET Framework, les types possèdent un concept de *valeurs par défaut*. Ainsi, la valeur par défaut d'un type référence est `null`, et celle d'un type entier est zéro. Il est parfois préférable d'omettre un membre de données des données sérialisées lorsqu'il est défini à sa valeur par défaut. Le membre ayant une valeur par défaut, il n'est pas nécessaire de sérialiser une valeur réelle ; cela présente un avantage en termes de performance.  
  
 Pour omettre un membre des données sérialisées, affectez <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> à la propriété <xref:System.Runtime.Serialization.DataMemberAttribute> de l'attribut `false` (la valeur par défaut est `true`).  
  
> [!NOTE]
>  Vous devez uniquement affecter la valeur <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> à la propriété `false` en cas de besoin spécifique, par exemple à des fins d'interopérabilité ou pour réduire la taille des données.  
  
## <a name="example"></a>Exemple  
 Le code suivant a plusieurs membres avec <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> défini à `false`.  
  
 [!code-csharp[DataMemberAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datamemberattribute/cs/overview.cs#4)]
 [!code-vb[DataMemberAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datamemberattribute/vb/overview.vb#4)]  
  
 Si une instance de cette classe est sérialisée, le résultat est le suivant : `employeeName` et `employeeID` sont sérialisés. La valeur null pour `employeeName` et la valeur zéro pour `employeeID` font explicitement partie des données sérialisées. Toutefois, les membres `position`, `salary` et `bonus` ne sont pas sérialisées. Enfin, `targetSalary` est sérialisé comme d'habitude, même si la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a la valeur `false`, car 57800 ne correspond pas à la valeur .NET par défaut pour un entier, qui est zéro.  
  
### <a name="xml-representation"></a>Représentation XML  
 Si l'exemple précédent est sérialisé en XML, la représentation est similaire à la suivante.  
  
```xml  
<Employee>  
   <employeeName xsi:nil="true" />  
   <employeeID>0</employeeID>  
<targetSalary>57800</targetSalary>  
</Employee>  
```  
  
 L’attribut `xsi:nil` est un attribut spécial dans l’espace de noms de l’instance WC3 (World Wide Web Consortium ) XML Schema qui offre un moyen interopérable pour représenter explicitement une valeur null. Notez que le XML ne contient aucune information sur le poste, le salaire et les primes des membres de données. L'extrémité de réception peut les interpréter comme `null`, zéro et `null`, respectivement. Il n'y a aucune garantie qu'un désérialiseur tiers puisse effectuer correctement l'interprétation ; c'est pourquoi ce modèle n'est pas recommandé. La classe <xref:System.Runtime.Serialization.DataContractSerializer> sélectionne systématiquement l'interprétation correcte pour les valeurs manquantes.  
  
### <a name="interaction-with-isrequired"></a>Interaction avec IsRequired  
 Comme indiqué dans [concernant les contrats de données](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md), le <xref:System.Runtime.Serialization.DataMemberAttribute> attribut a un <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> propriété (la valeur par défaut est `false`). La propriété indique si un membre de données spécifique doit ou non être présent dans les données sérialisées lorsqu'il est désérialisé. Si `IsRequired` a la valeur `true` (ce qui indique qu'une valeur doit être présente) et que <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a la valeur `false` (ce qui indique que la valeur ne doit pas être présente si la valeur indiquée est celle par défaut), les valeurs par défaut de ce membre de données ne peuvent pas être sérialisées car les résultats seraient contradictoires. Si un membre de données de ce type à pour valeur sa valeur par défaut (généralement `null` ou zéro) et qu'une sérialisation est tentée, une exception <xref:System.Runtime.Serialization.SerializationException> est levée.  
  
### <a name="schema-representation"></a>Représentation de schéma  
 Les détails de la représentation de schéma XML Schema definition language (XSD) des membres de données lorsque le `EmitDefaultValue` propriété est définie sur `false` sont abordées dans [Data Contract Schema Reference](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Toutefois, en voici une brève vue d'ensemble :  
  
- Lorsque le <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> a la valeur `false`, elle est représentée dans le schéma en tant qu’annotation spécifique à Windows Communication Foundation (WCF). Il n'existe pas de moyen interopérable pour représenter ces informations. En particulier, l'attribut "default" dans le schéma n'est pas utilisé à cette fin, l'attribut `minOccurs` est uniquement affecté par le paramètre <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>, et l'attribut `nillable` est uniquement affecté par le type du membre de données.  
  
- La valeur par défaut réelle à utiliser n'est pas présente dans le schéma. C'est au point de terminaison de réception d'interpréter correctement un élément manquant.  
  
 Lors de l’importation de schéma, le <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A> propriété est automatiquement définie sur `false` chaque fois que l’annotation spécifiques à WCF mentionnée précédemment est détectée. Il est également défini sur `false` pour les types de référence qui ont le `nillable` propriété définie sur `false` pour prendre en charge les scénarios d’interopérabilité spécifiques qui se produisent généralement lors de la consommation de services Web ASP.NET.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataMemberAttribute.EmitDefaultValue%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
