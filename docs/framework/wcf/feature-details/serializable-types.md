---
title: Types sérialisables
ms.date: 03/30/2017
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
ms.openlocfilehash: e65fcb93c5c36bb289b825cef58b3adc6f5155f5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586102"
---
# <a name="serializable-types"></a>Types sérialisables
Par défaut, <xref:System.Runtime.Serialization.DataContractSerializer> sérialise tous les types accessibles publiquement. Toutes les propriétés et tous les champs publics en lecture/écriture du type sont sérialisés.  
  
 Vous pouvez modifier le comportement par défaut en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> aux types et membres. Cette fonctionnalité peut être utile dans les situations dans lesquelles vous avez des types qui ne sont pas sous votre contrôle et ne peuvent pas être modifiés pour ajouter des attributs. Le <xref:System.Runtime.Serialization.DataContractSerializer> reconnaît ces types "non marqués".  
  
## <a name="serialization-defaults"></a>Valeurs par défaut de sérialisation  
 Vous pouvez appliquer les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> pour contrôler explicitement ou personnaliser la sérialisation de types et membres. De plus, vous pouvez appliquer ces attributs aux champs privés. Toutefois, même les types qui ne sont pas marqués avec ces attributs sont sérialisés et désérialisés. Les règles et les exceptions suivantes s'appliquent :  
  
- Le <xref:System.Runtime.Serialization.DataContractSerializer> déduit un contrat de données à partir des types sans attributs à l'aide des propriétés par défaut des types créés récemment.  
  
- Tous les champs publics et les propriétés avec les méthodes `get` et `set` publiques sont sérialisées, à moins que vous n'appliquiez l'attribut <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> à ce membre.  
  
- La sémantique de sérialisation est similaire à celle du <xref:System.Xml.Serialization.XmlSerializer>.  
  
- Dans les types non marqués, seuls les types publics avec les constructeurs qui n'ont pas de paramètres sont sérialisés. L'exception à cette règle est l'<xref:System.Runtime.Serialization.ExtensionDataObject> utilisé avec l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject>.  
  
- Les champs en lecture seule, les propriétés sans méthode `get` ou `set` et les propriétés avec des méthodes `set` ou `get` internes ou privées ne sont pas sérialisés. Ces propriétés sont ignorées et aucune exception n'est levée, sauf dans le cas des collections get-only.  
  
- Les attributs <xref:System.Xml.Serialization.XmlSerializer> (tels que  `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, etc.) sont ignorés.  
  
- Si vous n'appliquez pas l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> à un type donné, le sérialiseur ignore tout membre dans ce type auquel l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> est appliqué.  
  
- La propriété <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> est prise en charge dans les types non marqués avec l'attribut <xref:System.Runtime.Serialization.DataContractAttribute>. Cela inclut la prise en charge de l'attribut <xref:System.Runtime.Serialization.KnownTypeAttribute> sur les types non marqués.  
  
- Pour annuler le processus de sérialisation des membres publics, des propriétés ou des champs, appliquez l'attribut <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> à ce membre.  
  
## <a name="inheritance"></a>Héritage  
 Les types non marqués (type sans attribut <xref:System.Runtime.Serialization.DataContractAttribute>) peuvent hériter des types qui ont cet attribut. Toutefois, l'inverse n'est pas permis : les types avec l'attribut ne peuvent pas hériter de types non marqués. Cette règle est appliquée principalement pour garantir la compatibilité descendante avec le code écrit dans les versions antérieures de .NET Framework.  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Types pris en charge par le sérialiseur de contrat de données](types-supported-by-the-data-contract-serializer.md)
