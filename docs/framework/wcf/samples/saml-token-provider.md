---
title: SAML Token Provider
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 4e371d518d7ef25152aba83fa00d79893397b07f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554421"
---
# <a name="saml-token-provider"></a>SAML Token Provider
Cet exemple montre comment implémenter un fournisseur de jetons SAML client personnalisé. Un fournisseur de jetons dans Windows Communication Foundation (WCF) est utilisé pour fournir des informations d’identification à l’infrastructure de sécurité. En général, le fournisseur de jetons examine la cible et publie des informations d'identification appropriées afin que l'infrastructure de sécurité puisse sécuriser le message. WCF est fourni avec le fournisseur de jetons du gestionnaire d’informations d’identification par défaut. WCF est également fourni avec un fournisseur de jetons CardSpace. Les fournisseurs de jetons personnalisés sont utiles dans les cas suivants :

- si vous avez un magasin d'informations d'identification avec lequel ces fournisseurs de jetons ne peuvent pas fonctionner ;

- Si vous souhaitez fournir votre propre mécanisme personnalisé pour transformer les informations d’identification à partir du moment où l’utilisateur fournit les détails lorsque l’infrastructure cliente WCF utilise les informations d’identification.

- si vous générez un jeton personnalisé.

 Cet exemple montre comment générer un fournisseur de jetons personnalisé qui permet l’utilisation d’un jeton SAML obtenu en dehors de l’infrastructure cliente WCF.

 En résumé, cet exemple montre :

- la façon dont un client peut être configuré avec un fournisseur de jetons personnalisé ;

- la façon dont un jeton SAML peut être transmis aux informations d'identification du client personnalisées ;

- Comment le jeton SAML est fourni à l’infrastructure du client WCF.

- la façon dont le serveur est authentifié auprès du client à l'aide du certificat X.509 du serveur.

 Le service expose deux points de terminaison pour communiquer avec le service, défini à l’aide du fichier de configuration App.config. Chaque point de terminaison se compose d’une adresse, d’une liaison et d’un contrat. La liaison est configurée avec un `wsFederationHttpBinding` standard, qui utilise la sécurité des messages. Un point de terminaison attend une authentification du client à l'aide d'un jeton SAML qui utilise une clé de vérification symétrique tandis que l'autre attend une authentification du client avec un jeton SAML qui utilise une clé de vérification asymétrique. Le service configure également le certificat de service à l'aide du comportement `serviceCredentials`. Le comportement `serviceCredentials` permet de configurer un certificat de service. Un certificat de service est utilisé par un client pour authentifier le service et fournir la protection des messages. La configuration suivante référence le certificat « localhost » installé pendant l'installation de l'exemple, comme décrit dans les instructions d'installation à la fin de cette rubrique. Le comportement `serviceCredentials` permet également de configurer des certificats approuvés pour la signature des jetons SAML. La configuration suivante référence le certificat « Alice » installé au cours de l'exemple.

```xml
<system.serviceModel>
 <services>
  <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
   <host>
    <baseAddresses>
     <!-- configure base address provided by host -->
     <add
  baseAddress="http://localhost:8000/servicemodelsamples/service/" />
    </baseAddresses>
   </host>
   <!-- use base address provided by host -->
   <!-- Endpoint that expect SAML tokens with Symmetric proof keys -->
   <endpoint address="calc/symm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
   <!-- Endpoint that expect SAML tokens with Asymmetric proof keys -->
   <endpoint address="calc/asymm"
             binding="wsFederationHttpBinding"
             bindingConfiguration="Binding2"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </service>
 </services>

 <bindings>
  <wsFederationHttpBinding>
   <!-- Binding that expect SAML tokens with Symmetric proof keys -->
   <binding name="Binding1">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="SymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
   <!-- Binding that expect SAML tokens with Asymmetric proof keys -->
   <binding name="Binding2">
    <security mode="Message">
     <message negotiateServiceCredential ="false"
              issuedKeyType="AsymmetricKey"
              issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1"  />
    </security>
   </binding>
  </wsFederationHttpBinding>
 </bindings>

 <behaviors>
  <serviceBehaviors>
   <behavior name="CalculatorServiceBehavior">
    <!--
    The serviceCredentials behavior allows one to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
    This configuration references the "localhost" certificate installed during the setup instructions.
    -->
    <serviceCredentials>
     <!-- Set allowUntrustedRsaIssuers to true to allow self-signed, asymmetric key based SAML tokens -->
     <issuedTokenAuthentication allowUntrustedRsaIssuers ="true" >
      <!-- Add Alice to the list of certs trusted to issue SAML tokens -->
      <knownCertificates>
       <add storeLocation="LocalMachine"
            storeName="TrustedPeople"
            x509FindType="FindBySubjectName"
            findValue="Alice"/>
      </knownCertificates>
     </issuedTokenAuthentication>
     <serviceCertificate storeLocation="LocalMachine"
                         storeName="My"
                         x509FindType="FindBySubjectName"
                         findValue="localhost"  />
    </serviceCredentials>
   </behavior>
  </serviceBehaviors>
 </behaviors>

</system.serviceModel>
```

 Les étapes suivantes montrent comment développer un fournisseur de jetons SAML personnalisé et l’intégrer à WCF : infrastructure de sécurité :

1. Écrivez un fournisseur de jetons SAML personnalisé.

     L'exemple implémente un fournisseur de jetons SAML personnalisé qui retourne un jeton de sécurité selon une assertion SAML fournie au moment de la construction.

     Pour effectuer cette tâche, le fournisseur de jetons personnalisé est dérivé de la classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider> et remplace la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>. Cette méthode crée et retourne un nouveau `SecurityToken`.

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
     // Create a SamlSecurityToken from the provided assertion
     SamlSecurityToken samlToken = new SamlSecurityToken(assertion);

     // Create a SecurityTokenSerializer that will be used to
     // serialize the SamlSecurityToken
     WSSecurityTokenSerializer ser = new WSSecurityTokenSerializer();
     // Create a memory stream to write the serialized token into
     // Use an initial size of 64Kb
     MemoryStream s = new MemoryStream(UInt16.MaxValue);

     // Create an XmlWriter over the stream
     XmlWriter xw = XmlWriter.Create(s);

     // Write the SamlSecurityToken into the stream
     ser.WriteToken(xw, samlToken);

     // Seek back to the beginning of the stream
     s.Seek(0, SeekOrigin.Begin);

     // Load the serialized token into a DOM
     XmlDocument dom = new XmlDocument();
     dom.Load(s);

     // Create a KeyIdentifierClause for the SamlSecurityToken
     SamlAssertionKeyIdentifierClause samlKeyIdentifierClause = samlToken.CreateKeyIdentifierClause<SamlAssertionKeyIdentifierClause>();

    // Return a GenericXmlToken from the XML for the
    // SamlSecurityToken, the proof token, the valid from and valid
    // until times from the assertion and the key identifier clause
    // created above
    return new GenericXmlSecurityToken(dom.DocumentElement, proofToken, assertion.Conditions.NotBefore, assertion.Conditions.NotOnOrAfter, samlKeyIdentifierClause, samlKeyIdentifierClause, null);
    }
    ```

2. Écrivez un gestionnaire de jetons de sécurité personnalisé.

     La classe <xref:System.IdentityModel.Selectors.SecurityTokenManager> permet de créer <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pour la classe particulière <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> qui lui est transmise dans la méthode `CreateSecurityTokenProvider`. Le gestionnaire de jetons de sécurité permet également de créer des authentificateurs et des sérialiseurs de jeton, mais ceux-là ne sont pas traités dans cet exemple. Dans cet exemple, le gestionnaire de jetons de sécurité personnalisé hérite de la classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> et remplace la méthode `CreateSecurityTokenProvider` pour retourner le fournisseur de jetons SAML personnalisé lorsque les exigences du jeton transmis indiquent que le jeton SAML est demandé. Si la classe d'informations d'identification du client (voir l'étape 3) n'a pas spécifié d'assertion, le gestionnaire de jetons de sécurité crée une instance appropriée.

    ```csharp
    public class SamlSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
     SamlClientCredentials samlClientCredentials;

     public SamlSecurityTokenManager ( SamlClientCredentials samlClientCredentials)
      : base(samlClientCredentials)
     {
      // Store the creating client credentials
      this.samlClientCredentials = samlClientCredentials;
     }

     public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )
     {
      // If token requirement matches SAML token return the
      // custom SAML token provider
      if (tokenRequirement.TokenType == SecurityTokenTypes.Saml ||
          tokenRequirement.TokenType == "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1")
      {
       // Retrieve the SAML assertion and proof token from the
       // client credentials
       SamlAssertion assertion = this.samlClientCredentials.Assertion;
       SecurityToken prooftoken = this.samlClientCredentials.ProofToken;

       // If either the assertion of proof token is null...
       if (assertion == null || prooftoken == null)
       {
        // ...get the SecurityBindingElement and then the
        // specified algorithm suite
        SecurityBindingElement sbe = null;
        SecurityAlgorithmSuite sas = null;

        if ( tokenRequirement.TryGetProperty<SecurityBindingElement> ( "http://schemas.microsoft.com/ws/2006/05/servicemodel/securitytokenrequirement/SecurityBindingElement", out sbe))
        {
         sas = sbe.DefaultAlgorithmSuite;
        }

        // If the token requirement is for a SymmetricKey based token..
        if (tokenRequirement.KeyType == SecurityKeyType.SymmetricKey)
        {
         // Create a symmetric proof token
         prooftoken = SamlUtilities.CreateSymmetricProofToken ( tokenRequirement.KeySize );
         // and a corresponding assertion based on the claims specified in the client credentials
         assertion = SamlUtilities.CreateSymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, new X509SecurityToken ( samlClientCredentials.ClientCertificate.Certificate ), new X509SecurityToken ( samlClientCredentials.ServiceCertificate.DefaultCertificate ), (BinarySecretSecurityToken)prooftoken, sas);
        }
        // otherwise...
        else
        {
         // Create an asymmetric proof token
         prooftoken = SamlUtilities.CreateAsymmetricProofToken();
         // and a corresponding assertion based on the claims
         // specified in the client credentials
         assertion = SamlUtilities.CreateAsymmetricKeyBasedAssertion ( this.samlClientCredentials.Claims, prooftoken, sas );
        }
       }

       // Create a SamlSecurityTokenProvider based on the assertion and proof token
       return new SamlSecurityTokenProvider(assertion, prooftoken);
      }
      // otherwise use base implementation
      else
      {
       return base.CreateSecurityTokenProvider(tokenRequirement);
      }
    }
    ```

3. Écrivez une information d'identification client personnalisée.

     La classe d'informations d'identification du client est utilisée pour représenter les informations d'identification qui sont configurées pour le proxy client et crée un gestionnaire de jetons de sécurité qui permet d'obtenir des authentificateurs, des fournisseurs et un sérialiseur de jeton.

    ```csharp
    public class SamlClientCredentials : ClientCredentials
    {
     ClaimSet claims;
     SamlAssertion assertion;
     SecurityToken proofToken;

     public SamlClientCredentials() : base()
     {
      // Set SupportInteractive to false to suppress Cardspace UI
      base.SupportInteractive = false;
     }

     protected SamlClientCredentials(SamlClientCredentials other) : base ( other )
     {
      // Just do reference copy given sample nature
      this.assertion = other.assertion;
      this.claims = other.claims;
      this.proofToken = other.proofToken;
     }

     public SamlAssertion Assertion { get { return assertion; } set { assertion = value; } }

     public SecurityToken ProofToken { get { return proofToken; } set { proofToken = value; } }
     public ClaimSet Claims { get { return claims; } set { claims = value; } }

     protected override ClientCredentials CloneCore()
     {
      return new SamlClientCredentials(this);
     }

     public override SecurityTokenManager CreateSecurityTokenManager()
     {
      // return custom security token manager
      return new SamlSecurityTokenManager(this);
     }
    }
    ```

4. Configurez le client pour qu'il utilise les informations d'identification du client personnalisées.

     L'exemple supprime la classe des informations d'identification du client par défaut et fournit la classe des nouvelles informations d'identification ; le client peut ainsi utiliser les informations d'identification personnalisées.

    ```csharp
    // Create new credentials class
    SamlClientCredentials samlCC = new SamlClientCredentials();

    // Set the client certificate. This is the cert that will be used to sign the SAML token in the symmetric proof key case
    samlCC.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "Alice");

    // Set the service certificate. This is the cert that will be used to encrypt the proof key in the symmetric proof key case
    samlCC.ServiceCertificate.SetDefaultCertificate(StoreLocation.CurrentUser, StoreName.TrustedPeople, X509FindType.FindBySubjectName, "localhost");

    // Create some claims to put in the SAML assertion
    IList<Claim> claims = new List<Claim>();
    claims.Add(Claim.CreateNameClaim(samlCC.ClientCertificate.Certificate.Subject));
    ClaimSet claimset = new DefaultClaimSet(claims);
    samlCC.Claims = claimset;

    // set new credentials
    client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
    client.ChannelFactory.Endpoint.Behaviors.Add(samlCC);
    ```

 Sur le service, les revendications associées à l'appelant sont affichées. Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client. Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.

## <a name="setup-batch-file"></a>Fichier de commandes d'installation
 Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec le certificat approprié pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur. Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.

 Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.

- Création du certificat de serveur :

     Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser. La variable `%SERVER_NAME%` spécifie le nom du serveur. Modifiez cette variable pour spécifier votre propre nom de serveur. La valeur par défaut dans ce fichier de commandes est localhost.

     Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasins LocalMachine.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- Installation du certificat de serveur dans le magasin de certificats approuvés du client :

     Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- Création du certificat d'émetteur :

     Les lignes suivantes du fichier de commandes Setup.bat créent le certificat d'émetteur à utiliser. La variable `%USER_NAME%` représente le nom de l'émetteur. Modifiez cette variable pour spécifier votre propre nom d'émetteur. La valeur par défaut dans ce fichier de commandes est Alice.

     Le certificat est stocké dans le magasin My sous l'emplacement de magasins CurrentUser.

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- Installation du certificat d'émetteur dans le magasin de certificats approuvés du serveur :

     Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client. Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client. Si un certificat est déjà associé au certificat racine approuvé du client, par exemple un certificat Microsoft, le remplissage du magasin de certificats du serveur avec le certificat de l'émetteur n'est pas obligatoire.

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a>Pour configurer et générer l'exemple

1. Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).

2. Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).

> [!NOTE]
> Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.

#### <a name="to-run-the-sample-on-the-same-computer"></a>Pour exécuter l'exemple sur le même ordinateur

1. Exécutez Setup.bat à partir du dossier d’installation de l’exemple à l’aide d’une invite de commandes Visual Studio 2012 exécutée avec des privilèges d’administrateur. Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.

    > [!NOTE]
    > Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012. La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.  
  
2. Lancez Service.exe à partir de service\bin.  
  
3. Lancez Client.exe à partir de \client\bin. L'activité du client s'affiche sur son application de console.  
  
4. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-run-the-sample-across-computers"></a>Pour exécuter l'exemple sur plusieurs ordinateurs  
  
1. Créez un répertoire sur l'ordinateur de service pour les fichiers binaires du service.  
  
2. Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service. Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.  
  
3. Le nom de sujet de votre certificat de serveur doit contenir le nom de domaine complet de l'ordinateur. Le fichier Service.exe.config doit être mis à jour pour refléter ce nouveau nom de certificat. Vous pouvez créer le certificat de serveur en modifiant le fichier de commandes Setup.bat. Notez que le fichier setup.bat doit être exécuté dans une Invite de commandes développeur fenêtre pour Visual Studio ouverte avec des privilèges d’administrateur. Vous devez affecter à la variable `%SERVER_NAME%` le nom d'hôte complet de l'ordinateur utilisé pour héberger le service.  
  
4. Copiez le certificat de serveur dans le magasin CurrentUser-TrustedPeople du client. Cette étape n'est pas nécessaire lorsque le certificat de serveur est publié par un émetteur de confiance du client.  
  
5. Dans le fichier Service.exe.config sur l'ordinateur de service, modifiez la valeur de l'adresse de base pour spécifier le nom de l'ordinateur complet au lieu de localhost.  
  
6. Sur l'ordinateur de service, exécutez Service.exe à partir d'une invite de commandes.  
  
7. Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.  
  
8. Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.  
  
9. Sur l'ordinateur client, lancez `Client.exe` à partir d'une invite de commandes.  
  
10. Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).  
  
#### <a name="to-clean-up-after-the-sample"></a>Pour procéder au nettoyage après exécution de l'exemple  
  
1. Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.
