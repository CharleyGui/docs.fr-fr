---
title: Interoperating with ASMX Web Services
ms.date: 03/30/2017
ms.assetid: a7c11f0a-9e68-4f03-a6b1-39cf478d1a89
ms.openlocfilehash: 2ef4e34de76c046ba21dd7a3c50ea6ba782d459e
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989801"
---
# <a name="interoperating-with-asmx-web-services"></a>Interoperating with ASMX Web Services
Cet exemple montre comment intégrer une application cliente Windows Communication Foundation (WCF) à un service Web ASMX existant.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés par les services IIS (Internet Information Services). Le service correspond à un service Web ASMX qui implémente un contrat définissant un modèle de communication demande-réponse. Ce service expose les opérations mathématiques suivantes :`Add`, `Subtract`, `Multiply` et `Divide`. Le client adresse des demandes synchrones à une opération mathématique et le service répond avec le résultat. L'activité du client est affichée dans la fenêtre de console.  
  
 L'implémentation de service Web ASMX, telle qu'illustrée dans l'exemple de code suivant, calcule, puis retourne le résultat approprié.  
  
```csharp  
[WebService(Namespace="http://Microsoft.ServiceModel.Samples")]  
public class CalculatorService : System.Web.Services.WebService  
    {  
        [WebMethod]  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
        [WebMethod]  
        public double Subtract(double n1, double n2)  
        {  
            return n1 - n2;  
        }  
        [WebMethod]  
        public double Multiply(double n1, double n2)  
        {  
            return n1 * n2;  
        }  
        [WebMethod]  
        public double Divide(double n1, double n2)  
        {  
            return n1 / n2;  
        }  
    }  
```  
  
 Comme configuré, le service est accessible à `http://localhost/servicemodelsamples/service.asmx` un client sur le même ordinateur. Pour que les clients installés sur des ordinateurs distants puissent accéder au service, un nom de domaine complet doit être spécifié au lieu de localhost.  
  
 La communication s’effectue via un client généré par l' [outil ServiceModel Metadata Utility Tool (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Le client figure dans le fichier generatedClient.cs. Le service ASMX doit être disponible pour générer le code proxy, ce dernier permettant de récupérer les métadonnées mises à jour. Exécutez la commande suivante à partir d'une invite de commandes dans le répertoire client pour générer le proxy typé.  
  
```console  
svcutil.exe /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedClient.cs  
```  
  
 Le client généré vous permet d’accéder à un point de terminaison de service. Il vous suffit de configurer l’adresse et la liaison appropriées. À l'instar du service, le client utilise un fichier de configuration (App.config) pour spécifier le point de terminaison avec lequel il communique. La configuration de point de terminaison client se compose d’une adresse absolue pour le point de terminaison de service, de la liaison et du contrat, tel qu’indiqué dans l’exemple de configuration suivant.  
  
```xml  
<client>  
   <endpoint   
      address="http://localhost/ServiceModelSamples/service.asmx"   
      binding="basicHttpBinding"   
      contract="Microsoft.ServiceModel.Samples.CalculatorServiceSoap" />  
</client>  
```  
  
 L'implémentation cliente construit une instance du client généré. Le client généré peut ensuite être utilisé pour communiquer avec le service.  
  
```csharp  
// Create a client.  
CalculatorServiceSoapClient client = new CalculatorServiceSoapClient();  
  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = client.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
// Call the Subtract service operation.  
value1 = 145.00D;  
value2 = 76.54D;  
result = client.Subtract(value1, value2);  
Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
// Call the Multiply service operation.  
value1 = 9.00D;  
value2 = 81.25D;  
result = client.Multiply(value1, value2);  
Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
// Call the Divide service operation.  
value1 = 22.00D;  
value2 = 7.00D;  
result = client.Divide(value1, value2);  
Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
  
Console.WriteLine();  
Console.WriteLine("Press <ENTER> to terminate client.");  
Console.ReadLine();  
```  
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\Interop\ASMX`  
