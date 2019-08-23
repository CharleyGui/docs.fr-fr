---
title: <client>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel/client
- http://schemas.microsoft.com/.NetConfiguration/v2.0#client
ms.assetid: bf0f7031-76c8-4e7e-a6c6-9ad9119134be
ms.openlocfilehash: 7dce5984882e48c3e62efc44ef00b6256d9eb64e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919524"
---
# <a name="client"></a><span data-ttu-id="eabd6-101">\<client></span><span class="sxs-lookup"><span data-stu-id="eabd6-101">\<client></span></span>
<span data-ttu-id="eabd6-102">L'élément `client` définit une liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="eabd6-102">The `client` element defines a list of endpoints that a client can connect to.</span></span>  
  
 <span data-ttu-id="eabd6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="eabd6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="eabd6-104">\<client></span><span class="sxs-lookup"><span data-stu-id="eabd6-104">\<client></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eabd6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eabd6-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <endpoint>
    </endpoint>
    <metadata>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eabd6-106">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="eabd6-106">Attributes and Elements</span></span>  
 <span data-ttu-id="eabd6-107">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="eabd6-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eabd6-108">Attributs</span><span class="sxs-lookup"><span data-stu-id="eabd6-108">Attributes</span></span>  
 <span data-ttu-id="eabd6-109">Aucun</span><span class="sxs-lookup"><span data-stu-id="eabd6-109">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="eabd6-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="eabd6-110">Child Elements</span></span>  
  
|<span data-ttu-id="eabd6-111">Élément</span><span class="sxs-lookup"><span data-stu-id="eabd6-111">Element</span></span>|<span data-ttu-id="eabd6-112">Description</span><span class="sxs-lookup"><span data-stu-id="eabd6-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eabd6-113">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="eabd6-113">\<endpoint></span></span>](endpoint-of-client.md)|<span data-ttu-id="eabd6-114">Contient une collection d'éléments de point de terminaison qui spécifient les points de terminaison auxquels ce client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="eabd6-114">Contains a collection of endpoint elements, that specify the endpoints that this client can connect to.</span></span>|  
|[<span data-ttu-id="eabd6-115">\<metadata></span><span class="sxs-lookup"><span data-stu-id="eabd6-115">\<metadata></span></span>](metadata.md)|<span data-ttu-id="eabd6-116">Contient des paramètres pour le traitement de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="eabd6-116">Contains settings for processing metadata.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="eabd6-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="eabd6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="eabd6-118">Élément</span><span class="sxs-lookup"><span data-stu-id="eabd6-118">Element</span></span>|<span data-ttu-id="eabd6-119">Description</span><span class="sxs-lookup"><span data-stu-id="eabd6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eabd6-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eabd6-120">\<system.serviceModel></span></span>](system-servicemodel.md)|<span data-ttu-id="eabd6-121">Élément racine de tous les éléments de configuration Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="eabd6-121">The root element of all Windows Communication Foundation (WCF) configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eabd6-122">Notes</span><span class="sxs-lookup"><span data-stu-id="eabd6-122">Remarks</span></span>  
 <span data-ttu-id="eabd6-123">La section `client` définit une liste de points de terminaison auxquels un client peut se connecter.</span><span class="sxs-lookup"><span data-stu-id="eabd6-123">The `client` section defines a list of endpoints that a client can connect to.</span></span> <span data-ttu-id="eabd6-124">Chaque point de terminaison répertorié dans la section client définit ses propres liaison, comportement et contrat.</span><span class="sxs-lookup"><span data-stu-id="eabd6-124">Each endpoint listed in the client section defines its own binding, behavior, and contract.</span></span> <span data-ttu-id="eabd6-125">Il est identifié uniquement par la combinaison des attributs `name` et `contract`.</span><span class="sxs-lookup"><span data-stu-id="eabd6-125">It is uniquely identified by the combination of the `name` and `contract` attributes.</span></span> <span data-ttu-id="eabd6-126">Le code client spécifie le `name` permettant de se connecter à un point de terminaison pour le service que le client implémente.</span><span class="sxs-lookup"><span data-stu-id="eabd6-126">The client code specifies the `name` to connect to an endpoint for the service that the client implements.</span></span> <span data-ttu-id="eabd6-127">Si l'attribut `name` est omis, le point de terminaison agit comme point de terminaison par défaut pour le contrat qu'il implémente.</span><span class="sxs-lookup"><span data-stu-id="eabd6-127">If the `name` attribute is omitted, the endpoint acts as the default endpoint for the contract it implements.</span></span>  
  
 <span data-ttu-id="eabd6-128">De plus, cette section spécifie également des paramètres pour le traitement des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="eabd6-128">In addition, this section also specifies settings for processing metadata.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eabd6-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="eabd6-129">Example</span></span>  
  
```xml  
<client>
  <endpoint address="/HelloWorld/"
            bindingConfiguration="usingDefaults"
            name="MyBinding"
            binding="customBinding"
            contract="HelloWorld">
    <addressProperties actingAs="http://www.microsoft.com/TestActor"
                       identityData="BasicReadWrite"
                       identityType="Spn"
                       isAddressPrivate="false">
  </endpoint>
</client>
```  
  
## <a name="see-also"></a><span data-ttu-id="eabd6-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="eabd6-130">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- [<span data-ttu-id="eabd6-131">Configuration du client WCF</span><span class="sxs-lookup"><span data-stu-id="eabd6-131">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="eabd6-132">Clients</span><span class="sxs-lookup"><span data-stu-id="eabd6-132">Clients</span></span>](../../../wcf/feature-details/clients.md)
