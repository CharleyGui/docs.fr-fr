---
title: Transfert de données et sérialisation
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: b07937b0a94c24a934b17d6cf21b726ee0d4362e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593484"
---
# <a name="data-transfer-and-serialization"></a>Transfert de données et sérialisation
Dans un système connecté, les services et les clients se reposent sur l'échange de données pour accomplir une tâche. En tant que développeur d’un service ou d’un client, vous devez également comprendre comment Windows Communication Foundation (WCF) gère les données et la sérialisation des données afin de créer des applications efficaces et faciles à gérer.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md)  
 Décrit les concepts de base du transfert de données dans les services.  
  
 [Using Data Contracts](using-data-contracts.md)  
 Définit les contrats de données et la méthode utilisée pour les créer et les utiliser.  
  
 [Sérialiseur de contrat de données](data-contract-serializer.md)  
 Décrit comment accomplir la sérialisation des données avec la classe <xref:System.Runtime.Serialization.DataContractSerializer> ou une extension de la classe <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
 [Utilisation de la classe XmlSerializer](using-the-xmlserializer-class.md)  
 Décrit comment et pourquoi utiliser la classe <xref:System.Xml.Serialization.XmlSerializer>, une alternative à la classe <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 [Utilisation de contrats de message](using-message-contracts.md)  
 Décrit comment les contrats de message autorisent un contrôle pointu sur les messages SOAP.  
  
 [Utilisation de la classe message](using-the-message-class.md)  
 Décrit comment utiliser les fonctionnalités de la classe Message.  
  
 [Filtrage](filtering.md)  
 Décrit le filtrage qui permet le pré-traitement d'un message selon différents critères.  
  
 [Données volumineuses et diffusion en continu](large-data-and-streaming.md)  
 Décrit comment envoyer un grand bloc de données, tel qu'un fichier binaire.  
  
 [Considérations relatives à la sécurité des données](security-considerations-for-data.md)  
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

- [Meilleures pratiques : contrôle de version des contrats de données](../best-practices-data-contract-versioning.md)
- [Contrôle de version de service](../service-versioning.md)
