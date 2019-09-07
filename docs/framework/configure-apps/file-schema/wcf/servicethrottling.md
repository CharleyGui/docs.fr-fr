---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399560"
---
# <a name="servicethrottling"></a><span data-ttu-id="6b955-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="6b955-101">\<serviceThrottling></span></span>
<span data-ttu-id="6b955-102">Spécifie le mécanisme de limitation de requêtes d'un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="6b955-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="6b955-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6b955-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6b955-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6b955-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6b955-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6b955-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="6b955-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6b955-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="6b955-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="6b955-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="6b955-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceThrottling >**</span><span class="sxs-lookup"><span data-stu-id="6b955-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b955-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b955-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b955-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="6b955-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6b955-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="6b955-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b955-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="6b955-112">Attributes</span></span>  
  
|<span data-ttu-id="6b955-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="6b955-113">Attribute</span></span>|<span data-ttu-id="6b955-114">Description</span><span class="sxs-lookup"><span data-stu-id="6b955-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b955-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="6b955-115">maxConcurrentCalls</span></span>|<span data-ttu-id="6b955-116">Entier positif qui limite le nombre de messages actuellement traités dans <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6b955-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="6b955-117">Une fois cette limite atteinte, les appels sont mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="6b955-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="6b955-118">Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="6b955-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="6b955-119">La valeur par défaut est 16 \* nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="6b955-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="6b955-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="6b955-120">maxConcurrentInstances</span></span>|<span data-ttu-id="6b955-121">Entier positif qui limite le nombre d'objets <xref:System.ServiceModel.InstanceContext> exécutés à un moment donné sur <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="6b955-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="6b955-122">Les demandes de création d'instances supplémentaires sont mises en file d'attente et traitées lorsqu'un emplacement se libère.</span><span class="sxs-lookup"><span data-stu-id="6b955-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="6b955-123">La valeur par défaut est la somme de maxConcurrentSessions et MaxConcurrentCalls.</span><span class="sxs-lookup"><span data-stu-id="6b955-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="6b955-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="6b955-124">maxConcurrentSessions</span></span>|<span data-ttu-id="6b955-125">Entier positif qui limite le nombre de sessions qu'un objet <xref:System.ServiceModel.ServiceHost> peut accepter.</span><span class="sxs-lookup"><span data-stu-id="6b955-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="6b955-126">Le service acceptera des connexions une fois la limite atteinte, mais seuls les canaux ne dépassant pas la limite seront actifs (les messages seront lus à partir du canal).</span><span class="sxs-lookup"><span data-stu-id="6b955-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="6b955-127">Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="6b955-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="6b955-128">La valeur par défaut est 100 \* nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="6b955-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b955-129">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="6b955-129">Child Elements</span></span>  
 <span data-ttu-id="6b955-130">Aucun.</span><span class="sxs-lookup"><span data-stu-id="6b955-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b955-131">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="6b955-131">Parent Elements</span></span>  
  
|<span data-ttu-id="6b955-132">Élément</span><span class="sxs-lookup"><span data-stu-id="6b955-132">Element</span></span>|<span data-ttu-id="6b955-133">Description</span><span class="sxs-lookup"><span data-stu-id="6b955-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b955-134">\<behavior></span><span class="sxs-lookup"><span data-stu-id="6b955-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6b955-135">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="6b955-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b955-136">Notes</span><span class="sxs-lookup"><span data-stu-id="6b955-136">Remarks</span></span>  
 <span data-ttu-id="6b955-137">Les contrôles de limitation de requêtes limitent le nombre d'appels, d'instances ou de sessions simultanés pour empêcher une surconsommation des ressources.</span><span class="sxs-lookup"><span data-stu-id="6b955-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="6b955-138">Un suivi est écrit à chaque fois que la valeur des attributs est atteinte.</span><span class="sxs-lookup"><span data-stu-id="6b955-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="6b955-139">Le premier suivi est écrit en tant qu'avertissement.</span><span class="sxs-lookup"><span data-stu-id="6b955-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b955-140">Exemple</span><span class="sxs-lookup"><span data-stu-id="6b955-140">Example</span></span>  
 <span data-ttu-id="6b955-141">L'exemple de configuration suivant spécifie que le service restreint le nombre maximal d'appels simultanés à 2 et le nombre maximal d'instances simultanées à 10.</span><span class="sxs-lookup"><span data-stu-id="6b955-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="6b955-142">Pour obtenir un exemple détaillé de l’exécution de cet exemple, consultez [limitation](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="6b955-142">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="6b955-143">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6b955-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="6b955-144">Utilisation de ServiceThrottlingBehavior pour contrôler les performances du service WCF</span><span class="sxs-lookup"><span data-stu-id="6b955-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
