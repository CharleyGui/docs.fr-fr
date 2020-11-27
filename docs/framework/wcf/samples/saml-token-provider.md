---
title: SAML Token Provider
ms.date: 03/30/2017
ms.assetid: eb16e5e2-4c8d-4f61-a479-9c965fcec80c
ms.openlocfilehash: 97c3c89a94882000c529bae77f1a4d707b242d7e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262656"
---
# <a name="saml-token-provider"></a><span data-ttu-id="a1e8a-102">SAML Token Provider</span><span class="sxs-lookup"><span data-stu-id="a1e8a-102">SAML Token Provider</span></span>

<span data-ttu-id="a1e8a-103">Cet exemple montre comment implémenter un fournisseur de jetons SAML client personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-103">This sample demonstrates how to implement a custom client SAML token provider.</span></span> <span data-ttu-id="a1e8a-104">Un fournisseur de jetons dans Windows Communication Foundation (WCF) est utilisé pour fournir des informations d’identification à l’infrastructure de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="a1e8a-105">En général, le fournisseur de jetons examine la cible et publie des informations d'identification appropriées afin que l'infrastructure de sécurité puisse sécuriser le message.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="a1e8a-106">WCF est fourni avec le fournisseur de jetons du gestionnaire d’informations d’identification par défaut.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="a1e8a-107">WCF est également fourni avec un fournisseur de jetons CardSpace.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="a1e8a-108">Les fournisseurs de jetons personnalisés sont utiles dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="a1e8a-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="a1e8a-109">si vous avez un magasin d'informations d'identification avec lequel ces fournisseurs de jetons ne peuvent pas fonctionner ;</span><span class="sxs-lookup"><span data-stu-id="a1e8a-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="a1e8a-110">Si vous souhaitez fournir votre propre mécanisme personnalisé pour transformer les informations d’identification à partir du moment où l’utilisateur fournit les détails lorsque l’infrastructure cliente WCF utilise les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="a1e8a-111">si vous générez un jeton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-111">If you are building a custom token.</span></span>

 <span data-ttu-id="a1e8a-112">Cet exemple montre comment générer un fournisseur de jetons personnalisé qui permet l’utilisation d’un jeton SAML obtenu en dehors de l’infrastructure cliente WCF.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-112">This sample shows how to build a custom token provider that allows a SAML token obtained from outside of the WCF client framework to be used.</span></span>

 <span data-ttu-id="a1e8a-113">En résumé, cet exemple montre :</span><span class="sxs-lookup"><span data-stu-id="a1e8a-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="a1e8a-114">la façon dont un client peut être configuré avec un fournisseur de jetons personnalisé ;</span><span class="sxs-lookup"><span data-stu-id="a1e8a-114">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="a1e8a-115">la façon dont un jeton SAML peut être transmis aux informations d'identification du client personnalisées ;</span><span class="sxs-lookup"><span data-stu-id="a1e8a-115">How a SAML token can be passed to the custom client credentials.</span></span>

- <span data-ttu-id="a1e8a-116">Comment le jeton SAML est fourni à l’infrastructure du client WCF.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-116">How the SAML token is provided to the WCF client framework.</span></span>

- <span data-ttu-id="a1e8a-117">la façon dont le serveur est authentifié auprès du client à l'aide du certificat X.509 du serveur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="a1e8a-118">Le service expose deux points de terminaison pour communiquer avec le service, défini à l’aide du fichier de configuration App.config. Chaque point de terminaison se compose d’une adresse, d’une liaison et d’un contrat.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-118">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="a1e8a-119">La liaison est configurée avec un `wsFederationHttpBinding` standard, qui utilise la sécurité des messages.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-119">The binding is configured with a standard `wsFederationHttpBinding`, which uses Message security.</span></span> <span data-ttu-id="a1e8a-120">Un point de terminaison attend une authentification du client à l'aide d'un jeton SAML qui utilise une clé de vérification symétrique tandis que l'autre attend une authentification du client avec un jeton SAML qui utilise une clé de vérification asymétrique.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-120">One endpoint expects the client to authenticate with a SAML token that uses a symmetric proof key while the other expects the client to authenticate with a SAML token that uses an asymmetric proof key.</span></span> <span data-ttu-id="a1e8a-121">Le service configure également le certificat de service à l'aide du comportement `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-121">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="a1e8a-122">Le comportement `serviceCredentials` permet de configurer un certificat de service.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-122">The `serviceCredentials` behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="a1e8a-123">Un certificat de service est utilisé par un client pour authentifier le service et fournir la protection des messages.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-123">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="a1e8a-124">La configuration suivante référence le certificat « localhost » installé pendant l'installation de l'exemple, comme décrit dans les instructions d'installation à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-124">The following configuration references the "localhost" certificate installed during the sample setup as described in the setup instructions at the end of this topic.</span></span> <span data-ttu-id="a1e8a-125">Le comportement `serviceCredentials` permet également de configurer des certificats approuvés pour la signature des jetons SAML.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-125">The `serviceCredentials` behavior also allows you to configure certificates that are trusted to sign SAML tokens.</span></span> <span data-ttu-id="a1e8a-126">La configuration suivante référence le certificat « Alice » installé au cours de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-126">The following configuration references the 'Alice' certificate installed during the sample.</span></span>

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

 <span data-ttu-id="a1e8a-127">Les étapes suivantes montrent comment développer un fournisseur de jetons SAML personnalisé et l’intégrer à WCF : infrastructure de sécurité :</span><span class="sxs-lookup"><span data-stu-id="a1e8a-127">The following steps show how to develop a custom SAML token provider and integrate it with WCF: security framework:</span></span>

1. <span data-ttu-id="a1e8a-128">Écrivez un fournisseur de jetons SAML personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-128">Write a custom SAML token provider.</span></span>

     <span data-ttu-id="a1e8a-129">L'exemple implémente un fournisseur de jetons SAML personnalisé qui retourne un jeton de sécurité selon une assertion SAML fournie au moment de la construction.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-129">The sample implements a custom SAML token provider that returns a security token based on a SAML assertion that is provided at construction time.</span></span>

     <span data-ttu-id="a1e8a-130">Pour effectuer cette tâche, le fournisseur de jetons personnalisé est dérivé de la classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider> et remplace la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-130">To perform this task, the custom token provider is derived from the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="a1e8a-131">Cette méthode crée et retourne un nouveau `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-131">This method creates and returns a new `SecurityToken`.</span></span>

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

2. <span data-ttu-id="a1e8a-132">Écrivez un gestionnaire de jetons de sécurité personnalisé.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-132">Write custom security token manager.</span></span>

     <span data-ttu-id="a1e8a-133">La classe <xref:System.IdentityModel.Selectors.SecurityTokenManager> permet de créer <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pour la classe particulière <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> qui lui est transmise dans la méthode `CreateSecurityTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-133">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> class is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="a1e8a-134">Le gestionnaire de jetons de sécurité permet également de créer des authentificateurs et des sérialiseurs de jeton, mais ceux-là ne sont pas traités dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-134">A security token manager is also used to create token authenticators and token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="a1e8a-135">Dans cet exemple, le gestionnaire de jetons de sécurité personnalisé hérite de la classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> et remplace la méthode `CreateSecurityTokenProvider` pour retourner le fournisseur de jetons SAML personnalisé lorsque les exigences du jeton transmis indiquent que le jeton SAML est demandé.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-135">In this sample the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom SAML token provider when the passed token requirements indicate that the SAML token is requested.</span></span> <span data-ttu-id="a1e8a-136">Si la classe d'informations d'identification du client (voir l'étape 3) n'a pas spécifié d'assertion, le gestionnaire de jetons de sécurité crée une instance appropriée.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-136">If the client credentials class (see step 3) has not specified an assertion, the security token manager creates an appropriate instance.</span></span>

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

3. <span data-ttu-id="a1e8a-137">Écrivez une information d'identification client personnalisée.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-137">Write a custom client credential.</span></span>

     <span data-ttu-id="a1e8a-138">La classe d'informations d'identification du client est utilisée pour représenter les informations d'identification qui sont configurées pour le proxy client et crée un gestionnaire de jetons de sécurité qui permet d'obtenir des authentificateurs, des fournisseurs et un sérialiseur de jeton.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-138">Client credentials class is used to represent the credentials that are configured for the client proxy and creates a security token manager that is used to obtain token authenticators, token providers and token serializer.</span></span>

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

4. <span data-ttu-id="a1e8a-139">Configurez le client pour qu'il utilise les informations d'identification du client personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-139">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="a1e8a-140">L'exemple supprime la classe des informations d'identification du client par défaut et fournit la classe des nouvelles informations d'identification ; le client peut ainsi utiliser les informations d'identification personnalisées.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-140">The sample deletes the default client credential class and supplies the new client credential class so the client can use the custom client credential.</span></span>

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

 <span data-ttu-id="a1e8a-141">Sur le service, les revendications associées à l'appelant sont affichées.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-141">On the service, the claims associated with the caller are displayed.</span></span> <span data-ttu-id="a1e8a-142">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-142">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="a1e8a-143">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-143">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="a1e8a-144">Fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="a1e8a-144">Setup Batch File</span></span>

 <span data-ttu-id="a1e8a-145">Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec le certificat approprié pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-145">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="a1e8a-146">Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-146">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="a1e8a-147">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-147">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="a1e8a-148">Création du certificat de serveur :</span><span class="sxs-lookup"><span data-stu-id="a1e8a-148">Creating the server certificate:</span></span>

     <span data-ttu-id="a1e8a-149">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-149">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="a1e8a-150">La variable `%SERVER_NAME%` spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-150">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="a1e8a-151">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-151">Change this variable to specify your own server name.</span></span> <span data-ttu-id="a1e8a-152">La valeur par défaut dans ce fichier de commandes est localhost.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-152">The default value in this batch file is localhost.</span></span>

     <span data-ttu-id="a1e8a-153">Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasins LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-153">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss My -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="a1e8a-154">Installation du certificat de serveur dans le magasin de certificats approuvés du client :</span><span class="sxs-lookup"><span data-stu-id="a1e8a-154">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="a1e8a-155">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-155">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a1e8a-156">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-156">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a1e8a-157">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-157">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r LocalMachine -s TrustedPeople
    ```

- <span data-ttu-id="a1e8a-158">Création du certificat d'émetteur :</span><span class="sxs-lookup"><span data-stu-id="a1e8a-158">Creating the issuer certificate.</span></span>

     <span data-ttu-id="a1e8a-159">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat d'émetteur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-159">The following lines from the Setup.bat batch file create the issuer certificate to be used.</span></span> <span data-ttu-id="a1e8a-160">La variable `%USER_NAME%` représente le nom de l'émetteur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-160">The `%USER_NAME%` variable specifies the issuer name.</span></span> <span data-ttu-id="a1e8a-161">Modifiez cette variable pour spécifier votre propre nom d'émetteur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-161">Change this variable to specify your own issuer name.</span></span> <span data-ttu-id="a1e8a-162">La valeur par défaut dans ce fichier de commandes est Alice.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-162">The default value in this batch file is Alice.</span></span>

     <span data-ttu-id="a1e8a-163">Le certificat est stocké dans le magasin My sous l'emplacement de magasins CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-163">The certificate is stored in My store under the CurrentUser store location.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr CurrentUser -ss My -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="a1e8a-164">Installation du certificat d'émetteur dans le magasin de certificats approuvés du serveur :</span><span class="sxs-lookup"><span data-stu-id="a1e8a-164">Installing the issuer certificate into the server's trusted certificate store.</span></span>

     <span data-ttu-id="a1e8a-165">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-165">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="a1e8a-166">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-166">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="a1e8a-167">Si un certificat est déjà associé au certificat racine approuvé du client, par exemple un certificat Microsoft, le remplissage du magasin de certificats du serveur avec le certificat de l'émetteur n'est pas obligatoire.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-167">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the server certificate store with the issuer certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="a1e8a-168">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="a1e8a-168">To set up and build the sample</span></span>

1. <span data-ttu-id="a1e8a-169">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a1e8a-169">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="a1e8a-170">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="a1e8a-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

> [!NOTE]
> <span data-ttu-id="a1e8a-171">Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-171">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="a1e8a-172">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="a1e8a-172">To run the sample on the same computer</span></span>

1. <span data-ttu-id="a1e8a-173">Exécutez Setup.bat à partir du dossier d’installation de l’exemple à l’aide d’une invite de commandes Visual Studio 2012 exécutée avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-173">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt run with administrator privileges.</span></span> <span data-ttu-id="a1e8a-174">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-174">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a1e8a-175">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-175">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="a1e8a-176">La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-176">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="a1e8a-177">Lancez Service.exe à partir de service\bin.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-177">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="a1e8a-178">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-178">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="a1e8a-179">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-179">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="a1e8a-180">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a1e8a-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="a1e8a-181">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="a1e8a-181">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="a1e8a-182">Créez un répertoire sur l'ordinateur de service pour les fichiers binaires du service.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-182">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="a1e8a-183">Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-183">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="a1e8a-184">Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-184">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="a1e8a-185">Le nom de sujet de votre certificat de serveur doit contenir le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-185">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="a1e8a-186">Le fichier Service.exe.config doit être mis à jour pour refléter ce nouveau nom de certificat.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-186">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="a1e8a-187">Vous pouvez créer le certificat de serveur en modifiant le fichier de commandes Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-187">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="a1e8a-188">Notez que le fichier setup.bat doit être exécuté dans une Invite de commandes développeur fenêtre pour Visual Studio ouverte avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-188">Note that the setup.bat file must be run in a Developer Command Prompt for Visual Studio window opened with administrator privileges.</span></span> <span data-ttu-id="a1e8a-189">Vous devez affecter à la variable `%SERVER_NAME%` le nom d'hôte complet de l'ordinateur utilisé pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-189">You must set the `%SERVER_NAME%` variable to the fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="a1e8a-190">Copiez le certificat de serveur dans le magasin CurrentUser-TrustedPeople du client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-190">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="a1e8a-191">Cette étape n'est pas nécessaire lorsque le certificat de serveur est publié par un émetteur de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-191">This step is not necessary when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="a1e8a-192">Dans le fichier Service.exe.config sur l'ordinateur de service, modifiez la valeur de l'adresse de base pour spécifier le nom de l'ordinateur complet au lieu de localhost.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-192">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="a1e8a-193">Sur l'ordinateur de service, exécutez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-193">On the service computer, run Service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="a1e8a-194">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-194">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="a1e8a-195">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-195">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="a1e8a-196">Sur l'ordinateur client, lancez `Client.exe` à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-196">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="a1e8a-197">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="a1e8a-197">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="a1e8a-198">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="a1e8a-198">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="a1e8a-199">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="a1e8a-199">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
