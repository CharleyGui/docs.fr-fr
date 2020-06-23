---
title: Utilisation de contrats de données
description: En savoir plus sur un contrat de données, qui définit, pour chaque paramètre ou type de retour, les données qui sont sérialisées pour être échangées entre un client et un serveur WCF.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataContractAttribute class
- WCF, data
- data contracts [WCF]
ms.assetid: a3ae7b21-c15c-4c05-abd8-f483bcbf31af
ms.openlocfilehash: 80ea2a8bd67c627fbe11ee07e640704c1a41ef7b
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244723"
---
# <a name="using-data-contracts"></a>Utilisation de contrats de données
Un *contrat de données* est un accord en bonne et due forme entre un service et un client qui décrit de manière abstraite les données à échanger. Autrement dit, pour communiquer, le client et le service n'ont pas besoin de partager les mêmes types, mais uniquement les mêmes contrats de données. Un contrat de données définit précisément, pour chaque type de paramètre ou de retour, les données qui doivent être sérialisées (converties en données XML) pour être échangées.  
  
## <a name="data-contract-basics"></a>Principes de base des contrats de données  
 Windows Communication Foundation (WCF) utilise un moteur de sérialisation appelé sérialiseur de contrat de données par défaut pour sérialiser et désérialiser des données (les convertir vers et à partir de XML). Tous les .NET Framework types primitifs, tels que les entiers et les chaînes, ainsi que certains types traités comme des primitives, tels que <xref:System.DateTime> et <xref:System.Xml.XmlElement> , peuvent être sérialisés sans autre préparation et sont considérés comme ayant des contrats de données par défaut. De nombreux types de .NET Framework ont également des contrats de données existants. Pour obtenir la liste complète des types sérialisables, consultez [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).  
  
 Vous devez définir un contrat de données pour les nouveaux types complexes que vous créez afin que ces derniers soient sérialisables. Par défaut, le <xref:System.Runtime.Serialization.DataContractSerializer> déduit le contrat de données et sérialise tous les types visibles publiquement. Toutes les propriétés et tous les champs publics en lecture/écriture du type sont sérialisés. Vous pouvez supprimer des membres de la sérialisation en utilisant <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>. Vous pouvez également créer explicitement un contrat de données à l'aide des attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> . Pour cela, il faut normalement appliquer l'attribut <xref:System.Runtime.Serialization.DataContractAttribute> au type. Cet attribut peut être appliqué à des classes, des structures et des énumérations. Puis, l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> doit être appliqué à chaque membre du type de contrat de données pour indiquer qu'il s'agit d'un *membre de données*, c'est-à-dire qu'il doit être sérialisé. Pour plus d’informations, consultez [types sérialisables](serializable-types.md).  
  
### <a name="example"></a>Exemple  
 L'exemple suivant présente un contrat de service (une interface) auquel les attributs <xref:System.ServiceModel.ServiceContractAttribute> et <xref:System.ServiceModel.OperationContractAttribute> ont été explicitement appliqués. L'exemple montre que les types primitifs ne requièrent pas de contrat de données, contrairement au type complexe.  
  
 [!code-csharp[C_DataContract#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#1)]
 [!code-vb[C_DataContract#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#1)]  
  
 L'exemple suivant montre comment créer un contrat de données pour le type `MyTypes.PurchaseOrder` en appliquant les attributs <xref:System.Runtime.Serialization.DataContractAttribute> et <xref:System.Runtime.Serialization.DataMemberAttribute> à la classe et à ses membres.  
  
 [!code-csharp[C_DataContract#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#2)]
 [!code-vb[C_DataContract#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#2)]  
  
### <a name="notes"></a>Notes  
 Les remarques suivantes fournissent des éléments à prendre en compte lors de la création de contrats de données :  
  
- L'attribut <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> est honoré uniquement lorsqu'il est utilisé avec des types non marqués. Cela inclut les types qui ne sont pas marqués avec l'un des attributs <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.SerializableAttribute>, <xref:System.Runtime.Serialization.CollectionDataContractAttribute>ou <xref:System.Runtime.Serialization.EnumMemberAttribute> , ou qui sont marqués comme sérialisables par tout autre moyen (par exemple, objet <xref:System.Xml.Serialization.IXmlSerializable>).  
  
- Vous pouvez appliquer l'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> à des champs et à des propriétés.  
  
- Les niveaux d'accessibilité des membres (interne, privé, protégé ou public) n'affectent en aucune façon le contrat de données.  
  
- L'attribut <xref:System.Runtime.Serialization.DataMemberAttribute> est ignoré s'il est appliqué à des membres statiques.  
  
- Pendant la sérialisation, le code de propriété get est appelé pour que les membres de données de propriété obtiennent la valeur des propriétés à sérialiser.  
  
- Pendant la désérialisation, un objet non initialisé est d'abord créé, sans appeler de constructeur sur le type. Puis, tous les membres de données sont désérialisés.  
  
- Pendant la désérialisation, le code de propriété set est appelé pour que les membres de données de propriété attribuent aux propriétés la valeur désérialisée.  
  
- Pour qu'un contrat de données soit valide, il doit être possible de sérialiser tous ses membres de données. Pour obtenir la liste complète des types sérialisables, consultez [Types Supported by the Data Contract Serializer](types-supported-by-the-data-contract-serializer.md).  
  
     Les types génériques sont gérés exactement de la même façon que les types non génériques. Les paramètres génériques n'ont pas d'exigences particulières. Considérons par exemple le type suivant.  
  
 [!code-csharp[C_DataContract#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#3)]
 [!code-vb[C_DataContract#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#3)]  
  
 Ce type est sérialisable, que le type utilisé pour le paramètre de type générique (`T`) le soit ou non. Comme il doit être possible de sérialiser tous les membres de données, le type suivant est sérialisable uniquement si le paramètre de type générique l'est également, tel qu'indiqué dans le code suivant.  
  
 [!code-csharp[C_DataContract#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontract/cs/source.cs#4)]
 [!code-vb[C_DataContract#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontract/vb/source.vb#4)]  
  
 Pour obtenir un exemple de code complet d’un service WCF qui définit un contrat de données, consultez l’exemple [Basic Data Contract](../samples/basic-data-contract.md) .  
  
## <a name="see-also"></a>Voir aussi

- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- [Types sérialisables](serializable-types.md)
- [Noms de contrats de données](data-contract-names.md)
- [Data Contract Equivalence](data-contract-equivalence.md)
- [Classement des membres de données](data-member-order.md)
- [Types connus de contrats de données](data-contract-known-types.md)
- [Contrats de données à compatibilité ascendante](forward-compatible-data-contracts.md)
- [Contrôle de version des contrats de données](data-contract-versioning.md)
- [Rappels de sérialisation avec tolérance de version](version-tolerant-serialization-callbacks.md)
- [Valeurs par défaut des membres de données](data-member-default-values.md)
- [Types pris en charge par le sérialiseur de contrat de données](types-supported-by-the-data-contract-serializer.md)
- [Guide pratique pour créer un contrat de données de base destiné à une classe ou une structure](how-to-create-a-basic-data-contract-for-a-class-or-structure.md)
