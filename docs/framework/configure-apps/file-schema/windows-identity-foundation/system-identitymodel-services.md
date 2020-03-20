---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: 57757aaec39bc5c552e7ba12c9779cb3a92a9025
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152502"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="1597c-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="1597c-102">\<system.identityModel.services></span></span>
<span data-ttu-id="1597c-103">Section de configuration pour l’authentification à l’aide du protocole WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="1597c-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
<span data-ttu-id="1597c-104">[**\<configuration>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1597c-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1597c-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span><span class="sxs-lookup"><span data-stu-id="1597c-105">&nbsp;&nbsp;**\<system.identityModel.services>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1597c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1597c-106">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1597c-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="1597c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="1597c-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="1597c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1597c-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="1597c-109">Attributes</span></span>  
 <span data-ttu-id="1597c-110">None</span><span class="sxs-lookup"><span data-stu-id="1597c-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1597c-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="1597c-111">Child Elements</span></span>  
  
|<span data-ttu-id="1597c-112">Élément</span><span class="sxs-lookup"><span data-stu-id="1597c-112">Element</span></span>|<span data-ttu-id="1597c-113">Description</span><span class="sxs-lookup"><span data-stu-id="1597c-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1597c-114">\<fédérationConfiguration></span><span class="sxs-lookup"><span data-stu-id="1597c-114">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="1597c-115">Contient les paramètres <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> qui configurent les <xref:System.IdentityModel.Services.SessionAuthenticationModule> modules HTTP (WSFAM) et (SAM).</span><span class="sxs-lookup"><span data-stu-id="1597c-115">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1597c-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="1597c-116">Parent Elements</span></span>  
 <span data-ttu-id="1597c-117">None</span><span class="sxs-lookup"><span data-stu-id="1597c-117">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1597c-118">Notes </span><span class="sxs-lookup"><span data-stu-id="1597c-118">Remarks</span></span>  
 <span data-ttu-id="1597c-119">Ajoutez `<system.identityModel.services>` une section au fichier de configuration de votre application pour fournir les paramètres du SAM et du WSFAM.</span><span class="sxs-lookup"><span data-stu-id="1597c-119">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1597c-120">Lorsque vous <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> utilisez <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> le ou le groupe pour fournir un contrôle<xref:System.Security.Claims.ClaimsAuthorizationManager>d’accès fondé sur les réclamations dans `<identityConfiguration>` votre code, le gestionnaire de `<federationConfiguration>` l’autorisation des réclamations () et la stratégie utilisée pour prendre des décisions d’autorisation sont configurés à travers un élément qui est implicitement ou explicitement référencé à partir d’un élément de cette section.</span><span class="sxs-lookup"><span data-stu-id="1597c-120">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="1597c-121">Pour plus d’informations, voir **les remarques** sous la [ \<fédérationConfiguration>](federationconfiguration.md) élément.</span><span class="sxs-lookup"><span data-stu-id="1597c-121">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="1597c-122">La `<system.identityModel.services>` section est représentée <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> par la classe.</span><span class="sxs-lookup"><span data-stu-id="1597c-122">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="1597c-123">La collection `<federationConfiguration>` d’éléments pour enfants configuré <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> dans la section est représentée par la classe.</span><span class="sxs-lookup"><span data-stu-id="1597c-123">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1597c-124"> Exemple</span><span class="sxs-lookup"><span data-stu-id="1597c-124">Example</span></span>  
 <span data-ttu-id="1597c-125">Le XML suivant montre `<system.identityModel.services>` comment ajouter une section à un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="1597c-125">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="1597c-126">Vous devez d’abord ajouter `<system.identityModel.services>` des déclarations de section pour la section et les `<system.identityModel>` sections.</span><span class="sxs-lookup"><span data-stu-id="1597c-126">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="1597c-127">(Lorsque vous `<system.identityModel.services>` ajoutez une section, vous devez `<system.identityModel>` également ajouter une `<identityConfiguration>` déclaration pour la section afin de vous assurer qu’une section par défaut peut être créée par l’heure d’exécution si nécessaire.) Une fois les déclarations de section ajoutées, vous pouvez `<system.identityModel.services>` configurer les paramètres d’authentification fédéraux sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="1597c-127">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
