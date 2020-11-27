---
title: Considérations sur la sécurité pour les sessions sécurisées
ms.date: 03/30/2017
ms.assetid: 0d5be591-9a7b-4a6f-a906-95d3abafe8db
ms.openlocfilehash: abfbb565e06059e05eda3900ba9b8769e3657af8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276033"
---
# <a name="security-considerations-for-secure-sessions"></a>Considérations sur la sécurité pour les sessions sécurisées

Vous devez tenir compte des éléments suivants qui affectent la sécurité lors de l'implémentation de sessions sécurisées. Pour plus d’informations sur les considérations relatives à la sécurité, consultez Considérations sur la [sécurité](security-considerations-in-wcf.md) et [meilleures pratiques pour la sécurité](best-practices-for-security-in-wcf.md).  
  
## <a name="secure-sessions-and-metadata"></a>Sessions sécurisées et métadonnées  

 Lorsqu’une session sécurisée est établie et que la <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> propriété a la valeur `false` , Windows Communication Foundation (WCF) envoie une `mssp:MustNotSendCancel` assertion dans le cadre des métadonnées du document Web Services Description Language (WSDL) pour le point de terminaison de service. L'assertion `mssp:MustNotSendCancel` informe les clients que le service ne répond pas aux demandes d'annulation de session sécurisée. Lorsque la <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.RequireCancellation%2A> propriété a la valeur `true` , WCF n’émet pas d' `mssp:MustNotSendCancel` assertion dans le document WSDL. Lorsqu'ils n'ont plus besoin de la session sécurisée, les clients doivent envoyer une demande d'annulation au service. Lorsqu’un client est généré à l’aide de l' [outil ServiceModel Metadata Utility (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md), le code client réagit correctement à la présence ou l’absence de l' `mssp:MustNotSendCancel` assertion.  
  
## <a name="secure-conversations-and-custom-tokens"></a>Conversations sécurisées et jetons personnalisés  

 Le mélange de jetons personnalisés et de clés dérivées pose quelques problèmes en raison de la manière dont il est défini dans la spécification WS-SecureConversation. La spécification indique que `wsse:SecurityTokenReference` est un élément facultatif qui référence le jeton dérivé : « `/wsc:DerivedKeyToken/wsse:SecurityTokenReference` cet élément facultatif est utilisé pour spécifier le jeton de contexte de sécurité, le jeton de sécurité ou la clé partagée/secret utilisé pour la dérivation. Si cet élément n'est pas spécifié, il est supposé que le destinataire peut déterminer la clé partagée à partir du contexte de message. Si le contexte ne peut pas être déterminé, une erreur telle que `wsc:UnknownDerivationSource` doit être déclenchée.»  
  
 Cela signifie que si vous souhaitez qu'un jeton personnalisé soit dérivé, vous devez encapsuler son type de clause dans un élément `SecurityTokenReference`. Il est possible de désactiver la dérivation mais la valeur par défaut consiste à dériver les clés. Si vous ne parvenez pas à encapsuler la clé, la sérialisation du jeton de clé dérivé aboutit, mais la tentative de désérialisation de ce jeton lève une exception.  
  
## <a name="see-also"></a>Voir aussi

- [Procédure : désactiver des sessions sécurisées sur un WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
- [Security Considerations](security-considerations-in-wcf.md)
- [Bonnes pratiques pour la sécurité](best-practices-for-security-in-wcf.md)
