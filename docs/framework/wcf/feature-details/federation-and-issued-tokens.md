---
title: Fédération et jetons émis
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: dffba51c1bf1aaffbed8725aafc96fd747cb31c6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559250"
---
# <a name="federation-and-issued-tokens"></a>Fédération et jetons émis
Avec Windows Communication Foundation (WCF), vous pouvez créer des clients qui communiquent en toute sécurité avec les services qui implémentent les spécifications WS-Federation et WS-Trust. Ces spécifications utilisent XML, SOAP et WSDL (Web Services Description Language) pour fournir des mécanismes permettant d'activer l'authentification et l'autorisation sur différents domaines de confiance.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Fédération](federation.md)  
 Fournit une vue d'ensemble de la fédération.  
  
 [Fédération et confiance](federation-and-trust.md)  
 Répertorie les problèmes de conception dont il convient d'être informé lors de la création de services ou de clients fédérés.  
  
 [Procédure : créer un client fédéré](how-to-create-a-federated-client.md)  
 Décrit les principes de base de la création d’un client fédéré avec WCF.  
  
 [Procédure : configurer des informations d’identification sur un service de fédération](how-to-configure-credentials-on-a-federation-service.md)  
 Décrit les étapes de création d'un service fédéré.  
  
 [Procédure : créer un WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)  
 Décrit comment configurer des clients et des services qui utilisent `WSFederationHttpBinding`.  
  
 [Procédure : créer un service d’émission de jeton de sécurité](how-to-create-a-security-token-service.md)  
 Décrit les étapes de création d'un service d'émission de jeton de sécurité.  
  
 [Jetons SAML (Security Assertions Markup Language) et revendications](saml-tokens-and-claims.md)  
 Décrit les jetons SAML (Security Assertions Markup Language), qui sont extensibles et vous permettent de créer des types de revendications enrichies.  
  
 [Procédure : configurer un émetteur local](how-to-configure-a-local-issuer.md)  
 Décrit comment créer un émetteur local de jetons de sécurité.  
  
 [Procédure : désactiver des sessions sécurisées sur un WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 Décrit comment désactiver des sessions sécurisées sur `WSFederationHttpBinding`. La désactivation de sessions sécurisées est nécessaire lors de la création d'une batterie de serveurs Web qui requiert une session pour chaque client.  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a>Voir aussi

- [Autorisation](authorization-in-wcf.md)
- [Jetons personnalisés](../extending/custom-tokens.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
