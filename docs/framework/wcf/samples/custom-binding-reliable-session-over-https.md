---
title: Custom Binding Reliable Session over HTTPS
ms.date: 03/30/2017
ms.assetid: 16aaa80d-3ffe-47c4-8b16-ec65c4d25f8d
ms.openlocfilehash: 051e7f56662a2ca67018ae7dd29189ff50245fc8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183872"
---
# <a name="custom-binding-reliable-session-over-https"></a>Custom Binding Reliable Session over HTTPS
Cet exemple illustre l'utilisation de la sécurité de transport SSL avec des sessions fiables. Les sessions fiables implémentent le protocole WS-Reliable Messaging. Vous pouvez obtenir une session fiable sécurisée en composant WS-Security sur des sessions fiables. Mais parfois, vous pouvez choisir d'utiliser à la place la sécurité de transport HTTP avec SSL.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons. Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Custom\ReliableSessionOverHttps`  
  
## <a name="sample-details"></a>Détails de l'exemple  
 SSL garantit que les paquets eux-mêmes sont sécurisés. Il est important de noter que cela diffère de la sécurisation de la session fiable à l'aide de WS-Secure Conversation.  
  
 Pour utiliser la session fiable sur HTTPS, vous devez créer une liaison personnalisée. Cet échantillon est basé sur le [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui met en œuvre un service de calculatrice. Une reliure personnalisée est créée à l’aide de l’élément de liaison de session fiable et de la [ \<>httpsTransport ](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md). La configuration suivante est celle de la liaison personnalisée.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"  
          behaviorConfiguration="CalculatorServiceBehavior">  
        <!-- use base address provided by host -->  
        <endpoint address=""  
                  binding="customBinding"  
                  bindingConfiguration="reliableSessionOverHttps"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is exposed as http://localhost/servicemodelsamples/service.svc/mex-->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange"/>  
      </service>  
    </services>  
  
    <bindings>  
      <customBinding>  
        <binding name="reliableSessionOverHttps">  
          <reliableSession />  
          <httpsTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="true" />  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 Le code de programme de l’échantillon est identique à celui du service [Getting Started.](../../../../docs/framework/wcf/samples/getting-started-sample.md) Vous devez créer un certificat et l'assigner en utilisant l'Assistant Certificat de serveur Web avant de générer et exécuter l'exemple. La définition du point de terminaison et la définition de la liaison dans les paramètres du fichier de configuration permettent l’utilisation de la liaison personnalisée comme le montre l’exemple de configuration suivant pour le client.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!-- this endpoint has an https: address -->  
      <endpoint name=""  
                address="https://localhost/servicemodelsamples/service.svc"
                binding="customBinding"
                bindingConfiguration="reliableSessionOverHttps"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </client>  
  
      <bindings>  
        <customBinding>  
          <binding name="reliableSessionOverHttps">  
            <reliableSession />  
            <httpsTransport />  
          </binding>  
        </customBinding>
    </bindings>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
 L'adresse spécifiée utilise le modèle https://.  
  
 Parce que le certificat utilisé dans cet échantillon est un certificat de test créé avec Makecert.exe, https://localhost/servicemodelsamples/service.svcune alerte de sécurité apparaît lorsque vous essayez d’accéder à un https: adresse, comme , à partir de votre navigateur. Pour permettre au client de la Windows Communication Foundation (WCF) de travailler avec un certificat de test en place, un code supplémentaire a été ajouté au client pour supprimer l’alerte de sécurité. Ce code, et la classe qui l'accompagne, n'est pas requis lors de l'utilisation de certificats de production.  

```csharp
// This code is required only for test certificates like those created by Makecert.exe.  
PermissiveCertificatePolicy.Enact("CN=ServiceModelSamples-HTTPS-Server");  
```

 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Installez ASP.NET 4.0 à l’aide de la commande suivante.  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)  
  
3. Assurez-vous d’avoir effectué les [instructions d’installation de certificats de serveur des services d’information Internet (IIS).](../../../../docs/framework/wcf/samples/iis-server-certificate-installation-instructions.md)  
  
4. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
5. Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).  
