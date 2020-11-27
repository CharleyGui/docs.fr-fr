---
title: Contrôle de version des contrats de données
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
ms.openlocfilehash: 6f8623c9d8e9e7ba1f7c762c929f986b523c2f90
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96285198"
---
# <a name="data-contract-versioning"></a>Contrôle de version des contrats de données

À mesure que les applications évoluent, il peut s'avérer nécessaire de modifier les contrats de données utilisés par les services. Cette rubrique explique comment assigner des versions aux contrats de données. Cette rubrique décrit les mécanismes de contrôle de version des contrats de données. Pour obtenir une vue d’ensemble complète et des instructions de contrôle de version normatives, consultez [meilleures pratiques :](../best-practices-data-contract-versioning.md)contrôle de version des contrats de données.  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Modifications avec et sans rupture  

 Les modifications apportées à un contrat de données peuvent être avec ou sans rupture. Lorsqu'un contrat de données est modifié sans rupture, une application utilisant l'ancienne version du contrat peut communiquer avec une application utilisant la version plus récente, et vice versa. D'autre part, une modification avec rupture empêche la communication dans une ou les deux directions.  
  
 Les modifications apportées à un type qui n'affectent pas la façon dont il est transmis sont dites « sans rupture ». Les modifications de ce type n'affectent pas le contrat de données, mais uniquement le type sous-jacent. Par exemple, vous pouvez modifier le nom d'un champ sans rupture si vous affectez ensuite le nom de l'ancienne version à la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> de <xref:System.Runtime.Serialization.DataMemberAttribute>. Le code suivant présente la version 1 d'un contrat de données.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Le code suivant présente une modification sans rupture.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Certaines modifications affectent les données transmises, mais peuvent être avec ou sans rupture. Les modifications suivantes sont toujours avec rupture :  
  
- Modification de la valeur <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> ou <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> d'un contrat de données.  
  
- Modification de l'ordre de membres de données à l'aide de la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> de <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
- Attribution d'un nouveau nom à un membre de données.  
  
- Modification du contrat de données d'un membre de données. Par exemple, modification du type de membre de données d'un entier en une chaîne, ou d'un type avec un contrat de données « Customer » en un type avec un contrat de données « Person ».  
  
 Les modifications suivantes sont également possibles :  
  
## <a name="adding-and-removing-data-members"></a>Ajout et suppression de membres de données  

 Dans la plupart des cas, l'ajout ou la suppression d'un membre de données n'est pas une modification avec rupture, sauf si vous exigez la validité stricte du schéma (nouvelles instances qui valident l'ancien schéma).  
  
 Lorsqu'un type avec un champ supplémentaire est désérialisé dans un type avec un champ manquant, les informations supplémentaires sont ignorées. (Elles peuvent également être stockées à des fins d’aller-retour ; pour plus d’informations, consultez [contrats de données à compatibilité ascendante](forward-compatible-data-contracts.md)).  
  
 Lorsqu'un type avec un champ manquant est désérialisé dans un type avec un champ supplémentaire, le champ supplémentaire conserve sa valeur par défaut, généralement zéro ou `null`. (La valeur par défaut peut être modifiée. pour plus d’informations, consultez [rappels de sérialisation avec tolérance de version](version-tolerant-serialization-callbacks.md).)  
  
 Par exemple, vous pouvez utiliser la classe `CarV1` sur un client et la classe `CarV2` sur un service, ou la classe `CarV1` sur un service et la classe `CarV2` sur un client.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Le point de terminaison version 2 peut envoyer des données au point de terminaison version 1. La sérialisation de la version 2 du contrat de données `Car` génère du code XML semblable au code suivant.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 Le moteur de désérialisation sur la version 1 ne trouve pas de membre de données correspondant pour le champ `HorsePower` et ignore ces données.  
  
 En outre, le point de terminaison version 1 peut envoyer des données au point de terminaison version 2. La sérialisation de la version 1 du contrat de données `Car` génère du XML semblable au code suivant.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Le désérialiseur version 2 ne sait pas quelle valeur affecter au champ `HorsePower`, car il n'y a pas de données correspondantes dans le XML entrant. À la place, le champ prend la valeur par défaut 0.  
  
## <a name="required-data-members"></a>Membres de données requis  

 Un membre de données peut être marqué comme étant requis en affectant <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> à la propriété <xref:System.Runtime.Serialization.DataMemberAttribute> de `true`. Si des données requises sont manquantes lors de la désérialisation, une exception est levée au lieu que le membre de données soit défini à sa valeur par défaut.  
  
 L'ajout d'un membre de données requis est une modification avec rupture. En d'autres termes, le type le plus récent peut toujours être envoyé aux points de terminaison avec le type le plus ancien, mais pas l'inverse. La suppression d'un membre de données marqué comme étant requis dans les versions antérieures est également une modification avec rupture.  
  
 La modification de la valeur de la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> de `true` en `false` est sans rupture, mais sa modification de `false` en `true` peut être avec rupture si les versions antérieures du type n'ont pas le membre de données en question.  
  
> [!NOTE]
> Même si la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> a la valeur `true`, les données entrantes peuvent être null ou zéro, et un type doit être préparé à gérer cette éventualité. N'utilisez pas <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> comme mécanisme de sécurité pour vous protéger contre les données entrantes incorrectes.  
  
## <a name="omitted-default-values"></a>Valeurs par défaut omises  

 Il est possible (bien que cela ne soit pas recommandé) d’affecter la valeur `EmitDefaultValue` à la propriété de l’attribut DataMemberAttribute `false` , comme décrit dans [valeurs par défaut des données membres](data-member-default-values.md). Si ce paramètre est `false`, le membre de données ne sera pas émis s'il est défini à sa valeur par défaut (généralement null ou zéro). Cela n'est pas compatible avec les membres de données requis dans les différentes versions à deux niveaux :  
  
- Un contrat de données avec un membre de données requis dans une version ne peut pas recevoir de données par défaut (null ou zéro) d'une autre version dans laquelle le membre de données a `EmitDefaultValue` à la valeur `false`.  
  
- Un membre de données requis qui a `EmitDefaultValue` à la valeur `false` ne peut pas être utilisé pour sérialiser sa valeur par défaut (null ou zéro), mais peut recevoir une valeur de ce type lors de la désérialisation. Cela crée un problème d'aller-retour (les données peuvent être lues mais ne peuvent pas être ensuite écrites). Par conséquent, si `IsRequired` a la valeur `true` et `EmitDefaultValue` a la valeur `false` dans une version, la même combinaison doit s'appliquer à toutes les autres versions de sorte qu'aucune version du contrat de données ne puisse générer de valeur qui ne se traduise pas par un aller-retour.  
  
## <a name="schema-considerations"></a>Considérations sur le schéma  

 Pour obtenir une explication sur le schéma produit pour les types de contrat de données, consultez [Référence du schéma de contrat de données](data-contract-schema-reference.md).  
  
 Le schéma que WCF génère pour les types de contrat de données n’apporte aucune provision pour le contrôle de version. En d'autres termes, le schéma exporté à partir d'une version spécifique d'un type contient uniquement les membres de données présents dans cette version. L'implémentation de l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> ne modifie pas le schéma pour un type.  
  
 Les membres de données sont par défaut exportés dans le schéma en tant qu'éléments facultatifs. En d'autres termes, 0 est affecté à la valeur `minOccurs` (attribut XML). Les membres de données requis sont exportés, avec 1 étant affecté à `minOccurs`.  
  
 Un grand nombre des modifications considérées comme étant sans rupture sont en fait avec rupture si une adhésion stricte au schéma est requise. Dans l'exemple précédent, une instance `CarV1` avec l'élément `Model` uniquement validerait par rapport au schéma `CarV2` (lequel a `Model` et `Horsepower`, mais les deux sont facultatifs). Cependant, l'inverse n'est pas vrai : une instance `CarV2` échouerait la validation par rapport au schéma `CarV1`.  
  
 L'aller-retour implique également des considérations supplémentaires. Pour plus d’informations, consultez la section « Considérations relatives au schéma » dans les [contrats de données à compatibilité ascendante](forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Autres modifications autorisées  

 L'implémentation de l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> est une modification sans rupture. Toutefois, la prise en charge de l'aller-retour n'existe pas pour les versions du type antérieures à celle dans laquelle <xref:System.Runtime.Serialization.IExtensibleDataObject> a été implémenté. Pour plus d’informations, consultez [Contrats de données compatibles avec des versions ultérieures](forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Énumérations  

 L'ajout ou la suppression d'un membre d'énumération est une modification avec rupture. La modification du nom d'un membre d'énumération est avec rupture, sauf si son nom de contrat est conservé en utilisant l'attribut `EnumMemberAttribute`. Pour plus d’informations, consultez [types énumération dans les contrats de données](enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Collections  

 La plupart des modifications de collection sont sans rupture car la plupart des types de collections sont interchangeables les uns avec les autres dans le modèle de contrat de données. Toutefois, la personnalisation d'une collection non personnalisée, ou vice versa, est une modification avec rupture. De plus, la modification des paramètres de personnalisation de la collection est une modification avec rupture ; en d'autres termes, la modification de l'espace de noms et du nom de contrat de données, du nom d'élément répétitif, du nom d'élément clé et du nom d'élément de valeur. Pour plus d’informations sur la personnalisation des collections, consultez [types de collections dans les contrats de données](collection-types-in-data-contracts.md).  
Naturellement, la modification du contrat de données de contenu d’une collection (par exemple, la modification d’une liste d’entiers en une liste de chaînes) est une modification avec rupture.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.SerializationException>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- [Rappels de sérialisation avec tolérance de version](version-tolerant-serialization-callbacks.md)
- [Bonnes pratiques : Contrôle de version des contrats de données](../best-practices-data-contract-versioning.md)
- [Utilisation de contrats de données](using-data-contracts.md)
- [Équivalence de contrats de données](data-contract-equivalence.md)
- [Contrats de données à compatibilité ascendante](forward-compatible-data-contracts.md)
