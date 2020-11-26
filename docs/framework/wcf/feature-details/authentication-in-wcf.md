---
title: Authentification dans WCF
description: En savoir plus sur plusieurs mécanismes de WCF qui assurent l’authentification, tels que l’authentification Windows, les certificats X. 509 et le nom d’utilisateur et le mot de passe.
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [WCF]
- security [WCF], authentication
ms.assetid: 9254d873-843d-4c6e-bea4-8184ac3e44f4
ms.openlocfilehash: e2334a8c024238f38e1c927a278a4e25e7dabd9d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96247536"
---
# <a name="authentication-in-wcf"></a><span data-ttu-id="5f6cd-103">Authentification dans WCF</span><span class="sxs-lookup"><span data-stu-id="5f6cd-103">Authentication in WCF</span></span>

<span data-ttu-id="5f6cd-104">Les rubriques suivantes présentent un certain nombre de mécanismes différents dans Windows Communication Foundation (WCF) qui assurent l’authentification, par exemple l’authentification Windows, les certificats X. 509 et le nom d’utilisateur et les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-104">The following topics show a number of different mechanisms in Windows Communication Foundation (WCF) that provide authentication, for example, Windows authentication, X.509 certificates, and user name and passwords.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f6cd-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="5f6cd-105">In This Section</span></span>  

 [<span data-ttu-id="5f6cd-106">Procédure : utiliser le fournisseur d’appartenances ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5f6cd-106">How to: Use the ASP.NET Membership Provider</span></span>](how-to-use-the-aspnet-membership-provider.md)  
 <span data-ttu-id="5f6cd-107">Les fonctionnalités ASP.NET incluent une appartenance et un fournisseur de rôles, une base de données pour stocker des paires nom d’utilisateur/mot de passe pour l’authentification et des rôles d’utilisateur pour l’autorisation.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-107">ASP.NET features include a membership and role provider, a database to store user name/password pairs for authentication, and user roles for authorization.</span></span> <span data-ttu-id="5f6cd-108">Cette rubrique explique comment les services WCF peuvent utiliser la même base de données pour authentifier et autoriser des utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-108">This topic explains how WCF services can use the same database to authenticate and authorize users.</span></span>  
  
 [<span data-ttu-id="5f6cd-109">Procédure : utiliser un validateur de nom d’utilisateur et mot de passe personnalisé</span><span class="sxs-lookup"><span data-stu-id="5f6cd-109">How to: Use a Custom User Name and Password Validator</span></span>](how-to-use-a-custom-user-name-and-password-validator.md)  
 <span data-ttu-id="5f6cd-110">Montre comment intégrer un validateur personnalisé de nom d'utilisateur/mot de passe.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-110">Demonstrates how to integrate a custom user name/password validator.</span></span>  
  
 [<span data-ttu-id="5f6cd-111">Identité du service et authentification</span><span class="sxs-lookup"><span data-stu-id="5f6cd-111">Service Identity and Authentication</span></span>](service-identity-and-authentication.md)  
 <span data-ttu-id="5f6cd-112">En guise de protection supplémentaire, un client peut authentifier le service en spécifiant l' *identité* attendue du service.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-112">As an extra safeguard, a client can authenticate the service by specifying the expected *identity* of the service.</span></span> <span data-ttu-id="5f6cd-113">Si l'identité attendue et l'identité retournée par le service ne correspondent pas, l'authentification échoue.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-113">If the expected identity and the identity returned by the service do not match, authentication fails.</span></span>  
  
 [<span data-ttu-id="5f6cd-114">Négociation et délais de sécurité</span><span class="sxs-lookup"><span data-stu-id="5f6cd-114">Security Negotiation and Timeouts</span></span>](security-negotiation-and-timeouts.md)  
 <span data-ttu-id="5f6cd-115">Décrit comment utiliser la propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> de la classe <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-115">Describes how to use the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> property in the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class.</span></span>  
  
 [<span data-ttu-id="5f6cd-116">Débogage d'erreurs d'authentification Windows</span><span class="sxs-lookup"><span data-stu-id="5f6cd-116">Debugging Windows Authentication Errors</span></span>](debugging-windows-authentication-errors.md)  
 <span data-ttu-id="5f6cd-117">Traite des problèmes courants rencontrés lors de l'utilisation de l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="5f6cd-117">Focuses on common problems encountered when using Windows authentication.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5f6cd-118">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="5f6cd-118">Reference</span></span>  

 <xref:System.ServiceModel>  
  
## <a name="related-sections"></a><span data-ttu-id="5f6cd-119">Sections connexes</span><span class="sxs-lookup"><span data-stu-id="5f6cd-119">Related Sections</span></span>  

 [<span data-ttu-id="5f6cd-120">Scénarios de sécurité courants</span><span class="sxs-lookup"><span data-stu-id="5f6cd-120">Common Security Scenarios</span></span>](common-security-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="5f6cd-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f6cd-121">See also</span></span>

- [<span data-ttu-id="5f6cd-122">Présentation de la sécurité</span><span class="sxs-lookup"><span data-stu-id="5f6cd-122">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="5f6cd-123">[Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5f6cd-123">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
