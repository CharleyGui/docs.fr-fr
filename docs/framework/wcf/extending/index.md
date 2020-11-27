---
title: Extension de WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: b82dd4fb6a5b41a0160df8680fb1ba65d9a5bd33
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96254595"
---
# <a name="extending-wcf"></a>Extension de WCF

Windows Communication Foundation (WCF) vous permet de modifier et d’étendre les composants d’exécution afin de contrôler et d’étendre précisément les applications basées sur les services. Les rubriques de cette section approfondissent le concept d'architecture d'extensibilité. Pour plus d’informations sur la programmation de base, consultez [programmation WCF de base](../basic-wcf-programming.md).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Extension de ServiceHost et de la couche de modèle de service](extending-servicehost-and-the-service-model-layer.md)  
 La couche du modèle de service est chargée d'extraire des messages entrants des canaux sous-jacents, de les traduire dans des appels de méthode dans le code d'application et de renvoyer les résultats à l'appelant.  Les extensions de modèle de service modifient ou implémentent l'exécution ou les fonctionnalités de comportement et de communication ainsi que des fonctionnalités de répartiteur, des comportements personnalisés, l'interception de messages et de paramètres et d'autres fonctionnalités d'extensibilité.  
  
 [Extension de liaisons](extending-bindings.md)  
 Les liaisons sont des objets qui décrivent les détails de communication requis pour se connecter à un point de terminaison. Les extensions de liaison ou les liaisons personnalisées implémentent les fonctionnalités de communication personnalisées requises pour prendre en charge des fonctionnalités de l’application.  
  
 [Extension de la couche du canal](extending-the-channel-layer.md)  
 La couche du canal repose sous la couche du modèle de service et est chargée de l'échange des messages entre les clients et les services. Les extensions de canal peuvent implémenter des nouvelles fonctionnalités de protocole, telles que la sécurité. Les extensions de canal contiennent aussi des fonctionnalités, telles que l’implémentation d’un nouveau transport réseau pour transporter les messages SOAP.  
  
 [Extension de la sécurité](extending-security.md)  
 La sécurité dans WCF comprend la sécurité de transfert (intégrité, confidentialité et authentification), le contrôle d’accès (autorisation) et l’audit. Les classes trouvées dans l' `IdentityModel` espace de noms sont utilisées par WCF pour le contrôle d’accès. La maîtrise du fonctionnement de l'architecture de sécurité vous permet de créer des types de revendication personnalisée afin d'accommoder des systèmes de contrôle d'accès personnalisés.  
  
 [Extension du système de métadonnées](extending-the-metadata-system.md)  
 Le système de métadonnées WCF est un groupe de classes et d’interfaces qui représentent les métadonnées requises pour implémenter des applications basées sur les services. Modifiez ou étendez les classes ou implémentez et configurez les interfaces pour exporter et importer des métadonnées personnalisées telles que les extensions WSDL (Web Services Description Language) ou des assertions WS-PolicyAttachments personnalisées.  
  
 [Extension des encodeurs et des sérialiseurs](extending-encoders-and-serializers.md)  
 Les encodeurs et les sérialiseurs traduisent les données d'un format à l'autre. Les rubriques de cette section expliquent comment étendre les classes fournies pour satisfaire des exigences particulières.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>Sections connexes  

 [Programmation WCF de base](../basic-wcf-programming.md)  
  
 [Détails des fonctionnalités WCF](../feature-details/index.md)  
  
 [Indications et meilleures pratiques](../guidelines-and-best-practices.md)
