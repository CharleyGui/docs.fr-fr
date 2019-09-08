---
title: Informations d’identification personnalisées et validation d’informations d’identification
ms.date: 03/30/2017
helpviewer_keywords:
- credentials [WCF], custom
- credentials [WCF]
- custom credentials [WCF]
- credential validation [WCF]
- credentials [WCF], validation
ms.assetid: da831bec-e281-4d44-b343-437b5eef688e
ms.openlocfilehash: 1418d4155bc7f2fefc9f3e6caf4d3a264747a667
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795809"
---
# <a name="custom-credential-and-credential-validation"></a>Informations d’identification personnalisées et validation d’informations d’identification
La sécurité dans Windows Communication Foundation (WCF) est basée sur l’échange d’informations d’identification entre les services et les clients. La plupart des besoins en matière de sécurité peuvent être satisfaits à l'aide de types d'informations d'identification communs, tels que Windows (Kerberos), le nom d'utilisateur et les mots de passe et les certificats. Toutefois, si un nouveau type d'informations d'identification est requis, les rubriques de cette section expliquent comment gérer et valider des types nouveaux.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Guide pratique pour Créer un service qui utilise un validateur de certificat personnalisé](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 Explique comment personnaliser la validation WCF en héritant de la <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.  
  
 [Procédure pas à pas : Création d’informations d’identification de client et de service personnalisées](walkthrough-creating-custom-client-and-service-credentials.md)  
 Montre comment étendre les <xref:System.ServiceModel.Description.ClientCredentials> classes et <xref:System.ServiceModel.Description.ServiceCredentials> pour prendre en charge de nouveaux types d’informations d’identification. Il s'agit du premier volet d'une série de rubriques qui permettent de créer des types d'informations d'identification personnalisés.  
  
 [Guide pratique : Créer un fournisseur de jetons de sécurité personnalisé](how-to-create-a-custom-security-token-provider.md)  
 Explique comment créer un fournisseur de jetons de sécurité pour gérer de nouveaux types d'informations d'identification et retourner de nouveaux jetons pour les informations d'authentification. Il s'agit de la deuxième rubrique de la série.  
  
 [Guide pratique pour Créer un authentificateur de jetons de sécurité personnalisé](how-to-create-a-custom-security-token-authenticator.md)  
 Explique comment créer un authentificateur personnalisé pour authentifier un nouveau type d'informations d'identification. Il s'agit de la troisième rubrique de la série.  
  
## <a name="reference"></a>Référence  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a>Rubriques connexes  
 [Authentification](../feature-details/authentication-in-wcf.md)  
  
 [Fédération et jetons émis](../feature-details/federation-and-issued-tokens.md)  
  
 [Autorisation](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a>Voir aussi

- [Sécurité](../feature-details/security.md)
