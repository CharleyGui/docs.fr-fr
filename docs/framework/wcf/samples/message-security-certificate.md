---
title: Message Security Certificate
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: 909333b3-35ec-48f0-baff-9a50161896f6
ms.openlocfilehash: 164a939fa7ee0112e1ceae24755854b09dc72603
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283989"
---
# <a name="message-security-certificate"></a><span data-ttu-id="20efa-102">Message Security Certificate</span><span class="sxs-lookup"><span data-stu-id="20efa-102">Message Security Certificate</span></span>

<span data-ttu-id="20efa-103">Cet exemple montre comment implémenter une application qui utilise WS-Security avec l'authentification de certificat X.509 v3 pour le client et requiert l'authentification de serveur à l'aide du certificat X.509 v3 du serveur.</span><span class="sxs-lookup"><span data-stu-id="20efa-103">This sample demonstrates how to implement an application that uses WS-Security with X.509 v3 certificate authentication for the client and requires server authentication using the server's X.509 v3 certificate.</span></span> <span data-ttu-id="20efa-104">Il utilise des paramètres par défaut de sorte que tous les messages d'application entre le client et le serveur soient signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="20efa-104">This sample uses default settings such that all application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="20efa-105">Cet exemple est basé sur [WSHttpBinding](wshttpbinding.md) et se compose d’un programme de console client et d’une bibliothèque de service hébergée par Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="20efa-105">This sample is based on the [WSHttpBinding](wshttpbinding.md) and consists of a client console program and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="20efa-106">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="20efa-106">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20efa-107">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="20efa-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="20efa-108">L'exemple montre comment contrôler l'authentification à l'aide de la configuration et comment obtenir l'identité de l'appelant à partir du contexte de sécurité, tel qu'indiqué dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="20efa-108">The sample demonstrates controlling authentication by using configuration and how to obtain the caller’s identity from the security context, as shown in the following sample code.</span></span>  

```csharp
public class CalculatorService : ICalculator  
{  
    public string GetCallerIdentity()  
    {  
        // The client certificate is not mapped to a Windows identity by default.  
        // ServiceSecurityContext.PrimaryIdentity is populated based on the information  
        // in the certificate that the client used to authenticate itself to the service.  
        return ServiceSecurityContext.Current.PrimaryIdentity.Name;  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="20efa-109">Le service expose un point de terminaison permettant de communiquer avec le service et un point de terminaison permettant d'exposer le document WSDL du service à l'aide du  protocole WS-MetadataExchange, défini à l'aide du fichier de configuration (Web.config).</span><span class="sxs-lookup"><span data-stu-id="20efa-109">The service exposes one endpoint for communicating with the service and one endpoint for exposing the service's WSDL document using the WS-MetadataExchange protocol, defined by using the configuration file (Web.config).</span></span> <span data-ttu-id="20efa-110">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="20efa-110">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="20efa-111">La liaison est configurée avec un [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) élément standard, qui utilise par défaut la sécurité de message.</span><span class="sxs-lookup"><span data-stu-id="20efa-111">The binding is configured with a standard [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) element, which defaults to using message security.</span></span> <span data-ttu-id="20efa-112">Cet exemple affecte Certificat à l'attribut `clientCredentialType` pour requérir l'authentification du client.</span><span class="sxs-lookup"><span data-stu-id="20efa-112">This sample sets the `clientCredentialType` attribute to Certificate to require client authentication.</span></span>  
  
```xml  
<system.serviceModel>  
    <protocolMapping>  
      <add scheme="http" binding="wsHttpBinding"/>  
    </protocolMapping>  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding>  
          <security mode ="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
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
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
```  
  
 <span data-ttu-id="20efa-113">Le comportement spécifie les informations d'identification du service utilisées lorsque le client authentifie le service.</span><span class="sxs-lookup"><span data-stu-id="20efa-113">The behavior specifies the service's credentials that are used when the client authenticates the service.</span></span> <span data-ttu-id="20efa-114">Le nom du sujet du certificat de serveur est spécifié dans l' `findValue` attribut de l' [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) élément.</span><span class="sxs-lookup"><span data-stu-id="20efa-114">The server certificate subject name is specified in the `findValue` attribute in the [\<serviceCredentials>](../../configure-apps/file-schema/wcf/servicecredentials.md) element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--   
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by the service to authenticate itself to its clients and to provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
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
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
```  
  
 <span data-ttu-id="20efa-115">La configuration du point de terminaison du client se compose d’une adresse absolue pour le point de terminaison du service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="20efa-115">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="20efa-116">La liaison cliente est configurée avec les modes de sécurité et d’authentification appropriés.</span><span class="sxs-lookup"><span data-stu-id="20efa-116">The client binding is configured with the appropriate security mode and authentication mode.</span></span> <span data-ttu-id="20efa-117">Lors de l'exécution sur plusieurs ordinateurs, assurez-vous que l'adresse de point de terminaison de service est modifiée en conséquence.</span><span class="sxs-lookup"><span data-stu-id="20efa-117">When running in a cross-computer scenario, ensure that the service endpoint address is changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
    <client>  
      <!-- Use a behavior to configure the client certificate to present to the service. -->  
      <endpoint address="http://localhost/servicemodelsamples/service.svc" binding="wsHttpBinding" bindingConfiguration="Binding1" behaviorConfiguration="ClientCertificateBehavior" contract="Microsoft.Samples.Certificate.ICalculator"/>  
    </client>  
  
    <bindings>  
      <wsHttpBinding>  
        <!--   
        This configuration defines the security mode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1">  
          <security mode="Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="20efa-118">L'implémentation cliente peut définir le certificat à utiliser, soit via le fichier de configuration, soit via le code.</span><span class="sxs-lookup"><span data-stu-id="20efa-118">The client implementation can set the certificate to use, either through the configuration file or through code.</span></span> <span data-ttu-id="20efa-119">L'exemple suivant montre comment définir le certificat à utiliser dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="20efa-119">The following sample shows how to set the certificate to use in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  ...  
  
<behaviors>  
      <endpointBehaviors>  
        <behavior name="ClientCertificateBehavior">  
          <!--   
        The clientCredentials behavior allows one to define a certificate to present to a service.  
        A certificate is used by a client to authenticate itself to the service and provide message integrity.  
        This configuration references the "client.com" certificate installed during the setup instructions.  
        -->  
          <clientCredentials>  
            <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName"/>  
            <serviceCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certificate authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust"/>  
            </serviceCertificate>  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
  
</system.serviceModel>  
```  
  
 <span data-ttu-id="20efa-120">L'exemple suivant montre comment appeler le service dans votre programme.</span><span class="sxs-lookup"><span data-stu-id="20efa-120">The following sample shows how to call the service in your program.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Call the GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```
  
 <span data-ttu-id="20efa-121">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="20efa-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="20efa-122">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="20efa-122">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
CN=client.com  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="20efa-123">Le fichier de commandes Setup.bat inclus avec les exemples Message Security vous permet de configurer le client et le serveur avec les certificats appropriés pour exécuter une application hébergée qui requiert la sécurité basée sur le certificat.</span><span class="sxs-lookup"><span data-stu-id="20efa-123">The Setup.bat batch file included with the Message Security samples enables you to configure the client and server with relevant certificates to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="20efa-124">Ce fichier peut être exécuté en trois modes.</span><span class="sxs-lookup"><span data-stu-id="20efa-124">The batch file can be run in three modes.</span></span> <span data-ttu-id="20efa-125">Pour exécuter en mode ordinateur unique, tapez **setup.bat** dans un invite de commandes développeur pour Visual Studio ; pour le mode de service, tapez **setup.bat service**; et pour le mode client, tapez **setup.bat client**.</span><span class="sxs-lookup"><span data-stu-id="20efa-125">To run in single-computer mode type **setup.bat** in a Developer Command Prompt for Visual Studio ; for service mode type **setup.bat service**; and for client mode type **setup.bat client**.</span></span> <span data-ttu-id="20efa-126">Lorsque vous exécutez l'exemple sur plusieurs ordinateurs, utilisez le mode client et serveur.</span><span class="sxs-lookup"><span data-stu-id="20efa-126">Use the client and server mode when running the sample across computers.</span></span> <span data-ttu-id="20efa-127">Pour plus d'informations, consultez la procédure d'installation figurant en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="20efa-127">See the setup procedure at the end of this topic for details.</span></span> <span data-ttu-id="20efa-128">Les éléments suivants fournissent une brève vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée :</span><span class="sxs-lookup"><span data-stu-id="20efa-128">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in appropriate configuration:</span></span>  
  
- <span data-ttu-id="20efa-129">Création du certificat client</span><span class="sxs-lookup"><span data-stu-id="20efa-129">Creating the client certificate.</span></span>  
  
     <span data-ttu-id="20efa-130">La ligne suivante du fichier de commandes crée le certificat client.</span><span class="sxs-lookup"><span data-stu-id="20efa-130">The following line in the batch file creates the client certificate.</span></span> <span data-ttu-id="20efa-131">Le nom client spécifié est utilisé dans le nom du sujet du certificat créé.</span><span class="sxs-lookup"><span data-stu-id="20efa-131">The client name specified is used in the subject name of the certificate created.</span></span> <span data-ttu-id="20efa-132">Le certificat est stocké dans le magasin `My` situé au niveau de l'emplacement de magasin `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="20efa-132">The certificate is stored in `My` store at the `CurrentUser` store location.</span></span>  
  
    ```bat
    echo ************  
    echo making client cert  
    echo ************  
    makecert.exe -sr CurrentUser -ss MY -a sha1 -n CN=%CLIENT_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="20efa-133">Installation du certificat client dans le magasin de certificats approuvés du serveur</span><span class="sxs-lookup"><span data-stu-id="20efa-133">Installing the client certificate into the server’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="20efa-134">La ligne suivante du fichier de commandes copie le certificat client dans le magasin TrustedPeople du serveur afin que le serveur puisse prendre les décisions d'approbation ou de non-approbation appropriées.</span><span class="sxs-lookup"><span data-stu-id="20efa-134">The following line in the batch file copies the client certificate into the server's TrustedPeople store so that the server can make the relevant trust or no-trust decisions.</span></span> <span data-ttu-id="20efa-135">Pour qu’un certificat installé dans le magasin TrustedPeople soit approuvé par un service Windows Communication Foundation (WCF), le mode de validation du certificat client doit avoir la valeur `PeerOrChainTrust` ou `PeerTrust` .</span><span class="sxs-lookup"><span data-stu-id="20efa-135">In order for a certificate installed in the TrustedPeople store to be trusted by a Windows Communication Foundation (WCF) service, the client certificate validation mode must be set to `PeerOrChainTrust` or `PeerTrust`.</span></span> <span data-ttu-id="20efa-136">Pour connaître la procédure à suivre à l'aide d'un fichier de configuration, consultez l'exemple de configuration de service précédent.</span><span class="sxs-lookup"><span data-stu-id="20efa-136">See the previous service configuration sample to learn how this can be done by using a configuration file.</span></span>  
  
    ```bat
    echo ************  
    echo copying client cert to server's LocalMachine store  
    echo ************  
    certmgr.exe -add -r CurrentUser -s My -c -n %CLIENT_NAME% -r LocalMachine -s TrustedPeople
    ```  
  
- <span data-ttu-id="20efa-137">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="20efa-137">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="20efa-138">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="20efa-138">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="20efa-139">La variable %SERVER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="20efa-139">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="20efa-140">Le certificat est stocké dans le magasin LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="20efa-140">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="20efa-141">Si le fichier de commandes Setup.bat est exécuté avec un argument service (par exemple, **setup.bat service**), le% SERVER_NAME% contient le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="20efa-141">If the Setup.bat batch file is run with an argument of service (such as, **setup.bat service**) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="20efa-142">Dans le cas contraire, elle contient la valeur par défaut localhost.</span><span class="sxs-lookup"><span data-stu-id="20efa-142">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="20efa-143">Installation du certificat de serveur dans le magasin de certificats approuvés du client</span><span class="sxs-lookup"><span data-stu-id="20efa-143">Installing the server certificate into the client’s trusted certificate store.</span></span>  
  
     <span data-ttu-id="20efa-144">La ligne suivante copie le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="20efa-144">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="20efa-145">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="20efa-145">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="20efa-146">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.</span><span class="sxs-lookup"><span data-stu-id="20efa-146">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="20efa-147">Octroi d'autorisations sur la clé privée du certificat.</span><span class="sxs-lookup"><span data-stu-id="20efa-147">Granting permissions on the certificate's private key.</span></span>  
  
     <span data-ttu-id="20efa-148">Les lignes suivantes dans le fichier Setup.bat rendent le certificat de serveur stocké dans le magasin LocalMachine accessible au compte du processus de travail ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="20efa-148">The following lines in the Setup.bat file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
    ```bat
    echo ************  
    echo setting privileges on server certificates  
    echo ************  
    for /F "delims=" %%i in ('"%ProgramFiles%\ServiceModelSampleTools\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i  
    set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE  
    (ver | findstr /C:"5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET  
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R  
    iisreset  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="20efa-149">Si vous utilisez un non-U. S. Édition anglaise de Windows, vous devez modifier le fichier Setup.bat et remplacer le nom de compte « NT AUTHORITY\NETWORK SERVICE » par votre équivalent régional.</span><span class="sxs-lookup"><span data-stu-id="20efa-149">If you are using a non-U.S. English edition of Windows, you must edit the Setup.bat file and replace the "NT AUTHORITY\NETWORK SERVICE" account name with your regional equivalent.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20efa-150">Les outils utilisés dans ce fichier de commandes se trouvent dans C:\Program Files\Microsoft Visual Studio 8\Common7\tools ou C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span><span class="sxs-lookup"><span data-stu-id="20efa-150">The tools used in this batch file are located in either C:\Program Files\Microsoft Visual Studio 8\Common7\tools or C:\Program Files\Microsoft SDKs\Windows\v6.0\bin.</span></span> <span data-ttu-id="20efa-151">L’un de ces répertoires doit se trouver dans votre chemin d’accès système.</span><span class="sxs-lookup"><span data-stu-id="20efa-151">One of these directories must be in your system path.</span></span> <span data-ttu-id="20efa-152">Si vous avez installé Visual Studio, le moyen le plus simple pour obtenir ce répertoire dans votre chemin d’accès est d’ouvrir le Invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20efa-152">If you have Visual Studio installed, the easiest way to get this directory in your path is to open the Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="20efa-153">Cliquez sur **Démarrer**, puis sélectionnez **tous les programmes**, **Visual Studio 2012**, **Outils**.</span><span class="sxs-lookup"><span data-stu-id="20efa-153">Click **Start**, and then select **All Programs**, **Visual Studio 2012**, **Tools**.</span></span> <span data-ttu-id="20efa-154">Les chemins d’accès appropriés sont déjà configurés dans cette invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="20efa-154">This command prompt has the appropriate paths already configured.</span></span> <span data-ttu-id="20efa-155">Sinon, vous devez ajouter manuellement le répertoire approprié à votre chemin d’accès.</span><span class="sxs-lookup"><span data-stu-id="20efa-155">Otherwise you must add the appropriate directory to your path manually.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="20efa-156">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="20efa-156">The samples may already be installed on your computer.</span></span> <span data-ttu-id="20efa-157">Recherchez le répertoire (par défaut) suivant avant de continuer :</span><span class="sxs-lookup"><span data-stu-id="20efa-157">Check for the following (default) directory before continuing:</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="20efa-158">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="20efa-158">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20efa-159">Cet exemple se trouve dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="20efa-159">This sample is located in the following directory:</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MessageSecurity`  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="20efa-160">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="20efa-160">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="20efa-161">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20efa-161">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="20efa-162">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="20efa-162">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="20efa-163">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="20efa-163">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="20efa-164">Ouvrez une Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez Setup.bat à partir du dossier d’installation de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="20efa-164">Open a Developer Command Prompt for Visual Studio  with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="20efa-165">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="20efa-165">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="20efa-166">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’un Invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="20efa-166">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="20efa-167">La variable d'environnement PATH doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="20efa-167">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="20efa-168">Cette variable d’environnement est définie automatiquement dans une Invite de commandes développeur pour Visual Studio (2010).</span><span class="sxs-lookup"><span data-stu-id="20efa-168">This environment variable is automatically set within a Developer Command Prompt for Visual Studio (2010).</span></span>  
  
2. <span data-ttu-id="20efa-169">Vérifiez l’accès au service à l’aide d’un navigateur en entrant l’adresse `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="20efa-169">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
3. <span data-ttu-id="20efa-170">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="20efa-170">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="20efa-171">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="20efa-171">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="20efa-172">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="20efa-172">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="20efa-173">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="20efa-173">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="20efa-174">Créez un répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="20efa-174">Create a directory on the service computer.</span></span> <span data-ttu-id="20efa-175">Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="20efa-175">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="20efa-176">Copiez les fichiers programme du service de \inetpub\wwwroot\servicemodelsamples dans le répertoire virtuel sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="20efa-176">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="20efa-177">Assurez-vous de copier les fichiers dans le sous-répertoire \bin.</span><span class="sxs-lookup"><span data-stu-id="20efa-177">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="20efa-178">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportClientCert.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="20efa-178">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="20efa-179">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="20efa-179">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="20efa-180">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="20efa-180">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="20efa-181">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="20efa-181">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="20efa-182">Sur le serveur, exécutez **setup.bat service** dans une invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="20efa-182">On the server, run **setup.bat service** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="20efa-183">L’exécution de **setup.bat** avec l’argument **service** crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service vers un fichier nommé service. cer.</span><span class="sxs-lookup"><span data-stu-id="20efa-183">Running **setup.bat** with the **service** argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="20efa-184">Modifiez Web.config pour refléter le nouveau nom de certificat (dans l' `findValue` attribut dans [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ) qui est le même que le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="20efa-184">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)) which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="20efa-185">Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="20efa-185">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="20efa-186">Sur le client, exécutez **setup.bat client** dans une invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="20efa-186">On the client, run **setup.bat client** in a Developer Command Prompt for Visual Studio with administrator privileges.</span></span> <span data-ttu-id="20efa-187">L’exécution de **setup.bat** avec l’argument **client** crée un certificat client nommé client.com et exporte le certificat client vers un fichier nommé client. cer.</span><span class="sxs-lookup"><span data-stu-id="20efa-187">Running **setup.bat** with the **client** argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="20efa-188">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="20efa-188">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="20efa-189">Pour ce faire, remplacez localhost par le nom de domaine complet du serveur.</span><span class="sxs-lookup"><span data-stu-id="20efa-189">Do this by replacing localhost with the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="20efa-190">Copiez le fichier Client.cer du répertoire client dans le répertoire de service sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="20efa-190">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="20efa-191">Sur le client, exécutez ImportServiceCert.bat dans un Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="20efa-191">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="20efa-192">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="20efa-192">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="20efa-193">Sur le serveur, exécutez ImportClientCert.bat dans un Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="20efa-193">On the server, run ImportClientCert.bat in a Developer Command Prompt for Visual Studio with administrative privileges.</span></span> <span data-ttu-id="20efa-194">Le certificat client est ainsi importé à partir du fichier Client.cer dans le magasin LocalMachine - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="20efa-194">This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="20efa-195">Sur l'ordinateur client, lancez Client.exe à partir d'une fenêtre d'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="20efa-195">On the client computer, launch Client.exe from a command prompt window.</span></span> <span data-ttu-id="20efa-196">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="20efa-196">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="20efa-197">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="20efa-197">To clean up after the sample</span></span>  
  
- <span data-ttu-id="20efa-198">Exécutez Cleanup.bat dans le dossier exemples une fois que vous avez terminé d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="20efa-198">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="20efa-199">Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="20efa-199">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="20efa-200">Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="20efa-200">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="20efa-201">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="20efa-201">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>
