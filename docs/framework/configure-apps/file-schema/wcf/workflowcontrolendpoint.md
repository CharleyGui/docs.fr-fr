---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854785"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="17944-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="17944-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="17944-102">Cet élément de configuration définit un point de terminaison standard permettant de contrôler l'exécution d'instances de flux de travail (créer, exécuter, interrompre, arrêter, etc.).</span><span class="sxs-lookup"><span data-stu-id="17944-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="17944-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="17944-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="17944-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="17944-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="17944-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="17944-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="17944-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowControlEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="17944-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17944-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17944-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17944-108">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="17944-108">Attributes and Elements</span></span>  
 <span data-ttu-id="17944-109">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="17944-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17944-110">Attributs</span><span class="sxs-lookup"><span data-stu-id="17944-110">Attributes</span></span>  
  
|<span data-ttu-id="17944-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="17944-111">Attribute</span></span>|<span data-ttu-id="17944-112">Description</span><span class="sxs-lookup"><span data-stu-id="17944-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17944-113">name</span><span class="sxs-lookup"><span data-stu-id="17944-113">name</span></span>|<span data-ttu-id="17944-114">Chaîne qui spécifie le nom de la configuration du point de terminaison standard.</span><span class="sxs-lookup"><span data-stu-id="17944-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="17944-115">Le nom est utilisé dans l'attribut `endpointConfiguration` du point de terminaison de service pour lier un point de terminaison standard à sa configuration.</span><span class="sxs-lookup"><span data-stu-id="17944-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17944-116">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="17944-116">Child Elements</span></span>  
 <span data-ttu-id="17944-117">Aucun.</span><span class="sxs-lookup"><span data-stu-id="17944-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17944-118">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="17944-118">Parent Elements</span></span>  
  
|<span data-ttu-id="17944-119">Élément</span><span class="sxs-lookup"><span data-stu-id="17944-119">Element</span></span>|<span data-ttu-id="17944-120">Description</span><span class="sxs-lookup"><span data-stu-id="17944-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="17944-121">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="17944-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="17944-122">Collection de points de terminaison standard qui sont des points de terminaison prédéfinis dont une ou plusieurs propriétés (adresse, liaison, contrat) sont fixes.</span><span class="sxs-lookup"><span data-stu-id="17944-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17944-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17944-123">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
