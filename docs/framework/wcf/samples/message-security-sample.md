---
title: Message Security, exemple
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 1e57e82dc9394f34ab97da751a5d11c6099d353c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044858"
---
# <a name="message-security-sample"></a>Message Security, exemple
Cet exemple montre comment implémenter une application qui utilise `basicHttpBinding` et la sécurité de message. Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md) qui implémente un service de calculatrice.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Le mode de sécurité de `basicHttpBinding` peut avoir les valeurs suivantes : `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` et `None`. Dans l'exemple de fichier App.config de service suivant, la définition de point de terminaison spécifie `basicHttpBinding` et référence une configuration de liaison appelée `Binding1`, tel qu'indiqué dans l'exemple de configuration suivant :  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"   
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 La configuration de liaison affecte `mode` [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md) `Message` `clientCredentialType` à l’attribut du > de sécurité la valeur et définit l’attribut du > `Certificate` de [ messagesurcommeindiquédansl’exemplesuivant:\<](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md) exemple de configuration:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 Le certificat que le service utilise pour s'authentifier auprès du client est défini dans la section des comportements du fichier de configuration située sous l'élément `serviceCredentials`. Le mode de validation qui s’applique au certificat que le client utilise pour s’authentifier auprès du service est également défini dans la section des comportements située sous l’élément `clientCertificate`.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"   
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication   
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Les mêmes détails sur la liaison et la sécurité sont spécifiés dans le fichier de configuration client.  
  
 L'identité de l'appelant s'affiche dans la fenêtre de console du service à l'aide du code suivant :  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-machine"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1. Exécutez Setup.bat à partir du dossier d'installation de l'exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.  
  
    > [!NOTE]
    > Le fichier de commandes Setup.bat est conçu pour s'exécuter à partir d'une invite de commandes du Kit de développement Windows SDK. La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK. Cette variable est définie automatiquement dans une invite de commandes du Kit de développement logiciel Windows.  
  
2. Exécutez l'application de service à partir de \service\bin.  
  
3. Exécutez l'application cliente à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
4. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
5. Supprimez les certificats en exécutant Cleanup.bat une fois l'exemple terminé. D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
### <a name="to-run-the-sample-across-machines"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Créez un répertoire sur l'ordinateur de service destiné aux fichiers binaires de service.  
  
2. Copiez les fichiers programme du service dans le répertoire de service sur le serveur. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur le serveur.  
  
3. Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.  
  
4. Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.  
  
5. Sur le serveur, exécutez `setup.bat service`. L' `setup.bat` exécution avec `service` l’argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.  
  
6. Modifiez Service. exe. config pour refléter le nouveau nom de certificat (dans `findValue` l’attribut de l' [ \<élément serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur. Modifiez également la valeur de l'adresse de base afin de remplacer localhost par un nom d'ordinateur complet`.`  
  
7. Copiez le fichier Service.cer du répertoire de service dans le répertoire client sur l'ordinateur client.  
  
8. Sur le client, exécutez `setup.bat client`. L'exécution de `setup.bat` à l'aide de l'argument `client` crée un certificat client appelé client.com, puis exporte ce certificat vers un fichier nommé Client.cer.  
  
9. Dans le fichier Client.exe.config sur l'ordinateur client, modifiez la valeur d'adresse du point de terminaison pour qu'il corresponde à la nouvelle adresse de votre service. Pour ce faire, remplacez localhost par le nom de domaine complet du serveur. Remplacez également l' `findValue` attribut de l' [ \<> DefaultCertificate](../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md) par le nouveau nom du certificat de service, qui est le nom de domaine complet du serveur.  
  
10. Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
11. Sur le client, exécutez ImportServiceCert.bat. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
12. Sur le serveur, exécutez ImportClientCert.bat. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.  
  
13. Sur l'ordinateur de service, exécutez Service.exe à partir d'une invite de commandes.  
  
14. Sur l'ordinateur du client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.  
  
    1. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
    > [!NOTE]
    > Ce script ne supprime pas les certificats de service figurant sur le client lorsque l'exemple est exécuté sur plusieurs ordinateurs. Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople. Pour ce faire, utilisez la commande suivante: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` Exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ) et. Cet exemple se trouve dans le répertoire suivant.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`  
