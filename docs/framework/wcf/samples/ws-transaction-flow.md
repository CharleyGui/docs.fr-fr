---
title: WS Transaction Flow
ms.date: 03/30/2017
helpviewer_keywords:
- Transactions
ms.assetid: f8eecbcf-990a-4dbb-b29b-c3f9e3b396bd
ms.openlocfilehash: 8b037a2faa6ed5f7c77ea9347b92af7dc1ec2c27
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183170"
---
# <a name="ws-transaction-flow"></a>WS Transaction Flow
Cet exemple illustre l’utilisation d’une transaction coordonnée par le client et des options de client et de serveur pour le flux de transaction, à l’aide du protocole WS-Atomic Transaction ou OleTransactions. Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui met en œuvre `TransactionFlowAttribute` un service de calculatrice, mais les opérations sont attribuées pour démontrer l’utilisation de l’en énumération **transactionFlowOption** pour déterminer dans quelle mesure le flux de transaction est activé. Dans l'étendue de la transaction passée, un journal des opérations demandées est écrit dans une base de données et est conservé jusqu'à ce que la transaction coordonnée par le client soit terminée. Si la transaction cliente ne se termine pas, la transaction de service Web garantit que les mises à jour appropriées de la base de données ne sont pas validées.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Après avoir initialisé une connexion au service et une transaction, le client accède à plusieurs opérations de service. Le contrat de service est défini comme suit avec chacune des opérations qui montrent un paramètre différent pour `TransactionFlowOption`.  

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

 Cela permet de définir les opérations dans l'ordre dans lequel elles seront traitées :  
  
- Une demande d’opération `Add` doit inclure une transaction passée.  
  
- Une demande d’opération `Subtract` peut inclure une transaction passée.  
  
- Une demande d’opération `Multiply` ne doit pas inclure de transaction passée par l’intermédiaire du paramètre NotAllowed explicite.  
  
- Une demande d'opération `Divide` ne doit pas inclure de transaction passée par omission d'un attribut `TransactionFlow`.  
  
 Pour permettre le flux de transaction, les liaisons avec le [ \<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) propriété activée doivent être utilisées en plus des attributs d’exploitation appropriés. Dans cet exemple, la configuration du service expose un point de terminaison TCP et un point de terminaison HTTP en plus du point de terminaison d'échange de métadonnées. Le point de terminaison TCP et le critère de terminaison HTTP utilisent les liaisons suivantes, qui ont toutes deux activé le [ \<transactionFlow>](../../../../docs/framework/configure-apps/file-schema/wcf/transactionflow.md) propriété.  
  
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
> netTcpBinding fourni par le système autorise la spécification de transactionProtocol alors que wsHttpBinding fourni par le système utilise uniquement le protocole WSAtomicTransactionOctober2004 plus interopérable. Le protocole OleTransactions n’est disponible que pour une utilisation par les clients de la Windows Communication Foundation (WCF).  
  
 Pour la classe qui implémente l'interface `ICalculator`, toutes les méthodes sont attribuées avec la propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> définie sur `true`. Ce paramètre déclare que toutes les actions prises dans la méthode se produisent dans l’étendue d’une transaction. Dans ce cas, les actions prises incluent l'enregistrement dans la base de données journal. Si la demande d’opération inclut une transaction passée, les actions se produisent alors dans l’étendue de la transaction entrante ou une nouvelle étendue de transaction est automatiquement générée.  
  
> [!NOTE]
> La propriété <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> définit le comportement local appliqué aux implémentations de méthode de service et ne définit pas la capacité du client à transmettre la transaction, ni l'obligation de cette transmission.  

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

 Sur le client, les paramètres `TransactionFlowOption` du service sur les opérations sont répercutés dans la définition générée du client de l'interface `ICalculator`. De plus, les paramètres de la propriété `transactionFlow` du service sont répercutés dans la configuration de l'application du client. Le client peut sélectionner le transport et le protocole en sélectionnant le `endpointConfigurationName` approprié.  

```csharp
// Create a client using either wsat or oletx endpoint configurations  
CalculatorClient client = new CalculatorClient("WSAtomicTransaction_endpoint");  
// CalculatorClient client = new CalculatorClient("OleTransactions_endpoint");  
```

> [!NOTE]
> Le comportement observé de cet exemple est le même, quel que soit le protocole ou le transport choisi.  
  
 Une fois la connexion au service initialisée, le client crée un `TransactionScope` autour des appels aux opérations de service.  

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

 Les appels aux opérations sont comme suit :  
  
- La demande `Add` transmet la transaction requise au service et les actions du service se produisent dans la portée de la transaction du client.  
  
- La première demande `Subtract` transmet également la transaction autorisée au service et, de nouveau, les actions du service se produisent dans la portée de la transaction du client.  
  
- La seconde demande `Subtract` est effectuée dans une nouvelle portée de transaction déclarée avec l'option `TransactionScopeOption.Suppress`. Cela supprime la transaction externe initiale du client et la demande ne transmet pas de transaction au service. Cette approche permet à un client de choisir explicitement de ne pas transmettre une transaction à un service lorsque cela n'est pas obligatoire et de se protéger également contre toute transmission. Les actions du service se produisent dans l’étendue d’une transaction nouvelle et non connectée.  
  
- La demande `Multiply` ne transmet pas de transaction au service, car la définition générée du client de l’interface `ICalculator` inclut un <xref:System.ServiceModel.TransactionFlowAttribute> ayant la valeur <xref:System.ServiceModel.TransactionFlowOption>`NotAllowed`.  
  
- La demande `Divide` ne transmet pas de transaction au service, car la définition générée du client de l'interface `ICalculator` n'inclut pas de `TransactionFlowAttribute`. Les actions du service se produisent encore dans l’étendue d’une autre transaction nouvelle et non connectée.  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
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
  
 Le journal des demandes faites à l'opération de service est visible dans la fenêtre de console du service. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
Press <ENTER> to terminate the service.  
  Writing row to database: Adding 100 to 15.99  
  Writing row to database: Subtracting 76.54 from 145  
  Writing row to database: Subtracting 42.16 from 21.05  
  Writing row to database: Multiplying 9 by 81.25  
  Writing row to database: Dividing 22 by 7  
```  
  
 Après une exécution réussie, l'étendue de transaction du client se termine et toutes les actions prises dans cette étendue sont validées. En particulier, les 5 enregistrements distingués sont conservés dans la base de données du service. Les deux premiers se sont produits dans l'étendue de la transaction du client.  
  
 Si une exception s’est produite dans le `TransactionScope` du client, la transaction ne peut alors pas se terminer. Les enregistrements consignés dans cette étendue ne sont alors par validés dans la base de données. Pour observer cet effet, répétez l'exécution de l'exemple après avoir commenté l'appel pour qu'il termine le `TransactionScope` externe. Sur cette exécution, seules les 3 dernières actions (demandes de la seconde `Subtract`, `Multiply` et `Divide`) sont enregistrées, car la transaction cliente ne leur a pas été transmise.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Pour construire la version .NET de base visuelle ou de Cmd de la solution, suivez les instructions dans La construction des échantillons de [la Fondation De communication Windows](../../../../docs/framework/wcf/samples/building-the-samples.md)  
  
2. Assurez-vous d'avoir installé SQL Server Express Edition ou SQL Server et que la chaîne de connexion a été définie correctement dans le fichier de configuration de l'application du service. Pour exécuter l'exemple sans utiliser de base de données, affectez à `usingSql`, dans le fichier de configuration de l'application du service, la valeur `false`.  
  
3. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
    > [!NOTE]
    > Pour une configuration à plusieurs ordinateurs, activez Microsoft Distributed Transaction Coordinator (MSDTC) à l’aide des instructions ci-dessous et utilisez l’outil WsatConfig.exe du Kit de développement logiciel (SDK) Windows pour activer la prise en charge réseau des transactions WCF. Pour plus d’informations sur la mise en place de WsatConfig.exe, voir [Configuring WS-Atomic Transaction Support](../feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Que vous utilisiez l’échantillon sur le même ordinateur ou sur différents ordinateurs, vous devez configurer le coordinateur des transactions distribuées Microsoft (MSDTC) pour activer le flux de transactions réseau et utiliser l’outil WsatConfig.exe pour activer le support réseau de transactions WCF.  
  
### <a name="to-configure-the-microsoft-distributed-transaction-coordinator-msdtc-to-support-running-the-sample"></a>Pour configurer Microsoft Distributed Transaction Coordinator (MSDTC) de manière à prendre en charge l'exécution de l'exemple  
  
1. Sur un ordinateur de service Windows Server 2003 ou Windows XP, configurez MSDTC pour autoriser des transactions réseau entrantes en suivant ces instructions.  
  
    1. Du menu **Démarrer,** naviguez vers **Le panneau de contrôle,** puis **les outils administratifs,** puis **les services de composants**.  
  
    2. Élargir les **services de composants**. Ouvrez le dossier **Ordinateurs.**  
  
    3. Cliquez à droite **mon ordinateur** et sélectionnez **les propriétés**.  
  
    4. Sur l’onglet **MSDTC,** cliquez sur **Configuration de sécurité**.  
  
    5. Vérifier **Network DTC Access** and Allow **Inbound**.  
  
    6. Cliquez **sur OK**, puis cliquez sur **Oui** pour redémarrer le service MSDTC.  
  
    7. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
2. Sur un ordinateur de service Windows Server 2008 ou Windows Vista, configurez MSDTC pour autoriser des transactions réseau entrantes en suivant ces instructions.  
  
    1. Du menu **Démarrer,** naviguez vers **Le panneau de contrôle,** puis **les outils administratifs,** puis **les services de composants**.  
  
    2. Élargir les **services de composants**. Ouvrez le dossier **Ordinateurs.** Sélectionnez **Coordonnateur des transactions distribuées**.  
  
    3. Cliquer à droite **Coordonnateur DTC** et sélectionner **les propriétés**.  
  
    4. Sur l’onglet **Sécurité,** vérifiez **Network DTC Access** et **Allow Inbound**.  
  
    5. Cliquez **sur OK**, puis cliquez sur **Oui** pour redémarrer le service MSDTC.  
  
    6. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
3. Sur l'ordinateur client, configurez MSDTC pour autoriser les transactions réseau sortantes :  
  
    1. Du menu **Démarrer,** `Control Panel`naviguer vers , puis **outils administratifs**, puis **services de composants**.  
  
    2. Cliquez à droite **mon ordinateur** et sélectionnez **les propriétés**.  
  
    3. Sur l’onglet **MSDTC,** cliquez sur **Configuration de sécurité**.  
  
    4. Vérifiez **Network DTC Access** et Autoriser **Outbound**.  
  
    5. Cliquez **sur OK**, puis cliquez sur **Oui** pour redémarrer le service MSDTC.  
  
    6. Cliquez sur **OK** pour fermer la boîte de dialogue.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\TransactionFlow`
