---
title: <serviceHostingEnvironment>
ms.date: 03/30/2017
ms.assetid: 4f8a7c4f-e735-4987-979a-b74fcdae2652
ms.openlocfilehash: 5a7043064593fa329618510d15baeb87da432652
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167095"
---
# \<serviceHostingEnvironment>

<span data-ttu-id="7ee91-101">Cet élément définit le type instancié par l'environnement d'hébergement de service correspondant à un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="7ee91-101">This element defines the type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="7ee91-102">Si cet élément est vide, c'est le type par défaut qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="7ee91-102">If this element is empty, the default type is used.</span></span> <span data-ttu-id="7ee91-103">Cet élément ne peut être utilisé qu'au niveau des fichiers de configuration de l'application ou de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="7ee91-103">This element can only be used at the application or machine level configuration files.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceHostingEnvironment>**  
  
## <a name="syntax"></a><span data-ttu-id="7ee91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ee91-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="Boolean"
                           minFreeMemoryPercentageToActivateService="Integer"
                           multipleSiteBindingsEnabled="Boolean">
  <baseAddressPrefixFilters>
    <add prefix="string" />
  </baseAddressPrefixFilters>
  <serviceActivations>
    <add factory="String"
         service="String" />
  </serviceActivations>
  <transportConfigurationTypes>
    <add name="String"
         transportConfigurationType="String" />
  </transportConfigurationTypes>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ee91-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7ee91-105">Attributes and Elements</span></span>  

 <span data-ttu-id="7ee91-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7ee91-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ee91-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="7ee91-107">Attributes</span></span>  
  
|<span data-ttu-id="7ee91-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7ee91-108">Attribute</span></span>|<span data-ttu-id="7ee91-109">Description</span><span class="sxs-lookup"><span data-stu-id="7ee91-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ee91-110">aspNetCompatibilityEnabled</span><span class="sxs-lookup"><span data-stu-id="7ee91-110">aspNetCompatibilityEnabled</span></span>|<span data-ttu-id="7ee91-111">Valeur booléenne indiquant si le mode de compatibilité ASP.NET a été activé pour l'application actuelle.</span><span class="sxs-lookup"><span data-stu-id="7ee91-111">A Boolean value indicating whether the ASP.NET compatibility mode has been turned on for the current application.</span></span> <span data-ttu-id="7ee91-112">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="7ee91-112">The default is `false`.</span></span><br /><br /> <span data-ttu-id="7ee91-113">Lorsque cet attribut a la valeur `true` , les demandes adressées aux services Windows Communication Foundation (WCF) transitent via le pipeline HTTP ASP.net, et la communication sur les protocoles non-http est interdite.</span><span class="sxs-lookup"><span data-stu-id="7ee91-113">When this attribute is set to `true`, requests to Windows Communication Foundation (WCF) services flow through the ASP.NET HTTP pipeline, and communication over non-HTTP protocols is prohibited.</span></span> <span data-ttu-id="7ee91-114">Pour plus d’informations, consultez [services WCF et ASP.net](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="7ee91-114">For more information, see [WCF Services and ASP.NET](../../../wcf/feature-details/wcf-services-and-aspnet.md).</span></span>|  
|<span data-ttu-id="7ee91-115">minFreeMemoryPercentageToActivateService</span><span class="sxs-lookup"><span data-stu-id="7ee91-115">minFreeMemoryPercentageToActivateService</span></span>|<span data-ttu-id="7ee91-116">Entier qui spécifie la quantité minimale de mémoire disponible pour le système, avant qu’un service WCF puisse être activé.</span><span class="sxs-lookup"><span data-stu-id="7ee91-116">An integer that specifies the minimum amount of free memory that should be available to the system, before a WCF service can be activated.</span></span> <span data-ttu-id="7ee91-117">**Attention :**  La spécification de cet attribut avec une confiance partielle dans le fichier web.config d’un service WCF entraîne une <xref:System.Security.SecurityException> lorsque le service est exécuté.</span><span class="sxs-lookup"><span data-stu-id="7ee91-117">**Caution:**  Specifying this attribute along with partial trust in the web.config file of a WCF service will result in a <xref:System.Security.SecurityException> when the service is run.</span></span>|  
|<span data-ttu-id="7ee91-118">multipleSiteBindingsEnabled</span><span class="sxs-lookup"><span data-stu-id="7ee91-118">multipleSiteBindingsEnabled</span></span>|<span data-ttu-id="7ee91-119">Valeur booléenne qui spécifie si plusieurs liaisons IIS par site sont autorisées.</span><span class="sxs-lookup"><span data-stu-id="7ee91-119">A Boolean value that specifies whether multiple IIS bindings per site is enabled.</span></span><br /><br /> <span data-ttu-id="7ee91-120">Les services IIS se composent de sites Web, qui sont des conteneurs d'applications virtuelles contenant des répertoires virtuels.</span><span class="sxs-lookup"><span data-stu-id="7ee91-120">IIS consists of web sites, which are containers for virtual applications containing virtual directories.</span></span> <span data-ttu-id="7ee91-121">L’application dans un site est accessible par le biais d’une ou de plusieurs liaisons IIS.</span><span class="sxs-lookup"><span data-stu-id="7ee91-121">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="7ee91-122">Une liaison IIS fournit deux informations : un protocole de liaison et des informations de liaison.</span><span class="sxs-lookup"><span data-stu-id="7ee91-122">An IIS binding provides two pieces of information: a binding protocol and binding information.</span></span> <span data-ttu-id="7ee91-123">Le protocole de liaison définit le schéma selon lequel la communication est établie et les informations de liaison sont les informations utilisées pour accéder au site.</span><span class="sxs-lookup"><span data-stu-id="7ee91-123">Binding protocol defines the scheme over which communication occurs, and binding information is the information used to access the site.</span></span> <span data-ttu-id="7ee91-124">HTTP peut être un exemple de protocole de liaison, tandis que les informations de liaison peuvent contenir une adresse IP, un port, un en-tête d'hôte, etc.</span><span class="sxs-lookup"><span data-stu-id="7ee91-124">An example of a binding protocol can be HTTP, whereas binding information can contain an IP address, Port, host header, etc.</span></span><br /><br /> <span data-ttu-id="7ee91-125">IIS prend en charge la spécification de plusieurs liaisons IIS par site, ce qui entraîne plusieurs adresses de base par schéma.</span><span class="sxs-lookup"><span data-stu-id="7ee91-125">IIS supports specifying multiple IIS bindings per site, which results in multiple base addresses per scheme.</span></span> <span data-ttu-id="7ee91-126">Toutefois, un service Windows Communication Foundation (WCF) hébergé sur un site autorise la liaison à un seul baseAddress par schéma.</span><span class="sxs-lookup"><span data-stu-id="7ee91-126">However, a Windows Communication Foundation (WCF) service hosted under a site allows binding to only one baseAddress per scheme.</span></span><br /><br /> <span data-ttu-id="7ee91-127">Pour activer plusieurs liaisons IIS par site pour un service Windows Communication Foundation (WCF), affectez à cet attribut la valeur `true` .</span><span class="sxs-lookup"><span data-stu-id="7ee91-127">To enable multiple IIS bindings per site for a Windows Communication Foundation (WCF) service, set this attribute to `true`.</span></span> <span data-ttu-id="7ee91-128">Notez que la spécification de plusieurs liaisons de site est prise en charge uniquement pour le protocole HTTP.</span><span class="sxs-lookup"><span data-stu-id="7ee91-128">Notice that multiple site binding is supported only for the HTTP protocol.</span></span> <span data-ttu-id="7ee91-129">L'adresse des points de terminaison dans le fichier de configuration doit être un URI complet.</span><span class="sxs-lookup"><span data-stu-id="7ee91-129">The address of endpoints in the configuration file needs to be a complete URI.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ee91-130">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7ee91-130">Child Elements</span></span>  
  
|<span data-ttu-id="7ee91-131">Élément</span><span class="sxs-lookup"><span data-stu-id="7ee91-131">Element</span></span>|<span data-ttu-id="7ee91-132">Description</span><span class="sxs-lookup"><span data-stu-id="7ee91-132">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="7ee91-133">Collection des éléments de configuration qui spécifient des filtres de préfixe pour les adresses de base utilisée par l’hôte de service.</span><span class="sxs-lookup"><span data-stu-id="7ee91-133">A collection of configuration elements that specify prefix filters for the base addresses used by the service host.</span></span>|  
|[\<serviceActivations>](serviceactivations.md)|<span data-ttu-id="7ee91-134">Section de configuration qui décrit les paramètres d'activation.</span><span class="sxs-lookup"><span data-stu-id="7ee91-134">A configuration section that describes activation settings.</span></span>|  
|[\<transportConfigurationTypes>](transportconfigurationtypes.md)|<span data-ttu-id="7ee91-135">Collection des éléments de configuration identifiant le type d’un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="7ee91-135">A collection of configuration elements that identify the type of a particular transport.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ee91-136">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7ee91-136">Parent Elements</span></span>  
  
|<span data-ttu-id="7ee91-137">Élément</span><span class="sxs-lookup"><span data-stu-id="7ee91-137">Element</span></span>|<span data-ttu-id="7ee91-138">Description</span><span class="sxs-lookup"><span data-stu-id="7ee91-138">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7ee91-139">serviceModel</span><span class="sxs-lookup"><span data-stu-id="7ee91-139">serviceModel</span></span>|<span data-ttu-id="7ee91-140">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7ee91-140">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ee91-141">Notes</span><span class="sxs-lookup"><span data-stu-id="7ee91-141">Remarks</span></span>  

 <span data-ttu-id="7ee91-142">Par défaut, les services WCF sont exécutés conjointement à ASP.NET dans les domaines d'application hébergés (AppDomain).</span><span class="sxs-lookup"><span data-stu-id="7ee91-142">By default, WCF services run side-by-side with ASP.NET in hosted Application Domains (AppDomain).</span></span> <span data-ttu-id="7ee91-143">Bien que WCF et ASP.NET puissent coexister sur le même domaine AppDomain, les demandes WCF ne sont pas traitées par défaut par le pipeline HTTP d'ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7ee91-143">Even though WCF and ASP.NET can coexist in the same AppDomain, WCF requests are not processed by the ASP.NET HTTP Pipeline by default.</span></span> <span data-ttu-id="7ee91-144">En conséquence, plusieurs éléments de la plate-forme d'application ASP.NET ne sont pas disponibles pour les services WCF.</span><span class="sxs-lookup"><span data-stu-id="7ee91-144">As a result, several elements of the ASP.NET application platform are not available to WCF services.</span></span> <span data-ttu-id="7ee91-145">Cela comprend</span><span class="sxs-lookup"><span data-stu-id="7ee91-145">These include</span></span>  
  
- <span data-ttu-id="7ee91-146">Autorisation de l'URL/du fichier ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7ee91-146">ASP.NET File/URL Authorization</span></span>  
  
- <span data-ttu-id="7ee91-147">Emprunt d'identité ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7ee91-147">ASP.NET Impersonation</span></span>  
  
- <span data-ttu-id="7ee91-148">État de session basé sur les cookies</span><span class="sxs-lookup"><span data-stu-id="7ee91-148">Cookie-based Session State</span></span>  
  
- <span data-ttu-id="7ee91-149">HttpContext.Current</span><span class="sxs-lookup"><span data-stu-id="7ee91-149">HttpContext.Current</span></span>  
  
- <span data-ttu-id="7ee91-150">Extensibilité de pipeline via HttpModule personnalisé</span><span class="sxs-lookup"><span data-stu-id="7ee91-150">Pipeline Extensibility via custom HttpModule</span></span>  
  
 <span data-ttu-id="7ee91-151">Si vos services WCF doivent fonctionner dans le contexte ASP.NET et communiquer uniquement via HTTP, vous pouvez utiliser le mode de compatibilité ASP.NET de WCF.</span><span class="sxs-lookup"><span data-stu-id="7ee91-151">If your WCF services need to function in the ASP.NET context, and communicate only over HTTP, you can use WCF’s ASP.NET compatibility mode.</span></span> <span data-ttu-id="7ee91-152">Ce mode est activé lorsque l'attribut `aspNetCompatibilityEnabled` a la valeur `true` au niveau de l'application.</span><span class="sxs-lookup"><span data-stu-id="7ee91-152">This mode is turned on when the `aspNetCompatibilityEnabled` attribute is set to `true` at the application level.</span></span> <span data-ttu-id="7ee91-153">Les implémentations de service doivent déclarer leur capacité de fonctionner en mode de compatibilité à l'aide de la classe <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7ee91-153">Service implementations must declare their ability to run in compatibility mode using the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> class.</span></span> <span data-ttu-id="7ee91-154">Lorsque le mode de compatibilité est activé :</span><span class="sxs-lookup"><span data-stu-id="7ee91-154">When the compatibility mode is enabled,</span></span>  
  
- <span data-ttu-id="7ee91-155">L'autorisation de l'URL/du fichier ASP.NET est appliquée avant l'autorisation WCF.</span><span class="sxs-lookup"><span data-stu-id="7ee91-155">ASP.NET File/URL Authorization is enforced prior to WCF authorization.</span></span> <span data-ttu-id="7ee91-156">Une décision d'autorisation est basée sur l'identité de la demande au niveau du transport.</span><span class="sxs-lookup"><span data-stu-id="7ee91-156">An authorization decision is based on the transport-level identity of the request.</span></span> <span data-ttu-id="7ee91-157">Les identités au niveau du message sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="7ee91-157">Identities at the message level are ignored.</span></span>  
  
- <span data-ttu-id="7ee91-158">Les opérations de service WCF commencent à s'exécuter dans le contexte d'emprunt d'identité ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7ee91-158">WCF service operations start to execute in the ASP.NET impersonation context.</span></span> <span data-ttu-id="7ee91-159">Si les emprunts d'identité ASP.NET et WCF sont tous deux activés pour un service spécifique, c'est le contexte d'emprunt d'identité WCF qui est appliqué.</span><span class="sxs-lookup"><span data-stu-id="7ee91-159">If both ASP.NET impersonation and WCF impersonation are enabled for a specific service, the WCF impersonation context applies.</span></span>  
  
- <span data-ttu-id="7ee91-160">HttpContext.Current peut être utilisé à partir du code de service WCF ; cette opération permet d'empêcher l'exposition des points de terminaison non-HTTP.</span><span class="sxs-lookup"><span data-stu-id="7ee91-160">HttpContext.Current can be used from WCF service code, and services are prevented from exposing non-HTTP endpoints.</span></span>  
  
- <span data-ttu-id="7ee91-161">Les demandes WCF sont traitées par le pipeline ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="7ee91-161">WCF requests are processed by the ASP.NET pipeline.</span></span> <span data-ttu-id="7ee91-162">Les HttpModules ayant été configurés pour agir sur les requêtes entrantes peuvent également traiter des demandes WCF.</span><span class="sxs-lookup"><span data-stu-id="7ee91-162">HttpModules that have been configured to act on incoming requests can also process WCF requests.</span></span> <span data-ttu-id="7ee91-163">Ils peuvent inclure des composants de plate-forme ASP.NET (par exemple, <xref:System.Web.SessionState.SessionStateModule>), ainsi que des modules tiers personnalisés.</span><span class="sxs-lookup"><span data-stu-id="7ee91-163">These can include ASP.NET platform components (e.g., <xref:System.Web.SessionState.SessionStateModule>), as well as custom third party modules.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ee91-164">Exemple</span><span class="sxs-lookup"><span data-stu-id="7ee91-164">Example</span></span>  

 <span data-ttu-id="7ee91-165">L'exemple de code suivant indique comment activer le Mode de compatibilité ASP.</span><span class="sxs-lookup"><span data-stu-id="7ee91-165">The following code sample shows how to enable ASP Compatibility Mode.</span></span>  
  
## <a name="code"></a><span data-ttu-id="7ee91-166">Code</span><span class="sxs-lookup"><span data-stu-id="7ee91-166">Code</span></span>  
  
```xml  
<serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>
```  
  
## <a name="see-also"></a><span data-ttu-id="7ee91-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7ee91-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="7ee91-168">Hosting</span><span class="sxs-lookup"><span data-stu-id="7ee91-168">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
- [<span data-ttu-id="7ee91-169">Services WCF et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="7ee91-169">WCF Services and ASP.NET</span></span>](../../../wcf/feature-details/wcf-services-and-aspnet.md)
