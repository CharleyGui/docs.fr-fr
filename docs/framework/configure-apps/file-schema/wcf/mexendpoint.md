---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 7760ee4d3b118e339944317e8ec8d8217b5d909d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855109"
---
# \<mexEndpoint>
<span data-ttu-id="36c5b-101">Cet élément de configuration définit un point de terminaison standard avec un contrat IMetadataExchange fixe.</span><span class="sxs-lookup"><span data-stu-id="36c5b-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="36c5b-102">Puisque tous les points de terminaison d'échange de métadonnées ont comme contrat IMetadataExchange, vous pouvez utiliser ce point standard au lieu d'en définir un à votre intention.</span><span class="sxs-lookup"><span data-stu-id="36c5b-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="36c5b-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36c5b-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36c5b-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="36c5b-104">Attributes and Elements</span></span>  
 <span data-ttu-id="36c5b-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="36c5b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36c5b-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="36c5b-106">Attributes</span></span>  
  
|<span data-ttu-id="36c5b-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="36c5b-107">Attribute</span></span>|<span data-ttu-id="36c5b-108">Description</span><span class="sxs-lookup"><span data-stu-id="36c5b-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36c5b-109">name</span><span class="sxs-lookup"><span data-stu-id="36c5b-109">name</span></span>|<span data-ttu-id="36c5b-110">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="36c5b-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="36c5b-111">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="36c5b-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36c5b-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="36c5b-112">Child Elements</span></span>  
 <span data-ttu-id="36c5b-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="36c5b-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36c5b-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="36c5b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="36c5b-115">Élément</span><span class="sxs-lookup"><span data-stu-id="36c5b-115">Element</span></span>|<span data-ttu-id="36c5b-116">Description</span><span class="sxs-lookup"><span data-stu-id="36c5b-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="36c5b-117">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="36c5b-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
