---
title: <add> de <baseAddressPrefixFilter>
ms.date: 03/30/2017
ms.assetid: b226bede-8459-4de9-b2ac-3d39604ce2bc
ms.openlocfilehash: fefe85381aec113da123e6f2246aee340b0cf97a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91181594"
---
# <a name="add-of-baseaddressprefixfilter"></a><span data-ttu-id="0cfc3-102">\<add> de \<baseAddressPrefixFilter></span><span class="sxs-lookup"><span data-stu-id="0cfc3-102">\<add> of \<baseAddressPrefixFilter></span></span>

<span data-ttu-id="0cfc3-103">Représente un élément de configuration qui spécifie un filtre direct, qui fournit un mécanisme permettant de sélectionner les liaisons d’Internet Information Services (IIS) appropriées lors de l’hébergement d’une application Windows Communication Foundation (WCF) dans IIS.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-103">Represents a configuration element that specifies a pass-through filter, which provides a mechanism to pick the appropriate Internet Information Services (IIS) bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceHostingEnvironment>**](servicehostingenvironment.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddressPrefixFilters>**](baseaddressprefixfilters.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="0cfc3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cfc3-104">Syntax</span></span>  
  
```xml  
<serviceHostingEnvironment>
  <baseAddressPrefixFilters>
    <add prefix="String" />
  </baseAddressPrefixFilters>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0cfc3-105">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="0cfc3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0cfc3-106">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0cfc3-107">Attributs</span><span class="sxs-lookup"><span data-stu-id="0cfc3-107">Attributes</span></span>  
  
|<span data-ttu-id="0cfc3-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="0cfc3-108">Attribute</span></span>|<span data-ttu-id="0cfc3-109">Description</span><span class="sxs-lookup"><span data-stu-id="0cfc3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0cfc3-110">prefix</span><span class="sxs-lookup"><span data-stu-id="0cfc3-110">prefix</span></span>|<span data-ttu-id="0cfc3-111">URI utilisé pour correspondre à une partie d'une adresse de base.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-111">A URI that is used to match a part of a base address.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0cfc3-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="0cfc3-112">Child Elements</span></span>  

 <span data-ttu-id="0cfc3-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0cfc3-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="0cfc3-114">Parent Elements</span></span>  
  
|<span data-ttu-id="0cfc3-115">Élément</span><span class="sxs-lookup"><span data-stu-id="0cfc3-115">Element</span></span>|<span data-ttu-id="0cfc3-116">Description</span><span class="sxs-lookup"><span data-stu-id="0cfc3-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddressPrefixFilters>](baseaddressprefixfilters.md)|<span data-ttu-id="0cfc3-117">Collection d’éléments de configuration qui spécifient des filtres directs qui fournissent un mécanisme pour choisir les liaisons IIS appropriées lors de l’hébergement d’une application Windows Communication Foundation (WCF) dans IIS.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-117">A collection of configuration elements that specify pass-through filters, which provide a mechanism to pick the appropriate IIS bindings when hosting a Windows Communication Foundation (WCF) application in IIS.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0cfc3-118">Notes</span><span class="sxs-lookup"><span data-stu-id="0cfc3-118">Remarks</span></span>  

 <span data-ttu-id="0cfc3-119">Un filtre de préfixe permet aux fournisseurs d'hébergement partagé de spécifier les URI que le service doit utiliser.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-119">A prefix filter provides a way for shared hosting providers to specify which URIs are to be used by the service.</span></span> <span data-ttu-id="0cfc3-120">Il permet aux hôtes partagés d'héberger plusieurs applications avec différentes adresses de base pour la même méthode sur le même site.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-120">It enables shared hosts to host multiple applications with different base addresses for the same scheme on the same site.</span></span>  
  
 <span data-ttu-id="0cfc3-121">Les sites Web IIS sont des conteneurs d'applications virtuelles qui contiennent des répertoires virtuels.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-121">IIS Web sites are containers for virtual applications which contain virtual directories.</span></span> <span data-ttu-id="0cfc3-122">L’application dans un site est accessible par le biais d’une ou de plusieurs liaisons IIS.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-122">The application in a site can be accessed through one or more IIS binding.</span></span> <span data-ttu-id="0cfc3-123">Les liaisons IIS fournissent deux informations : un protocole de liaison et des informations de liaison.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-123">IIS bindings provide two pieces of information: binding protocol and binding information.</span></span> <span data-ttu-id="0cfc3-124">Le protocole de liaison (par exemple, HTTP) définit le modèle sur lequel la communication se produit, tandis que les informations de liaison (par exemple, adresse IP, port, en-tête de l'hôte) contiennent les données servant à accéder au site.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-124">Binding protocol (for example, HTTP) defines the scheme over which communication occurs, and binding information (for example, IP Address, Port, Hostheader) contains data used to access the site.</span></span>  
  
 <span data-ttu-id="0cfc3-125">IIS prend en charge la spécification de plusieurs liaisons IIS pour chaque site, ce qui génère plusieurs adresses de base pour chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-125">IIS supports specifying multiple IIS bindings for each site, which results in multiple base addresses for each scheme.</span></span> <span data-ttu-id="0cfc3-126">Étant donné qu’un service WCF hébergé sur un site autorise la liaison à une seule adresse de base pour chaque schéma, vous pouvez utiliser la fonctionnalité de filtre de préfixe pour choisir l’adresse de base requise du service hébergé.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-126">Because a WCF service hosted under a site allows binding to only one base address for each scheme, you can use the prefix filter feature to pick the required base address of the hosted service.</span></span> <span data-ttu-id="0cfc3-127">Les adresses de base entrantes, fournies par IIS, sont filtrées selon le filtre de la liste de préfixes facultative.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-127">The incoming base addresses, supplied by IIS, are filtered based on the optional prefix list filter.</span></span>  
  
 <span data-ttu-id="0cfc3-128">Par exemple, votre site peut contenir les adresses de base suivantes :</span><span class="sxs-lookup"><span data-stu-id="0cfc3-128">For example, your site can contain the following base addresses:</span></span>
  
```http
http://testl.fabrikam.com/Service.svc  
http://test2.fabrikam.com/Service.svc  
```  
  
 <span data-ttu-id="0cfc3-129">Vous pouvez utiliser le fichier de configuration suivant pour spécifier un filtre de préfixe au niveau AppDomain.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-129">You can use the following configuration file to specify a prefix filter at the appdomain level.</span></span>  
  
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
  
 <span data-ttu-id="0cfc3-130">Dans cet exemple, `net.tcp://test1.fabrikam.com:8000` et `http://test2.fabrikam.com:9000` sont les seules adresses de base pouvant être transmises pour leur modèle respectif.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-130">In this example, `net.tcp://test1.fabrikam.com:8000` and `http://test2.fabrikam.com:9000` are the only base addresses for their respective schemes which are allowed to be passed through.</span></span>  
  
 <span data-ttu-id="0cfc3-131">Par défaut, si aucun préfixe n'est spécifié, toutes les adresses sont transmises.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-131">By default, when prefix is not specified, all addresses are passed through.</span></span> <span data-ttu-id="0cfc3-132">La spécification du préfixe autorise uniquement la transmission de l'adresse de base correspondante pour ce modèle.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-132">Specifying the prefix only allows the matching base address for that scheme to be passed through.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0cfc3-133">Le filtre ne prend pas en charge les caractères génériques.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-133">The filter does not support any wildcards.</span></span> <span data-ttu-id="0cfc3-134">En outre, les adresses de base fournies par IIS peuvent avoir des adresses liées à d'autres modèles non présents dans la liste `baseAddressPrefixFilters`.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-134">In addition, the baseAddresses supplied by IIS may have addresses bound to other schemes not present in the `baseAddressPrefixFilters` list.</span></span> <span data-ttu-id="0cfc3-135">Ces adresses ne sont pas éliminées par filtrage.</span><span class="sxs-lookup"><span data-stu-id="0cfc3-135">These addresses are not filtered out.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cfc3-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cfc3-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.BaseAddressPrefixFilterElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
- [<span data-ttu-id="0cfc3-137">Hosting</span><span class="sxs-lookup"><span data-stu-id="0cfc3-137">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
