---
title: Schéma de configuration de Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: fddff8428da7efad2823f068e89c6f621283183f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942685"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="1b535-102">Schéma de configuration de Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="1b535-102">Windows Identity Foundation Configuration Schema</span></span>
<span data-ttu-id="1b535-103">Les rubriques de cette section fournissent des informations sur le schéma de configuration de Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="1b535-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="1b535-104">Vous pouvez également configurer une application pour utiliser WIF via des classes exposées par l’infrastructure.</span><span class="sxs-lookup"><span data-stu-id="1b535-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="1b535-105">Ces classes sont indiquées dans les sections qui traitent les éléments correspondants dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="1b535-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="1b535-106">L’exemple suivant montre la structure de la balise XML de base exposée par le schéma de configuration WIF.</span><span class="sxs-lookup"><span data-stu-id="1b535-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="1b535-107">Les attributs sont omis.</span><span class="sxs-lookup"><span data-stu-id="1b535-107">Attributes are omitted.</span></span> <span data-ttu-id="1b535-108">Les commentaires surlignés indiquent les principaux composants du schéma.</span><span class="sxs-lookup"><span data-stu-id="1b535-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<system.identityModel>  
    <!-- Service Configuration -->  
    <identityConfiguration>  
        <caches>  
            <sessionSecurityTokenCache />  
            <tokenReplayCache />  
        </caches>  
  
        <certificateValidation>  
            <certificateValidator />   
        </certificateValidation>  
  
        <claimsAuthenticationManager />  
  
        <claimsAuthorizationManager>  
            <optionalConfigurationElement>  
        </claimsAuthorizationManager>  
  
        <claimTypeRequired>  
            <claimType />   
        </claimTypeRequired>  
  
        <tokenReplayDetection />  
  
        <!-- Security Token Handler Collection Configuration -->  
        <securityTokenHandlers>  
            <add>  
                <!-- Can take an optional configuration element which can be one of  
                     the following or a custom element -->  
                <samlSecurityTokenHandlerRequirement>  
                    <nameClaimType>  
                    <roleClaimType>   
                </samlSecurityTokenHandlerRequirement>  
  
                <sessionSecurityTokenHandlerRequirement />  
                <x509SecurityTokenHandlerRequirement />  
                <userNameSecurityTokenHandlerRequirement />  
            </add>  
            <clear />  
            <remove />  
            <securityTokenHandlerConfiguration>  
                <audienceUris>  
                    <add>  
                    <clear>  
                    <remove>  
                </audienceUris>  
  
                <caches>  
                    <sessionSecurityTokenCache />  
                    <tokenReplayCache />  
                </caches>  
  
                <certificateValidation>  
                    <certificateValidator>   
                </certificateValidation>  
  
                <issuerNameRegistry>  
                    <!-- Can take an optional configuration element which can be   
                         the <trustedIssuers> element to configure a configuration-based  
                         issuer name registry or can be a custom element -->  
                    <trustedIssuers>  
                        <add>  
                        <clear>  
                        <remove>  
                    </trustedIssuers>  
                </issuerNameRegistry>  
  
                <issuerTokenResolver />  
                <serviceTokenResolver />  
                <tokenReplayDetection />  
            </securityTokenHandlerConfiguration>  
        </securityTokenHandlers>  
    </identityConfiguration>  
</system.identityModel>  
  
<system.identityModel.services>  
    <!-- Federation Authentication Configuration -->  
    <federatedAuthentication>  
        <cookieHandler>  
            <chunkedCookieHandler />  
            <customCookieHandler />  
        </cookieHandler>  
  
        <serviceCertificate>  
            <certificateReference>  
        </serviceCertificate>  
  
        <wsFederation />  
    </federatedAuthentication>  
</system.identityModel.services>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="1b535-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="1b535-109">In This Section</span></span>  
 <span data-ttu-id="1b535-110">[\<system.identityModel>](system-identitymodel.md) Fournit la configuration permettant d’activer des options WIF dans les applications.</span><span class="sxs-lookup"><span data-stu-id="1b535-110">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
 <span data-ttu-id="1b535-111">[\<system.identityModel.services>](system-identitymodel-services.md) Fournit la configuration de la fédération passive à l’aide de WIF.</span><span class="sxs-lookup"><span data-stu-id="1b535-111">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="1b535-112">Configure le module d’authentification de session (SAM) et le module d’authentification fédérée (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="1b535-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
