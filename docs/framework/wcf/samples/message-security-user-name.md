---
title: Message Security User Name
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 783969342f007895016ed4183257d6b24188d76c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584725"
---
# <a name="message-security-user-name"></a>Message Security User Name
Cet exemple montre comment implémenter une application qui utilise WS-Security et l'authentification de nom d'utilisateur pour le client et qui nécessite l'authentification du serveur à l'aide de son certificat X.509v3. Tous les messages d'application échangés entre le client et le serveur sont signés et chiffrés. Par défaut, le nom d'utilisateur et le mot de passe fournis par le client sont utilisés pour ouvrir une session à l'aide d'un compte Windows valable. Cet exemple est basé sur [WSHttpBinding](wshttpbinding.md). Cet exemple se compose d'un programme de console client (client.exe) et d'une bibliothèque de service hébergé par les services IIS (Internet Information Services). Le service implémente un contrat qui définit un modèle de communication demande-réponse.  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 Cet exemple montre également :  
  
- Le mappage par défaut aux comptes Windows pour permettre au processus d'autorisation supplémentaire de se dérouler.  
  
- Comment accéder aux informations d'identité de l'appelant à partir du code du service.  
  
 Le service expose un point de terminaison unique pour communiquer avec le service, qui est défini à l’aide du fichier de configuration Web. config. Le point de terminaison se compose d’une adresse, d’une liaison et d’un contrat. La liaison est configurée avec un standard [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) , qui utilise par défaut la sécurité de message. Cet exemple définit la norme [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) pour utiliser l’authentification du nom d’utilisateur du client. Le comportement spécifie que les informations d'identification de l'utilisateur doivent être utilisées à des fins d'authentification du service. Le certificat de serveur doit contenir la même valeur pour le nom du sujet que l' `findValue` attribut dans [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) .  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 La configuration du point de terminaison du client se compose d’une adresse absolue pour le point de terminaison du service, de la liaison et du contrat. La liaison du client est configurée avec le `securityMode` et le `authenticationMode` appropriés. Lors de l'exécution sur plusieurs ordinateurs, l'adresse de point de terminaison du service doit être modifiée en conséquence.  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 L'implémentation cliente définit le nom d'utilisateur et le mot de passe à utiliser.  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 Le fichier de commandes Setup.bat contenu dans les exemples MessageSecurity vous permet de configurer le serveur à l'aide du certificat nécessaire à l'exécution des applications hébergées utilisant une sécurité basée sur des certificats. Deux modes d'exécution sont disponibles pour ce fichier. Pour exécuter le fichier de commandes en mode ordinateur unique, tapez `setup.bat` dans la ligne de commande. Pour l'exécuter en mode service, tapez `setup.bat service`. Utilisez ce mode lorsque l'exemple est exécuté sur plusieurs ordinateurs. Pour plus d'informations, consultez la procédure d'installation figurant en fin de rubrique.  
  
 Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes.  
  
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
  
     La variable %SERVER_NAME% spécifie le nom du serveur. Le certificat est stocké dans le magasin LocalMachine. Si le fichier de commandes Setup.bat est exécuté à l'aide d'un argument de service (tel que `setup.bat service`), la variable % SERVER_NAME% contient le nom de domaine complet de l'ordinateur.  Dans le cas contraire, elle contient la valeur par défaut localhost.  
  
- Installation du certificat de serveur dans le magasin de certificats approuvés du client.  
  
     La ligne suivante copie le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- Octroi d'autorisations sur la clé privée du certificat.  
  
     Les lignes suivantes du fichier de commandes Setup. bat rendent le certificat de serveur stocké dans le magasin LocalMachine accessible au compte du processus de travail ASP.NET.  
  
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
    > Si vous utilisez une édition non américaine de Windows, vous devez modifier le fichier Setup. bat et remplacer le `NT AUTHORITY\NETWORK SERVICE` nom du compte par votre équivalent régional.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1. Assurez-vous que le chemin d’accès contient le dossier dans lequel Makecert.exe et FindPrivateKey.exe se trouvent.  
  
2. Exécutez setup. bat à partir du dossier d’installation de l’exemple dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.  
  
    > [!NOTE]
    > Le fichier de commandes Setup. bat est conçu pour être exécuté à partir d’un Invite de commandes développeur pour Visual Studio. La variable d'environnement PATH doit pointer vers le répertoire d'installation du Kit de développement SDK. Cette variable d’environnement est définie automatiquement dans un Invite de commandes développeur pour Visual Studio.  
  
3. Vérifiez l’accès au service à l’aide d’un navigateur en entrant l’adresse `http://localhost/servicemodelsamples/service.svc` .
  
4. Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
5. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Créez un répertoire sur l'ordinateur de service. Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).  
  
2. Copiez les fichiers programme du service de \inetpub\wwwroot\servicemodelsamples dans le répertoire virtuel sur l'ordinateur de service. Assurez-vous de copier les fichiers dans le sous-répertoire \bin. Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.  
  
3. Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.  
  
4. Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.  
  
5. Sur le serveur, exécutez `setup.bat service` dans un invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur. `setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.  
  
6. Modifiez le fichier Web.config en fonction du nouveau nom du certificat (au niveau de l'attribut findValue de l'élément serviceCertificate), lequel correspond au nom de domaine complet de l'ordinateur`.`  
  
7. Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.  
  
8. Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.  
  
9. Sur le client, exécutez ImportServiceCert. bat dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
10. Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Exécutez Cleanup.bat dans le dossier exemples une fois que vous avez terminé d'exécuter l'exemple.  
  
    > [!NOTE]
    > Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs. Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople. Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
