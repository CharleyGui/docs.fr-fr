---
title: Authentification dans WCF
description: En savoir plus sur plusieurs mécanismes de WCF qui assurent l’authentification, tels que l’authentification Windows, les certificats X. 509 et le nom d’utilisateur et le mot de passe.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: 414353b360992abea69d47de9efb22c3c77f4bf6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558275"
---
# <a name="authentication-in-wcf"></a>Authentification dans WCF
Les rubriques suivantes présentent un certain nombre de mécanismes différents dans Windows Communication Foundation (WCF) qui assurent l’authentification, par exemple l’authentification Windows, les certificats X. 509 et le nom d’utilisateur et les mots de passe.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Procédure : utiliser le fournisseur d’appartenances ASP.NET](how-to-use-the-aspnet-membership-provider.md)  
 Les fonctionnalités ASP.NET incluent une appartenance et un fournisseur de rôles, une base de données pour stocker des paires nom d’utilisateur/mot de passe pour l’authentification et des rôles d’utilisateur pour l’autorisation. Cette rubrique explique comment les services WCF peuvent utiliser la même base de données pour authentifier et autoriser des utilisateurs.  
  
 [Procédure : utiliser un validateur de nom d’utilisateur et mot de passe personnalisé](how-to-use-a-custom-user-name-and-password-validator.md)  
 Montre comment intégrer un validateur personnalisé de nom d'utilisateur/mot de passe.  
  
 [Identité du service et authentification](service-identity-and-authentication.md)  
 En guise de protection supplémentaire, un client peut authentifier le service en spécifiant l' *identité* attendue du service. Si l'identité attendue et l'identité retournée par le service ne correspondent pas, l'authentification échoue.  
  
 [Négociation et délais de sécurité](security-negotiation-and-timeouts.md)  
 Décrit comment utiliser la propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> de la classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.  
  
 [Débogage d'erreurs d'authentification Windows](debugging-windows-authentication-errors.md)  
 Traite des problèmes courants rencontrés lors de l'utilisation de l'authentification Windows.  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a>Sections connexes  
 [Scénarios de sécurité courants](common-security-scenarios.md)  
  
## <a name="see-also"></a>Voir aussi

- [Présentation de la sécurité](security-overview.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
