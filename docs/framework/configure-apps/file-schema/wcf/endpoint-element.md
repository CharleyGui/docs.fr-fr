---
title: <endpoint> (élément)
ms.date: 03/30/2017
ms.assetid: 2fc8fedc-78d0-4e87-8142-fbfd26c15a4e
ms.openlocfilehash: befebc090900576b1e0f7ca679e1f5f5cd15af9a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183804"
---
# <a name="endpoint-element"></a><span data-ttu-id="c5150-102">\<endpoint>, élément</span><span class="sxs-lookup"><span data-stu-id="c5150-102">\<endpoint> element</span></span>

<span data-ttu-id="c5150-103">Spécifie la liaison, le contrat et les propriétés d’adresse d’un point de terminaison de service, utilisé pour exposer des services.</span><span class="sxs-lookup"><span data-stu-id="c5150-103">Specifies binding, contract, and address properties for a service endpoint, which is used to expose services.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="c5150-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5150-104">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          bindingName="String"
          bindingNamespace="String"
          contract="String"
          endpointConfiguration="String"
          isSystemEndpoint="Boolean"
          kind="String"
          listenUriMode="Explicit/Unique"
          listenUri="Uri">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c5150-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="c5150-105">Attributes and Elements</span></span>  

 <span data-ttu-id="c5150-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="c5150-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c5150-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="c5150-107">Attributes</span></span>  
  
|<span data-ttu-id="c5150-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c5150-108">Attribute</span></span>|<span data-ttu-id="c5150-109">Description</span><span class="sxs-lookup"><span data-stu-id="c5150-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c5150-110">address</span><span class="sxs-lookup"><span data-stu-id="c5150-110">address</span></span>|<span data-ttu-id="c5150-111">Chaîne qui contient l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c5150-111">A string that contains the address of the endpoint.</span></span> <span data-ttu-id="c5150-112">L'adresse peut être spécifiée comme une adresse absolue ou relative.</span><span class="sxs-lookup"><span data-stu-id="c5150-112">The address can be specified as an absolute or relative address.</span></span> <span data-ttu-id="c5150-113">Si une adresse relative est fournie, l'hôte doit fournir une adresse de base appropriée au schéma de transport utilisé dans la liaison.</span><span class="sxs-lookup"><span data-stu-id="c5150-113">If a relative address is provided, the host is expected to provide a base address appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="c5150-114">Si une adresse n'est pas configurée, l'adresse de base est l'adresse pour ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c5150-114">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span><br /><br /> <span data-ttu-id="c5150-115">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="c5150-115">The default is an empty string.</span></span>|  
|<span data-ttu-id="c5150-116">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="c5150-116">behaviorConfiguration</span></span>|<span data-ttu-id="c5150-117">Chaîne qui contient le nom du comportement à utiliser au point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c5150-117">A string that contains the name of the behavior to be used in the endpoint.</span></span>|  
|<span data-ttu-id="c5150-118">binding</span><span class="sxs-lookup"><span data-stu-id="c5150-118">binding</span></span>|<span data-ttu-id="c5150-119">Attribut de chaîne requis indiquant le type de liaison à utiliser.</span><span class="sxs-lookup"><span data-stu-id="c5150-119">Required string attribute that specifies the type of binding to use.</span></span> <span data-ttu-id="c5150-120">Ce type doit posséder une section de configuration inscrite pour pouvoir être référencé.</span><span class="sxs-lookup"><span data-stu-id="c5150-120">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="c5150-121">Il est inscrit en fonction du nom de la section et non en fonction du nom du type de la liaison.</span><span class="sxs-lookup"><span data-stu-id="c5150-121">The type is the registered by section name, rather than by the type name of the binding.</span></span>|  
|<span data-ttu-id="c5150-122">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="c5150-122">bindingConfiguration</span></span>|<span data-ttu-id="c5150-123">Chaîne qui spécifie le nom de la liaison à utiliser lorsque le point de terminaison est instancié.</span><span class="sxs-lookup"><span data-stu-id="c5150-123">A string that specifies the binding name of the binding to use when the endpoint is instantiated.</span></span> <span data-ttu-id="c5150-124">Le nom de liaison doit être dans la portée, au niveau où le point de terminaison est défini.</span><span class="sxs-lookup"><span data-stu-id="c5150-124">The binding name must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="c5150-125">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="c5150-125">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="c5150-126">Cet attribut est utilisé conjointement à `binding` pour référencer une configuration de liaison spécifique dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="c5150-126">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="c5150-127">Définissez cet attribut si vous essayez d’utiliser une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="c5150-127">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="c5150-128">Sinon, une exception peut être levée.</span><span class="sxs-lookup"><span data-stu-id="c5150-128">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="c5150-129">bindingName</span><span class="sxs-lookup"><span data-stu-id="c5150-129">bindingName</span></span>|<span data-ttu-id="c5150-130">Chaîne qui spécifie le nom qualifié unique de la liaison pour l’exportation de définition à travers WSDL.</span><span class="sxs-lookup"><span data-stu-id="c5150-130">A string that specifies the unique qualified name of the binding for definition export through WSDL.</span></span> <span data-ttu-id="c5150-131">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="c5150-131">The default is an empty string.</span></span>|  
|<span data-ttu-id="c5150-132">bindingNamespace</span><span class="sxs-lookup"><span data-stu-id="c5150-132">bindingNamespace</span></span>|<span data-ttu-id="c5150-133">Chaîne qui spécifie le nom qualifié de l’espace de noms de la liaison pour l’exportation de définition à travers WSDL.</span><span class="sxs-lookup"><span data-stu-id="c5150-133">A string that specifies the qualified name of the namespace of the binding for definition export through WSDL.</span></span> <span data-ttu-id="c5150-134">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="c5150-134">The default is an empty string.</span></span>|  
|<span data-ttu-id="c5150-135">contract</span><span class="sxs-lookup"><span data-stu-id="c5150-135">contract</span></span>|<span data-ttu-id="c5150-136">Chaîne qui indique le contrat exposé par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="c5150-136">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="c5150-137">L'assembly doit implémenter le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="c5150-137">The assembly must implement the contract type.</span></span> <span data-ttu-id="c5150-138">Si une implémentation de service implémente un seul type de contrat, cette propriété peut alors être omise.</span><span class="sxs-lookup"><span data-stu-id="c5150-138">If a service implementation implements a single contract type, then this property can be omitted.</span></span> <span data-ttu-id="c5150-139">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="c5150-139">The default is an empty string.</span></span>|  
|<span data-ttu-id="c5150-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="c5150-140">endpointConfiguration</span></span>|<span data-ttu-id="c5150-141">Chaîne qui spécifie le nom du point de terminaison standard défini par l'attribut `kind`, qui fait référence aux informations de configuration supplémentaires de ce point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="c5150-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="c5150-142">Le même nom doit être défini dans la section `<standardEndpoints>`.</span><span class="sxs-lookup"><span data-stu-id="c5150-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="c5150-143">isSystemEndpoint</span><span class="sxs-lookup"><span data-stu-id="c5150-143">isSystemEndpoint</span></span>|<span data-ttu-id="c5150-144">Valeur booléenne qui spécifie si un point de terminaison est un point de terminaison d'infrastructure.</span><span class="sxs-lookup"><span data-stu-id="c5150-144">A Boolean value that specifies whether an endpoint is an infrastructure endpoint.</span></span>|  
|<span data-ttu-id="c5150-145">kind</span><span class="sxs-lookup"><span data-stu-id="c5150-145">kind</span></span>|<span data-ttu-id="c5150-146">Chaîne qui spécifie le type de point de terminaison standard appliqué.</span><span class="sxs-lookup"><span data-stu-id="c5150-146">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="c5150-147">Le type doit être inscrit dans la section `<extensions>` ou dans machine.config. Si rien n’est spécifié, un point de terminaison de service commun est créé.</span><span class="sxs-lookup"><span data-stu-id="c5150-147">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common service endpoint is created.</span></span>|  
|<span data-ttu-id="c5150-148">listenUriMode</span><span class="sxs-lookup"><span data-stu-id="c5150-148">listenUriMode</span></span>|<span data-ttu-id="c5150-149">Spécifie la manière dont le transport traite le `ListenUri` fourni sur lequel le service effectue son écoute.</span><span class="sxs-lookup"><span data-stu-id="c5150-149">Specifies how the transport treats the `ListenUri` provided for the service to listen on.</span></span> <span data-ttu-id="c5150-150">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c5150-150">Valid values are</span></span><br /><br /> <span data-ttu-id="c5150-151">-Explicit</span><span class="sxs-lookup"><span data-stu-id="c5150-151">-   Explicit</span></span><br /><span data-ttu-id="c5150-152">-Unique</span><span class="sxs-lookup"><span data-stu-id="c5150-152">-   Unique</span></span><br /><br /> <span data-ttu-id="c5150-153">La valeur par défaut est Explicit.</span><span class="sxs-lookup"><span data-stu-id="c5150-153">The default value is Explicit.</span></span>|  
|<span data-ttu-id="c5150-154">listenUri</span><span class="sxs-lookup"><span data-stu-id="c5150-154">listenUri</span></span>|<span data-ttu-id="c5150-155">Chaîne qui spécifie l'URI au niveau duquel le point de terminaison de service effectue son écoute.</span><span class="sxs-lookup"><span data-stu-id="c5150-155">A string that specifies the URI at which the service endpoint listens.</span></span> <span data-ttu-id="c5150-156">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="c5150-156">The default is an empty string.</span></span>|  
|<span data-ttu-id="c5150-157">name</span><span class="sxs-lookup"><span data-stu-id="c5150-157">name</span></span>|<span data-ttu-id="c5150-158">Attribut facultatif.</span><span class="sxs-lookup"><span data-stu-id="c5150-158">Optional attribute.</span></span> <span data-ttu-id="c5150-159">Chaîne qui spécifie le nom du point de terminaison du service.</span><span class="sxs-lookup"><span data-stu-id="c5150-159">A string that specifies the name the service endpoint.</span></span> <span data-ttu-id="c5150-160">La valeur par défaut correspond à la concaténation du nom de la liaison et de celui de la description du contrat.</span><span class="sxs-lookup"><span data-stu-id="c5150-160">The default value is the concatenation of the binding name and the contract description name.</span></span> <span data-ttu-id="c5150-161">Les services peuvent disposer de plusieurs points de terminaison, l'attribut `name` du point de terminaison est donc différent du nom du service.</span><span class="sxs-lookup"><span data-stu-id="c5150-161">Services may have multiple endpoints, so the endpoint’s `name` attribute is distinct from the name of the service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c5150-162">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="c5150-162">Child Elements</span></span>  
  
|<span data-ttu-id="c5150-163">Élément</span><span class="sxs-lookup"><span data-stu-id="c5150-163">Element</span></span>|<span data-ttu-id="c5150-164">Description</span><span class="sxs-lookup"><span data-stu-id="c5150-164">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="c5150-165">Collection d'en-têtes d'adresses.</span><span class="sxs-lookup"><span data-stu-id="c5150-165">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="c5150-166">Identité qui permet l'authentification d'un point de terminaison par les autres points de terminaison qui échangent des messages avec lui.</span><span class="sxs-lookup"><span data-stu-id="c5150-166">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c5150-167">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="c5150-167">Parent Elements</span></span>  
  
|<span data-ttu-id="c5150-168">Élément</span><span class="sxs-lookup"><span data-stu-id="c5150-168">Element</span></span>|<span data-ttu-id="c5150-169">Description</span><span class="sxs-lookup"><span data-stu-id="c5150-169">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="c5150-170">Section de configuration qui définit une liste des points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="c5150-170">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="c5150-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="c5150-171">Example</span></span>  

 <span data-ttu-id="c5150-172">Il s'agit d'un exemple de configuration de point de terminaison de service.</span><span class="sxs-lookup"><span data-stu-id="c5150-172">This is an example of a service endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          bindingName="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
  <headers>
    <region xmlns="http://tempuri.org/">EastCoast</region>
    <member xmlns="http://tempuri.org/">Gold</member>
  </headers>
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="c5150-173">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c5150-173">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceEndpointElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.Description.ServiceEndpoint>
- [<span data-ttu-id="c5150-174">Points de terminaison : Adresses, liaisons et contrats</span><span class="sxs-lookup"><span data-stu-id="c5150-174">Endpoints: Addresses, Bindings, and Contracts</span></span>](../../../wcf/feature-details/endpoints-addresses-bindings-and-contracts.md)
- [<span data-ttu-id="c5150-175">Procédure : créer un point de terminaison de service dans la configuration</span><span class="sxs-lookup"><span data-stu-id="c5150-175">How to: Create a Service Endpoint in Configuration</span></span>](../../../wcf/feature-details/how-to-create-a-service-endpoint-in-configuration.md)
