---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855109"
---
# <a name="mexendpoint"></a><span data-ttu-id="439d4-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="439d4-101">\<mexEndpoint></span></span>
<span data-ttu-id="439d4-102">Cet élément de configuration définit un point de terminaison standard avec un contrat IMetadataExchange fixe.</span><span class="sxs-lookup"><span data-stu-id="439d4-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="439d4-103">Puisque tous les points de terminaison d'échange de métadonnées ont comme contrat IMetadataExchange, vous pouvez utiliser ce point standard au lieu d'en définir un à votre intention.</span><span class="sxs-lookup"><span data-stu-id="439d4-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
<span data-ttu-id="439d4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="439d4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="439d4-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="439d4-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="439d4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="439d4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="439d4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="439d4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="439d4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="439d4-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="439d4-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="439d4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="439d4-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="439d4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="439d4-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="439d4-111">Attributes</span></span>  
  
|<span data-ttu-id="439d4-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="439d4-112">Attribute</span></span>|<span data-ttu-id="439d4-113">Description</span><span class="sxs-lookup"><span data-stu-id="439d4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="439d4-114">name</span><span class="sxs-lookup"><span data-stu-id="439d4-114">name</span></span>|<span data-ttu-id="439d4-115">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="439d4-115">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="439d4-116">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="439d4-116">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="439d4-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="439d4-117">Child Elements</span></span>  
 <span data-ttu-id="439d4-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="439d4-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="439d4-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="439d4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="439d4-120">Élément</span><span class="sxs-lookup"><span data-stu-id="439d4-120">Element</span></span>|<span data-ttu-id="439d4-121">Description</span><span class="sxs-lookup"><span data-stu-id="439d4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="439d4-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="439d4-122">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="439d4-123">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="439d4-123">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
