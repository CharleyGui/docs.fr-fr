---
title: Supporting Tokens
ms.date: 03/30/2017
ms.assetid: 65a8905d-92cc-4ab0-b6ed-1f710e40784e
ms.openlocfilehash: ff46a2f5289bc72244ea586f01ea05504d628f69
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555196"
---
# <a name="supporting-tokens"></a>Supporting Tokens
Cet exemple montre comment ajouter des jetons supplémentaires à un message qui utilise WS-Security. L'exemple ajoute un jeton de sécurité binaire X.509 outre un jeton de sécurité de nom d'utilisateur. Le jeton est passé dans un en-tête de message WS-Security du client au service et une partie du message est signée avec la clé privée associée au jeton de sécurité X.509 pour prouver la possession du certificat X.509 au récepteur. Cela s’avère utile dans le cas où plusieurs revendications doivent être associées à un message pour authentifier ou autoriser l’expéditeur. Le service implémente un contrat qui définit un modèle de communication demande-réponse.

## <a name="demonstrates"></a>Illustre le
 L'exemple montre :

- Comment un client peut passer des jetons de sécurité supplémentaires à un service.

- Comment le serveur peut accéder aux revendications associées aux jetons de sécurité supplémentaires.

- Comment le certificat X.509 du serveur permet de protéger la clé symétrique utilisée pour la signature et le chiffrement des messages.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

## <a name="client-authenticates-with-username-token-and-supporting-x509-security-token"></a>Le client s'authentifie à l'aide du jeton de nom d'utilisateur et du jeton de sécurité X.509 de prise en charge
 Le service expose un point de terminaison unique de communication qui est créé par programme à l'aide des classes `BindingHelper` et `EchoServiceHost`. Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat. La liaison est configurée avec une liaison personnalisé à l'aide de `SymmetricSecurityBindingElement` et `HttpTransportBindingElement`. Cet exemple oblige `SymmetricSecurityBindingElement` à utiliser un certificat X.509 du service pour protéger la clé symétrique pendant la transmission et à passer un `UserNameToken` avec le `X509SecurityToken` de prise en charge dans un en-tête de message WS-Security. La clé symétrique permet de chiffrer le corps du message et le jeton de sécurité de nom d'utilisateur. Le jeton de prise en charge est passé comme jeton de sécurité binaire supplémentaire dans l'en-tête de message WS-Security. L'authenticité du jeton de prise en charge est prouvée en signant une partie du message avec la clé privée associée au jeton de sécurité X.509 de prise en charge.

```csharp
public static Binding CreateMultiFactorAuthenticationBinding()
{
    HttpTransportBindingElement httpTransport = new HttpTransportBindingElement();

    // the message security binding element will be configured to require 2 tokens:
    // 1) A username-password encrypted with the service token
    // 2) A client certificate used to sign the message

    // Instantiate a binding element that will require the username/password token in the message (encrypted with the server cert)
    SymmetricSecurityBindingElement messageSecurity = SecurityBindingElement.CreateUserNameForCertificateBindingElement();

    // Create supporting token parameters for the client X509 certificate.
    X509SecurityTokenParameters clientX509SupportingTokenParameters = new X509SecurityTokenParameters();
    // Specify that the supporting token is passed in message send by the client to the service
    clientX509SupportingTokenParameters.InclusionMode = SecurityTokenInclusionMode.AlwaysToRecipient;
    // Turn off derived keys
    clientX509SupportingTokenParameters.RequireDerivedKeys = false;
    // Augment the binding element to require the client's X509 certificate as an endorsing token in the message
    messageSecurity.EndpointSupportingTokenParameters.Endorsing.Add(clientX509SupportingTokenParameters);

    // Create a CustomBinding based on the constructed security binding element.
    return new CustomBinding(messageSecurity, httpTransport);
}
```

 Le comportement spécifie les informations d'identification du service qui doivent être utilisées pour l'authentification du client ainsi que les informations sur le certificat X.509 du service. L'exemple utilise `CN=localhost` comme nom du sujet dans le certificat X.509 du service.

```csharp
override protected void InitializeRuntime()
{
    // Extract the ServiceCredentials behavior or create one.
    ServiceCredentials serviceCredentials =
        this.Description.Behaviors.Find<ServiceCredentials>();
    if (serviceCredentials == null)
    {
        serviceCredentials = new ServiceCredentials();
        this.Description.Behaviors.Add(serviceCredentials);
    }

    // Set the service certificate
    serviceCredentials.ServiceCertificate.SetCertificate(
                                       "CN=localhost");

/*
Setting the CertificateValidationMode to PeerOrChainTrust means that if the certificate is in the Trusted People store, then it will be trusted without performing a validation of the certificate's issuer chain. This setting is used here for convenience so that the sample can be run without having to have certificates issued by a certification authority (CA).
This setting is less secure than the default, ChainTrust. The security implications of this setting should be carefully considered before using PeerOrChainTrust in production code.
*/
    serviceCredentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;

    // Create the custom binding and add an endpoint to the service.
    Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
    this.AddServiceEndpoint(typeof(IEchoService),
                          multipleTokensBinding, string.Empty);
    base.InitializeRuntime();
}
```

 Code de service :

```csharp
[ServiceBehavior(IncludeExceptionDetailInFaults = true)]
public class EchoService : IEchoService
{
    public string Echo()
    {
        string userName;
        string certificateSubjectName;
        GetCallerIdentities(
            OperationContext.Current.ServiceSecurityContext,
            out userName,
            out certificateSubjectName);
            return $"Hello {userName}, {certificateSubjectName}";
    }

    public void Dispose()
    {
    }

    bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet,
            string claimType, out TClaimResource resourceValue)
            where TClaimResource : class
    {
        resourceValue = default(TClaimResource);
        IEnumerable<Claim> matchingClaims =
            claimSet.FindClaims(claimType, Rights.PossessProperty);
        if(matchingClaims == null)
            return false;
        IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
        if (enumerator.MoveNext())
        {
            resourceValue =
              (enumerator.Current.Resource == null) ? null :
              (enumerator.Current.Resource as TClaimResource);
            return true;
        }
        else
        {
            return false;
        }
    }

    // Returns the username and certificate subject name provided by
    //the client
    void GetCallerIdentities(ServiceSecurityContext
        callerSecurityContext,
        out string userName, out string certificateSubjectName)
    {
        userName = null;
        certificateSubjectName = null;

       // Look in all the claimsets in the authorization context
       foreach (ClaimSet claimSet in
               callerSecurityContext.AuthorizationContext.ClaimSets)
       {
            if (claimSet is WindowsClaimSet)
            {
                // Try to find a Name claim. This will have been
                // generated from the windows username.
                string tmpName;
                if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                      out tmpName))
                {
                    userName = tmpName;
                }
            }
            else if (claimSet is X509CertificateClaimSet)
            {
                // Try to find an X500DistinguishedName claim. This will
                // have been generated from the client certificate.
                X500DistinguishedName tmpDistinguishedName;
                if (TryGetClaimValue<X500DistinguishedName>(claimSet,
                               ClaimTypes.X500DistinguishedName,
                               out tmpDistinguishedName))
                {
                    certificateSubjectName = tmpDistinguishedName.Name;
                }
            }
        }
    }
}
```

 Le point de terminaison client est configuré de la même manière que le point de terminaison de service. Le client utilise une classe `BindingHelper` identique pour créer sa liaison. La suite de la configuration s'effectue dans classe `Client`. Le client définit les formations sur le jeton de sécurité de nom d’utilisateur, le jeton de sécurité X.509 de prise en charge et les informations sur le certificat X.509 du service dans le code d’installation vers la collection de comportements de point de terminaison client.

```csharp
 static void Main()
 {
     // Create the custom binding and an endpoint address for
     // the service.
     Binding multipleTokensBinding =
         BindingHelper.CreateMultiFactorAuthenticationBinding();
         EndpointAddress serviceAddress = new EndpointAddress(
         "http://localhost/servicemodelsamples/service.svc");
       ChannelFactory<IEchoService> channelFactory = null;
       IEchoService client = null;

       Console.WriteLine("Username authentication required.");
       Console.WriteLine(
         "Provide a valid machine or domain account. [domain\\user]");
       Console.WriteLine("   Enter username:");
       string username = Console.ReadLine();
       Console.WriteLine("   Enter password:");
       string password = "";
       ConsoleKeyInfo info = Console.ReadKey(true);
       while (info.Key != ConsoleKey.Enter)
       {
           if (info.Key != ConsoleKey.Backspace)
           {
               if (info.KeyChar != '\0')
               {
                   password += info.KeyChar;
                }
                info = Console.ReadKey(true);
            }
            else if (info.Key == ConsoleKey.Backspace)
            {
                if (password != "")
                {
                    password =
                       password.Substring(0, password.Length - 1);
                }
                info = Console.ReadKey(true);
            }
         }
         for (int i = 0; i < password.Length; i++)
            Console.Write("*");
         Console.WriteLine();
         try
         {
           // Create a proxy with the previously create binding and
           // endpoint address
              channelFactory =
                 new ChannelFactory<IEchoService>(
                     multipleTokensBinding, serviceAddress);
           // configure the username credentials, the client
           // certificate and the server certificate on the channel
           // factory
           channelFactory.Credentials.UserName.UserName = username;
           channelFactory.Credentials.UserName.Password = password;
           channelFactory.Credentials.ClientCertificate.SetCertificate(
           "CN=client.com", StoreLocation.CurrentUser, StoreName.My);
              channelFactory.Credentials.ServiceCertificate.SetDefaultCertificate(
           "CN=localhost", StoreLocation.LocalMachine, StoreName.My);
           client = channelFactory.CreateChannel();
           Console.WriteLine("Echo service returned: {0}",
                                           client.Echo());

           ((IChannel)client).Close();
           channelFactory.Close();
        }
        catch (CommunicationException e)
        {
         Abort((IChannel)client, channelFactory);
         // if there is a fault then print it out
         FaultException fe = null;
         Exception tmp = e;
         while (tmp != null)
         {
            fe = tmp as FaultException;
            if (fe != null)
            {
                break;
            }
            tmp = tmp.InnerException;
        }
        if (fe != null)
        {
           Console.WriteLine("The server sent back a fault: {0}",
         fe.CreateMessageFault().Reason.GetMatchingTranslation().Text);
        }
        else
        {
         Console.WriteLine("The request failed with exception: {0}",e);
        }
    }
    catch (TimeoutException)
    {
        Abort((IChannel)client, channelFactory);
        Console.WriteLine("The request timed out");
    }
    catch (Exception e)
    {
         Abort((IChannel)client, channelFactory);
          Console.WriteLine(
          "The request failed with unexpected exception: {0}", e);
    }
    Console.WriteLine();
    Console.WriteLine("Press <ENTER> to terminate client.");
    Console.ReadLine();
}
```

## <a name="displaying-callers-information"></a>Affichage des informations sur les appelants
 Pour afficher les informations sur l'appelant, vous pouvez utiliser `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets`, tel qu'indiqué dans le code suivant. `ServiceSecurityContext.Current.AuthorizationContext.ClaimSets` contient les revendications d'autorisation associées à l'appelant actuel. Ces revendications sont fournies automatiquement par Windows Communication Foundation (WCF) pour chaque jeton reçu dans le message.

```csharp
bool TryGetClaimValue<TClaimResource>(ClaimSet claimSet, string
                         claimType, out TClaimResource resourceValue)
    where TClaimResource : class
{
    resourceValue = default(TClaimResource);
    IEnumerable<Claim> matchingClaims =
    claimSet.FindClaims(claimType, Rights.PossessProperty);
    if (matchingClaims == null)
          return false;
    IEnumerator<Claim> enumerator = matchingClaims.GetEnumerator();
    if (enumerator.MoveNext())
    {
        resourceValue = (enumerator.Current.Resource == null) ? null : (enumerator.Current.Resource as TClaimResource);
        return true;
    }
    else
    {
         return false;
    }
}

// Returns the username and certificate subject name provided by the client
void GetCallerIdentities(ServiceSecurityContext callerSecurityContext, out string userName, out string certificateSubjectName)
{
    userName = null;
    certificateSubjectName = null;

    // Look in all the claimsets in the authorization context
    foreach (ClaimSet claimSet in
      callerSecurityContext.AuthorizationContext.ClaimSets)
    {
        if (claimSet is WindowsClaimSet)
        {
            // Try to find a Name claim. This will have been generated
            //from the windows username.
            string tmpName;
            if (TryGetClaimValue<string>(claimSet, ClaimTypes.Name,
                                                     out tmpName))
            {
                userName = tmpName;
            }
        }
        else if (claimSet is X509CertificateClaimSet)
         {
            //Try to find an X500DistinguishedName claim.
            //This will have been generated from the client
            //certificate.
            X500DistinguishedName tmpDistinguishedName;
            if (TryGetClaimValue<X500DistinguishedName>(claimSet,
               ClaimTypes.X500DistinguishedName,
               out tmpDistinguishedName))
            {
                    certificateSubjectName = tmpDistinguishedName.Name;
            }
        }
    }
}
```

## <a name="running-the-sample"></a>Exécution de l'exemple
 Lorsque vous exécutez l'exemple, le client vous invite d'abord à fournir un nom d'utilisateur et un mot de passe pour le jeton de nom d'utilisateur. Veillez à fournir les valeurs correctes pour votre compte système, car WCF sur le service mappe les valeurs fournies dans le jeton de nom d’utilisateur à l’identité fournie par le système. Ceci fait, le client affiche la réponse provenant du service. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.

## <a name="setup-batch-file"></a>Fichier de commandes d'installation
 Le fichier de commandes Setup.bat inclus avec cet exemple vous permet de configurer le serveur avec les certificats appropriés pour exécuter l'application hébergée IIS (Internet Information Services) qui requiert une sécurité basée sur le certificat du serveur. Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.

 Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.

### <a name="creating-the-client-certificate"></a>Création du certificat client
 Les lignes suivantes du fichier de commandes Setup.bat créent le certificat client à utiliser. La variable `%CLIENT_NAME%` spécifie le sujet du certificat client. Cet exemple utilise "client.com" comme nom du sujet.

 Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasin `CurrentUser`.

```console
echo ************
echo making client cert
echo ************
makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
```

### <a name="installing-the-client-certificate-into-the-servers-trusted-store"></a>Installation du certificat client dans le magasin approuvé du serveur :
 La ligne suivante du fichier de commandes Setup.bat copie le certificat client dans le magasin de personnes de confiance du serveur. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système du serveur. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.

```console
echo ************
echo copying client cert to server's CurrentUserstore
echo ************
certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
```

### <a name="creating-the-server-certificate"></a>Création du certificat de serveur
 Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser. La variable `%SERVER_NAME%` spécifie le nom du serveur. Modifiez cette variable pour spécifier votre propre nom de serveur. La valeur par défaut dans ce fichier de commandes est localhost.

 Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasins LocalMachine. Le certificat est stocké dans le magasin LocalMachine pour les services hébergés par IIS. Pour les services auto-hébergés, vous devez modifier le fichier de commandes afin de stocker le certificat de serveur dans l'emplacement de magasin CurrentUser en remplaçant la chaîne LocalMachine par CurrentUser.

```console
echo ************
echo Server cert setup starting
echo %SERVER_NAME%
echo ************
echo making server cert
echo ************
makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
```

### <a name="installing-server-certificate-into-clients-trusted-certificate-store"></a>Installation du certificat de serveur dans le magasin de certificats approuvé du client :
 Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.

```console
echo ************
echo copying server cert to client's TrustedPeople store
echo ************certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
```

### <a name="enabling-access-to-the-certificates-private-key"></a>Activation de l'accès à la clé privée du certificat
 Pour activer l'accès à la clé privée du certificat à partir du service hébergé par IIS, le compte d'utilisateur sous lequel le processus hébergé par IIS s'exécute doit disposer des autorisations permettant d'y accéder. Cette opération est effectuée par les dernières étapes du script Setup.bat.

```console
echo ************
echo setting privileges on server certificates
echo ************
for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i
set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
(ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
iisreset
```

##### <a name="to-set-up-build-and-run-the-sample"></a>Pour configurer, générer et exécuter l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

3. Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, utilisez les instructions suivantes.

##### <a name="to-run-the-sample-on-the-same-machine"></a>Pour exécuter l'exemple sur le même ordinateur

1. Exécutez Setup.bat à partir du dossier d’installation de l’exemple à l’aide de l’invite de commandes de Visual Studio 2012 avec des privilèges d’administrateur. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.

    > [!NOTE]
    > Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012. La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat. Assurez-vous de supprimer les certificats en exécutant Cleanup.bat une fois l'exemple terminé. D'autres exemples de sécurité utilisent ces mêmes certificats.  
  
2. Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
3. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-run-the-sample-across-machines"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Créez un répertoire sur l'ordinateur de service. Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).  
  
2. Copiez les fichiers du programme de service figurant dans le dossier \inetpub\wwwroot\servicemodelsamples dans ce répertoire virtuel. Assurez-vous de copier les fichiers dans le sous-répertoire \bin. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur l'ordinateur de service.  
  
3. Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.  
  
4. Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.  
  
5. Sur le serveur, exécutez `setup.bat service` dans un invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur. `setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.  
  
6. Modifiez Web.config pour refléter le nouveau nom de certificat (dans l' `findValue` attribut dans [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur.  
  
7. Copiez le fichier Service.cer du répertoire de service dans le répertoire client sur l'ordinateur client.  
  
8. Sur le client, exécutez `setup.bat client` dans un invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur. L'exécution de `setup.bat` à l'aide de l'argument `client` crée un certificat client appelé client.com, puis exporte ce certificat vers un fichier nommé Client.cer.  
  
9. Dans le fichier Client.exe.config sur l'ordinateur client, modifiez la valeur d'adresse du point de terminaison pour qu'il corresponde à la nouvelle adresse de votre service. Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.  
  
10. Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.  
  
11. Sur le client, exécutez ImportServiceCert.bat. Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.  
  
12. Sur le serveur, exécutez ImportClientCert.bat. Cette opération importe le certificat client du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.  
  
13. Sur l'ordinateur du client, lancez Client.exe à partir d'une fenêtre d'invite de commandes. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
##### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
- Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.  
  
> [!NOTE]
> Ce script ne supprime pas les certificats de service figurant sur le client lorsque l'exemple est exécuté sur plusieurs ordinateurs. Si vous avez exécuté des exemples WCF qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople. Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
