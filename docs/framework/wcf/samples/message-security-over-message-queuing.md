---
title: Message Security over Message Queuing
ms.date: 03/30/2017
ms.assetid: 329aea9c-fa80-45c0-b2b9-e37fd7b85b38
ms.openlocfilehash: 1733cea17c82f85751b810f4a6033caefd828e29
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90558639"
---
# <a name="message-security-over-message-queuing"></a>Message Security over Message Queuing
Cet exemple montre comment implémenter une application qui utilise WS-Security avec l'authentification de certificat X.509v3 pour le client et requiert l'authentification de serveur à l'aide du certificat X.509v3 du serveur via MSMQ. La sécurité de message est parfois plus souhaitable pour garantir que les messages du magasin MSMQ demeurent chiffrés et que l'application peut effectuer sa propre authentification du message.

 Cet exemple est basé sur l’exemple de [liaison MSMQ transactionnelle](transacted-msmq-binding.md) . Les messages sont chiffrés et signés.

### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Si le service est exécuté en premier, il vérifie que la file d'attente existe. Si la file d'attente n'existe pas, le service en crée une. Vous pouvez exécuter le service en premier pour créer la file d'attente, ou en créer une à l'aide du Gestionnaire de files d'attente MSMQ. Procédez comme suit pour créer une file d'attente dans Windows 2008 :

    1. Ouvrez Gestionnaire de serveur dans Visual Studio 2012.

    2. Développez l’onglet **fonctionnalités** .

    3. Cliquez avec le bouton droit sur **files d’attente de messages privées**, puis sélectionnez **nouveau**, **file d’attente privée**.

    4. Activez la case à cocher **transactionnelle** .

    5. Entrez `ServiceModelSamplesTransacted` comme nom de la nouvelle file d’attente.

3. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).

### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur

1. Vérifiez que le chemin d’accès inclut le dossier qui contient Makecert.exe et FindPrivateKey.exe.

2. Exécutez Setup.bat à partir du dossier d'installation de l'exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.

    > [!NOTE]
    > Assurez-vous d'effacer les certificats en exécutant Cleanup.bat une fois l'exemple terminé. D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
3. Lancez Service.exe à partir de \service\bin.  
  
4. Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
5. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Copiez les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur l'ordinateur de service.  
  
2. Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.  
  
3. Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.  
  
4. Sur le serveur, exécutez `setup.bat service`. `setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.  
  
5. Modifiez le service.exe.config du service pour refléter le nouveau nom de certificat (dans l' `findValue` attribut de [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur.  
  
6. Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.  
  
7. Sur le client, exécutez `setup.bat client`. L'exécution de `setup.bat` à l'aide de l'argument `client` crée un certificat client appelé client.com, puis exporte ce certificat vers un fichier nommé Client.cer.  
  
8. Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service. Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.  Vous devez également modifier le nom de certificat du service pour qu'il soit identique au nom de domaine complet de l'ordinateur de service (dans l'attribut `findValue` de l'élément `defaultCertificate` de `serviceCertificate` sous `clientCredentials`).  
  
9. Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
10. Sur le client, exécutez `ImportServiceCert.bat`. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
11. Sur le serveur, exécutez `ImportClientCert.bat`. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.  
  
12. Sur l'ordinateur de service, lancez Service.exe à partir d'une invite de commandes.  
  
13. Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
    > [!NOTE]
    > Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs. Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople. Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.

## <a name="requirements"></a>Spécifications
 Cet exemple requiert l'installation et l'exécution de MSMQ.

## <a name="demonstrates"></a>Illustre le
 Le client chiffre le message à l'aide de la clé publique du service et signe le message qui utilise son propre certificat. Le service qui lit le message depuis la file d'attente authentifie le certificat client avec le certificat de son magasin de personnes de confiance. Il déchiffre alors le message et distribue le message à l'opération de service.

 Étant donné que le message Windows Communication Foundation (WCF) est transporté comme une charge dans le corps du message MSMQ, le corps reste chiffré dans le magasin MSMQ. Cela protège le message contre toute divulgation non désirée du message. Notez que MSMQ lui-même ne sait pas si le message qu'il transporte est chiffré.

 L'exemple montre comment l'authentification mutuelle au niveau du message peut être utilisée avec MSMQ. Les certificats sont échangés hors bande. C'est toujours le cas avec les applications mises en file d'attente parce que le service et le client n'ont pas à être en marche en même temps.

## <a name="description"></a>Description
 L’exemple de code de client et de service est identique à l’exemple de [liaison MSMQ transactionnelle](transacted-msmq-binding.md) , avec une différence. Le contrat d’opération est annoté avec le niveau de protection, ce qui suggère que le message doit être signé et chiffré.

```csharp
// Define a service contract.
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface IOrderProcessor
{
    [OperationContract(IsOneWay = true, ProtectionLevel=ProtectionLevel.EncryptAndSign)]
    void SubmitPurchaseOrder(PurchaseOrder po);
}
```

 Pour garantir que le message est sécurisé à l'aide du jeton requis pour identifier le service et le client, App.config contient des informations d'identification.

 La configuration client spécifie le certificat de service pour authentifier le service. Elle utilise son magasin LocalMachine comme magasin de confiance pour s'appuyer sur la validation du service. Elle spécifie également le certificat client joint avec le message pour l'authentification du service du client.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <system.serviceModel>

    <client>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                binding="netMsmqBinding"
                bindingConfiguration="messageSecurityBinding"
                contract="Microsoft.ServiceModel.Samples.IOrderProcessor"
                behaviorConfiguration="ClientCertificateBehavior" />
    </client>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate"/>
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <!--
        The clientCredentials behavior allows one to define a certificate to present to a service.
        A certificate is used by a client to authenticate itself to the service and provide message integrity.
        This configuration references the "client.com" certificate installed during the setup instructions.
        -->
          <clientCredentials>
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />
            <serviceCertificate>
                <defaultCertificate findValue="localhost" storeLocation="CurrentUser" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>

  </system.serviceModel>
</configuration>
```

 Notez que le mode de sécurité est Message et que le ClientCredentialType a pour valeur Certificat.

 La configuration du service inclut un comportement de service qui spécifie les informations d'identification du service utilisées lorsque le client authentifie le service. Le nom du sujet du certificat de serveur est spécifié dans l' `findValue` attribut de [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>

  <appSettings>
    <!-- Use appSetting to configure MSMQ queue name. -->
    <add key="queueName" value=".\private$\ServiceModelSamplesMessageSecurity" />
  </appSettings>

  <system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.OrderProcessorService"
          behaviorConfiguration="PurchaseOrderServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
          </baseAddresses>
        </host>
        <!-- Define NetMsmqEndpoint -->
        <endpoint address="net.msmq://localhost/private/ServiceModelSamplesMessageSecurity"
                  binding="netMsmqBinding"
                  bindingConfiguration="messageSecurityBinding"
                  contract="Microsoft.ServiceModel.Samples.IOrderProcessor" />
        <!-- The mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex. -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>

    <bindings>
        <netMsmqBinding>
            <binding name="messageSecurityBinding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
                </security>
            </binding>
        </netMsmqBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="PurchaseOrderServiceBehavior">
          <serviceMetadata httpGetEnabled="True"/>
          <!--
               The serviceCredentials behavior allows one to define a service certificate.
               A service certificate is used by the service to authenticate itself to its clients and to provide message protection.
               This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
            <clientCertificate>
                <certificate findValue="client.com" storeLocation="LocalMachine" storeName="TrustedPeople" x509FindType="FindBySubjectName"/>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it is trusted without performing a
            validation of the certificate's issuer chain. This setting is used here for convenience so that the
            sample can be run without having to have certificates issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust. The security implications of this
            setting should be carefully considered before using PeerOrChainTrust in production code.
            -->
              <authentication certificateValidationMode="PeerOrChainTrust" />
            </clientCertificate>
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>

</configuration>
```

 L'exemple montre comment contrôler l'authentification à l'aide de la configuration, et comment obtenir l'identité de l'appelant à partir du contexte de sécurité, tel qu'indiqué dans l'exemple de code suivant :

```csharp
// Service class which implements the service contract.
// Added code to write output to the console window.
public class OrderProcessorService : IOrderProcessor
{
    private string GetCallerIdentity()
    {
        // The client certificate is not mapped to a Windows identity by default.
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information
        // in the certificate that the client used to authenticate itself to the service.
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;
    }

    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    public void SubmitPurchaseOrder(PurchaseOrder po)
    {
        Console.WriteLine("Client's Identity {0} ", GetCallerIdentity());
        Orders.Add(po);
        Console.WriteLine("Processing {0} ", po);
    }
  //…
}
```

 Lorsqu'il est exécuté, le code de service affiche l'identification du client. L'exemple suivant illustre une sortie du code de service :

```console
The service is ready.
Press <ENTER> to terminate service.

Client's Identity CN=client.com; ECA6629A3C695D01832D77EEE836E04891DE9D3C
Processing Purchase Order: 6536e097-da96-4773-9da3-77bab4345b5d
        Customer: somecustomer.com
        OrderDetails
                Order LineItem: 54 of Blue Widget @unit price: $29.99
                Order LineItem: 890 of Red Widget @unit price: $45.89
        Total cost of this order: $42461.56
        Order status: Pending
```

## <a name="comments"></a>Commentaires

- Création du certificat client

     La ligne suivante du fichier de commandes crée le certificat client. Le nom client spécifié est utilisé dans le nom du sujet du certificat créé. Le certificat est stocké dans le magasin `My` situé au niveau de l'emplacement de magasin `CurrentUser`.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Installation du certificat client dans le magasin de certificats approuvés du serveur.

     La ligne suivante du fichier de commandes copie le certificat client dans le magasin TrustedPeople du serveur afin que le serveur puisse prendre les décisions d'approbation ou de non-approbation appropriées. Pour qu’un certificat installé dans le magasin TrustedPeople soit approuvé par un service Windows Communication Foundation (WCF), le mode de validation du certificat client doit avoir `PeerOrChainTrust` la `PeerTrust` valeur ou. Pour connaître la procédure à suivre à l'aide d'un fichier de configuration, consultez l'exemple de configuration de service précédent.

    ```bat
    echo ************
    echo copying client cert to server's LocalMachine store
    echo ************
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

- Création du certificat de serveur

     Les lignes suivantes du fichier de commandes Setup.bat génèrent le certificat de serveur à utiliser :

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     La variable %SERVER_NAME% spécifie le nom du serveur. Le certificat est stocké dans le magasin LocalMachine. Si le fichier de commandes d’installation est exécuté à l’aide d’un argument de service (tel que `setup.bat service` ), le% SERVER_NAME% contient le nom de domaine complet de l’ordinateur. Dans le cas contraire, la valeur par défaut est localhost

- Installation du certificat de serveur dans le magasin de certificats approuvés du client.

     La ligne suivante copie le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > Si vous utilisez un non-U. S. Édition anglaise de Microsoft Windows, vous devez modifier le fichier Setup.bat et remplacer le nom de compte « NT AUTHORITY\NETWORK SERVICE » par votre équivalent régional.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\MessageSecurity`
