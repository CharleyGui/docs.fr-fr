---
title: Configuration de liaisons pour les services Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- binding configuration [WCF]
ms.assetid: 99a85fd8-f7eb-4a84-a93e-7721b37d415c
ms.openlocfilehash: 92f9457dd0c118c9a7c578a7088f66cdea1e5ad0
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320664"
---
# <a name="configuring-bindings-for-windows-communication-foundation-services"></a><span data-ttu-id="698ad-102">Configuration de liaisons pour les services Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="698ad-102">Configuring Bindings for Windows Communication Foundation Services</span></span>
<span data-ttu-id="698ad-103">Lorsque vous créez une application, vous souhaitez souvent confier des décisions à l'administrateur après le déploiement de l'application.</span><span class="sxs-lookup"><span data-stu-id="698ad-103">When creating an application, you often want to defer decisions to the administrator after the deployment of the application.</span></span> <span data-ttu-id="698ad-104">Par exemple, il n'existe souvent aucune façon de savoir à l'avance ce que sera une adresse de service ou un URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="698ad-104">For example, there is often no way of knowing in advance what a service address, or Uniform Resource Identifier (URI), will be.</span></span> <span data-ttu-id="698ad-105">Au lieu de d'encoder de manière irréversible une adresse, il est préférable de permettre à un administrateur de le faire après avoir créé un service.</span><span class="sxs-lookup"><span data-stu-id="698ad-105">Instead of hard-coding an address, it is preferable to allow an administrator to do so after creating a service.</span></span> <span data-ttu-id="698ad-106">Cette souplesse est obtenue par le biais de la configuration.</span><span class="sxs-lookup"><span data-stu-id="698ad-106">This flexibility is accomplished through configuration.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="698ad-107">Utilisez l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) avec le commutateur `/config` pour créer rapidement des fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="698ad-107">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) with the `/config` switch to quickly create configuration files.</span></span>  
  
## <a name="major-sections"></a><span data-ttu-id="698ad-108">Sections principales</span><span class="sxs-lookup"><span data-stu-id="698ad-108">Major Sections</span></span>  
 <span data-ttu-id="698ad-109">Le schéma de configuration Windows Communication Foundation (WCF) comprend les trois sections principales suivantes (`serviceModel`, `bindings` et `services`) :</span><span class="sxs-lookup"><span data-stu-id="698ad-109">The Windows Communication Foundation (WCF) configuration scheme includes the following three major sections (`serviceModel`, `bindings`, and `services`):</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <bindings>  
        </bindings>  
        <services>  
        </services>  
        <behaviors>  
        </behaviors>  
    </system.serviceModel>  
</configuration>  
```  
  
### <a name="servicemodel-elements"></a><span data-ttu-id="698ad-110">Éléments ServiceModel</span><span class="sxs-lookup"><span data-stu-id="698ad-110">ServiceModel Elements</span></span>  
 <span data-ttu-id="698ad-111">Vous pouvez utiliser la section délimitée par l’élément `system.ServiceModel` pour configurer un type de service avec un ou plusieurs points de terminaison, ainsi que des paramètres pour un service.</span><span class="sxs-lookup"><span data-stu-id="698ad-111">You can use the section bounded by the `system.ServiceModel` element to configure a service type with one or more endpoints, as well as settings for a service.</span></span> <span data-ttu-id="698ad-112">Ensuite, chaque point de terminaison peut être configuré avec une adresse, un contrat et une liaison.</span><span class="sxs-lookup"><span data-stu-id="698ad-112">Each endpoint can then be configured with an address, a contract, and a binding.</span></span> <span data-ttu-id="698ad-113">Pour plus d’informations sur les points de terminaison, consultez [vue d’ensemble](endpoint-creation-overview.md)de la création de points de terminaison.</span><span class="sxs-lookup"><span data-stu-id="698ad-113">For more information about endpoints, see [Endpoint Creation Overview](endpoint-creation-overview.md).</span></span> <span data-ttu-id="698ad-114">Si aucun point de terminaison n'est spécifié, le runtime ajoute des points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="698ad-114">If no endpoints are specified, the runtime adds default endpoints.</span></span> <span data-ttu-id="698ad-115">Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](simplified-configuration.md) et [Configuration simplifiée pour les services WCF](./samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="698ad-115">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](simplified-configuration.md) and [Simplified Configuration for WCF Services](./samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="698ad-116">Une liaison spécifie des transports (HTTP, TCP, canaux, Message Queuing ) et des protocoles (sécurité, fiabilité, flux de transaction) et se compose d’éléments de liaison, dont chacun spécifie un aspect de la manière dont un point de terminaison communique avec le monde.</span><span class="sxs-lookup"><span data-stu-id="698ad-116">A binding specifies transports (HTTP, TCP, pipes, Message Queuing) and protocols (Security, Reliability, Transaction flows) and consists of binding elements, each of which specifies an aspect of how an endpoint communicates with the world.</span></span>  
  
 <span data-ttu-id="698ad-117">Par exemple, la spécification de l’élément [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) indique d’utiliser le protocole http comme transport pour un point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="698ad-117">For example, specifying the [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) element indicates to use HTTP as the transport for an endpoint.</span></span> <span data-ttu-id="698ad-118">Cela permet de rattacher le point de terminaison au moment de l'exécution lorsque le service qui utilise ce point de terminaison est ouvert.</span><span class="sxs-lookup"><span data-stu-id="698ad-118">This is used to wire up the endpoint at run time when the service using this endpoint is opened.</span></span>  
  
 <span data-ttu-id="698ad-119">Il existe deux types de liaisons : les liaisons prédéfinies et les liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="698ad-119">There are two kinds of bindings: predefined and custom.</span></span> <span data-ttu-id="698ad-120">Les liaisons prédéfinies contiennent des combinaisons utiles d’éléments utilisés dans des scénarios courants.</span><span class="sxs-lookup"><span data-stu-id="698ad-120">Predefined bindings contain useful combinations of elements that are used in common scenarios.</span></span> <span data-ttu-id="698ad-121">Pour obtenir la liste des types de liaison prédéfinis fournis par WCF, consultez [liaisons fournies par le système](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="698ad-121">For a list of predefined binding types that WCF provides, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="698ad-122">Si aucune collection de liaison prédéfinie n’a la combinaison correcte de fonctionnalités dont une application de service a besoin, vous pouvez construire des liaisons personnalisées pour satisfaire les exigences de l’application.</span><span class="sxs-lookup"><span data-stu-id="698ad-122">If no predefined binding collection has the correct combination of features that a service application needs, you can construct custom bindings to meet the application's requirements.</span></span> <span data-ttu-id="698ad-123">Pour plus d’informations sur les liaisons personnalisées, consultez [\<customBinding >](../configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="698ad-123">For more information about custom bindings, see [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
 <span data-ttu-id="698ad-124">Les quatre exemples suivants illustrent les configurations de liaison les plus courantes utilisées pour configurer un service WCF.</span><span class="sxs-lookup"><span data-stu-id="698ad-124">The following four examples illustrate the most common binding configurations used for setting up a WCF service.</span></span>  
  
#### <a name="specifying-an-endpoint-to-use-a-binding-type"></a><span data-ttu-id="698ad-125">Spécification d’un point de terminaison pour utiliser un type de liaison</span><span class="sxs-lookup"><span data-stu-id="698ad-125">Specifying an Endpoint to Use a Binding Type</span></span>  
 <span data-ttu-id="698ad-126">Le premier exemple montre comment spécifier un point de terminaison configuré avec une adresse, un contrat et une liaison.</span><span class="sxs-lookup"><span data-stu-id="698ad-126">The first example illustrates how to specify an endpoint configured with an address, a contract, and a binding.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <!-- This section is optional with the default configuration introduced  
       in .NET Framework 4. -->  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
```  
  
 <span data-ttu-id="698ad-127">Dans cet exemple, l'attribut `name` indique à quel type de service la configuration est destinée.</span><span class="sxs-lookup"><span data-stu-id="698ad-127">In this example, the `name` attribute indicates which service type the configuration is for.</span></span> <span data-ttu-id="698ad-128">Lorsque vous créez un service dans votre code avec le contrat `HelloWorld`, il est initialisé avec tous les points de terminaison définis dans l'exemple de configuration.</span><span class="sxs-lookup"><span data-stu-id="698ad-128">When you create a service in your code with the `HelloWorld` contract, it is initialized with all of the endpoints defined in the example configuration.</span></span> <span data-ttu-id="698ad-129">Si l’assembly implémente un seul contrat de service, l’attribut `name` peut être omis, car le service utilise le seul type disponible.</span><span class="sxs-lookup"><span data-stu-id="698ad-129">If the assembly implements only one service contract, the `name` attribute can be omitted because the service uses the only available type.</span></span> <span data-ttu-id="698ad-130">L'attribut utilise une chaîne, qui doit être dans le format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span><span class="sxs-lookup"><span data-stu-id="698ad-130">The attribute takes a string, which must be in the format `Namespace.Class, AssemblyName, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null`</span></span>  
  
 <span data-ttu-id="698ad-131">L'attribut `address` spécifie l'URI que d'autres points de terminaison utilisent pour communiquer avec le service.</span><span class="sxs-lookup"><span data-stu-id="698ad-131">The `address` attribute specifies the URI that other endpoints use to communicate to the service.</span></span> <span data-ttu-id="698ad-132">L’URI peut être un chemin d’accès absolu ou relatif.</span><span class="sxs-lookup"><span data-stu-id="698ad-132">The URI can be either an absolute or relative path.</span></span> <span data-ttu-id="698ad-133">Si une adresse relative est fournie, l’hôte est censé fournir une adresse de base appropriée au schéma de transport utilisé dans la liaison.</span><span class="sxs-lookup"><span data-stu-id="698ad-133">If a relative address is provided, the host is expected to provide a base address that is appropriate for the transport scheme used in the binding.</span></span> <span data-ttu-id="698ad-134">Si une adresse n'est pas configurée, l'adresse de base est l'adresse pour ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="698ad-134">If an address is not configured, the base address is assumed to be the address for that endpoint.</span></span>  
  
 <span data-ttu-id="698ad-135">L'attribut `contract` spécifie le contrat que ce point de terminaison expose.</span><span class="sxs-lookup"><span data-stu-id="698ad-135">The `contract` attribute specifies the contract this endpoint is exposing.</span></span> <span data-ttu-id="698ad-136">Le type d'implémentation de service doit implémenter le type de contrat.</span><span class="sxs-lookup"><span data-stu-id="698ad-136">The service implementation type must implement the contract type.</span></span> <span data-ttu-id="698ad-137">Si une implémentation de service implémente un seul type de contrat, cette propriété peut alors être omise.</span><span class="sxs-lookup"><span data-stu-id="698ad-137">If a service implementation implements a single contract type, then this property can be omitted.</span></span>  
  
 <span data-ttu-id="698ad-138">L’attribut de `binding` sélectionne une liaison prédéfinie ou personnalisée à utiliser pour ce point de terminaison spécifique.</span><span class="sxs-lookup"><span data-stu-id="698ad-138">The `binding` attribute selects a predefined or custom binding to use for this specific endpoint.</span></span> <span data-ttu-id="698ad-139">Un point de terminaison qui ne sélectionne pas explicitement de liaison utilise la sélection de liaison par défaut, qui correspond à `BasicHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="698ad-139">An endpoint that does not explicitly select a binding uses the default binding selection, which is `BasicHttpBinding`.</span></span>  
  
#### <a name="modifying-a-predefined-binding"></a><span data-ttu-id="698ad-140">Modification d'une liaison prédéfinie</span><span class="sxs-lookup"><span data-stu-id="698ad-140">Modifying a Predefined Binding</span></span>  
 <span data-ttu-id="698ad-141">Dans l'exemple suivant, une liaison prédéfinie est modifiée.</span><span class="sxs-lookup"><span data-stu-id="698ad-141">In the following example, a predefined binding is modified.</span></span> <span data-ttu-id="698ad-142">Elle peut alors être utilisée pour configurer tout point de terminaison dans le service.</span><span class="sxs-lookup"><span data-stu-id="698ad-142">It can then be used to configure any endpoint in the service.</span></span> <span data-ttu-id="698ad-143">La liaison est modifiée en affectant 1 seconde à la valeur <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="698ad-143">The binding is modified by setting the <xref:System.ServiceModel.Configuration.IBindingConfigurationElement.ReceiveTimeout%2A> value to 1 second.</span></span> <span data-ttu-id="698ad-144">Notez que la propriété retourne un objet <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="698ad-144">Note that the property returns a <xref:System.TimeSpan> object.</span></span>  
  
 <span data-ttu-id="698ad-145">Cette liaison modifiée se trouve dans la section consacrée aux liaisons.</span><span class="sxs-lookup"><span data-stu-id="698ad-145">That altered binding is found in the bindings section.</span></span> <span data-ttu-id="698ad-146">Cette liaison modifiée peut maintenant être utilisée lors de la création de tout point de terminaison en définissant l'attribut `binding` dans l'élément `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="698ad-146">This altered binding can now be used when creating any endpoint by setting the `binding` attribute in the `endpoint` element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="698ad-147">Si vous donnez un nom particulier à la liaison, le `bindingConfiguration` spécifié dans le point de terminaison du service doit lui correspondre.</span><span class="sxs-lookup"><span data-stu-id="698ad-147">If you give a particular name to the binding, the `bindingConfiguration` specified in the service endpoint must match with it.</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
  <endpoint   
      address="/HelloWorld2/"  
      contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
      binding="basicHttpBinding" />
</service>  
<bindings>  
    <basicHttpBinding   
        receiveTimeout="00:00:01"  
    />  
</bindings>  
```  
  
## <a name="configuring-a-behavior-to-apply-to-a-service"></a><span data-ttu-id="698ad-148">Configuration d'un comportement à appliquer à un service</span><span class="sxs-lookup"><span data-stu-id="698ad-148">Configuring a Behavior to Apply to a Service</span></span>  
 <span data-ttu-id="698ad-149">Dans l'exemple ci-dessous, un comportement spécifique est configuré pour le type de service.</span><span class="sxs-lookup"><span data-stu-id="698ad-149">In the following example, a specific behavior is configured for the service type.</span></span> <span data-ttu-id="698ad-150">L’élément `ServiceMetadataBehavior` est utilisé pour permettre à l' [outil ServiceModel Metadata Utility (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) d’interroger le service et de générer des documents Web Services Description Language (WSDL) à partir des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="698ad-150">The `ServiceMetadataBehavior` element is used to enable the [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) to query the service and generate Web Services Description Language (WSDL) documents from the metadata.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="698ad-151">Si vous donnez un nom particulier au comportement, le `behaviorConfiguration` spécifié dans la section du point de terminaison ou du service doit lui correspondre.</span><span class="sxs-lookup"><span data-stu-id="698ad-151">If you give a particular name to the behavior, the `behaviorConfiguration` specified in the service or endpoint section must match it.</span></span>  
  
```xml  
<behaviors>  
    <behavior>  
        <ServiceMetadata httpGetEnabled="true" />   
    </behavior>  
</behaviors>  
<services>  
    <service   
       name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">
       <endpoint   
          address="http://computer:8080/Hello"  
          contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
          binding="basicHttpBinding" />
    </service>  
</services>  
```  
  
 <span data-ttu-id="698ad-152">La configuration précédente permet à un client d'appeler et d'obtenir les métadonnées du service typé « HelloWorld ».</span><span class="sxs-lookup"><span data-stu-id="698ad-152">The preceding configuration enables a client to call and get the metadata of the "HelloWorld" typed service.</span></span>  
  
 `svcutil /config:Client.exe.config http://computer:8080/Hello?wsdl`  
  
## <a name="specifying-a-service-with-two-endpoints-using-different-binding-values"></a><span data-ttu-id="698ad-153">Spécification d’un service avec deux points de terminaison qui utilisent des valeurs de liaison différentes</span><span class="sxs-lookup"><span data-stu-id="698ad-153">Specifying a Service with Two Endpoints Using Different Binding Values</span></span>  
 <span data-ttu-id="698ad-154">Dans ce dernier exemple, deux points de terminaison sont configurés pour le type de service `HelloWorld`.</span><span class="sxs-lookup"><span data-stu-id="698ad-154">In this last example, two endpoints are configured for the `HelloWorld` service type.</span></span> <span data-ttu-id="698ad-155">Chaque point de terminaison utilise un autre attribut `bindingConfiguration` personnalisé du même type de liaison (chacun modifie le `basicHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="698ad-155">Each endpoint uses a different customized  `bindingConfiguration` attribute of the same binding type (each modifies the `basicHttpBinding`).</span></span>  
  
```xml  
<service name="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null">  
    <endpoint  
        address="http://computer:8080/Hello1"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="shortTimeout" />
    <endpoint  
        address="http://computer:8080/Hello2"  
        contract="HelloWorld, IndigoConfig, Version=2.0.0.0, Culture=neutral, PublicKeyToken=null"  
        binding="basicHttpBinding"  
        bindingConfiguration="Secure" />
</service>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure">  
        <Security mode="Transport" />  
     </basicHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="698ad-156">Vous pouvez obtenir le même comportement à l'aide de la configuration par défaut en ajoutant une section `protocolMapping` et en configurant les liaisons comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="698ad-156">You can get the same behavior using the default configuration by adding a `protocolMapping` section and configuring the bindings as demonstrated in the following example.</span></span>  
  
```xml  
<protocolMapping>  
    <add scheme="http" binding="basicHttpBinding" bindingConfiguration="shortTimeout" />  
    <add scheme="https" binding="basicHttpBinding" bindingConfiguration="Secure" />  
</protocolMapping>  
<bindings>  
    <basicHttpBinding   
        name="shortTimeout"  
        timeout="00:00:00:01"   
     />  
     <basicHttpBinding   
        name="Secure" />  
        <Security mode="Transport" />  
</bindings>  
```  
  
## <a name="see-also"></a><span data-ttu-id="698ad-157">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="698ad-157">See also</span></span>

- [<span data-ttu-id="698ad-158">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="698ad-158">Simplified Configuration</span></span>](simplified-configuration.md)
- [<span data-ttu-id="698ad-159">Liaisons fournies par le système</span><span class="sxs-lookup"><span data-stu-id="698ad-159">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="698ad-160">Vue d’ensemble de la création de points de terminaison</span><span class="sxs-lookup"><span data-stu-id="698ad-160">Endpoint Creation Overview</span></span>](endpoint-creation-overview.md)
- [<span data-ttu-id="698ad-161">Utilisation de liaisons pour configurer des services et des clients</span><span class="sxs-lookup"><span data-stu-id="698ad-161">Using Bindings to Configure Services and Clients</span></span>](using-bindings-to-configure-services-and-clients.md)
