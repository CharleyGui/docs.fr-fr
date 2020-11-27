---
title: Validateur de nom d'utilisateur et de mot de passe
ms.date: 03/30/2017
ms.assetid: 42f03841-286b-42d8-ba58-18c75422bc8e
ms.openlocfilehash: bf20c9baaec44ebdfed351b35c54ab14448c7644
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294922"
---
# <a name="user-name-password-validator"></a><span data-ttu-id="4d113-102">Validateur de nom d'utilisateur et de mot de passe</span><span class="sxs-lookup"><span data-stu-id="4d113-102">User Name Password Validator</span></span>

<span data-ttu-id="4d113-103">Cet exemple montre comment implémenter un validateur UserNamePassword personnalisé.</span><span class="sxs-lookup"><span data-stu-id="4d113-103">This sample demonstrates how to implement a custom UserNamePassword Validator.</span></span> <span data-ttu-id="4d113-104">Cela s’avère utile dans les cas où aucun des modes de validation UserNamePassword intégrés ne convient aux exigences de l’application ; par exemple, lorsque les paires nom d’utilisateur/mot de passe sont stockées dans quelque magasin externe, tel qu’une base de données.</span><span class="sxs-lookup"><span data-stu-id="4d113-104">This is useful in cases where none of the built-in UserNamePassword Validation modes is appropriate for the requirements of the application; for example, when username/password pairs are stored in some external store, such as a database.</span></span> <span data-ttu-id="4d113-105">Cet exemple illustre un service qui comprend un validateur personnalisé qui vérifie pour deux paires nom d'utilisateur/mot de passe particulières.</span><span class="sxs-lookup"><span data-stu-id="4d113-105">This sample shows a service that has a custom validator that checks for two particular username/password pairs.</span></span> <span data-ttu-id="4d113-106">Le client utilise une paire nom d'utilisateur/mot de passe pour s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="4d113-106">The client uses such a username/password pair to authenticate to the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4d113-107">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4d113-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4d113-108">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="4d113-108">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="4d113-109">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="4d113-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4d113-110">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="4d113-110">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Security\UserNamePasswordValidator`  
  
> [!NOTE]
> <span data-ttu-id="4d113-111">Étant donné que n'importe qui peut générer une information d'identification de nom d'utilisateur qui utilise les paires nom d'utilisateur/mot de passe acceptées par le validateur personnalisé, le service est moins sécurisé que le comportement par défaut fourni par le validateur UserNamePassword standard.</span><span class="sxs-lookup"><span data-stu-id="4d113-111">Because anyone can construct a Username credential that uses the username/password pairs that the custom validator accepts, the service is less secure than the default behavior provided by the standard UserNamePassword Validator.</span></span> <span data-ttu-id="4d113-112">Le validateur UserNamePassword standard essaie de mapper la paire nom d'utilisateur/mot de passe fournie à un compte Windows et fait échouer l'authentification si ce mappage échoue.</span><span class="sxs-lookup"><span data-stu-id="4d113-112">The standard UserNamePassword Validator attempts to map the provided username/password pair to a Windows account and fails authentication if this mapping fails.</span></span> <span data-ttu-id="4d113-113">Le validateur UserNamePassword personnalisé dans cet exemple NE DOIT PAS être utilisé dans le code de production ; il est fourni à titre d'illustration uniquement.</span><span class="sxs-lookup"><span data-stu-id="4d113-113">The custom UserNamePassword Validator in this sample MUST NOT be used in production code, it is for illustration purposes only.</span></span>

 <span data-ttu-id="4d113-114">En résumé, cet exemple montre comment :</span><span class="sxs-lookup"><span data-stu-id="4d113-114">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="4d113-115">Le client peut être authentifié à l'aide d'un jeton de nom d'utilisateur ;</span><span class="sxs-lookup"><span data-stu-id="4d113-115">The client can be authenticated using a Username Token.</span></span>

- <span data-ttu-id="4d113-116">Le serveur valide les informations d’identification du client à l’aide d’un UserNamePasswordValidator personnalisé et comment propager les erreurs personnalisées de la logique de validation du nom d’utilisateur et du mot de passe au client ;</span><span class="sxs-lookup"><span data-stu-id="4d113-116">The server validates the client credentials against a custom UserNamePasswordValidator and how to propagate custom faults from the username and password validation logic to the client.</span></span>

- <span data-ttu-id="4d113-117">Le serveur est authentifié à l'aide du certificat X.509 du serveur.</span><span class="sxs-lookup"><span data-stu-id="4d113-117">The server is authenticated using the server's X.509 certificate.</span></span>

 <span data-ttu-id="4d113-118">Le service expose un point de terminaison unique pour communiquer avec le service, défini à l’aide du fichier de configuration App.config. Le point de terminaison se compose d’une adresse, d’une liaison et d’un contrat.</span><span class="sxs-lookup"><span data-stu-id="4d113-118">The service exposes a single endpoint for communicating with the service, defined using the configuration file, App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="4d113-119">La liaison est configurée avec une norme `wsHttpBinding` qui utilise par défaut l’authentification WS-Security et de nom d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="4d113-119">The binding is configured with a standard `wsHttpBinding` that defaults to using WS-Security and username authentication.</span></span> <span data-ttu-id="4d113-120">Le comportement de service spécifie le mode `Custom` pour valider les paires nom d'utilisateur/mot de passe du client avec le type de la classe de validateur.</span><span class="sxs-lookup"><span data-stu-id="4d113-120">The service behavior specifies the `Custom` mode for validating client username/password pairs along with the type of the validator class.</span></span> <span data-ttu-id="4d113-121">Le comportement spécifie également le certificat de serveur à l'aide de l'élément `serviceCertificate`.</span><span class="sxs-lookup"><span data-stu-id="4d113-121">The behavior also specifies the server certificate using the `serviceCertificate` element.</span></span> <span data-ttu-id="4d113-122">Le certificat de serveur doit contenir la même valeur pour le `SubjectName` que le `findValue` dans le [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="4d113-122">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

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

 <span data-ttu-id="4d113-123">La configuration de point de terminaison de client se compose d’un nom de configuration, d’une adresse absolue pour le point de terminaison de service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="4d113-123">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="4d113-124">La liaison de client est configurée avec le mode et le message `clientCredentialType` appropriés.</span><span class="sxs-lookup"><span data-stu-id="4d113-124">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

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

 <span data-ttu-id="4d113-125">L'implémentation cliente invite l'utilisateur à entrer un nom d'utilisateur et un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="4d113-125">The client implementation prompts the user to enter a username and password.</span></span>

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

 <span data-ttu-id="4d113-126">Cet exemple utilise un UserNamePasswordValidator personnalisé pour valider des paires nom d'utilisateur/mot de passe.</span><span class="sxs-lookup"><span data-stu-id="4d113-126">This sample uses a custom UserNamePasswordValidator to validate username/password pairs.</span></span> <span data-ttu-id="4d113-127">L'exemple implémente `CustomUserNamePasswordValidator`, dérivé de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="4d113-127">The sample implements `CustomUserNamePasswordValidator`, derived from <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span></span> <span data-ttu-id="4d113-128">Pour plus d'informations, consultez la documentation de <xref:System.IdentityModel.Selectors.UserNamePasswordValidator>.</span><span class="sxs-lookup"><span data-stu-id="4d113-128">See the documentation for <xref:System.IdentityModel.Selectors.UserNamePasswordValidator> for more information.</span></span> <span data-ttu-id="4d113-129">Cet exemple de validateur personnalisé particulier implémente la méthode `Validate` pour accepter deux paires nom d'utilisateur/mot de passe particulières, comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d113-129">This particular custom validator sample implements the `Validate` method to accept two particular username/password pairs as shown in the following code.</span></span>

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

 <span data-ttu-id="4d113-130">Une fois que le validateur est implémenté dans le code de service, l'hôte de service doit être informé de l'instance de validateur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4d113-130">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="4d113-131">Cela est effectué à l'aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="4d113-131">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.UserNameAuthentication.UserNamePasswordValidationMode = UserNamePasswordValidationMode.Custom;
serviceHost.Credentials. UserNameAuthentication.CustomUserNamePasswordValidator = new CustomUserNamePasswordValidator();
```

 <span data-ttu-id="4d113-132">Vous pouvez faire la même chose dans la configuration comme suit.</span><span class="sxs-lookup"><span data-stu-id="4d113-132">Or you can do the same thing in configuration as follows.</span></span>

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

 <span data-ttu-id="4d113-133">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="4d113-133">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="4d113-134">Le client doit appeler toutes les méthodes avec succès.</span><span class="sxs-lookup"><span data-stu-id="4d113-134">The client should successfully call all the methods.</span></span> <span data-ttu-id="4d113-135">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="4d113-135">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="4d113-136">Fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="4d113-136">Setup Batch File</span></span>

 <span data-ttu-id="4d113-137">Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec les certificats pertinents pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="4d113-137">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="4d113-138">Ce fichier doit être modifié pour fonctionner sur plusieurs ordinateurs ou dans un cas non hébergé.</span><span class="sxs-lookup"><span data-stu-id="4d113-138">This batch file must be modified to work across machines or to work in a non-self-hosted case.</span></span>

 <span data-ttu-id="4d113-139">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.</span><span class="sxs-lookup"><span data-stu-id="4d113-139">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>

- <span data-ttu-id="4d113-140">Création du certificat de serveur :</span><span class="sxs-lookup"><span data-stu-id="4d113-140">Creating the server certificate:</span></span>

     <span data-ttu-id="4d113-141">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="4d113-141">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="4d113-142">La variable %SERVER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="4d113-142">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="4d113-143">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="4d113-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="4d113-144">La valeur par défaut est localhost.</span><span class="sxs-lookup"><span data-stu-id="4d113-144">The default value is localhost.</span></span>

    ```console
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="4d113-145">Installation du certificat de serveur dans le magasin de certificats approuvés du client :</span><span class="sxs-lookup"><span data-stu-id="4d113-145">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="4d113-146">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="4d113-146">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="4d113-147">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="4d113-147">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="4d113-148">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="4d113-148">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="4d113-149">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="4d113-149">To set up and build the sample</span></span>

1. <span data-ttu-id="4d113-150">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4d113-150">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="4d113-151">Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, utilisez les instructions suivantes.</span><span class="sxs-lookup"><span data-stu-id="4d113-151">To run the sample in a single- or cross-machine configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="4d113-152">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="4d113-152">To run the sample on the same machine</span></span>

1. <span data-ttu-id="4d113-153">Exécutez Setup.bat à partir du dossier d’installation de l’exemple à l’intérieur d’une invite de commandes Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="4d113-153">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt.</span></span> <span data-ttu-id="4d113-154">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="4d113-154">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4d113-155">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="4d113-155">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="4d113-156">La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="4d113-156">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="4d113-157">Lancez Service.exe à partir de service\bin.</span><span class="sxs-lookup"><span data-stu-id="4d113-157">Launch Service.exe from service\bin.</span></span>  
  
3. <span data-ttu-id="4d113-158">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="4d113-158">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="4d113-159">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="4d113-159">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="4d113-160">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4d113-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="4d113-161">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="4d113-161">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="4d113-162">Créez un répertoire sur l'ordinateur de service destiné aux fichiers binaires de service.</span><span class="sxs-lookup"><span data-stu-id="4d113-162">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="4d113-163">Copiez les fichiers programme du service dans le répertoire de service sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="4d113-163">Copy the service program files the service directory on the service machine.</span></span> <span data-ttu-id="4d113-164">Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="4d113-164">Also copy the Setup.bat and Cleanup.bat files to the service machine.</span></span>  
  
3. <span data-ttu-id="4d113-165">Il vous faut un certificat de serveur dont le nom du sujet contient le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="4d113-165">You need a server certificate with the subject name that contains the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="4d113-166">Le fichier de configuration pour le serveur doit être mis à jour pour refléter ce nouveau nom de certificat.</span><span class="sxs-lookup"><span data-stu-id="4d113-166">The configuration file for the server must be updated to reflect this new certificate name.</span></span>  
  
4. <span data-ttu-id="4d113-167">Copiez le certificat de serveur dans le magasin CurrentUser-TrustedPeople du client.</span><span class="sxs-lookup"><span data-stu-id="4d113-167">Copy the server certificate into the CurrentUser-TrustedPeople store of the client.</span></span> <span data-ttu-id="4d113-168">Cette tâche est requise uniquement si le certificat du serveur n'est pas publié par un émetteur approuvé.</span><span class="sxs-lookup"><span data-stu-id="4d113-168">You need to do this only if the server certificate is not issued by a trusted issuer.</span></span>  
  
5. <span data-ttu-id="4d113-169">Dans le fichier App.config sur l'ordinateur de service, modifiez la valeur de l'adresse de base afin de remplacer localhost par un nom d'ordinateur complet.</span><span class="sxs-lookup"><span data-stu-id="4d113-169">In the App.config file on the service machine, change the value of the base address to specify a fully-qualified machine name instead of localhost.</span></span>  
  
6. <span data-ttu-id="4d113-170">Sur l'ordinateur de service, lancez Service.exe à partir d'une fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="4d113-170">On the service machine, launch Service.exe from a command prompt window.</span></span>  
  
7. <span data-ttu-id="4d113-171">Copiez les fichiers programme du client du dossier \client\bin\ (situé dans le dossier correspondant à votre langue) sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="4d113-171">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client machine.</span></span>  
  
8. <span data-ttu-id="4d113-172">Dans le fichier Client.exe.config sur l'ordinateur client, modifiez la valeur d'adresse du point de terminaison pour qu'il corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="4d113-172">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="4d113-173">Sur l'ordinateur du client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="4d113-173">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
10. <span data-ttu-id="4d113-174">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="4d113-174">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="4d113-175">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="4d113-175">To clean up after the sample</span></span>  
  
1. <span data-ttu-id="4d113-176">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="4d113-176">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="4d113-177">Cela supprime le certificat de serveur du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="4d113-177">This removes the server certificate from the certificate store.</span></span>
