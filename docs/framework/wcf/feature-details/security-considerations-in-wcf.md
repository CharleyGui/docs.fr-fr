---
title: Considérations relatives à la sécurité dans WCF
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF]
- Windows Communication Foundation, security
- WCF, security
ms.assetid: 42055ee0-6d0c-443d-9d89-788dfc345d6d
ms.openlocfilehash: 796098258601ec5fa208fd8a8060b28c3eeeb4d6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96276020"
---
# <a name="security-considerations-in-wcf"></a>Considérations relatives à la sécurité dans WCF

Les rubriques de cette section répertorient les différents éléments liés à la sécurité à prendre en compte lors de la conception d’une application Windows Communication Foundation (WCF).  
  
## <a name="in-this-section"></a>Dans cette section  

 [Divulgation d’informations](information-disclosure.md)  
 Traite des diverses manières dont les informations peuvent être divulguées ou attaquées, et de la manière de limiter ce risque.  
  
 [Élévation de privilège](elevation-of-privilege.md)  
 Traite des conséquences de l'attribution à un intrus d'autorisations plus étendues celles accordées initialement, et de la manière de limiter ce risque.  
  
 [Déni de service](denial-of-service.md)  
 Traite de ce qui arrive lorsqu'un système ne peut pas traiter des messages convenablement, et de la manière de limiter ce risque.  
  
 [Falsification](tampering.md)  
 Traite de la modification des messages ou de la remise des messages, et de la manière de limiter ce risque.  
  
 [Attaques par relecture](replay-attacks.md)  
 Traite de ce qui arrive lorsqu'un intrus copie un flux de messages entre deux correspondants et relit le flux à l'un des correspondants ou les deux, et de la manière de limiter ce risque.  
  
 [Considérations sur la sécurité pour les sessions sécurisées](security-considerations-for-secure-sessions.md)  
 Traite des éléments suivants qui affectent la sécurité lors de l'implémentation de sessions sécurisées.  
  
 [Scénarios non pris en charge](unsupported-scenarios.md)  
 Répertorie différents scénarios qui ne prennent pas en charge un aspect particulier de la sécurité et qui doivent être évités ou pris en compte.  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sections connexes  

 [Aide sur la sécurité et meilleures pratiques](security-guidance-and-best-practices.md)  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité](security.md)
