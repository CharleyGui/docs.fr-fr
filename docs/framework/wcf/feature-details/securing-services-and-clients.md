---
title: Sécurisation des services et des clients
ms.date: 03/30/2017
helpviewer_keywords:
- message security [WCF]
ms.assetid: e681f3bd-0c09-4a58-b0e4-0ecbdf1aa6c7
ms.openlocfilehash: 713737b129771967958fddf44e9ef28583d49422
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554076"
---
# <a name="securing-services-and-clients"></a>Sécurisation des services et des clients
Les informations contenues dans cette section se concentrent sur la programmation de la sécurité dans Windows Communication Foundation (WCF). En général, l’opération inclut la sélection d’une liaison appropriée fournie par le système, la définition des propriétés de l’élément de sécurité, puis la définition des propriétés des comportements du service qui déterminent la manière dont les informations d’identification sont récupérées pour être utilisées par le service ou le client. Ces techniques couvrent les exigences de sécurité de la plupart des utilisateurs pour la plupart des scénarios, comme indiqué dans les [scénarios de sécurité courants](common-security-scenarios.md). Si votre scénario nécessite plus de fonctionnalités, commencez [par consulter les fonctionnalités de sécurité avec des liaisons personnalisées](security-capabilities-with-custom-bindings.md). Si une solution n’est pas visible, consultez extension de la [sécurité](../extending/extending-security.md). Si vous créez (ou interopèrez avec) un système qui utilise des revendications enrichies, consultez les rubriques dans [autorisation](authorization-in-wcf.md).  
  
## <a name="in-this-section"></a>Dans cette section  
 [Programmation de la sécurité dans WCF](programming-wcf-security.md)  
 Vue d'ensemble du modèle de programmation utilisé pour sécuriser des messages.  
  
 [Vue d'ensemble de la sécurité des transports](transport-security-overview.md)  
 Vue d'ensemble de la sécurisation des messages par le biais de la couche transport.  
  
 [Sécurité des messages](message-security-in-wcf.md)  
 Résume les raisons de l’utilisation de la sécurité au niveau du message dans Windows Communication Foundation (WCF).  
  
 [Sessions sécurisées](secure-sessions.md)  
 Discussion des points à prendre en compte lors de la sécurisation d’une session WCF.  
  
 [Utilisation des certificats](working-with-certificates.md)  
 Explication de quelques-unes des tâches courantes requises lors de l’utilisation de certificats X.509.  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.ServiceModel>  
  
 <xref:System.ServiceModel.Channels>  
  
 <xref:System.ServiceModel.Security>  
  
## <a name="related-sections"></a>Sections connexes  
 [Concepts de sécurité](security-concepts.md)  
  
 [Extension de la sécurité](../extending/extending-security.md)  
  
 [Scénarios de sécurité courants](common-security-scenarios.md)  
  
 [Liaisons et sécurité](bindings-and-security.md)  
  
 [Fonctionnalités de sécurité avec des liaisons personnalisées](security-capabilities-with-custom-bindings.md)  
  
 [Extension de la sécurité](../extending/extending-security.md)  
  
 [Autorisation](authorization-in-wcf.md)  
  
## <a name="see-also"></a>Voir aussi

- [Programmation WCF de base](../basic-wcf-programming.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
