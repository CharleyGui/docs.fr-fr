---
title: Service Transaction Behavior
ms.date: 03/30/2017
helpviewer_keywords:
- Service Transaction Behavior Sample [Windows Communication Foundation]
ms.assetid: 1a9842a3-e84d-427c-b6ac-6999cbbc2612
ms.openlocfilehash: 0be5bf0dbe6416febb898fb5150c5a516c8b0969
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84591525"
---
# <a name="service-transaction-behavior"></a><span data-ttu-id="5a82f-102">Service Transaction Behavior</span><span class="sxs-lookup"><span data-stu-id="5a82f-102">Service Transaction Behavior</span></span>

<span data-ttu-id="5a82f-103">Cet exemple illustre l’utilisation d’une transaction coordonnée par le client et les paramètres de ServiceBehaviorAttribute et OperationBehaviorAttribute pour contrôler le comportement de la transaction du service.</span><span class="sxs-lookup"><span data-stu-id="5a82f-103">This sample demonstrates the use of a client-coordinated transaction and the settings of ServiceBehaviorAttribute and OperationBehaviorAttribute to control service transaction behavior.</span></span> <span data-ttu-id="5a82f-104">Cet exemple est basé sur la [prise en main](getting-started-sample.md) qui implémente un service de calculatrice, mais qui est étendu pour conserver un journal du serveur des opérations effectuées dans une table de base de données et un total des exécutions avec état pour les opérations de calculatrice.</span><span class="sxs-lookup"><span data-stu-id="5a82f-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service, but is extended to maintain a server log of the performed operations in a database table and a stateful running total for the calculator operations.</span></span> <span data-ttu-id="5a82f-105">Les écritures rendues persistantes dans la table du journal de serveur dépendent du résultat d'une transaction coordonnée par le client : si la transaction cliente ne se complète pas, la transaction de service Web garantit que les mises à jour de la base de données ne sont pas validées.</span><span class="sxs-lookup"><span data-stu-id="5a82f-105">Persisted writes to the server log table are dependent upon the outcome of a client coordinated transaction - if the client transaction does not complete, the Web service transaction ensures that the updates to the database are not committed.</span></span>

> [!NOTE]
> <span data-ttu-id="5a82f-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="5a82f-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="5a82f-107">Le contrat pour le service définit que toutes les opérations requièrent qu’une transaction soit transmise avec les demandes :</span><span class="sxs-lookup"><span data-stu-id="5a82f-107">The contract for the service defines that all of the operations require a transaction to be flowed with requests:</span></span>

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples",
                    SessionMode = SessionMode.Required)]
public interface ICalculator
{
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Add(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Subtract(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Multiply(double n);
    [OperationContract]
    [TransactionFlow(TransactionFlowOption.Mandatory)]
    double Divide(double n);
}
```

<span data-ttu-id="5a82f-108">Pour activer le flux de transaction entrant, le service est configuré avec la wsHttpBinding fournie par le système, avec l’attribut transactionFlow ayant la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="5a82f-108">To enable the incoming transaction flow, the service is configured with the system-provided wsHttpBinding with the transactionFlow attribute set to `true`.</span></span> <span data-ttu-id="5a82f-109">Cette liaison utilise le protocole WSAtomicTransactionOctober2004 interopérable :</span><span class="sxs-lookup"><span data-stu-id="5a82f-109">This binding uses the interoperable WSAtomicTransactionOctober2004 protocol:</span></span>

```xml
<bindings>
  <wsHttpBinding>
    <binding name="transactionalBinding" transactionFlow="true" />
  </wsHttpBinding>
</bindings>
```

<span data-ttu-id="5a82f-110">Après avoir initialisé à la fois une connexion au service et une transaction, le client accède à plusieurs opérations de service dans l’étendue de cette transaction, puis complète la transaction et ferme la connexion :</span><span class="sxs-lookup"><span data-stu-id="5a82f-110">After initiating both a connection to the service and a transaction, the client accesses several service operations within the scope of that transaction and then completes the transaction and closes the connection:</span></span>

```csharp
// Create a client
CalculatorClient client = new CalculatorClient();

// Create a transaction scope with the default isolation level of Serializable
using (TransactionScope tx = new TransactionScope())
{
    Console.WriteLine("Starting transaction");

    // Call the Add service operation.
    double value = 100.00D;
    Console.WriteLine("  Adding {0}, running total={1}",
                                        value, client.Add(value));

    // Call the Subtract service operation.
    value = 45.00D;
    Console.WriteLine("  Subtracting {0}, running total={1}",
                                        value, client.Subtract(value));

    // Call the Multiply service operation.
    value = 9.00D;
    Console.WriteLine("  Multiplying by {0}, running total={1}",
                                        value, client.Multiply(value));

    // Call the Divide service operation.
    value = 15.00D;
    Console.WriteLine("  Dividing by {0}, running total={1}",
                                        value, client.Divide(value));

    Console.WriteLine("  Completing transaction");
    tx.Complete();
}

Console.WriteLine("Transaction committed");

// Closing the client gracefully closes the connection and cleans up resources
client.Close();
```

<span data-ttu-id="5a82f-111">Sur le service, il y a trois attributs qui affectent le comportement de la transaction de service, et qui procèdent comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a82f-111">On the service, there are three attributes that affect the service transaction behavior, and they do so in the following ways:</span></span>

- <span data-ttu-id="5a82f-112">Sur le `ServiceBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="5a82f-112">On the `ServiceBehaviorAttribute`:</span></span>

  - <span data-ttu-id="5a82f-113">La propriété `TransactionTimeout` spécifie le délai dans lequel une nouvelle transaction doit s’exécuter.</span><span class="sxs-lookup"><span data-stu-id="5a82f-113">The `TransactionTimeout` property specifies the time period within which a transaction must complete.</span></span> <span data-ttu-id="5a82f-114">Dans cet exemple, elle a pour valeur 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="5a82f-114">In this sample it is set to 30 seconds.</span></span>

  - <span data-ttu-id="5a82f-115">La propriété `TransactionIsolationLevel` spécifie le niveau d'isolation que le service prend en charge.</span><span class="sxs-lookup"><span data-stu-id="5a82f-115">The `TransactionIsolationLevel` property specifies the isolation level that the service supports.</span></span> <span data-ttu-id="5a82f-116">Il doit correspondre au niveau d'isolation du client.</span><span class="sxs-lookup"><span data-stu-id="5a82f-116">This is required to match the client's isolation level.</span></span>

  - <span data-ttu-id="5a82f-117">La propriété `ReleaseServiceInstanceOnTransactionComplete` spécifie si l'instance de service sous-jacente est recyclée à la fin de l'exécution d'une transaction.</span><span class="sxs-lookup"><span data-stu-id="5a82f-117">The `ReleaseServiceInstanceOnTransactionComplete` property specifies whether the service instance is recycled when a transaction completes.</span></span> <span data-ttu-id="5a82f-118">Si elle a la valeur `false`, le service maintient la même instance de service à travers les demandes de l'opération.</span><span class="sxs-lookup"><span data-stu-id="5a82f-118">By setting it to `false`, the service maintains the same service instance across the operation requests.</span></span> <span data-ttu-id="5a82f-119">Cela est nécessaire pour maintenir le total évolutif.</span><span class="sxs-lookup"><span data-stu-id="5a82f-119">This is required to maintain the running total.</span></span> <span data-ttu-id="5a82f-120">Si elle a la valeur `true`, une nouvelle instance est générée après chaque action complétée.</span><span class="sxs-lookup"><span data-stu-id="5a82f-120">If set to `true`, a new instance is generated after each completed action.</span></span>

  - <span data-ttu-id="5a82f-121">La propriété `TransactionAutoCompleteOnSessionClose` spécifie si les transactions en attente sont exécutées lorsque la session se ferme.</span><span class="sxs-lookup"><span data-stu-id="5a82f-121">The `TransactionAutoCompleteOnSessionClose` property specifies whether outstanding transactions are completed when the session closes.</span></span> <span data-ttu-id="5a82f-122">En lui affectant `false` la valeur, les opérations individuelles sont requises pour affecter à la propriété la valeur <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> `true` ou pour exiger explicitement un appel à la <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> méthode pour terminer des transactions.</span><span class="sxs-lookup"><span data-stu-id="5a82f-122">By setting it to `false`, the individual operations are required to either set the <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete?displayProperty=nameWithType> property to `true` or to explicitly require a call to the <xref:System.ServiceModel.OperationContext.SetTransactionComplete?displayProperty=nameWithType> method to complete transactions.</span></span> <span data-ttu-id="5a82f-123">Cet exemple illustre les deux approches.</span><span class="sxs-lookup"><span data-stu-id="5a82f-123">This sample demonstrates both approaches.</span></span>

- <span data-ttu-id="5a82f-124">Sur le `ServiceContractAttribute` :</span><span class="sxs-lookup"><span data-stu-id="5a82f-124">On the `ServiceContractAttribute`:</span></span>

  - <span data-ttu-id="5a82f-125">La propriété `SessionMode` spécifie si le service met en corrélation les demandes appropriées dans une session logique.</span><span class="sxs-lookup"><span data-stu-id="5a82f-125">The `SessionMode` property specifies whether the service correlates the appropriate requests into a logical session.</span></span> <span data-ttu-id="5a82f-126">Étant donné que ce service inclut des opérations où la propriété OperationBehaviorAttribute TransactionAutoComplete a la valeur `false` (multiplication et division), `SessionMode.Required` doit être spécifié.</span><span class="sxs-lookup"><span data-stu-id="5a82f-126">Because this service includes operations where the OperationBehaviorAttribute TransactionAutoComplete property is set to `false` (Multiply and Divide), `SessionMode.Required` must be specified.</span></span> <span data-ttu-id="5a82f-127">Par exemple, l’opération de multiplication n’exécute pas sa transaction et à la place compte sur un appel ultérieur à l’opération de division pour s’exécuter à l’aide de la méthode `SetTransactionComplete` ; le service doit être en mesure de déterminer que ces opérations se produisent dans la même session.</span><span class="sxs-lookup"><span data-stu-id="5a82f-127">For example, the Multiply operation does not complete its transaction and instead relies upon a later call to Divide to complete using the `SetTransactionComplete` method; the service must be able to determine that these operations are occurring within the same session.</span></span>

- <span data-ttu-id="5a82f-128">Sur le `OperationBehaviorAttribute` :</span><span class="sxs-lookup"><span data-stu-id="5a82f-128">On the `OperationBehaviorAttribute`:</span></span>

  - <span data-ttu-id="5a82f-129">La propriété `TransactionScopeRequired` spécifie si les actions de l'opération doivent être exécutées dans une étendue de transaction.</span><span class="sxs-lookup"><span data-stu-id="5a82f-129">The `TransactionScopeRequired` property specifies whether the operation's actions should be executed within a transaction scope.</span></span> <span data-ttu-id="5a82f-130">Elle a la valeur `true` pour toutes les opérations dans cet exemple et, vu que le client transmet sa transaction à toutes les opérations, les actions se produisent dans l'étendue de cette transaction cliente.</span><span class="sxs-lookup"><span data-stu-id="5a82f-130">This is set to `true` for all operations in this sample and, because the client flows its transaction to all operations, the actions occur within the scope of that client transaction.</span></span>

  - <span data-ttu-id="5a82f-131">La propriété `TransactionAutoComplete` spécifie si la transaction dans laquelle la méthode s’exécute est automatiquement effectuée si aucune exception non prise en charge n’est levée.</span><span class="sxs-lookup"><span data-stu-id="5a82f-131">The `TransactionAutoComplete` property specifies whether the transaction in which the method executes is automatically completed if no unhandled exceptions occur.</span></span> <span data-ttu-id="5a82f-132">Comme décrit précédemment, cette propriété a la valeur `true` pour les opérations d'addition et de soustraction mais `false` pour les opérations de multiplication et de division.</span><span class="sxs-lookup"><span data-stu-id="5a82f-132">As previously described, this is set to `true` for the Add and Subtract operations but `false` for the Multiply and Divide operations.</span></span> <span data-ttu-id="5a82f-133">Les opérations d'addition et de soustraction s'exécutent automatiquement, l'opération de division s'exécute à travers un appel explicite à la méthode `SetTransactionComplete`, et l'opération de multiplication ne s'exécute mais à la place compte sur un appel ultérieur obligatoire, à l'opération de division par exemple, pour s'exécuter.</span><span class="sxs-lookup"><span data-stu-id="5a82f-133">The Add and Subtract operations complete their actions automatically, the Divide completes its actions through an explicit call to the `SetTransactionComplete` method, and the Multiply does not complete its actions but instead relies upon and requires a later call, such as to Divide, to complete the actions.</span></span>

<span data-ttu-id="5a82f-134">L'implémentation du service doté d'attributs se déroule comme suit :</span><span class="sxs-lookup"><span data-stu-id="5a82f-134">The attributed service implementation is as follows:</span></span>

```csharp
[ServiceBehavior(
    TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable,
    TransactionTimeout = "00:00:30",
    ReleaseServiceInstanceOnTransactionComplete = false,
    TransactionAutoCompleteOnSessionClose = false)]
public class CalculatorService : ICalculator
{
    double runningTotal;

    public CalculatorService()
    {
        Console.WriteLine("Creating new service instance...");
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public double Add(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n, runningTotal));
        runningTotal = runningTotal + n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public double Subtract(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n, runningTotal));
        runningTotal = runningTotal - n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]
    public double Multiply(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", runningTotal, n));
        runningTotal = runningTotal * n;
        return runningTotal;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = false)]
    public double Divide(double n)
    {
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", runningTotal, n));
        runningTotal = runningTotal / n;
        OperationContext.Current.SetTransactionComplete();
        return runningTotal;
    }

    // Logging method omitted for brevity
}
```

<span data-ttu-id="5a82f-135">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="5a82f-135">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5a82f-136">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="5a82f-136">Press ENTER in the client window to shut down the client.</span></span>

```console
Starting transaction
Performing calculations...
  Adding 100, running total=100
  Subtracting 45, running total=55
  Multiplying by 9, running total=495
  Dividing by 15, running total=33
  Completing transaction
Transaction committed
Press <ENTER> to terminate client.
```

<span data-ttu-id="5a82f-137">Le journal des demandes faites à l'opération de service est visible dans la fenêtre de console du service.</span><span class="sxs-lookup"><span data-stu-id="5a82f-137">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="5a82f-138">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="5a82f-138">Press ENTER in the client window to shut down the client.</span></span>

```console
Press <ENTER> to terminate service.
Creating new service instance...
  Writing row 1 to database: Adding 100 to 0
  Writing row 2 to database: Subtracting 45 from 100
  Writing row 3 to database: Multiplying 55 by 9
  Writing row 4 to database: Dividing 495 by 15
```

<span data-ttu-id="5a82f-139">Notez qu'en plus de conserver le total évolutif des calculs, le service signale la création d'instances (une instance pour cet exemple) et enregistre les demandes d'opération dans une base de données.</span><span class="sxs-lookup"><span data-stu-id="5a82f-139">Note that in addition to keeping the running total of the calculations, the service reports the creation of instances (one instance for this sample) and logs the operation requests to a database.</span></span> <span data-ttu-id="5a82f-140">Étant donné que toutes les demandes transmettent la transaction du client, tout échec d'exécution de cette transaction entraîne la restauration de toutes les opérations de la base de données.</span><span class="sxs-lookup"><span data-stu-id="5a82f-140">Because all of the requests flow the client's transaction, any failure to complete that transaction results in all of the database operations being rolled back.</span></span> <span data-ttu-id="5a82f-141">Cela peut être démontré de plusieurs manières :</span><span class="sxs-lookup"><span data-stu-id="5a82f-141">This can be demonstrated in a number of ways:</span></span>

- <span data-ttu-id="5a82f-142">Supprimez l’appel du client à `tx.Complete` () et répétez la transaction : le client quitte l’étendue de la transaction sans l’exécuter.</span><span class="sxs-lookup"><span data-stu-id="5a82f-142">Comment out the client's call to `tx.Complete`() and rerun - this results in the client exiting the transaction scope without completing its transaction.</span></span>

- <span data-ttu-id="5a82f-143">Supprimez l'appel à l'opération de division du service : cela empêche l'action initiée par l'opération de multiplication de s'effectuer. Par conséquent, la transaction du client échoue également.</span><span class="sxs-lookup"><span data-stu-id="5a82f-143">Comment out the call to the Divide service operation - this results prevent the action initiated by the Multiply operation from completing and thus the client's transaction ultimately also fails to complete.</span></span>

- <span data-ttu-id="5a82f-144">Levez une exception non gérée n’importe où dans l’étendue de transaction du client : cela empêche également le client d’exécuter sa transaction.</span><span class="sxs-lookup"><span data-stu-id="5a82f-144">Throw an unhandled exception anywhere in the client's transaction scope - this similarly prevents the client from completing its transaction.</span></span>

<span data-ttu-id="5a82f-145">Le résultat est toujours le même : aucune des opérations exécutées dans cette étendue n’est validée et le nombre de lignes rendues persistantes dans la base de données n’est pas incrémenté.</span><span class="sxs-lookup"><span data-stu-id="5a82f-145">The result of any of these is that none of the operations performed within that scope are committed and the count of rows persisted to the database do not increment.</span></span>

> [!NOTE]
> <span data-ttu-id="5a82f-146">Dans le cadre du processus de génération, le fichier de la base de données est copié dans le dossier bin.</span><span class="sxs-lookup"><span data-stu-id="5a82f-146">As part of the build process the database file is copied to the bin folder.</span></span> <span data-ttu-id="5a82f-147">Vous devez examiner cette copie du fichier de la base de données pour observer les lignes rendues persistantes dans le journal plutôt que dans le fichier inclus dans le projet Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a82f-147">You must look at that copy of the database file to observe the rows that are persisted to the log rather than the file that is included in the Visual Studio project.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5a82f-148">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="5a82f-148">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="5a82f-149">Vérifiez que vous avez installé SQL Server 2005 Express Edition ou SQL Server 2005.</span><span class="sxs-lookup"><span data-stu-id="5a82f-149">Ensure that you have installed SQL Server 2005 Express Edition or SQL Server 2005.</span></span> <span data-ttu-id="5a82f-150">Dans le fichier App.config du service, le `connectionString` de la base de données peut être défini ou les interactions avec la base de données peuvent être désactivées en affectant `usingSql` à la valeur `false` d'appSettings.</span><span class="sxs-lookup"><span data-stu-id="5a82f-150">In the service's App.config file, the database `connectionString` may be set or the database interactions may be disabled by setting the appSettings `usingSql` value to `false`.</span></span>

2. <span data-ttu-id="5a82f-151">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a82f-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

3. <span data-ttu-id="5a82f-152">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5a82f-152">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>

<span data-ttu-id="5a82f-153">Si vous exécutez l’exemple sur plusieurs ordinateurs, vous devez configurer le Distributed Transaction Coordinator Microsoft (MSDTC) pour activer le workflow de transaction réseau et utiliser l’outil WsatConfig. exe pour activer la prise en charge réseau des transactions Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5a82f-153">If you run the sample across machines, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable Windows Communication Foundation (WCF) transactions network support.</span></span>

### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample-across-machines"></a><span data-ttu-id="5a82f-154">Pour configurer le Microsoft Distributed Transaction Coordinator (MSDTC) de manière à prendre en charge l’exécution de l’exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="5a82f-154">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample across machines</span></span>

1. <span data-ttu-id="5a82f-155">Sur l'ordinateur de service, configurez MSDTC pour autoriser des transactions réseau entrantes.</span><span class="sxs-lookup"><span data-stu-id="5a82f-155">On the service machine, configure MSDTC to allow incoming network transactions.</span></span>

    1. <span data-ttu-id="5a82f-156">Dans le menu **Démarrer** , accédez à **panneau de configuration**, puis **Outils d’administration**et **services de composants**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-156">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="5a82f-157">Cliquez avec le bouton droit sur **poste de travail** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-157">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="5a82f-158">Sous l’onglet **MSDTC** , cliquez sur Configuration de la **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-158">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="5a82f-159">Cochez **accès DTC réseau** et **autoriser les transactions entrantes**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-159">Check **Network DTC Access** and **Allow Inbound**.</span></span>

    5. <span data-ttu-id="5a82f-160">Cliquez sur **Oui** pour redémarrer le service MS DTC, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-160">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="5a82f-161">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5a82f-161">Click **OK** to close the dialog box.</span></span>

2. <span data-ttu-id="5a82f-162">Sur l’ordinateur du service et l’ordinateur du client, configurez le Pare-feu Windows pour inclure le Microsoft Distributed Transaction Coordinator (MSDTC) à la liste des exceptions :</span><span class="sxs-lookup"><span data-stu-id="5a82f-162">On the service machine and the client machine, configure the Windows Firewall to include the Microsoft Distributed Transaction Coordinator (MSDTC) to the list of excepted applications:</span></span>

    1. <span data-ttu-id="5a82f-163">Exécutez l'application de Pare-feu Windows à partir du Panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="5a82f-163">Run the Windows Firewall application from Control Panel.</span></span>

    2. <span data-ttu-id="5a82f-164">Sous l’onglet **exceptions** , cliquez sur **Ajouter un programme**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-164">From the **Exceptions** tab, click **Add Program**.</span></span>

    3. <span data-ttu-id="5a82f-165">Naviguez jusqu’au dossier C:\WINDOWS\System32.</span><span class="sxs-lookup"><span data-stu-id="5a82f-165">Browse to the folder C:\WINDOWS\System32.</span></span>

    4. <span data-ttu-id="5a82f-166">Sélectionnez MSDTC. exe, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-166">Select Msdtc.exe and click **Open**.</span></span>

    5. <span data-ttu-id="5a82f-167">Cliquez sur **OK** pour fermer la boîte de dialogue **Ajouter un programme** , puis cliquez à nouveau sur **OK** pour fermer l’applet du pare-feu Windows.</span><span class="sxs-lookup"><span data-stu-id="5a82f-167">Click **OK** to close the **Add Program** dialog box, and click **OK** again to close the Windows Firewall applet.</span></span>

3. <span data-ttu-id="5a82f-168">Sur l'ordinateur client, configurez MSDTC pour autoriser les transactions réseau sortantes :</span><span class="sxs-lookup"><span data-stu-id="5a82f-168">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>

    1. <span data-ttu-id="5a82f-169">Dans le menu **Démarrer** , accédez à **panneau de configuration**, puis **Outils d’administration**et **services de composants**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>

    2. <span data-ttu-id="5a82f-170">Cliquez avec le bouton droit sur **poste de travail** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-170">Right-click **My Computer** and select **Properties**.</span></span>

    3. <span data-ttu-id="5a82f-171">Sous l’onglet **MSDTC** , cliquez sur Configuration de la **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-171">On the **MSDTC** tab, click **Security Configuration**.</span></span>

    4. <span data-ttu-id="5a82f-172">Cochez **accès DTC réseau** et **autoriser les transactions sortantes**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-172">Check **Network DTC Access** and **Allow Outbound**.</span></span>

    5. <span data-ttu-id="5a82f-173">Cliquez sur **Oui** pour redémarrer le service MS DTC, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="5a82f-173">Click **Yes** to restart the MS DTC service and then click **OK**.</span></span>

    6. <span data-ttu-id="5a82f-174">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="5a82f-174">Click **OK** to close the dialog box.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a82f-175">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="5a82f-175">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5a82f-176">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="5a82f-176">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="5a82f-177">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="5a82f-177">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5a82f-178">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="5a82f-178">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Transactions`
