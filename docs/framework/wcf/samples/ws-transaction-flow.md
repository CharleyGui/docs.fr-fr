---
title: WS Transaction Flow
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 781934e9ab27f761e71841c2edc509f9b8022aa7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094746"
---
# <a name="ws-transaction-flow"></a><span data-ttu-id="39506-102">WS Transaction Flow</span><span class="sxs-lookup"><span data-stu-id="39506-102">WS Transaction Flow</span></span>
<span data-ttu-id="39506-103">Cet exemple illustre l’utilisation d’une transaction coordonnée par le client et des options de client et de serveur pour le flux de transaction, à l’aide du protocole WS-Atomic Transaction ou OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="39506-103">This sample demonstrates the use of a client-coordinated transaction and the client and server options for transaction flow using either the WS-Atomic Transaction or OleTransactions protocol.</span></span> <span data-ttu-id="39506-104">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice, mais les opérations sont attribuées pour démontrer l’utilisation de l' `TransactionFlowAttribute` avec l’énumération **TransactionFlowOption** pour déterminer à quel degré le workflow de transaction est activé.</span><span class="sxs-lookup"><span data-stu-id="39506-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service but the operations are attributed to demonstrate the use of the `TransactionFlowAttribute` with the **TransactionFlowOption** enumeration to determine to what degree transaction flow is enabled.</span></span> <span data-ttu-id="39506-105">Dans l'étendue de la transaction passée, un journal des opérations demandées est écrit dans une base de données et est conservé jusqu'à ce que la transaction coordonnée par le client soit terminée. Si la transaction cliente ne se termine pas, la transaction de service Web garantit que les mises à jour appropriées de la base de données ne sont pas validées.</span><span class="sxs-lookup"><span data-stu-id="39506-105">Within the scope of the flowed transaction, a log of the requested operations is written to a database and persists until the client coordinated transaction has completed - if the client transaction does not complete, the Web service transaction ensures that the appropriate updates to the database are not committed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39506-106">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="39506-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="39506-107">Après avoir initialisé une connexion au service et une transaction, le client accède à plusieurs opérations de service.</span><span class="sxs-lookup"><span data-stu-id="39506-107">After initiating a connection to the service and a transaction, the client accesses several service operations.</span></span> <span data-ttu-id="39506-108">Le contrat de service est défini comme suit avec chacune des opérations qui montrent un paramètre différent pour `TransactionFlowOption`.</span><span class="sxs-lookup"><span data-stu-id="39506-108">The contract for the service is defined as follows with each of the operations demonstrating a different setting for the `TransactionFlowOption`.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Mandatory)]  
    double Add(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.Allowed)]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    [TransactionFlow(TransactionFlowOption.NotAllowed)]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);   
}  
```

 <span data-ttu-id="39506-109">Cela permet de définir les opérations dans l'ordre dans lequel elles seront traitées :</span><span class="sxs-lookup"><span data-stu-id="39506-109">This defines the operations in the order they are to be processed:</span></span>  
  
- <span data-ttu-id="39506-110">Une demande d’opération `Add` doit inclure une transaction passée.</span><span class="sxs-lookup"><span data-stu-id="39506-110">An `Add` operation request must include a flowed transaction.</span></span>  
  
- <span data-ttu-id="39506-111">Une demande d’opération `Subtract` peut inclure une transaction passée.</span><span class="sxs-lookup"><span data-stu-id="39506-111">A `Subtract` operation request may include a flowed transaction.</span></span>  
  
- <span data-ttu-id="39506-112">Une demande d’opération `Multiply` ne doit pas inclure de transaction passée par l’intermédiaire du paramètre NotAllowed explicite.</span><span class="sxs-lookup"><span data-stu-id="39506-112">A `Multiply` operation request must not include a flowed transaction through the explicit NotAllowed setting.</span></span>  
  
- <span data-ttu-id="39506-113">Une demande d'opération `Divide` ne doit pas inclure de transaction passée par omission d'un attribut `TransactionFlow`.</span><span class="sxs-lookup"><span data-stu-id="39506-113">A `Divide` operation request must not include a flowed transaction through the omission of a `TransactionFlow` attribute.</span></span>  
  
 <span data-ttu-id="39506-114">Pour activer le workflow de transaction, les liaisons avec la propriété [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) activée doivent être utilisées en plus des attributs d’opération appropriés.</span><span class="sxs-lookup"><span data-stu-id="39506-114">To enable transaction flow, bindings with the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled must be used in addition to the appropriate operation attributes.</span></span> <span data-ttu-id="39506-115">Dans cet exemple, la configuration du service expose un point de terminaison TCP et un point de terminaison HTTP en plus du point de terminaison d'échange de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="39506-115">In this sample, the service's configuration exposes a TCP endpoint and an HTTP endpoint in addition to a Metadata Exchange endpoint.</span></span> <span data-ttu-id="39506-116">Le point de terminaison TCP et le point de terminaison HTTP utilisent les liaisons suivantes, qui ont la propriété [\<transactionFlow >](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) activée.</span><span class="sxs-lookup"><span data-stu-id="39506-116">The TCP endpoint and the HTTP endpoint use the following bindings, both of which have the [\<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) property enabled.</span></span>  
  
```xml  
<bindings>  
  <netTcpBinding>  
    <binding name="transactionalOleTransactionsTcpBinding"  
             transactionFlow="true"  
             transactionProtocol="OleTransactions"/>  
  </netTcpBinding>  
  <wsHttpBinding>  
    <binding name="transactionalWsatHttpBinding"  
             transactionFlow="true" />  
  </wsHttpBinding>  
</bindings>  
```  
  
> [!NOTE]
> <span data-ttu-id="39506-117">netTcpBinding fourni par le système autorise la spécification de transactionProtocol alors que wsHttpBinding fourni par le système utilise uniquement le protocole WSAtomicTransactionOctober2004 plus interopérable.</span><span class="sxs-lookup"><span data-stu-id="39506-117">The system-provided netTcpBinding allows specification of the transactionProtocol whereas the system-provided wsHttpBinding uses only the more interoperable WSAtomicTransactionOctober2004 protocol.</span></span> <span data-ttu-id="39506-118">Le protocole OleTransactions est uniquement disponible pour une utilisation par les clients Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="39506-118">The OleTransactions protocol is only available for use by Windows Communication Foundation (WCF) clients.</span></span>  
  
 <span data-ttu-id="39506-119">Pour la classe qui implémente l'interface `ICalculator`, toutes les méthodes sont attribuées avec la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> définie sur `true`.</span><span class="sxs-lookup"><span data-stu-id="39506-119">For the class that implements the `ICalculator` interface, all of the methods are attributed with <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property set to `true`.</span></span> <span data-ttu-id="39506-120">Ce paramètre déclare que toutes les actions prises dans la méthode se produisent dans l’étendue d’une transaction.</span><span class="sxs-lookup"><span data-stu-id="39506-120">This setting declares that all actions taken within the method occur within the scope of a transaction.</span></span> <span data-ttu-id="39506-121">Dans ce cas, les actions prises incluent l'enregistrement dans la base de données journal.</span><span class="sxs-lookup"><span data-stu-id="39506-121">In this case, the actions taken include recording to the log database.</span></span> <span data-ttu-id="39506-122">Si la demande d’opération inclut une transaction passée, les actions se produisent alors dans l’étendue de la transaction entrante ou une nouvelle étendue de transaction est automatiquement générée.</span><span class="sxs-lookup"><span data-stu-id="39506-122">If the operation request includes a flowed transaction then the actions occur within the scope of the incoming transaction or a new transaction scope is automatically generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="39506-123">La propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> définit le comportement local appliqué aux implémentations de méthode de service et ne définit pas la capacité du client à transmettre la transaction, ni l'obligation de cette transmission.</span><span class="sxs-lookup"><span data-stu-id="39506-123">The <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> property defines behavior local to the service method implementations and does not define the client's ability to or requirement for flowing a transaction.</span></span>  

```csharp
// Service class that implements the service contract.  
[ServiceBehavior(TransactionIsolationLevel = System.Transactions.IsolationLevel.Serializable)]  
public class CalculatorService : ICalculator  
{  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Add(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Adding {0} to {1}", n1, n2));  
        return n1 + n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Subtract(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Subtracting {0} from {1}", n2, n1));  
        return n1 - n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Multiply(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Multiplying {0} by {1}", n1, n2));  
        return n1 * n2;  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true)]  
    public double Divide(double n1, double n2)  
    {  
        RecordToLog(String.Format(CultureInfo.CurrentCulture, "Dividing {0} by {1}", n1, n2));  
        return n1 / n2;  
    }  
  
    // Logging method omitted for brevity  
}  
```

 <span data-ttu-id="39506-124">Sur le client, les paramètres `TransactionFlowOption` du service sur les opérations sont répercutés dans la définition générée du client de l'interface `ICalculator`.</span><span class="sxs-lookup"><span data-stu-id="39506-124">On the client, the service's `TransactionFlowOption` settings on the operations are reflected in the client's generated definition of the `ICalculator` interface.</span></span> <span data-ttu-id="39506-125">De plus, les paramètres de la propriété `transactionFlow` du service sont répercutés dans la configuration de l'application du client.</span><span class="sxs-lookup"><span data-stu-id="39506-125">Also, the service's `transactionFlow` property settings are reflected in the client's application configuration.</span></span> <span data-ttu-id="39506-126">Le client peut sélectionner le transport et le protocole en sélectionnant le `endpointConfigurationName` approprié.</span><span class="sxs-lookup"><span data-stu-id="39506-126">The client can select the transport and protocol by selecting the appropriate `endpointConfigurationName`.</span></span>  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> <span data-ttu-id="39506-127">Le comportement observé de cet exemple est le même, quel que soit le protocole ou le transport choisi.</span><span class="sxs-lookup"><span data-stu-id="39506-127">The observed behavior of this sample is the same no matter which protocol or transport is chosen.</span></span>  
  
 <span data-ttu-id="39506-128">Une fois la connexion au service initialisée, le client crée un `TransactionScope` autour des appels aux opérations de service.</span><span class="sxs-lookup"><span data-stu-id="39506-128">Having initiated the connection to the service, the client creates a new `TransactionScope` around the calls to the service operations.</span></span>  

```csharp
// Start a transaction scope  
using (TransactionScope tx =  
            new TransactionScope(TransactionScopeOption.RequiresNew))  
{  
    Console.WriteLine("Starting transaction");  
  
    // Call the Add service operation  
    //  - generatedClient will flow the required active transaction  
    double value1 = 100.00D;  
    double value2 = 15.99D;  
    double result = client.Add(value1, value2);  
    Console.WriteLine("  Add({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Subtract service operation  
    //  - generatedClient will flow the allowed active transaction  
    value1 = 145.00D;  
    value2 = 76.54D;  
    result = client.Subtract(value1, value2);  
    Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
    // Start a transaction scope that suppresses the current transaction  
    using (TransactionScope txSuppress =  
                new TransactionScope(TransactionScopeOption.Suppress))  
    {  
        // Call the Subtract service operation  
        //  - the active transaction is suppressed from the generatedClient  
        //    and no transaction will flow  
        value1 = 21.05D;  
        value2 = 42.16D;  
        result = client.Subtract(value1, value2);  
        Console.WriteLine("  Subtract({0},{1}) = {2}", value1, value2, result);  
  
        // Complete the suppressed scope  
        txSuppress.Complete();  
    }  
  
    // Call the Multiply service operation  
    // - generatedClient will not flow the active transaction  
    value1 = 9.00D;  
    value2 = 81.25D;  
    result = client.Multiply(value1, value2);  
    Console.WriteLine("  Multiply({0},{1}) = {2}", value1, value2, result);  
  
    // Call the Divide service operation.  
    // - generatedClient will not flow the active transaction  
    value1 = 22.00D;  
    value2 = 7.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("  Divide({0},{1}) = {2}", value1, value2, result);  
  
    // Complete the transaction scope  
    Console.WriteLine("  Completing transaction");  
    tx.Complete();  
}  
  
Console.WriteLine("Transaction committed");  
```

 <span data-ttu-id="39506-129">Les appels aux opérations sont comme suit :</span><span class="sxs-lookup"><span data-stu-id="39506-129">The calls to the operations are as follows:</span></span>  
  
- <span data-ttu-id="39506-130">La demande `Add` transmet la transaction requise au service et les actions du service se produisent dans la portée de la transaction du client.</span><span class="sxs-lookup"><span data-stu-id="39506-130">The `Add` request flows the required transaction to the service and the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="39506-131">La première demande `Subtract` transmet également la transaction autorisée au service et, de nouveau, les actions du service se produisent dans la portée de la transaction du client.</span><span class="sxs-lookup"><span data-stu-id="39506-131">The first `Subtract` request also flows the allowed transaction to the service and again the service's actions occur within the scope of the client's transaction.</span></span>  
  
- <span data-ttu-id="39506-132">La seconde demande `Subtract` est effectuée dans une nouvelle portée de transaction déclarée avec l'option `TransactionScopeOption.Suppress`.</span><span class="sxs-lookup"><span data-stu-id="39506-132">The second `Subtract` request is performed within a new transaction scope declared with the `TransactionScopeOption.Suppress` option.</span></span> <span data-ttu-id="39506-133">Cela supprime la transaction externe initiale du client et la demande ne transmet pas de transaction au service.</span><span class="sxs-lookup"><span data-stu-id="39506-133">This suppresses the client's initial outer transaction and the request does not flow a transaction to the service.</span></span> <span data-ttu-id="39506-134">Cette approche permet à un client de choisir explicitement de ne pas transmettre une transaction à un service lorsque cela n'est pas obligatoire et de se protéger également contre toute transmission.</span><span class="sxs-lookup"><span data-stu-id="39506-134">This approach allows a client to explicitly opt-out of and protect against flowing a transaction to a service when that is not required.</span></span> <span data-ttu-id="39506-135">Les actions du service se produisent dans l’étendue d’une transaction nouvelle et non connectée.</span><span class="sxs-lookup"><span data-stu-id="39506-135">The service's actions occur within the scope of a new and unconnected transaction.</span></span>  
  
- <span data-ttu-id="39506-136">La demande `Multiply` ne transmet pas de transaction au service, car la définition générée du client de l’interface `ICalculator` inclut un <xref:System.ServiceModel.TransactionFlowAttribute> ayant la valeur <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span><span class="sxs-lookup"><span data-stu-id="39506-136">The `Multiply` request does not flow a transaction to the service because the client's generated definition of the `ICalculator` interface includes a <xref:System.ServiceModel.TransactionFlowAttribute> set to <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.</span></span>  
  
- <span data-ttu-id="39506-137">La demande `Divide` ne transmet pas de transaction au service, car la définition générée du client de l'interface `ICalculator` n'inclut pas de `TransactionFlowAttribute`.</span><span class="sxs-lookup"><span data-stu-id="39506-137">The `Divide` request does not flow a transaction to the service because again the client's generated definition of the `ICalculator` interface does not include a `TransactionFlowAttribute`.</span></span> <span data-ttu-id="39506-138">Les actions du service se produisent encore dans l’étendue d’une autre transaction nouvelle et non connectée.</span><span class="sxs-lookup"><span data-stu-id="39506-138">The service's actions again occur within the scope of another new and unconnected transaction.</span></span>  
  
 <span data-ttu-id="39506-139">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="39506-139">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="39506-140">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="39506-140">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Starting transaction  
  Add(100,15.99) = 115.99  
  Subtract(145,76.54) = 68.46  
  Subtract(21.05,42.16) = -21.11  
  Multiply(9,81.25) = 731.25  
  Divide(22,7) = 3.14285714285714  
  Completing transaction  
Transaction committed  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="39506-141">Le journal des demandes faites à l'opération de service est visible dans la fenêtre de console du service.</span><span class="sxs-lookup"><span data-stu-id="39506-141">The logging of the service operation requests are displayed in the service's console window.</span></span> <span data-ttu-id="39506-142">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="39506-142">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 <span data-ttu-id="39506-143">Après une exécution réussie, l'étendue de transaction du client se termine et toutes les actions prises dans cette étendue sont validées.</span><span class="sxs-lookup"><span data-stu-id="39506-143">After a successful execution, the client's transaction scope completes and all actions taken within that scope are committed.</span></span> <span data-ttu-id="39506-144">En particulier, les 5 enregistrements distingués sont conservés dans la base de données du service.</span><span class="sxs-lookup"><span data-stu-id="39506-144">Specifically, the noted 5 records are persisted in the service's database.</span></span> <span data-ttu-id="39506-145">Les deux premiers se sont produits dans l'étendue de la transaction du client.</span><span class="sxs-lookup"><span data-stu-id="39506-145">The first 2 of these have occurred within the scope of the client's transaction.</span></span>  
  
 <span data-ttu-id="39506-146">Si une exception s’est produite dans le `TransactionScope` du client, la transaction ne peut alors pas se terminer.</span><span class="sxs-lookup"><span data-stu-id="39506-146">If an exception occurred anywhere within the client's `TransactionScope` then the transaction cannot complete.</span></span> <span data-ttu-id="39506-147">Les enregistrements consignés dans cette étendue ne sont alors par validés dans la base de données.</span><span class="sxs-lookup"><span data-stu-id="39506-147">This causes the records logged within that scope to not be committed to the database.</span></span> <span data-ttu-id="39506-148">Pour observer cet effet, répétez l'exécution de l'exemple après avoir commenté l'appel pour qu'il termine le `TransactionScope` externe.</span><span class="sxs-lookup"><span data-stu-id="39506-148">This effect can be observed by repeating the sample run after commenting out the call to complete the outer `TransactionScope`.</span></span> <span data-ttu-id="39506-149">Sur cette exécution, seules les 3 dernières actions (demandes de la seconde `Subtract`, `Multiply` et `Divide`) sont enregistrées, car la transaction cliente ne leur a pas été transmise.</span><span class="sxs-lookup"><span data-stu-id="39506-149">On such a run, only the last 3 actions (from the second `Subtract`, the `Multiply` and the `Divide` requests) are logged because the client transaction did not flow to those.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="39506-150">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="39506-150">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="39506-151">Pour générer la C# version ou Visual Basic .net de la solution, suivez les instructions de la [création des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md)</span><span class="sxs-lookup"><span data-stu-id="39506-151">To build the C# or Visual Basic .NET version of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)</span></span>  
  
2. <span data-ttu-id="39506-152">Assurez-vous d'avoir installé SQL Server Express Edition ou SQL Server et que la chaîne de connexion a été définie correctement dans le fichier de configuration de l'application du service.</span><span class="sxs-lookup"><span data-stu-id="39506-152">Ensure that you have installed SQL Server Express Edition or SQL Server, and that the connection string has been correctly set in the service’s application configuration file.</span></span> <span data-ttu-id="39506-153">Pour exécuter l'exemple sans utiliser de base de données, affectez à `usingSql`, dans le fichier de configuration de l'application du service, la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="39506-153">To run the sample without using a database, set the `usingSql` value in the service’s application configuration file to `false`</span></span>  
  
3. <span data-ttu-id="39506-154">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="39506-154">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="39506-155">Pour une configuration à plusieurs ordinateurs, activez Microsoft Distributed Transaction Coordinator (MSDTC) à l’aide des instructions ci-dessous et utilisez l’outil WsatConfig.exe du Kit de développement logiciel (SDK) Windows pour activer la prise en charge réseau des transactions WCF.</span><span class="sxs-lookup"><span data-stu-id="39506-155">For cross-machine configuration, enable the Distributed Transaction Coordinator using the instructions below, and use the WsatConfig.exe tool from the Windows SDK to enable WCF Transactions network support.</span></span> <span data-ttu-id="39506-156">Pour plus d’informations sur la configuration de WsatConfig. exe, consultez Configuration de la [prise en charge des transactions WS-Atomic](../feature-details/configuring-ws-atomic-transaction-support.md).</span><span class="sxs-lookup"><span data-stu-id="39506-156">For information on setting up WsatConfig.exe, see [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).</span></span>  
  
 <span data-ttu-id="39506-157">Que vous exécutiez l’exemple sur le même ordinateur ou sur des ordinateurs différents, vous devez configurer le Distributed Transaction Coordinator Microsoft (MSDTC) pour activer le workflow de transaction réseau et utiliser l’outil WsatConfig. exe pour activer la prise en charge réseau des transactions WCF.</span><span class="sxs-lookup"><span data-stu-id="39506-157">Whether you run the sample on the same computer or on different computers, you must configure the Microsoft Distributed Transaction Coordinator (MSDTC) to enable network transaction flow and use the WsatConfig.exe tool to enable WCF transactions network support.</span></span>  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a><span data-ttu-id="39506-158">Pour configurer Microsoft Distributed Transaction Coordinator (MSDTC) de manière à prendre en charge l'exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="39506-158">To configure the Microsoft Distributed Transaction Coordinator (MSDTC) to support running the sample</span></span>  
  
1. <span data-ttu-id="39506-159">Sur un ordinateur de service Windows Server 2003 ou Windows XP, configurez MSDTC pour autoriser des transactions réseau entrantes en suivant ces instructions.</span><span class="sxs-lookup"><span data-stu-id="39506-159">On a service machine running Windows Server 2003 or Windows XP, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="39506-160">Dans le menu **Démarrer** , accédez à **panneau de configuration**, puis **Outils d’administration**et **services de composants**.</span><span class="sxs-lookup"><span data-stu-id="39506-160">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="39506-161">Développez **services de composants**.</span><span class="sxs-lookup"><span data-stu-id="39506-161">Expand **Component Services**.</span></span> <span data-ttu-id="39506-162">Ouvrez le dossier **ordinateurs** .</span><span class="sxs-lookup"><span data-stu-id="39506-162">Open the **Computers** folder.</span></span>  
  
    3. <span data-ttu-id="39506-163">Cliquez avec le bouton droit sur **poste de travail** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="39506-163">Right-click **My Computer** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="39506-164">Sous l’onglet **MSDTC** , cliquez sur Configuration de la **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="39506-164">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    5. <span data-ttu-id="39506-165">Cochez **accès DTC réseau** et **autoriser les transactions entrantes**.</span><span class="sxs-lookup"><span data-stu-id="39506-165">Check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    6. <span data-ttu-id="39506-166">Cliquez sur **OK**, puis sur **Oui** pour redémarrer le service MSDTC.</span><span class="sxs-lookup"><span data-stu-id="39506-166">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    7. <span data-ttu-id="39506-167">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="39506-167">Click **OK** to close the dialog box.</span></span>  
  
2. <span data-ttu-id="39506-168">Sur un ordinateur de service Windows Server 2008 ou Windows Vista, configurez MSDTC pour autoriser des transactions réseau entrantes en suivant ces instructions.</span><span class="sxs-lookup"><span data-stu-id="39506-168">On a service machine running Windows Server 2008 or Windows Vista, configure MSDTC to allow incoming network transactions by following these instructions.</span></span>  
  
    1. <span data-ttu-id="39506-169">Dans le menu **Démarrer** , accédez à **panneau de configuration**, puis **Outils d’administration**et **services de composants**.</span><span class="sxs-lookup"><span data-stu-id="39506-169">From the **Start** menu, navigate to **Control Panel**, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="39506-170">Développez **services de composants**.</span><span class="sxs-lookup"><span data-stu-id="39506-170">Expand **Component Services**.</span></span> <span data-ttu-id="39506-171">Ouvrez le dossier **ordinateurs** .</span><span class="sxs-lookup"><span data-stu-id="39506-171">Open the **Computers** folder.</span></span> <span data-ttu-id="39506-172">Sélectionnez **Distributed Transaction Coordinator**.</span><span class="sxs-lookup"><span data-stu-id="39506-172">Select **Distributed Transaction Coordinator**.</span></span>  
  
    3. <span data-ttu-id="39506-173">Cliquez avec le bouton droit sur **Coordinateur DTC** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="39506-173">Right-click **DTC Coordinator** and select **Properties**.</span></span>  
  
    4. <span data-ttu-id="39506-174">Sous l’onglet **sécurité** , cochez **accès DTC réseau** et **autoriser les transactions entrantes**.</span><span class="sxs-lookup"><span data-stu-id="39506-174">On the **Security** tab, check **Network DTC Access** and **Allow Inbound**.</span></span>  
  
    5. <span data-ttu-id="39506-175">Cliquez sur **OK**, puis sur **Oui** pour redémarrer le service MSDTC.</span><span class="sxs-lookup"><span data-stu-id="39506-175">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="39506-176">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="39506-176">Click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="39506-177">Sur l'ordinateur client, configurez MSDTC pour autoriser les transactions réseau sortantes :</span><span class="sxs-lookup"><span data-stu-id="39506-177">On the client machine, configure MSDTC to allow outgoing network transactions:</span></span>  
  
    1. <span data-ttu-id="39506-178">Dans le menu **Démarrer** , accédez à `Control Panel`, puis **Outils d’administration**et **services de composants**.</span><span class="sxs-lookup"><span data-stu-id="39506-178">From the **Start** menu, navigate to `Control Panel`, then **Administrative Tools**, and then **Component Services**.</span></span>  
  
    2. <span data-ttu-id="39506-179">Cliquez avec le bouton droit sur **poste de travail** , puis sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="39506-179">Right-click **My Computer** and select **Properties**.</span></span>  
  
    3. <span data-ttu-id="39506-180">Sous l’onglet **MSDTC** , cliquez sur Configuration de la **sécurité**.</span><span class="sxs-lookup"><span data-stu-id="39506-180">On the **MSDTC** tab, click **Security Configuration**.</span></span>  
  
    4. <span data-ttu-id="39506-181">Cochez **accès DTC réseau** et **autoriser les transactions sortantes**.</span><span class="sxs-lookup"><span data-stu-id="39506-181">Check **Network DTC Access** and **Allow Outbound**.</span></span>  
  
    5. <span data-ttu-id="39506-182">Cliquez sur **OK**, puis sur **Oui** pour redémarrer le service MSDTC.</span><span class="sxs-lookup"><span data-stu-id="39506-182">Click **OK**, then click **Yes** to restart the MSDTC service.</span></span>  
  
    6. <span data-ttu-id="39506-183">Cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="39506-183">Click **OK** to close the dialog box.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="39506-184">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="39506-184">The samples may already be installed on your machine.</span></span> <span data-ttu-id="39506-185">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="39506-185">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="39506-186">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="39506-186">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="39506-187">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="39506-187">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
