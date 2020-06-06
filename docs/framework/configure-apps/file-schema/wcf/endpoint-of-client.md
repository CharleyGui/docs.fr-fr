---
title: <endpoint> de <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855316"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="6d8a5-102">\<endpoint> de \<client></span><span class="sxs-lookup"><span data-stu-id="6d8a5-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="6d8a5-103">Spécifie les propriétés du contrat, de la liaison et de l’adresse du point de terminaison du canal employées par les clients pour se connecter aux points de terminaison de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="6d8a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d8a5-104">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d8a5-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6d8a5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6d8a5-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d8a5-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="6d8a5-107">Attributes</span></span>  
  
|<span data-ttu-id="6d8a5-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="6d8a5-108">Attribute</span></span>|<span data-ttu-id="6d8a5-109">Description</span><span class="sxs-lookup"><span data-stu-id="6d8a5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6d8a5-110">address</span><span class="sxs-lookup"><span data-stu-id="6d8a5-110">address</span></span>|<span data-ttu-id="6d8a5-111">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-111">Required string attribute.</span></span><br /><br /> <span data-ttu-id="6d8a5-112">Spécifie l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-112">Specifies the address of the endpoint.</span></span> <span data-ttu-id="6d8a5-113">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-113">The default is an empty string.</span></span> <span data-ttu-id="6d8a5-114">L'adresse doit être un URI absolu.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-114">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="6d8a5-115">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="6d8a5-115">behaviorConfiguration</span></span>|<span data-ttu-id="6d8a5-116">Chaîne qui contient le nom de comportement du comportement à utiliser pour instancier le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-116">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="6d8a5-117">Le nom du comportement doit être dans la portée, au niveau où le service est défini.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-117">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="6d8a5-118">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="6d8a5-119">binding</span><span class="sxs-lookup"><span data-stu-id="6d8a5-119">binding</span></span>|<span data-ttu-id="6d8a5-120">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-120">Required string attribute.</span></span><br /><br /> <span data-ttu-id="6d8a5-121">Chaîne qui indique le type de liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-121">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="6d8a5-122">Ce type doit posséder une section de configuration inscrite pour pouvoir être référencé.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-122">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="6d8a5-123">Il est inscrit en fonction du nom de la section et non en fonction du nom du type de la liaison.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-123">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="6d8a5-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="6d8a5-124">bindingConfiguration</span></span>|<span data-ttu-id="6d8a5-125">facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-125">Optional.</span></span> <span data-ttu-id="6d8a5-126">Chaîne qui contient le nom de la configuration de liaison à utiliser lorsque le point de terminaison est instancié.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-126">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="6d8a5-127">La configuration de la liaison doit être dans la portée, au niveau où le point de terminaison est défini.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-127">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="6d8a5-128">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="6d8a5-129">Cet attribut est utilisé conjointement à `binding` pour référencer une configuration de liaison spécifique dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="6d8a5-130">Définissez cet attribut si vous essayez d’utiliser une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="6d8a5-131">Sinon, une exception peut être levée.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="6d8a5-132">contract</span><span class="sxs-lookup"><span data-stu-id="6d8a5-132">contract</span></span>|<span data-ttu-id="6d8a5-133">Attribut de chaîne requis.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-133">Required string attribute.</span></span><br /><br /> <span data-ttu-id="6d8a5-134">Chaîne qui indique le contrat exposé par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-134">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="6d8a5-135">L'assembly doit implémenter le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-135">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="6d8a5-136">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="6d8a5-136">endpointConfiguration</span></span>|<span data-ttu-id="6d8a5-137">Chaîne qui spécifie le nom du point de terminaison standard défini par l'attribut `kind`, qui fait référence aux informations de configuration supplémentaires de ce point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-137">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="6d8a5-138">Le même nom doit être défini dans la section `<standardEndpoints>`.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-138">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="6d8a5-139">kind</span><span class="sxs-lookup"><span data-stu-id="6d8a5-139">kind</span></span>|<span data-ttu-id="6d8a5-140">Chaîne qui spécifie le type de point de terminaison standard appliqué.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-140">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="6d8a5-141">Le type doit être inscrit dans la `<extensions>` section ou dans machine. config. Si rien n’est spécifié, un point de terminaison de canal commun est créé.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-141">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="6d8a5-142">name</span><span class="sxs-lookup"><span data-stu-id="6d8a5-142">name</span></span>|<span data-ttu-id="6d8a5-143">Attribut de chaîne facultatif.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-143">Optional string attribute.</span></span> <span data-ttu-id="6d8a5-144">Cet attribut identifie uniquement un point de terminaison pour un contrat donné.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-144">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="6d8a5-145">Vous pouvez définir plusieurs clients pour un type de contrat donné.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-145">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="6d8a5-146">Chaque définition doit être différenciée par un nom de configuration unique.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-146">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="6d8a5-147">Si cet attribut est omis, le point de terminaison correspondant est utilisé comme point de terminaison par défaut associé au type de contrat spécifié.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-147">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="6d8a5-148">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-148">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="6d8a5-149">L'attribut `name` d'une liaison est utilisé pour l'exportation de définition à travers WSDL.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-149">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d8a5-150">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6d8a5-150">Child Elements</span></span>  
  
|<span data-ttu-id="6d8a5-151">Élément</span><span class="sxs-lookup"><span data-stu-id="6d8a5-151">Element</span></span>|<span data-ttu-id="6d8a5-152">Description</span><span class="sxs-lookup"><span data-stu-id="6d8a5-152">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="6d8a5-153">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-153">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="6d8a5-154">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-154">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6d8a5-155">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6d8a5-155">Parent Elements</span></span>  
  
|<span data-ttu-id="6d8a5-156">Élément</span><span class="sxs-lookup"><span data-stu-id="6d8a5-156">Element</span></span>|<span data-ttu-id="6d8a5-157">Description</span><span class="sxs-lookup"><span data-stu-id="6d8a5-157">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="6d8a5-158">Section de configuration qui définit une liste des points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-158">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="6d8a5-159">Exemple</span><span class="sxs-lookup"><span data-stu-id="6d8a5-159">Example</span></span>  
 <span data-ttu-id="6d8a5-160">Il s'agit d'un exemple de configuration de point de terminaison de canal.</span><span class="sxs-lookup"><span data-stu-id="6d8a5-160">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="6d8a5-161">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d8a5-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="6d8a5-162">Configuration client WCF</span><span class="sxs-lookup"><span data-stu-id="6d8a5-162">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="6d8a5-163">Clients</span><span class="sxs-lookup"><span data-stu-id="6d8a5-163">Clients</span></span>](../../../wcf/feature-details/clients.md)
