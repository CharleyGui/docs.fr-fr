---
title: Token Authenticator
ms.date: 03/30/2017
ms.assetid: 84382f2c-f6b1-4c32-82fa-aebc8f6064db
ms.openlocfilehash: f4b49edd3b5a2cecd203feed713c7694450f7497
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596550"
---
# <a name="token-authenticator"></a><span data-ttu-id="3221b-102">Token Authenticator</span><span class="sxs-lookup"><span data-stu-id="3221b-102">Token Authenticator</span></span>
<span data-ttu-id="3221b-103">Cet exemple montre comment implémenter un authentificateur de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-103">This sample demonstrates how to implement a custom token authenticator.</span></span> <span data-ttu-id="3221b-104">Un authentificateur de jetons dans Windows Communication Foundation (WCF) est utilisé pour valider le jeton utilisé avec le message, vérifier qu’il est auto-cohérent et authentifier l’identité associée au jeton.</span><span class="sxs-lookup"><span data-stu-id="3221b-104">A token authenticator in Windows Communication Foundation (WCF) is used for validating the token used with the message, verifying that it is self-consistent, and authenticating the identity associated with the token.</span></span>

 <span data-ttu-id="3221b-105">Les authentificateurs de jetons personnalisés sont utiles dans un grand nombre de cas, dont les suivants :</span><span class="sxs-lookup"><span data-stu-id="3221b-105">Custom token authenticators are useful in a variety of cases, such as:</span></span>

- <span data-ttu-id="3221b-106">Lorsque vous souhaitez substituer le mécanisme d'authentification par défaut associé à un jeton.</span><span class="sxs-lookup"><span data-stu-id="3221b-106">When you want to override the default authentication mechanism associated with a token.</span></span>

- <span data-ttu-id="3221b-107">Lorsque vous générez un jeton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-107">When you are building a custom token.</span></span>

 <span data-ttu-id="3221b-108">Cet exemple indique :</span><span class="sxs-lookup"><span data-stu-id="3221b-108">This sample demonstrates the following:</span></span>

- <span data-ttu-id="3221b-109">la façon dont un client peut s'authentifier à l'aide d'une paire nom d'utilisateur/mot de passe ;</span><span class="sxs-lookup"><span data-stu-id="3221b-109">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="3221b-110">Comment le serveur peut valider les informations d'identification du client à l'aide d'un authentificateur de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-110">How the server can validate the client credentials using a custom token authenticator.</span></span>

- <span data-ttu-id="3221b-111">Comment le code du service WCF entre en lien avec l’authentificateur de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-111">How the WCF service code ties in with the custom token authenticator.</span></span>

- <span data-ttu-id="3221b-112">Comment le serveur peut être authentifié à l'aide de son certificat X.509.</span><span class="sxs-lookup"><span data-stu-id="3221b-112">How the server can be authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="3221b-113">Cet exemple montre également comment l’identité de l’appelant est accessible à partir de WCF après le processus d’authentification du jeton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-113">This sample also shows how the caller's identity is accessible from WCF after the custom token authentication process.</span></span>

 <span data-ttu-id="3221b-114">Le service expose un point de terminaison unique permettant de communiquer avec le service, défini à l'aide du fichier de configuration App.config.</span><span class="sxs-lookup"><span data-stu-id="3221b-114">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="3221b-115">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="3221b-115">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="3221b-116">La liaison est configurée avec un `wsHttpBinding` standard, avec le mode de sécurité du message (mode par défaut de `wsHttpBinding`).</span><span class="sxs-lookup"><span data-stu-id="3221b-116">The binding is configured with a standard `wsHttpBinding`, with the security mode set to message - the default mode of the `wsHttpBinding`.</span></span> <span data-ttu-id="3221b-117">Cet exemple définit le `wsHttpBinding` standard pour permettre l'authentification du client à l'aide du nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3221b-117">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="3221b-118">Le service configure également le certificat de service à l'aide du comportement `serviceCredentials`.</span><span class="sxs-lookup"><span data-stu-id="3221b-118">The service also configures the service certificate using `serviceCredentials` behavior.</span></span> <span data-ttu-id="3221b-119">Le comportement `securityCredentials` vous permet de spécifier un certificat de service.</span><span class="sxs-lookup"><span data-stu-id="3221b-119">The `securityCredentials` behavior allows you to specify a service certificate.</span></span> <span data-ttu-id="3221b-120">Un certificat de service est utilisé par un client pour authentifier le service et fournir la protection des messages.</span><span class="sxs-lookup"><span data-stu-id="3221b-120">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="3221b-121">La configuration suivante référence le certificat localhost installé pendant l'installation de l'exemple, tel que décrit dans les instructions d'installation suivantes.</span><span class="sxs-lookup"><span data-stu-id="3221b-121">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address provided by host -->
        <endpoint address=""
                  binding="wsHttpBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>

    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults="False" />
          <!--
          The serviceCredentials behavior allows one to define a service certificate.
          A service certificate is used by a client to authenticate the service and provide message protection.
          This configuration references the "localhost" certificate installed during the setup instructions.
....        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

 <span data-ttu-id="3221b-122">La configuration de point de terminaison de client se compose d’un nom de configuration, d’une adresse absolue pour le point de terminaison de service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="3221b-122">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="3221b-123">La liaison du client est configurée avec le `Mode` et le `clientCredentialType` appropriés.</span><span class="sxs-lookup"><span data-stu-id="3221b-123">The client binding is configured with the appropriate `Mode` and `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <endpoint name=""
                address="http://localhost:8000/servicemodelsamples/service"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>

    <bindings>
      <wsHttpBinding>
        <binding name="Binding1">
          <security mode="Message">
            <message clientCredentialType="UserName" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
  </system.serviceModel>
```

 <span data-ttu-id="3221b-124">L'implémentation cliente définit le nom d'utilisateur et le mot de passe à utiliser.</span><span class="sxs-lookup"><span data-stu-id="3221b-124">The client implementation sets the user name and password to use.</span></span>

```csharp
static void Main()
{
     ...
     client.ClientCredentials.UserNamePassword.UserName = username;
     client.ClientCredentials.UserNamePassword.Password = password;
     ...
}
```

## <a name="custom-token-authenticator"></a><span data-ttu-id="3221b-125">Authentificateur de jetons personnalisé</span><span class="sxs-lookup"><span data-stu-id="3221b-125">Custom Token Authenticator</span></span>
 <span data-ttu-id="3221b-126">Suivez les étapes suivantes pour créer un authentificateur de jetons personnalisé :</span><span class="sxs-lookup"><span data-stu-id="3221b-126">Use the following steps to create a custom token authenticator:</span></span>

1. <span data-ttu-id="3221b-127">Écrivez un authentificateur de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-127">Write a custom token authenticator.</span></span>

     <span data-ttu-id="3221b-128">L'exemple implémente un authentificateur de jetons personnalisé qui valide que le nom d'utilisateur a un format d'adresse de messagerie valide.</span><span class="sxs-lookup"><span data-stu-id="3221b-128">The sample implements a custom token authenticator that validates that the username has a valid email format.</span></span> <span data-ttu-id="3221b-129">Il dérive <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span><span class="sxs-lookup"><span data-stu-id="3221b-129">It derives the <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator>.</span></span> <span data-ttu-id="3221b-130">La méthode la plus importante de cette classe est <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span><span class="sxs-lookup"><span data-stu-id="3221b-130">The most important method in this class is <xref:System.IdentityModel.Selectors.UserNameSecurityTokenAuthenticator.ValidateUserNamePasswordCore%28System.String%2CSystem.String%29>.</span></span> <span data-ttu-id="3221b-131">Dans cette méthode, l'authentificateur valide le format du nom d'utilisateur et également que le nom d'hôte ne provient pas d'un domaine non autorisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-131">In this method, the authenticator validates the format of the username and also that the host name is not from a rogue domain.</span></span> <span data-ttu-id="3221b-132">Si ces deux conditions sont vérifiées, il retourne une collection d'instances <xref:System.IdentityModel.Policy.IAuthorizationPolicy> en lecture seule qui est par la suite utilisée pour fournir des revendications représentant les informations stockée à l'intérieur du jeton de nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="3221b-132">If both conditions are met, then it returns a read-only collection of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> instances that is then used to provide claims that represent the information stored inside the username token.</span></span>

    ```csharp
    protected override ReadOnlyCollection<IAuthorizationPolicy> ValidateUserNamePasswordCore(string userName, string password)
    {
        if (!ValidateUserNameFormat(userName))
            throw new SecurityTokenValidationException("Incorrect UserName format");

        ClaimSet claimSet = new DefaultClaimSet(ClaimSet.System, new Claim(ClaimTypes.Name, userName, Rights.PossessProperty));
        List<IIdentity> identities = new List<IIdentity>(1);
        identities.Add(new GenericIdentity(userName));
        List<IAuthorizationPolicy> policies = new List<IAuthorizationPolicy>(1);
        policies.Add(new UnconditionalPolicy(ClaimSet.System, claimSet, DateTime.MaxValue.ToUniversalTime(), identities));
        return policies.AsReadOnly();
    }
    ```

2. <span data-ttu-id="3221b-133">Fournissez une stratégie d'autorisation retournée par l'authentificateur de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-133">Provide an authorization policy that is returned by custom token authenticator.</span></span>

     <span data-ttu-id="3221b-134">Cet exemple fournit sa propre implémentation de <xref:System.IdentityModel.Policy.IAuthorizationPolicy> appelé `UnconditionalPolicy` qui retourne l'ensemble de revendications et d'identités qui lui ont été passées dans son constructeur.</span><span class="sxs-lookup"><span data-stu-id="3221b-134">This sample provides its own implementation of <xref:System.IdentityModel.Policy.IAuthorizationPolicy> called `UnconditionalPolicy` that returns set of claims and identities that were passed to it in its constructor.</span></span>

    ```csharp
    class UnconditionalPolicy : IAuthorizationPolicy
    {
        String id = Guid.NewGuid().ToString();
        ClaimSet issuer;
        ClaimSet issuance;
        DateTime expirationTime;
        IList<IIdentity> identities;

        public UnconditionalPolicy(ClaimSet issuer, ClaimSet issuance, DateTime expirationTime, IList<IIdentity> identities)
        {
            if (issuer == null)
                throw new ArgumentNullException("issuer");
            if (issuance == null)
                throw new ArgumentNullException("issuance");

            this.issuer = issuer;
            this.issuance = issuance;
            this.identities = identities;
            this.expirationTime = expirationTime;
        }

        public string Id
        {
            get { return this.id; }
        }

        public ClaimSet Issuer
        {
            get { return this.issuer; }
        }

        public DateTime ExpirationTime
        {
            get { return this.expirationTime; }
        }

        public bool Evaluate(EvaluationContext evaluationContext, ref object state)
        {
            evaluationContext.AddToTarget(this, this.issuance);

            if (this.identities != null)
            {
                object value;
                IList<IIdentity> contextIdentities;
                if (!evaluationContext.Properties.TryGetValue("Identities", out value))
                {
                    contextIdentities = new List<IIdentity>(this.identities.Count);
                    evaluationContext.Properties.Add("Identities", contextIdentities);
                }
                else
                {
                    contextIdentities = value as IList<IIdentity>;
                }
                foreach (IIdentity identity in this.identities)
                {
                    contextIdentities.Add(identity);
                }
            }

            evaluationContext.RecordExpirationTime(this.expirationTime);
            return true;
        }
    }
    ```

3. <span data-ttu-id="3221b-135">Écrivez un gestionnaire de jetons de sécurité personnalisé.</span><span class="sxs-lookup"><span data-stu-id="3221b-135">Write a custom security token manager.</span></span>

     <span data-ttu-id="3221b-136"><xref:System.IdentityModel.Selectors.SecurityTokenManager> permet de créer <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> pour des objets <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> spécifiques qui lui sont passés dans la méthode `CreateSecurityTokenAuthenticator`.</span><span class="sxs-lookup"><span data-stu-id="3221b-136">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create a <xref:System.IdentityModel.Selectors.SecurityTokenAuthenticator> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> objects that are passed to it in the `CreateSecurityTokenAuthenticator` method.</span></span> <span data-ttu-id="3221b-137">Le gestionnaire de jetons de sécurité permet également de créer des fournisseurs et des sérialiseurs de jeton, mais ceux-ci ne sont pas traités dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="3221b-137">The security token manager is also used to create token providers and token serializers, but those are not covered by this sample.</span></span> <span data-ttu-id="3221b-138">Dans cet exemple, le gestionnaire de jetons de sécurité personnalisé hérite de classe <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> et substitue la méthode `CreateSecurityTokenAuthenticator` pour retourner l’authentificateur de jeton de nom d’utilisateur personnalisé lorsque les exigences de jeton passées indiquent que l’authentificateur de nom d’utilisateur est demandé.</span><span class="sxs-lookup"><span data-stu-id="3221b-138">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.Security.ServiceCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenAuthenticator` method to return custom username token authenticator when the passed token requirements indicate that username authenticator is requested.</span></span>

    ```csharp
    public class MySecurityTokenManager : ServiceCredentialsSecurityTokenManager
    {
        MyUserNameCredential myUserNameCredential;

        public MySecurityTokenManager(MyUserNameCredential myUserNameCredential)
            : base(myUserNameCredential)
        {
            this.myUserNameCredential = myUserNameCredential;
        }

        public override SecurityTokenAuthenticator CreateSecurityTokenAuthenticator(SecurityTokenRequirement tokenRequirement, out SecurityTokenResolver outOfBandTokenResolver)
        {
            if (tokenRequirement.TokenType ==  SecurityTokenTypes.UserName)
            {
                outOfBandTokenResolver = null;
                return new MyTokenAuthenticator();
            }
            else
            {
                return base.CreateSecurityTokenAuthenticator(tokenRequirement, out outOfBandTokenResolver);
            }
        }
    }
    ```

4. <span data-ttu-id="3221b-139">Écrivez une information d'identification de service personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3221b-139">Write a custom service credential.</span></span>

     <span data-ttu-id="3221b-140">La classe d'informations d'identification de service permet de représenter les informations d'identification qui sont configurées pour le service et crée un gestionnaire de jetons de sécurité utilisé pour obtenir des authentificateurs, des fournisseurs et des sérialiseurs de jeton.</span><span class="sxs-lookup"><span data-stu-id="3221b-140">The service credentials class is used to represent the credentials that are configured for the service and creates a security token manager that is used to obtain token authenticators, token providers and token serializers.</span></span>

    ```csharp
    public class MyUserNameCredential : ServiceCredentials
    {

        public MyUserNameCredential()
            : base()
        {
        }

        protected override ServiceCredentials CloneCore()
        {
            return new MyUserNameCredential();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            return new MySecurityTokenManager(this);
        }

    }
    ```

5. <span data-ttu-id="3221b-141">Configurez le service pour qu'il utilise l'information d'identification de service personnalisée.</span><span class="sxs-lookup"><span data-stu-id="3221b-141">Configure the service to use the custom service credential.</span></span>

     <span data-ttu-id="3221b-142">Pour que le service utilise l'information d'identification de service personnalisée, nous supprimons la classe d'informations d'identification de service par défaut après avoir capturé le certificat de service qui est déjà préconfiguré dans les informations d'identification de service par défaut, puis nous configurons la nouvelle instance d'informations d'identification de service afin qu'elle utilise les certificats de service préconfigurés et ajoutons cette nouvelle instance aux comportements de service.</span><span class="sxs-lookup"><span data-stu-id="3221b-142">In order for the service to use the custom service credential, we delete the default service credential class after capturing the service certificate that is already preconfigured in the default service credential, and configure the new service credential instance to use the preconfigured service certificates and add this new service credential instance to service behaviors.</span></span>

    ```csharp
    ServiceCredentials sc = serviceHost.Credentials;
    X509Certificate2 cert = sc.ServiceCertificate.Certificate;
    MyUserNameCredential serviceCredential = new MyUserNameCredential();
    serviceCredential.ServiceCertificate.Certificate = cert;
    serviceHost.Description.Behaviors.Remove((typeof(ServiceCredentials)));
    serviceHost.Description.Behaviors.Add(serviceCredential);
    ```

 <span data-ttu-id="3221b-143">Pour afficher les informations sur l'appelant, vous pouvez utiliser <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A>, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="3221b-143">To display the caller's information, you can use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code.</span></span> <span data-ttu-id="3221b-144"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contient des informations sur les revendications relatives à l'appelant actuel.</span><span class="sxs-lookup"><span data-stu-id="3221b-144">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
            ServiceSecurityContext.Current.PrimaryIdentity.Name);
     return;
}
```

 <span data-ttu-id="3221b-145">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="3221b-145">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3221b-146">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="3221b-146">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="3221b-147">Fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="3221b-147">Setup Batch File</span></span>
 <span data-ttu-id="3221b-148">Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec les certificats appropriés pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="3221b-148">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate based security.</span></span> <span data-ttu-id="3221b-149">Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.</span><span class="sxs-lookup"><span data-stu-id="3221b-149">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="3221b-150">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.</span><span class="sxs-lookup"><span data-stu-id="3221b-150">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration.</span></span>

- <span data-ttu-id="3221b-151">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="3221b-151">Creating the server certificate.</span></span>

     <span data-ttu-id="3221b-152">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="3221b-152">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="3221b-153">La variable `%SERVER_NAME%` spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="3221b-153">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="3221b-154">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="3221b-154">Change this variable to specify your own server name.</span></span> <span data-ttu-id="3221b-155">La valeur par défaut dans ce fichier de commandes est localhost.</span><span class="sxs-lookup"><span data-stu-id="3221b-155">The default in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="3221b-156">Installation du certificat de serveur dans le magasin de certificats approuvé du client.</span><span class="sxs-lookup"><span data-stu-id="3221b-156">Installing the server certificate into client's trusted certificate store.</span></span>

     <span data-ttu-id="3221b-157">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="3221b-157">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="3221b-158">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="3221b-158">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="3221b-159">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="3221b-159">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    > <span data-ttu-id="3221b-160">Le fichier de commandes d'installation est conçu pour s'exécuter à partir d'une invite de commandes du Kit de développement Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="3221b-160">The setup batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="3221b-161">La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="3221b-161">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="3221b-162">Cette variable est définie automatiquement dans une invite de commandes du Kit de développement logiciel Windows.</span><span class="sxs-lookup"><span data-stu-id="3221b-162">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="3221b-163">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="3221b-163">To set up and build the sample</span></span>

1. <span data-ttu-id="3221b-164">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3221b-164">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3221b-165">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3221b-165">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="3221b-166">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="3221b-166">To run the sample on the same computer</span></span>

1. <span data-ttu-id="3221b-167">Exécutez setup. bat à partir du dossier d’installation de l’exemple à l’aide d’une invite de commandes Visual Studio 2012 ouverte avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="3221b-167">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="3221b-168">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="3221b-168">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="3221b-169">Le fichier de commandes Setup. bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="3221b-169">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="3221b-170">La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup. bat.</span><span class="sxs-lookup"><span data-stu-id="3221b-170">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="3221b-171">Lancez service.exe à partir de service\bin.</span><span class="sxs-lookup"><span data-stu-id="3221b-171">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="3221b-172">Lancez client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="3221b-172">Launch client.exe from \client\bin.</span></span> <span data-ttu-id="3221b-173">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="3221b-173">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="3221b-174">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3221b-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="3221b-175">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="3221b-175">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="3221b-176">Créez un répertoire sur l'ordinateur de service pour les fichiers binaires du service.</span><span class="sxs-lookup"><span data-stu-id="3221b-176">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="3221b-177">Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="3221b-177">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="3221b-178">Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="3221b-178">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="3221b-179">Le nom de sujet de votre certificat de serveur doit contenir le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3221b-179">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="3221b-180">Le fichier App.config du service doit être mis à jour afin de prendre en compte ce nouveau nom de certificat.</span><span class="sxs-lookup"><span data-stu-id="3221b-180">The service App.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="3221b-181">Vous pouvez en créer un en utilisant Setup.bat si vous affectez à la variable `%SERVER_NAME%` le nom d'hôte complet de l'ordinateur sur lequel le service s'exécutera.</span><span class="sxs-lookup"><span data-stu-id="3221b-181">You can create one by using the Setup.bat if you set the `%SERVER_NAME%` variable to fully-qualified host name of the computer on which the service will run.</span></span> <span data-ttu-id="3221b-182">Notez que le fichier Setup. bat doit être exécuté à partir d’un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="3221b-182">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span>  
  
4. <span data-ttu-id="3221b-183">Copiez le certificat de serveur dans le magasin CurrentUser-TrustedPeople du client.</span><span class="sxs-lookup"><span data-stu-id="3221b-183">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="3221b-184">Cette opération n'est pas nécessaire sauf lorsque le certificat de serveur est émis par un émetteur approuvé du client.</span><span class="sxs-lookup"><span data-stu-id="3221b-184">You do not need to do this except when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="3221b-185">Dans le fichier App.config sur l'ordinateur de service, modifiez la valeur de l'adresse de base pour spécifier le nom de l'ordinateur complet au lieu de localhost.</span><span class="sxs-lookup"><span data-stu-id="3221b-185">In the App.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="3221b-186">Sur l'ordinateur de service, exécutez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3221b-186">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="3221b-187">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="3221b-187">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="3221b-188">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="3221b-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="3221b-189">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="3221b-189">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
10. <span data-ttu-id="3221b-190">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="3221b-190">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="3221b-191">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="3221b-191">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="3221b-192">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="3221b-192">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
