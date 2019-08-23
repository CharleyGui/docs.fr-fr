---
title: Configuration des services à l'aide de fichiers de configuration
ms.date: 03/30/2017
helpviewer_keywords:
- configuring services [WCF]
ms.assetid: c9c8cd32-2c9d-4541-ad0d-16dff6bd2a00
ms.openlocfilehash: 68b427a81104d0f5102915002025103ef8d35dc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928594"
---
# <a name="configuring-services-using-configuration-files"></a><span data-ttu-id="0a795-102">Configuration des services à l'aide de fichiers de configuration</span><span class="sxs-lookup"><span data-stu-id="0a795-102">Configuring Services Using Configuration Files</span></span>
<span data-ttu-id="0a795-103">La configuration d’un service Windows Communication Foundation (WCF) avec un fichier de configuration vous donne la possibilité de fournir des données sur le point de terminaison et le comportement de service au point de déploiement au lieu de le faire au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="0a795-103">Configuring a Windows Communication Foundation (WCF) service with a configuration file gives you the flexibility of providing endpoint and service behavior data at the point of deployment instead of at design time.</span></span> <span data-ttu-id="0a795-104">Cette rubrique esquisse les principales techniques disponibles.</span><span class="sxs-lookup"><span data-stu-id="0a795-104">This topic outlines the primary techniques available.</span></span>  
  
 <span data-ttu-id="0a795-105">Un service WCF peut être configuré à l’aide de la technologie de configuration .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a795-105">A WCF service is configurable using the .NET Framework configuration technology.</span></span> <span data-ttu-id="0a795-106">Le plus souvent, les éléments XML sont ajoutés au fichier Web. config pour un site Internet Information Services (IIS) qui héberge un service WCF.</span><span class="sxs-lookup"><span data-stu-id="0a795-106">Most commonly, XML elements are added to the Web.config file for an Internet Information Services (IIS) site that hosts a WCF service.</span></span> <span data-ttu-id="0a795-107">Les éléments vous permettent de modifier des détails, tels que les adresses de point de terminaison (les adresses réelles qui communiquent avec le service) à partir de chaque ordinateur individuel.</span><span class="sxs-lookup"><span data-stu-id="0a795-107">The elements allow you to change details such as the endpoint addresses (the actual addresses used to communicate with the service) on a machine-by-machine basis.</span></span> <span data-ttu-id="0a795-108">En outre, WCF comprend plusieurs éléments fournis par le système qui vous permettent de sélectionner rapidement les fonctionnalités les plus basiques pour un service.</span><span class="sxs-lookup"><span data-stu-id="0a795-108">In addition, WCF includes several system-provided elements that allow you to quickly select the most basic features for a service.</span></span> <span data-ttu-id="0a795-109">À compter [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)]de, WCF est fourni avec un nouveau modèle de configuration par défaut qui simplifie les exigences de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="0a795-109">Starting with [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)], WCF comes with a new default configuration model that simplifies WCF configuration requirements.</span></span> <span data-ttu-id="0a795-110">Si vous ne fournissez aucune configuration WCF pour un service particulier, le runtime configure automatiquement votre service avec certains points de terminaison standard et la liaison/comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="0a795-110">If you do not provide any WCF configuration for a particular service, the runtime automatically configures your service with some standard endpoints and default binding/behavior.</span></span> <span data-ttu-id="0a795-111">Dans la pratique, l’écriture de la configuration est une partie importante de la programmation des applications WCF.</span><span class="sxs-lookup"><span data-stu-id="0a795-111">In practice, writing configuration is a major part of programming WCF applications.</span></span>  
  
 <span data-ttu-id="0a795-112">Pour plus d’informations, consultez [Configuration des liaisons pour les services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0a795-112">For more information, see [Configuring Bindings for Services](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md).</span></span> <span data-ttu-id="0a795-113">Pour obtenir la liste des éléments les plus couramment utilisés, consultez [liaisons fournies](../../../docs/framework/wcf/system-provided-bindings.md)par le système.</span><span class="sxs-lookup"><span data-stu-id="0a795-113">For a list of the most commonly used elements, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="0a795-114">Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](../../../docs/framework/wcf/simplified-configuration.md) et [Configuration simplifiée pour les services WCF](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0a795-114">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0a795-115">Si vous déployez des scénarios côte à côte où deux versions différentes d'un service sont déployées, vous devez spécifier les noms partiels des assemblys référencés dans les fichiers de configuration.</span><span class="sxs-lookup"><span data-stu-id="0a795-115">When deploying side by side scenarios where two different versions of a service are deployed, it is necessary to specify partial names of assemblies referenced in configuration files.</span></span> <span data-ttu-id="0a795-116">En effet, le fichier de configuration est partagé entre toutes les versions d'un service et elles peuvent s'exécuter sous différentes versions du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a795-116">This is because the configuration file is shared across all versions of a service and they could be running under different versions of the .NET Framework.</span></span>  
  
## <a name="systemconfiguration-webconfig-and-appconfig"></a><span data-ttu-id="0a795-117">System. Configuration: Web. config et App. config</span><span class="sxs-lookup"><span data-stu-id="0a795-117">System.Configuration: Web.config and App.config</span></span>  
 <span data-ttu-id="0a795-118">WCF utilise le système de configuration System. Configuration du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0a795-118">WCF uses the System.Configuration configuration system of the .NET Framework.</span></span>  
  
 <span data-ttu-id="0a795-119">Quand vous configurez un service dans Visual Studio, utilisez un fichier Web. config ou un fichier app. config pour spécifier les paramètres.</span><span class="sxs-lookup"><span data-stu-id="0a795-119">When configuring a service in Visual Studio, use either a Web.config file or an App.config file to specify the settings.</span></span> <span data-ttu-id="0a795-120">Le choix du nom de fichier de configuration est déterminé par l'environnement d'hébergement que vous choisissez pour le service.</span><span class="sxs-lookup"><span data-stu-id="0a795-120">The choice of the configuration file name is determined by the hosting environment you choose for the service.</span></span> <span data-ttu-id="0a795-121">Si vous utilisez IIS pour héberger votre service, utilisez un fichier Web.config.</span><span class="sxs-lookup"><span data-stu-id="0a795-121">If you are using IIS to host your service, use a Web.config file.</span></span> <span data-ttu-id="0a795-122">Si vous utilisez tout autre environnement d'hébergement, utilisez un fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="0a795-122">If you are using any other hosting environment, use an App.config file.</span></span>  
  
 <span data-ttu-id="0a795-123">Dans Visual Studio, le fichier nommé App. config est utilisé pour créer le fichier de configuration final.</span><span class="sxs-lookup"><span data-stu-id="0a795-123">In Visual Studio, the file named App.config is used to create the final configuration file.</span></span> <span data-ttu-id="0a795-124">Le nom final réellement utilisé pour la configuration dépend du nom de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="0a795-124">The final name actually used for the configuration depends on the assembly name.</span></span> <span data-ttu-id="0a795-125">Par exemple, un assembly nommé "Cohowinery.exe" porte le nom de fichier de configuration final "Cohowinery.exe.config".</span><span class="sxs-lookup"><span data-stu-id="0a795-125">For example, an assembly named "Cohowinery.exe" has a final configuration file name of "Cohowinery.exe.config".</span></span> <span data-ttu-id="0a795-126">Toutefois, vous devez seulement modifier le fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="0a795-126">However, you only need to modify the App.config file.</span></span> <span data-ttu-id="0a795-127">Les modifications apportées à ce fichier sont automatiquement répercutées dans le fichier final de configuration de l'application, à la compilation.</span><span class="sxs-lookup"><span data-stu-id="0a795-127">Changes made to that file are automatically made to the final application configuration file at compile time.</span></span>  
  
 <span data-ttu-id="0a795-128">Pour utiliser un fichier App.config, le système de configuration fusionne le fichier App.config avec le contenu du fichier Machine.config lorsque l'application démarre et la configuration est appliquée.</span><span class="sxs-lookup"><span data-stu-id="0a795-128">In using an App.config, file the configuration system merges the App.config file with content of the Machine.config file when the application starts and the configuration is applied.</span></span> <span data-ttu-id="0a795-129">Ce mécanisme autorise la définition de paramètres à l'échelle de l'ordinateur dans le fichier Machine.config.</span><span class="sxs-lookup"><span data-stu-id="0a795-129">This mechanism allows machine-wide settings to be defined in the Machine.config file.</span></span> <span data-ttu-id="0a795-130">Le fichier App.config peut être utilisé pour substituer les paramètres du fichier Machine.config ; vous pouvez également verrouiller les paramètres dans le fichier Machine.config afin qu'ils soient utilisés.</span><span class="sxs-lookup"><span data-stu-id="0a795-130">The App.config file can be used to override the settings of the Machine.config file; you can also lock in the settings in Machine.config file so that they get used.</span></span> <span data-ttu-id="0a795-131">Dans le cas de Web.config, le système de configuration fusionne les fichiers Web.config dans tous les répertoires qui mènent au répertoire de l'application dans la configuration qui est appliquée.</span><span class="sxs-lookup"><span data-stu-id="0a795-131">In the Web.config case, the configuration system merges the Web.config files in all directories leading up to the application directory into the configuration that gets applied.</span></span> <span data-ttu-id="0a795-132">Pour plus d’informations sur la configuration et les priorités de paramètres, consultez <xref:System.Configuration> les rubriques de l’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="0a795-132">For more information about configuration and the setting priorities, see topics in the <xref:System.Configuration> namespace.</span></span>  
  
## <a name="major-sections-of-the-configuration-file"></a><span data-ttu-id="0a795-133">Sections majeures du fichier de configuration</span><span class="sxs-lookup"><span data-stu-id="0a795-133">Major Sections of the Configuration File</span></span>  
 <span data-ttu-id="0a795-134">Les sections principales dans le fichier de configuration incluent les éléments suivants.</span><span class="sxs-lookup"><span data-stu-id="0a795-134">The main sections in the configuration file include the following elements.</span></span>  
  
```xml  
<system.ServiceModel>  
  
   <services>  
   <!-- Define the service endpoints. This section is optional in the new  
    default configuration model in .NET Framework 4. -->  
      <service>  
         <endpoint/>  
      </service>  
   </services>  
  
   <bindings>  
   <!-- Specify one or more of the system-provided binding elements,  
    for example, <basicHttpBinding> -->   
   <!-- Alternatively, <customBinding> elements. -->  
      <binding>  
      <!-- For example, a <BasicHttpBinding> element. -->  
      </binding>  
   </bindings>  
  
   <behaviors>  
   <!-- One or more of the system-provided or custom behavior elements. -->  
      <behavior>  
      <!-- For example, a <throttling> element. -->  
      </behavior>  
   </behaviors>  
  
</system.ServiceModel>  
```  
  
> [!NOTE]
> <span data-ttu-id="0a795-135">Les sections de liaison et de comportement sont facultatives et sont incluses uniquement si besoin est.</span><span class="sxs-lookup"><span data-stu-id="0a795-135">The bindings and behaviors sections are optional and are only included if required.</span></span>  
  
### <a name="the-services-element"></a><span data-ttu-id="0a795-136">Élément \<> Services</span><span class="sxs-lookup"><span data-stu-id="0a795-136">The \<services> Element</span></span>  
 <span data-ttu-id="0a795-137">L'élément `services` contient les caractéristiques pour tous les services que l'application héberge.</span><span class="sxs-lookup"><span data-stu-id="0a795-137">The `services` element contains the specifications for all services the application hosts.</span></span> <span data-ttu-id="0a795-138">Depuis l'apparition du modèle de configuration simplifié dans [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], cette section est facultative.</span><span class="sxs-lookup"><span data-stu-id="0a795-138">Starting with the simplified configuration model in [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], this section is optional.</span></span>  
  
 [<span data-ttu-id="0a795-139">\<services></span><span class="sxs-lookup"><span data-stu-id="0a795-139">\<services></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/services.md)  
  
### <a name="the-service-element"></a><span data-ttu-id="0a795-140">Élément \<de > de service</span><span class="sxs-lookup"><span data-stu-id="0a795-140">The \<service> Element</span></span>  
 <span data-ttu-id="0a795-141">Chaque service a les attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="0a795-141">Each service has these attributes:</span></span>  
  
- <span data-ttu-id="0a795-142">`name`.</span><span class="sxs-lookup"><span data-stu-id="0a795-142">`name`.</span></span> <span data-ttu-id="0a795-143">Spécifie le type qui fournit une implémentation d'un contrat de service.</span><span class="sxs-lookup"><span data-stu-id="0a795-143">Specifies the type that provides an implementation of a service contract.</span></span> <span data-ttu-id="0a795-144">Il s'agit d'un nom complet composé de l'espace de noms, d'un point et du nom du type.</span><span class="sxs-lookup"><span data-stu-id="0a795-144">This is a fully qualified name which consists of the namespace, a period, and then the type name.</span></span> <span data-ttu-id="0a795-145">Par exemple, `"MyNameSpace.myServiceType"`.</span><span class="sxs-lookup"><span data-stu-id="0a795-145">For example `"MyNameSpace.myServiceType"`.</span></span>  
  
- <span data-ttu-id="0a795-146">`behaviorConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="0a795-146">`behaviorConfiguration`.</span></span> <span data-ttu-id="0a795-147">Spécifie le nom de l'un des éléments `behavior` recherché dans l'élément `behaviors` .</span><span class="sxs-lookup"><span data-stu-id="0a795-147">Specifies the name of one of the `behavior` elements found in the `behaviors` element.</span></span> <span data-ttu-id="0a795-148">Le comportement spécifié gouverne des actions comme l'autorisation de l'emprunt d'identité par le service.</span><span class="sxs-lookup"><span data-stu-id="0a795-148">The specified behavior governs actions such as whether the service allows impersonation.</span></span> <span data-ttu-id="0a795-149">Si sa valeur correspond au nom vide ou qu'aucun `behaviorConfiguration` n'est fourni, l'ensemble de comportements de service par défaut est ajouté au service.</span><span class="sxs-lookup"><span data-stu-id="0a795-149">If its value is the empty name or no `behaviorConfiguration` is provided then the default set of service behaviors is added to the service.</span></span>  
  
- [<span data-ttu-id="0a795-150">\<service></span><span class="sxs-lookup"><span data-stu-id="0a795-150">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)  
  
### <a name="the-endpoint-element"></a><span data-ttu-id="0a795-151">Élément \<de point de terminaison ></span><span class="sxs-lookup"><span data-stu-id="0a795-151">The \<endpoint> Element</span></span>  
 <span data-ttu-id="0a795-152">Chaque point de terminaison requiert une adresse, une liaison et un contrat, représentés par les attributs suivants :</span><span class="sxs-lookup"><span data-stu-id="0a795-152">Each endpoint requires an address, a binding, and a contract, which are represented by the following attributes:</span></span>  
  
- <span data-ttu-id="0a795-153">`address`.</span><span class="sxs-lookup"><span data-stu-id="0a795-153">`address`.</span></span> <span data-ttu-id="0a795-154">Spécifie l'URI (Uniform Resource Identifier) du service, qui peut être une adresse absolue ou une adresse donnée relativement à l'adresse de base du service.</span><span class="sxs-lookup"><span data-stu-id="0a795-154">Specifies the service's Uniform Resource Identifier (URI), which can be an absolute address or one that is given relative to the base address of the service.</span></span> <span data-ttu-id="0a795-155">Si l'attribut a une valeur de chaîne vide, il indique que le point de terminaison est disponible à l'adresse de base spécifiée lors de la création de <xref:System.ServiceModel.ServiceHost> pour le service.</span><span class="sxs-lookup"><span data-stu-id="0a795-155">If set to an empty string, it indicates that the endpoint is available at the base address that is specified when creating the <xref:System.ServiceModel.ServiceHost> for the service.</span></span>  
  
- <span data-ttu-id="0a795-156">`binding`.</span><span class="sxs-lookup"><span data-stu-id="0a795-156">`binding`.</span></span> <span data-ttu-id="0a795-157">En général, spécifie une liaison fournie par le système comme <xref:System.ServiceModel.WSHttpBinding>, mais peut également spécifier une liaison définie par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="0a795-157">Typically specifies a system-provided binding like <xref:System.ServiceModel.WSHttpBinding>, but can also specify a user-defined binding.</span></span> <span data-ttu-id="0a795-158">La liaison spécifiée détermine le type de transport, de sécurité et d'encodage utilisé, et si des sessions fiables, des transactions ou la diffusion en continu sont pris en charge ou activés.</span><span class="sxs-lookup"><span data-stu-id="0a795-158">The binding specified determines the type of transport, security and encoding used, and whether reliable sessions, transactions, or streaming is supported or enabled.</span></span>  
  
- <span data-ttu-id="0a795-159">`bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="0a795-159">`bindingConfiguration`.</span></span> <span data-ttu-id="0a795-160">Si les valeurs par défaut d'une liaison doivent être modifiées, cela peut être fait en configurant l'élément `binding` approprié dans l'élément `bindings` .</span><span class="sxs-lookup"><span data-stu-id="0a795-160">If the default values of a binding must be modified, this can be done by configuring the appropriate `binding` element in the `bindings` element.</span></span> <span data-ttu-id="0a795-161">Cet attribut doit avoir la même valeur que l'attribut `name` de l'élément `binding` utilisé pour modifier les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="0a795-161">This attribute should be given the same value as the `name` attribute of the `binding` element that is used to change the defaults.</span></span> <span data-ttu-id="0a795-162">Si aucun nom n'est donné ou qu'aucun `bindingConfiguration` n'est spécifié dans la liaison, la liaison par défaut du type de liaison est utilisée dans le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0a795-162">If no name is given, or no `bindingConfiguration` is specified in the binding, then the default binding of the binding type is used in the endpoint.</span></span>  
  
- <span data-ttu-id="0a795-163">`contract`.</span><span class="sxs-lookup"><span data-stu-id="0a795-163">`contract`.</span></span> <span data-ttu-id="0a795-164">Spécifie l'interface qui définit le contrat.</span><span class="sxs-lookup"><span data-stu-id="0a795-164">Specifies the interface that defines the contract.</span></span> <span data-ttu-id="0a795-165">C'est l'interface implémentée dans le type Common Language Runtime (CLR) spécifié par l'attribut `name` de l'élément `service` .</span><span class="sxs-lookup"><span data-stu-id="0a795-165">This is the interface implemented in the common language runtime (CLR) type specified by the `name` attribute of the `service` element.</span></span>  
  
- [<span data-ttu-id="0a795-166">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="0a795-166">\<endpoint></span></span>](../configure-apps/file-schema/wcf/endpoint-element.md)  
  
### <a name="the-bindings-element"></a><span data-ttu-id="0a795-167">Élément \<de liaison ></span><span class="sxs-lookup"><span data-stu-id="0a795-167">The \<bindings> Element</span></span>  
 <span data-ttu-id="0a795-168">L'élément `bindings` contient les caractéristiques pour toutes les liaisons qui peuvent être utilisées par tout point de terminaison défini dans un service.</span><span class="sxs-lookup"><span data-stu-id="0a795-168">The `bindings` element contains the specifications for all bindings that can be used by any endpoint defined in any service.</span></span>  
  
 [<span data-ttu-id="0a795-169">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0a795-169">\<bindings></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
  
### <a name="the-binding-element"></a><span data-ttu-id="0a795-170">Élément \<de > de liaison</span><span class="sxs-lookup"><span data-stu-id="0a795-170">The \<binding> Element</span></span>  
 <span data-ttu-id="0a795-171">L'élément `binding` contenus dans l'élément `bindings` peuvent être une des liaisons fournies par le système (consultez [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) ou une liaison personnalisée (consultez [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="0a795-171">The `binding` elements contained in the `bindings` element can be either one of the system-provided bindings (see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md)) or a custom binding (see [Custom Bindings](../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="0a795-172">L'élément `binding` a un attribut `name` qui correspond la liaison avec le point de terminaison spécifié dans l'attribut `bindingConfiguration` de l'élément `endpoint` .</span><span class="sxs-lookup"><span data-stu-id="0a795-172">The `binding` element has a `name` attribute that correlates the binding with the endpoint specified in the `bindingConfiguration` attribute of the `endpoint` element.</span></span> <span data-ttu-id="0a795-173">Si aucun nom n'est spécifié, cette liaison correspond à la valeur par défaut de ce type de liaison.</span><span class="sxs-lookup"><span data-stu-id="0a795-173">If no name is specified then that binding corresponds to the default of that binding type.</span></span>  
  
<span data-ttu-id="0a795-174">Pour plus d’informations sur la configuration des services et des clients, consultez [Configuration des services WCF](configuring-services.md).</span><span class="sxs-lookup"><span data-stu-id="0a795-174">For more information about configuring services and clients, see [Configuring WCF services](configuring-services.md).</span></span>
  
 [<span data-ttu-id="0a795-175">\<binding></span><span class="sxs-lookup"><span data-stu-id="0a795-175">\<binding></span></span>](../../../docs/framework/misc/binding.md)  
  
### <a name="the-behaviors-element"></a><span data-ttu-id="0a795-176">Les \<comportements > élément</span><span class="sxs-lookup"><span data-stu-id="0a795-176">The \<behaviors> Element</span></span>  
 <span data-ttu-id="0a795-177">C'est un élément conteneur des éléments `behavior` qui définissent les comportements pour un service.</span><span class="sxs-lookup"><span data-stu-id="0a795-177">This is a container element for the `behavior` elements that define the behaviors for a service.</span></span>  
  
 [<span data-ttu-id="0a795-178">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="0a795-178">\<behaviors></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
  
### <a name="the-behavior-element"></a><span data-ttu-id="0a795-179">Élément \<de > de comportement</span><span class="sxs-lookup"><span data-stu-id="0a795-179">The \<behavior> Element</span></span>  
 <span data-ttu-id="0a795-180">Chaque `behavior` élément est identifié par un `name` attribut et fournit un comportement fourni par le système, tel que <`throttling`> ou un comportement personnalisé.</span><span class="sxs-lookup"><span data-stu-id="0a795-180">Each `behavior` element is identified by a `name` attribute and provides either a system-provided behavior, such as <`throttling`>, or a custom behavior.</span></span> <span data-ttu-id="0a795-181">Si aucun nom n'est donné, cet élément behavior correspond au service par défaut ou au comportement du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="0a795-181">If no name is given then that behavior element corresponds to the default service or endpoint behavior.</span></span>  
  
 [<span data-ttu-id="0a795-182">\<behavior></span><span class="sxs-lookup"><span data-stu-id="0a795-182">\<behavior></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md)  
  
## <a name="how-to-use-binding-and-behavior-configurations"></a><span data-ttu-id="0a795-183">Comment : utiliser les configurations de liaison et de comportement</span><span class="sxs-lookup"><span data-stu-id="0a795-183">How to Use Binding and Behavior Configurations</span></span>  
 <span data-ttu-id="0a795-184">WCF facilite le partage des configurations entre des points de terminaison à l’aide d’un système de référence dans la configuration.</span><span class="sxs-lookup"><span data-stu-id="0a795-184">WCF makes it easy to share configurations between endpoints using a reference system in configuration.</span></span> <span data-ttu-id="0a795-185">Plutôt qu'assigner directement des valeurs de configuration à un point de terminaison, les valeurs de configuration connexes à la liaison sont groupées dans les éléments `bindingConfiguration` dans la section `<binding>` .</span><span class="sxs-lookup"><span data-stu-id="0a795-185">Rather than directly assigning configuration values to an endpoint, binding-related configuration values are grouped in `bindingConfiguration` elements in the `<binding>` section.</span></span> <span data-ttu-id="0a795-186">Une configuration de liaison est un groupe nommé de paramètres sur une liaison.</span><span class="sxs-lookup"><span data-stu-id="0a795-186">A binding configuration is a named group of settings on a binding.</span></span> <span data-ttu-id="0a795-187">Les points de terminaison peuvent référencer ensuite l'élément `bindingConfiguration` par nom.</span><span class="sxs-lookup"><span data-stu-id="0a795-187">Endpoints can then reference the `bindingConfiguration` by name.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
 <system.serviceModel>  
  <bindings>  
    <basicHttpBinding>  
     <binding name="myBindingConfiguration1" closeTimeout="00:01:00" />  
     <binding name="myBindingConfiguration2" closeTimeout="00:02:00" />  
     <binding closeTimeout="00:03:00" />  <!-- Default binding for basicHttpBinding -->  
    </basicHttpBinding>  
     </bindings>  
     <services>  
      <service name="MyNamespace.myServiceType">  
       <endpoint   
          address="myAddress" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration1"  
          contract="MyContract"  />  
       <endpoint   
          address="myAddress2" binding="basicHttpBinding"   
          bindingConfiguration="myBindingConfiguration2"  
          contract="MyContract" />  
       <endpoint   
          address="myAddress3" binding="basicHttpBinding"   
          contract="MyContract" />  
       </service>  
      </services>  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0a795-188">L'attribut `name` de l'élément `bindingConfiguration` est défini dans l'élément `<binding>` .</span><span class="sxs-lookup"><span data-stu-id="0a795-188">The `name` of the `bindingConfiguration` is set in the `<binding>` element.</span></span> <span data-ttu-id="0a795-189">Doit être une chaîne unique dans l’étendue du type de liaison (dans ce cas, le [< BasicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)ou une valeur vide pour faire référence à la liaison par défaut). `name`</span><span class="sxs-lookup"><span data-stu-id="0a795-189">The `name` must be a unique string within the scope of the binding type—in this case the [<basicHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), or an empty value to refer to the default binding.</span></span> <span data-ttu-id="0a795-190">Le point de terminaison est relié à la configuration en affectant l'attribut `bindingConfiguration` à cette chaîne.</span><span class="sxs-lookup"><span data-stu-id="0a795-190">The endpoint links to the configuration by setting the `bindingConfiguration` attribute to this string.</span></span>  
  
 <span data-ttu-id="0a795-191">Un attribut `behaviorConfiguration` est implémenté de la même façon, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="0a795-191">A `behaviorConfiguration` is implemented the same way, as illustrated in the following sample.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myBehavior">  
           <callbackDebug includeExceptionDetailInFaults="true" />  
         </behavior>  
      </endpointBehaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="true" />  
        </behavior>  
      </serviceBehaviors>  
  
    </behaviors>  
    <services>  
     <service name="NewServiceType">  
       <endpoint   
          address="myAddress3" behaviorConfiguration="myBehavior"  
          binding="basicHttpBinding"  
          contract="MyContract" />  
      </service>  
    </services>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0a795-192">Notez que l'ensemble par défaut des comportements de service est ajouté au service.</span><span class="sxs-lookup"><span data-stu-id="0a795-192">Note that the default set of service behaviors are added to the service.</span></span> <span data-ttu-id="0a795-193">Ce système permet aux points de terminaison de partager des configurations communes sans redéfinir les paramètres.</span><span class="sxs-lookup"><span data-stu-id="0a795-193">This system allows endpoints to share common configurations without redefining the settings.</span></span> <span data-ttu-id="0a795-194">Si une étendue à l'échelle de l'ordinateur est requise, créez la configuration de la liaison ou du comportement dans Machine.config. Les paramètres de configuration sont disponibles dans tous les fichiers App.config.</span><span class="sxs-lookup"><span data-stu-id="0a795-194">If machine-wide scope is required, create the binding or behavior configuration in Machine.config. The configuration settings are available in all App.config files.</span></span> <span data-ttu-id="0a795-195">L' [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) facilite la création des configurations.</span><span class="sxs-lookup"><span data-stu-id="0a795-195">The [Configuration Editor Tool (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) makes it easy to create configurations.</span></span>  
  
## <a name="behavior-merge"></a><span data-ttu-id="0a795-196">Fusion des comportements</span><span class="sxs-lookup"><span data-stu-id="0a795-196">Behavior Merge</span></span>  
 <span data-ttu-id="0a795-197">La fonctionnalité de fusion des comportements facilite la gestion des comportements lorsque vous souhaitez définir des comportements communs à utiliser régulièrement.</span><span class="sxs-lookup"><span data-stu-id="0a795-197">The behavior merge feature makes it easier to manage behaviors when you want a set of common behaviors to be used consistently.</span></span> <span data-ttu-id="0a795-198">Elle vous permet de spécifier des comportements à différents niveaux de la hiérarchie de configuration et d'hériter les comportements de service de plusieurs niveaux de la hiérarchie de configuration.</span><span class="sxs-lookup"><span data-stu-id="0a795-198">This feature allows you to specify behaviors at different levels of the configuration hierarchy and have services inherit behaviors from multiple levels of the configuration hierarchy.</span></span> <span data-ttu-id="0a795-199">Pour illustrer le fonctionnement, supposons que vous disposez de la structure de répertoires virtuels suivante dans IIS :</span><span class="sxs-lookup"><span data-stu-id="0a795-199">To illustrate how this works assume you have the following virtual directory layout in IIS:</span></span>  
  
 `~\Web.config~\Service.svc~\Child\Web.config~\Child\Service.svc`
  
 <span data-ttu-id="0a795-200">Et votre `~\Web.config` fichier présente le contenu suivant:</span><span class="sxs-lookup"><span data-stu-id="0a795-200">And your `~\Web.config` file has the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceDebug includeExceptionDetailInFaults="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0a795-201">Votre fichier Web.config enfant qui se trouve à l'emplacement ~\Child\Web.config a le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="0a795-201">And you have a child Web.config located at ~\Child\Web.config with the following contents:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0a795-202">Le service situé à l'emplacement ~\Child\Service.svc se comportera comme s'il contenait les comportements serviceDebug et serviceMetadata.</span><span class="sxs-lookup"><span data-stu-id="0a795-202">The service located at ~\Child\Service.svc will behave as though it has both the serviceDebug and serviceMetadata behaviors.</span></span> <span data-ttu-id="0a795-203">Le service qui se trouve à l'emplacement ~\Service.svc aura uniquement le comportement serviceDebug.</span><span class="sxs-lookup"><span data-stu-id="0a795-203">The service located at ~\Service.svc will only have the serviceDebug behavior.</span></span> <span data-ttu-id="0a795-204">Les deux collections de comportements portant le même nom (dans ce cas la chaîne vide) sont fusionnées.</span><span class="sxs-lookup"><span data-stu-id="0a795-204">What happens is that the two behavior collections with the same name (in this case the empty string) are merged.</span></span>  
  
 <span data-ttu-id="0a795-205">Vous pouvez également effacer les collections de comportements à \<l’aide de la balise Clear > et supprimer des comportements individuels de \<la collection à l’aide de la balise Remove >.</span><span class="sxs-lookup"><span data-stu-id="0a795-205">You can also clear behavior collections by using the \<clear> tag and removed individual behaviors from the collection by using the \<remove> tag.</span></span> <span data-ttu-id="0a795-206">Par exemple, les deux configurations suivantes provoquent uniquement le comportement serviceMetadata du service enfant :</span><span class="sxs-lookup"><span data-stu-id="0a795-206">For example, the following two configuration results in the child service having only the serviceMetadata behavior:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <remove name="serviceDebug"/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <clear/>  
          <serviceMetadata httpGetEnabled="True" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0a795-207">La fusion des comportements est effectuée pour les collections de comportements sans nom, tel qu'illustré ci-dessus, ainsi que pour les collections de comportements nommées.</span><span class="sxs-lookup"><span data-stu-id="0a795-207">Behavior merge is done for nameless behavior collections as shown above and named behavior collections as well.</span></span>  
  
 <span data-ttu-id="0a795-208">Elle fonctionne dans l'environnement d'hébergement IIS, dans lequel les fichiers Web.config sont fusionnés hiérarchiquement avec le fichier Web.config racine et le fichier machine.config. Elle fonctionne aussi dans l'environnement d'application, où le fichier machine.config peut être fusionné avec le fichier App.config.</span><span class="sxs-lookup"><span data-stu-id="0a795-208">Behavior merge works in the IIS hosting environment, in which Web.config files merge hierarchically with the root Web.config file and machine.config. But it also works in the application environment, where machine.config can merge with the App.config file.</span></span>  
  
 <span data-ttu-id="0a795-209">La fusion des comportements s'applique à la fois aux comportements de points de terminaison et aux comportements de services dans une configuration.</span><span class="sxs-lookup"><span data-stu-id="0a795-209">Behavior merge applies to both endpoint behaviors and service behaviors in configuration.</span></span>  
  
 <span data-ttu-id="0a795-210">Si une collection de comportements enfants contient un comportement qui est déjà présent dans la collection de comportements parents, le comportement enfant remplace le comportement parent.</span><span class="sxs-lookup"><span data-stu-id="0a795-210">If a child behavior collection contains a behavior that’s already present in the parent behavior collection, the child behavior overrides the parent.</span></span> <span data-ttu-id="0a795-211">Par conséquent, si une collection de `<serviceMetadata httpGetEnabled="False" />` comportements parente avait et une `<serviceMetadata httpGetEnabled="True" />`collection de comportements enfants avait, le comportement enfant remplace le comportement parent dans la collection de comportements et httpGetEnabled serait «true».</span><span class="sxs-lookup"><span data-stu-id="0a795-211">So if a parent behavior collection had `<serviceMetadata httpGetEnabled="False" />` and a child behavior collection had `<serviceMetadata httpGetEnabled="True" />`, the child behavior would override the parent behavior in the behavior collection and httpGetEnabled would be "true".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a795-212">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0a795-212">See also</span></span>

- [<span data-ttu-id="0a795-213">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="0a795-213">Simplified Configuration</span></span>](../../../docs/framework/wcf/simplified-configuration.md)
- [<span data-ttu-id="0a795-214">Configuration des services WCF</span><span class="sxs-lookup"><span data-stu-id="0a795-214">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="0a795-215">\<service></span><span class="sxs-lookup"><span data-stu-id="0a795-215">\<service></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/service.md)
- [<span data-ttu-id="0a795-216">\<binding></span><span class="sxs-lookup"><span data-stu-id="0a795-216">\<binding></span></span>](../../../docs/framework/misc/binding.md)
