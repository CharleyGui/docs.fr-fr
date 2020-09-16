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
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="c2070-102">Fédération et jetons émis</span><span class="sxs-lookup"><span data-stu-id="c2070-102">Federation and Issued Tokens</span></span>
<span data-ttu-id="c2070-103">Avec Windows Communication Foundation (WCF), vous pouvez créer des clients qui communiquent en toute sécurité avec les services qui implémentent les spécifications WS-Federation et WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="c2070-103">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="c2070-104">Ces spécifications utilisent XML, SOAP et WSDL (Web Services Description Language) pour fournir des mécanismes permettant d'activer l'authentification et l'autorisation sur différents domaines de confiance.</span><span class="sxs-lookup"><span data-stu-id="c2070-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c2070-105">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="c2070-105">In This Section</span></span>  
 [<span data-ttu-id="c2070-106">Fédération</span><span class="sxs-lookup"><span data-stu-id="c2070-106">Federation</span></span>](federation.md)  
 <span data-ttu-id="c2070-107">Fournit une vue d'ensemble de la fédération.</span><span class="sxs-lookup"><span data-stu-id="c2070-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="c2070-108">Fédération et confiance</span><span class="sxs-lookup"><span data-stu-id="c2070-108">Federation and Trust</span></span>](federation-and-trust.md)  
 <span data-ttu-id="c2070-109">Répertorie les problèmes de conception dont il convient d'être informé lors de la création de services ou de clients fédérés.</span><span class="sxs-lookup"><span data-stu-id="c2070-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="c2070-110">Procédure : créer un client fédéré</span><span class="sxs-lookup"><span data-stu-id="c2070-110">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)  
 <span data-ttu-id="c2070-111">Décrit les principes de base de la création d’un client fédéré avec WCF.</span><span class="sxs-lookup"><span data-stu-id="c2070-111">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="c2070-112">Procédure : configurer des informations d’identification sur un service de fédération</span><span class="sxs-lookup"><span data-stu-id="c2070-112">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="c2070-113">Décrit les étapes de création d'un service fédéré.</span><span class="sxs-lookup"><span data-stu-id="c2070-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="c2070-114">Procédure : créer un WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c2070-114">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="c2070-115">Décrit comment configurer des clients et des services qui utilisent `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="c2070-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="c2070-116">Procédure : créer un service d’émission de jeton de sécurité</span><span class="sxs-lookup"><span data-stu-id="c2070-116">How to: Create a Security Token Service</span></span>](how-to-create-a-security-token-service.md)  
 <span data-ttu-id="c2070-117">Décrit les étapes de création d'un service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c2070-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="c2070-118">Jetons SAML (Security Assertions Markup Language) et revendications</span><span class="sxs-lookup"><span data-stu-id="c2070-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](saml-tokens-and-claims.md)  
 <span data-ttu-id="c2070-119">Décrit les jetons SAML (Security Assertions Markup Language), qui sont extensibles et vous permettent de créer des types de revendications enrichies.</span><span class="sxs-lookup"><span data-stu-id="c2070-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="c2070-120">Procédure : configurer un émetteur local</span><span class="sxs-lookup"><span data-stu-id="c2070-120">How to: Configure a Local Issuer</span></span>](how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="c2070-121">Décrit comment créer un émetteur local de jetons de sécurité.</span><span class="sxs-lookup"><span data-stu-id="c2070-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="c2070-122">Procédure : désactiver des sessions sécurisées sur un WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="c2070-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="c2070-123">Décrit comment désactiver des sessions sécurisées sur `WSFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="c2070-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="c2070-124">La désactivation de sessions sécurisées est nécessaire lors de la création d'une batterie de serveurs Web qui requiert une session pour chaque client.</span><span class="sxs-lookup"><span data-stu-id="c2070-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c2070-125">Informations de référence</span><span class="sxs-lookup"><span data-stu-id="c2070-125">Reference</span></span>  
 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="c2070-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2070-126">See also</span></span>

- [<span data-ttu-id="c2070-127">Autorisation</span><span class="sxs-lookup"><span data-stu-id="c2070-127">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="c2070-128">Jetons personnalisés</span><span class="sxs-lookup"><span data-stu-id="c2070-128">Custom Tokens</span></span>](../extending/custom-tokens.md)
- <span data-ttu-id="c2070-129">[Modèle de sécurité pour Windows Server AppFabric](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c2070-129">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
