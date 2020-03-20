---
title: Message Security User Name
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c63cfc87-6b20-4949-93b3-bcd4b732b0a2
ms.openlocfilehash: 62b6f24bab1c655038ad3295f5af3dee0fa198fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183513"
---
# <a name="message-security-user-name"></a><span data-ttu-id="50b7a-102">Message Security User Name</span><span class="sxs-lookup"><span data-stu-id="50b7a-102">Message Security User Name</span></span>
<span data-ttu-id="50b7a-103">Cet exemple montre comment implémenter une application qui utilise WS-Security et l'authentification de nom d'utilisateur pour le client et qui nécessite l'authentification du serveur à l'aide de son certificat X.509v3.</span><span class="sxs-lookup"><span data-stu-id="50b7a-103">This sample demonstrates how to implement an application that uses WS-Security with username authentication for the client and requires server authentication using the server's X.509v3 certificate.</span></span> <span data-ttu-id="50b7a-104">Tous les messages d'application échangés entre le client et le serveur sont signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="50b7a-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="50b7a-105">Par défaut, le nom d'utilisateur et le mot de passe fournis par le client sont utilisés pour ouvrir une session à l'aide d'un compte Windows valable.</span><span class="sxs-lookup"><span data-stu-id="50b7a-105">By default, the username and password supplied by the client are used to logon to a valid Windows account.</span></span> <span data-ttu-id="50b7a-106">Cet échantillon est basé sur le [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="50b7a-106">This sample is based on the [WSHttpBinding](../../../../docs/framework/wcf/samples/wshttpbinding.md).</span></span> <span data-ttu-id="50b7a-107">Cet exemple se compose d'un programme de console client (client.exe) et d'une bibliothèque de service hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="50b7a-107">This sample consists of a client console program (Client.exe) and a service library (Service.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="50b7a-108">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="50b7a-108">The service implements a contract that defines a request-reply communication pattern.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50b7a-109">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="50b7a-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="50b7a-110">Cet exemple montre également :</span><span class="sxs-lookup"><span data-stu-id="50b7a-110">This sample also demonstrates:</span></span>  
  
- <span data-ttu-id="50b7a-111">Le mappage par défaut aux comptes Windows pour permettre au processus d'autorisation supplémentaire de se dérouler.</span><span class="sxs-lookup"><span data-stu-id="50b7a-111">The default mapping to Windows accounts so that additional authorization can be performed.</span></span>  
  
- <span data-ttu-id="50b7a-112">Comment accéder aux informations d'identité de l'appelant à partir du code du service.</span><span class="sxs-lookup"><span data-stu-id="50b7a-112">How to access the caller's identity information from the service code.</span></span>  
  
 <span data-ttu-id="50b7a-113">Le service expose un seul critère d’évaluation pour communiquer avec le service, qui est défini à l’aide du fichier de configuration Web.config. Le critère de terminaison se compose d’une adresse, d’une liaison et d’un contrat.</span><span class="sxs-lookup"><span data-stu-id="50b7a-113">The service exposes a single endpoint for communicating with the service, which is defined using the configuration file Web.config. The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="50b7a-114">La liaison est configurée avec un [ \<wsHttpBinding ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)standard>, qui par défaut à l’utilisation de la sécurité des messages.</span><span class="sxs-lookup"><span data-stu-id="50b7a-114">The binding is configured with a standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), which defaults to using message security.</span></span> <span data-ttu-id="50b7a-115">Cet exemple définit la norme [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) d’utiliser l’authentification du nom d’utilisateur client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-115">This sample sets the standard [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) to use client username authentication.</span></span> <span data-ttu-id="50b7a-116">Le comportement spécifie que les informations d'identification de l'utilisateur doivent être utilisées à des fins d'authentification du service.</span><span class="sxs-lookup"><span data-stu-id="50b7a-116">The behavior specifies that the user credentials are to be used for service authentication.</span></span> <span data-ttu-id="50b7a-117">Le certificat serveur doit contenir la même `findValue` valeur pour le nom du sujet que l’attribut dans le [ \<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span><span class="sxs-lookup"><span data-stu-id="50b7a-117">The server certificate must contain the same value for the subject name as the `findValue` attribute in the [\<serviceCredentials>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md).</span></span>  
  
```xml  
<system.serviceModel>  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      By default, Username authentication attempts to authenticate the provided  
      username as a Windows computer or domain account.  
      -->  
      <binding>  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!--   
      The serviceCredentials behavior allows one to define a service certificate.  
      A service certificate is used by the service to authenticate itself to the client and to provide message protection.  
      This configuration references the "localhost" certificate installed during the setup instructions.  
      -->  
        <serviceCredentials>  
          <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
        </serviceCredentials>  
        <serviceMetadata httpGetEnabled="True"/>  
        <serviceDebug includeExceptionDetailInFaults="False" />  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="50b7a-118">La configuration du point de terminaison du client se compose d’une adresse absolue pour le point de terminaison du service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="50b7a-118">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="50b7a-119">La liaison du client est configurée avec le `securityMode` et le `authenticationMode` appropriés.</span><span class="sxs-lookup"><span data-stu-id="50b7a-119">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span> <span data-ttu-id="50b7a-120">Lors de l'exécution sur plusieurs ordinateurs, l'adresse de point de terminaison du service doit être modifiée en conséquence.</span><span class="sxs-lookup"><span data-stu-id="50b7a-120">When running in a cross-computer scenario, the service endpoint address must be changed accordingly.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address="http://localhost/servicemodelsamples/service.svc"
              binding="wsHttpBinding"
              bindingConfiguration="Binding1"
              behaviorConfiguration="ClientCredentialsBehavior"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!--   
      This configuration defines the security mode as Message and   
      the clientCredentialType as Username.  
      -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true.-->  
  <behaviors>  
    <endpointBehaviors>  
      <behavior name="ClientCredentialsBehavior">  
        <!--   
      Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
      is in the user's Trusted People store, then it is trusted without performing a  
      validation of the certificate's issuer chain. This setting is used here for convenience so that the   
      sample can be run without having to have certificates issued by a certification authority (CA).  
      This setting is less secure than the default, ChainTrust. The security implications of this   
      setting should be carefully considered before using PeerOrChainTrust in production code.   
      -->  
        <clientCredentials>  
          <serviceCertificate>  
            <authentication certificateValidationMode="PeerOrChainTrust" />  
          </serviceCertificate>  
        </clientCredentials>  
      </behavior>  
    </endpointBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="50b7a-121">L'implémentation cliente définit le nom d'utilisateur et le mot de passe à utiliser.</span><span class="sxs-lookup"><span data-stu-id="50b7a-121">The client implementation sets the user name and password to use.</span></span>  

```csharp
// Create a client.  
CalculatorClient client = new CalculatorClient();  
  
// Configure client with valid computer or domain account (username,password).  
client.ClientCredentials.UserName.UserName = username;  
client.ClientCredentials.UserName.Password = password.ToString();  
  
// Call GetCallerIdentity service operation.  
Console.WriteLine(client.GetCallerIdentity());  
...  
//Closing the client gracefully closes the connection and cleans up resources.  
client.Close();  
```

 <span data-ttu-id="50b7a-122">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-122">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="50b7a-123">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="50b7a-123">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
MyMachine\TestAccount  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="50b7a-124">Le fichier de commandes Setup.bat contenu dans les exemples MessageSecurity vous permet de configurer le serveur à l'aide du certificat nécessaire à l'exécution des applications hébergées utilisant une sécurité basée sur des certificats.</span><span class="sxs-lookup"><span data-stu-id="50b7a-124">The Setup.bat batch file included with the MessageSecurity samples enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="50b7a-125">Deux modes d'exécution sont disponibles pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="50b7a-125">The batch file can be run in two modes.</span></span> <span data-ttu-id="50b7a-126">Pour exécuter le fichier de commandes en mode ordinateur unique, tapez `setup.bat` dans la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="50b7a-126">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="50b7a-127">Pour l'exécuter en mode service, tapez `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="50b7a-127">To run it in service mode type `setup.bat service`.</span></span> <span data-ttu-id="50b7a-128">Utilisez ce mode lorsque l'exemple est exécuté sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="50b7a-128">You use this mode when running the sample across computers.</span></span> <span data-ttu-id="50b7a-129">Pour plus d'informations, consultez la procédure d'installation figurant en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="50b7a-129">See the setup procedure at the end of this topic for details.</span></span>  
  
 <span data-ttu-id="50b7a-130">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes.</span><span class="sxs-lookup"><span data-stu-id="50b7a-130">The following provides a brief overview of the different sections of the batch files.</span></span>  
  
- <span data-ttu-id="50b7a-131">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="50b7a-131">Creating the server certificate</span></span>  
  
     <span data-ttu-id="50b7a-132">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="50b7a-132">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>  
  
    ```bat
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
     <span data-ttu-id="50b7a-133">La variable %SERVER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="50b7a-133">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="50b7a-134">Le certificat est stocké dans le magasin LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="50b7a-134">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="50b7a-135">Si le fichier de commandes Setup.bat est exécuté à l'aide d'un argument de service (tel que `setup.bat service`), la variable % SERVER_NAME% contient le nom de domaine complet de l'ordinateur.</span><span class="sxs-lookup"><span data-stu-id="50b7a-135">If the Setup.bat batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span>  <span data-ttu-id="50b7a-136">Dans le cas contraire, elle contient la valeur par défaut localhost.</span><span class="sxs-lookup"><span data-stu-id="50b7a-136">Otherwise it defaults to localhost.</span></span>  
  
- <span data-ttu-id="50b7a-137">Installation du certificat de serveur dans le magasin de certificats approuvés du client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-137">Installing the server certificate into the client's trusted certificate store</span></span>  
  
     <span data-ttu-id="50b7a-138">La ligne suivante copie le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-138">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="50b7a-139">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-139">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="50b7a-140">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-140">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```  
  
- <span data-ttu-id="50b7a-141">Octroi d'autorisations sur la clé privée du certificat.</span><span class="sxs-lookup"><span data-stu-id="50b7a-141">Granting permissions on the certificate's private key</span></span>  
  
     <span data-ttu-id="50b7a-142">Les lignes suivantes dans le fichier de lot Setup.bat rendent le certificat serveur stocké dans le magasin LocalMachine accessible au compte de processus ASP.NET travailleur.</span><span class="sxs-lookup"><span data-stu-id="50b7a-142">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>  
  
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
    > <span data-ttu-id="50b7a-143">Si vous utilisez une édition anglaise non américaine de Windows, vous devez modifier `NT AUTHORITY\NETWORK SERVICE` le fichier Setup.bat et remplacer le nom de compte par votre équivalent régional.</span><span class="sxs-lookup"><span data-stu-id="50b7a-143">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="50b7a-144">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="50b7a-144">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="50b7a-145">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les échantillons de la Fondation De communication Windows.](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)</span><span class="sxs-lookup"><span data-stu-id="50b7a-145">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="50b7a-146">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="50b7a-146">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="50b7a-147">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="50b7a-147">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="50b7a-148">Assurez-vous que le chemin d’accès contient le dossier dans lequel Makecert.exe et FindPrivateKey.exe se trouvent.</span><span class="sxs-lookup"><span data-stu-id="50b7a-148">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>  
  
2. <span data-ttu-id="50b7a-149">Exécuter Setup.bat à partir de l’échantillon installer dossier dans un Developer Command Prompt pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="50b7a-149">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="50b7a-150">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="50b7a-150">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="50b7a-151">Le fichier de lot Setup.bat est conçu pour être exécuté à partir d’une invite de commande de développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50b7a-151">The Setup.bat batch file is designed to be run from a Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="50b7a-152">La variable d'environnement PATH doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="50b7a-152">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="50b7a-153">Cette variable d’environnement est automatiquement définie dans une invite de commande de développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="50b7a-153">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="50b7a-154">Vérifier l’accès au service à `http://localhost/servicemodelsamples/service.svc`l’aide d’un navigateur en entrant l’adresse .</span><span class="sxs-lookup"><span data-stu-id="50b7a-154">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>
  
4. <span data-ttu-id="50b7a-155">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="50b7a-155">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="50b7a-156">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="50b7a-156">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="50b7a-157">Si le client et le service ne sont pas en mesure de communiquer, voir [Conseils de dépannage pour les échantillons WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="50b7a-157">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="50b7a-158">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="50b7a-158">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="50b7a-159">Créez un répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="50b7a-159">Create a directory on the service computer.</span></span> <span data-ttu-id="50b7a-160">Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="50b7a-160">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services management tool.</span></span>  
  
2. <span data-ttu-id="50b7a-161">Copiez les fichiers programme du service de \inetpub\wwwroot\servicemodelsamples dans le répertoire virtuel sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="50b7a-161">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="50b7a-162">Assurez-vous de copier les fichiers dans le sous-répertoire \bin.</span><span class="sxs-lookup"><span data-stu-id="50b7a-162">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="50b7a-163">Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="50b7a-163">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="50b7a-164">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-164">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="50b7a-165">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-165">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="50b7a-166">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-166">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="50b7a-167">Sur le serveur, exécutez `setup.bat service` dans un Developer Command Prompt for Visual Studio ouvert avec les privilèges de l’administrateur.</span><span class="sxs-lookup"><span data-stu-id="50b7a-167">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="50b7a-168">Exécution `setup.bat` avec `service` l’argument crée un certificat de service avec le nom de domaine entièrement qualifié de l’ordinateur et exporte le certificat de service à un fichier nommé Service.cer.</span><span class="sxs-lookup"><span data-stu-id="50b7a-168">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="50b7a-169">Modifiez le fichier Web.config en fonction du nouveau nom du certificat (au niveau de l'attribut findValue de l'élément serviceCertificate), lequel correspond au nom de domaine complet de l'ordinateur`.`</span><span class="sxs-lookup"><span data-stu-id="50b7a-169">Edit Web.config to reflect the new certificate name (in the findValue attribute in the serviceCertificate element) which is the same as the fully-qualified domain name of the computer`.`</span></span>  
  
7. <span data-ttu-id="50b7a-170">Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="50b7a-170">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="50b7a-171">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="50b7a-171">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="50b7a-172">Sur le client, exécuter ImportServiceCert.bat dans un Developer Command Prompt for Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="50b7a-172">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="50b7a-173">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="50b7a-173">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="50b7a-174">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="50b7a-174">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="50b7a-175">Si le client et le service ne sont pas en mesure de communiquer, voir [Conseils de dépannage pour les échantillons WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="50b7a-175">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="50b7a-176">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="50b7a-176">To clean up after the sample</span></span>  
  
- <span data-ttu-id="50b7a-177">Exécutez Cleanup.bat dans le dossier exemples une fois que vous avez terminé d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="50b7a-177">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="50b7a-178">Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="50b7a-178">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="50b7a-179">Si vous avez exécuté des échantillons de la Windows Communication Foundation (WCF) qui utilisent des certificats sur les ordinateurs, assurez-vous d’effacer les certificats de service qui ont été installés dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="50b7a-179">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="50b7a-180">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="50b7a-180">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
