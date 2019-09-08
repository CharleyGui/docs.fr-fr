---
title: Extension de WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, extensibility
- extensibility [WCF]
- Windows Communication Foundation, extensibility
ms.assetid: c145e2f6-f402-41f5-8b5a-eee03978737b
ms.openlocfilehash: 037182a3cb105f544e15a05f955c142ba57f62f3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795540"
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
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Description>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Tokens>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Programmation WCF de base](../basic-wcf-programming.md)  
  
 [Informations détaillées sur les fonctionnalités de WCF](../feature-details/index.md)  
  
 [Conseils et bonnes pratiques](../guidelines-and-best-practices.md)
