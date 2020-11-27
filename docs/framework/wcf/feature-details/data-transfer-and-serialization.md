---
title: Transfert de données et sérialisation
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 490c89f5cfbecd4b2cc0c0e639aa97849132a809
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261980"
---
# <a name="data-transfer-and-serialization"></a>Transfert de données et sérialisation

Dans un système connecté, les services et les clients se reposent sur l'échange de données pour accomplir une tâche. En tant que développeur d’un service ou d’un client, vous devez également comprendre comment Windows Communication Foundation (WCF) gère les données et la sérialisation des données afin de créer des applications efficaces et faciles à gérer.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Spécification du transfert de données dans des contrats de service](specifying-data-transfer-in-service-contracts.md)  
 Décrit les concepts de base du transfert de données dans les services.  
  
 [Utilisation de contrats de données](using-data-contracts.md)  
 Définit les contrats de données et la méthode utilisée pour les créer et les utiliser.  
  
 [Sérialiseur de contrat de données](data-contract-serializer.md)  
 Décrit comment accomplir la sérialisation des données avec la classe <xref:System.Runtime.Serialization.DataContractSerializer> ou une extension de la classe <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 [Utilisation de la classe XmlSerializer](using-the-xmlserializer-class.md)  
 Décrit comment et pourquoi utiliser la classe <xref:System.Xml.Serialization.XmlSerializer>, une alternative à la classe <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 [Utilisation de contrats de message](using-message-contracts.md)  
 Décrit comment les contrats de message autorisent un contrôle pointu sur les messages SOAP.  
  
 [Utilisation de la classe Message](using-the-message-class.md)  
 Décrit comment utiliser les fonctionnalités de la classe Message.  
  
 [Filtrage](filtering.md)  
 Décrit le filtrage qui permet le pré-traitement d'un message selon différents critères.  
  
 [Données volumineuses et diffusion en continu](large-data-and-streaming.md)  
 Décrit comment envoyer un grand bloc de données, tel qu'un fichier binaire.  
  
 [Considérations sur la sécurité des données](security-considerations-for-data.md)  
 Décrit des éléments à connaître lors de la programmation du transfert de données et de la sérialisation.  
  
 [Vue d'ensemble de l'architecture de transfert de données](data-transfer-architectural-overview.md)  
 Décrit une vue de la conception globale du transfert de données dans WCF.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Sections connexes  

 [Extension des encodeurs et des sérialiseurs](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Voir aussi

- [Bonnes pratiques : Contrôle de version des contrats de données](../best-practices-data-contract-versioning.md)
- [Contrôle de version de service](../service-versioning.md)
