---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 206a684e1279871eee4aed95a087921123f8efb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918662"
---
# <a name="transactionflow"></a><span data-ttu-id="32d49-101">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="32d49-101">\<transactionFlow></span></span>
<span data-ttu-id="32d49-102">Spécifie le support du flux de la transaction pour la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="32d49-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="32d49-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="32d49-103">\<system.serviceModel></span></span>  
<span data-ttu-id="32d49-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="32d49-104">\<bindings></span></span>  
<span data-ttu-id="32d49-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="32d49-105">\<customBinding></span></span>  
<span data-ttu-id="32d49-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="32d49-106">\<binding></span></span>  
<span data-ttu-id="32d49-107">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="32d49-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d49-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32d49-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32d49-109">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="32d49-109">Attributes and Elements</span></span>  
 <span data-ttu-id="32d49-110">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="32d49-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32d49-111">Attributs</span><span class="sxs-lookup"><span data-stu-id="32d49-111">Attributes</span></span>  
  
|<span data-ttu-id="32d49-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="32d49-112">Attribute</span></span>|<span data-ttu-id="32d49-113">Description</span><span class="sxs-lookup"><span data-stu-id="32d49-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32d49-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="32d49-114">transactionProtocol</span></span>|<span data-ttu-id="32d49-115">Spécifie le protocole de transaction à utiliser.</span><span class="sxs-lookup"><span data-stu-id="32d49-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="32d49-116">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="32d49-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="32d49-117">-   OleTransactions</span><span class="sxs-lookup"><span data-stu-id="32d49-117">-   OleTransactions</span></span><br /><span data-ttu-id="32d49-118">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="32d49-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="32d49-119">La valeur par défaut est OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="32d49-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="32d49-120">Cet attribut est de type <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="32d49-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32d49-121">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="32d49-121">Child Elements</span></span>  
 <span data-ttu-id="32d49-122">Aucun.</span><span class="sxs-lookup"><span data-stu-id="32d49-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32d49-123">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="32d49-123">Parent Elements</span></span>  
  
|<span data-ttu-id="32d49-124">Élément</span><span class="sxs-lookup"><span data-stu-id="32d49-124">Element</span></span>|<span data-ttu-id="32d49-125">Description</span><span class="sxs-lookup"><span data-stu-id="32d49-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32d49-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="32d49-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="32d49-127">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="32d49-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32d49-128">Notes</span><span class="sxs-lookup"><span data-stu-id="32d49-128">Remarks</span></span>  
 <span data-ttu-id="32d49-129">Cet élément vous permet d’activer ou de désactiver le flux de transactions entrantes dans les paramètres de liaison d’un point de terminaison, ainsi que de spécifier le format de protocole souhaité pour les transactions entrantes.</span><span class="sxs-lookup"><span data-stu-id="32d49-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="32d49-130">Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Configuration des transactions ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) et [activation du workflow de transaction](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="32d49-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="32d49-131">Lors de l’utilisation du protocole `OleTransactions` pour faire passer les transactions d’un point de terminaison vers un autre, le délai d’attente de transaction peut se perdre si le point de terminaison de destination tente un nouveau flux à l’aide d’un autre protocole que `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="32d49-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="32d49-132">Cela peut provoquer l'expiration de tous les nœuds de niveau inférieur après le tronçon OleTransactions selon un délai plus long que prévu.</span><span class="sxs-lookup"><span data-stu-id="32d49-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d49-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32d49-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="32d49-134">Configuration des transactions ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32d49-134">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="32d49-135">Activation du flux de transaction</span><span class="sxs-lookup"><span data-stu-id="32d49-135">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="32d49-136">Liaisons</span><span class="sxs-lookup"><span data-stu-id="32d49-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="32d49-137">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="32d49-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="32d49-138">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="32d49-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="32d49-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="32d49-139">\<customBinding></span></span>](custombinding.md)
