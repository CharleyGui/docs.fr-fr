---
title: Validateur de nom d'utilisateur et de mot de passe
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: 5fbca30ef2dff0aebc13bda12c06adfd1989ea20
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596511"
---
# <a name="user-name-password-validator"></a>Validateur de nom d'utilisateur et de mot de passe
Cet exemple montre comment implémenter un validateur UserNamePassword personnalisé. Cela s’avère utile dans les cas où aucun des modes de validation UserNamePassword intégrés ne convient aux exigences de l’application ; par exemple, lorsque les paires nom d’utilisateur/mot de passe sont stockées dans quelque magasin externe, tel qu’une base de données. Cet exemple illustre un service qui comprend un validateur personnalisé qui vérifie pour deux paires nom d'utilisateur/mot de passe particulières. Le client utilise une paire nom d'utilisateur/mot de passe pour s'authentifier auprès du service.

> [!IMPORTANT]
> Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> Étant donné que n'importe qui peut générer une information d'identification de nom d'utilisateur qui utilise les paires nom d'utilisateur/mot de passe acceptées par le validateur personnalisé, le service est moins sécurisé que le comportement par défaut fourni par le validateur UserNamePassword standard. Le validateur UserNamePassword standard essaie de mapper la paire nom d'utilisateur/mot de passe fournie à un compte Windows et fait échouer l'authentification si ce mappage échoue. Le validateur UserNamePassword personnalisé dans cet exemple NE DOIT PAS être utilisé dans le code de production ; il est fourni à titre d'illustration uniquement.

 En résumé, cet exemple montre comment :

- Le client peut être authentifié à l'aide d'un jeton de nom d'utilisateur ;

- Le serveur valide les informations d’identification du client à l’aide d’un UserNamePasswordValidator personnalisé et comment propager les erreurs personnalisées de la logique de validation du nom d’utilisateur et du mot de passe au client ;

- Le serveur est authentifié à l'aide du certificat X.509 du serveur.

 Le service expose un point de terminaison unique pour communiquer avec le service, défini à l’aide du fichier de configuration, app. config. Le point de terminaison se compose d’une adresse, d’une liaison et d’un contrat. La liaison est configurée avec une norme `wsHttpBinding` qui utilise par défaut le protocole WS-Security et l’authentification du nom d’utilisateur. Le comportement de service spécifie le mode `Custom` pour valider les paires nom d'utilisateur/mot de passe du client avec le type de la classe de validateur. Le comportement spécifie également le certificat de serveur à l'aide de l'élément `serviceCertificate`. Le certificat de serveur doit contenir la même valeur pour le `SubjectName` que le `findValue` dans le [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <!-- use host/baseAddresses to configure base address provided by host -->
      <host>
        <baseAddresses>
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service" />
        </baseAddresses>
      </host>
      <!-- use base address specified above, provide one endpoint -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- username binding -->
      <binding name="Binding">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceDebug includeExceptionDetailInFaults ="true"/>
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to
          specify a custom validator for username/password
          combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom"
                                  customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate. A service certificate is used by a client to authenticate the service and provide message protection. You must specify a server certificate when passing username/passwords to encrypt the information as it is sent on the wire. Otherwise the username and password information would be sent as clear text. This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

 La configuration de point de terminaison de client se compose d’un nom de configuration, d’une adresse absolue pour le point de terminaison de service, de la liaison et du contrat. La liaison de client est configurée avec le mode et le message `clientCredentialType` appropriés.

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
address="http://localhost:8001/servicemodelsamples/service/username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!--
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
            is in the user's Trusted People store, then it will be trusted without performing a
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
```

 L'implémentation cliente invite l'utilisateur à entrer un nom d'utilisateur et un mot de passe.

```csharp
// Get the username and password
Console.WriteLine("Username authentication required.");
Console.WriteLine("Provide a username.");
Console.WriteLine("   Enter username: (test1)");
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
            password = password.Substring(0, password.Length - 1);
        }
        info = Console.ReadKey(true);
    }
}
for (int i = 0; i < password.Length; i++)
{
    Console.Write("*");
}
Console.WriteLine();
// Create a proxy with Certificate endpoint configuration
CalculatorProxy proxy = new CalculatorProxy("Username")
try
{
  proxy.ClientCredentials.Username.Username = username;
  proxy.ClientCredentials.Username.Password = password;
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = proxy.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
  }
  catch (Exception e)
  {
      Console.WriteLine("Call failed:");
      while (e != null)
      {
          Console.WriteLine("\t{0}", e.Message);
          e = e.InnerException;
      }
      proxy.Abort();
  }
}
```

 Cet exemple utilise un UserNamePasswordValidator personnalisé pour valider des paires nom d'utilisateur/mot de passe. L'exemple implémente `CustomUserNamePasswordValidator`, dérivé de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Pour plus d'informations, consultez la documentation de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Cet exemple de validateur personnalisé particulier implémente la méthode `Validate` pour accepter deux paires nom d'utilisateur/mot de passe particulières, comme le montre le code suivant.

```csharp
public class CustomUserNameValidator : UserNamePasswordValidator
{
 // This method validates users. It allows in two users,
 // test1 and test2 with passwords 1tset and 2tset respectively.
 // This code is for illustration purposes only and
 // MUST NOT be used in a production environment because it
 // is NOT secure.
 public override void Validate(string userName, string password)
 {
  if (null == userName || null == password)
  {
   throw new ArgumentNullException();
  }

  if (!(userName == "test1" && password == "1tset") && !(userName == "test2" && password == "2tset"))
  {
   throw new FaultException("Unknown Username or Incorrect Password");
   }
  }
 }
```

 Une fois que le validateur est implémenté dans le code de service, l'hôte de service doit être informé de l'instance de validateur à utiliser. Cela est effectué à l'aide du code suivant.

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 Vous pouvez faire la même chose dans la configuration comme suit.

```xml
<behaviors>
 <serviceBehaviors>
  <behavior name="CalculatorServiceBehavior">
  ...
   <serviceCredentials>
    <!--
    The serviceCredentials behavior allows one to specify authentication constraints on username / password combinations.
    -->
    <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.CalculatorService+CustomUserNameValidator, service" />
   ...
   </serviceCredentials>
  </behavior>
 </serviceBehaviors>
</behaviors>
```

 Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Le client doit appeler toutes les méthodes avec succès. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.

## <a name="setup-batch-file"></a>Fichier de commandes d'installation
 Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec les certificats pertinents pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur. Ce fichier doit être modifié pour fonctionner sur plusieurs ordinateurs ou dans un cas non hébergé.

 Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.

- Création du certificat de serveur :

     Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser. La variable %SERVER_NAME% spécifie le nom du serveur. Modifiez cette variable pour spécifier votre propre nom de serveur. La valeur par défaut est localhost.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Installation du certificat de serveur dans le magasin de certificats approuvés du client :

     Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple

1. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

2. Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, utilisez les instructions suivantes.

#### <a name="to-run-the-sample-on-the-same-machine"></a>Pour exécuter l'exemple sur le même ordinateur

1. Exécutez setup. bat à partir du dossier d’installation de l’exemple à l’intérieur d’une invite de commandes de Visual Studio 2012. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.

    > [!NOTE]
    > Le fichier de commandes Setup. bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012. La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup. bat.  
  
2. Lancez Service.exe à partir de service\bin.  
  
3. Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
4. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-machines"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Créez un répertoire sur l'ordinateur de service destiné aux fichiers binaires de service.  
  
2. Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service. Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.  
  
3. Il vous faut un certificat de serveur dont le nom du sujet contient le nom de domaine complet de l'ordinateur. Le fichier de configuration pour le serveur doit être mis à jour pour refléter ce nouveau nom de certificat.  
  
4. Copiez le certificat de serveur dans le magasin CurrentUser-TrustedPeople du client. Cette tâche est requise uniquement si le certificat du serveur n'est pas publié par un émetteur approuvé.  
  
5. Dans le fichier App.config sur l'ordinateur de service, modifiez la valeur de l'adresse de base afin de remplacer localhost par un nom d'ordinateur complet.  
  
6. Sur l'ordinateur de service, lancez Service.exe à partir d'une fenêtre d'invite de commandes.  
  
7. Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.  
  
8. Dans le fichier Client.exe.config sur l'ordinateur client, modifiez la valeur d'adresse du point de terminaison pour qu'il corresponde à la nouvelle adresse de votre service.  
  
9. Sur l'ordinateur du client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.  
  
10. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
1. Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple. Cela supprime le certificat de serveur du magasin de certificats.  
