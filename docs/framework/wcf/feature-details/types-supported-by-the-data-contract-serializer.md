---
title: Types pris en charge par le sérialiseur de contrat de données
description: Consultez la liste complète des types pris en charge par le sérialiseur de contrat de données WCF pour la sérialisation et la désérialisation.
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: ef9d2e61ab7121c97bd474bb151fee32907b1dac
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246530"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Types pris en charge par le sérialiseur de contrat de données

Windows Communication Foundation (WCF) utilise <xref:System.Runtime.Serialization.DataContractSerializer> comme moteur de sérialisation par défaut pour convertir des données en XML et pour convertir XML en données. <xref:System.Runtime.Serialization.DataContractSerializer> est conçu pour sérialiser des types de *contrat de données* . Toutefois, il prend en charge de nombreux autres types qui peuvent être considérés comme ayant un contrat de données implicite. Voici une liste complète des types qui peuvent être sérialisés :

- Tous les types visibles publiquement qui ont un constructeur sans paramètre.

- Types de contrats de données. Ce sont les types auxquels l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> a été appliqué. Les nouveaux types personnalisés qui représentent des objets métier doivent normalement être créés en tant que types de contrat de données. Pour plus d’informations, consultez [utilisation de contrats de données](using-data-contracts.md) et de [types sérialisables](serializable-types.md).

- Types collection. Ce sont des types qui représentent des listes de données. Il peut s'agir de tableaux normaux de types, ou de types collection, tels que <xref:System.Collections.ArrayList> et <xref:System.Collections.Generic.Dictionary%602>. L'attribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> peut être utilisé pour personnaliser la sérialisation de ces types, mais n'est pas requis. Pour plus d’informations, consultez [types de collections dans les contrats de données](collection-types-in-data-contracts.md).

- Types énumération. Les énumérations, y compris les énumérations d'indicateur, sont sérialisables. Les types énumération peuvent, de manière facultative, être marqués avec l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> , auquel cas chaque membre participant à la sérialisation, doit être marqué avec l'attribut <xref:System.Runtime.Serialization.EnumMemberAttribute> . Les membres qui ne sont pas marqués ne sont pas sérialisés. Pour plus d’informations, consultez [types énumération dans les contrats de données](enumeration-types-in-data-contracts.md).

- Types primitifs .NET Framework. Les types suivants construits dans le .NET Framework peuvent tous être sérialisés et sont considérés comme des types primitifs : <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>et <xref:System.String>.

- Autres types primitifs. Ces types ne sont pas primitifs dans le .NET Framework mais sont traités comme des types primitifs dans le format XML sérialisé. Ces types sont <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>et les tableaux de <xref:System.Byte>.

  > [!NOTE]
  > Contrairement à d'autres types primitifs, <xref:System.DateTimeOffset> n'est pas un type connu par défaut. Pour plus d’informations, consultez [types connus de contrat de données](data-contract-known-types.md)).

- Types marqués avec l'attribut <xref:System.SerializableAttribute> . De nombreux types inclus dans la bibliothèque de classes de base .NET Framework appartiennent à cette catégorie. <xref:System.Runtime.Serialization.DataContractSerializer> prend totalement en charge ce modèle de programmation de sérialisation, utilisé par .NET Framework Remoting, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>et <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, incluant la prise en charge de l'interface <xref:System.Runtime.Serialization.ISerializable> .

- Types qui représentent des types XML bruts ou des types qui représentent des données relationnelles ADO.NET. <xref:System.Xml.XmlElement> et le tableau des types <xref:System.Xml.XmlNode> sont pris en charge en tant que solution de représentation directe de XML. En outre, les types qui implémentent l'interface <xref:System.Xml.Serialization.IXmlSerializable> sont pris en charge, y compris l'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> connexe et les types <xref:System.Xml.Linq.XDocument> et <xref:System.Xml.Linq.XElement> . Le <xref:System.Data.DataTable> type ADO.net et le <xref:System.Data.DataSet> type (ainsi que ses classes dérivées typées) implémentent tous l' <xref:System.Xml.Serialization.IXmlSerializable> interface et, par conséquent, s’intègrent à cette catégorie. Pour plus d’informations, consultez [types XML et ADO.net dans les contrats de données](xml-and-ado-net-types-in-data-contracts.md).

## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Limitations d'utilisation de certains types en mode de confiance partielle

Voici une liste de limitations qui s'appliquent en cas d'utilisation de certains types dans les scénarios en mode de confiance partielle :

- Pour sérialiser ou désérialiser un type qui implémente <xref:System.Runtime.Serialization.ISerializable> dans un code d'un niveau de confiance partielle utilisant <xref:System.Runtime.Serialization.DataContractSerializer> , les autorisations <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> et <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> sont nécessaires.

- Lors de l’exécution de code WCF en mode de [confiance partielle](partial-trust.md) , la sérialisation et la désérialisation des `readonly` champs (à la fois `public` et `private` ) ne sont pas prises en charge. C'est parce que l'IL généré est incontrôlable et par conséquent requiert des autorisations élevées.

- Le <xref:System.Runtime.Serialization.DataContractSerializer> et le <xref:System.Xml.Serialization.XmlSerializer> sont pris en charge dans un environnement de confiance partielle. Toutefois, l'utilisation du <xref:System.Runtime.Serialization.DataContractSerializer> est soumise aux conditions suivantes :

  - Tous les types `[DataContract]` sérialisables doivent être "public".

  - Tous les champs ou les propriétés `[DataMember]` sérialisables dans un type `[DataContract]` doivent être "public" et en lecture/écriture. La sérialisation et la désérialisation des `readonly` champs ne sont pas prises en charge lors de l’exécution de WCF dans une application de confiance partielle.

  - L'attribut `[Serializable]`/`ISerializable]` n'est pas pris en charge dans un environnement de confiance partielle.

  - Les types connus doivent être spécifiés dans le code ou dans la configuration au niveau de l'ordinateur (`Machine.config`). Les types connus ne peuvent pas être spécifiés dans la configuration au niveau de l'application pour des raisons de sécurité.

- Les types qui implémentent <xref:System.Runtime.Serialization.IObjectReference> lèveront une exception dans un environnement de confiance partielle car la méthode <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> requiert l'autorisation de sécurité `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.

## <a name="additional-notes-on-serialization"></a>Remarques supplémentaires sur la sérialisation

Les règles suivantes s'appliquent également aux types pris en charge par le sérialiseur de contrat de données :

- Les types génériques sont pleinement pris en charge par le sérialiseur de contrat de données.

- Les types valeur Nullable sont entièrement pris en charge par le sérialiseur de contrat de données.

- Les types d'interface sont traités comme <xref:System.Object> ou, dans le cas d'interfaces de la collection, comme types collection.

- À la fois les structures et les classes sont prises en charge.

- <xref:System.Runtime.Serialization.DataContractSerializer>Ne prend pas en charge le modèle de programmation utilisé par les <xref:System.Xml.Serialization.XmlSerializer> services Web et ASP.net. En particulier, il ne prend pas en charge d'attributs comme <xref:System.Xml.Serialization.XmlElementAttribute> et <xref:System.Xml.Serialization.XmlAttributeAttribute>. Pour activer la prise en charge de ce modèle de programmation, WCF doit être basculé pour utiliser à la <xref:System.Xml.Serialization.XmlSerializer> place de <xref:System.Runtime.Serialization.DataContractSerializer> .

- Le type <xref:System.DBNull> est traité d'une façon spéciale. C'est un type singleton et, sur la désérialisation, le désérialiseur respecte la contrainte singleton et pointe toutes les références `DBNull` à l'instance singleton. Parce que `DBNull` est un type sérialisable, il demande l'autorisation <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> .

## <a name="see-also"></a>Voir aussi

- [Types XML et ADO.NET dans les contrats de données](xml-and-ado-net-types-in-data-contracts.md)
- [Using Data Contracts](using-data-contracts.md)
- [Types sérialisables](serializable-types.md)
- [Collection Types in Data Contracts](collection-types-in-data-contracts.md)
- [Enumeration Types in Data Contracts](enumeration-types-in-data-contracts.md)
