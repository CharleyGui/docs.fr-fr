---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152502"
---
# \<system.identityModel.services>
<span data-ttu-id="03bee-102">Section de configuration pour l’authentification à l’aide du protocole WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="03bee-102">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.identityModel.services>**  
  
## <a name="syntax"></a><span data-ttu-id="03bee-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03bee-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03bee-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="03bee-104">Attributes and Elements</span></span>  
 <span data-ttu-id="03bee-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="03bee-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03bee-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="03bee-106">Attributes</span></span>  
 <span data-ttu-id="03bee-107">Aucune</span><span class="sxs-lookup"><span data-stu-id="03bee-107">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03bee-108">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="03bee-108">Child Elements</span></span>  
  
|<span data-ttu-id="03bee-109">Élément</span><span class="sxs-lookup"><span data-stu-id="03bee-109">Element</span></span>|<span data-ttu-id="03bee-110">Description</span><span class="sxs-lookup"><span data-stu-id="03bee-110">Description</span></span>|  
|-------------|-----------------|  
|[\<federationConfiguration>](federationconfiguration.md)|<span data-ttu-id="03bee-111">Contient les paramètres qui configurent les <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> modules http (WSFAM) et <xref:System.IdentityModel.Services.SessionAuthenticationModule> (Sam).</span><span class="sxs-lookup"><span data-stu-id="03bee-111">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03bee-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="03bee-112">Parent Elements</span></span>  
 <span data-ttu-id="03bee-113">None</span><span class="sxs-lookup"><span data-stu-id="03bee-113">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03bee-114">Notes</span><span class="sxs-lookup"><span data-stu-id="03bee-114">Remarks</span></span>  
 <span data-ttu-id="03bee-115">Ajoutez une `<system.identityModel.services>` section au fichier de configuration de votre application pour fournir des paramètres pour le Sam et WSFAM.</span><span class="sxs-lookup"><span data-stu-id="03bee-115">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="03bee-116">Lors de l’utilisation de la <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code, le gestionnaire d’autorisations des revendications ( <xref:System.Security.Claims.ClaimsAuthorizationManager> ) et la stratégie utilisés pour prendre des décisions d’autorisation sont configurés par le biais d’un `<identityConfiguration>` élément qui est explicitement ou explicitement référencé à partir d’un `<federationConfiguration>` élément de cette section.</span><span class="sxs-lookup"><span data-stu-id="03bee-116">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="03bee-117">Pour plus d’informations, consultez les **Notes** sous l' [\<federationConfiguration>](federationconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="03bee-117">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="03bee-118">La `<system.identityModel.services>` section est représentée par la <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe.</span><span class="sxs-lookup"><span data-stu-id="03bee-118">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="03bee-119">La collection d' `<federationConfiguration>` éléments enfants configurés dans la section est représentée par la <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> classe.</span><span class="sxs-lookup"><span data-stu-id="03bee-119">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03bee-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="03bee-120">Example</span></span>  
 <span data-ttu-id="03bee-121">Le code XML suivant montre comment ajouter une `<system.identityModel.services>` section à un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="03bee-121">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="03bee-122">Vous devez d’abord ajouter des déclarations de section pour la `<system.identityModel.services>` section et les `<system.identityModel>` sections.</span><span class="sxs-lookup"><span data-stu-id="03bee-122">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="03bee-123">(Lorsque vous ajoutez une `<system.identityModel.services>` section, vous devez également ajouter une déclaration pour la `<system.identityModel>` section pour vous assurer qu’une `<identityConfiguration>` section par défaut peut être créée par le runtime, si nécessaire.) Une fois les déclarations de section ajoutées, vous pouvez configurer les paramètres d’authentification fédérée sous l' `<system.identityModel.services>` élément.</span><span class="sxs-lookup"><span data-stu-id="03bee-123">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
```xml  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
  <system.identityModel.services>  
    <federationConfiguration>  
      <wsFederation passiveRedirectEnabled="true"
        issuer="http://localhost:15839/wsFederationSTS/Issue"
        realm="http://localhost:50969/" reply="http://localhost:50969/"
        requireHttps="false"
        signOutReply="http://localhost:50969/SignedOutPage.html"
        signOutQueryString="Param1=value2&Param2=value2"
        persistentCookiesOnPassiveRedirects="true" />  
      <cookieHandler requireSsl="false" />  
    </federationConfiguration>  
  </system.identityModel.services>  
  
</configuration>  
```
