---
title: <baseAddressPrefixFilters>
ms.date: 03/30/2017
ms.assetid: 8cab2a9a-c51f-4283-bb60-2ad0c274fd46
ms.openlocfilehash: 55ffcfb5c0c84d68033d082cbe451696bd3c9dc2
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988360"
---
# <a name="baseaddressprefixfilters"></a><span data-ttu-id="53d9b-101">\<baseAddressPrefixFilters></span><span class="sxs-lookup"><span data-stu-id="53d9b-101">\<baseAddressPrefixFilters></span></span>
<span data-ttu-id="53d9b-102">Représente une collection d’éléments de configuration qui spécifient des filtres de passage, qui fournissent un mécanisme permettant de sélectionner les liaisons d’Internet Information Services (IIS) appropriées lors de l’hébergement de l’application Windows Communication Foundation (WCF) dans IIS.</span><span class="sxs-lookup"><span data-stu-id="53d9b-102">Represents a collection of configuration elements that specify pass through filters, which provide a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting the Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="53d9b-103">\<baseAddressPrefixFilters > ne reconnaît pas «localhost», utilisez le nom d’ordinateur complet à la place.</span><span class="sxs-lookup"><span data-stu-id="53d9b-103">\<baseAddressPrefixFilters> does not recognize "localhost", use the fully qualified machine name instead.</span></span>  
  
 <span data-ttu-id="53d9b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="53d9b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="53d9b-105">\<ServiceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="53d9b-105">\<ServiceHostingEnvironment></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53d9b-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53d9b-106">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
   </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53d9b-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="53d9b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="53d9b-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="53d9b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53d9b-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="53d9b-109">Attributes</span></span>  
 <span data-ttu-id="53d9b-110">Aucun.</span><span class="sxs-lookup"><span data-stu-id="53d9b-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="53d9b-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="53d9b-111">Child Elements</span></span>  
  
|<span data-ttu-id="53d9b-112">Élément</span><span class="sxs-lookup"><span data-stu-id="53d9b-112">Element</span></span>|<span data-ttu-id="53d9b-113">Description</span><span class="sxs-lookup"><span data-stu-id="53d9b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53d9b-114">\<add></span><span class="sxs-lookup"><span data-stu-id="53d9b-114">\<add></span></span>](add-of-baseaddressprefixfilter.md)|<span data-ttu-id="53d9b-115">Ajoute un élément de configuration spécifiant un filtre de préfixe pour les adresses de base utilisées par l'hôte de service.</span><span class="sxs-lookup"><span data-stu-id="53d9b-115">Adds a configuration element that specifies a prefix filter for the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="53d9b-116">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="53d9b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="53d9b-117">Élément</span><span class="sxs-lookup"><span data-stu-id="53d9b-117">Element</span></span>|<span data-ttu-id="53d9b-118">Description</span><span class="sxs-lookup"><span data-stu-id="53d9b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53d9b-119">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="53d9b-119">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="53d9b-120">Définit le type instancié par l'environnement d'hébergement du service pour un transport particulier.</span><span class="sxs-lookup"><span data-stu-id="53d9b-120">Defines the type the service hosting environment instantiates for a particular transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53d9b-121">Notes</span><span class="sxs-lookup"><span data-stu-id="53d9b-121">Remarks</span></span>  
 <span data-ttu-id="53d9b-122">Un filtre de préfixe permet aux fournisseurs d'hébergement partagé de spécifier les URI que le service doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="53d9b-122">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="53d9b-123">Il permet aux hôtes partagés d'héberger plusieurs applications avec différentes adresses de base pour la même méthode sur le même site.</span><span class="sxs-lookup"><span data-stu-id="53d9b-123">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="53d9b-124">Les sites Web IIS sont des conteneurs d'applications virtuelles qui contiennent des répertoires virtuels.</span><span class="sxs-lookup"><span data-stu-id="53d9b-124">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="53d9b-125">L’application dans un site est accessible par le biais d’une ou de plusieurs liaisons IIS.</span><span class="sxs-lookup"><span data-stu-id="53d9b-125">The application in a site can be accessed through one or more IIS bindings.</span></span> <span data-ttu-id="53d9b-126">Les liaisons IIS fournissent deux informations : un protocole de liaison et des informations de liaison.</span><span class="sxs-lookup"><span data-stu-id="53d9b-126">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="53d9b-127">Le protocole de liaison (par exemple, HTTP) définit le modèle sur lequel la communication se produit, tandis que les informations de liaison (par exemple, adresse IP, port, en-tête de l'hôte) contiennent les données servant à accéder au site.</span><span class="sxs-lookup"><span data-stu-id="53d9b-127">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="53d9b-128">IIS prend en charge la spécification de plusieurs liaisons IIS pour chaque site, ce qui génère plusieurs adresses de base pour chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="53d9b-128">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="53d9b-129">Étant donné qu’un service WCF hébergé sur un site autorise la liaison à une seule adresse de base pour chaque schéma, vous pouvez utiliser la fonctionnalité de filtre de préfixe pour choisir l’adresse de base requise du service hébergé.</span><span class="sxs-lookup"><span data-stu-id="53d9b-129">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="53d9b-130">Les adresses de base entrantes, fournies par IIS, sont filtrées selon le filtre de la liste de préfixes facultative.</span><span class="sxs-lookup"><span data-stu-id="53d9b-130">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="53d9b-131">Par exemple, votre site peut contenir les adresses de base suivantes.</span><span class="sxs-lookup"><span data-stu-id="53d9b-131">For example, your site can contain the following base addresses.</span></span>  
  
```  
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="53d9b-132">Vous pouvez utiliser le fichier de configuration suivant pour spécifier un filtre de préfixe au niveau AppDomain.</span><span class="sxs-lookup"><span data-stu-id="53d9b-132">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
```xml  
<system.serviceModel>
  <serviceHostingEnvironment>
    <baseAddressPrefixFilters>
      <add prefix="net.tcp://test1.fabrikam.com:8000" />
      <add prefix="http://test2.fabrikam.com:9000" />
    </baseAddressPrefixFilters>
  </serviceHostingEnvironment>
</system.serviceModel>
```  
  
 <span data-ttu-id="53d9b-133">Dans cet exemple, `net.tcp://test1.fabrikam.com:8000` et `http://test2.fabrikam.com:9000` sont les seules adresses de base pouvant être passées pour leur modèle respectif.</span><span class="sxs-lookup"><span data-stu-id="53d9b-133">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes, which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="53d9b-134">Par défaut, si aucun préfixe n'est spécifié, toutes les adresses sont transmises.</span><span class="sxs-lookup"><span data-stu-id="53d9b-134">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="53d9b-135">La spécification du préfixe autorise uniquement la transmission de l'adresse de base correspondante pour ce modèle.</span><span class="sxs-lookup"><span data-stu-id="53d9b-135">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53d9b-136">Le filtre ne prend pas en charge les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="53d9b-136">The filter does not support any wildcards.</span></span> <span data-ttu-id="53d9b-137">En outre, les adresses de base fournies par IIS peuvent avoir des adresses liées à d'autres modèles non présents dans la liste `baseAddressPrefixFilters`.</span><span class="sxs-lookup"><span data-stu-id="53d9b-137">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="53d9b-138">Ces adresses ne sont pas éliminées par filtrage.</span><span class="sxs-lookup"><span data-stu-id="53d9b-138">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53d9b-139">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="53d9b-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="53d9b-140">Hébergement</span><span class="sxs-lookup"><span data-stu-id="53d9b-140">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
