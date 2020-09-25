---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: e8f0e0fa2ea1606bf980fd6fa1fcd47f12c3b540
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204747"
---
# \<mexEndpoint>

<span data-ttu-id="5bd05-101">Cet élément de configuration définit un point de terminaison standard avec un contrat IMetadataExchange fixe.</span><span class="sxs-lookup"><span data-stu-id="5bd05-101">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="5bd05-102">Puisque tous les points de terminaison d'échange de métadonnées ont comme contrat IMetadataExchange, vous pouvez utiliser ce point standard au lieu d'en définir un à votre intention.</span><span class="sxs-lookup"><span data-stu-id="5bd05-102">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="5bd05-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5bd05-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5bd05-104">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="5bd05-104">Attributes and Elements</span></span>  

 <span data-ttu-id="5bd05-105">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="5bd05-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5bd05-106">Attributs</span><span class="sxs-lookup"><span data-stu-id="5bd05-106">Attributes</span></span>  
  
|<span data-ttu-id="5bd05-107">Attribut</span><span class="sxs-lookup"><span data-stu-id="5bd05-107">Attribute</span></span>|<span data-ttu-id="5bd05-108">Description</span><span class="sxs-lookup"><span data-stu-id="5bd05-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5bd05-109">name</span><span class="sxs-lookup"><span data-stu-id="5bd05-109">name</span></span>|<span data-ttu-id="5bd05-110">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="5bd05-110">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5bd05-111">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="5bd05-111">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5bd05-112">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="5bd05-112">Child Elements</span></span>  

 <span data-ttu-id="5bd05-113">Aucun.</span><span class="sxs-lookup"><span data-stu-id="5bd05-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5bd05-114">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="5bd05-114">Parent Elements</span></span>  
  
|<span data-ttu-id="5bd05-115">Élément</span><span class="sxs-lookup"><span data-stu-id="5bd05-115">Element</span></span>|<span data-ttu-id="5bd05-116">Description</span><span class="sxs-lookup"><span data-stu-id="5bd05-116">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="5bd05-117">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="5bd05-117">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
