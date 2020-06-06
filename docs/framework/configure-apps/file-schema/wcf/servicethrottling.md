---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399560"
---
# \<serviceThrottling>
<span data-ttu-id="ff3e5-101">Spécifie le mécanisme de limitation de requêtes d'un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ff3e5-101">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="ff3e5-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ff3e5-102">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff3e5-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="ff3e5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="ff3e5-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff3e5-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="ff3e5-105">Attributes</span></span>  
  
|<span data-ttu-id="ff3e5-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="ff3e5-106">Attribute</span></span>|<span data-ttu-id="ff3e5-107">Description</span><span class="sxs-lookup"><span data-stu-id="ff3e5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff3e5-108">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="ff3e5-108">maxConcurrentCalls</span></span>|<span data-ttu-id="ff3e5-109">Entier positif qui limite le nombre de messages actuellement traités dans <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-109">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="ff3e5-110">Les appels excédentaires sont mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-110">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="ff3e5-111">Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-111">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="ff3e5-112">La valeur par défaut est 16 \* nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-112">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="ff3e5-113">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="ff3e5-113">maxConcurrentInstances</span></span>|<span data-ttu-id="ff3e5-114">Entier positif qui limite le nombre d'objets <xref:System.ServiceModel.InstanceContext> exécutés à un moment donné sur <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-114">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="ff3e5-115">Les demandes de création d'instances supplémentaires sont mises en file d'attente et traitées lorsqu'un emplacement se libère.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-115">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="ff3e5-116">La valeur par défaut est la somme de maxConcurrentSessions et MaxConcurrentCalls.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-116">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="ff3e5-117">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="ff3e5-117">maxConcurrentSessions</span></span>|<span data-ttu-id="ff3e5-118">Entier positif qui limite le nombre de sessions qu'un objet <xref:System.ServiceModel.ServiceHost> peut accepter.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-118">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="ff3e5-119">Le service acceptera des connexions une fois la limite atteinte, mais seuls les canaux ne dépassant pas la limite seront actifs (les messages seront lus à partir du canal).</span><span class="sxs-lookup"><span data-stu-id="ff3e5-119">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="ff3e5-120">Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-120">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="ff3e5-121">La valeur par défaut est 100 \* nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-121">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff3e5-122">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="ff3e5-122">Child Elements</span></span>  
 <span data-ttu-id="ff3e5-123">Aucun.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ff3e5-124">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="ff3e5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="ff3e5-125">Élément</span><span class="sxs-lookup"><span data-stu-id="ff3e5-125">Element</span></span>|<span data-ttu-id="ff3e5-126">Description</span><span class="sxs-lookup"><span data-stu-id="ff3e5-126">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="ff3e5-127">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff3e5-128">Remarques</span><span class="sxs-lookup"><span data-stu-id="ff3e5-128">Remarks</span></span>  
 <span data-ttu-id="ff3e5-129">Les contrôles de limitation de requêtes limitent le nombre d'appels, d'instances ou de sessions simultanés pour empêcher une surconsommation des ressources.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-129">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="ff3e5-130">Un suivi est écrit à chaque fois que la valeur des attributs est atteinte.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-130">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="ff3e5-131">Le premier suivi est écrit en tant qu'avertissement.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-131">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff3e5-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="ff3e5-132">Example</span></span>  
 <span data-ttu-id="ff3e5-133">L'exemple de configuration suivant spécifie que le service restreint le nombre maximal d'appels simultanés à 2 et le nombre maximal d'instances simultanées à 10.</span><span class="sxs-lookup"><span data-stu-id="ff3e5-133">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="ff3e5-134">Pour obtenir un exemple détaillé de l’exécution de cet exemple, consultez [limitation](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="ff3e5-134">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ff3e5-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff3e5-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="ff3e5-136">Utilisation de ServiceThrottlingBehavior pour contrôler les performances du service WCF</span><span class="sxs-lookup"><span data-stu-id="ff3e5-136">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
