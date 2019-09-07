---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399452"
---
# <a name="systemservicemodel"></a><span data-ttu-id="94297-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="94297-102">\<system.serviceModel></span></span>
<span data-ttu-id="94297-103">Cette section de configuration contient tous les éléments de configuration de l’Windows Communication Foundation (WCF) ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="94297-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

<span data-ttu-id="94297-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="94297-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="94297-105">&nbsp;&nbsp; **\<System. serviceModel >**</span><span class="sxs-lookup"><span data-stu-id="94297-105">&nbsp;&nbsp;**\<system.serviceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94297-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94297-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94297-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="94297-107">Attributes and Elements</span></span>  
 <span data-ttu-id="94297-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="94297-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94297-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="94297-109">Attributes</span></span>  
 <span data-ttu-id="94297-110">Aucun</span><span class="sxs-lookup"><span data-stu-id="94297-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="94297-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="94297-111">Child Elements</span></span>  
  
|<span data-ttu-id="94297-112">Élément</span><span class="sxs-lookup"><span data-stu-id="94297-112">Element</span></span>|<span data-ttu-id="94297-113">Description</span><span class="sxs-lookup"><span data-stu-id="94297-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94297-114">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="94297-114">\<behaviors></span></span>](behaviors.md)|<span data-ttu-id="94297-115">Cette section définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="94297-115">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="94297-116">Chaque collection définit des éléments de comportement consommés respectivement par les points de terminaison et les services.</span><span class="sxs-lookup"><span data-stu-id="94297-116">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="94297-117">Chaque élément de comportement est identifié par son attribut `name` unique.</span><span class="sxs-lookup"><span data-stu-id="94297-117">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="94297-118">\<bindings></span><span class="sxs-lookup"><span data-stu-id="94297-118">\<bindings></span></span>](bindings.md)|<span data-ttu-id="94297-119">Cette section contient une collection de liaisons standard et personnalisées.</span><span class="sxs-lookup"><span data-stu-id="94297-119">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="94297-120">Chaque entrée est identifiée par son `name` unique.</span><span class="sxs-lookup"><span data-stu-id="94297-120">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="94297-121">Les services utilisent les liaisons en les liant à l’aide de `name`.</span><span class="sxs-lookup"><span data-stu-id="94297-121">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="94297-122">\<client></span><span class="sxs-lookup"><span data-stu-id="94297-122">\<client></span></span>](client.md)|<span data-ttu-id="94297-123">Cette section contient la liste des points de terminaison utilisés par un client pour se connecter à un service.</span><span class="sxs-lookup"><span data-stu-id="94297-123">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="94297-124">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="94297-124">\<comContracts></span></span>](comcontracts.md)|<span data-ttu-id="94297-125">Cette section définit des contrats COM activés pour interagir avec WCF et COM.</span><span class="sxs-lookup"><span data-stu-id="94297-125">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="94297-126">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="94297-126">\<commonBehaviors></span></span>](commonbehaviors.md)|<span data-ttu-id="94297-127">Cette section peut uniquement être définie dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="94297-127">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="94297-128">Elle définit deux collections enfants nommées `endpointBehaviors` et `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="94297-128">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="94297-129">Chaque collection définit des éléments de comportement consommés respectivement par tous les services et points de terminaison WCF sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="94297-129">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="94297-130">Si un comportement est défini dans `<commonBehaviors>` les sections et `<behaviors>` , le comportement de la \<section > des comportements est préféré.</span><span class="sxs-lookup"><span data-stu-id="94297-130">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="94297-131">\<diagnostics></span><span class="sxs-lookup"><span data-stu-id="94297-131">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="94297-132">Cette section contient les paramètres des fonctionnalités de diagnostic de WCF.</span><span class="sxs-lookup"><span data-stu-id="94297-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="94297-133">L'utilisateur peut activer/désactiver le suivi, les compteurs de performance et le fournisseur WMI et ajouter des filtres de messages personnalisés.</span><span class="sxs-lookup"><span data-stu-id="94297-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="94297-134">\<extensions></span><span class="sxs-lookup"><span data-stu-id="94297-134">\<extensions></span></span>](extensions-section.md)|<span data-ttu-id="94297-135">Cette section contient une collection d’extensions qui permettent à l’utilisateur de créer des liaisons, des comportements et d’autres aspects d’extensions définis par l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="94297-135">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="94297-136">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="94297-136">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="94297-137">Cette section définit un ensemble de mappages de protocole par défaut entre des schémas de protocole de transport (par exemple, http, net. TCP, net. pipe, etc.) et des liaisons WCF.</span><span class="sxs-lookup"><span data-stu-id="94297-137">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="94297-138">\<routing></span><span class="sxs-lookup"><span data-stu-id="94297-138">\<routing></span></span>](routing.md)|<span data-ttu-id="94297-139">Cette section définit un ensemble de filtres de routage qui déterminent le type de Windows Communication Foundation (WCF<xref:System.ServiceModel.Dispatcher.MessageFilter> ) à utiliser lors de l’évaluation des messages entrants, ainsi que les tables de routage qui définissent les points de terminaison cibles auxquels envoyer des messages lorsqu’un filtrer les correspondances.</span><span class="sxs-lookup"><span data-stu-id="94297-139">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="94297-140">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="94297-140">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="94297-141">Cette section définit le type instancié par l'environnement d'hébergement de service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="94297-141">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="94297-142">Si cette section est vide, le type par défaut est utilisé.</span><span class="sxs-lookup"><span data-stu-id="94297-142">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="94297-143">\<services></span><span class="sxs-lookup"><span data-stu-id="94297-143">\<services></span></span>](services.md)|<span data-ttu-id="94297-144">Cette section contient une collection de services.</span><span class="sxs-lookup"><span data-stu-id="94297-144">The section contains a collection of services.</span></span> <span data-ttu-id="94297-145">Pour chaque service défini dans l'assembly, cet élément contient un élément `service` indiquant les paramètres du service.</span><span class="sxs-lookup"><span data-stu-id="94297-145">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="94297-146">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="94297-146">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="94297-147">Cette section définit une collection de points de terminaison standard, qui sont des points de terminaison préconfigurés réutilisables.</span><span class="sxs-lookup"><span data-stu-id="94297-147">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="94297-148">Un point de terminaison standard possède un ou plusieurs attributs d’adresse, de liaison et de contrat ayant une valeur fixe.</span><span class="sxs-lookup"><span data-stu-id="94297-148">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="94297-149">Par exemple, dans le point de terminaison de découverte, le contrat est fixe.</span><span class="sxs-lookup"><span data-stu-id="94297-149">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="94297-150">Vous pouvez également utiliser des points de terminaison standard pour étendre le point de terminaison de service avec de nouvelles propriétés, ce qui revient à définir des liaisons personnalisées.</span><span class="sxs-lookup"><span data-stu-id="94297-150">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="94297-151">\<tracking></span><span class="sxs-lookup"><span data-stu-id="94297-151">\<tracking></span></span>](tracking-of-wcf.md)|<span data-ttu-id="94297-152">Cette section définit les paramètres de suivi d’un service de Workflow.</span><span class="sxs-lookup"><span data-stu-id="94297-152">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="94297-153">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="94297-153">Parent Elements</span></span>  
  
|<span data-ttu-id="94297-154">Élément</span><span class="sxs-lookup"><span data-stu-id="94297-154">Element</span></span>|<span data-ttu-id="94297-155">Description</span><span class="sxs-lookup"><span data-stu-id="94297-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="94297-156">\<configuration></span><span class="sxs-lookup"><span data-stu-id="94297-156">\<configuration></span></span>|<span data-ttu-id="94297-157">Élément racine correspondant à tous les éléments de configuration qui se trouvent dans un fichier de configuration .NET.</span><span class="sxs-lookup"><span data-stu-id="94297-157">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="94297-158">Notes</span><span class="sxs-lookup"><span data-stu-id="94297-158">Remarks</span></span>  
 <span data-ttu-id="94297-159">WCF n’ajoute pas d’éléments aux sections de configuration d’autres produits.</span><span class="sxs-lookup"><span data-stu-id="94297-159">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="94297-160">Les services WCF sont définis dans `services` la section du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="94297-160">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="94297-161">Un assembly peut contenir n'importe quel nombre de services.</span><span class="sxs-lookup"><span data-stu-id="94297-161">An assembly can contain any number of services.</span></span> <span data-ttu-id="94297-162">Chacun dispose de sa propre section de configuration de `service`.</span><span class="sxs-lookup"><span data-stu-id="94297-162">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="94297-163">Cette section et son contenu définissent le contrat, le comportement et les points de terminaison du service en question.</span><span class="sxs-lookup"><span data-stu-id="94297-163">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="94297-164">Seul l'attribut `name` d'un service est requis.</span><span class="sxs-lookup"><span data-stu-id="94297-164">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="94297-165">Par défaut, le nom d'un service décrit le type CLR sous-jacent utilisé pour implémenter un service ; toutefois, vous pouvez modifier la propriété ConfigurationName d'un <xref:System.ServiceModel.ServiceContractAttribute> pour remplacer la spécification de type CLR.</span><span class="sxs-lookup"><span data-stu-id="94297-165">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="94297-166">L'attribut `behaviorConfiguration` est facultatif.</span><span class="sxs-lookup"><span data-stu-id="94297-166">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="94297-167">Il identifie le comportement utilisé par un service.</span><span class="sxs-lookup"><span data-stu-id="94297-167">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="94297-168">Le comportement spécifié par cet attribut doit être lié à un comportement de service défini dans l'étendue du même fichier de configuration (c'est-à-dire le même fichier ou un fichier parent).</span><span class="sxs-lookup"><span data-stu-id="94297-168">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="94297-169">Chaque service expose un ou plusieurs points de terminaison définis dans un élément `endpoint`.</span><span class="sxs-lookup"><span data-stu-id="94297-169">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="94297-170">Chaque point de terminaison possède sa propre adresse et sa propre liaison.</span><span class="sxs-lookup"><span data-stu-id="94297-170">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="94297-171">Toutes les liaisons utilisées dans le fichier de configuration doivent être définies dans l'étendue du fichier.</span><span class="sxs-lookup"><span data-stu-id="94297-171">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="94297-172">Les liaisons sont liées aux points de terminaison grâce à la combinaison des attributs `name` et `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="94297-172">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="94297-173">L’attribut `binding` définit la section dans laquelle la liaison est définie.</span><span class="sxs-lookup"><span data-stu-id="94297-173">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="94297-174">L'attribut `bindingConfiguration` définit parmi les liaisons configurées figurant dans la section de liaison celle qui est utilisée.</span><span class="sxs-lookup"><span data-stu-id="94297-174">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="94297-175">Une section de liaison peut définir plusieurs liaisons configurées.</span><span class="sxs-lookup"><span data-stu-id="94297-175">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94297-176">Exemple</span><span class="sxs-lookup"><span data-stu-id="94297-176">Example</span></span>  
 <span data-ttu-id="94297-177">Voici un exemple de fichier de configuration WCF.</span><span class="sxs-lookup"><span data-stu-id="94297-177">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="94297-178">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94297-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
