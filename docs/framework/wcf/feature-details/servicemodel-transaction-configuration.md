---
title: Configuration des transactions ServiceModel
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], ServiceModel configuration
ms.assetid: 5636067a-7fbd-4485-aaa2-8141c502acf3
ms.openlocfilehash: 79772d19ddaec041aa1fac936b9951731507b6e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184453"
---
# <a name="servicemodel-transaction-configuration"></a><span data-ttu-id="a89c3-102">Configuration des transactions ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a89c3-102">ServiceModel Transaction Configuration</span></span>
<span data-ttu-id="a89c3-103">Windows Communication Foundation (WCF) fournit trois attributs pour `transactionFlow`configurer les transactions pour un service: , `transactionProtocol`, et `transactionTimeout`.</span><span class="sxs-lookup"><span data-stu-id="a89c3-103">Windows Communication Foundation (WCF) provides three attributes for configuring transactions for a service: `transactionFlow`, `transactionProtocol`, and `transactionTimeout`.</span></span>  
  
## <a name="configuring-transactionflow"></a><span data-ttu-id="a89c3-104">Configuration de transactionFlow</span><span class="sxs-lookup"><span data-stu-id="a89c3-104">Configuring transactionFlow</span></span>  
 <span data-ttu-id="a89c3-105">La plupart des fixations prédéfinies `transactionFlow` `transactionProtocol` que WCF fournit contiennent les attributs et les attributs, de sorte que vous pouvez configurer la liaison pour accepter les transactions entrantes pour un point de terminaison spécifique à l’aide d’un protocole de flux de transaction spécifique.</span><span class="sxs-lookup"><span data-stu-id="a89c3-105">Most of the predefined bindings WCF provides contain the `transactionFlow` and `transactionProtocol` attributes, so that you can configure the binding to accept incoming transactions for a specific endpoint using a specific transaction flow protocol.</span></span> <span data-ttu-id="a89c3-106">Par ailleurs, l’élément `transactionFlow` et son attribut `transactionProtocol` vous permettent de générer votre propre liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a89c3-106">In addition, you can use the `transactionFlow` element and its `transactionProtocol` attribute to build your own custom binding.</span></span> <span data-ttu-id="a89c3-107">Pour plus d’informations sur [ \<](../../configure-apps/file-schema/wcf/bindings.md) la configuration des éléments de configuration, voir la liaison>et [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span><span class="sxs-lookup"><span data-stu-id="a89c3-107">For more information about setting the configuration elements, see [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) and [WCF Configuration Schema](../../../../docs/framework/configure-apps/file-schema/wcf/index.md).</span></span>  
  
 <span data-ttu-id="a89c3-108">L'attribut `transactionFlow` spécifie si le flux de transaction est activé pour les points de terminaison de service qui utilisent la liaison.</span><span class="sxs-lookup"><span data-stu-id="a89c3-108">The `transactionFlow` attribute specifies whether transaction flow is enabled for service endpoints that use the binding.</span></span>  
  
## <a name="configuring-transactionprotocol"></a><span data-ttu-id="a89c3-109">Configuration de transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="a89c3-109">Configuring transactionProtocol</span></span>  
 <span data-ttu-id="a89c3-110">L'attribut `transactionProtocol` spécifie le protocole de transaction à utiliser avec les points de terminaison de service qui utilisent la liaison.</span><span class="sxs-lookup"><span data-stu-id="a89c3-110">The `transactionProtocol` attribute specifies the transaction protocol to use with service endpoints that use the binding.</span></span>  
  
 <span data-ttu-id="a89c3-111">L'exemple suivant présente une section de configuration qui configure la liaison spécifiée pour prendre en charge le flux de transaction, ainsi qu'une utilisation du protocole WS-AtomicTransaction.</span><span class="sxs-lookup"><span data-stu-id="a89c3-111">The following is an example of a configuration section that configures the specified binding to support transaction flow, as well as a use the WS-AtomicTransaction protocol.</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding name="test"  
      closeTimeout="00:00:10"  
      openTimeout="00:00:20"
      receiveTimeout="00:00:30"  
      sendTimeout="00:00:40"  
      transactionFlow="true"  
      transactionProtocol="WSAtomicTransactionOctober2004"  
      hostNameComparisonMode="WeakWildcard"  
      maxBufferSize="1001"  
      maxConnections="123"
      maxReceivedMessageSize="1000">  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="configuring-transactiontimeout"></a><span data-ttu-id="a89c3-112">Configuration de transactionTimeout</span><span class="sxs-lookup"><span data-stu-id="a89c3-112">Configuring transactionTimeout</span></span>  
 <span data-ttu-id="a89c3-113">Vous pouvez `transactionTimeout` configurer l’attribut pour `behavior` votre service WCF dans l’élément du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="a89c3-113">You can configure the `transactionTimeout` attribute for your WCF service in the `behavior` element of the configuration file.</span></span> <span data-ttu-id="a89c3-114">Le code suivant montre comment procéder.</span><span class="sxs-lookup"><span data-stu-id="a89c3-114">The following code demonstrates how to do this.</span></span>  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <behaviors>  
         <behavior name="NewBehavior" transactionTimeout="00:01:00" /> <!-- 1 minute timeout -->  
      </behaviors>  
   </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="a89c3-115">L’attribut `transactionTimeout` spécifie le délai dans lequel une nouvelle transaction créée au niveau du service doit se terminer.</span><span class="sxs-lookup"><span data-stu-id="a89c3-115">The `transactionTimeout` attribute specifies the time period within which a new transaction created at the service must complete.</span></span> <span data-ttu-id="a89c3-116">Il est utilisé comme délai d’attente <xref:System.Transactions.TransactionScope> pour toute opération qui établit une nouvelle transaction ; si <xref:System.ServiceModel.OperationBehaviorAttribute> est appliqué, la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="a89c3-116">It is used as the <xref:System.Transactions.TransactionScope> time-out for any operation that establishes a new transaction, and if <xref:System.ServiceModel.OperationBehaviorAttribute> is applied, the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="a89c3-117">Le délai d'attente spécifie la durée entre la création de la transaction et l'exécution de la phase 1 du protocole de validation en deux phases.</span><span class="sxs-lookup"><span data-stu-id="a89c3-117">The time-out specifies the duration of time from the creation of the transaction to the completion of phase 1 in the two-phase commit protocol.</span></span>  
  
 <span data-ttu-id="a89c3-118">Si cet attribut est défini dans une section de configuration de `service`, vous devez appliquer au moins une méthode du service correspondant avec <xref:System.ServiceModel.OperationBehaviorAttribute>, dans lequel la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> a la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="a89c3-118">If this attribute is set within a `service` configuration section, you should apply at least one method of the corresponding service with <xref:System.ServiceModel.OperationBehaviorAttribute>, in which the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property is set to `true`.</span></span>  
  
 <span data-ttu-id="a89c3-119">Notez que la valeur du délai d'attente utilisée est toujours la plus petite entre le paramètre de configuration `transactionTimeout` et la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="a89c3-119">Note that the time-out value used is the smaller value between this `transactionTimeout` configuration setting and any <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89c3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a89c3-120">See also</span></span>

- [<span data-ttu-id="a89c3-121">\<>contraignantes</span><span class="sxs-lookup"><span data-stu-id="a89c3-121">\<binding></span></span>](../../configure-apps/file-schema/wcf/bindings.md)
- [<span data-ttu-id="a89c3-122">Schéma de configuration WCF</span><span class="sxs-lookup"><span data-stu-id="a89c3-122">WCF Configuration Schema</span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/index.md)
