---
title: X.509 Certificate Validator
ms.date: 03/30/2017
ms.assetid: 3b042379-02c4-4395-b927-e57c842fd3e0
ms.openlocfilehash: 2d117dda8e6748407b6d58677ec55e4e8e4e4740
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90554239"
---
# <a name="x509-certificate-validator"></a><span data-ttu-id="394fb-102">X.509 Certificate Validator</span><span class="sxs-lookup"><span data-stu-id="394fb-102">X.509 Certificate Validator</span></span>

<span data-ttu-id="394fb-103">Cet exemple montre comment implémenter un validateur de certificat X.509 personnalisé.</span><span class="sxs-lookup"><span data-stu-id="394fb-103">This sample demonstrates how to implement a custom X.509 Certificate Validator.</span></span> <span data-ttu-id="394fb-104">Cela s’avère utile dans les cas où aucun des modes de validation de certificat X.509 intégrés ne convient aux spécifications de l’application.</span><span class="sxs-lookup"><span data-stu-id="394fb-104">This is useful in cases where none of the built-in X.509 Certificate Validation modes is appropriate for the requirements of the application.</span></span> <span data-ttu-id="394fb-105">Cet exemple illustre un service qui possède un validateur personnalisé qui accepte les certificats auto-émis.</span><span class="sxs-lookup"><span data-stu-id="394fb-105">This sample shows a service that has a custom validator that accepts self-issued certificates.</span></span> <span data-ttu-id="394fb-106">Le client utilise un certificat X.509 pour s'authentifier auprès du service.</span><span class="sxs-lookup"><span data-stu-id="394fb-106">The client uses such a certificate to authenticate to the service.</span></span>

<span data-ttu-id="394fb-107">Remarque : comme n'importe qui peut généré un certificat auto-émis, le validateur personnalisé utilisé par le service est moins sécurisé que le comportement par défaut fourni par le mode de validation ChainTrust X509CertificateValidationMode.</span><span class="sxs-lookup"><span data-stu-id="394fb-107">Note: As anyone can construct a self-issued certificate the custom validator used by the service is less secure than the default behavior provided by the ChainTrust X509CertificateValidationMode.</span></span> <span data-ttu-id="394fb-108">Les implications en termes de sécurité doivent être soigneusement étudiées avant d’utiliser cette logique de validation dans le code de production.</span><span class="sxs-lookup"><span data-stu-id="394fb-108">The security implications of this should be carefully considered before using this validation logic in production code.</span></span>

<span data-ttu-id="394fb-109">En résumé, cet exemple montre comment :</span><span class="sxs-lookup"><span data-stu-id="394fb-109">In summary this sample demonstrates how:</span></span>

- <span data-ttu-id="394fb-110">Le client peut être authentifié à l'aide d'un certificat X.509 ;</span><span class="sxs-lookup"><span data-stu-id="394fb-110">The client can be authenticated using an X.509 certificate.</span></span>

- <span data-ttu-id="394fb-111">Le serveur valide les informations d'identification du client en fonction d'un X509CertificateValidator personnalisé ;</span><span class="sxs-lookup"><span data-stu-id="394fb-111">The server validates the client credentials against a custom X509CertificateValidator.</span></span>

- <span data-ttu-id="394fb-112">Le serveur est authentifié à l'aide du certificat X.509 du serveur.</span><span class="sxs-lookup"><span data-stu-id="394fb-112">The server is authenticated using the server's X.509 certificate.</span></span>

<span data-ttu-id="394fb-113">Le service expose un point de terminaison unique pour communiquer avec le service, défini à l’aide du fichier de configuration App.config. Le point de terminaison se compose d’une adresse, d’une liaison et d’un contrat.</span><span class="sxs-lookup"><span data-stu-id="394fb-113">The service exposes a single endpoint for communicating with the service, defined using the configuration file App.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="394fb-114">La liaison est configurée avec une norme `wsHttpBinding` qui utilise par défaut `WSSecurity` et l’authentification par certificat client.</span><span class="sxs-lookup"><span data-stu-id="394fb-114">The binding is configured with a standard `wsHttpBinding` that defaults to using `WSSecurity` and client certificate authentication.</span></span> <span data-ttu-id="394fb-115">Le comportement de service spécifie le mode personnalisé de validation des certificats clients X.509 ainsi que le type de classe du validateur.</span><span class="sxs-lookup"><span data-stu-id="394fb-115">The service behavior specifies the Custom mode for validating client X.509 certificates along with the type of the validator class.</span></span> <span data-ttu-id="394fb-116">Le comportement spécifie également le certificat de serveur à l'aide de l'élément serviceCertificate.</span><span class="sxs-lookup"><span data-stu-id="394fb-116">The behavior also specifies the server certificate using the serviceCertificate element.</span></span> <span data-ttu-id="394fb-117">Le certificat de serveur doit contenir la même valeur pour le `SubjectName` que le `findValue` dans le [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) .</span><span class="sxs-lookup"><span data-stu-id="394fb-117">The server certificate has to contain the same value for the `SubjectName` as the `findValue` in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>

```xml
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- use host/baseAddresses to configure base address -->
        <!-- provided by host -->
        <host>
          <baseAddresses>
            <add baseAddress =
                "http://localhost:8001/servicemodelsamples/service" />
          </baseAddresses>
        </host>
        <!-- use base address specified above, provide one endpoint -->
        <endpoint address="certificate"
               binding="wsHttpBinding"
               bindingConfiguration="Binding"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <!-- X509 certificate binding -->
        <binding name="Binding">
          <security mode="Message">
            <message clientCredentialType="Certificate" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceDebug includeExceptionDetailInFaults ="true"/>
          <serviceCredentials>
            <!-- The serviceCredentials behavior allows one -->
            <!-- to specify authentication constraints on -->
            <!-- client certificates. -->
            <clientCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- Custom means that if the custom -->
              <!-- X509CertificateValidator does NOT throw -->
              <!-- an exception, then the provided certificate -->
              <!-- will be trusted without performing any -->
              <!-- validation beyond that performed by the custom -->
              <!-- validator. The security implications of this -->
              <!-- setting should be carefully considered before -->
              <!-- using Custom in production code. -->
              <authentication
                 certificateValidationMode="Custom"
                 customCertificateValidatorType =
"Microsoft.ServiceModel.Samples.CustomX509CertificateValidator, service" />
            </clientCertificate>
            <!-- The serviceCredentials behavior allows one to -->
            <!-- define a service certificate. -->
            <!-- A service certificate is used by a client to -->
            <!-- authenticate the service and provide message -->
            <!-- protection. This configuration references the -->
            <!-- "localhost" certificate installed during the setup -->
            <!-- instructions. -->
            <serviceCertificate findValue="localhost"
                 storeLocation="LocalMachine"
                 storeName="My" x509FindType="FindBySubjectName" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
      </system.serviceModel>
```

<span data-ttu-id="394fb-118">La configuration de point de terminaison de client se compose d’un nom de configuration, d’une adresse absolue pour le point de terminaison de service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="394fb-118">The client endpoint configuration consists of a configuration name, an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="394fb-119">La liaison de client est configurée avec le mode et le message `clientCredentialType` appropriés.</span><span class="sxs-lookup"><span data-stu-id="394fb-119">The client binding is configured with the appropriate mode and message `clientCredentialType`.</span></span>

```xml
<system.serviceModel>
    <client>
      <!-- X509 certificate based endpoint -->
      <endpoint name="Certificate"
        address=
        "http://localhost:8001/servicemodelsamples/service/certificate"
                binding="wsHttpBinding"
                bindingConfiguration="Binding"
                behaviorConfiguration="ClientCertificateBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator">
      </endpoint>
    </client>
    <bindings>
        <wsHttpBinding>
            <!-- X509 certificate binding -->
            <binding name="Binding">
                <security mode="Message">
                    <message clientCredentialType="Certificate" />
               </security>
            </binding>
       </wsHttpBinding>
    </bindings>
    <behaviors>
      <endpointBehaviors>
        <behavior name="ClientCertificateBehavior">
          <clientCredentials>
            <serviceCertificate>
              <!-- Setting the certificateValidationMode to -->
              <!-- PeerOrChainTrust means that if the certificate -->
              <!-- is in the user's Trusted People store, then it -->
              <!-- is trusted without performing a validation of -->
              <!-- the certificate's issuer chain. -->
              <!-- This setting is used here for convenience so -->
              <!-- that the sample can be run without having to -->
              <!-- have certificates issued by a certification -->
              <!-- authority (CA). This setting is less secure -->
              <!-- than the default, ChainTrust. The security -->
              <!-- implications of this setting should be -->
              <!-- carefully considered before using -->
              <!-- PeerOrChainTrust in production code.-->
              <authentication
                  certificateValidationMode="PeerOrChainTrust" />
            </serviceCertificate>
          </clientCredentials>
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>
```

<span data-ttu-id="394fb-120">L'implémentation cliente définit le certificat client à utiliser.</span><span class="sxs-lookup"><span data-stu-id="394fb-120">The client implementation sets the client certificate to use.</span></span>

```csharp
// Create a client with Certificate endpoint configuration
CalculatorClient client = new CalculatorClient("Certificate");
try
{
    client.ClientCredentials.ClientCertificate.SetCertificate(StoreLocation.CurrentUser, StoreName.My, X509FindType.FindBySubjectName, "test1");

    // Call the Add service operation.
    double value1 = 100.00D;
    double value2 = 15.99D;
    double result = client.Add(value1, value2);
    Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

    // Call the Subtract service operation.
    value1 = 145.00D;
    value2 = 76.54D;
    result = client.Subtract(value1, value2);
    Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);

    // Call the Multiply service operation.
    value1 = 9.00D;
    value2 = 81.25D;
    result = client.Multiply(value1, value2);
    Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);

    // Call the Divide service operation.
    value1 = 22.00D;
    value2 = 7.00D;
    result = client.Divide(value1, value2);
    Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);
    client.Close();
}
catch (TimeoutException e)
{
    Console.WriteLine("Call timed out : {0}", e.Message);
    client.Abort();
}
catch (CommunicationException e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
catch (Exception e)
{
    Console.WriteLine("Call failed : {0}", e.Message);
    client.Abort();
}
```

<span data-ttu-id="394fb-121">Cet exemple utilise un X509CertificateValidator personnalisé pour valider des certificats.</span><span class="sxs-lookup"><span data-stu-id="394fb-121">This sample uses a custom X509CertificateValidator to validate certificates.</span></span> <span data-ttu-id="394fb-122">L'exemple implémente CustomX509CertificateValidator, dérivé de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="394fb-122">The sample implements CustomX509CertificateValidator, derived from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="394fb-123">Pour plus d'informations, consultez la documentation <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="394fb-123">See documentation about <xref:System.IdentityModel.Selectors.X509CertificateValidator> for more information.</span></span> <span data-ttu-id="394fb-124">Cet exemple de validateur personnalisé particulier implémente la méthode Validate pour accepter tout certificat X.509 auto-émis comme le montre le code suivant.</span><span class="sxs-lookup"><span data-stu-id="394fb-124">This particular custom validator sample implements the Validate method to accept any X.509 certificate that is self-issued as shown in the following code.</span></span>

```csharp
public class CustomX509CertificateValidator : X509CertificateValidator
{
  public override void Validate ( X509Certificate2 certificate )
  {
   // Only accept self-issued certificates
   if (certificate.Subject != certificate.Issuer)
     throw new Exception("Certificate is not self-issued");
   }
}
```

 <span data-ttu-id="394fb-125">Une fois que le validateur est implémenté dans le code de service, l'hôte de service doit être informé de l'instance de validateur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="394fb-125">Once the validator is implemented in service code, the service host must be informed about the validator instance to use.</span></span> <span data-ttu-id="394fb-126">Cela est effectué à l'aide du code suivant.</span><span class="sxs-lookup"><span data-stu-id="394fb-126">This is done using the following code.</span></span>

```csharp
serviceHost.Credentials.ClientCertificate.Authentication.CertificateValidationMode = X509CertificateValidationMode.Custom;
serviceHost.Credentials.ClientCertificate.Authentication.CustomCertificateValidator = new CustomX509CertificateValidator();
```

 <span data-ttu-id="394fb-127">Vous pouvez faire la même chose dans la configuration comme suit.</span><span class="sxs-lookup"><span data-stu-id="394fb-127">Or you can do the same thing in configuration as follows.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
     <behavior name="CalculatorServiceBehavior">
       ...
   <serviceCredentials>
    <!--The serviceCredentials behavior allows one to specify -->
    <!--authentication constraints on client certificates.-->
    <clientCertificate>
    <!-- Setting the certificateValidationMode to Custom means -->
    <!--that if the custom X509CertificateValidator does NOT -->
    <!--throw an exception, then the provided certificate will -->
    <!--be trusted without performing any validation beyond that -->
    <!--performed by the custom validator. The security -->
    <!--implications of this setting should be carefully -->
    <!--considered before using Custom in production code. -->
    <authentication certificateValidationMode="Custom"
       customCertificateValidatorType =
"Microsoft.ServiceModel.Samples. CustomX509CertificateValidator, service" />
   </clientCertificate>
   </serviceCredentials>
   ...
  </behavior>
 </serviceBehaviors>
</behaviors>
```

<span data-ttu-id="394fb-128">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="394fb-128">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="394fb-129">Le client doit appeler toutes les méthodes avec succès.</span><span class="sxs-lookup"><span data-stu-id="394fb-129">The client should successfully call all the methods.</span></span> <span data-ttu-id="394fb-130">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="394fb-130">Press ENTER in the client window to shut down the client.</span></span>

## <a name="setup-batch-file"></a><span data-ttu-id="394fb-131">Fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="394fb-131">Setup Batch File</span></span>

<span data-ttu-id="394fb-132">Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec les certificats pertinents pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="394fb-132">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="394fb-133">Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.</span><span class="sxs-lookup"><span data-stu-id="394fb-133">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

<span data-ttu-id="394fb-134">Les éléments suivants fournissent une brève vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée :</span><span class="sxs-lookup"><span data-stu-id="394fb-134">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="394fb-135">Création du certificat de serveur :</span><span class="sxs-lookup"><span data-stu-id="394fb-135">Creating the server certificate:</span></span>

     <span data-ttu-id="394fb-136">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="394fb-136">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="394fb-137">La variable %SERVER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="394fb-137">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="394fb-138">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="394fb-138">Change this variable to specify your own server name.</span></span> <span data-ttu-id="394fb-139">La valeur par défaut est localhost.</span><span class="sxs-lookup"><span data-stu-id="394fb-139">The default value is localhost.</span></span>

    ```bash
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="394fb-140">Installation du certificat de serveur dans le magasin de certificats approuvés du client :</span><span class="sxs-lookup"><span data-stu-id="394fb-140">Installing the server certificate into client's trusted certificate store:</span></span>

     <span data-ttu-id="394fb-141">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="394fb-141">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="394fb-142">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="394fb-142">This step is required since certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="394fb-143">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats client avec le certificat de serveur n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="394fb-143">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="394fb-144">Création du certificat client :</span><span class="sxs-lookup"><span data-stu-id="394fb-144">Creating the client certificate:</span></span>

     <span data-ttu-id="394fb-145">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat client à utiliser.</span><span class="sxs-lookup"><span data-stu-id="394fb-145">The following lines from the Setup.bat batch file create the client certificate to be used.</span></span> <span data-ttu-id="394fb-146">La variable % USER_NAME% spécifie le nom du client.</span><span class="sxs-lookup"><span data-stu-id="394fb-146">The %USER_NAME% variable specifies the client name.</span></span> <span data-ttu-id="394fb-147">Cette valeur est « test1 » parce que c'est le nom que le code client recherche.</span><span class="sxs-lookup"><span data-stu-id="394fb-147">This value is set to "test1" because this is the name the client code looks for.</span></span> <span data-ttu-id="394fb-148">Si vous modifiez la valeur de % USER_NAME%, vous devez modifier la valeur correspondante dans le fichier source Client.cs et reconstruire le client.</span><span class="sxs-lookup"><span data-stu-id="394fb-148">If you change the value of %USER_NAME% you must change the corresponding value in the Client.cs source file and rebuild the client.</span></span>

     <span data-ttu-id="394fb-149">Le certificat est stocké dans le magasin My (Personal) sous l'emplacement de magasin CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="394fb-149">The certificate is stored in My (Personal) store under the CurrentUser store location.</span></span>

    ```bash
    echo ************
    echo Client cert setup starting
    echo %USER_NAME%
    echo ************
    echo making client cert
    echo ************
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%USER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="394fb-150">Installation du certificat client dans le magasin de certificats approuvés du serveur :</span><span class="sxs-lookup"><span data-stu-id="394fb-150">Installing the client certificate into server's trusted certificate store:</span></span>

     <span data-ttu-id="394fb-151">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat client dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="394fb-151">The following lines in the Setup.bat batch file copy the client certificate into the trusted people store.</span></span> <span data-ttu-id="394fb-152">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système du serveur.</span><span class="sxs-lookup"><span data-stu-id="394fb-152">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the server system.</span></span> <span data-ttu-id="394fb-153">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple un certificat émis par Microsoft, cette étape de remplissage du magasin de certificats du serveur avec le certificat client n'est pas requise.</span><span class="sxs-lookup"><span data-stu-id="394fb-153">If you already have a certificate that is rooted in a trusted root certificate—for example, a Microsoft issued certificate—this step of populating the server certificate store with the client certificate is not required.</span></span>

    ```bash
    certmgr.exe -add -r CurrentUser -s My -c -n %USER_NAME% -r LocalMachine -s TrustedPeople
    ```

#### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="394fb-154">Pour configurer et générer l'exemple</span><span class="sxs-lookup"><span data-stu-id="394fb-154">To set up and build the sample</span></span>

1. <span data-ttu-id="394fb-155">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="394fb-155">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

2. <span data-ttu-id="394fb-156">Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="394fb-156">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>

#### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="394fb-157">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="394fb-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="394fb-158">Exécutez Setup.bat à partir du dossier d’installation de l’exemple à l’aide d’une invite de commandes Visual Studio 2012 ouverte avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="394fb-158">Run Setup.bat from the sample install folder inside a Visual Studio 2012 command prompt opened with administrator privileges.</span></span> <span data-ttu-id="394fb-159">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="394fb-159">This installs all the certificates required for running the sample.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="394fb-160">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’une invite de commandes de Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="394fb-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="394fb-161">La variable d’environnement PATH définie dans l’invite de commandes de Visual Studio 2012 pointe vers le répertoire qui contient les exécutables requis par le script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="394fb-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>

2. <span data-ttu-id="394fb-162">Lancez Service.exe à partir de service\bin.</span><span class="sxs-lookup"><span data-stu-id="394fb-162">Launch Service.exe from service\bin.</span></span>

3. <span data-ttu-id="394fb-163">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="394fb-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="394fb-164">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="394fb-164">Client activity is displayed on the client console application.</span></span>

4. <span data-ttu-id="394fb-165">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="394fb-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="394fb-166">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="394fb-166">To run the sample across computers</span></span>

1. <span data-ttu-id="394fb-167">Créez un répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="394fb-167">Create a directory on the service computer.</span></span>

2. <span data-ttu-id="394fb-168">Copiez les fichiers programme du service de \service\bin vers le répertoire virtuel sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="394fb-168">Copy the service program files from \service\bin to the virtual directory on the service computer.</span></span> <span data-ttu-id="394fb-169">Copiez également les fichiers Setup.bat, Cleanup.bat, GetComputerName.vbs et ImportClientCert.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="394fb-169">Also copy the Setup.bat, Cleanup.bat, GetComputerName.vbs and ImportClientCert.bat files to the service computer.</span></span>

3. <span data-ttu-id="394fb-170">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="394fb-170">Create a directory on the client computer for the client binaries.</span></span>

4. <span data-ttu-id="394fb-171">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="394fb-171">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="394fb-172">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="394fb-172">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>

5. <span data-ttu-id="394fb-173">Sur le serveur, exécutez `setup.bat service` dans un invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="394fb-173">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="394fb-174">`setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.</span><span class="sxs-lookup"><span data-stu-id="394fb-174">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>

6. <span data-ttu-id="394fb-175">Modifiez Service.exe.config pour refléter le nouveau nom de certificat (dans l' `findValue` attribut dans [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="394fb-175">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="394fb-176">Remplacez également le nom de l’ordinateur localhost par localhost par le \<service> / \<baseAddresses> nom complet de votre ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="394fb-176">Also change the computer name in the \<service>/\<baseAddresses> element from localhost to fully qualified name of your service computer.</span></span>

7. <span data-ttu-id="394fb-177">Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="394fb-177">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>

8. <span data-ttu-id="394fb-178">Sur le client, exécutez `setup.bat client` dans un invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="394fb-178">On the client, run `setup.bat client` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="394fb-179">L'exécution de `setup.bat` à l'aide de l'argument `client` crée un certificat client appelé client.com, puis exporte ce certificat vers un fichier nommé Client.cer.</span><span class="sxs-lookup"><span data-stu-id="394fb-179">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>

9. <span data-ttu-id="394fb-180">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="394fb-180">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="394fb-181">Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="394fb-181">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>

10. <span data-ttu-id="394fb-182">Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="394fb-182">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>

11. <span data-ttu-id="394fb-183">Sur le client, exécutez ImportServiceCert.bat dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="394fb-183">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="394fb-184">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="394fb-184">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>

12. <span data-ttu-id="394fb-185">Sur le serveur, exécutez ImportClientCert.bat dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="394fb-185">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="394fb-186">Le certificat client est ainsi importé à partir du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="394fb-186">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>

13. <span data-ttu-id="394fb-187">Sur l'ordinateur serveur, lancez Service.exe à partir de la fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="394fb-187">On the server computer, launch Service.exe from the command prompt window.</span></span>

14. <span data-ttu-id="394fb-188">Sur l'ordinateur client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="394fb-188">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="394fb-189">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="394fb-189">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>

#### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="394fb-190">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="394fb-190">To clean up after the sample</span></span>

1. <span data-ttu-id="394fb-191">Exécutez Cleanup.bat dans le dossier d'exemples après avoir exécuté l'exemple.</span><span class="sxs-lookup"><span data-stu-id="394fb-191">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span> <span data-ttu-id="394fb-192">Cela supprime les certificats du serveur et du client du magasin de certificats.</span><span class="sxs-lookup"><span data-stu-id="394fb-192">This removes the server and client certificates from the certificate store.</span></span>

> [!NOTE]
> <span data-ttu-id="394fb-193">Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="394fb-193">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="394fb-194">Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="394fb-194">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="394fb-195">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="394fb-195">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
