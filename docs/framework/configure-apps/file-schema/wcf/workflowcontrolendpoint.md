---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70854785"
---
# \<workflowControlEndpoint>
<span data-ttu-id="31bd7-101">Cet élément de configuration définit un point de terminaison standard permettant de contrôler l'exécution d'instances de flux de travail (créer, exécuter, interrompre, arrêter, etc.).</span><span class="sxs-lookup"><span data-stu-id="31bd7-101">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="31bd7-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31bd7-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="31bd7-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="31bd7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="31bd7-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="31bd7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="31bd7-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="31bd7-105">Attributes</span></span>  
  
|<span data-ttu-id="31bd7-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="31bd7-106">Attribute</span></span>|<span data-ttu-id="31bd7-107">Description</span><span class="sxs-lookup"><span data-stu-id="31bd7-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="31bd7-108">name</span><span class="sxs-lookup"><span data-stu-id="31bd7-108">name</span></span>|<span data-ttu-id="31bd7-109">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="31bd7-109">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="31bd7-110">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="31bd7-110">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="31bd7-111">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="31bd7-111">Child Elements</span></span>  
 <span data-ttu-id="31bd7-112">Aucun.</span><span class="sxs-lookup"><span data-stu-id="31bd7-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="31bd7-113">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="31bd7-113">Parent Elements</span></span>  
  
|<span data-ttu-id="31bd7-114">Élément</span><span class="sxs-lookup"><span data-stu-id="31bd7-114">Element</span></span>|<span data-ttu-id="31bd7-115">Description</span><span class="sxs-lookup"><span data-stu-id="31bd7-115">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="31bd7-116">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="31bd7-116">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="31bd7-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31bd7-117">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
