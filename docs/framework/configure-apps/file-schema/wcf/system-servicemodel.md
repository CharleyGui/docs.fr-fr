---
title: <system.serviceModel>
description: En savoir plus sur les éléments de configuration de ServiceModel WCF, qui vous permettent de configurer les applications clientes et de service WCF.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 44966ed9ee3abb3d1babdf09dd44f087376ada55
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91158680"
---
# \<system.serviceModel>

<span data-ttu-id="e145f-103">Cette section de configuration contient tous les éléments de configuration de l’Windows Communication Foundation (WCF) ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="e145f-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="e145f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e145f-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <behaviors>
  </behaviors>
  <bindings>
  </bindings>
  <client>
  </client>
  <comContracts>
  </comContracts>
  <commonBehaviors>
  </commonBehaviors>
  <diagnostics>
  </diagnostics>
  <extensions>
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>
  <serviceHostingEnvironment>
  </serviceHostingEnvironment>
  <services>
  </services>
  <standardEndpoints>
  </standardEndpoints>
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e145f-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="e145f-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e145f-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="e145f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e145f-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="e145f-107">Attributes</span></span>  

 <span data-ttu-id="e145f-108">None</span><span class="sxs-lookup"><span data-stu-id="e145f-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e145f-109">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="e145f-109">Child Elements</span></span>  
  
|<span data-ttu-id="e145f-110">Élément</span><span class="sxs-lookup"><span data-stu-id="e145f-110">Element</span></span>|<span data-ttu-id="e145f-111">Description</span><span class="sxs-lookup"><span data-stu-id="e145f-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="e145f-112">Cette section définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="e145f-112">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="e145f-113">Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services.</span><span class="sxs-lookup"><span data-stu-id="e145f-113">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="e145f-114">Chaque élément de comportement est identifié par son attribut `name` unique.</span><span class="sxs-lookup"><span data-stu-id="e145f-114">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="e145f-115">Cette section contient une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="e145f-115">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="e145f-116">Chaque entrée est identifiée par son `name` unique.</span><span class="sxs-lookup"><span data-stu-id="e145f-116">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="e145f-117">Les services utilisent les liaisons en les liant à l’aide de `name`.</span><span class="sxs-lookup"><span data-stu-id="e145f-117">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="e145f-118">Cette section contient la liste des points de terminaison utilisés par un client pour se connecter à un service.</span><span class="sxs-lookup"><span data-stu-id="e145f-118">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="e145f-119">Cette section définit des contrats COM activés pour interagir avec WCF et COM.</span><span class="sxs-lookup"><span data-stu-id="e145f-119">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="e145f-120">Cette section peut uniquement être définie dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="e145f-120">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="e145f-121">Elle définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="e145f-121">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="e145f-122">Chaque collection définit des éléments de comportement consommés respectivement par tous les services et points de terminaison WCF sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e145f-122">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="e145f-123">Si un comportement est défini dans les sections `<commonBehaviors>` et `<behaviors>`, le comportement dans la section \<behaviors> a la préférence.</span><span class="sxs-lookup"><span data-stu-id="e145f-123">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="e145f-124">Cette section contient les paramètres des fonctionnalités de diagnostic de WCF.</span><span class="sxs-lookup"><span data-stu-id="e145f-124">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="e145f-125">L'utilisateur peut activer/désactiver le suivi, les compteurs de performance et le fournisseur WMI et ajouter des filtres de messages personnalisés.</span><span class="sxs-lookup"><span data-stu-id="e145f-125">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="e145f-126">Cette section contient une collection d’extensions qui permettent à l’utilisateur de créer des liaisons, des comportements et d’autres aspects d’extensions définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e145f-126">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="e145f-127">Cette section définit un ensemble de mappages de protocole par défaut entre des schémas de protocole de transport (par exemple, http, net.tcp, net.pipe, etc.) et des liaisons WCF.</span><span class="sxs-lookup"><span data-stu-id="e145f-127">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="e145f-128">Cette section définit un ensemble de filtres de routage, qui déterminent le type de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu’un filtre correspond.</span><span class="sxs-lookup"><span data-stu-id="e145f-128">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="e145f-129">Cette section définit le type instancié par l'environnement d'hébergement de service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="e145f-129">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="e145f-130">Si cette section est vide, le type par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="e145f-130">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="e145f-131">Cette section contient une collection de services.</span><span class="sxs-lookup"><span data-stu-id="e145f-131">The section contains a collection of services.</span></span> <span data-ttu-id="e145f-132">Pour chaque service défini dans l'assembly, cet élément contient un élément `service` indiquant les paramètres du service.</span><span class="sxs-lookup"><span data-stu-id="e145f-132">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="e145f-133">Cette section définit une collection de points de terminaison standard, qui sont des points de terminaison préconfigurés réutilisables.</span><span class="sxs-lookup"><span data-stu-id="e145f-133">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="e145f-134">Un point de terminaison standard possède un ou plusieurs attributs d’adresse, de liaison et de contrat ayant une valeur fixe.</span><span class="sxs-lookup"><span data-stu-id="e145f-134">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="e145f-135">Par exemple, dans le point de terminaison de découverte, le contrat est fixe.</span><span class="sxs-lookup"><span data-stu-id="e145f-135">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="e145f-136">Vous pouvez également utiliser des points de terminaison standard pour étendre le point de terminaison de service avec de nouvelles propriétés, ce qui revient à définir des liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="e145f-136">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="e145f-137">Cette section définit les paramètres de suivi d’un service de Workflow.</span><span class="sxs-lookup"><span data-stu-id="e145f-137">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e145f-138">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="e145f-138">Parent Elements</span></span>  
  
|<span data-ttu-id="e145f-139">Élément</span><span class="sxs-lookup"><span data-stu-id="e145f-139">Element</span></span>|<span data-ttu-id="e145f-140">Description</span><span class="sxs-lookup"><span data-stu-id="e145f-140">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="e145f-141">Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.</span><span class="sxs-lookup"><span data-stu-id="e145f-141">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e145f-142">Notes</span><span class="sxs-lookup"><span data-stu-id="e145f-142">Remarks</span></span>  

 <span data-ttu-id="e145f-143">WCF n’ajoute pas d’éléments aux sections de configuration d’autres produits.</span><span class="sxs-lookup"><span data-stu-id="e145f-143">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="e145f-144">Les services WCF sont définis dans la `services` section du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="e145f-144">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="e145f-145">Un assembly peut contenir n'importe quel nombre de services.</span><span class="sxs-lookup"><span data-stu-id="e145f-145">An assembly can contain any number of services.</span></span> <span data-ttu-id="e145f-146">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="e145f-146">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="e145f-147">Cette section et son contenu définissent le contrat, le comportement et les points de terminaison du service en question.</span><span class="sxs-lookup"><span data-stu-id="e145f-147">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="e145f-148">Seul l'attribut `name` d'un service est requis.</span><span class="sxs-lookup"><span data-stu-id="e145f-148">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="e145f-149">Par défaut, le nom d'un service décrit le type CLR sous-jacent utilisé pour implémenter un service ; toutefois, vous pouvez modifier la propriété ConfigurationName d'un <xref:System.ServiceModel.ServiceContractAttribute> pour remplacer la spécification de type CLR.</span><span class="sxs-lookup"><span data-stu-id="e145f-149">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="e145f-150">L'attribut `behaviorConfiguration` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="e145f-150">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="e145f-151">Il identifie le comportement utilisé par un service.</span><span class="sxs-lookup"><span data-stu-id="e145f-151">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="e145f-152">Le comportement spécifié par cet attribut doit être lié à un comportement de service défini dans l'étendue du même fichier de configuration (c'est-à-dire le même fichier ou un fichier parent).</span><span class="sxs-lookup"><span data-stu-id="e145f-152">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="e145f-153">Chaque service expose un ou plusieurs points de terminaison définis dans un élément `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="e145f-153">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="e145f-154">Chaque point de terminaison possède sa propre adresse et sa propre liaison.</span><span class="sxs-lookup"><span data-stu-id="e145f-154">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="e145f-155">Toutes les liaisons utilisées dans le fichier de configuration doivent être définies dans l'étendue du fichier.</span><span class="sxs-lookup"><span data-stu-id="e145f-155">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="e145f-156">Les liaisons sont liées aux points de terminaison grâce à la combinaison des attributs `name` et `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="e145f-156">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="e145f-157">L’attribut `binding` définit la section dans laquelle la liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="e145f-157">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="e145f-158">L'attribut `bindingConfiguration` définit parmi les liaisons configurées figurant dans la section de liaison celle qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="e145f-158">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="e145f-159">Une section de liaison peut définir plusieurs liaisons configurées.</span><span class="sxs-lookup"><span data-stu-id="e145f-159">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e145f-160">Exemple</span><span class="sxs-lookup"><span data-stu-id="e145f-160">Example</span></span>  

 <span data-ttu-id="e145f-161">Voici un exemple de fichier de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="e145f-161">This is an example of a WCF configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <!-- List of Behaviors -->
    </behaviors>
    <client>
      <!-- List of Endpoints -->
    </client>
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
    </diagnostics>
    <serviceHostingEnvironment>
      <!-- List of entries -->
    </serviceHostingEnvironment>
    <comContracts>
      <!-- List of COM+ Contracts -->
    </comContracts>
    <services>
      <!-- List of Services -->
    </services>
    <bindings>
      <!-- List of Bindings -->
    </bindings>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="e145f-162">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e145f-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
