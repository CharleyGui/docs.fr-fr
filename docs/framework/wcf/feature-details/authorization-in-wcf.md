---
title: Autorisation dans WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authorization [WCF]
- security [WCF], authorization
ms.assetid: 8ea0b552-af65-45b0-a157-c6c111b8ce5e
ms.openlocfilehash: 0097adc3d9677d9ce5595a3ac632b51d94d53f6f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964682"
---
# <a name="authorization-in-wcf"></a><span data-ttu-id="9e119-102">Autorisation dans WCF</span><span class="sxs-lookup"><span data-stu-id="9e119-102">Authorization in WCF</span></span>
<span data-ttu-id="9e119-103">L'autorisation est le processus qui consiste à contrôler l'accès et les droits aux ressources, telles que les services ou fichiers.</span><span class="sxs-lookup"><span data-stu-id="9e119-103">Authorization is the process of controlling access and rights to resources, such as services or files.</span></span> <span data-ttu-id="9e119-104">Les rubriques de cette section vous montrent comment effectuer cette tâche de base dans Windows Communication Foundation (WCF) de différentes façons.</span><span class="sxs-lookup"><span data-stu-id="9e119-104">The topics in this section show you how to perform this basic task in Windows Communication Foundation (WCF) in a variety of ways.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9e119-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9e119-105">In This Section</span></span>  
 [<span data-ttu-id="9e119-106">Mécanismes de contrôle d’accès</span><span class="sxs-lookup"><span data-stu-id="9e119-106">Access Control Mechanisms</span></span>](../../../../docs/framework/wcf/feature-details/access-control-mechanisms.md)  
 <span data-ttu-id="9e119-107">Fournit un bref aperçu des mécanismes d’autorisation dans WCF et les utilisations suggérées.</span><span class="sxs-lookup"><span data-stu-id="9e119-107">Provides a brief outline of the authorization mechanisms in WCF, and suggested uses.</span></span>  
  
 [<span data-ttu-id="9e119-108">Guide pratique pour restreindre l’accès avec la classe PrincipalPermissionAttribute</span><span class="sxs-lookup"><span data-stu-id="9e119-108">How to: Restrict Access with the PrincipalPermissionAttribute Class</span></span>](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)  
 <span data-ttu-id="9e119-109">Illustre le processus de limitation de l'accès à un service avec le <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9e119-109">Shows the process of restricting access to a service with the <xref:System.Security.Permissions.PrincipalPermissionAttribute>.</span></span>  
  
 [<span data-ttu-id="9e119-110">Guide pratique pour utiliser le fournisseur de rôle ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="9e119-110">How to: Use the ASP.NET Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)  
 <span data-ttu-id="9e119-111">Parcourt la configuration d’un service pour lui permettre d’utiliser la fonctionnalité de fournisseur de rôle de ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9e119-111">Walks through the configuration of a service to enable it to use the role provider feature of ASP.NET.</span></span>  
  
 [<span data-ttu-id="9e119-112">Guide pratique pour utiliser le fournisseur de rôle du Gestionnaire d’autorisations ASP.NET avec un service</span><span class="sxs-lookup"><span data-stu-id="9e119-112">How to: Use the ASP.NET Authorization Manager Role Provider with a Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)  
 <span data-ttu-id="9e119-113">ASP.NET peut utiliser le gestionnaire d’autorisations pour gérer l’autorisation pour un site Web.</span><span class="sxs-lookup"><span data-stu-id="9e119-113">ASP.NET can use the Authorization Manager to manage authorization for a Web site.</span></span> <span data-ttu-id="9e119-114">WCF peut utiliser de la même façon la combinaison ASP.NET/Authorization Manager pour l’autorisation des clients.</span><span class="sxs-lookup"><span data-stu-id="9e119-114">WCF can similarly leverage the ASP.NET/Authorization Manager combination for authorization of clients.</span></span>  
  
 [<span data-ttu-id="9e119-115">Gestion des revendications et autorisation avec le modèle d’identité</span><span class="sxs-lookup"><span data-stu-id="9e119-115">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 <span data-ttu-id="9e119-116">Explique les principes de base de l'utilisation de l'infrastructure Modèle d'identité pour l'autorisation basée sur les revendications.</span><span class="sxs-lookup"><span data-stu-id="9e119-116">Explains the basics of using the Identity Model infrastructure for claims-based authorization.</span></span>  
  
 [<span data-ttu-id="9e119-117">Délégation et emprunt d’identité</span><span class="sxs-lookup"><span data-stu-id="9e119-117">Delegation and Impersonation</span></span>](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)  
 <span data-ttu-id="9e119-118">Explique la différence entre la délégation et l'emprunt d'identité.</span><span class="sxs-lookup"><span data-stu-id="9e119-118">Explains the difference between delegation and impersonation.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9e119-119">Reference</span><span class="sxs-lookup"><span data-stu-id="9e119-119">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.ServiceModel.Description.PrincipalPermissionMode>  
  
 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>  
  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
## <a name="related-sections"></a><span data-ttu-id="9e119-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9e119-120">Related Sections</span></span>  
 [<span data-ttu-id="9e119-121">Authentification</span><span class="sxs-lookup"><span data-stu-id="9e119-121">Authentication</span></span>](../../../../docs/framework/wcf/feature-details/authentication-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="9e119-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9e119-122">See also</span></span>

- [<span data-ttu-id="9e119-123">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="9e119-123">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="9e119-124">[Modèle de sécurité pour Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9e119-124">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
