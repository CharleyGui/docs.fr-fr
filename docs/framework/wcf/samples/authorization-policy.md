---
title: Authorization Policy
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: 5b93f7e05261d9770650335160ddb56404aed94d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84585504"
---
# <a name="authorization-policy"></a>Authorization Policy

Cet exemple montre comment implémenter une stratégie d'autorisation de revendication personnalisée et un gestionnaire d'autorisations de service personnalisé associé. Cela s'avère utile lorsque le service procède à des vérifications d'accès basées sur des revendications sur des opérations de service et, avant d'effectuer ces vérifications, accorde certains droits à l'appelant. Cet exemple illustre à la fois le processus d'ajout de revendications ainsi que le processus de vérification de l'accès en fonction de l'ensemble de revendications finalisé. Tous les messages d'application échangés entre le client et le serveur sont signés et chiffrés. Par défaut, avec la liaison `wsHttpBinding`, un nom d’utilisateur et un mot de passe fournis par le client sont utilisés pour l’ouverture de session d’un compte Windows NT valide. Cet exemple montre comment utiliser un <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> personnalisé pour authentifier le client. De plus, cet exemple montre comment le client s'authentifie auprès du service à l'aide d'un certificat X.509. Cet exemple montre une implémentation de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> et <xref:System.ServiceModel.ServiceAuthorizationManager>, qui accordent à des utilisateurs spécifiques l'accès à des méthodes spécifiques du service. Cet exemple est basé sur le [nom d’utilisateur de sécurité du message](message-security-user-name.md), mais montre comment effectuer une transformation de revendication avant l' <xref:System.ServiceModel.ServiceAuthorizationManager> appel de.

> [!NOTE]
> La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.

 En résumé, cet exemple montre comment :

- Le client peut être authentifié à l'aide d'un nom d'utilisateur et d'un mot de passe ;

- Le client peut être authentifié à l'aide d'un certificat X.509 ;

- Le serveur valide les informations d'identification du client en fonction d'un validateur `UsernamePassword` personnalisé ;

- Le serveur est authentifié à l'aide du certificat X.509 du serveur.

- Le serveur peut utiliser <xref:System.ServiceModel.ServiceAuthorizationManager> pour contrôler l'accès à certaines méthodes dans le service ;

- Implémenter une interface <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.

Le service expose deux points de terminaison pour communiquer avec le service, défini à l’aide du fichier de configuration App. config. Chaque point de terminaison se compose d’une adresse, d’une liaison et d’un contrat. Une liaison est configurée avec une liaison `wsHttpBinding` standard qui utilise WS-Security et l’authentification du nom d’utilisateur du client. L'autre liaison est configurée avec une liaison `wsHttpBinding` standard qui utilise WS-Security et l'authentification du certificat du client. [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)Spécifie que les informations d’identification de l’utilisateur doivent être utilisées pour l’authentification du service. Le certificat de serveur doit contenir la même valeur pour la `SubjectName` propriété que l' `findValue` attribut dans [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .

```xml
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <!-- configure base address provided by host -->
          <add baseAddress ="http://localhost:8001/servicemodelsamples/service"/>
        </baseAddresses>
      </host>
      <!-- use base address provided by host, provide two endpoints -->
      <endpoint address="username"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <endpoint address="certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding2"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </service>
  </services>

  <bindings>
    <wsHttpBinding>
      <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
    <message clientCredentialType="UserName" />
        </security>
      </binding>
      <!-- X509 certificate binding -->
      <binding name="Binding2">
        <security mode="Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>

  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior" >
        <serviceDebug includeExceptionDetailInFaults ="true" />
        <serviceCredentials>
          <!--
          The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
          -->
          <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
          <!--
          The serviceCredentials behavior allows one to specify authentication constraints on client certificates.
          -->
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
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
          -->
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
        </serviceCredentials>
        <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
          <!--
          The serviceAuthorization behavior allows one to specify custom authorization policies.
          -->
          <authorizationPolicies>
            <add policyType="Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary" />
          </authorizationPolicies>
        </serviceAuthorization>
      </behavior>
    </serviceBehaviors>
  </behaviors>

</system.serviceModel>
```

Chaque configuration de point de terminaison de client se compose d'un nom de configuration, d'une adresse absolue pour le point de terminaison de service, de la liaison et du contrat. La liaison client est configurée avec le mode de sécurité approprié, tel que spécifié dans ce cas dans le [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) et `clientCredentialType` comme spécifié dans le [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) .

```xml
<system.serviceModel>

    <client>
      <!-- Username based endpoint -->
      <endpoint name="Username"
            address="http://localhost:8001/servicemodelsamples/service/username"
    binding="wsHttpBinding"
    bindingConfiguration="Binding1"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" >
      </endpoint>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
                        address="http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
            bindingConfiguration="Binding2"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <!-- Username binding -->
      <binding name="Binding1">
        <security mode="Message">
          <message clientCredentialType="UserName" />
        </security>
      </binding>
        <!-- X509 certificate binding -->
        <binding name="Binding2">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
    </wsHttpBinding>
    </bindings>

    <behaviors>
      <behavior name="ClientCertificateBehavior">
        <clientCredentials>
          <serviceCertificate>
            <!--
            Setting the certificateValidationMode to PeerOrChainTrust
            means that if the certificate
            is in the user's Trusted People store, then it will be
            trusted without performing a
            validation of the certificate's issuer chain. This setting
            is used here for convenience so that the
            sample can be run without having to have certificates
            issued by a certification authority (CA).
            This setting is less secure than the default, ChainTrust.
            The security implications of this
            setting should be carefully considered before using
            PeerOrChainTrust in production code.
            -->
            <authentication certificateValidationMode = "PeerOrChainTrust" />
          </serviceCertificate>
        </clientCredentials>
      </behavior>
    </behaviors>

  </system.serviceModel>
```

Pour le point de terminaison basé sur nom de l'utilisateur , l'implémentation cliente définit le nom d'utilisateur et le mot de passe à utiliser.

```csharp
// Create a client with Username endpoint configuration
CalculatorClient client1 = new CalculatorClient("Username");

client1.ClientCredentials.UserName.UserName = "test1";
client1.ClientCredentials.UserName.Password = "1tset";

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client1.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client1.Close();
```

Pour le point de terminaison basé sur certificat, l'implémentation cliente définit le certificat client à utiliser.

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client2 = new CalculatorClient("Certificate");

client2.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

try
{
    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client2.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);
    ...
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
}

client2.Close();
```

Cet exemple utilise un <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> personnalisé pour valider les noms d'utilisateur et les mots de passe. L'exemple implémente `MyCustomUserNamePasswordValidator`, dérivé de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Pour plus d'informations, consultez la documentation relative au <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>. Pour les besoins de la démonstration de l'intégration avec le <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, cet exemple de validateur personnalisé implémente la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> pour accepter des paires de nom d'utilisateur/mot de passe où le nom d'utilisateur correspond au mot de passe comme le montre le code suivant.

```csharp
public class MyCustomUserNamePasswordValidator : UserNamePasswordValidator
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
      throw new SecurityTokenException("Unknown Username or Password");
    }
  }
}
```

Une fois que le validateur est implémenté dans le code de service, l'hôte de service doit être informé de l'instance de validateur à utiliser. Pour ce faire, utilisez le code suivant :

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

Vous pouvez aussi faire la même chose dans la configuration :

```xml
<behavior>
    <serviceCredentials>
      <!--
      The serviceCredentials behavior allows one to specify a custom validator for username/password combinations.
      -->
      <userNameAuthentication userNamePasswordValidationMode="Custom" customUserNamePasswordValidatorType="Microsoft.ServiceModel.Samples.MyCustomUserNameValidator, service" />
    ...
    </serviceCredentials>
</behavior>
```

Windows Communication Foundation (WCF) fournit un modèle riche basé sur les revendications pour effectuer des vérifications d’accès. L’objet <xref:System.ServiceModel.ServiceAuthorizationManager> est utilisé pour effectuer la vérification d’accès et détermine si les revendications associées au client répondent aux exigences nécessaires pour accéder à la méthode de service.

À des fins de démonstration, cet exemple montre une implémentation de <xref:System.ServiceModel.ServiceAuthorizationManager> qui implémente la <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> méthode pour permettre à l’utilisateur d’accéder aux méthodes en fonction des revendications de type `http://example.com/claims/allowedoperation` dont la valeur est l’URI d’action de l’opération qui est autorisée à être appelée.

```csharp
public class MyServiceAuthorizationManager : ServiceAuthorizationManager
{
  protected override bool CheckAccessCore(OperationContext operationContext)
  {
    string action = operationContext.RequestContext.RequestMessage.Headers.Action;
    Console.WriteLine("action: {0}", action);
    foreach(ClaimSet cs in operationContext.ServiceSecurityContext.AuthorizationContext.ClaimSets)
    {
      if ( cs.Issuer == ClaimSet.System )
      {
        foreach (Claim c in cs.FindClaims("http://example.com/claims/allowedoperation", Rights.PossessProperty))
        {
          Console.WriteLine("resource: {0}", c.Resource.ToString());
          if (action == c.Resource.ToString())
            return true;
        }
      }
    }
    return false;
  }
}
```

Une fois que le <xref:System.ServiceModel.ServiceAuthorizationManager> personnalisé est implémenté, l'hôte de service doit être informé du <xref:System.ServiceModel.ServiceAuthorizationManager> à utiliser. Cela est illustré dans le code suivant :

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

La méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy> principale à implémenter est la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>.

```csharp
public class MyAuthorizationPolicy : IAuthorizationPolicy
{
    string id;

    public MyAuthorizationPolicy()
    {
    id =  Guid.NewGuid().ToString();
    }

    public bool Evaluate(EvaluationContext evaluationContext,
                                            ref object state)
    {
        bool bRet = false;
        CustomAuthState customstate = null;

        if (state == null)
        {
            customstate = new CustomAuthState();
            state = customstate;
        }
        else
            customstate = (CustomAuthState)state;
        Console.WriteLine("In Evaluate");
        if (!customstate.ClaimsAdded)
        {
           IList<Claim> claims = new List<Claim>();

           foreach (ClaimSet cs in evaluationContext.ClaimSets)
              foreach (Claim c in cs.FindClaims(ClaimTypes.Name,
                                         Rights.PossessProperty))
                  foreach (string s in
                        GetAllowedOpList(c.Resource.ToString()))
                  {
                       claims.Add(new
               Claim("http://example.com/claims/allowedoperation",
                                    s, Rights.PossessProperty));
                            Console.WriteLine("Claim added {0}", s);
                      }
                   evaluationContext.AddClaimSet(this,
                           new DefaultClaimSet(this.Issuer,claims));
                   customstate.ClaimsAdded = true;
                   bRet = true;
                }
         else
         {
              bRet = true;
         }
         return bRet;
     }
...
}
```

Le code précédent montre comment la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> vérifie qu'aucune nouvelle revendication n'a été ajoutée qui affecte le traitement et ajoute des revendications spécifiques. Les revendications autorisées sont obtenues de la méthode `GetAllowedOpList`, implémentée pour retourner une liste spécifique d'opérations que l'utilisateur est autorisé à effectuer. La stratégie d'autorisation ajoute des revendications pour l'accès à l'opération particulière. Elle est utilisée ultérieurement par le <xref:System.ServiceModel.ServiceAuthorizationManager> pour exécuter des décisions relatives à la vérification de l'accès.

Une fois la <xref:System.IdentityModel.Policy.IAuthorizationPolicy> personnalisée implémentée, l'hôte de service doit être informé des stratégies d'autorisation à utiliser.

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Le client appelle avec succès les méthodes d'addition, de soustraction et de multiplication, et obtient le message « Accès refusé » lors de la tentative d'appel de la méthode de division. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.

## <a name="setup-batch-file"></a>Fichier de commandes d'installation

Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec les certificats pertinents pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur.

Les éléments suivants fournissent une brève vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée :

- Création du certificat de serveur

    Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser. La variable %SERVER_NAME% spécifie le nom du serveur. Modifiez cette variable pour spécifier votre propre nom de serveur. La valeur par défaut est localhost.

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Installation du certificat de serveur dans le magasin de certificats approuvé du client.

    Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- Création du certificat client

    Les lignes suivantes du fichier de commandes Setup.bat créent le certificat client à utiliser. La variable %USER_NAME% spécifie le nom du serveur. Cette valeur est « test1 » parce que c'est le nom que la `IAuthorizationPolicy` recherche. Si vous modifiez la valeur de %USER_NAME%, vous devez modifier la valeur correspondante dans la méthode `IAuthorizationPolicy.Evaluate`.

    Le certificat est stocké dans le magasin My (Personal) sous l'emplacement de magasin CurrentUser.

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- Installation du certificat client dans le magasin de certificats approuvés du serveur.

    Les lignes suivantes du fichier de commandes Setup.bat copient le certificat client dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système du serveur. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats du serveur avec le certificat client n'est pas requise.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple

1. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

2. Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions ci-dessous.

> [!NOTE]
> Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.

### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur

1. Ouvrez Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez *Setup. bat* à partir du dossier d’installation de l’exemple. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.

    > [!NOTE]
    > Le fichier de commandes Setup. bat est conçu pour être exécuté à partir de Invite de commandes développeur pour Visual Studio. La variable d’environnement PATH définie dans Invite de commandes développeur pour Visual Studio pointe vers le répertoire qui contient les exécutables requis par le script *Setup. bat* .

1. Lancez service. exe à partir de *service\bin*.

1. Lancez client. exe à partir de *\client\bin*. L'activité du client s'affiche sur son application de console.

Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs

1. Créez un répertoire sur l'ordinateur de service.

2. Copiez les fichiers programme du service à partir de *\service\bin* dans le répertoire de l’ordinateur de service. Copiez également les fichiers Setup.bat, Cleanup.bat, GetComputerName.vbs et ImportClientCert.bat sur l'ordinateur de service.

3. Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.

4. Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client. Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.

5. Sur le serveur, exécutez `setup.bat service` dans invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.

    `setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur, puis exporte le certificat de service dans un fichier nommé *service. cer*.

6. Modifiez *service. exe. config* pour refléter le nouveau nom de certificat (dans l' `findValue` attribut de [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur. Modifiez également le nom d’hôte **dans l'** \<service> / \<baseAddresses> élément de localhost en lui attribuant le nom complet de votre ordinateur de service.

7. Copiez le fichier *service. cer* du répertoire du service vers le répertoire du client sur l’ordinateur client.

8. Sur le client, exécutez `setup.bat client` dans invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.

    `setup.bat`L’exécution de avec l' `client` argument crée un certificat client nommé **Test1** et exporte le certificat client vers un fichier nommé *client. cer*.

9. Dans le fichier *client. exe. config* sur l’ordinateur client, modifiez la valeur d’adresse du point de terminaison afin qu’elle corresponde à la nouvelle adresse de votre service. Pour ce faire, remplacez **localhost** par le nom de domaine complet du serveur.

10. Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.

11. Sur le client, exécutez *ImportServiceCert. bat* dans invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.

    Cela importe le certificat de service à partir du fichier service. cer dans le magasin **CurrentUser-TrustedPeople** .

12. Sur le serveur, exécutez *ImportClientCert. bat* dans invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.

    Cela importe le certificat client du fichier client. cer dans le magasin **LocalMachine-TrustedPeople** .

13. Sur l'ordinateur serveur, lancez Service.exe à partir de la fenêtre d'invite de commandes.

14. Sur l'ordinateur client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.

    Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).

### <a name="clean-up-after-the-sample"></a>Nettoyer après l’exemple

Pour nettoyer après l’exemple, exécutez *Cleanup. bat* dans le dossier Samples lorsque vous avez terminé d’exécuter l’exemple. Cela supprime les certificats du serveur et du client du magasin de certificats.

> [!NOTE]
> Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs. Si vous avez exécuté des exemples WCF qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople. Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.
