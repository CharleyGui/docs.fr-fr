---
title: Token Provider
ms.date: 03/30/2017
ms.assetid: 947986cf-9946-4987-84e5-a14678d96edb
ms.openlocfilehash: e761f32ab26cf620b6ef1dddff2bcba53289af84
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262331"
---
# <a name="token-provider"></a><span data-ttu-id="64cfd-102">Token Provider</span><span class="sxs-lookup"><span data-stu-id="64cfd-102">Token Provider</span></span>

<span data-ttu-id="64cfd-103">Cet exemple montre comment implémenter un fournisseur de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64cfd-103">This sample demonstrates how to implement a custom token provider.</span></span> <span data-ttu-id="64cfd-104">Un fournisseur de jetons dans Windows Communication Foundation (WCF) est utilisé pour fournir des informations d’identification à l’infrastructure de sécurité.</span><span class="sxs-lookup"><span data-stu-id="64cfd-104">A token provider in Windows Communication Foundation (WCF) is used for supplying credentials to the security infrastructure.</span></span> <span data-ttu-id="64cfd-105">En général, le fournisseur de jetons examine la cible et publie des informations d'identification appropriées afin que l'infrastructure de sécurité puisse sécuriser le message.</span><span class="sxs-lookup"><span data-stu-id="64cfd-105">The token provider in general examines the target and issues appropriate credentials so that the security infrastructure can secure the message.</span></span> <span data-ttu-id="64cfd-106">WCF est fourni avec le fournisseur de jetons du gestionnaire d’informations d’identification par défaut.</span><span class="sxs-lookup"><span data-stu-id="64cfd-106">WCF ships with the default Credential Manager Token Provider.</span></span> <span data-ttu-id="64cfd-107">WCF est également fourni avec un fournisseur de jetons CardSpace.</span><span class="sxs-lookup"><span data-stu-id="64cfd-107">WCF also ships with a CardSpace token provider.</span></span> <span data-ttu-id="64cfd-108">Les fournisseurs de jetons personnalisés sont utiles dans les cas suivants :</span><span class="sxs-lookup"><span data-stu-id="64cfd-108">Custom token providers are useful in the following cases:</span></span>

- <span data-ttu-id="64cfd-109">si vous avez un magasin d'informations d'identification avec lequel ces fournisseurs de jetons ne peuvent pas fonctionner ;</span><span class="sxs-lookup"><span data-stu-id="64cfd-109">If you have a credential store that these token providers cannot operate with.</span></span>

- <span data-ttu-id="64cfd-110">Si vous souhaitez fournir votre propre mécanisme personnalisé pour transformer les informations d’identification à partir du moment où l’utilisateur fournit les détails lorsque l’infrastructure cliente WCF utilise les informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="64cfd-110">If you want to provide your own custom mechanism for transforming the credentials from the point when the user provides the details to when the WCF client framework uses the credentials.</span></span>

- <span data-ttu-id="64cfd-111">si vous générez un jeton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64cfd-111">If you are building a custom token.</span></span>

 <span data-ttu-id="64cfd-112">Cet exemple montre comment générer un fournisseur de jetons personnalisé qui convertit les entrées de l'utilisateur dans un autre format.</span><span class="sxs-lookup"><span data-stu-id="64cfd-112">This sample shows how to build a custom token provider that transforms the input from the user into a different format.</span></span>

 <span data-ttu-id="64cfd-113">En résumé, cet exemple montre :</span><span class="sxs-lookup"><span data-stu-id="64cfd-113">To summarize, this sample demonstrates the following:</span></span>

- <span data-ttu-id="64cfd-114">la façon dont un client peut s'authentifier à l'aide d'une paire nom d'utilisateur/mot de passe ;</span><span class="sxs-lookup"><span data-stu-id="64cfd-114">How a client can authenticate using a username/password pair.</span></span>

- <span data-ttu-id="64cfd-115">la façon dont un client peut être configuré avec un fournisseur de jetons personnalisé ;</span><span class="sxs-lookup"><span data-stu-id="64cfd-115">How a client can be configured with a custom token provider.</span></span>

- <span data-ttu-id="64cfd-116">la façon dont le serveur peut valider les informations d'identification du client à l'aide d'un mot de passe avec un <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> personnalisé qui valide que le nom d'utilisateur et le mot de passe correspondent ;</span><span class="sxs-lookup"><span data-stu-id="64cfd-116">How the server can validate the client credentials using a password with a custom <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> that validates that the username and password match.</span></span>

- <span data-ttu-id="64cfd-117">la façon dont le serveur est authentifié auprès du client à l'aide du certificat X.509 du serveur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-117">How the server is authenticated by the client using the server's X.509 certificate.</span></span>

 <span data-ttu-id="64cfd-118">Cet exemple montre également comment l'identité de l'appelant est accessible après le processus d'authentification du jeton personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64cfd-118">This sample also shows how the caller's identity is accessible after the custom token authentication process.</span></span>

 <span data-ttu-id="64cfd-119">Le service expose un point de terminaison unique permettant de communiquer avec le service, défini à l'aide du fichier de configuration App.config.</span><span class="sxs-lookup"><span data-stu-id="64cfd-119">The service exposes a single endpoint for communicating with the service, defined using the App.config configuration file.</span></span> <span data-ttu-id="64cfd-120">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="64cfd-120">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="64cfd-121">La liaison est configurée avec un `wsHttpBinding`standard, qui utilise par défaut le mode de sécurité du message.</span><span class="sxs-lookup"><span data-stu-id="64cfd-121">The binding is configured with a standard `wsHttpBinding`, which uses message security by default.</span></span> <span data-ttu-id="64cfd-122">Cet exemple définit le `wsHttpBinding` standard pour permettre l'authentification du client à l'aide du nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-122">This sample sets the standard `wsHttpBinding` to use client username authentication.</span></span> <span data-ttu-id="64cfd-123">Le service configure également le certificat de service à l'aide du comportement serviceCredentials.</span><span class="sxs-lookup"><span data-stu-id="64cfd-123">The service also configures the service certificate using the serviceCredentials behavior.</span></span> <span data-ttu-id="64cfd-124">Le comportement serviceCredentials vous permet de configurer un certificat de service.</span><span class="sxs-lookup"><span data-stu-id="64cfd-124">The serviceCredentials behavior allows you to configure a service certificate.</span></span> <span data-ttu-id="64cfd-125">Un certificat de service est utilisé par un client pour authentifier le service et fournir la protection des messages.</span><span class="sxs-lookup"><span data-stu-id="64cfd-125">A service certificate is used by a client to authenticate the service and provide message protection.</span></span> <span data-ttu-id="64cfd-126">La configuration suivante référence le certificat localhost installé pendant l'installation de l'exemple, tel que décrit dans les instructions d'installation suivantes.</span><span class="sxs-lookup"><span data-stu-id="64cfd-126">The following configuration references the localhost certificate installed during the sample setup as described in the following setup instructions.</span></span>

```xml
<system.serviceModel>
    <services>
      <service
          name="Microsoft.ServiceModel.Samples.CalculatorService"
          behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <!-- configure base address provided by host -->
            <add baseAddress ="http://localhost:8000/servicemodelsamples/service"/>
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
        -->
          <serviceCredentials>
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
```

 <span data-ttu-id="64cfd-127">La configuration de point de terminaison de client se compose d’un nom de configuration, d’une adresse absolue pour le point de terminaison de service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="64cfd-127">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="64cfd-128">La liaison de client est configurée avec le `Mode` et le message `clientCredentialType` appropriés.</span><span class="sxs-lookup"><span data-stu-id="64cfd-128">The client binding is configured with the appropriate `Mode` and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="64cfd-129">Les étapes suivantes montrent comment développer un fournisseur de jetons personnalisé et l’intégrer à l’infrastructure de sécurité WCF :</span><span class="sxs-lookup"><span data-stu-id="64cfd-129">The following steps show how to develop a custom token provider and integrate it with the WCF security framework:</span></span>

1. <span data-ttu-id="64cfd-130">Écrivez un fournisseur de jetons personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64cfd-130">Write a custom token provider.</span></span>

     <span data-ttu-id="64cfd-131">L'exemple implémente un fournisseur de jetons personnalisé qui obtient le nom d'utilisateur et le mot de passe.</span><span class="sxs-lookup"><span data-stu-id="64cfd-131">The sample implements a custom token provider that obtains the username and password.</span></span> <span data-ttu-id="64cfd-132">Le mot de passe doit correspondre à ce nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-132">The password must match this username.</span></span> <span data-ttu-id="64cfd-133">Ce fournisseur de jetons personnalisé est uniquement fourni à des fins de démonstration et son utilisation n'est pas recommandée en cas de déploiement réel.</span><span class="sxs-lookup"><span data-stu-id="64cfd-133">This custom token provider is for demonstration purposes only and is not recommended for real world deployment.</span></span>

     <span data-ttu-id="64cfd-134">Pour effectuer cette tâche, le fournisseur de jetons personnalisé dérive la classe <xref:System.IdentityModel.Selectors.SecurityTokenProvider> et substitue la méthode <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29>.</span><span class="sxs-lookup"><span data-stu-id="64cfd-134">To perform this task, the custom token provider derives the <xref:System.IdentityModel.Selectors.SecurityTokenProvider> class and overrides the <xref:System.IdentityModel.Selectors.SecurityTokenProvider.GetTokenCore%28System.TimeSpan%29> method.</span></span> <span data-ttu-id="64cfd-135">Cette méthode crée et retourne un nouveau `UserNameSecurityToken`.</span><span class="sxs-lookup"><span data-stu-id="64cfd-135">This method creates and returns a new `UserNameSecurityToken`.</span></span>

    ```csharp
    protected override SecurityToken GetTokenCore(TimeSpan timeout)
    {
        // obtain username and password from the user using console window
        string username = GetUserName();
        string password = GetPassword();
        Console.WriteLine("username: {0}", username);

        // return new UserNameSecurityToken containing information obtained from user
        return new UserNameSecurityToken(username, password);
    }
    ```

2. <span data-ttu-id="64cfd-136">Écrivez un gestionnaire de jetons de sécurité personnalisé.</span><span class="sxs-lookup"><span data-stu-id="64cfd-136">Write custom security token manager.</span></span>

     <span data-ttu-id="64cfd-137"><xref:System.IdentityModel.Selectors.SecurityTokenManager> permet de créer <xref:System.IdentityModel.Selectors.SecurityTokenProvider> pour le <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> spécifique qui lui est passé dans la méthode `CreateSecurityTokenProvider`.</span><span class="sxs-lookup"><span data-stu-id="64cfd-137">The <xref:System.IdentityModel.Selectors.SecurityTokenManager> is used to create <xref:System.IdentityModel.Selectors.SecurityTokenProvider> for specific <xref:System.IdentityModel.Selectors.SecurityTokenRequirement> that is passed to it in `CreateSecurityTokenProvider` method.</span></span> <span data-ttu-id="64cfd-138">Le gestionnaire de jetons de sécurité permet également de créer des authentificateurs et un sérialiseur de jeton, mais ceux-ci ne sont pas traités dans cet exemple.</span><span class="sxs-lookup"><span data-stu-id="64cfd-138">Security token manager is also used to create token authenticators and a token serializer, but those are not covered by this sample.</span></span> <span data-ttu-id="64cfd-139">Dans cet exemple, le gestionnaire de jetons de sécurité personnalisé hérite de la classe <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> et substitue la méthode `CreateSecurityTokenProvider` pour retourner le fournisseur de jetons de nom d'utilisateur personnalisé lorsque les spécifications du jeton passé indiquent qu'un fournisseur de noms d'utilisateur est demandé.</span><span class="sxs-lookup"><span data-stu-id="64cfd-139">In this sample, the custom security token manager inherits from <xref:System.ServiceModel.ClientCredentialsSecurityTokenManager> class and overrides the `CreateSecurityTokenProvider` method to return custom username token provider when the passed token requirements indicate that username provider is requested.</span></span>

    ```csharp
    public class MyUserNameSecurityTokenManager : ClientCredentialsSecurityTokenManager
    {
        MyUserNameClientCredentials myUserNameClientCredentials;

        public MyUserNameSecurityTokenManager(MyUserNameClientCredentials myUserNameClientCredentials)
            : base(myUserNameClientCredentials)
        {
            this.myUserNameClientCredentials = myUserNameClientCredentials;
        }

        public override SecurityTokenProvider CreateSecurityTokenProvider(SecurityTokenRequirement tokenRequirement)
        {
            // if token requirement matches username token return custom username token provider
            // otherwise use base implementation
            if (tokenRequirement.TokenType == SecurityTokenTypes.UserName)
            {
                return new MyUserNameTokenProvider();
            }
            else
            {
                return base.CreateSecurityTokenProvider(tokenRequirement);
            }
        }
    }
    ```

3. <span data-ttu-id="64cfd-140">Écrivez une information d'identification client personnalisée.</span><span class="sxs-lookup"><span data-stu-id="64cfd-140">Write a custom client credential.</span></span>

     <span data-ttu-id="64cfd-141">La classe d'informations d'identification client permet de représenter les informations d'identification qui sont configurées pour le proxy client et crée le gestionnaire de jetons de sécurité utilisé pour obtenir des authentificateurs, des fournisseurs et un sérialiseur de jeton.</span><span class="sxs-lookup"><span data-stu-id="64cfd-141">Client credentials class is used to represent the credentials that are configured for the client proxy and creates security token manager that is used to obtain token authenticators, token providers and a token serializer.</span></span>

    ```csharp
    public class MyUserNameClientCredentials : ClientCredentials
    {
        public MyUserNameClientCredentials()
            : base()
        {
        }

        protected override ClientCredentials CloneCore()
        {
            return new MyUserNameClientCredentials();
        }

        public override SecurityTokenManager CreateSecurityTokenManager()
        {
            // return custom security token manager
            return new MyUserNameSecurityTokenManager(this);
        }
    }
    ```

4. <span data-ttu-id="64cfd-142">Configurez le client pour qu'il utilise les informations d'identification du client personnalisées.</span><span class="sxs-lookup"><span data-stu-id="64cfd-142">Configure the client to use the custom client credential.</span></span>

     <span data-ttu-id="64cfd-143">Pour que le client puisse utiliser les informations d'identification client personnalisées, l'exemple supprime la classe d'informations d'identification client par défaut et fournit la nouvelle.</span><span class="sxs-lookup"><span data-stu-id="64cfd-143">In order for the client to use the custom client credential, the sample deletes the default client credential class and supplies the new client credential class.</span></span>

    ```csharp
    static void Main()
    {
        // ...
           // Create a client with given client endpoint configuration
          CalculatorClient client = new CalculatorClient();

          // set new credentials
           client.ChannelFactory.Endpoint.Behaviors.Remove(typeof(ClientCredentials));
         client.ChannelFactory.Endpoint.Behaviors.Add(new MyUserNameClientCredentials());
       // ...
    }
    ```

 <span data-ttu-id="64cfd-144">Sur le service, utilisez <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> tel qu'indiqué dans l'exemple de code suivant pour afficher les informations de l'appelant.</span><span class="sxs-lookup"><span data-stu-id="64cfd-144">On the service, to display the caller's information, use the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> as shown in the following code example.</span></span> <span data-ttu-id="64cfd-145"><xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contient des informations sur les revendications relatives à l'appelant actuel.</span><span class="sxs-lookup"><span data-stu-id="64cfd-145">The <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> contains claims information about the current caller.</span></span>

```csharp
static void DisplayIdentityInformation()
{
    Console.WriteLine("\t\tSecurity context identity  :  {0}",
        ServiceSecurityContext.Current.PrimaryIdentity.Name);
}
```

 <span data-ttu-id="64cfd-146">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="64cfd-146">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="64cfd-147">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="64cfd-147">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="64cfd-148">Fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="64cfd-148">Setup Batch File</span></span>

 <span data-ttu-id="64cfd-149">Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec le certificat approprié pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-149">The Setup.bat batch file included with this sample allows you to configure the server with the relevant certificate to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="64cfd-150">Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.</span><span class="sxs-lookup"><span data-stu-id="64cfd-150">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="64cfd-151">Les éléments suivants fournissent une brève vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée :</span><span class="sxs-lookup"><span data-stu-id="64cfd-151">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="64cfd-152">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="64cfd-152">Creating the server certificate.</span></span>

     <span data-ttu-id="64cfd-153">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="64cfd-153">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="64cfd-154">La variable `%SERVER_NAME%` spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-154">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="64cfd-155">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-155">Change this variable to specify your own server name.</span></span> <span data-ttu-id="64cfd-156">La valeur par défaut dans ce fichier de commandes est localhost.</span><span class="sxs-lookup"><span data-stu-id="64cfd-156">The default value in this batch file is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="64cfd-157">Installation du certificat de serveur dans le magasin de certificats approuvés du client :</span><span class="sxs-lookup"><span data-stu-id="64cfd-157">Installing the server certificate into the client's trusted certificate store:</span></span>

     <span data-ttu-id="64cfd-158">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="64cfd-158">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="64cfd-159">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="64cfd-159">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="64cfd-160">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="64cfd-160">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

> [!NOTE]
> <span data-ttu-id="64cfd-161">Le fichier de commandes Setup.bat est conçu pour s'exécuter à partir d'une invite de commandes du Kit de développement Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="64cfd-161">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="64cfd-162">La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="64cfd-162">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="64cfd-163">Cette variable est définie automatiquement dans une invite de commandes du Kit de développement logiciel Windows.</span><span class="sxs-lookup"><span data-stu-id="64cfd-163">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="64cfd-164">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="64cfd-164">To set up and build the sample</span></span>

1. <span data-ttu-id="64cfd-165">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="64cfd-165">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="64cfd-166">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="64cfd-166">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="64cfd-167">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="64cfd-167">To run the sample on the same computer</span></span>

1. <span data-ttu-id="64cfd-168">Exécutez Setup.bat à partir du dossier d’installation de l’exemple à l’aide d’une invite de commandes Visual Studio 2012 ouverte avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-168">Run Setup.bat from the sample installation folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="64cfd-169">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="64cfd-169">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="64cfd-170">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="64cfd-170">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="64cfd-171">La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="64cfd-171">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="64cfd-172">Lancez service.exe à partir de service\bin.</span><span class="sxs-lookup"><span data-stu-id="64cfd-172">Launch service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="64cfd-173">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="64cfd-173">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="64cfd-174">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="64cfd-174">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="64cfd-175">À l'invite de nom d'utilisateur, tapez un nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-175">At the username prompt, type a user name.</span></span>  
  
5. <span data-ttu-id="64cfd-176">À l'invite de mot de passe, utilisez la même chaîne tapée pour l'invite de nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-176">At the password prompt, use the same string that was typed for the username prompt.</span></span>  
  
6. <span data-ttu-id="64cfd-177">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="64cfd-177">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="64cfd-178">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="64cfd-178">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="64cfd-179">Créez un répertoire sur l'ordinateur de service pour les fichiers binaires du service.</span><span class="sxs-lookup"><span data-stu-id="64cfd-179">Create a directory on the service computer for the service binaries.</span></span>  
  
2. <span data-ttu-id="64cfd-180">Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="64cfd-180">Copy the service program files to the service directory on the service computer.</span></span> <span data-ttu-id="64cfd-181">Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="64cfd-181">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="64cfd-182">Le nom de sujet de votre certificat de serveur doit contenir le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-182">You must have a server certificate with the subject name that contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="64cfd-183">Le fichier Service.exe.config doit être mis à jour pour refléter ce nouveau nom de certificat.</span><span class="sxs-lookup"><span data-stu-id="64cfd-183">The Service.exe.config file must be updated to reflect this new certificate name.</span></span> <span data-ttu-id="64cfd-184">Vous pouvez créer le certificat de serveur en modifiant le fichier de commandes Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="64cfd-184">You can create server certificate by modifying the Setup.bat batch file.</span></span> <span data-ttu-id="64cfd-185">Notez que le fichier setup.bat doit être exécuté à partir d’un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="64cfd-185">Note that the setup.bat file must be run from a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="64cfd-186">Vous devez affecter à la variable `%SERVER_NAME%` le nom d'hôte complet de l'ordinateur utilisé pour héberger le service.</span><span class="sxs-lookup"><span data-stu-id="64cfd-186">You must set `%SERVER_NAME%` variable to fully-qualified host name of the computer that is used to host the service.</span></span>  
  
4. <span data-ttu-id="64cfd-187">Copiez le certificat de serveur dans le magasin CurrentUser-TrustedPeople du client.</span><span class="sxs-lookup"><span data-stu-id="64cfd-187">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="64cfd-188">Cette opération n'est pas nécessaire lorsque le certificat de serveur est émis par un émetteur approuvé du client.</span><span class="sxs-lookup"><span data-stu-id="64cfd-188">You do not need to do this when the server certificate is issued by a client trusted issuer.</span></span>  
  
5. <span data-ttu-id="64cfd-189">Dans le fichier Service.exe.config sur l'ordinateur de service, modifiez la valeur de l'adresse de base pour spécifier le nom de l'ordinateur complet au lieu de localhost.</span><span class="sxs-lookup"><span data-stu-id="64cfd-189">In the Service.exe.config file on the service computer, change the value of the base address to specify a fully-qualified computer name instead of localhost.</span></span>  
  
6. <span data-ttu-id="64cfd-190">Sur l'ordinateur de service, exécutez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="64cfd-190">On the service computer, run service.exe from a command prompt.</span></span>  
  
7. <span data-ttu-id="64cfd-191">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="64cfd-191">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
8. <span data-ttu-id="64cfd-192">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="64cfd-192">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="64cfd-193">Sur l'ordinateur client, lancez `Client.exe` à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="64cfd-193">On the client computer, launch `Client.exe` from a command prompt window.</span></span>  
  
10. <span data-ttu-id="64cfd-194">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="64cfd-194">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="64cfd-195">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="64cfd-195">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="64cfd-196">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="64cfd-196">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>
