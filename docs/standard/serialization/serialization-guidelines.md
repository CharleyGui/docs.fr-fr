---
title: Indications concernant la sérialisation
description: Ce document fournit des instructions à prendre en compte lors de la conception d’une API à sérialiser, ainsi qu’un résumé des trois principales technologies de sérialisation offertes par .NET.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
ms.openlocfilehash: 6a8fd644e6f9132bf93277ae9928788f236a7bd1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558197"
---
# <a name="serialization-guidelines"></a>Indications concernant la sérialisation
Ce document répertorie les indications à prendre en compte lors de la conception d'une API à sérialiser.  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 .NET offre trois technologies de sérialisation principales qui sont optimisées pour différents scénarios de sérialisation. Le tableau suivant répertorie ces technologies et les principaux types .NET qui leur sont associés.  
  
|Technologie|Classes concernées|Notes|  
|----------------|----------------------|-----------|  
|Sérialisation du contrat de données|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|Persistance générale<br /><br /> Services Web<br /><br /> JSON|  
|Sérialisation XML|<xref:System.Xml.Serialization.XmlSerializer>|Format XML <br />avec contrôle total|  
|Sérialisation du runtime (binaire et SOAP)|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|.NET Remoting|  
  
 Lorsque vous concevez de nouveaux types, vous devez décider laquelle de ces technologies, le cas échéant, doit être prise en charge par ces types. Les indications suivantes expliquent comment effectuer ce choix et fournir cette prise en charge. Elles ne sont pas destinées à vous aider à choisir la technologie de sérialisation que vous devez utiliser dans l'implémentation de votre application ou bibliothèque. Elles ne sont pas non plus directement liées à la conception d'une API et par conséquent, elles ne relèvent pas du propos de cette rubrique.  
  
## <a name="guidelines"></a>Consignes  
  
- PENSEZ à la sérialisation lorsque vous concevez de nouveaux types.  
  
     La sérialisation constitue une considération de conception importante pour tout type, car les programmes devront peut-être rendre persistantes ou transmettre des instances du type.  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a>Choix de la technologie de sérialisation appropriée à prendre en charge  
 Tout type donné peut prendre en charge une ou plusieurs des technologies de sérialisation ou aucune d'entre elles.  
  
- ENVISAGEZ la prise en charge de la *sérialisation du contrat de données* si des instances de votre type doivent être rendues persistantes ou utilisées dans des services web.  
  
- ENVISAGEZ la prise en charge de la *sérialisation XML* à la place ou en plus de la sérialisation du contrat de données si vous devez davantage contrôler le format XML généré lors de la sérialisation du type.  
  
     Cela peut être nécessaire dans certains scénarios d'interopérabilité où vous devez utiliser une construction XML qui n'est pas prise en charge par la sérialisation du contrat de données, par exemple, pour générer des attributs XML.  
  
- ENVISAGEZ la prise en charge de la *sérialisation du runtime* si des instances de votre type doivent passer des limites .NET Remoting.  
  
- ÉVITEZ de prendre en charge la sérialisation XML ou du runtime uniquement pour des raisons de persistance. Préférez plutôt la sérialisation du contrat de données.  
  
#### <a name="supporting-data-contract-serialization"></a>Prise en charge de la sérialisation du contrat de données  
 Les types peuvent prendre en charge la sérialisation du contrat de données en appliquant <xref:System.Runtime.Serialization.DataContractAttribute> au type et <xref:System.Runtime.Serialization.DataMemberAttribute> aux membres (champs et propriétés) du type.  
  
 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]  
  
1. ENVISAGEZ de marquer les données membres de votre type public si le type peut être utilisé en mode de confiance partielle. En mode de confiance totale, les sérialiseurs de contrat de données peuvent sérialiser et désérialiser les types et les membres non publics, mais seuls les membres publics peuvent être sérialisés et désérialisés en mode de confiance partielle.  
  
2. IMPLÉMENTEZ un accesseur Get et Set sur toutes les propriétés pour lesquelles Data-MemberAttribute est défini. Les sérialiseurs de contrat de données nécessitent à la fois l'accesseur Get et Set pour que le type soit considéré comme étant sérialisable. Si le type n'est pas utilisé en mode de confiance partielle, un des accesseurs de propriété, ou les deux, peuvent être non publics.  
  
     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]  
  
3. ENVISAGEZ d'utiliser les rappels de sérialisation pour l'initialisation des instances désérialisées.  
  
     Les constructeurs ne sont pas appelés lorsque les objets sont désérialisés. Par conséquent, toute logique qui s’exécute pendant une construction normale doit être implémentée comme l’un des *rappels de sérialisation*.  
  
     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]  
  
     L'attribut <xref:System.Runtime.Serialization.OnDeserializedAttribute> est l'attribut de rappel le plus communément utilisé. Les autres attributs de la famille sont <xref:System.Runtime.Serialization.OnDeserializingAttribute> , <xref:System.Runtime.Serialization.OnSerializingAttribute> et <xref:System.Runtime.Serialization.OnSerializedAttribute> . Ils peuvent être utilisés pour marquer les rappels exécutés avant la désérialisation, avant la sérialisation et enfin, après la sérialisation, respectivement.  
  
4. ENVISAGEZ d'utiliser <xref:System.Runtime.Serialization.KnownTypeAttribute> pour indiquer les types concrets qui doivent être utilisés lors de la désérialisation d'un graphique d'objet complexe.  
  
     Par exemple, si un type de données membres désérialisées est représenté par une classe abstraite, le sérialiseur a besoin des informations sur le *type connu* pour décider quel type concret doit être instancié et assigné au membre. Si le type connu n'est pas spécifié à l'aide de l'attribut, il devra être passé au sérialiseur explicitement (par exemple, en passant des types connus au constructeur du sérialiseur) ou être spécifié dans le fichier de configuration.  
  
     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]  
  
     Dans les cas où la liste de types connus n’est pas connue de façon statique (lorsque la classe **Person** est compilée), **KnownTypeAttribute** peut également pointer vers une méthode qui retourne une liste de types connus au moment de l’exécution.  
  
5. TENEZ COMPTE de la compatibilité ascendante et descendante lors de la création ou modification de types sérialisables.  
  
     Gardez à l'esprit que les flux sérialisés de futures versions de votre type peuvent être désérialisés dans la version actuelle du type, et inversement. Assurez-vous que vous avez bien assimilé que les données membres, même privées et internes, ne peuvent pas modifier leurs nom, type ou ordre dans les futures versions du type, sauf si vous veillez à conserver le contrat à l'aide de paramètres explicites dans les attributs du contrat de données. Testez la compatibilité de la sérialisation lorsque vous apportez des modifications aux types sérialisables. Essayez de désérialiser la nouvelle version dans une ancienne version, et inversement.  
  
6. ENVISAGEZ d'implémenter l'interface <xref:System.Runtime.Serialization.IExtensibleDataObject> pour permettre l'aller-retour entre les différentes versions du type.  
  
     L'interface permet au sérialiseur de garantir qu'aucune donnée n'est perdue lors de l'aller-retour. La propriété <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> stocke les données de la future version du type qui est inconnu de la version actuelle. Quand la version actuelle est par la suite sérialisée et désérialisée dans une version ultérieure, les données supplémentaires sont disponibles dans le flux sérialisé via la valeur de la propriété **ExtensionData**.  
  
     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]  
  
     Pour plus d’informations, consultez [Contrats de données compatibles avec des versions ultérieures](../../framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
#### <a name="supporting-xml-serialization"></a>Prise en charge de la sérialisation XML  
 La sérialisation du contrat de données est la principale technologie de sérialisation (par défaut) dans le .NET Framework. Il existe cependant des scénarios de sérialisation qui ne sont pas pris en charge par cette technologie. Par exemple, vous n'avez pas le contrôle total sur la forme du XML généré ou consommé par le sérialiseur. Si ce contrôle renforcé est nécessaire, vous devez utiliser la *sérialisation XML*, et concevoir vos types pour prendre en charge cette technologie de sérialisation.  
  
1. ÉVITEZ de concevoir vos types spécifiquement pour la sérialisation XML, sauf si vous avez une bonne raison de contrôler la forme du XML généré. Cette technologie de sérialisation a été remplacée par la sérialisation du contrat de données présentée dans la section précédente.  
  
     En d'autres termes, n'appliquez pas d'attributs de l'espace de noms <xref:System.Xml.Serialization> aux nouveaux types, sauf si vous savez que le type doit être utilisé avec la sérialisation XML. L’exemple suivant montre comment utiliser **System.Xml.Serialization** pour contrôler la forme du XML généré.  
  
     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]  
  
2. ENVISAGEZ d'utiliser l'interface <xref:System.Xml.Serialization.IXmlSerializable> si vous souhaitez davantage de contrôle sur la forme du XML sérialisé que celui proposé en appliquant les attributs de sérialisation XML. Deux méthodes de l’interface, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> et <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> , vous permettent de contrôler entièrement le flux XML sérialisé. Vous pouvez aussi contrôler le schéma XML qui est généré pour le type en appliquant l'attribut <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>.  
  
#### <a name="supporting-runtime-serialization"></a>Prise en charge de la sérialisation du runtime  
 La technologie de *sérialisation du runtime* est utilisée par .NET Remoting. Si vous pensez que vos types vont être transportés à l'aide de .NET Remoting, assurez-vous qu'ils prennent en charge la sérialisation du runtime.  
  
 La prise en charge de base de la *sérialisation du runtime* peut être fournie en appliquant l’attribut <xref:System.SerializableAttribute>. Des scénarios plus avancés nécessitent l’implémentation d’un *modèle sérialisable du runtime* simple (implémentez -<xref:System.Runtime.Serialization.ISerializable> et fournissez un constructeur de sérialisation).  
  
1. ENVISAGEZ la prise en charge de la sérialisation du runtime si vos types doivent être utilisés avec .NET Remoting. Par exemple, l’espace de noms <xref:System.AddIn> utilise .NET Remoting et, par conséquent, tous les types échangés entre les compléments **System.AddIn** doivent prendre en charge la sérialisation du runtime.  
  
     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]  
  
2. ENVISAGEZ d’implémenter le *modèle sérialisable du runtime* si vous souhaitez avoir un contrôle total sur le processus de sérialisation. Par exemple, si vous souhaitez transformer des données à mesure qu'elles sont sérialisées ou désérialisées.  
  
     Le modèle est très simple. Il suffit d'implémenter l'interface <xref:System.Runtime.Serialization.ISerializable> et de fournir un constructeur spécial qui est utilisé lorsque l'objet est désérialisé.  
  
     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]  
  
3. SÉCURISEZ le constructeur de sérialisation et fournissez deux paramètres typés et nommés de la même façon que dans l'exemple disponible ici.  
  
     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]  
  
4. IMPLÉMENTEZ explicitement les membres ISerializable.  
  
     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]  
  
5. EFFECTUEZ une demande de liaison pour l’implémentation **ISerializable.GetObjectData**. Cela garantit que seuls le code d'un niveau de confiance totale et le sérialiseur du runtime ont accès au membre.  
  
     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]  
  
## <a name="see-also"></a>Voir aussi

- [Utilisation de contrats de données](../../framework/wcf/feature-details/using-data-contracts.md)
- [Sérialiseur de contrat de données](../../framework/wcf/feature-details/data-contract-serializer.md)
- [Types pris en charge par le sérialiseur de contrat de données](../../framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [Sérialisation binaire](binary-serialization.md)
- [.NET Remoting](/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))
- [Sérialisation XML et SOAP](xml-and-soap-serialization.md)
- [Sécurité et sérialisation](../../framework/misc/security-and-serialization.md)
