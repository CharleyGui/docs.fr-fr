---
title: Services et transactions
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: 4c59b83448f5a2c448843c12dae99c442441441f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143276"
---
# <a name="services-and-transactions"></a><span data-ttu-id="af2ec-102">Services et transactions</span><span class="sxs-lookup"><span data-stu-id="af2ec-102">Services and Transactions</span></span>
<span data-ttu-id="af2ec-103">Les applications de la Windows Communication Foundation (WCF) peuvent lancer une transaction à partir d’un client et coordonner la transaction au sein de l’opération de service.</span><span class="sxs-lookup"><span data-stu-id="af2ec-103">Windows Communication Foundation (WCF) applications can initiate a transaction from within a client and coordinate the transaction within the service operation.</span></span> <span data-ttu-id="af2ec-104">Les clients peuvent initier une transaction et appeler plusieurs opérations de service et s'assurer que les opérations de service sont validées ou annulées en tant qu'unité unique.</span><span class="sxs-lookup"><span data-stu-id="af2ec-104">Clients can initiate a transaction and invoke several service operations and ensure that the service operations are either committed or rolled back as a single unit.</span></span>  
  
 <span data-ttu-id="af2ec-105">Vous pouvez activer le comportement de transaction dans le contrat de service en spécifiant un <xref:System.ServiceModel.ServiceBehaviorAttribute> et en définissant ses propriétés <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> et <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> pour les opérations de service qui requièrent des transactions clientes.</span><span class="sxs-lookup"><span data-stu-id="af2ec-105">You can enable the transaction behavior in the service contract by specifying a <xref:System.ServiceModel.ServiceBehaviorAttribute> and setting its <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> properties for service operations that require client transactions.</span></span> <span data-ttu-id="af2ec-106">Le paramètre <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> spécifie si la transaction dans laquelle la méthode s’exécute est automatiquement effectuée si aucune exception non prise en charge n’est levée.</span><span class="sxs-lookup"><span data-stu-id="af2ec-106">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> parameter specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="af2ec-107">Pour plus d’informations sur ces attributs, voir [Attributs transactionnels De ServiceModel](./feature-details/servicemodel-transaction-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="af2ec-107">For more information about these attributes, see [ServiceModel Transaction Attributes](./feature-details/servicemodel-transaction-attributes.md).</span></span>  
  
 <span data-ttu-id="af2ec-108">Le travail effectué dans les opérations de service et géré par un gestionnaire de ressources, tel que l'enregistrement des mises à jour de base de données, fait partie de la transaction du client.</span><span class="sxs-lookup"><span data-stu-id="af2ec-108">The work that is performed in the service operations and managed by a resource manager, such as logging database updates, is part of the client’s transaction.</span></span>  
  
 <span data-ttu-id="af2ec-109">L'exemple suivant illustre l'utilisation des attributs <xref:System.ServiceModel.ServiceBehaviorAttribute> et <xref:System.ServiceModel.OperationBehaviorAttribute> pour contrôler le comportement de transaction du côté service.</span><span class="sxs-lookup"><span data-stu-id="af2ec-109">The following sample demonstrates usage of the <xref:System.ServiceModel.ServiceBehaviorAttribute> and <xref:System.ServiceModel.OperationBehaviorAttribute> attributes to control service-side transaction behavior.</span></span>  
  
```csharp
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService: ICalculatorLog  
{  
    [OperationBehavior(TransactionScopeRequired = true,  
                           TransactionAutoComplete = true)]  
    public double Add(double n1, double n2)  
    {  
        recordToLog($"Added {n1} to {n2}");
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                               TransactionAutoComplete = true)]  
    public double Subtract(double n1, double n2)  
    {  
        recordToLog($"Subtracted {n1} from {n2}");
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Multiply(double n1, double n2)  
    {  
        recordToLog($"Multiplied {n1} by {n2}");
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,
                                       TransactionAutoComplete = true)]  
    public double Divide(double n1, double n2)  
    {  
        recordToLog($"Divided {n1} by {n2}", n1, n2);
        return n1 / n2;  
    }  
  
}  
```  
  
 <span data-ttu-id="af2ec-110">Vous pouvez activer les transactions et le flux de transactions en configurant les liaisons client et service pour utiliser `true`le protocole WS-AtomicTransaction, et en définissant [ \<l’élément transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) élément à , comme indiqué dans la configuration de l’échantillon suivant.</span><span class="sxs-lookup"><span data-stu-id="af2ec-110">You can enable transactions and transaction flow by configuring the client and service bindings to use the WS-AtomicTransaction protocol, and setting the [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) element to `true`, as shown in the following sample configuration.</span></span>  
  
```xml  
<client>  
    <endpoint address="net.tcp://localhost/ServiceModelSamples/service"
          binding="netTcpBinding"
          bindingConfiguration="netTcpBindingWSAT"
          contract="Microsoft.ServiceModel.Samples.ICalculatorLog" />  
</client>  
  
<bindings>  
    <netTcpBinding>  
        <binding name="netTcpBindingWSAT"  
                transactionFlow="true"  
                transactionProtocol="WSAtomicTransactionOctober2004" />  
     </netTcpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="af2ec-111">Les clients peuvent commencer une transaction en créant un <xref:System.Transactions.TransactionScope> et en appelant des opérations de service dans la portée de la transaction.</span><span class="sxs-lookup"><span data-stu-id="af2ec-111">Clients can begin a transaction by creating a <xref:System.Transactions.TransactionScope> and invoking service operations within the scope of the transaction.</span></span>  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="af2ec-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af2ec-112">See also</span></span>

- [<span data-ttu-id="af2ec-113">Prise en charge transactionnelle dans System.ServiceModel</span><span class="sxs-lookup"><span data-stu-id="af2ec-113">Transactional Support in System.ServiceModel</span></span>](./feature-details/transactional-support-in-system-servicemodel.md)
- [<span data-ttu-id="af2ec-114">Modèles de transaction</span><span class="sxs-lookup"><span data-stu-id="af2ec-114">Transaction Models</span></span>](./feature-details/transaction-models.md)
- [<span data-ttu-id="af2ec-115">WS Transaction Flow</span><span class="sxs-lookup"><span data-stu-id="af2ec-115">WS Transaction Flow</span></span>](./samples/ws-transaction-flow.md)
