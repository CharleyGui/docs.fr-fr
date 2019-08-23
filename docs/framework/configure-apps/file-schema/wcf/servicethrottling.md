---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 77ed5e91f09d9e658deeb7996baaca445b4e0c90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937110"
---
# <a name="servicethrottling"></a><span data-ttu-id="48b43-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="48b43-101">\<serviceThrottling></span></span>
<span data-ttu-id="48b43-102">Spécifie le mécanisme de limitation de requêtes d'un service Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="48b43-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="48b43-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="48b43-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="48b43-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="48b43-104">\<behaviors></span></span>  
<span data-ttu-id="48b43-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="48b43-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="48b43-106">\<> de comportement</span><span class="sxs-lookup"><span data-stu-id="48b43-106">\<behavior></span></span>  
<span data-ttu-id="48b43-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="48b43-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48b43-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="48b43-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48b43-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="48b43-109">Attributes and Elements</span></span>  
 <span data-ttu-id="48b43-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="48b43-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48b43-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="48b43-111">Attributes</span></span>  
  
|<span data-ttu-id="48b43-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="48b43-112">Attribute</span></span>|<span data-ttu-id="48b43-113">Description</span><span class="sxs-lookup"><span data-stu-id="48b43-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48b43-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="48b43-114">maxConcurrentCalls</span></span>|<span data-ttu-id="48b43-115">Entier positif qui limite le nombre de messages actuellement traités dans <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="48b43-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="48b43-116">Une fois cette limite atteinte, les appels sont mis en file d'attente.</span><span class="sxs-lookup"><span data-stu-id="48b43-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="48b43-117">Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="48b43-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="48b43-118">La valeur par défaut est 16 \* nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="48b43-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="48b43-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="48b43-119">maxConcurrentInstances</span></span>|<span data-ttu-id="48b43-120">Entier positif qui limite le nombre d'objets <xref:System.ServiceModel.InstanceContext> exécutés à un moment donné sur <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="48b43-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="48b43-121">Les demandes de création d'instances supplémentaires sont mises en file d'attente et traitées lorsqu'un emplacement se libère.</span><span class="sxs-lookup"><span data-stu-id="48b43-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="48b43-122">La valeur par défaut est la somme de maxConcurrentSessions et MaxConcurrentCalls.</span><span class="sxs-lookup"><span data-stu-id="48b43-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="48b43-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="48b43-123">maxConcurrentSessions</span></span>|<span data-ttu-id="48b43-124">Entier positif qui limite le nombre de sessions qu'un objet <xref:System.ServiceModel.ServiceHost> peut accepter.</span><span class="sxs-lookup"><span data-stu-id="48b43-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="48b43-125">Le service acceptera des connexions une fois la limite atteinte, mais seuls les canaux ne dépassant pas la limite seront actifs (les messages seront lus à partir du canal).</span><span class="sxs-lookup"><span data-stu-id="48b43-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="48b43-126">Affecter 0 à cette valeur équivaut à lui affecter la valeur Int32.MaxValue.</span><span class="sxs-lookup"><span data-stu-id="48b43-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="48b43-127">La valeur par défaut est 100 \* nombre de processeurs.</span><span class="sxs-lookup"><span data-stu-id="48b43-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48b43-128">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="48b43-128">Child Elements</span></span>  
 <span data-ttu-id="48b43-129">Aucun.</span><span class="sxs-lookup"><span data-stu-id="48b43-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="48b43-130">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="48b43-130">Parent Elements</span></span>  
  
|<span data-ttu-id="48b43-131">Élément</span><span class="sxs-lookup"><span data-stu-id="48b43-131">Element</span></span>|<span data-ttu-id="48b43-132">Description</span><span class="sxs-lookup"><span data-stu-id="48b43-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48b43-133">\<behavior></span><span class="sxs-lookup"><span data-stu-id="48b43-133">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="48b43-134">Spécifie un élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="48b43-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48b43-135">Notes</span><span class="sxs-lookup"><span data-stu-id="48b43-135">Remarks</span></span>  
 <span data-ttu-id="48b43-136">Les contrôles de limitation de requêtes limitent le nombre d'appels, d'instances ou de sessions simultanés pour empêcher une surconsommation des ressources.</span><span class="sxs-lookup"><span data-stu-id="48b43-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="48b43-137">Un suivi est écrit à chaque fois que la valeur des attributs est atteinte.</span><span class="sxs-lookup"><span data-stu-id="48b43-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="48b43-138">Le premier suivi est écrit en tant qu'avertissement.</span><span class="sxs-lookup"><span data-stu-id="48b43-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="48b43-139">Exemple</span><span class="sxs-lookup"><span data-stu-id="48b43-139">Example</span></span>  
 <span data-ttu-id="48b43-140">L'exemple de configuration suivant spécifie que le service restreint le nombre maximal d'appels simultanés à 2 et le nombre maximal d'instances simultanées à 10.</span><span class="sxs-lookup"><span data-stu-id="48b43-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="48b43-141">Pour obtenir un exemple détaillé de l’exécution de cet exemple, consultez [limitation](../../../wcf/samples/throttling.md).</span><span class="sxs-lookup"><span data-stu-id="48b43-141">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48b43-142">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="48b43-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="48b43-143">Utilisation de ServiceThrottlingBehavior pour contrôler les performances du service WCF</span><span class="sxs-lookup"><span data-stu-id="48b43-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
