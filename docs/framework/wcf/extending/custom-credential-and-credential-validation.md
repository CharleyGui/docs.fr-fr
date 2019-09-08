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
# <a name="custom-credential-and-credential-validation"></a><span data-ttu-id="8aef8-102">Informations d’identification personnalisées et validation d’informations d’identification</span><span class="sxs-lookup"><span data-stu-id="8aef8-102">Custom Credential and Credential Validation</span></span>
<span data-ttu-id="8aef8-103">La sécurité dans Windows Communication Foundation (WCF) est basée sur l’échange d’informations d’identification entre les services et les clients.</span><span class="sxs-lookup"><span data-stu-id="8aef8-103">Security in Windows Communication Foundation (WCF) is based on the exchange of credentials between services and clients.</span></span> <span data-ttu-id="8aef8-104">La plupart des besoins en matière de sécurité peuvent être satisfaits à l'aide de types d'informations d'identification communs, tels que Windows (Kerberos), le nom d'utilisateur et les mots de passe et les certificats.</span><span class="sxs-lookup"><span data-stu-id="8aef8-104">Most security scenarios can be satisfied using common credential types, such as Windows (Kerberos), username and passwords, and certificates.</span></span> <span data-ttu-id="8aef8-105">Toutefois, si un nouveau type d'informations d'identification est requis, les rubriques de cette section expliquent comment gérer et valider des types nouveaux.</span><span class="sxs-lookup"><span data-stu-id="8aef8-105">However, if a new type of credential is required, the topics in this section explain how to handle and validate new types.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8aef8-106">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8aef8-106">In This Section</span></span>  
 [<span data-ttu-id="8aef8-107">Guide pratique pour Créer un service qui utilise un validateur de certificat personnalisé</span><span class="sxs-lookup"><span data-stu-id="8aef8-107">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 <span data-ttu-id="8aef8-108">Explique comment personnaliser la validation WCF en héritant de la <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="8aef8-108">Explains how to customize WCF validation by inheriting from the <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span>  
  
 [<span data-ttu-id="8aef8-109">Procédure pas à pas : Création d’informations d’identification de client et de service personnalisées</span><span class="sxs-lookup"><span data-stu-id="8aef8-109">Walkthrough: Creating Custom Client and Service Credentials</span></span>](walkthrough-creating-custom-client-and-service-credentials.md)  
 <span data-ttu-id="8aef8-110">Montre comment étendre les <xref:System.ServiceModel.Description.ClientCredentials> classes et <xref:System.ServiceModel.Description.ServiceCredentials> pour prendre en charge de nouveaux types d’informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="8aef8-110">Demonstrates how to extend the <xref:System.ServiceModel.Description.ClientCredentials> and <xref:System.ServiceModel.Description.ServiceCredentials> classes to accommodate new credential types.</span></span> <span data-ttu-id="8aef8-111">Il s'agit du premier volet d'une série de rubriques qui permettent de créer des types d'informations d'identification personnalisés.</span><span class="sxs-lookup"><span data-stu-id="8aef8-111">This is first in a series of topics that enable creation of custom credential types.</span></span>  
  
 [<span data-ttu-id="8aef8-112">Guide pratique : Créer un fournisseur de jetons de sécurité personnalisé</span><span class="sxs-lookup"><span data-stu-id="8aef8-112">How to: Create a Custom Security Token Provider</span></span>](how-to-create-a-custom-security-token-provider.md)  
 <span data-ttu-id="8aef8-113">Explique comment créer un fournisseur de jetons de sécurité pour gérer de nouveaux types d'informations d'identification et retourner de nouveaux jetons pour les informations d'authentification.</span><span class="sxs-lookup"><span data-stu-id="8aef8-113">Explains how to create a security token provider to handle new credential types and return new tokens for the credential.</span></span> <span data-ttu-id="8aef8-114">Il s'agit de la deuxième rubrique de la série.</span><span class="sxs-lookup"><span data-stu-id="8aef8-114">This is the second topic in the series.</span></span>  
  
 [<span data-ttu-id="8aef8-115">Guide pratique pour Créer un authentificateur de jetons de sécurité personnalisé</span><span class="sxs-lookup"><span data-stu-id="8aef8-115">How to: Create a Custom Security Token Authenticator</span></span>](how-to-create-a-custom-security-token-authenticator.md)  
 <span data-ttu-id="8aef8-116">Explique comment créer un authentificateur personnalisé pour authentifier un nouveau type d'informations d'identification.</span><span class="sxs-lookup"><span data-stu-id="8aef8-116">Explains how to create a custom authenticator to authenticate a new credential type.</span></span> <span data-ttu-id="8aef8-117">Il s'agit de la troisième rubrique de la série.</span><span class="sxs-lookup"><span data-stu-id="8aef8-117">This is the third topic in the series.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8aef8-118">Référence</span><span class="sxs-lookup"><span data-stu-id="8aef8-118">Reference</span></span>  
 <xref:System.ServiceModel.Security>  
  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.IdentityModel.Policy>  
  
 <xref:System.IdentityModel.Tokens>  
  
 <xref:System.IdentityModel.Selectors>  
  
 <xref:System.IdentityModel.Selectors.X509CertificateValidator>  
  
 <xref:System.ServiceModel.Description.ClientCredentials>  
  
 <xref:System.ServiceModel.Description.ServiceCredentials>  
  
## <a name="related-sections"></a><span data-ttu-id="8aef8-119">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="8aef8-119">Related Sections</span></span>  
 [<span data-ttu-id="8aef8-120">Authentification</span><span class="sxs-lookup"><span data-stu-id="8aef8-120">Authentication</span></span>](../feature-details/authentication-in-wcf.md)  
  
 [<span data-ttu-id="8aef8-121">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="8aef8-121">Federation and Issued Tokens</span></span>](../feature-details/federation-and-issued-tokens.md)  
  
 [<span data-ttu-id="8aef8-122">Autorisation</span><span class="sxs-lookup"><span data-stu-id="8aef8-122">Authorization</span></span>](../feature-details/authorization-in-wcf.md)  
  
## <a name="see-also"></a><span data-ttu-id="8aef8-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8aef8-123">See also</span></span>

- [<span data-ttu-id="8aef8-124">Sécurité</span><span class="sxs-lookup"><span data-stu-id="8aef8-124">Security</span></span>](../feature-details/security.md)
