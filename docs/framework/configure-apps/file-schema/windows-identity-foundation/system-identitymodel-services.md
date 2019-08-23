---
title: <system.identityModel.services>
ms.date: 03/30/2017
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
author: BrucePerlerMS
ms.openlocfilehash: bef061c5c982fb0e740f889336a3b334bc19225e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943658"
---
# <a name="systemidentitymodelservices"></a><span data-ttu-id="91a35-102">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="91a35-102">\<system.identityModel.services></span></span>
<span data-ttu-id="91a35-103">Section de configuration pour l’authentification à l’aide du protocole WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="91a35-103">Configuration section for authentication using the WS-Federation protocol.</span></span>  
  
 <span data-ttu-id="91a35-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="91a35-104">\<system.identityModel.services></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a35-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91a35-105">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="91a35-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="91a35-106">Attributes and Elements</span></span>  
 <span data-ttu-id="91a35-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="91a35-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="91a35-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="91a35-108">Attributes</span></span>  
 <span data-ttu-id="91a35-109">Aucun</span><span class="sxs-lookup"><span data-stu-id="91a35-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="91a35-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="91a35-110">Child Elements</span></span>  
  
|<span data-ttu-id="91a35-111">Élément</span><span class="sxs-lookup"><span data-stu-id="91a35-111">Element</span></span>|<span data-ttu-id="91a35-112">Description</span><span class="sxs-lookup"><span data-stu-id="91a35-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="91a35-113">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="91a35-113">\<federationConfiguration></span></span>](federationconfiguration.md)|<span data-ttu-id="91a35-114">Contient les paramètres qui configurent les <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> modules http (WSFAM) <xref:System.IdentityModel.Services.SessionAuthenticationModule> et (Sam).</span><span class="sxs-lookup"><span data-stu-id="91a35-114">Contains the settings that configure the <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) and the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) HTTP modules.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="91a35-115">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="91a35-115">Parent Elements</span></span>  
 <span data-ttu-id="91a35-116">Aucun</span><span class="sxs-lookup"><span data-stu-id="91a35-116">None</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91a35-117">Notes</span><span class="sxs-lookup"><span data-stu-id="91a35-117">Remarks</span></span>  
 <span data-ttu-id="91a35-118">Ajoutez une `<system.identityModel.services>` section au fichier de configuration de votre application pour fournir des paramètres pour le Sam et WSFAM.</span><span class="sxs-lookup"><span data-stu-id="91a35-118">Add a `<system.identityModel.services>` section to your application’s configuration file to provide settings for the SAM and WSFAM.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="91a35-119">Lors de l' <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> utilisation de <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> la classe ou pour fournir un contrôle d’accès basé sur les revendications dans votre code,<xref:System.Security.Claims.ClaimsAuthorizationManager>le gestionnaire d’autorisations des revendications () et la stratégie utilisés pour prendre `<identityConfiguration>` des décisions d’autorisation sont configurés via un élément qui est référencé implicitement ou explicitement à partir d' `<federationConfiguration>` un élément de cette section.</span><span class="sxs-lookup"><span data-stu-id="91a35-119">When using the <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> or the <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> class to provide claims-based access control in your code, the claims authorization manager (<xref:System.Security.Claims.ClaimsAuthorizationManager>) and policy that is used to make authorization decisions are configured through an `<identityConfiguration>` element that is implicitly or explicitly referenced from a `<federationConfiguration>` element in this section.</span></span> <span data-ttu-id="91a35-120">Pour plus d’informations, consultez les **Notes** sous l' [ \<élément federationConfiguration >](federationconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="91a35-120">For more information, see the **Remarks** under the [\<federationConfiguration>](federationconfiguration.md) element.</span></span>  
  
 <span data-ttu-id="91a35-121">La `<system.identityModel.services>` section est représentée par la <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> classe.</span><span class="sxs-lookup"><span data-stu-id="91a35-121">The `<system.identityModel.services>` section is represented by the <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection> class.</span></span> <span data-ttu-id="91a35-122">La collection d’éléments `<federationConfiguration>` enfants configurés dans la section est représentée par <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> la classe.</span><span class="sxs-lookup"><span data-stu-id="91a35-122">The collection of child `<federationConfiguration>` elements configured in the section is represented by the <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91a35-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="91a35-123">Example</span></span>  
 <span data-ttu-id="91a35-124">Le code XML suivant montre comment ajouter une `<system.identityModel.services>` section à un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="91a35-124">The following XML shows how to add a `<system.identityModel.services>` section to a configuration file.</span></span> <span data-ttu-id="91a35-125">Vous devez d’abord ajouter des déclarations de section `<system.identityModel.services>` pour la section `<system.identityModel>` et les sections.</span><span class="sxs-lookup"><span data-stu-id="91a35-125">You must first add section declarations for both the `<system.identityModel.services>` section and the `<system.identityModel>` sections.</span></span> <span data-ttu-id="91a35-126">(Lorsque vous ajoutez une `<system.identityModel.services>` section, vous devez également ajouter une déclaration pour la `<system.identityModel>` section pour vous assurer qu’une `<identityConfiguration>` section par défaut peut être créée par le runtime, si nécessaire.) Une fois les déclarations de section ajoutées, vous pouvez configurer les paramètres d’authentification fédérée `<system.identityModel.services>` sous l’élément.</span><span class="sxs-lookup"><span data-stu-id="91a35-126">(When you add a `<system.identityModel.services>` section, you should also add a declaration for the `<system.identityModel>` section to ensure that a default `<identityConfiguration>` section can be created by the runtime if necessary.) After the section declarations have been added, you can configure federated authentication settings under the `<system.identityModel.services>` element.</span></span>  
  
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
