---
title: Schéma de configuration de Windows Identity Foundation
ms.date: 03/30/2017
ms.assetid: 4d4f6d76-49a5-4bad-b345-097b2e2844e9
author: BrucePerlerMS
ms.openlocfilehash: 14d596ae77019932d169e1a84732fb8522bfc46c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152721"
---
# <a name="windows-identity-foundation-configuration-schema"></a><span data-ttu-id="8be2c-102">Schéma de configuration de Windows Identity Foundation</span><span class="sxs-lookup"><span data-stu-id="8be2c-102">Windows Identity Foundation Configuration Schema</span></span>

<span data-ttu-id="8be2c-103">Les rubriques de cette section fournissent des informations sur le schéma de configuration de Windows Identity Foundation (WIF).</span><span class="sxs-lookup"><span data-stu-id="8be2c-103">The topics in this section provide information about the Windows Identity Foundation (WIF) configuration schema.</span></span> <span data-ttu-id="8be2c-104">Vous pouvez également configurer une application pour utiliser WIF à travers des classes exposées par le cadre.</span><span class="sxs-lookup"><span data-stu-id="8be2c-104">You can also configure an application to use WIF through classes exposed by the framework.</span></span> <span data-ttu-id="8be2c-105">Ces classes sont indiquées dans les sections qui traitent les éléments correspondants dans le schéma.</span><span class="sxs-lookup"><span data-stu-id="8be2c-105">These classes are noted in the sections that treat relevant elements in the schema.</span></span> <span data-ttu-id="8be2c-106">L’exemple suivant montre la structure de la balise XML de base exposée par le schéma de configuration WIF.</span><span class="sxs-lookup"><span data-stu-id="8be2c-106">The following shows the basic XML tag structure exposed by the WIF configuration schema.</span></span> <span data-ttu-id="8be2c-107">Les attributs sont omis.</span><span class="sxs-lookup"><span data-stu-id="8be2c-107">Attributes are omitted.</span></span> <span data-ttu-id="8be2c-108">Les commentaires surlignés indiquent les principaux composants du schéma.</span><span class="sxs-lookup"><span data-stu-id="8be2c-108">Highlighted comments indicate major components of the schema.</span></span>  
  
```xml  
<configuration>  
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
</configuration>  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="8be2c-109">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="8be2c-109">In This Section</span></span>  

<span data-ttu-id="8be2c-110">[ \<system.identityModel>](system-identitymodel.md) Fournit une configuration pour activer les options WIF dans les applications.</span><span class="sxs-lookup"><span data-stu-id="8be2c-110">[\<system.identityModel>](system-identitymodel.md) Provides configuration for enabling WIF options in applications.</span></span>  
  
<span data-ttu-id="8be2c-111">[ \<system.identityModel.services>](system-identitymodel-services.md) Fournit la configuration pour la fédération passive utilisant WIF.</span><span class="sxs-lookup"><span data-stu-id="8be2c-111">[\<system.identityModel.services>](system-identitymodel-services.md) Provides configuration for passive federation using WIF.</span></span> <span data-ttu-id="8be2c-112">Configure le module d’authentification de session (SAM) et le module d’authentification fédérée (WSFAM).</span><span class="sxs-lookup"><span data-stu-id="8be2c-112">Configures the Session Authentication Module (SAM) and the Federated Authentication Module (WSFAM).</span></span>
