---
title: 'Bonnes pratiques : Contrôle de version des contrats de données'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- service contracts
- best practices [WCF], data contract versioning
- Windows Communication Foundation, data contracts
ms.assetid: bf0ab338-4d36-4e12-8002-8ebfdeb346cb
ms.openlocfilehash: d6a1eef949e30a1a6d9a1c5971d33c788cc548b9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96277905"
---
# <a name="best-practices-data-contract-versioning"></a>Bonnes pratiques : Contrôle de version des contrats de données

Cette rubrique répertorie les méthodes conseillées pour créer des contrats de données qui peuvent évoluer facilement avec le temps. Pour plus d’informations sur les contrats de données, consultez les rubriques relatives [à l’utilisation des contrats de données](./feature-details/using-data-contracts.md).  
  
## <a name="note-on-schema-validation"></a>Note sur la validation de schéma  

 Dans la discussion sur le contrôle de version des contrats de données, il est important de noter que le schéma de contrat de données exporté par Windows Communication Foundation (WCF) n’a pas de prise en charge du contrôle de version, à l’exception du fait que les éléments sont marqués comme facultatifs par défaut.  
  
 Cela signifie que même le scénario le plus courant de contrôle de version, tel que l'ajout d'un nouveau membre de données, ne peut pas être implémenté d'une manière transparente par rapport à un schéma donné. Les versions plus récentes d'un contrat de données (avec un nouveau membre de données, par exemple) ne valident pas l'utilisation de l'ancien schéma.  
  
 Toutefois, de nombreux scénarios existent où la stricte conformité de schéma n'est pas nécessaire. De nombreuses plateformes de services Web, notamment les services Web XML et WCF créés à l’aide de ASP.NET, n’effectuent pas de validation de schéma par défaut et tolèrent donc les éléments supplémentaires qui ne sont pas décrits par le schéma. L'utilisation de ces plateformes simplifie l'implémentation d'un grand nombre de scénarios de contrôle de version.  
  
 Par conséquent, il existe deux jeux d'instructions relatives au contrôle de version des contrats de données : un jeu pour les scénarios où la validation stricte de schéma est importante, et un autre jeu pour les scénarios où elle ne l'est pas.  
  
## <a name="versioning-when-schema-validation-is-required"></a>Contrôle de version lorsque la validation de schéma est requise  

 Si la validité stricte de schéma est requise dans toutes les directions (du nouveau vers l'ancien et de l'ancien vers le nouveau), les contrats de données doivent être considérés comme immuables. Si le contrôle de version est requis, un nouveau contrat de données doit être créé, avec un nom ou un espace de noms différent, et la version du contrat de service qui utilise le type de données doit être gérée en conséquence.  
  
 Par exemple, un contrat de service pour le traitement de bon de commande nommé `PoProcessing` avec une opération `PostPurchaseOrder` accepte un paramètre conforme à un contrat de données `PurchaseOrder`. Si le contrat `PurchaseOrder` doit changer, vous devez créer un contrat de données, c'est-à-dire `PurchaseOrder2`, qui inclut les modifications. Vous devez gérer ensuite le contrôle de version au niveau du contrat de service. Par exemple, en créant une opération `PostPurchaseOrder2` qui accepte le paramètre `PurchaseOrder2` ou en créant un contrat de service `PoProcessing2` où l'opération `PostPurchaseOrder` accepte un contrat de données `PurchaseOrder2`.  
  
 Notez que les modifications dans les contrats de données référencés par d'autres contrats de données s'étendent aussi à la couche de modèle de service. Par exemple, dans le scénario précédent, le contrat de données `PurchaseOrder` n'a pas besoin d'être modifié. Cependant, il contient un membre de données d'un contrat de données `Customer`, qui contenait de son côté un membre de données du contrat de données `Address`, qui doit être modifié. Dans ce cas, vous devez créer un contrat de données `Address2` contenant les modifications requises, un contrat de données `Customer2` qui contient le membre de données `Address2`, et un contrat de données `PurchaseOrder2` qui contient un membre de données `Customer2`. Comme dans le cas précédent, la version du contrat de service doit aussi être prise en charge.  
  
 Même si les noms dans ces exemples sont changés (en ajoutant un "2"), il est recommandé de modifier les espaces de noms plutôt que les noms en ajoutant de nouveaux espaces de noms avec un numéro de version ou une date. Par exemple, le contrat de données `http://schemas.contoso.com/2005/05/21/PurchaseOrder` se transformerait en contrat de données `http://schemas.contoso.com/2005/10/14/PurchaseOrder`  
  
 Pour plus d’informations, consultez meilleures pratiques : contrôle de [version du service](service-versioning.md).  
  
 Parfois, il est nécessaire de garantir la conformité stricte de schéma pour les messages envoyés par votre application, sans pouvoir compter sur la conformité stricte des messages entrants. Dans ce cas, il est possible qu'un message entrant contienne des données étrangères. Les valeurs superflues sont stockées et retournées par WCF, ce qui entraîne l’envoi de messages de schéma non valides. Pour éviter ce problème, la fonctionnalité d’aller-retour doit être désactivée. Il existe deux façons d'effectuer cette opération.  
  
- N'implémentez l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> sur aucun de vos types.  
  
- Appliquez un attribut <xref:System.ServiceModel.ServiceBehaviorAttribute> à votre contrat de service en affectant à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> la valeur `true`.  
  
 Pour plus d’informations sur les allers-retours, consultez [contrats de données à compatibilité ascendante](./feature-details/forward-compatible-data-contracts.md).  
  
## <a name="versioning-when-schema-validation-is-not-required"></a>Contrôle de version lorsque la validation de schéma n’est pas requise  

 La conformité stricte de schéma est rarement requise. De nombreuses plateformes tolèrent des éléments supplémentaires non décrits par un schéma. Tant que cela est toléré, l’ensemble complet des fonctionnalités décrites dans gestion des [versions](./feature-details/data-contract-versioning.md) des contrats de données et des [contrats de données à compatibilité ascendante](./feature-details/forward-compatible-data-contracts.md) peut être utilisé. Les instructions suivantes sont recommandées.  
  
 Certaines instructions doivent être suivies à la lettre pour envoyer de nouvelles versions d'un type alors qu'un type antérieur est attendu ou envoyer un type antérieur alors qu'une nouvelle version est attendue. Certaines instructions ne sont pas obligatoires, mais sont répertoriées dans ce contexte parce qu'elles peuvent être concernées à terme par l'évolution du contrôle de version de schéma.  
  
1. Ne tentez pas de gérer les versions des contrats de données selon l'héritage de types. Pour créer des versions ultérieures, modifiez le contrat de données sur un type existant ou créez un nouveau type non apparenté.  
  
2. L'utilisation de l'héritage avec les contrats de données est autorisée, à condition que l'héritage ne soit pas utilisé comme un mécanisme de contrôle des versions et que certaines règles soient observées. Si un type dérive d'un certain type de base, ne le faites pas dériver d'un autre type de base dans une version future (sauf s'il a le même contrat de données). Il y a une exception à cela : vous pouvez insérer un type dans la hiérarchie entre un type de contrat de données et son type de base, mais uniquement s'il ne contient pas de membre de données avec les mêmes noms que d'autres membres dans n'importe quelle version possible des autres types dans la hiérarchie. En général, l'utilisation de membres de données avec les mêmes noms à différents niveaux de la même hiérarchie d'héritage peut causer des problèmes de contrôle de version et doit être évité.  
  
3. Pour la première version d'un contrat de données, implémentez toujours <xref:System.Runtime.Serialization.IExtensibleDataObject> pour permettre l'aller-retour. Pour plus d’informations, consultez [Contrats de données compatibles avec des versions ultérieures](./feature-details/forward-compatible-data-contracts.md). Si vous avez publié une ou plusieurs versions d’un type sans implémenter cette interface, implémentez-la dans la version suivante du type.  
  
4. Dans les versions ultérieures, ne modifiez pas le nom ou l'espace de noms de contrat de données. Si vous modifiez le nom ou l'espace de noms du type qui sous tend le contrat de données, veillez à conserver le nom et l'espace de noms de contrat de données en utilisant les mécanismes appropriés, tels que la propriété <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> du <xref:System.Runtime.Serialization.DataContractAttribute>. Pour plus d’informations sur l’affectation de noms, consultez [noms de contrat de données](./feature-details/data-contract-names.md).  
  
5. Dans les versions ultérieures, ne modifiez pas les noms de membres de données. Si vous modifiez le nom du champ, de la propriété ou de l'événement qui sous-tend le membre de données, utilisez la propriété `Name` du <xref:System.Runtime.Serialization.DataMemberAttribute> pour conserver le nom du membre de données existant.  
  
6. Dans les versions ultérieures, ne modifiez pas le type d'un champ, d'une propriété ou d'un événement qui sous-tend un membre de données de telle sorte que le contrat de données résultant pour ce membre de données s'en trouve modifié. N'oubliez pas que les types d'interface sont équivalents à <xref:System.Object> lorsqu'il s'agit de déterminer le contrat de données attendu.  
  
7. Dans les versions ultérieures, ne modifiez pas l'ordre des membres de données existants en ajustant la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> de l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
8. Dans les versions ultérieures, il est possible d'ajouter des membres de données. Ceux-ci doivent toujours observer les règles suivantes :  
  
    1. La propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> doit toujours conserver sa valeur par défaut de `false`.  
  
    2. Si le membre ne peut pas avoir de valeur par défaut `null` ou zéro, une méthode de rappel doit être fournie à l'aide de <xref:System.Runtime.Serialization.OnDeserializingAttribute> pour fournir une valeur par défaut acceptable au cas où le membre ne serait pas présent dans le flux de données entrant. Pour plus d’informations sur le rappel, consultez [rappels de sérialisation avec tolérance de version](./feature-details/version-tolerant-serialization-callbacks.md).  
  
    3. La <xref:System.Runtime.Serialization.DataMemberAttribute.Order?displayProperty=nameWithType> propriété doit être utilisée pour s’assurer que tous les membres de données récemment ajoutés apparaissent après les membres de données existants. Pour cela, la méthode recommandée consiste à ne pas définir la propriété `Order` des membres de données dans la première version du contrat de données. La propriété `Order` de tous les membres de données ajoutés à la version 2 du contrat de données doit avoir la valeur 2. La propriété `Order` de tous les membres de données ajoutés à la version 3 du contrat de données doit avoir la valeur 3, etc. Il est possible que plusieurs membres de données aient le même numéro d'`Order`.  
  
9. Ne supprimez pas de membres de données dans les versions ultérieures, même si la propriété <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> conserve sa propriété `false` par défaut dans les versions antérieures.  
  
10. Ne modifiez pas la propriété `IsRequired` sur des membres de données existante d'une version à l'autre.  
  
11. Pour les membres de données obligatoires (où `IsRequired` a la valeur `true`), ne modifiez pas la propriété `EmitDefaultValue` d'une version à l'autre.  
  
12. N'essayez pas de créer des hiérarchies de contrôle de version avec des branches. Autrement dit, il doit toujours y avoir un chemin d'accès dans au moins une direction d'une version à l'autre qui utilise uniquement les modifications autorisées par ces instructions.  
  
     Par exemple, si la version 1 d'un contrat de données Person contient uniquement le membre de données Name, vous ne devez pas créer une version 2a du contrat en ajoutant seulement le membre Age, et la version 2b en ajoutant seulement le membre Address. La transition de 2a à 2b impliquerait la suppression du membre Age et l'ajout d'Address ; dans la direction inverse, il faudrait supprimer Address et ajouter Age. La suppression de membres n'est pas autorisée par ces instructions.  
  
13. En règle général, il ne faut pas créer de nouveaux sous-types de types de contrat de données existants dans une nouvelle version de votre application. De même, il ne faut pas créer de nouveaux contrats de données utilisés à la place des membres de données déclarés en tant qu'Object ou comme types d'interface. La création de ces nouvelles classes est autorisée uniquement lorsque vous savez que vous pouvez ajouter les nouveaux types à la liste des types connus de toutes les instances de votre ancienne application. Par exemple, dans la version 1 de votre application, vous pouvez avoir le type de contrat de données LibraryItem avec les sous-types du contrat de données Book et Newspaper. LibraryItem aurait ensuite une liste de types connus qui contient Book et Newspaper. Supposons que vous ajoutez maintenant un type Magazine dans la version 2 qui est un sous-type de LibraryItem. Si vous envoyez une instance Magazine de la version 2 à la version 1, le contrat de données Magazine est introuvable dans la liste de types connus et une exception est levée.  
  
14. Vous ne devez pas ajouter ou supprimer des membres de l'énumération entre des versions. Vous ne devez pas non plus renommer de membres de l'énumération, sauf si vous utilisez la propriété Name sur l'attribut `EnumMemberAttribute` pour conserver les mêmes noms dans le modèle de contrat de données.  
  
15. Les collections sont interchangeables dans le modèle de contrat de données, comme décrit dans [types de collections dans les contrats de données](./feature-details/collection-types-in-data-contracts.md). Cela permet un plus grand degré de souplesse. Toutefois, veillez à ne pas modifier accidentellement un type de collection de manière non interchangeable d'une version à l'autre. Par exemple, ne passez pas d’une collection non personnalisée (autrement dit, sans l’attribut `CollectionDataContractAttribute`) à une collection personnalisée ou vice versa. Ne modifiez pas non plus les propriétés sur `CollectionDataContractAttribute` d'une version à l'autre. La seule modification autorisée consiste à ajouter une propriété Name ou Namespace si le nom ou l’espace de noms du type de collection sous-jacent a changé et si vous conservez le même nom et espace de noms de contrat de données que dans une version antérieure.  
  
 Certaines instructions répertoriées dans cette rubrique peuvent être ignorées sans risque si des circonstances particulières s'appliquent. Veillez à bien maîtriser la sérialisation, la désérialisation et les mécanismes de schéma concernés avant de prendre des libertés avec les instructions.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>
- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>
- <xref:System.Runtime.Serialization.IExtensibleDataObject>
- <xref:System.ServiceModel.ServiceBehaviorAttribute>
- <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A>
- <xref:System.Runtime.Serialization.ExtensionDataObject>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- [Utilisation de contrats de données](./feature-details/using-data-contracts.md)
- [Contrôle de version des contrats de données](./feature-details/data-contract-versioning.md)
- [Noms de contrats de données](./feature-details/data-contract-names.md)
- [Contrats de données à compatibilité ascendante](./feature-details/forward-compatible-data-contracts.md)
- [Rappels de sérialisation avec tolérance de version](./feature-details/version-tolerant-serialization-callbacks.md)
