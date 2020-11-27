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
# <a name="how-to-create-a-transactional-service"></a><span data-ttu-id="55ba2-102">Procédure : créer un service transactionnel</span><span class="sxs-lookup"><span data-stu-id="55ba2-102">How to: Create a Transactional Service</span></span>

<span data-ttu-id="55ba2-103">Cet exemple présente les divers aspects de la création d’un service transactionnel et l’utilisation d’une transaction initialisée par le client pour coordonner des opérations de service.</span><span class="sxs-lookup"><span data-stu-id="55ba2-103">This sample demonstrates various aspects of creating a transactional service and the use of a client-initiated transaction to coordinate service operations.</span></span>  
  
### <a name="creating-a-transactional-service"></a><span data-ttu-id="55ba2-104">Création d'un service transactionnel</span><span class="sxs-lookup"><span data-stu-id="55ba2-104">Creating a transactional service</span></span>  
  
1. <span data-ttu-id="55ba2-105">Créez un contrat de service et annotez les opérations avec le paramètre souhaité de l’énumération <xref:System.ServiceModel.TransactionFlowOption> afin d’indiquer les spécifications des transactions entrantes.</span><span class="sxs-lookup"><span data-stu-id="55ba2-105">Create a service contract and annotate the operations with the desired setting from the <xref:System.ServiceModel.TransactionFlowOption> enumeration to specify the incoming transaction requirements.</span></span> <span data-ttu-id="55ba2-106">Notez que vous pouvez également placer <xref:System.ServiceModel.TransactionFlowAttribute> sur la classe de service implémentée.</span><span class="sxs-lookup"><span data-stu-id="55ba2-106">Note that you can also place the <xref:System.ServiceModel.TransactionFlowAttribute> on the service class being implemented.</span></span> <span data-ttu-id="55ba2-107">Cela permet à une seule implémentation d’une interface d’utiliser ces paramètres de transaction, au lieu d’être le cas pour chaque implémentation.</span><span class="sxs-lookup"><span data-stu-id="55ba2-107">This allows for a single implementation of an interface to use these transaction settings, instead of every implementation.</span></span>  
  
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
  
2. <span data-ttu-id="55ba2-108">Créez une classe d'implémentation et utilisez <xref:System.ServiceModel.ServiceBehaviorAttribute> pour spécifier éventuellement <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> et <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span><span class="sxs-lookup"><span data-stu-id="55ba2-108">Create an implementation class, and use the <xref:System.ServiceModel.ServiceBehaviorAttribute> to optionally specify a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> and a <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A>.</span></span> <span data-ttu-id="55ba2-109">Notez que dans de nombreux cas, le <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> par défaut de 60 secondes et le <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> par défaut de `Unspecified` sont appropriés.</span><span class="sxs-lookup"><span data-stu-id="55ba2-109">You should note that in many cases, the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionTimeout%2A> of 60 seconds and the default <xref:System.ServiceModel.ServiceBehaviorAttribute.TransactionIsolationLevel%2A> of `Unspecified` are appropriate.</span></span> <span data-ttu-id="55ba2-110">Pour chaque opération, vous pouvez utiliser l’attribut <xref:System.ServiceModel.OperationBehaviorAttribute> pour spécifier si le travail exécuté dans la méthode doit s’effectuer dans l’étendue d’une étendue de transaction en fonction de la valeur de l’attribut <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A>.</span><span class="sxs-lookup"><span data-stu-id="55ba2-110">For each operation, you can use the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute to specify whether work performed within the method should occur within the scope of a transaction scope according to the value of the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> attribute.</span></span> <span data-ttu-id="55ba2-111">Dans ce cas, la transaction utilisée pour la méthode `Add` est identique à la transaction entrante obligatoire qui est transmise à partir du client, et la transaction utilisée pour la méthode `Subtract` est soit identique à la transaction entrante si une transaction a été transmise à partir du client, soit une nouvelle transaction créée implicitement et localement.</span><span class="sxs-lookup"><span data-stu-id="55ba2-111">In this case, the transaction used for the `Add` method is the same as the mandatory incoming transaction that is flowed from the client, and the transaction used for the `Subtract` method is either the same as the incoming transaction if one was flowed from the client, or a new implicitly and locally created transaction.</span></span>  
  
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
  
3. <span data-ttu-id="55ba2-112">Configurez les liaisons dans le fichier de configuration, en spécifiant que le contexte de transaction doit être transmis, et les protocoles à utiliser pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="55ba2-112">Configure the bindings in the configuration file, specifying that the transaction context should be flowed, and the protocols to be used to do so.</span></span> <span data-ttu-id="55ba2-113">Pour plus d’informations, consultez [Configuration des transactions ServiceModel](servicemodel-transaction-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="55ba2-113">For more information, see [ServiceModel Transaction Configuration](servicemodel-transaction-configuration.md).</span></span> <span data-ttu-id="55ba2-114">Plus précisément, le type de liaison est spécifié dans l’attribut `binding` de l’élément de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="55ba2-114">Specifically, the binding type is specified in the endpoint element’s `binding` attribute.</span></span> <span data-ttu-id="55ba2-115">L' [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) élément contient un `bindingConfiguration` attribut qui référence une configuration de liaison nommée `transactionalOleTransactionsTcpBinding` , comme indiqué dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="55ba2-115">The [\<endpoint>](../../configure-apps/file-schema/wcf/endpoint-element.md) element contains a `bindingConfiguration` attribute that references a binding configuration named `transactionalOleTransactionsTcpBinding`, as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <service name="CalculatorService">  
      <endpoint address="net.tcp://localhost:8008/CalcService"  
        binding="netTcpBinding"  
        bindingConfiguration="transactionalOleTransactionsTcpBinding"  
        contract="ICalculator"  
        name="OleTransactions_endpoint" />  
    </service>  
    ```  
  
     <span data-ttu-id="55ba2-116">Le flux de transaction est activé au niveau de la configuration en utilisant l’attribut `transactionFlow`, et le protocole de transaction est spécifié à l’aide de l’attribut `transactionProtocol`, tel qu’indiqué dans la configuration suivante.</span><span class="sxs-lookup"><span data-stu-id="55ba2-116">Transaction flow is enabled at the configuration level by using the `transactionFlow` attribute, and the transaction protocol is specified using the `transactionProtocol` attribute, as shown in the following configuration.</span></span>  
  
    ```xml  
    <bindings>  
      <netTcpBinding>  
        <binding name="transactionalOleTransactionsTcpBinding"  
          transactionFlow="true"  
          transactionProtocol="OleTransactions"/>  
      </netTcpBinding>  
    </bindings>  
    ```  
  
### <a name="supporting-multiple-transaction-protocols"></a><span data-ttu-id="55ba2-117">Prise en charge de plusieurs protocoles de transaction</span><span class="sxs-lookup"><span data-stu-id="55ba2-117">Supporting multiple transaction protocols</span></span>  
  
1. <span data-ttu-id="55ba2-118">Pour des performances optimales, vous devez utiliser le protocole OleTransactions pour les scénarios impliquant un client et un service écrits à l’aide de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="55ba2-118">For optimal performance, you should use the OleTransactions protocol for scenarios involving a client and service written using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="55ba2-119">Cependant, le protocole WS-AT (WS-AtomicTransaction) est utile pour les scénarios où l'interopérabilité avec des piles de protocoles tierces est requise.</span><span class="sxs-lookup"><span data-stu-id="55ba2-119">However, the WS-AtomicTransaction (WS-AT) protocol is useful for scenarios when interoperability with third-party protocol stacks is required.</span></span> <span data-ttu-id="55ba2-120">Vous pouvez configurer les services WCF pour accepter les deux protocoles en fournissant plusieurs points de terminaison avec des liaisons spécifiques au protocole appropriées, comme indiqué dans l’exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="55ba2-120">You can configure WCF services to accept both protocols by providing multiple endpoints with appropriate protocol-specific bindings, as shown in the following sample configuration.</span></span>  
  
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
  
     <span data-ttu-id="55ba2-121">Le protocole de transaction est spécifié à l'aide de l'attribut `transactionProtocol`.</span><span class="sxs-lookup"><span data-stu-id="55ba2-121">The transaction protocol is specified using the `transactionProtocol` attribute.</span></span> <span data-ttu-id="55ba2-122">Cependant, cet attribut est absent du `wsHttpBinding` fourni par le système, car cette liaison peut uniquement utiliser le protocole WS-AT.</span><span class="sxs-lookup"><span data-stu-id="55ba2-122">However, this attribute is absent from the system-provided `wsHttpBinding`, because this binding can only use the WS-AT protocol.</span></span>  
  
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
  
### <a name="controlling-the-completion-of-a-transaction"></a><span data-ttu-id="55ba2-123">Contrôle de l'exécution d'une transaction</span><span class="sxs-lookup"><span data-stu-id="55ba2-123">Controlling the completion of a transaction</span></span>  
  
1. <span data-ttu-id="55ba2-124">Par défaut, les opérations WCF effectuent automatiquement des transactions si aucune exception non gérée n’est levée.</span><span class="sxs-lookup"><span data-stu-id="55ba2-124">By default, WCF operations automatically complete transactions if no unhandled exceptions are thrown.</span></span> <span data-ttu-id="55ba2-125">Vous pouvez modifier ce comportement à l'aide de la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> et de la méthode <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A>.</span><span class="sxs-lookup"><span data-stu-id="55ba2-125">You can modify this behavior by using the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property and the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method.</span></span> <span data-ttu-id="55ba2-126">Lorsqu’une opération doit s’exécuter dans la même transaction qu’une autre (par exemple, une opération de débit et de crédit), vous pouvez désactiver le comportement de saisie semi-automatique en affectant <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> à la propriété `false`, tel qu’indiqué dans l’exemple d’opération `Debit` suivant.</span><span class="sxs-lookup"><span data-stu-id="55ba2-126">When an operation is required to occur within the same transaction as another operation (for example, a debit and credit operation), you can disable the autocomplete behavior by setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` as shown in the following `Debit` operation example.</span></span> <span data-ttu-id="55ba2-127">La transaction utilisée par l'opération `Debit` ne s'exécute pas tant qu'une méthode avec la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> à la valeur `true` n'est pas appelée, tel qu'indiqué dans l'opération `Credit1`, ou lorsque la méthode <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> est appelée pour marquer explicitement la transaction comme étant exécutée, tel qu'indiqué dans l'opération `Credit2`.</span><span class="sxs-lookup"><span data-stu-id="55ba2-127">The transaction the `Debit` operation uses is not completed until a method with the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property set to `true` is called, as shown in the operation `Credit1`, or when the <xref:System.ServiceModel.OperationContext.SetTransactionComplete%2A> method is called to explicitly mark the transaction as complete, as shown in the operation `Credit2`.</span></span> <span data-ttu-id="55ba2-128">Notez que les deux opérations de crédit sont indiquées à titre d'exemple, et qu'une opération de crédit unique serait plus courante.</span><span class="sxs-lookup"><span data-stu-id="55ba2-128">Note that the two credit operations are shown for illustration purposes, and that a single credit operation would be more typical.</span></span>  
  
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
  
2. <span data-ttu-id="55ba2-129">Dans le cadre de la corrélation de transactions, l'affectation de <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> à la propriété `false` requiert l'utilisation d'une liaison de session.</span><span class="sxs-lookup"><span data-stu-id="55ba2-129">For the purposes of transaction correlation, setting the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete%2A> property to `false` requires the use of a sessionful binding.</span></span> <span data-ttu-id="55ba2-130">Cette exigence est spécifiée avec la propriété `SessionMode` sur <xref:System.ServiceModel.ServiceContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="55ba2-130">This requirement is specified with the `SessionMode` property on the <xref:System.ServiceModel.ServiceContractAttribute>.</span></span>  
  
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
  
### <a name="controlling-the-lifetime-of-a-transactional-service-instance"></a><span data-ttu-id="55ba2-131">Contrôle de la durée de vie d’une instance de service transactionnelle</span><span class="sxs-lookup"><span data-stu-id="55ba2-131">Controlling the lifetime of a transactional service instance</span></span>  
  
1. <span data-ttu-id="55ba2-132">WCF utilise la <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> propriété pour spécifier si l’instance de service sous-jacente est libérée lorsqu’une transaction se termine.</span><span class="sxs-lookup"><span data-stu-id="55ba2-132">WCF uses the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to specify whether the underlying service instance is released when a transaction completes.</span></span> <span data-ttu-id="55ba2-133">Dans la mesure où la valeur par défaut est `true` , sauf si elle est configurée dans le cas contraire, WCF présente un comportement d’activation « juste-à-temps » efficace et prévisible.</span><span class="sxs-lookup"><span data-stu-id="55ba2-133">Since this defaults to `true`, unless configured otherwise, WCF exhibits an efficient and predictable "just-in-time" activation behavior.</span></span> <span data-ttu-id="55ba2-134">Les appels à un service sur une transaction suivante sont assurés de disposer d'une nouvelle instance de service sans restes de l'état de la transaction précédente.</span><span class="sxs-lookup"><span data-stu-id="55ba2-134">Calls to a service on a subsequent transaction are assured a new service instance with no remnants of the previous transaction's state.</span></span> <span data-ttu-id="55ba2-135">Bien que cela s’avère souvent utile, vous pouvez souhaiter conserver l’état dans l’instance de service après l’exécution de la transaction.</span><span class="sxs-lookup"><span data-stu-id="55ba2-135">While this is often useful, sometimes you may want to maintain state within the service instance beyond the transaction completion.</span></span> <span data-ttu-id="55ba2-136">Ce peut être le cas, par exemple, lorsque l'état requis ou des handles vers des ressources sont coûteux à récupérer ou à reconstituer.</span><span class="sxs-lookup"><span data-stu-id="55ba2-136">Examples of this would be when required state or handles to resources are expensive to retrieve or reconstitute.</span></span> <span data-ttu-id="55ba2-137">Pour ce faire, vous pouvez affecter <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> à la propriété `false`.</span><span class="sxs-lookup"><span data-stu-id="55ba2-137">You can do this by setting the <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A> property to `false`.</span></span> <span data-ttu-id="55ba2-138">Avec ce paramètre, l'instance et les états associés seront disponibles sur les appels suivants.</span><span class="sxs-lookup"><span data-stu-id="55ba2-138">With that setting, the instance and any associated state will be available on subsequent calls.</span></span> <span data-ttu-id="55ba2-139">Lorsque vous utilisez ce paramètre, tenez compte du moment auquel et de la manière dont les transactions et l’état seront effacés et exécutés.</span><span class="sxs-lookup"><span data-stu-id="55ba2-139">When using this, give careful consideration to when and how state and transactions will be cleared and completed.</span></span> <span data-ttu-id="55ba2-140">L'exemple suivant montre comment procéder en conservant l'instance avec la variable `runningTotal`.</span><span class="sxs-lookup"><span data-stu-id="55ba2-140">The following sample demonstrates how to do this by maintaining the instance with the `runningTotal` variable.</span></span>  
  
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
    > <span data-ttu-id="55ba2-141">La durée de vie d'instance étant un comportement interne au service et contrôlée via la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute>, aucune modification de la configuration de service ou du contrat de service n'est nécessaire pour définir le comportement d'instance.</span><span class="sxs-lookup"><span data-stu-id="55ba2-141">Since the instance lifetime is a behavior that is internal to the service, and controlled through the <xref:System.ServiceModel.ServiceBehaviorAttribute> property, no modification to the service configuration or service contract is required to set the instance behavior.</span></span> <span data-ttu-id="55ba2-142">Par ailleurs, le câble ne contiendra pas de représentation de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="55ba2-142">In addition, the wire will contain no representation of this.</span></span>
