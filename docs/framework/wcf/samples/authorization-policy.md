---
title: Authorization Policy
ms.date: 03/30/2017
ms.assetid: 1db325ec-85be-47d0-8b6e-3ba2fdf3dda0
ms.openlocfilehash: a789faae1f6224512f9a8a9ab084c8a82e4a2b87
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553660"
---
# <a name="authorization-policy"></a><span data-ttu-id="b83cc-102">Authorization Policy</span><span class="sxs-lookup"><span data-stu-id="b83cc-102">Authorization Policy</span></span>

<span data-ttu-id="b83cc-103">Cet exemple montre comment implémenter une stratégie d'autorisation de revendication personnalisée et un gestionnaire d'autorisations de service personnalisé associé.</span><span class="sxs-lookup"><span data-stu-id="b83cc-103">This sample demonstrates how to implement a custom claim authorization policy and an associated custom service authorization manager.</span></span> <span data-ttu-id="b83cc-104">Cela s'avère utile lorsque le service procède à des vérifications d'accès basées sur des revendications sur des opérations de service et, avant d'effectuer ces vérifications, accorde certains droits à l'appelant.</span><span class="sxs-lookup"><span data-stu-id="b83cc-104">This is useful when the service makes claim-based access checks to service operations and prior to the access checks, grants the caller certain rights.</span></span> <span data-ttu-id="b83cc-105">Cet exemple illustre à la fois le processus d'ajout de revendications ainsi que le processus de vérification de l'accès en fonction de l'ensemble de revendications finalisé.</span><span class="sxs-lookup"><span data-stu-id="b83cc-105">This sample shows both the process of adding claims as well as the process for doing an access check against the finalized set of claims.</span></span> <span data-ttu-id="b83cc-106">Tous les messages d'application échangés entre le client et le serveur sont signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="b83cc-106">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="b83cc-107">Par défaut, avec la liaison `wsHttpBinding`, un nom d’utilisateur et un mot de passe fournis par le client sont utilisés pour l’ouverture de session d’un compte Windows NT valide.</span><span class="sxs-lookup"><span data-stu-id="b83cc-107">By default with the `wsHttpBinding` binding, a username and password supplied by the client are used to logon to a valid Windows NT account.</span></span> <span data-ttu-id="b83cc-108">Cet exemple montre comment utiliser un <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> personnalisé pour authentifier le client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-108">This sample demonstrates how to utilize a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to authenticate the client.</span></span> <span data-ttu-id="b83cc-109">De plus, cet exemple montre comment le client s'authentifie auprès du service à l'aide d'un certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="b83cc-109">In addition this sample shows the client authenticating to the service using an X.509 certificate.</span></span> <span data-ttu-id="b83cc-110">Cet exemple montre une implémentation de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> et <xref:System.ServiceModel.ServiceAuthorizationManager>, qui accordent à des utilisateurs spécifiques l'accès à des méthodes spécifiques du service.</span><span class="sxs-lookup"><span data-stu-id="b83cc-110">This sample shows an implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> and <xref:System.ServiceModel.ServiceAuthorizationManager>, which between them grant access to specific methods of the service for specific users.</span></span> <span data-ttu-id="b83cc-111">Cet exemple est basé sur le [nom d’utilisateur de sécurité du message](message-security-user-name.md), mais montre comment effectuer une transformation de revendication avant l' <xref:System.ServiceModel.ServiceAuthorizationManager> appel de.</span><span class="sxs-lookup"><span data-stu-id="b83cc-111">This sample is based on the [Message Security User Name](message-security-user-name.md), but demonstrates how to perform a claim transformation prior to the <xref:System.ServiceModel.ServiceAuthorizationManager> being called.</span></span>

> [!NOTE]
> <span data-ttu-id="b83cc-112">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="b83cc-112">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="b83cc-113">En résumé, cet exemple montre comment :</span><span class="sxs-lookup"><span data-stu-id="b83cc-113">In summary, this sample demonstrates how:</span></span>

- <span data-ttu-id="b83cc-114">Le client peut être authentifié à l'aide d'un nom d'utilisateur et d'un mot de passe ;</span><span class="sxs-lookup"><span data-stu-id="b83cc-114">The client can be authenticated using a user name-password.</span></span>

- <span data-ttu-id="b83cc-115">Le client peut être authentifié à l'aide d'un certificat X.509 ;</span><span class="sxs-lookup"><span data-stu-id="b83cc-115">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="b83cc-116">Le serveur valide les informations d'identification du client en fonction d'un validateur `UsernamePassword` personnalisé ;</span><span class="sxs-lookup"><span data-stu-id="b83cc-116">The server validates the client credentials against a custom `UsernamePassword` validator.</span></span>

- <span data-ttu-id="b83cc-117">Le serveur est authentifié à l'aide du certificat X.509 du serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-117">The server is authenticated using the server's X.509 certificate.</span></span>

- <span data-ttu-id="b83cc-118">Le serveur peut utiliser <xref:System.ServiceModel.ServiceAuthorizationManager> pour contrôler l'accès à certaines méthodes dans le service ;</span><span class="sxs-lookup"><span data-stu-id="b83cc-118">The server can use <xref:System.ServiceModel.ServiceAuthorizationManager> to control access to certain methods in the service.</span></span>

- <span data-ttu-id="b83cc-119">Implémenter une interface <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span><span class="sxs-lookup"><span data-stu-id="b83cc-119">How to implement <xref:System.IdentityModel.Policy.IAuthorizationPolicy>.</span></span>

<span data-ttu-id="b83cc-120">Le service expose deux points de terminaison pour communiquer avec le service, défini à l’aide du fichier de configuration App.config. Chaque point de terminaison se compose d’une adresse, d’une liaison et d’un contrat.</span><span class="sxs-lookup"><span data-stu-id="b83cc-120">The service exposes two endpoints for communicating with the service, defined using the configuration file App.config. Each endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="b83cc-121">Une liaison est configurée avec une liaison `wsHttpBinding` standard qui utilise WS-Security et l’authentification du nom d’utilisateur du client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-121">One binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client username authentication.</span></span> <span data-ttu-id="b83cc-122">L'autre liaison est configurée avec une liaison `wsHttpBinding` standard qui utilise WS-Security et l'authentification du certificat du client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-122">The other binding is configured with a standard `wsHttpBinding` binding that uses WS-Security and client certificate authentication.</span></span> <span data-ttu-id="b83cc-123">[\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)Spécifie que les informations d’identification de l’utilisateur doivent être utilisées pour l’authentification du service.</span><span class="sxs-lookup"><span data-stu-id="b83cc-123">The [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="b83cc-124">Le certificat de serveur doit contenir la même valeur pour la `SubjectName` propriété que l' `findValue` attribut dans [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="b83cc-124">The server certificate must contain the same value for the `SubjectName` property as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

<span data-ttu-id="b83cc-125">Chaque configuration de point de terminaison de client se compose d'un nom de configuration, d'une adresse absolue pour le point de terminaison de service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="b83cc-125">Each client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="b83cc-126">La liaison client est configurée avec le mode de sécurité approprié, tel que spécifié dans ce cas dans le [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) et `clientCredentialType` comme spécifié dans le [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="b83cc-126">The client binding is configured with the appropriate security mode as specified in this case in the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) and `clientCredentialType` as specified in the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md).</span></span>

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

<span data-ttu-id="b83cc-127">Pour le point de terminaison basé sur nom de l'utilisateur , l'implémentation cliente définit le nom d'utilisateur et le mot de passe à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b83cc-127">For the user name-based endpoint, the client implementation sets the user name and password to use.</span></span>

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

<span data-ttu-id="b83cc-128">Pour le point de terminaison basé sur certificat, l'implémentation cliente définit le certificat client à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b83cc-128">For the certificate-based endpoint, the client implementation sets the client certificate to use.</span></span>

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

<span data-ttu-id="b83cc-129">Cet exemple utilise un <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> personnalisé pour valider les noms d'utilisateur et les mots de passe.</span><span class="sxs-lookup"><span data-stu-id="b83cc-129">This sample uses a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> to validate user names and passwords.</span></span> <span data-ttu-id="b83cc-130">L'exemple implémente `MyCustomUserNamePasswordValidator`, dérivé de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="b83cc-130">The sample implements `MyCustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="b83cc-131">Pour plus d'informations, consultez la documentation relative au <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="b83cc-131">See the documentation about <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="b83cc-132">Pour les besoins de la démonstration de l'intégration avec le <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, cet exemple de validateur personnalisé implémente la méthode <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> pour accepter des paires de nom d'utilisateur/mot de passe où le nom d'utilisateur correspond au mot de passe comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="b83cc-132">For the purposes of demonstrating the integration with the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>, this custom validator sample implements the <xref:System.IdentityModel.Selectors.UserNamePasswordValidator.Validate%2A> method to accept user name/password pairs where the user name matches the password as shown in the following code.</span></span>

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

<span data-ttu-id="b83cc-133">Une fois que le validateur est implémenté dans le code de service, l'hôte de service doit être informé de l'instance de validateur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b83cc-133">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="b83cc-134">Pour ce faire, utilisez le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b83cc-134">This is done using the following code:</span></span>

```csharp
Servicehost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials.UserNameAuthentication.CustomUserNamePasswordValidator = new MyCustomUserNamePasswordValidatorProvider();
```

<span data-ttu-id="b83cc-135">Vous pouvez aussi faire la même chose dans la configuration :</span><span class="sxs-lookup"><span data-stu-id="b83cc-135">Or you can do the same thing in configuration:</span></span>

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

<span data-ttu-id="b83cc-136">Windows Communication Foundation (WCF) fournit un modèle riche basé sur les revendications pour effectuer des vérifications d’accès.</span><span class="sxs-lookup"><span data-stu-id="b83cc-136">Windows Communication Foundation (WCF) provides a rich claims-based model for performing access checks.</span></span> <span data-ttu-id="b83cc-137">L’objet <xref:System.ServiceModel.ServiceAuthorizationManager> est utilisé pour effectuer la vérification d’accès et détermine si les revendications associées au client répondent aux exigences nécessaires pour accéder à la méthode de service.</span><span class="sxs-lookup"><span data-stu-id="b83cc-137">The <xref:System.ServiceModel.ServiceAuthorizationManager> object is used to perform the access check and determine whether the claims associated with the client satisfy the requirements necessary to access the service method.</span></span>

<span data-ttu-id="b83cc-138">À des fins de démonstration, cet exemple montre une implémentation de <xref:System.ServiceModel.ServiceAuthorizationManager> qui implémente la <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> méthode pour permettre à l’utilisateur d’accéder aux méthodes en fonction des revendications de type `http://example.com/claims/allowedoperation` dont la valeur est l’URI d’action de l’opération qui est autorisée à être appelée.</span><span class="sxs-lookup"><span data-stu-id="b83cc-138">For the purposes of demonstration, this sample shows an implementation of <xref:System.ServiceModel.ServiceAuthorizationManager> that implements the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> method to allow a user's access to methods based on claims of type `http://example.com/claims/allowedoperation` whose value is the Action URI of the operation that is allowed to be called.</span></span>

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

<span data-ttu-id="b83cc-139">Une fois que le <xref:System.ServiceModel.ServiceAuthorizationManager> personnalisé est implémenté, l'hôte de service doit être informé du <xref:System.ServiceModel.ServiceAuthorizationManager> à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b83cc-139">Once the custom <xref:System.ServiceModel.ServiceAuthorizationManager> is implemented, the service host must be informed about the <xref:System.ServiceModel.ServiceAuthorizationManager> to use.</span></span> <span data-ttu-id="b83cc-140">Cela est illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="b83cc-140">This is done as shown in the following code.</span></span>

```xml
<behavior>
    ...
    <serviceAuthorization serviceAuthorizationManagerType="Microsoft.ServiceModel.Samples.MyServiceAuthorizationManager, service">
        ...
    </serviceAuthorization>
</behavior>
```

<span data-ttu-id="b83cc-141">La méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy> principale à implémenter est la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29>.</span><span class="sxs-lookup"><span data-stu-id="b83cc-141">The primary <xref:System.IdentityModel.Policy.IAuthorizationPolicy> method to implement is the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method.</span></span>

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

<span data-ttu-id="b83cc-142">Le code précédent montre comment la méthode <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> vérifie qu'aucune nouvelle revendication n'a été ajoutée qui affecte le traitement et ajoute des revendications spécifiques.</span><span class="sxs-lookup"><span data-stu-id="b83cc-142">The previous code shows how the <xref:System.IdentityModel.Policy.IAuthorizationPolicy.Evaluate%28System.IdentityModel.Policy.EvaluationContext%2CSystem.Object%40%29> method checks that no new claims have been added that affect the processing and adds specific claims.</span></span> <span data-ttu-id="b83cc-143">Les revendications autorisées sont obtenues de la méthode `GetAllowedOpList`, implémentée pour retourner une liste spécifique d'opérations que l'utilisateur est autorisé à effectuer.</span><span class="sxs-lookup"><span data-stu-id="b83cc-143">The claims that are allowed are obtained from the `GetAllowedOpList` method, which is implemented to return a specific list of operations that the user is allowed to perform.</span></span> <span data-ttu-id="b83cc-144">La stratégie d'autorisation ajoute des revendications pour l'accès à l'opération particulière.</span><span class="sxs-lookup"><span data-stu-id="b83cc-144">The authorization policy adds claims for accessing the particular operation.</span></span> <span data-ttu-id="b83cc-145">Elle est utilisée ultérieurement par le <xref:System.ServiceModel.ServiceAuthorizationManager> pour exécuter des décisions relatives à la vérification de l'accès.</span><span class="sxs-lookup"><span data-stu-id="b83cc-145">This is later used by the <xref:System.ServiceModel.ServiceAuthorizationManager> to perform access check decisions.</span></span>

<span data-ttu-id="b83cc-146">Une fois la <xref:System.IdentityModel.Policy.IAuthorizationPolicy> personnalisée implémentée, l'hôte de service doit être informé des stratégies d'autorisation à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b83cc-146">Once the custom <xref:System.IdentityModel.Policy.IAuthorizationPolicy> is implemented, the service host must be informed about the authorization policies to use.</span></span>

```xml
<serviceAuthorization>
       <authorizationPolicies>
            <add policyType='Microsoft.ServiceModel.Samples.CustomAuthorizationPolicy.MyAuthorizationPolicy, PolicyLibrary' />
       </authorizationPolicies>
</serviceAuthorization>
```

<span data-ttu-id="b83cc-147">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-147">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b83cc-148">Le client appelle avec succès les méthodes d'addition, de soustraction et de multiplication, et obtient le message « Accès refusé » lors de la tentative d'appel de la méthode de division.</span><span class="sxs-lookup"><span data-stu-id="b83cc-148">The client successfully calls the Add, Subtract and Multiple methods and gets an "Access is denied" message when trying to call the Divide method.</span></span> <span data-ttu-id="b83cc-149">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="b83cc-149">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="b83cc-150">Fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="b83cc-150">Setup Batch File</span></span>

<span data-ttu-id="b83cc-151">Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec les certificats pertinents pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-151">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span>

<span data-ttu-id="b83cc-152">Les éléments suivants fournissent une brève vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée :</span><span class="sxs-lookup"><span data-stu-id="b83cc-152">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="b83cc-153">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="b83cc-153">Creating the server certificate.</span></span>

    <span data-ttu-id="b83cc-154">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b83cc-154">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="b83cc-155">La variable %SERVER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-155">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="b83cc-156">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-156">Change this variable to specify your own server name.</span></span> <span data-ttu-id="b83cc-157">La valeur par défaut est localhost.</span><span class="sxs-lookup"><span data-stu-id="b83cc-157">The default value is localhost.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="b83cc-158">Installation du certificat de serveur dans le magasin de certificats approuvé du client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-158">Installing the server certificate into client's trusted certificate store.</span></span>

    <span data-ttu-id="b83cc-159">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-159">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="b83cc-160">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-160">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="b83cc-161">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="b83cc-161">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="b83cc-162">Création du certificat client</span><span class="sxs-lookup"><span data-stu-id="b83cc-162">Creating the client certificate.</span></span>

    <span data-ttu-id="b83cc-163">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat client à utiliser.</span><span class="sxs-lookup"><span data-stu-id="b83cc-163">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="b83cc-164">La variable %USER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-164">The %USER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="b83cc-165">Cette valeur est « test1 » parce que c'est le nom que la `IAuthorizationPolicy` recherche.</span><span class="sxs-lookup"><span data-stu-id="b83cc-165">This value is set to "test1" because this is the name the `IAuthorizationPolicy` looks for.</span></span> <span data-ttu-id="b83cc-166">Si vous modifiez la valeur de %USER_NAME%, vous devez modifier la valeur correspondante dans la méthode `IAuthorizationPolicy.Evaluate`.</span><span class="sxs-lookup"><span data-stu-id="b83cc-166">If you change the value of %USER_NAME% you must change the corresponding value in the `IAuthorizationPolicy.Evaluate` method.</span></span>

    <span data-ttu-id="b83cc-167">Le certificat est stocké dans le magasin My (Personal) sous l'emplacement de magasin CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="b83cc-167">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bat
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="b83cc-168">Installation du certificat client dans le magasin de certificats approuvés du serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-168">Installing the client certificate into server's trusted certificate store.</span></span>

    <span data-ttu-id="b83cc-169">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat client dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-169">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="b83cc-170">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système du serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-170">This step is required because certificates that are generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="b83cc-171">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats du serveur avec le certificat client n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="b83cc-171">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```

### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="b83cc-172">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="b83cc-172">To set up and build the sample</span></span>

1. <span data-ttu-id="b83cc-173">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b83cc-173">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="b83cc-174">Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="b83cc-174">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

> [!NOTE]
> <span data-ttu-id="b83cc-175">Si vous utilisez Svcutil.exe pour régénérer la configuration pour cet exemple, assurez-vous de modifier le nom du point de terminaison dans la configuration client afin qu'il corresponde au code client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-175">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="b83cc-176">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="b83cc-176">To run the sample on the same computer</span></span>

1. <span data-ttu-id="b83cc-177">Ouvrez Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez *Setup.bat* à partir du dossier d’installation de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="b83cc-177">Open Developer Command Prompt for Visual Studio with administrator privileges and run *Setup.bat* from the sample install folder.</span></span> <span data-ttu-id="b83cc-178">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="b83cc-178">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="b83cc-179">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir de Invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b83cc-179">The Setup.bat batch file is designed to be run from Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="b83cc-180">La variable d’environnement PATH définie dans Invite de commandes développeur pour Visual Studio pointe vers le répertoire qui contient les exécutables requis par le script *Setup.bat* .</span><span class="sxs-lookup"><span data-stu-id="b83cc-180">The PATH environment variable set within Developer Command Prompt for Visual Studio points to the directory that contains executables required by the *Setup.bat* script.</span></span>

1. <span data-ttu-id="b83cc-181">Lancez Service.exe à partir de *service\bin*.</span><span class="sxs-lookup"><span data-stu-id="b83cc-181">Launch Service.exe from *service\bin*.</span></span>

1. <span data-ttu-id="b83cc-182">Lancez Client.exe à partir de *\client\bin*.</span><span class="sxs-lookup"><span data-stu-id="b83cc-182">Launch Client.exe from *\client\bin*.</span></span> <span data-ttu-id="b83cc-183">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="b83cc-183">Client activity is displayed on the client console application.</span></span>

<span data-ttu-id="b83cc-184">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="b83cc-184">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="b83cc-185">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="b83cc-185">To run the sample across computers</span></span>

1. <span data-ttu-id="b83cc-186">Créez un répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="b83cc-186">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="b83cc-187">Copiez les fichiers programme du service à partir de *\service\bin* dans le répertoire de l’ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="b83cc-187">Copy the service program files from *\service\bin* to the directory on the service computer.</span></span> <span data-ttu-id="b83cc-188">Copiez également les fichiers Setup.bat, Cleanup.bat, GetComputerName.vbs et ImportClientCert.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="b83cc-188">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="b83cc-189">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-189">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="b83cc-190">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-190">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="b83cc-191">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-191">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="b83cc-192">Sur le serveur, exécutez `setup.bat service` dans invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-192">On the server, run `setup.bat service` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="b83cc-193">`setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur, puis exporte le certificat de service dans un fichier nommé *service. cer*.</span><span class="sxs-lookup"><span data-stu-id="b83cc-193">Running `setup.bat` with the `service` argument creates a service certificate with the fully qualified domain name of the computer, and exports the service certificate to a file named *Service.cer*.</span></span>

6. <span data-ttu-id="b83cc-194">Modifiez *Service.exe.config* pour refléter le nouveau nom de certificat (dans l' `findValue` attribut dans [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-194">Edit *Service.exe.config* to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully qualified domain name of the computer.</span></span> <span data-ttu-id="b83cc-195">Modifiez également le nom d’hôte **dans l'** \<service> / \<baseAddresses> élément de localhost en lui attribuant le nom complet de votre ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="b83cc-195">Also change the **computername** in the \<service>/\<baseAddresses> element from localhost to the fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="b83cc-196">Copiez le fichier *service. cer* du répertoire du service vers le répertoire du client sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="b83cc-196">Copy the *Service.cer* file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="b83cc-197">Sur le client, exécutez `setup.bat client` dans invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-197">On the client, run `setup.bat client` in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="b83cc-198">`setup.bat`L’exécution de avec l' `client` argument crée un certificat client nommé **Test1** et exporte le certificat client vers un fichier nommé *client. cer*.</span><span class="sxs-lookup"><span data-stu-id="b83cc-198">Running `setup.bat` with the `client` argument creates a client certificate named **test1** and exports the client certificate to a file named *Client.cer*.</span></span>

9. <span data-ttu-id="b83cc-199">Dans le fichier *Client.exe.config* sur l’ordinateur client, modifiez la valeur adresse du point de terminaison afin qu’elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="b83cc-199">In the *Client.exe.config* file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="b83cc-200">Pour ce faire, remplacez **localhost** par le nom de domaine complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-200">Do this by replacing **localhost** with the fully qualified domain name of the server.</span></span>

10. <span data-ttu-id="b83cc-201">Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-201">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="b83cc-202">Sur le client, exécutez *ImportServiceCert.bat* dans invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-202">On the client, run *ImportServiceCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="b83cc-203">Cela importe le certificat de service à partir du fichier service. cer dans le magasin **CurrentUser-TrustedPeople** .</span><span class="sxs-lookup"><span data-stu-id="b83cc-203">This imports the service certificate from the Service.cer file into the **CurrentUser - TrustedPeople** store.</span></span>

12. <span data-ttu-id="b83cc-204">Sur le serveur, exécutez *ImportClientCert.bat* dans invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="b83cc-204">On the server, run *ImportClientCert.bat* in Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>

    <span data-ttu-id="b83cc-205">Cela importe le certificat client du fichier client. cer dans le magasin **LocalMachine-TrustedPeople** .</span><span class="sxs-lookup"><span data-stu-id="b83cc-205">This imports the client certificate from the Client.cer file into the **LocalMachine - TrustedPeople** store.</span></span>

13. <span data-ttu-id="b83cc-206">Sur l'ordinateur serveur, lancez Service.exe à partir de la fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b83cc-206">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="b83cc-207">Sur l'ordinateur client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="b83cc-207">On the client computer, launch Client.exe from a command prompt window.</span></span>

    <span data-ttu-id="b83cc-208">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="b83cc-208">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

### <a name="clean-up-after-the-sample"></a><span data-ttu-id="b83cc-209">Nettoyer après l’exemple</span><span class="sxs-lookup"><span data-stu-id="b83cc-209">Clean up after the sample</span></span>

<span data-ttu-id="b83cc-210">Pour nettoyer après l’exemple, exécutez *Cleanup.bat* dans le dossier Samples lorsque vous avez terminé d’exécuter l’exemple.</span><span class="sxs-lookup"><span data-stu-id="b83cc-210">To clean up after the sample, run *Cleanup.bat* in the samples folder when you have finished running the sample.</span></span> <span data-ttu-id="b83cc-211">Cela supprime les certificats du serveur et du client du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="b83cc-211">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="b83cc-212">Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="b83cc-212">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="b83cc-213">Si vous avez exécuté des exemples WCF qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="b83cc-213">If you have run WCF samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="b83cc-214">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="b83cc-214">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
