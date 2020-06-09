---
title: Message Security Certificate
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 1dec66631368543eecd548ac1ec9bbcda466d746
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584846"
---
# <a name="message-security-certificate"></a>Message Security Certificate
Cet exemple montre comment implémenter une application qui utilise WS-Security avec l'authentification de certificat X.509 v3 pour le client et requiert l'authentification de serveur à l'aide du certificat X.509 v3 du serveur. Il utilise des paramètres par défaut de sorte que tous les messages d'application entre le client et le serveur soient signés et chiffrés. Cet exemple est basé sur [WSHttpBinding](wshttpbinding.md) et se compose d’un programme de console client et d’une bibliothèque de service hébergée par Internet Information Services (IIS). Le service implémente un contrat qui définit un modèle de communication demande-réponse.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple montre comment contrôler l'authentification à l'aide de la configuration et comment obtenir l'identité de l'appelant à partir du contexte de sécurité, tel qu'indiqué dans l'exemple de code suivant.  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 Le service expose un point de terminaison permettant de communiquer avec le service et un point de terminaison permettant d'exposer le document WSDL du service à l'aide du  protocole WS-MetadataExchange, défini à l'aide du fichier de configuration (Web.config). Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat. La liaison est configurée avec un [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) élément standard, qui utilise par défaut la sécurité de message. Cet exemple affecte Certificat à l'attribut `clientCredentialType` pour requérir l'authentification du client.  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
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
```  
  
 Le comportement spécifie les informations d'identification du service utilisées lorsque le client authentifie le service. Le nom du sujet du certificat de serveur est spécifié dans l' `findValue` attribut de l' [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) élément.  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
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
```  
  
 La configuration du point de terminaison du client se compose d’une adresse absolue pour le point de terminaison du service, de la liaison et du contrat. La liaison cliente est configurée avec les modes de sécurité et d’authentification appropriés. Lors de l'exécution sur plusieurs ordinateurs, assurez-vous que l'adresse de point de terminaison de service est modifiée en conséquence.  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 L'implémentation cliente peut définir le certificat à utiliser, soit via le fichier de configuration, soit via le code. L'exemple suivant montre comment définir le certificat à utiliser dans le fichier de configuration.  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 L'exemple suivant montre comment appeler le service dans votre programme.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Le fichier de commandes Setup.bat inclus avec les exemples Message Security vous permet de configurer le client et le serveur avec les certificats appropriés pour exécuter une application hébergée qui requiert la sécurité basée sur le certificat. Ce fichier peut être exécuté en trois modes. Pour exécuter en mode ordinateur unique, tapez **Setup. bat** dans un invite de commandes développeur pour Visual Studio ; pour le mode de service, tapez **Setup. bat service.** et pour le mode client, tapez **Setup. bat client**. Lorsque vous exécutez l'exemple sur plusieurs ordinateurs, utilisez le mode client et serveur. Pour plus d'informations, consultez la procédure d'installation figurant en fin de rubrique. Les éléments suivants fournissent une brève vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée :  
  
- Création du certificat client  
  
     La ligne suivante du fichier de commandes crée le certificat client. Le nom client spécifié est utilisé dans le nom du sujet du certificat créé. Le certificat est stocké dans le magasin `My` situé au niveau de l'emplacement de magasin `CurrentUser`.  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- Installation du certificat client dans le magasin de certificats approuvés du serveur  
  
     La ligne suivante du fichier de commandes copie le certificat client dans le magasin TrustedPeople du serveur afin que le serveur puisse prendre les décisions d'approbation ou de non-approbation appropriées. Pour qu’un certificat installé dans le magasin TrustedPeople soit approuvé par un service Windows Communication Foundation (WCF), le mode de validation du certificat client doit avoir la valeur `PeerOrChainTrust` ou `PeerTrust` . Pour connaître la procédure à suivre à l'aide d'un fichier de configuration, consultez l'exemple de configuration de service précédent.  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- Création du certificat de serveur  
  
     Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     La variable %SERVER_NAME% spécifie le nom du serveur. Le certificat est stocké dans le magasin LocalMachine. Si le fichier de commandes Setup. bat est exécuté avec un argument service (par exemple, le **service Setup. bat**), le% SERVER_NAME% contient le nom de domaine complet de l’ordinateur. Dans le cas contraire, elle contient la valeur par défaut localhost.  
  
- Installation du certificat de serveur dans le magasin de certificats approuvés du client  
  
     La ligne suivante copie le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Octroi d'autorisations sur la clé privée du certificat.  
  
     Les lignes suivantes du fichier Setup. bat rendent le certificat de serveur stocké dans le magasin LocalMachine accessible au compte du processus de travail ASP.NET.  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > Si vous utilisez une édition non américaine de Windows, vous devez modifier le fichier Setup. bat et remplacer le nom de compte « NT AUTHORITY\NETWORK SERVICE » par votre équivalent régional.  
  
> [!NOTE]
> Les outils utilisés dans ce fichier de commandes se trouvent dans C:\Program Files\Microsoft Visual Studio 8\Common7\tools ou C:\Program Files\Microsoft SDKs\Windows\v6.0\bin. L’un de ces répertoires doit se trouver dans votre chemin d’accès système. Si vous avez installé Visual Studio, le moyen le plus simple pour obtenir ce répertoire dans votre chemin d’accès est d’ouvrir le Invite de commandes développeur pour Visual Studio. Cliquez sur **Démarrer**, puis sélectionnez **tous les programmes**, **Visual Studio 2012**, **Outils**. Les chemins d’accès appropriés sont déjà configurés dans cette invite de commandes. Sinon, vous devez ajouter manuellement le répertoire approprié à votre chemin d’accès.  
  
> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer :  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant :  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1. Ouvrez une Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez Setup. bat à partir du dossier d’installation de l’exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.  
  
    > [!NOTE]
    > Le fichier de commandes Setup. bat est conçu pour être exécuté à partir d’un Invite de commandes développeur pour Visual Studio. La variable d'environnement PATH doit pointer vers le répertoire d'installation du Kit de développement SDK. Cette variable d’environnement est définie automatiquement dans une Invite de commandes développeur pour Visual Studio (2010).  
  
2. Vérifiez l’accès au service à l’aide d’un navigateur en entrant l’adresse `http://localhost/servicemodelsamples/service.svc` .  
  
3. Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
4. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Créez un répertoire sur l'ordinateur de service. Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).  
  
2. Copiez les fichiers programme du service de \inetpub\wwwroot\servicemodelsamples dans le répertoire virtuel sur l'ordinateur de service. Assurez-vous de copier les fichiers dans le sous-répertoire \bin. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur l'ordinateur de service.  
  
3. Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.  
  
4. Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.  
  
5. Sur le serveur, exécutez **le service Setup. bat** dans un invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur. L’exécution de **Setup. bat** avec l’argument **service** crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.  
  
6. Modifiez le fichier Web. config pour refléter le nouveau nom de certificat (dans l' `findValue` attribut de [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur.  
  
7. Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.  
  
8. Sur le client, exécutez **le client setup. bat** dans un invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur. L’exécution de **Setup. bat** avec l’argument **client** crée un certificat client nommé client.com et exporte le certificat client vers un fichier nommé client. cer.  
  
9. Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service. Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.  
  
10. Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
11. Sur le client, exécutez ImportServiceCert. bat dans un Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
12. Sur le serveur, exécutez ImportClientCert. bat dans un Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur. Le certificat client est ainsi importé à partir du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.  
  
13. Sur l'ordinateur client, lancez Client.exe à partir d'une fenêtre d'invite de commandes. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Exécutez Cleanup.bat dans le dossier exemples une fois que vous avez terminé d'exécuter l'exemple.  
  
    > [!NOTE]
    > Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs. Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople. Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
