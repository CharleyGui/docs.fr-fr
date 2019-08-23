---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 78788f9dfbf6cdf3439fd6e33eddfe721e49840d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931254"
---
# <a name="mexendpoint"></a><span data-ttu-id="8c6ef-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="8c6ef-101">\<mexEndpoint></span></span>
<span data-ttu-id="8c6ef-102">Cet élément de configuration définit un point de terminaison standard avec un contrat IMetadataExchange fixe.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="8c6ef-103">Puisque tous les points de terminaison d'échange de métadonnées ont comme contrat IMetadataExchange, vous pouvez utiliser ce point standard au lieu d'en définir un à votre intention.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="8c6ef-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8c6ef-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8c6ef-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8c6ef-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c6ef-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c6ef-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8c6ef-107">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="8c6ef-107">Attributes and Elements</span></span>  
 <span data-ttu-id="8c6ef-108">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8c6ef-109">Attributs</span><span class="sxs-lookup"><span data-stu-id="8c6ef-109">Attributes</span></span>  
  
|<span data-ttu-id="8c6ef-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8c6ef-110">Attribute</span></span>|<span data-ttu-id="8c6ef-111">Description</span><span class="sxs-lookup"><span data-stu-id="8c6ef-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8c6ef-112">name</span><span class="sxs-lookup"><span data-stu-id="8c6ef-112">name</span></span>|<span data-ttu-id="8c6ef-113">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="8c6ef-114">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8c6ef-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="8c6ef-115">Child Elements</span></span>  
 <span data-ttu-id="8c6ef-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8c6ef-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="8c6ef-117">Parent Elements</span></span>  
  
|<span data-ttu-id="8c6ef-118">Élément</span><span class="sxs-lookup"><span data-stu-id="8c6ef-118">Element</span></span>|<span data-ttu-id="8c6ef-119">Description</span><span class="sxs-lookup"><span data-stu-id="8c6ef-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8c6ef-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="8c6ef-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="8c6ef-121">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="8c6ef-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
