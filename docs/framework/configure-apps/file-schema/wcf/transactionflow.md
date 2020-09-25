---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: c4e5cbac24e2c72791c2f5c0faed0703363c99e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91201419"
---
# \<transactionFlow>

<span data-ttu-id="7baf5-101">Spécifie le support du flux de la transaction pour la liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="7baf5-101">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="7baf5-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7baf5-102">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7baf5-103">Attributs et éléments</span><span class="sxs-lookup"><span data-stu-id="7baf5-103">Attributes and Elements</span></span>  

 <span data-ttu-id="7baf5-104">Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.</span><span class="sxs-lookup"><span data-stu-id="7baf5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7baf5-105">Attributs</span><span class="sxs-lookup"><span data-stu-id="7baf5-105">Attributes</span></span>  
  
|<span data-ttu-id="7baf5-106">Attribut</span><span class="sxs-lookup"><span data-stu-id="7baf5-106">Attribute</span></span>|<span data-ttu-id="7baf5-107">Description</span><span class="sxs-lookup"><span data-stu-id="7baf5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7baf5-108">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="7baf5-108">transactionProtocol</span></span>|<span data-ttu-id="7baf5-109">Spécifie le protocole de transaction à utiliser.</span><span class="sxs-lookup"><span data-stu-id="7baf5-109">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="7baf5-110">Les valeurs valides sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7baf5-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7baf5-111">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="7baf5-111">-   OleTransactions</span></span><br /><span data-ttu-id="7baf5-112">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="7baf5-112">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="7baf5-113">La valeur par défaut est OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="7baf5-113">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="7baf5-114">Cet attribut est de type <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="7baf5-114">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7baf5-115">Éléments enfants</span><span class="sxs-lookup"><span data-stu-id="7baf5-115">Child Elements</span></span>  

 <span data-ttu-id="7baf5-116">Aucun.</span><span class="sxs-lookup"><span data-stu-id="7baf5-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7baf5-117">Éléments parents</span><span class="sxs-lookup"><span data-stu-id="7baf5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7baf5-118">Élément</span><span class="sxs-lookup"><span data-stu-id="7baf5-118">Element</span></span>|<span data-ttu-id="7baf5-119">Description</span><span class="sxs-lookup"><span data-stu-id="7baf5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="7baf5-120">Définit toutes les fonctions de liaison d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="7baf5-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7baf5-121">Notes</span><span class="sxs-lookup"><span data-stu-id="7baf5-121">Remarks</span></span>  

 <span data-ttu-id="7baf5-122">Cet élément vous permet d’activer ou de désactiver le flux de transactions entrantes dans les paramètres de liaison d’un point de terminaison, ainsi que de spécifier le format de protocole souhaité pour les transactions entrantes.</span><span class="sxs-lookup"><span data-stu-id="7baf5-122">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="7baf5-123">Pour plus d’informations sur l’utilisation de cet élément de configuration, consultez [Configuration des transactions ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) et [activation du workflow de transaction](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="7baf5-123">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="7baf5-124">Lors de l’utilisation du protocole `OleTransactions` pour faire passer les transactions d’un point de terminaison vers un autre, le délai d’attente de transaction peut se perdre si le point de terminaison de destination tente un nouveau flux à l’aide d’un autre protocole que `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="7baf5-124">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="7baf5-125">Cela peut provoquer l'expiration de tous les nœuds de niveau inférieur après le tronçon OleTransactions selon un délai plus long que prévu.</span><span class="sxs-lookup"><span data-stu-id="7baf5-125">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7baf5-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7baf5-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="7baf5-127">Configuration des transactions ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7baf5-127">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="7baf5-128">Activation du flux de transaction</span><span class="sxs-lookup"><span data-stu-id="7baf5-128">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="7baf5-129">Liaisons</span><span class="sxs-lookup"><span data-stu-id="7baf5-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7baf5-130">Extension de liaisons</span><span class="sxs-lookup"><span data-stu-id="7baf5-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7baf5-131">Liaisons personnalisées</span><span class="sxs-lookup"><span data-stu-id="7baf5-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
