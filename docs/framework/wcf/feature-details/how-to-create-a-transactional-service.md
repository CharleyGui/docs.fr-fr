---
title: 'Procédure : créer un service transactionnel'
ms.date: 03/30/2017
ms.assetid: 1bd2e4ed-a557-43f9-ba98-4c70cb75c154
ms.openlocfilehash: c3d094dbd5822f6025e1cc6c90aab04b61459314
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286290"
---
# <a name="how-to-create-a-transactional-service"></a>Procédure : créer un service transactionnel

Cet exemple présente les divers aspects de la création d’un service transactionnel et l’utilisation d’une transaction initialisée par le client pour coordonner des opérations de service.  
  
### <a name="creating-a-transactional-service"></a>Création d'un service transactionnel  
  
1. Créez un contrat de service et annotez les opérations avec le paramètre souhaité de l’énumération <xref:System.ServiceModel.TransactionFlowOption> afin d’indiquer les spécifications des transactions entrantes. Notez que vous pouvez également placer <xref:System.ServiceModel.TransactionFlowAttribute> sur la classe de service implémentée. Cela permet à une seule implémentation d’une interface d’utiliser ces paramètres de transaction, au lieu d’être le cas pour chaque implémentation.  
  
    ```csharp
    [ServiceContract]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // Use this to require an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Mandatory)]  
        double Add(double n1, double n2);  
        [OperationContract]  
        // Use this to permit an incoming transaction  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        double Subtract(double n1, double n2);  
    }  
    ```  
  
2. Créez une classe d'implémentation et utilisez <xref:System.ServiceModel.ServiceBehaviorAttribute> pour spécifier éventuellement <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> et <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>. Notez que dans de nombreux cas, le <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> par défaut de 60 secondes et le <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> par défaut de `Unspecified` sont appropriés. Pour chaque opération, vous pouvez utiliser l’attribut <xref:System.ServiceModel.OperationBehaviorAttribute> pour spécifier si le travail exécuté dans la méthode doit s’effectuer dans l’étendue d’une étendue de transaction en fonction de la valeur de l’attribut <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>. Dans ce cas, la transaction utilisée pour la méthode `Add` est identique à la transaction entrante obligatoire qui est transmise à partir du client, et la transaction utilisée pour la méthode `Subtract` est soit identique à la transaction entrante si une transaction a été transmise à partir du client, soit une nouvelle transaction créée implicitement et localement.  
  
    ```csharp
    [ServiceBehavior(  
        TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,  
        TransactionTimeout = "00:00:45")]  
    public class CalculatorService : ICalculator  
    {  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n1} to {n2}");
            return n1 + n2;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n1, double n2)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n2} from {n1}");
            return n1 - n2;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
            // This is where the transaction provides specific benefit  
            // - changes to the database will be committed only when  
            // the transaction completes.  
        }  
    }  
    ```  
  
3. Configurez les liaisons dans le fichier de configuration, en spécifiant que le contexte de transaction doit être transmis, et les protocoles à utiliser pour ce faire. Pour plus d’informations, consultez [Configuration des transactions ServiceModel](servicemodel-transaction-configuration.md). Plus précisément, le type de liaison est spécifié dans l’attribut `binding` de l’élément de point de terminaison. L' [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) élément contient un `bindingConfiguration` attribut qui référence une configuration de liaison nommée `transactionalOleTransactionsTcpBinding` , comme indiqué dans l’exemple de configuration suivant.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Le flux de transaction est activé au niveau de la configuration en utilisant l’attribut `transactionFlow`, et le protocole de transaction est spécifié à l’aide de l’attribut `transactionProtocol`, tel qu’indiqué dans la configuration suivante.  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a>Prise en charge de plusieurs protocoles de transaction  
  
1. Pour des performances optimales, vous devez utiliser le protocole OleTransactions pour les scénarios impliquant un client et un service écrits à l’aide de Windows Communication Foundation (WCF). Cependant, le protocole WS-AT (WS-AtomicTransaction) est utile pour les scénarios où l'interopérabilité avec des piles de protocoles tierces est requise. Vous pouvez configurer les services WCF pour accepter les deux protocoles en fournissant plusieurs points de terminaison avec des liaisons spécifiques au protocole appropriées, comme indiqué dans l’exemple de configuration suivant.  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="http://localhost:8000/CalcService"  
        binding="wsHttpBinding"  
        bindingConfiguration="transactionalWsatHttpBinding"  
        contract="ICalculator"  
        name="WSAtomicTransaction_endpoint" />  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     Le protocole de transaction est spécifié à l'aide de l'attribut `transactionProtocol`. Cependant, cet attribut est absent du `wsHttpBinding` fourni par le système, car cette liaison peut uniquement utiliser le protocole WS-AT.  
  
    ```xml  
    <bindings>  
      <wsHttpBinding>  
        <binding name="transactionalWsatHttpBinding"  
          transactionFlow="true" />  
      </wsHttpBinding>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="controlling-the-completion-of-a-transaction"></a>Contrôle de l'exécution d'une transaction  
  
1. Par défaut, les opérations WCF effectuent automatiquement des transactions si aucune exception non gérée n’est levée. Vous pouvez modifier ce comportement à l'aide de la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> et de la méthode <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>. Lorsqu’une opération doit s’exécuter dans la même transaction qu’une autre (par exemple, une opération de débit et de crédit), vous pouvez désactiver le comportement de saisie semi-automatique en affectant <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> à la propriété `false`, tel qu’indiqué dans l’exemple d’opération `Debit` suivant. La transaction utilisée par l'opération `Debit` ne s'exécute pas tant qu'une méthode avec la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> à la valeur `true` n'est pas appelée, tel qu'indiqué dans l'opération `Credit1`, ou lorsque la méthode <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> est appelée pour marquer explicitement la transaction comme étant exécutée, tel qu'indiqué dans l'opération `Credit2`. Notez que les deux opérations de crédit sont indiquées à titre d'exemple, et qu'une opération de crédit unique serait plus courante.  
  
    ```csharp
    [ServiceBehavior]  
    public class CalculatorService : IAccount  
    {  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Debit(double n)  
        {  
            // Perform debit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = true)]  
        public void Credit1(double n)  
        {  
            // Perform credit operation  
  
            return;  
        }  
  
        [OperationBehavior(  
            TransactionScopeRequired = true, TransactionAutoComplete = false)]  
        public void Credit2(double n)  
        {  
            // Perform alternate credit operation  
  
            OperationContext.Current.SetTransactionComplete();  
            return;  
        }  
    }  
    ```  
  
2. Dans le cadre de la corrélation de transactions, l'affectation de <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> à la propriété `false` requiert l'utilisation d'une liaison de session. Cette exigence est spécifiée avec la propriété `SessionMode` sur <xref:System.ServiceModel.ServiceContractAttribute>.  
  
    ```csharp
    [ServiceContract(SessionMode = SessionMode.Required)]  
    public interface IAccount  
    {  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Debit(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit1(double n);  
        [OperationContract]  
        [TransactionFlow(TransactionFlowOption.Allowed)]  
        void Credit2(double n);  
    }  
    ```  
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a>Contrôle de la durée de vie d’une instance de service transactionnelle  
  
1. WCF utilise la <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> propriété pour spécifier si l’instance de service sous-jacente est libérée lorsqu’une transaction se termine. Dans la mesure où la valeur par défaut est `true` , sauf si elle est configurée dans le cas contraire, WCF présente un comportement d’activation « juste-à-temps » efficace et prévisible. Les appels à un service sur une transaction suivante sont assurés de disposer d'une nouvelle instance de service sans restes de l'état de la transaction précédente. Bien que cela s’avère souvent utile, vous pouvez souhaiter conserver l’état dans l’instance de service après l’exécution de la transaction. Ce peut être le cas, par exemple, lorsque l'état requis ou des handles vers des ressources sont coûteux à récupérer ou à reconstituer. Pour ce faire, vous pouvez affecter <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> à la propriété `false`. Avec ce paramètre, l'instance et les états associés seront disponibles sur les appels suivants. Lorsque vous utilisez ce paramètre, tenez compte du moment auquel et de la manière dont les transactions et l’état seront effacés et exécutés. L'exemple suivant montre comment procéder en conservant l'instance avec la variable `runningTotal`.  
  
    ```csharp
    [ServiceBehavior(TransactionIsolationLevel = [ServiceBehavior(  
        ReleaseServiceInstanceOnTransactionComplete = false)]  
    public class CalculatorService : ICalculator  
    {  
        double runningTotal = 0;  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Add(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Adding {n} to {runningTotal}");
            runningTotal = runningTotal + n;  
            return runningTotal;  
        }  
  
        [OperationBehavior(TransactionScopeRequired = true)]  
        public double Subtract(double n)  
        {  
            // Perform transactional operation  
            RecordToLog($"Subtracting {n} from {runningTotal}");
            runningTotal = runningTotal - n;  
            return runningTotal;  
        }  
  
        private static void RecordToLog(string recordText)  
        {  
            // Database operations omitted for brevity  
        }  
    }  
    ```  
  
    > [!NOTE]
    > La durée de vie d'instance étant un comportement interne au service et contrôlée via la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute>, aucune modification de la configuration de service ou du contrat de service n'est nécessaire pour définir le comportement d'instance. Par ailleurs, le câble ne contiendra pas de représentation de celui-ci.
