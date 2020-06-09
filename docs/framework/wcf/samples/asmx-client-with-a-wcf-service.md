---
title: ASMX Client with a WCF Service
ms.date: 03/30/2017
ms.assetid: 3ea381ee-ac7d-4d62-8c6c-12dc3650879f
ms.openlocfilehash: fd13d4907f1be09440387a36e14ecdc4926ba7e7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594775"
---
# <a name="asmx-client-with-a-wcf-service"></a>ASMX Client with a WCF Service

Cet exemple montre comment créer un service à l’aide d’Windows Communication Foundation (WCF), puis accéder au service à partir d’un client non-WCF, tel qu’un client ASMX.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

Cet exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés par les services IIS (Internet Information Services). Le service implémente un contrat qui définit un modèle de communication demande-réponse. Le contrat est défini par l'interface `ICalculator`, qui expose des opérations mathématiques (`Add`, `Subtract`, `Multiply` et `Divide`). Le client ASMX adresse des demandes synchrones à une opération mathématique et le service répond avec le résultat.

Le service implémente un contrat `ICalculator` tel que défini dans le code suivant.

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples"), XmlSerializerFormat]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

Le <xref:System.Runtime.Serialization.DataContractSerializer> et le <xref:System.Xml.Serialization.XmlSerializer> mappent des types CLR à une représentation XML. Le <xref:System.Runtime.Serialization.DataContractSerializer> interprète des représentations XML différemment du XmlSerializer. Les générateurs de proxy non-WCF, tels que WSDL. exe, génèrent une interface plus utilisable lorsque le XmlSerializer est utilisé. Le <xref:System.ServiceModel.XmlSerializerFormatAttribute> est appliqué à l' `ICalculator` interface, pour s’assurer que le XmlSerializer est utilisé pour le mappage des types CLR au format XML. L'implémentation de service calcule et retourne le résultat approprié.

Le service expose un point de terminaison unique de communication avec le service, lequel est défini à l'aide du fichier de configuration Web.config. Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat. Le service expose le point de terminaison à l'adresse de base fournie par l'hôte IIS (Internet Information Services). L'attribut `binding` a la valeur basicHttpBinding, qui fournit des communications HTTP à l'aide de SOAP 1.1, qui est conforme à WS-BasicProfile 1.1, comme le montre l'exemple de configuration suivant.

```xml
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <!-- This endpoint is exposed at the base address provided by the host: http://localhost/servicemodelsamples/service.svc.  -->
    <endpoint address=""
              binding="basicHttpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
</services>
```

Le client ASMX communique avec le service WCF à l’aide d’un proxy typé généré par l’utilitaire Web Services Description Language (WSDL) (WSDL. exe). Le proxy typé est contenu dans le fichier generatedClient.cs. L'utilitaire WSDL récupère les métadonnées pour le service spécifié et génère un proxy typé qui sera utilisé par un client pour communiquer. Par défaut, l'infrastructure n'expose pas de métadonnées. Pour exposer les métadonnées requises pour générer le proxy, vous devez ajouter un [\<serviceMetadata>](../../configure-apps/file-schema/wcf/servicemetadata.md) et affecter `httpGetEnabled` à son attribut la valeur, `True` comme indiqué dans la configuration suivante.

```xml
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <!-- Setting httpGetEnabled to True on the serviceMetadata
           behavior exposes the service's wsdl at <base address>?wsdl :
           http://localhost/servicemodelsamples/service.svc?wsdl -->
      <serviceMetadata httpGetEnabled="True"/>
      <serviceDebug includeExceptionDetailInFaults="False" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```

Exécutez la commande suivante à partir d'une invite de commandes dans le répertoire client pour générer le proxy typé.

```console
wsdl /n:Microsoft.ServiceModel.Samples /o:generatedClient.cs /urlkey:CalculatorServiceAddress http://localhost/servicemodelsamples/service.svc?wsdl
```

En utilisant le proxy typé généré, le client peut accéder à un point de terminaison de service donné en configurant l'adresse appropriée. Le client utilise un fichier de configuration (App.config) pour spécifier le point de terminaison avec lequel communiquer.

```xml
<appSettings>
  <add key="CalculatorServiceAddress"
       value="http://localhost/ServiceModelSamples/service.svc"/>
</appSettings>
```

L'implémentation cliente génère une instance du proxy typé pour commencer à communiquer avec le service.

```csharp
// Create a client to the CalculatorService.
using (CalculatorService client = new CalculatorService())
{
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

}

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

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

3. Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](running-the-samples.md).

> [!NOTE]
> Pour plus d’informations sur le passage et le retour de types de données complexes, consultez : [liaison de données dans un client Windows Forms](data-binding-in-a-windows-forms-client.md), [liaison de données dans un client Windows Presentation Foundation](data-binding-in-a-wpf-client.md)et [liaison de données dans un client ASP.net](data-binding-in-an-aspnet-client.md)

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Interop\ASMX`
