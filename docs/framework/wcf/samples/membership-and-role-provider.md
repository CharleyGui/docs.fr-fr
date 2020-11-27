---
title: Membership and Role Provider
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: fa2a813c2dc1a891119e922c86f045e7f2df7125
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96264710"
---
# <a name="membership-and-role-provider"></a>Membership and Role Provider

L’exemple de fournisseur d’appartenances et de rôles montre comment un service peut utiliser les fournisseurs d’appartenances et de rôles ASP.NET pour authentifier et autoriser des clients.  
  
 Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).  
  
> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.  
  
 L'exemple montre comment :  
  
- Un client peut authentifier des utilisateurs à l'aide de la combinaison nom d'utilisateur et mot de passe.  
  
- Le serveur peut valider les informations d’identification du client par rapport au fournisseur d’appartenances ASP.NET.  
  
- Le serveur peut être authentifié à l'aide du certificat X.509 du serveur.  
  
- Le serveur peut mapper le client authentifié à un rôle à l’aide du fournisseur de rôles ASP.NET.  
  
- Le serveur peut utiliser l'`PrincipalPermissionAttribute` pour contrôler l'accès à certaines méthodes exposées par le service.  
  
 Les fournisseurs d'appartenances et de rôles sont configurés pour utiliser un magasin soutenu par SQL Server. Une chaîne de connexion et différentes options sont spécifiées dans le fichier de configuration du service. Le fournisseur d'appartenances reçoit le nom `SqlMembershipProvider` tandis que le fournisseur de rôles reçoit le nom `SqlRoleProvider`.  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add
        name="SqlMembershipProvider"
        type="System.Web.Security.SqlMembershipProvider"
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 Le service expose un point de terminaison unique de communication avec le service, qui est défini à l'aide du fichier de configuration Web.config. Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat. La liaison est configurée avec une `wsHttpBinding`standard, qui utilise par défaut l'authentification Windows. Cet exemple définit la `wsHttpBinding` standard de manière à utiliser l'authentification du nom d'utilisateur. Le comportement spécifie que le certificat de serveur sera utilisé pour l'authentification du service. Le certificat de serveur doit contenir la même valeur pour le `SubjectName` en tant qu' `findValue` attribut dans l' [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) élément de configuration. En outre, le comportement spécifie que l’authentification des paires nom d’utilisateur/mot de passe est effectuée par le fournisseur d’appartenances ASP.NET et que le mappage de rôle est effectué par le fournisseur de rôle ASP.NET en spécifiant les noms définis pour les deux fournisseurs.  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"
                              storeName ="My"
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Lorsque vous exécutez l'exemple, le client appelle plusieurs opérations de service sous trois comptes d'utilisateurs différents : Alice, Bob et Charlie. Les demandes et réponses de l'opération sont affichées dans la fenêtre de console cliente. Les quatre appels passés par l'utilisateur « Alice » doivent réussir. L'utilisateur « Bob » doit obtenir une erreur d'accès refusé lors de la tentative d'appel de la méthode Divide. L'utilisateur  « Charlie » doit obtenir à une erreur d'accès refusé lors de la tentative d'appel de la méthode Multiply. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple  
  
1. Pour générer l’édition C# ou Visual Basic .NET de la solution, suivez les instructions de la procédure d' [exécution des exemples de Windows Communication Foundation](running-the-samples.md).  
  
2. Vérifiez que vous avez configuré la [base de données ASP.NET services d’application](https://go.microsoft.com/fwlink/?LinkId=94997).  
  
    > [!NOTE]
    > Si vous exécutez SQL Server Express Edition, le nom de votre serveur est .\SQLEXPRESS. Ce serveur doit être utilisé lors de la configuration de la base de données ASP.NET Services d’application ainsi que dans la chaîne de connexion Web.config.  
  
    > [!NOTE]
    > Le compte de processus de travail ASP.NET doit avoir des autorisations sur la base de données créée dans cette étape. Utilisez l'utilitaire sqlcmd ou SQL Server Management Studio pour ce faire.  
  
3. Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions ci-dessous.  
  
### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur  
  
1. Assurez-vous que le chemin d'accès inclut le dossier dans lequel Makecert.exe se trouve.  
  
2. Exécutez Setup.bat à partir du dossier d’installation de l’exemple dans une Invite de commandes développeur pour Visual Studio exécuter avec des privilèges d’administrateur. Tous les certificats de service requis pour l'exécution de l'exemple sont ainsi installés.  
  
3. Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
4. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Créez un répertoire sur l'ordinateur de service. Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).  
  
2. Copiez les fichiers programme du service de \inetpub\wwwroot\servicemodelsamples dans le répertoire virtuel sur l'ordinateur de service. Assurez-vous de copier les fichiers dans le sous-répertoire \bin. Copiez également les fichiers Setup.bat, GetComputerName.vbs et Cleanup.bat sur l'ordinateur de service.  
  
3. Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.  
  
4. Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.  
  
5. Sur le serveur, ouvrez une Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez `setup.bat service` . `setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.  
  
6. Modifiez Web.config pour refléter le nouveau nom de certificat (dans l' `findValue` attribut de [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), qui est le même que le nom de domaine complet de l’ordinateur.  
  
7. Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.  
  
8. Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.  
  
9. Sur le client, ouvrez une Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez ImportServiceCert.bat. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
10. Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Exécutez Cleanup.bat dans le dossier exemples une fois que vous avez terminé d'exécuter l'exemple.  
  
> [!NOTE]
> Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs. Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople. Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.  
  
## <a name="the-setup-batch-file"></a>Le fichier de commandes d'installation  

 Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec les certificats pertinents pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur. Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.  
  
 Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.  
  
- Création du certificat de serveur  
  
     Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser. La variable %SERVER_NAME% spécifie le nom du serveur. Modifiez cette variable pour spécifier votre propre nom de serveur. Ce fichier de commandes a comme valeur par défaut « localhost ».  
  
     Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasins LocalMachine.  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- Installation du certificat de serveur dans le magasin de certificats approuvés du client.  
  
     Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```
