---
title: Autorisation dans WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: c86a07b96b15963af9f078b52bc0d28e9a38187a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90556256"
---
# <a name="authorization-in-wcf"></a>Autorisation dans WCF
L'autorisation est le processus qui consiste à contrôler l'accès et les droits aux ressources, telles que les services ou fichiers. Les rubriques de cette section vous montrent comment effectuer cette tâche de base dans Windows Communication Foundation (WCF) de différentes façons.  
  
## <a name="in-this-section"></a>Dans cette section  
 [Mécanismes de contrôle d'accès](access-control-mechanisms.md)  
 Fournit un bref aperçu des mécanismes d’autorisation dans WCF et les utilisations suggérées.  
  
 [Procédure : restreindre l’accès à la classe PrincipalPermissionAttribute](../how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 Illustre le processus de limitation de l'accès à un service avec le <xref:System.Security.Permissions.PrincipalPermissionAttribute>.  
  
 [Procédure : utiliser le fournisseur de rôle ASP.NET avec un service](how-to-use-the-aspnet-role-provider-with-a-service.md)  
 Parcourt la configuration d’un service pour lui permettre d’utiliser la fonctionnalité de fournisseur de rôle de ASP.NET.  
  
 [Procédure : utiliser le fournisseur de rôle du Gestionnaire d’autorisations ASP.NET avec un service](how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 ASP.NET peut utiliser le gestionnaire d’autorisations pour gérer l’autorisation pour un site Web. WCF peut utiliser de la même façon la combinaison ASP.NET/Authorization Manager pour l’autorisation des clients.  
  
 [Gestion des revendications et autorisation avec le modèle d'identité](managing-claims-and-authorization-with-the-identity-model.md)  
 Explique les principes de base de l'utilisation de l'infrastructure Modèle d'identité pour l'autorisation basée sur les revendications.  
  
 [Délégation et emprunt d’identité](delegation-and-impersonation-with-wcf.md)  
 Explique la différence entre la délégation et l'emprunt d'identité.  
  
## <a name="reference"></a>Informations de référence  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a>Sections connexes  
 [Authentification](authentication-in-wcf.md)  
  
## <a name="see-also"></a>Voir aussi

- [Présentation de la sécurité](security-overview.md)
- [Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))
