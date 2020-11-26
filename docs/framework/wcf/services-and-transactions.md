---
title: Services et transactions
ms.date: 03/30/2017
helpviewer_keywords:
- service contracts [WCF], designing services and transactions
ms.assetid: 864813ff-2709-4376-912d-f5c8d318c460
ms.openlocfilehash: e60f84aafe6c62a657cd3f27c9ccdb6b65186c35
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96235907"
---
# <a name="services-and-transactions"></a>Services et transactions

Les applications Windows Communication Foundation (WCF) peuvent initier une transaction à partir d’un client et coordonner la transaction au sein de l’opération de service. Les clients peuvent initier une transaction et appeler plusieurs opérations de service et s'assurer que les opérations de service sont validées ou annulées en tant qu'unité unique.  
  
 Vous pouvez activer le comportement de transaction dans le contrat de service en spécifiant un <xref:System.ServiceModel.ServiceBehaviorAttribute> et en définissant ses propriétés <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> et <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> pour les opérations de service qui requièrent des transactions clientes. Le paramètre <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> spécifie si la transaction dans laquelle la méthode s’exécute est automatiquement effectuée si aucune exception non prise en charge n’est levée. Pour plus d’informations sur ces attributs, consultez [attributs de transaction ServiceModel](./feature-details/servicemodel-transaction-attributes.md).  
  
 Le travail effectué dans les opérations de service et géré par un gestionnaire de ressources, tel que l'enregistrement des mises à jour de base de données, fait partie de la transaction du client.  
  
 L'exemple suivant illustre l'utilisation des attributs <xref:System.ServiceModel.ServiceBehaviorAttribute> et <xref:System.ServiceModel.OperationBehaviorAttribute> pour contrôler le comportement de transaction du côté service.  
  
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
  
 Vous pouvez activer les transactions et le déroulement des transactions en configurant les liaisons du client et du service pour utiliser le protocole WS-AtomicTransaction, et en définissant l' [\<transactionFlow>](../configure-apps/file-schema/wcf/transactionflow.md) élément sur `true` , comme indiqué dans l’exemple de configuration suivant.  
  
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
  
 Les clients peuvent commencer une transaction en créant un <xref:System.Transactions.TransactionScope> et en appelant des opérations de service dans la portée de la transaction.  
  
```csharp
using (TransactionScope ts = new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    //Do work here  
    ts.Complete();  
}  
```  
  
## <a name="see-also"></a>Voir aussi

- [Prise en charge transactionnelle dans System.ServiceModel](./feature-details/transactional-support-in-system-servicemodel.md)
- [Modèles de transaction](./feature-details/transaction-models.md)
- [WS Transaction Flow](./samples/ws-transaction-flow.md)
