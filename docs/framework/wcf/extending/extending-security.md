---
title: Extension de la sécurité
ms.date: 03/30/2017
helpviewer_keywords:
- security [WCF], extending
ms.assetid: a015a040-9fdf-4147-9ea9-f83b570be1d4
ms.openlocfilehash: d91f4812dbccb7807be2e0780cccd1d0c38b1f40
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273059"
---
# <a name="extending-security"></a>Extension de la sécurité

Pour prendre en charge de nouveaux types de revendication et des jetons personnalisés, vous pouvez étendre l’infrastructure de sécurité de Windows Communication Foundation (WCF). Les rubriques de cette section vous montrent comment procéder.  
  
## <a name="in-this-section"></a>Dans cette section  
  
 [Informations d’identification personnalisées et validation d’informations d’identification](custom-credential-and-credential-validation.md)  
 Explique comment le modèle d'identité est utilisé lors de la validation d'informations d'identification personnalisées.  
  
 [Jetons personnalisés](custom-tokens.md)  
 Les jetons émis par un service de jeton de sécurité sont en général des jetons SAML. Cette rubrique explique comment créer un type de jeton personnalisé.  
  
 [Autorisation personnalisée](custom-authorization.md)  
 Explique comment implémenter une autorisation personnalisée.  
  
 [Substitution de l'identité d'un service pour l'authentification](overriding-the-identity-of-a-service-for-authentication.md)  
 Décrit comment remplacer l'identité d'un service pour l'authentification.  
  
 [Procédure : créer un vérificateur d’identité du client personnalisé](how-to-create-a-custom-client-identity-verifier.md)  
 Montre comment valider une identité de point de terminaison personnalisée.  
  
 [Procédure : utiliser des certificats X.509 distincts pour les signatures et le chiffrement](how-to-use-separate-x-509-certificates-for-signing-and-encryption.md)  
 Les messages sont généralement signés et chiffrés à l'aide d'un certificat unique. Cette rubrique explique comment deux certificats peuvent être utilisés, s'ils sont requis.  
  
 [Procédure : remplacer le fournisseur de services de chiffrement par la clé privée d’un certificat X.509](change-cryptographic-provider-x509-certificate-private-key.md)  
 Explique comment modifier le fournisseur de services de chiffrement utilisé pour fournir la clé privée d’un certificat X. 509 et comment intégrer le fournisseur dans l’infrastructure Windows Communication Foundation (WCF).  
  
## <a name="reference"></a>Informations de référence  

 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
## <a name="related-sections"></a>Sections connexes  

 [Sécurité](../feature-details/security.md)  
  
 [Programmation WCF de base](../basic-wcf-programming.md)  
  
## <a name="see-also"></a>Voir aussi

- [Présentation de la sécurité](../feature-details/security-overview.md)
