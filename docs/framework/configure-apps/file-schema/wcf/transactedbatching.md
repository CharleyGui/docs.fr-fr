---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399412"
---
# <a name="transactedbatching"></a><span data-ttu-id="40d3d-101">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="40d3d-101">\<transactedBatching></span></span>

<span data-ttu-id="40d3d-102">Spécifie si le traitement par lots de la transaction est pris en charge pour les opérations de réception.</span><span class="sxs-lookup"><span data-stu-id="40d3d-102">Specifies whether transaction batching is supported for receive operations.</span></span>

<span data-ttu-id="40d3d-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="40d3d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="40d3d-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="40d3d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="40d3d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportements >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="40d3d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="40d3d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="40d3d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="40d3d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportement**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="40d3d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="40d3d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactedBatching >**</span><span class="sxs-lookup"><span data-stu-id="40d3d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="40d3d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40d3d-109">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="40d3d-110">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="40d3d-110">Attributes and Elements</span></span>

<span data-ttu-id="40d3d-111">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="40d3d-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="40d3d-112">Attributs</span><span class="sxs-lookup"><span data-stu-id="40d3d-112">Attributes</span></span>

|<span data-ttu-id="40d3d-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="40d3d-113">Attribute</span></span>|<span data-ttu-id="40d3d-114">Description</span><span class="sxs-lookup"><span data-stu-id="40d3d-114">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="40d3d-115">Entier qui spécifie le nombre maximal d’opérations de réception qui peuvent être regroupées dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="40d3d-115">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="40d3d-116">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="40d3d-116">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="40d3d-117">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="40d3d-117">Child Elements</span></span>

<span data-ttu-id="40d3d-118">Aucun.</span><span class="sxs-lookup"><span data-stu-id="40d3d-118">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="40d3d-119">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="40d3d-119">Parent Elements</span></span>

|<span data-ttu-id="40d3d-120">Élément</span><span class="sxs-lookup"><span data-stu-id="40d3d-120">Element</span></span>|<span data-ttu-id="40d3d-121">Description</span><span class="sxs-lookup"><span data-stu-id="40d3d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="40d3d-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="40d3d-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="40d3d-123">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="40d3d-123">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="40d3d-124">Notes</span><span class="sxs-lookup"><span data-stu-id="40d3d-124">Remarks</span></span>

<span data-ttu-id="40d3d-125">Un transport configuré avec le traitement par lots de la transaction fait des tentatives de traitement par lot de plusieurs opérations de réception en une transaction.</span><span class="sxs-lookup"><span data-stu-id="40d3d-125">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="40d3d-126">Ainsi, le coût relativement élevé de la création d’une transaction et de sa validation dans chaque opération de réception est évité.</span><span class="sxs-lookup"><span data-stu-id="40d3d-126">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="40d3d-127">Exemple</span><span class="sxs-lookup"><span data-stu-id="40d3d-127">Example</span></span>

<span data-ttu-id="40d3d-128">L'exemple suivant explique comment ajouter le comportement de traitement par lot avec transaction à un service dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="40d3d-128">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```

## <a name="see-also"></a><span data-ttu-id="40d3d-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="40d3d-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
