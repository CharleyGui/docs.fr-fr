---
title: Intégration à des applications COM
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, COM integration
- COM [WCF], Windows Communication Foundation integration
- WCF, reusing code
- Windows Communication Foundation, reusing code
- COM [WCF]
- WCF, COM integration
ms.assetid: c98bda3e-6779-419e-8e6d-9aa94053026d
ms.openlocfilehash: bc58e22b64284d66367302d55b5c9554c9ec0d72
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268233"
---
# <a name="integrating-with-com-applications"></a>Intégration à des applications COM

Les services Windows Communication Foundation (WCF) peuvent être intégrés directement dans votre code existant à l’aide du moniker de service WCF. Le moniker de service peut être utilisé à partir d'une large gamme d'environnements de développement COM, tels qu'Office VBA, Visual Basic 6.0 ou Visual C++ 6.0.  
  
## <a name="in-this-section"></a>Dans cette section  

 [Vue d'ensemble de l'intégration à des applications COM](integrating-with-com-applications-overview.md)  
 Fournit une vue d'ensemble des principales phases du processus d'intégration.  
  
 [Procédure : inscrire et configurer un moniker de service](how-to-register-and-configure-a-service-moniker.md)  
 Pour utiliser le moniker de service WCF dans une application COM, inscrivez les types attribués requis avec COM et configurez l’application COM et le moniker avec la configuration de liaison requise.  
  
 [Procédure : utiliser le moniker de service Windows Communication Foundation sans inscription](use-the-wcf-service-moniker-without-registration.md)  
 Explique comment obtenir la définition du contrat sous la forme d'un document WSDL (Web Services Definition Language) ou à partir d'un point de terminaison WS-MetadataExchange.  
  
 [Procédure : utiliser un moniker de service avec des contrats WSDL](how-to-use-a-service-moniker-with-wsdl-contracts.md)  
 Décrit comment appeler un exemple WCF à l’aide d’un moniker WSDL WCF.  
  
 [Procédure : utiliser un moniker de service avec des contrats d’échange de métadonnées](how-to-use-a-service-moniker-with-metadata-exchange-contracts.md)  
 Décrit comment appeler un exemple WCF à l’aide d’un moniker WCF qui spécifie un point de terminaison MEX.  
  
 [Procédure : spécifier des informations d’identification de sécurité de canal](how-to-specify-channel-security-credentials.md)  
 Le moniker de service WCF prend en charge l' `IChannelCredentials` interface qui autorise une plage de méthodes alternatives pour spécifier les informations d’identification de canal.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.ServiceModel>  
  
## <a name="see-also"></a>Voir aussi

- [Intégration à des applications COM+](integrating-with-com-plus-applications.md)
