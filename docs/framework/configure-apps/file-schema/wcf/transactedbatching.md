---
title: <transactedBatching>
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 6167a4ad56a9481a9f695b770605991a0a88d2d9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399412"
---
# \<transactedBatching>

<span data-ttu-id="59dc2-101">Spécifie si le traitement par lots de la transaction est pris en charge pour les opérations de réception.</span><span class="sxs-lookup"><span data-stu-id="59dc2-101">Specifies whether transaction batching is supported for receive operations.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactedBatching>**  

## <a name="syntax"></a><span data-ttu-id="59dc2-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59dc2-102">Syntax</span></span>

```xml
<transactedBatching maxBatchSize="Integer" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="59dc2-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="59dc2-103">Attributes and Elements</span></span>

<span data-ttu-id="59dc2-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="59dc2-104">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="59dc2-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="59dc2-105">Attributes</span></span>

|<span data-ttu-id="59dc2-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="59dc2-106">Attribute</span></span>|<span data-ttu-id="59dc2-107">Description</span><span class="sxs-lookup"><span data-stu-id="59dc2-107">Description</span></span>|
|---------------|-----------------|
|`maxBatchSize`|<span data-ttu-id="59dc2-108">Entier qui spécifie le nombre maximal d’opérations de réception qui peuvent être regroupées dans une transaction.</span><span class="sxs-lookup"><span data-stu-id="59dc2-108">An integer that specifies the maximum number of receive operations that can be batched together in one transaction.</span></span> <span data-ttu-id="59dc2-109">La valeur par défaut est 0.</span><span class="sxs-lookup"><span data-stu-id="59dc2-109">The default is 0.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="59dc2-110">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="59dc2-110">Child Elements</span></span>

<span data-ttu-id="59dc2-111">Aucun.</span><span class="sxs-lookup"><span data-stu-id="59dc2-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="59dc2-112">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="59dc2-112">Parent Elements</span></span>

|<span data-ttu-id="59dc2-113">Élément</span><span class="sxs-lookup"><span data-stu-id="59dc2-113">Element</span></span>|<span data-ttu-id="59dc2-114">Description</span><span class="sxs-lookup"><span data-stu-id="59dc2-114">Description</span></span>|
|-------------|-----------------|
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="59dc2-115">Spécifie un comportement de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="59dc2-115">Specifies an endpoint behavior.</span></span>|

## <a name="remarks"></a><span data-ttu-id="59dc2-116">Remarques</span><span class="sxs-lookup"><span data-stu-id="59dc2-116">Remarks</span></span>

<span data-ttu-id="59dc2-117">Un transport configuré avec le traitement par lots de la transaction fait des tentatives de traitement par lot de plusieurs opérations de réception en une transaction.</span><span class="sxs-lookup"><span data-stu-id="59dc2-117">A transport that is configured with transaction batching attempts to batch several receive operations into one transaction.</span></span> <span data-ttu-id="59dc2-118">Ainsi, le coût relativement élevé de la création d’une transaction et de sa validation dans chaque opération de réception est évité.</span><span class="sxs-lookup"><span data-stu-id="59dc2-118">By doing so, the relatively high cost of creating a transaction and committing it in every receive operation is avoided.</span></span>

## <a name="example"></a><span data-ttu-id="59dc2-119">Exemple</span><span class="sxs-lookup"><span data-stu-id="59dc2-119">Example</span></span>

<span data-ttu-id="59dc2-120">L'exemple suivant explique comment ajouter le comportement de traitement par lot avec transaction à un service dans un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="59dc2-120">The following example shows how to add the transacted batching behavior to a service in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="59dc2-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="59dc2-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
