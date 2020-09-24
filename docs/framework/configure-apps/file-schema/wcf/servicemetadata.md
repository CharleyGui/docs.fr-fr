---
title: <serviceMetadata>
ms.date: 03/30/2017
ms.assetid: 2b4c3b4c-31d4-4908-a9b7-5bb411c221f2
ms.openlocfilehash: 2236361316254d065abd1fb62fd2e509be289a4c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153857"
---
# \<serviceMetadata>

<span data-ttu-id="2f91b-101">Spécifie la publication de métadonnées de service et des informations associées.</span><span class="sxs-lookup"><span data-stu-id="2f91b-101">Specifies the publication of service metadata and associated information.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceMetadata>**  
  
## <a name="syntax"></a><span data-ttu-id="2f91b-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2f91b-102">Syntax</span></span>  
  
```xml  
<serviceMetadata externalMetadataLocation="String"
                 httpGetBinding="String"
                 httpGetBindingConfiguration="String"
                 httpGetEnabled="Boolean"
                 httpGetUrl="String"
                 httpsGetBinding="String"
                 httpsGetBindingConfiguration="String"
                 httpsGetEnabled="Boolean"
                 httpsGetUrl="String"
                 policyVersion="Policy12/Policy15" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2f91b-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="2f91b-103">Attributes and Elements</span></span>  

 <span data-ttu-id="2f91b-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="2f91b-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2f91b-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="2f91b-105">Attributes</span></span>  
  
|<span data-ttu-id="2f91b-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="2f91b-106">Attribute</span></span>|<span data-ttu-id="2f91b-107">Description</span><span class="sxs-lookup"><span data-stu-id="2f91b-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2f91b-108">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="2f91b-108">externalMetadataLocation</span></span>|<span data-ttu-id="2f91b-109">Uri contenant l'emplacement d'un fichier WSDL renvoyé à l'utilisateur en réponse aux demandes WSDL et MEX au lieu du WSDL généré automatiquement.</span><span class="sxs-lookup"><span data-stu-id="2f91b-109">A Uri that contains the location of a WSDL file, which is returned to the user in response to WSDL and MEX requests instead of the auto-generated WSDL.</span></span> <span data-ttu-id="2f91b-110">Lorsque cet attribut n'est pas défini, le WSDL par défaut est renvoyé.</span><span class="sxs-lookup"><span data-stu-id="2f91b-110">When this attribute is not set, the default WSDL is returned.</span></span> <span data-ttu-id="2f91b-111">La valeur par défaut est une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="2f91b-111">The default is an empty string.</span></span>|  
|<span data-ttu-id="2f91b-112">httpGetBinding</span><span class="sxs-lookup"><span data-stu-id="2f91b-112">httpGetBinding</span></span>|<span data-ttu-id="2f91b-113">Chaîne qui spécifie le type de la liaison qui sera utilisée pour la récupération de métadonnées via HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="2f91b-113">A string that specifies the type of the binding that will be used for metadata retrieval via HTTP GET.</span></span> <span data-ttu-id="2f91b-114">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="2f91b-114">This setting is optional.</span></span> <span data-ttu-id="2f91b-115">En l'absence de spécification, les liaisons par défaut seront utilisées.</span><span class="sxs-lookup"><span data-stu-id="2f91b-115">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="2f91b-116">La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="2f91b-116">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="2f91b-117">En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f91b-117">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="2f91b-118">httpGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f91b-118">httpGetBindingConfiguration</span></span>|<span data-ttu-id="2f91b-119">Chaîne qui définit le nom de la liaison spécifiée dans l’attribut `httpGetBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="2f91b-119">A string that sets the name of the binding that is specified in the `httpGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="2f91b-120">Le même nom doit être défini dans la section `<bindings>`.</span><span class="sxs-lookup"><span data-stu-id="2f91b-120">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="2f91b-121">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="2f91b-121">httpGetEnabled</span></span>|<span data-ttu-id="2f91b-122">Valeur booléenne indiquant si les métadonnées de service correspondant à la récupération doivent être publiées à l'aide d'une demande HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="2f91b-122">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="2f91b-123">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="2f91b-123">The default is `false`.</span></span><br /><br /> <span data-ttu-id="2f91b-124">Si l'attribut httpGetUrl n'est pas spécifié, l'adresse utilisée pour publier les métadonnées est celle du service à laquelle est ajouté le suffixe « ? wsdl ».</span><span class="sxs-lookup"><span data-stu-id="2f91b-124">If the httpGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="2f91b-125">Par exemple, si l’adresse du service est `http://localhost:8080/CalculatorService` , l’adresse de métadonnées http/obtenir est `http://localhost:8080/CalculatorService?wsdl` .</span><span class="sxs-lookup"><span data-stu-id="2f91b-125">For example, if the service address is `http://localhost:8080/CalculatorService`, the HTTP/Get metadata address is `http://localhost:8080/CalculatorService?wsdl`.</span></span><br /><br /> <span data-ttu-id="2f91b-126">Si cette propriété est `false` , ou si l’adresse du service n’est pas basée sur http ou HTTPS, «  ? WSDL » est ignoré.</span><span class="sxs-lookup"><span data-stu-id="2f91b-126">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="2f91b-127">httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="2f91b-127">httpGetUrl</span></span>|<span data-ttu-id="2f91b-128">URI indiquant l'adresse utilisée pour publier les métadonnées correspondant à la récupération à l'aide d'une demande HTTP/Get.</span><span class="sxs-lookup"><span data-stu-id="2f91b-128">A Uri that specifies the address at which the metadata is published for retrieval using an HTTP/Get request.</span></span> <span data-ttu-id="2f91b-129">Si l'URI relatif est spécifié, il sera traité comme étant relatif à l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="2f91b-129">If a relative Uri is specified it will be treated as relative to the service’s base address.</span></span>|  
|<span data-ttu-id="2f91b-130">httpsGetBinding</span><span class="sxs-lookup"><span data-stu-id="2f91b-130">httpsGetBinding</span></span>|<span data-ttu-id="2f91b-131">Chaîne qui spécifie le type de la liaison qui sera utilisée pour la récupération de métadonnées via HTTPS GET.</span><span class="sxs-lookup"><span data-stu-id="2f91b-131">A string that specifies the type of the binding that will be used for metadata retrieval via HTTPS GET.</span></span> <span data-ttu-id="2f91b-132">Ce paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="2f91b-132">This setting is optional.</span></span> <span data-ttu-id="2f91b-133">En l'absence de spécification, les liaisons par défaut seront utilisées.</span><span class="sxs-lookup"><span data-stu-id="2f91b-133">If it is not specified, the default bindings will be used.</span></span><br /><br /> <span data-ttu-id="2f91b-134">La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="2f91b-134">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="2f91b-135">En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f91b-135">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>|  
|<span data-ttu-id="2f91b-136">httpsGetBindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="2f91b-136">httpsGetBindingConfiguration</span></span>|<span data-ttu-id="2f91b-137">Chaîne qui définit le nom de la liaison spécifiée dans l’attribut `httpsGetBinding`, qui fait référence aux informations de configuration supplémentaires de cette liaison.</span><span class="sxs-lookup"><span data-stu-id="2f91b-137">A string that sets the name of the binding that is specified in the `httpsGetBinding` attribute, which references to the additional configuration information of this binding.</span></span> <span data-ttu-id="2f91b-138">Le même nom doit être défini dans la section `<bindings>`.</span><span class="sxs-lookup"><span data-stu-id="2f91b-138">The same name must be defined in the `<bindings>` section.</span></span>|  
|<span data-ttu-id="2f91b-139">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="2f91b-139">httpsGetEnabled</span></span>|<span data-ttu-id="2f91b-140">Valeur booléenne indiquant si les métadonnées de service correspondant à la récupération doivent être publiées à l'aide d'une demande HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="2f91b-140">A Boolean value that specifies whether to publish service metadata for retrieval using an HTTPS/Get request.</span></span> <span data-ttu-id="2f91b-141">Par défaut, il s’agit de `false`.</span><span class="sxs-lookup"><span data-stu-id="2f91b-141">The default is `false`.</span></span><br /><br /> <span data-ttu-id="2f91b-142">Si l'attribut httpsGetUrl n'est pas spécifié, l'adresse utilisée pour publier les métadonnées est celle du service à laquelle est ajouté le suffixe « ? wsdl ».</span><span class="sxs-lookup"><span data-stu-id="2f91b-142">If the httpsGetUrl attribute is not specified, the address at which the metadata is published is the service address plus a "?wsdl".</span></span> <span data-ttu-id="2f91b-143">Par exemple, si l’adresse du service est « https://localhost:8080/CalculatorService », l’adresse des métadonnées http/obtenir est « https://localhost:8080/CalculatorService?wsdl ».</span><span class="sxs-lookup"><span data-stu-id="2f91b-143">For example, if the service address is "https://localhost:8080/CalculatorService", the HTTP/Get metadata address is "https://localhost:8080/CalculatorService?wsdl".</span></span><br /><br /> <span data-ttu-id="2f91b-144">Si cette propriété est `false` , ou si l’adresse du service n’est pas basée sur http ou HTTPS, «  ? WSDL » est ignoré.</span><span class="sxs-lookup"><span data-stu-id="2f91b-144">If this property is `false`, or the address of the service is not based on HTTP or HTTPS, "?wsdl" is ignored.</span></span>|  
|<span data-ttu-id="2f91b-145">httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="2f91b-145">httpsGetUrl</span></span>|<span data-ttu-id="2f91b-146">URI indiquant l'adresse utilisée pour publier les métadonnées afin d'effectuer une récupération à l'aide d'une demande HTTPS/Get.</span><span class="sxs-lookup"><span data-stu-id="2f91b-146">A Uri that specifies the address at which the metadata is published for retrieval using an HTTPS/Get request.</span></span>|  
|<span data-ttu-id="2f91b-147">policyVersion</span><span class="sxs-lookup"><span data-stu-id="2f91b-147">policyVersion</span></span>|<span data-ttu-id="2f91b-148">Chaîne indiquant la version de la spécification WS-Policy utilisée.</span><span class="sxs-lookup"><span data-stu-id="2f91b-148">A string that specifies the version of the WS-Policy specification being used.</span></span> <span data-ttu-id="2f91b-149">Cet attribut est de type <xref:System.ServiceModel.Description.PolicyVersion>.</span><span class="sxs-lookup"><span data-stu-id="2f91b-149">This attribute is of type <xref:System.ServiceModel.Description.PolicyVersion>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2f91b-150">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="2f91b-150">Child Elements</span></span>  

 <span data-ttu-id="2f91b-151">None</span><span class="sxs-lookup"><span data-stu-id="2f91b-151">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2f91b-152">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="2f91b-152">Parent Elements</span></span>  
  
|<span data-ttu-id="2f91b-153">Élément</span><span class="sxs-lookup"><span data-stu-id="2f91b-153">Element</span></span>|<span data-ttu-id="2f91b-154">Description</span><span class="sxs-lookup"><span data-stu-id="2f91b-154">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2f91b-155">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="2f91b-155">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f91b-156">Notes</span><span class="sxs-lookup"><span data-stu-id="2f91b-156">Remarks</span></span>  

 <span data-ttu-id="2f91b-157">Cet élément de configuration permet de contrôler les métadonnées qui publient les fonctionnalités d’un service.</span><span class="sxs-lookup"><span data-stu-id="2f91b-157">This configuration element allows you to control the metadata publishing features of a service.</span></span> <span data-ttu-id="2f91b-158">Pour empêcher la divulgation non intentionnelle de métadonnées de service potentiellement sensibles, la configuration par défaut pour les services Windows Communication Foundation (WCF) désactive la publication de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2f91b-158">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="2f91b-159">Ce comportement est sécurisé par défaut, mais il signifie également que vous ne pouvez pas utiliser d'outil d'importation de métadonnées (tel que Svcutil.exe) pour générer le code client requis pour appeler le service, à moins que le comportement de publication des métadonnées du service soit activé explicitement dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="2f91b-159">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span> <span data-ttu-id="2f91b-160">À l'aide de cet élément de configuration, vous pouvez activer ce comportement de publication pour votre service.</span><span class="sxs-lookup"><span data-stu-id="2f91b-160">Using this configuration element, you can enable this publishing behavior for your service.</span></span>  
  
 <span data-ttu-id="2f91b-161">Pour obtenir un exemple détaillé de la configuration de ce comportement, consultez [comportement de publication des métadonnées](../../../wcf/samples/metadata-publishing-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="2f91b-161">For a detailed example of configuring this behavior, see [Metadata Publishing Behavior](../../../wcf/samples/metadata-publishing-behavior.md).</span></span>  
  
 <span data-ttu-id="2f91b-162">Les attributs facultatifs `httpGetBinding` et `httpsGetBinding` vous permettent de configurer les liaisons utilisées pour la récupération de métadonnées via HTTP GET (ou HTTPS GET).</span><span class="sxs-lookup"><span data-stu-id="2f91b-162">The optional `httpGetBinding` and `httpsGetBinding` attributes allow you to configure the bindings used for metadata retrieval via HTTP GET (or HTTPS GET).</span></span> <span data-ttu-id="2f91b-163">S’ils ne sont pas spécifiés, les liaisons par défaut (`HttpTransportBindingElement` dans le cas de HTTP et `HttpsTransportBindingElement` dans le cas de HTTPS) sont utilisées pour la récupération des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="2f91b-163">If they are not specified, the default bindings (`HttpTransportBindingElement`, in the case of HTTP and `HttpsTransportBindingElement`, in the case of HTTPS) are used for metadata retrieval as appropriate.</span></span> <span data-ttu-id="2f91b-164">Notez que vous ne pouvez pas utiliser ces attributs avec les liaisons WCF intégrées.</span><span class="sxs-lookup"><span data-stu-id="2f91b-164">Notice that you cannot use these attributes with the built-in WCF bindings.</span></span> <span data-ttu-id="2f91b-165">La prise en charge n'est assurée que pour les liaisons comportant des éléments de liaison internes qui prennent en charge <xref:System.ServiceModel.Channels.IReplyChannel>.</span><span class="sxs-lookup"><span data-stu-id="2f91b-165">Only bindings with inner binding elements that support <xref:System.ServiceModel.Channels.IReplyChannel> will be supported.</span></span> <span data-ttu-id="2f91b-166">En outre, la propriété <xref:System.ServiceModel.Channels.MessageVersion> de la liaison doit être <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f91b-166">Additionally, the <xref:System.ServiceModel.Channels.MessageVersion> property of the binding must be <xref:System.ServiceModel.Channels.MessageVersion.None%2A>.</span></span>  
  
 <span data-ttu-id="2f91b-167">Pour éviter l'exposition d'un service aux utilisateurs malveillants, il est possible de sécuriser le transfert à l'aide du mécanisme HTTPS (SSL over HTTP).</span><span class="sxs-lookup"><span data-stu-id="2f91b-167">To reduce the exposure of a service to malicious users, it is possible to secure the transfer using the SSL over HTTP (HTTPS) mechanism.</span></span> <span data-ttu-id="2f91b-168">Pour ce faire, vous devez d'abord lier un certificat X.509 approprié à un port spécifique sur l'ordinateur qui héberge le service.</span><span class="sxs-lookup"><span data-stu-id="2f91b-168">To do so, you must first bind a suitable X.509 certificate to a specific port on the computer that is hosting the service.</span></span> <span data-ttu-id="2f91b-169">(Pour plus d’informations, consultez [utilisation des certificats](../../../wcf/feature-details/working-with-certificates.md).) Ensuite, ajoutez cet élément à la configuration du service et affectez à l’attribut la valeur `httpsGetEnabled` `true` .</span><span class="sxs-lookup"><span data-stu-id="2f91b-169">(For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).) Second, add this element to the service configuration and set the `httpsGetEnabled` attribute to `true`.</span></span> <span data-ttu-id="2f91b-170">Enfin, affectez l'URL du point de terminaison des métadonnées du service à l'attribut `httpsGetUrl`, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="2f91b-170">Finally, set the `httpsGetUrl` attribute to the URL of the service metadata endpoint, as shown in the following example.</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="NewBehavior">
      <serviceMetadata httpsGetEnabled="true"
                       httpsGetUrl="https://myComputerName/myEndpoint" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="example"></a><span data-ttu-id="2f91b-171">Exemple</span><span class="sxs-lookup"><span data-stu-id="2f91b-171">Example</span></span>  

 <span data-ttu-id="2f91b-172">L’exemple suivant configure un service pour exposer des métadonnées à l’aide de l' \<serviceMetadata> élément.</span><span class="sxs-lookup"><span data-stu-id="2f91b-172">The following example configure a service to expose metadata by using the \<serviceMetadata> element.</span></span> <span data-ttu-id="2f91b-173">Il configure également un point de terminaison afin d'exposer le contrat `IMetadataExchange` comme implémentation d'un protocole WS-MetadataExchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="2f91b-173">It also configures an endpoint to expose the `IMetadataExchange` contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="2f91b-174">L’exemple utilise `mexHttpBinding`, qui est une liaison standard équivalente à `wsHttpBinding` dans laquelle le mode de sécurité a la valeur `None`.</span><span class="sxs-lookup"><span data-stu-id="2f91b-174">The example uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="2f91b-175">Une adresse relative de « MEX » est utilisée dans le point de terminaison, qui, lorsqu’elle est résolue par rapport à l’adresse de base des services, se traduit par une adresse de point de terminaison `http://localhost/servicemodelsamples/service.svc/mex` .</span><span class="sxs-lookup"><span data-stu-id="2f91b-175">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of `http://localhost/servicemodelsamples/service.svc/mex`.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex
             To expose the IMetadataExchange contract, you must enable the serviceMetadata behavior as demonstrated below. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <!-- The serviceMetadata behavior publishes metadata through the IMetadataExchange contract. When this behavior is
               present, you can expose this contract through an endpoint as shown above. Setting httpGetEnabled to true publishes
               the service's WSDL at the <baseaddress>?wsdl eg. http://localhost/servicemodelsamples/service.svc?wsdl -->
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="2f91b-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2f91b-176">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceMetadataPublishingElement>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- [<span data-ttu-id="2f91b-177">Comportements de sécurité</span><span class="sxs-lookup"><span data-stu-id="2f91b-177">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="2f91b-178">Metadata Publishing Behavior</span><span class="sxs-lookup"><span data-stu-id="2f91b-178">Metadata Publishing Behavior</span></span>](../../../wcf/samples/metadata-publishing-behavior.md)
