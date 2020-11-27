---
title: Introduction à l'extensibilité
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], extensibility
- Windows Communication Foundation [WCF], extensibility
- extensibility [WCF]
ms.assetid: ef56c251-d63c-4b3f-944f-b0c67bfb0f68
ms.openlocfilehash: 8f4cc490df49a91e448c02fef370ce828536f907
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262721"
---
# <a name="introduction-to-extensibility"></a>Introduction à l'extensibilité

Le modèle d’application Windows Communication Foundation (WCF) est conçu pour résoudre la plus grande partie des exigences de communication de toute application distribuée. Néanmoins, il existe des situations qui ne sont pas prises en charge par le modèle d'application par défaut et les implémentations fournies par le système. Le modèle d’extensibilité WCF est conçu pour prendre en charge des scénarios personnalisés en vous permettant de modifier le comportement du système à tous les niveaux, même au moment de remplacer l’ensemble du modèle d’application. Cette rubrique présente les différentes zones d’extension et fournit des informations détaillées sur chacune d’elles.  
  
## <a name="areas-to-extend"></a>Zones à étendre  

 Vous pouvez étendre les zones suivantes :  
  
- Le runtime de l'application. Cela permet d'étendre la distribution et le traitement des messages pour l'application. Dans ce cadre, vous pouvez également étendre le système de sécurité, le système de métadonnées, le système de sérialisation, ainsi que les liaisons et éléments de liaison qui connectent l'application au système de canaux sous-jacent.  
  
- Le canal et le runtime du canal. Cela permet d'étendre le système qui fonctionne au niveau du message, en fournissant la prise en charge du protocole, du transport et de l'encodage.  
  
- Le runtime de l'hôte. Cela permet d'étendre la relation du domaine de l'application d'hébergement avec le runtime du canal de l'application.  
  
### <a name="extending-the-application-runtime"></a>Extension du runtime de l'application  

 Dans les applications WCF, il existe une distinction entre les messages destinés à un canal et les messages correspondants qui sont destinés à l’application elle-même. Les messages de canaux prennent en charge des fonctionnalités relatives aux canaux, comme l'établissement d'une conversation sécurisée ou d'une session fiable. Ces messages ne sont pas disponibles pour le runtime de l'application. Ils sont traités avant que la couche Application ne soit impliquée.  
  
 Les messages d'application contiennent des données destinées à une opération de client ou de service que vous ou votre client a créée. Ces messages sont disponibles pour le système d'extension de niveau application sous la forme de message ou d'objet, en fonction de vos besoins.  
  
 Tous les messages passent par le système de canaux. Seuls les messages d'application sont passés entre le système de canaux et l'application. Pour créer de nouvelles fonctionnalités de niveau canal, vous devez étendre le système de canaux. Pour créer de nouvelles fonctionnalités de niveau application, vous devez étendre le runtime du service ou du client (respectivement, répartiteurs et fabrications de canaux). Pour plus d’informations sur l’extension du runtime de l’application, consultez [extension de ServiceHost et de la couche de modèle de service](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
#### <a name="extending-security"></a>Extension de la sécurité  

 Pour créer des mécanismes de sécurité personnalisés comme des jetons et des informations d'identification, vous devez étendre le système de sécurité. Pour plus d’informations, consultez extension de la [sécurité](./extending/extending-security.md).  
  
#### <a name="extending-metadata"></a>Extension des métadonnées  

 Pour exposer vos métadonnées différemment de ce qui est prévu par défaut, vous devez étendre le système de métadonnées. Pour plus d’informations, consultez [extension du système de métadonnées](./extending/extending-the-metadata-system.md).  
  
#### <a name="extending-serialization"></a>Extension de la sérialisation  

 Pour créer des encodeurs personnalisés, proposer des substituts de données ou pour tout autre travail impliquant la personnalisation des données transférées, vous devez étendre le système de sérialisation. Pour plus d’informations, consultez [extension des encodeurs et des sérialiseurs](./extending/extending-encoders-and-serializers.md).  
  
#### <a name="extending-bindings"></a>Extension de liaisons  

 Pour associer des canaux de transport ou de protocole à la couche Application, vous devez étendre le système de liaison. Pour plus d’informations, consultez [extension des liaisons](./extending/extending-bindings.md).  
  
### <a name="extending-the-channel-system"></a>Extension du système de canaux  

 Pour créer des canaux qui prennent en charge des transports personnalisés ou des fonctionnalités de protocole, consultez [extension de la couche de canal](./extending/extending-the-channel-layer.md).  
  
### <a name="extending-the-service-hosting-system"></a>Extension du système d'hébergement de service  

 Pour modifier le modèle d'application à l'échelle du service, vous devez étendre la classe <xref:System.ServiceModel.ServiceHostBase?displayProperty=nameWithType>. Pour plus d’informations, consultez [extension de ServiceHost et de la couche de modèle de service](./extending/extending-servicehost-and-the-service-model-layer.md).  
  
 Pour modifier la relation entre le domaine de l'application d'hébergement et l'hôte de service, vous devez étendre la classe <xref:System.ServiceModel.Activation.ServiceHostFactory?displayProperty=nameWithType>. Pour plus d’informations, consultez [extension de l’hébergement à l’aide de ServiceHostFactory](./extending/extending-hosting-using-servicehostfactory.md).  
  
## <a name="see-also"></a>Voir aussi

- [Extension de WCF](./extending/index.md)
