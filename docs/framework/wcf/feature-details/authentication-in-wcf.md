---
title: Authentification dans WCF
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: abe7aff025207ad8bdf8657daba3584e6a1b2e7f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964698"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="9b85b-102">Authentification dans WCF</span><span class="sxs-lookup"><span data-stu-id="9b85b-102">Authentication in WCF</span></span>
<span data-ttu-id="9b85b-103">Les rubriques suivantes présentent un certain nombre de mécanismes différents dans Windows Communication Foundation (WCF) qui assurent l’authentification, par exemple l’authentification Windows, les certificats X. 509 et le nom d’utilisateur et les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="9b85b-103">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b85b-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="9b85b-104">In This Section</span></span>  
 [<span data-ttu-id="9b85b-105">Guide pratique pour utiliser le fournisseur d’appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9b85b-105">How to: Use the ASP.NET Membership Provider</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="9b85b-106">Les fonctionnalités ASP.NET incluent une appartenance et un fournisseur de rôles, une base de données pour stocker des paires nom d’utilisateur/mot de passe pour l’authentification et des rôles d’utilisateur pour l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="9b85b-106">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="9b85b-107">Cette rubrique explique comment les services WCF peuvent utiliser la même base de données pour authentifier et autoriser des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="9b85b-107">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="9b85b-108">Guide pratique pour utiliser un validateur de nom d’utilisateur et de mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="9b85b-108">How to: Use a Custom User Name and Password Validator</span></span>](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="9b85b-109">Montre comment intégrer un validateur personnalisé de nom d'utilisateur/mot de passe.</span><span class="sxs-lookup"><span data-stu-id="9b85b-109">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="9b85b-110">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="9b85b-110">Service Identity and Authentication</span></span>](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 <span data-ttu-id="9b85b-111">En guise de protection supplémentaire, un client peut authentifier le service en spécifiant l' *identité* attendue du service.</span><span class="sxs-lookup"><span data-stu-id="9b85b-111">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="9b85b-112">Si l'identité attendue et l'identité retournée par le service ne correspondent pas, l'authentification échoue.</span><span class="sxs-lookup"><span data-stu-id="9b85b-112">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="9b85b-113">Négociation et délais de sécurité</span><span class="sxs-lookup"><span data-stu-id="9b85b-113">Security Negotiation and Timeouts</span></span>](../../../../docs/framework/wcf/feature-details/security-negotiation-and-timeouts.md)  
 <span data-ttu-id="9b85b-114">Décrit comment utiliser la propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> de la classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.</span><span class="sxs-lookup"><span data-stu-id="9b85b-114">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="9b85b-115">Débogage d’erreurs d’authentification Windows</span><span class="sxs-lookup"><span data-stu-id="9b85b-115">Debugging Windows Authentication Errors</span></span>](../../../../docs/framework/wcf/feature-details/debugging-windows-authentication-errors.md)  
 <span data-ttu-id="9b85b-116">Traite des problèmes courants rencontrés lors de l'utilisation de l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="9b85b-116">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9b85b-117">Reference</span><span class="sxs-lookup"><span data-stu-id="9b85b-117">Reference</span></span>  
 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="9b85b-118">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="9b85b-118">Related Sections</span></span>  
 [<span data-ttu-id="9b85b-119">Scénarios de sécurité courants</span><span class="sxs-lookup"><span data-stu-id="9b85b-119">Common Security Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="9b85b-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9b85b-120">See also</span></span>

- [<span data-ttu-id="9b85b-121">Vue d’ensemble de la sécurité</span><span class="sxs-lookup"><span data-stu-id="9b85b-121">Security Overview</span></span>](../../../../docs/framework/wcf/feature-details/security-overview.md)
- <span data-ttu-id="9b85b-122">[Modèle de sécurité pour Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9b85b-122">[Security Model for Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
