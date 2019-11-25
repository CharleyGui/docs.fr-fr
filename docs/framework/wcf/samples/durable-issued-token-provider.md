---
title: Durable Issued Token Provider
ms.date: 03/30/2017
ms.assetid: 76fb27f5-8787-4b6a-bf4c-99b4be1d2e8b
ms.openlocfilehash: 52c4e99f8b2a834d7200c2d2c2383fbdb21bdd1a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73978324"
---
# <a name="durable-issued-token-provider"></a><span data-ttu-id="b8197-102">Durable Issued Token Provider</span><span class="sxs-lookup"><span data-stu-id="b8197-102">Durable Issued Token Provider</span></span>
<span data-ttu-id="b8197-103">Cet exemple montre comment implémenter un fournisseur de jetons émis client personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b8197-103">This sample demonstrates how to implement a custom client issued token provider.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="b8197-104">Discussion</span><span class="sxs-lookup"><span data-stu-id="b8197-104">Discussion</span></span>  
 <span data-ttu-id="b8197-105">Un fournisseur de jetons dans Windows Communication Foundation (WCF) est utilisé pour fournir des informations d’identification à l’infrastructure de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b8197-105">A token provider in Windows Communication Foundation (WCF) is used to supply credentials to the security infrastructure.</span></span> <span data-ttu-id="b8197-106">En général, le fournisseur de jetons examine la cible et publie des informations d'identification appropriées afin que l'infrastructure de sécurité puisse sécuriser le message.</span><span class="sxs-lookup"><span data-stu-id="b8197-106">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="b8197-107">WCF est fourni avec un fournisseur de jetons CardSpace.</span><span class="sxs-lookup"><span data-stu-id="b8197-107">WCF ships with a CardSpace token provider.</span></span> <span data-ttu-id="b8197-108">Les fournisseurs de jetons personnalisés sont utiles dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="b8197-108">Custom token providers are useful in the following cases:</span></span>  
  
- <span data-ttu-id="b8197-109">Si vous disposez d'un magasin d'informations d'identification avec lequel le fournisseur de jetons intégré ne peut pas fonctionner.</span><span class="sxs-lookup"><span data-stu-id="b8197-109">If you have a credential store that the built-in token provider cannot operate with.</span></span>  
  
- <span data-ttu-id="b8197-110">Si vous souhaitez fournir votre propre mécanisme personnalisé pour transformer les informations d’identification à partir du moment où l’utilisateur fournit les détails lorsque le client WCF utilise les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="b8197-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client uses the credentials.</span></span>  
  
- <span data-ttu-id="b8197-111">si vous générez un jeton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b8197-111">If you are building a custom token.</span></span>  
  
 <span data-ttu-id="b8197-112">Cet exemple montre comment générer un fournisseur de jetons personnalisé qui met en cache des jetons émis par un service d'émission de jeton de sécurité (STS, Security Token Service).</span><span class="sxs-lookup"><span data-stu-id="b8197-112">This sample shows how to build a custom token provider that caches tokens issued by a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="b8197-113">En résumé, cet exemple montre :</span><span class="sxs-lookup"><span data-stu-id="b8197-113">To summarize, this sample demonstrates the following:</span></span>  
  
- <span data-ttu-id="b8197-114">la façon dont un client peut être configuré avec un fournisseur de jetons personnalisé ;</span><span class="sxs-lookup"><span data-stu-id="b8197-114">How a client can be configured with a custom token provider.</span></span>  
  
- <span data-ttu-id="b8197-115">Comment les jetons émis peuvent être mis en cache et fournis au client WCF.</span><span class="sxs-lookup"><span data-stu-id="b8197-115">How issued tokens can be cached and provided to the WCF client.</span></span>  
  
- <span data-ttu-id="b8197-116">la façon dont le serveur est authentifié auprès du client à l'aide du certificat X.509 du serveur.</span><span class="sxs-lookup"><span data-stu-id="b8197-116">How the server is authenticated by the client using the server's X.509 certificate.</span></span>  
  
 <span data-ttu-id="b8197-117">Cet exemple comporte un programme de console client (Client.exe), un programme de console de service d'émission de jeton de sécurité (Securitytokenservice.exe) et un programme de console de service (Service.exe).</span><span class="sxs-lookup"><span data-stu-id="b8197-117">This sample consists of a client console program (Client.exe), a security token service console program (Securitytokenservice.exe) and a service console program (Service.exe).</span></span> <span data-ttu-id="b8197-118">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="b8197-118">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="b8197-119">Le contrat est défini par l'interface `ICalculator`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division.</span><span class="sxs-lookup"><span data-stu-id="b8197-119">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="b8197-120">Le client obtient un jeton de sécurité du STS et effectue des demandes synchrones au service pour une opération mathématique donnée, puis le service répond avec le résultat.</span><span class="sxs-lookup"><span data-stu-id="b8197-120">The client gets a security token from the Security Token Service (STS) and makes synchronous requests to the service for a given math operation and the service replies with the result.</span></span> <span data-ttu-id="b8197-121">L'activité du client est affichée dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="b8197-121">Client activity is visible in the console window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8197-122">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="b8197-122">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b8197-123">Cet exemple expose le contrat ICalculator à l’aide de la [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="b8197-123">This sample exposes the ICalculator contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="b8197-124">La configuration de cette liaison sur le client est présentée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b8197-124">The configuration of this binding on the client is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuer address="http://localhost:8000/sts/windows" 
                  binding="wsHttpBinding" />
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="b8197-125">Sur l'élément `security` de `wsFederationHttpBinding`, la valeur `mode` configure le mode de sécurité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b8197-125">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="b8197-126">Dans cet exemple, la sécurité de niveau message est utilisée ; c'est pourquoi l'élément `message` de `wsFederationHttpBinding` est spécifié dans l'élément `security` de `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="b8197-126">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="b8197-127">L’élément `issuer` de `wsFederationHttpBinding` dans l’élément `message` de `wsFederationHttpBinding` spécifie l’adresse et la liaison du STS qui publie un jeton de sécurité pour le client afin de permettre à ce dernier de s’authentifier auprès du service Calculator.</span><span class="sxs-lookup"><span data-stu-id="b8197-127">The `issuer` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and binding for the Security Token Service that issues a security token to the client so that the client can authenticate to the Calculator service.</span></span>  
  
 <span data-ttu-id="b8197-128">La configuration de cette liaison sur le service est présentée dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b8197-128">The configuration of this binding on the service is shown in the following code.</span></span>  
  
```xml  
<bindings>
  <wsFederationHttpBinding>
    <binding name="ServiceFed">
      <security mode="Message">
        <message issuedKeyType="SymmetricKey" 
                 issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">
          <issuerMetadata address="http://localhost:8000/sts/mex">
            <identity>
              <certificateReference storeLocation="CurrentUser" 
                                    storeName="TrustedPeople" 
                                    x509FindType="FindBySubjectDistinguishedName" 
                                    findValue="CN=STS" />
            </identity>
          </issuerMetadata>
        </message>
      </security>
    </binding>
  </wsFederationHttpBinding>
</bindings>  
```  
  
 <span data-ttu-id="b8197-129">Sur l'élément `security` de `wsFederationHttpBinding`, la valeur `mode` configure le mode de sécurité à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b8197-129">On the `security` element of `wsFederationHttpBinding`, the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="b8197-130">Dans cet exemple, la sécurité de niveau message est utilisée ; c'est pourquoi l'élément `message` de `wsFederationHttpBinding` est spécifié dans l'élément `security` de `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="b8197-130">In this sample, messages security is being used, which is why the `message` element of `wsFederationHttpBinding` is specified inside the `security` element of `wsFederationHttpBinding`.</span></span> <span data-ttu-id="b8197-131">L'élément `issuerMetadata` de `wsFederationHttpBinding` dans l'élément `message` de `wsFederationHttpBinding` spécifie l'adresse et l'identité du point de terminaison qui peut être utilisé afin de récupérer les métadonnées destinées au STS.</span><span class="sxs-lookup"><span data-stu-id="b8197-131">The `issuerMetadata` element of `wsFederationHttpBinding` inside the `message` element of `wsFederationHttpBinding` specifies the address and identity for an endpoint that can be used to retrieve metadata for the Security Token Service.</span></span>  
  
 <span data-ttu-id="b8197-132">Le comportement du service est présenté dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b8197-132">The behavior for the service is shown in the following code.</span></span>  
  
```xml  
<behavior name="ServiceBehavior">
  <serviceDebug includeExceptionDetailInFaults="true" />
  <serviceMetadata httpGetEnabled="true" />
  <serviceCredentials>
    <issuedTokenAuthentication>
      <knownCertificates>
        <add storeLocation="LocalMachine" 
              storeName="TrustedPeople" 
              x509FindType="FindBySubjectDistinguishedName" 
              findValue="CN=STS" />
      </knownCertificates>
    </issuedTokenAuthentication>
    <serviceCertificate storeLocation="LocalMachine" 
                        storeName="My" 
                        x509FindType="FindBySubjectDistinguishedName" 
                        findValue="CN=localhost" />
  </serviceCredentials>
</behavior>  
```  
  
 <span data-ttu-id="b8197-133">L'élément `issuedTokenAuthentication` dans l'élément `serviceCredentials` permet au service de spécifier des contraintes sur les jetons que les clients sont autorisés à présenter pendant l'authentification.</span><span class="sxs-lookup"><span data-stu-id="b8197-133">The `issuedTokenAuthentication` element inside the `serviceCredentials` element allows the service to specify constraints on the tokens it allows clients to present during authentication.</span></span> <span data-ttu-id="b8197-134">Cette configuration spécifie que les jetons signés par un certificat ayant CN=STS comme nom du sujet sont acceptés par le service.</span><span class="sxs-lookup"><span data-stu-id="b8197-134">This configuration specifies that tokens signed by a certificate whose Subject Name is CN=STS are accepted by the service.</span></span>  
  
 <span data-ttu-id="b8197-135">Le service d'émission de jeton de sécurité expose un point de terminaison unique à l'aide du wsHttpBinding standard.</span><span class="sxs-lookup"><span data-stu-id="b8197-135">The Security Token Service exposes a single endpoint using the standard wsHttpBinding.</span></span> <span data-ttu-id="b8197-136">Le service d'émission de jeton de sécurité répond pour demander des jetons aux clients et, à la condition que le client s'authentifie à l'aide d'un compte Windows, il émet un jeton qui contient le nom d'utilisateur du client comme revendication dans le jeton émis.</span><span class="sxs-lookup"><span data-stu-id="b8197-136">The Security Token Service responds to request from clients for tokens and, provided the client authenticates using a Windows account, issues a token that contains the client's user name as a claim in the issued token.</span></span> <span data-ttu-id="b8197-137">Dans le cadre de la création du jeton, le service d'émission de jeton de sécurité le signe à l'aide de la clé privée associée au certificat CN=STS.</span><span class="sxs-lookup"><span data-stu-id="b8197-137">As part of creating the token, the Security Token Service signs the token using the private key associated with the CN=STS certificate.</span></span> <span data-ttu-id="b8197-138">Par ailleurs, il crée une clé symétrique et la chiffre à l'aide de la clé publique associée au certificat CN=localhost.</span><span class="sxs-lookup"><span data-stu-id="b8197-138">In addition, it creates a symmetric key and encrypts it using the public key associated with the CN=localhost certificate.</span></span> <span data-ttu-id="b8197-139">Lors du retour du jeton au client, le service d'émission de jeton de sécurité retourne également la clé symétrique.</span><span class="sxs-lookup"><span data-stu-id="b8197-139">In returning the token to the client, the Security Token Service also returns the symmetric key.</span></span> <span data-ttu-id="b8197-140">Le client présente le jeton émis au service de calculatrice et prouve qu'il connaît la clé symétrique en signant le message à l'aide de celle-ci.</span><span class="sxs-lookup"><span data-stu-id="b8197-140">The client presents the issued token to the Calculator service, and proves that it knows the symmetric key by signing the message with that key.</span></span>  
  
## <a name="custom-client-credentials-and-token-provider"></a><span data-ttu-id="b8197-141">Informations d'identification client personnalisées et fournisseur de jetons personnalisé</span><span class="sxs-lookup"><span data-stu-id="b8197-141">Custom Client Credentials and Token Provider</span></span>  
 <span data-ttu-id="b8197-142">Les étapes suivantes indiquent comment développer un fournisseur de jetons personnalisé qui met en cache les jetons émis et les intègre à WCF : Security.</span><span class="sxs-lookup"><span data-stu-id="b8197-142">The following steps show how to develop a custom token provider that caches issued tokens and integrate it with WCF: security.</span></span>  
  
### <a name="to-develop-a-custom-token-provider"></a><span data-ttu-id="b8197-143">Pour développer un fournisseur de jetons personnalisé</span><span class="sxs-lookup"><span data-stu-id="b8197-143">To develop a custom token provider</span></span>  
  
1. <span data-ttu-id="b8197-144">Écrivez un fournisseur de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b8197-144">Write a custom token provider.</span></span>  
  
     <span data-ttu-id="b8197-145">L'exemple implémente un fournisseur de jetons personnalisé qui retourne un jeton de sécurité récupéré d'un cache.</span><span class="sxs-lookup"><span data-stu-id="b8197-145">The sample implements a custom token provider that returns a security token retrieved from a cache.</span></span>  
  
     <span data-ttu-id="b8197-146">Pour effectuer cette tâche, le fournisseur de jetons personnalisé dérive la classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider> et substitue la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8197-146">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%2A> method.</span></span> <span data-ttu-id="b8197-147">Cette méthode tente d'obtenir un jeton provenant du cache, ou si aucun jeton n'est trouvé dans le cache, elle en récupère un du fournisseur sous-jacent, puis le met en cache.</span><span class="sxs-lookup"><span data-stu-id="b8197-147">This method tries to get a token from the cache, or if a token cannot be found in the cache, retrieves a token from the underlying provider and then caches that token.</span></span> <span data-ttu-id="b8197-148">Dans les deux cas, la méthode retourne un `SecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="b8197-148">In both cases the method returns a `SecurityToken`.</span></span>  
  
    ```csharp  
    protected override SecurityToken GetTokenCore(TimeSpan timeout)  
    {  
      GenericXmlSecurityToken token;  
      if (!this.cache.TryGetToken(target, issuer, out token))  
      {  
        token = (GenericXmlSecurityToken) this.innerTokenProvider.GetToken(timeout);  
        this.cache.AddToken(token, target, issuer);  
      }  
      return token;  
    }  
    ```  
  
2. <span data-ttu-id="b8197-149">Écrivez un gestionnaire de jetons de sécurité personnalisé.</span><span class="sxs-lookup"><span data-stu-id="b8197-149">Write custom security token manager.</span></span>  
  
     <span data-ttu-id="b8197-150"><xref:System.IdentityModel.Selectors.SecurityTokenManager> permet de créer un <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pour un <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> spécifique qui lui est passé dans la méthode `CreateSecurityTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="b8197-150">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for a specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in the `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="b8197-151">Le gestionnaire de jetons de sécurité permet également de créer des authentificateurs et des sérialiseurs de jeton, mais ceux-là ne sont pas traités dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="b8197-151">Security token manager is also used to create token authenticators and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="b8197-152">Dans cet exemple, le gestionnaire de jetons de sécurité personnalisé hérite de la classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> et substitue la méthode `CreateSecurityTokenProvider` pour retourner le fournisseur de jetons personnalisé lorsque les exigences du jeton passé indiquent qu’un jeton émis est demandé.</span><span class="sxs-lookup"><span data-stu-id="b8197-152">In this sample, the custom security token manager inherits from the <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return the custom token provider when the passed token requirements indicate that an issued token is requested.</span></span>  
  
    ```csharp
    class DurableIssuedTokenClientCredentialsTokenManager :  
     ClientCredentialsSecurityTokenManager  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentialsTokenManager ( DurableIssuedTokenClientCredentials creds ): base(creds)  
      {  
        this.cache = creds.IssuedTokenCache;  
      }  
  
      public override SecurityTokenProvider CreateSecurityTokenProvider ( SecurityTokenRequirement tokenRequirement )  
      {  
        if (IsIssuedSecurityTokenRequirement(tokenRequirement))  
        {  
          return new DurableIssuedSecurityTokenProvider ((IssuedSecurityTokenProvider)base.CreateSecurityTokenProvider( tokenRequirement), this.cache);  
        }  
        else
        {  
          return base.CreateSecurityTokenProvider(tokenRequirement);  
        }  
      }  
    }  
    ```  
  
3. <span data-ttu-id="b8197-153">Écrivez une information d'identification client personnalisée.</span><span class="sxs-lookup"><span data-stu-id="b8197-153">Write a custom client credential.</span></span>  
  
     <span data-ttu-id="b8197-154">Une classe d'informations d'identification client permet de représenter les informations d'identification qui sont configurées pour le proxy client et crée le gestionnaire de jetons de sécurité utilisé pour obtenir des authentificateurs, des fournisseurs et des sérialiseurs de jeton.</span><span class="sxs-lookup"><span data-stu-id="b8197-154">A client credentials class is used to represent the credentials that are configured for the client proxy and creates the security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>  
  
    ```csharp
    public class DurableIssuedTokenClientCredentials : ClientCredentials  
    {  
      IssuedTokenCache cache;  
  
      public DurableIssuedTokenClientCredentials() : base()  
      {  
      }  
  
      DurableIssuedTokenClientCredentials ( DurableIssuedTokenClientCredentials other) : base(other)  
      {  
        this.cache = other.cache;  
      }  
  
      public IssuedTokenCache IssuedTokenCache  
      {  
        get  
        {  
          return this.cache;  
        }  
        set  
        {  
          this.cache = value;  
        }  
      }  
  
      protected override ClientCredentials CloneCore()  
      {  
        return new DurableIssuedTokenClientCredentials(this);  
      }  
  
      public override SecurityTokenManager CreateSecurityTokenManager()  
      {  
        return new DurableIssuedTokenClientCredentialsTokenManager ((DurableIssuedTokenClientCredentials)this.Clone());  
      }  
    }  
    ```  
  
4. <span data-ttu-id="b8197-155">Implémentez le cache du jeton.</span><span class="sxs-lookup"><span data-stu-id="b8197-155">Implement the token cache.</span></span> <span data-ttu-id="b8197-156">L'exemple d'implémentation utilise une classe de base abstraite par l'intermédiaire de laquelle les consommateurs d'un cache de jeton donné interagissent avec le cache.</span><span class="sxs-lookup"><span data-stu-id="b8197-156">The sample implementation uses an abstract base class through which consumers of a given token cache interact with the cache.</span></span>  
  
    ```csharp
    public abstract class IssuedTokenCache  
    {  
      public abstract void AddToken ( GenericXmlSecurityToken token, EndpointAddress target, EndpointAddress issuer);  
      public abstract bool TryGetToken(EndpointAddress target, EndpointAddress issuer, out GenericXmlSecurityToken cachedToken);  
    }  
    // Configure the client to use the custom client credential.  
    ```  
  
     <span data-ttu-id="b8197-157">Pour que le client puisse utiliser l'information d'identification client personnalisée, l'exemple supprime la classe d'informations d'identification client par défaut et fournit la nouvelle.</span><span class="sxs-lookup"><span data-stu-id="b8197-157">For the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>  
  
    ```csharp
    clientFactory.Endpoint.Behaviors.Remove<ClientCredentials>();  
    DurableIssuedTokenClientCredentials durableCreds = new DurableIssuedTokenClientCredentials();  
    durableCreds.IssuedTokenCache = cache;  
    durableCreds.ServiceCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.PeerOrChainTrust;  
    clientFactory.Endpoint.Behaviors.Add(durableCreds);  
    ```  
  
## <a name="running-the-sample"></a><span data-ttu-id="b8197-158">Exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="b8197-158">Running the sample</span></span>  
 <span data-ttu-id="b8197-159">Consultez les instructions suivantes pour exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="b8197-159">See the following instructions to run the sample.</span></span> <span data-ttu-id="b8197-160">Lorsque vous exécutez l'exemple, la demande de jeton de sécurité s'affiche dans la fenêtre de console du service d'émission de jeton de sécurité.</span><span class="sxs-lookup"><span data-stu-id="b8197-160">When you run the sample, the request for the security token is shown in the Security Token Service console window.</span></span> <span data-ttu-id="b8197-161">Les demandes et réponses d'opération s'affichent dans les fenêtres de console du client et du service.</span><span class="sxs-lookup"><span data-stu-id="b8197-161">The operation requests and responses are displayed in the client and service console windows.</span></span> <span data-ttu-id="b8197-162">Appuyez sur ENTER dans l'une ou l'autre de ces fenêtres pour arrêter l'application leur correspondant.</span><span class="sxs-lookup"><span data-stu-id="b8197-162">Press ENTER in any of the console windows to shut down the application.</span></span>  
  
## <a name="the-setupcmd-batch-file"></a><span data-ttu-id="b8197-163">Fichier de commandes Setup.cmd</span><span class="sxs-lookup"><span data-stu-id="b8197-163">The Setup.cmd Batch File</span></span>  
 <span data-ttu-id="b8197-164">Le fichier de commandes Setup.cmd inclus avec cet exemple vous permet de configurer le serveur et le service d'émission de jeton de sécurité avec les certificats appropriés pour exécuter une application auto-hébergée.</span><span class="sxs-lookup"><span data-stu-id="b8197-164">The Setup.cmd batch file included with this sample allows you to configure the server and security token service with relevant certificates to run a self-hosted application.</span></span> <span data-ttu-id="b8197-165">Il crée deux certificats dans le magasin de certificats CurrentUser/TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="b8197-165">The batch file creates two certificates both in the CurrentUser/TrustedPeople certificate store.</span></span> <span data-ttu-id="b8197-166">Le nom du sujet du premier certificat est CN=STS. Ce certificat est utilisé par le service d'émission de jeton de sécurité pour signer les jetons de sécurité qu'il émet au client.</span><span class="sxs-lookup"><span data-stu-id="b8197-166">The first certificate has a subject name of CN=STS and is used by the Security Token Service to sign the security tokens that it issues to the client.</span></span> <span data-ttu-id="b8197-167">Le deuxième a le nom du sujet CN=localhost et est utilisé par le service d'émission de jeton de sécurité pour chiffrer un secret de sorte que le service puisse le déchiffrer.</span><span class="sxs-lookup"><span data-stu-id="b8197-167">The second certificate has a subject name of CN=localhost and is used by the Security Token Service to encrypt a secret so that the service can decrypt it.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b8197-168">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="b8197-168">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b8197-169">Exécutez le fichier Setup.cmd pour créer les certificats requis.</span><span class="sxs-lookup"><span data-stu-id="b8197-169">Run the Setup.cmd file to create the required certificates.</span></span>  
  
2. <span data-ttu-id="b8197-170">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b8197-170">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span> <span data-ttu-id="b8197-171">Assurez-vous que tous les projets de la solution sont générés (Shared, RSTRSTR, Service, SecurityTokenService et Client).</span><span class="sxs-lookup"><span data-stu-id="b8197-171">Ensure that all the projects in the solution are built (Shared, RSTRSTR, Service, SecurityTokenService, and Client).</span></span>  
  
3. <span data-ttu-id="b8197-172">Veillez à ce que Service.exe et SecurityTokenService.exe s'exécutent tous deux avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="b8197-172">Ensure that Service.exe and SecurityTokenService.exe are both running with administrator privileges.</span></span>  
  
4. <span data-ttu-id="b8197-173">Exécutez client.exe.</span><span class="sxs-lookup"><span data-stu-id="b8197-173">Run Client.exe.</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="b8197-174">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="b8197-174">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="b8197-175">Exécutez Cleanup.cmd dans le dossier d’exemples après avoir exécuté l’exemple.</span><span class="sxs-lookup"><span data-stu-id="b8197-175">Run Cleanup.cmd in the samples folder once you have finished running the sample.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b8197-176">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b8197-176">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b8197-177">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="b8197-177">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="b8197-178">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b8197-178">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b8197-179">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="b8197-179">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\DurableIssuedTokenProvider`  
