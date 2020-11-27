---
title: Message Security Anonymous
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: c321cbf9-8c05-4cce-b5a5-4bf7b230ee03
ms.openlocfilehash: 4349b53ca86c0ed8bd7e0527ad1e903543f56631
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294398"
---
# <a name="message-security-anonymous"></a><span data-ttu-id="2888c-102">Message Security Anonymous</span><span class="sxs-lookup"><span data-stu-id="2888c-102">Message Security Anonymous</span></span>

<span data-ttu-id="2888c-103">Cet exemple montre comment implémenter une application Windows Communication Foundation (WCF) qui utilise la sécurité au niveau du message sans authentification du client, mais qui requiert l’authentification du serveur à l’aide du certificat X. 509 du serveur.</span><span class="sxs-lookup"><span data-stu-id="2888c-103">The Message Security Anonymous sample demonstrates how to implement a Windows Communication Foundation (WCF) application that uses message-level security with no client authentication but that requires server authentication using the server's X.509 certificate.</span></span> <span data-ttu-id="2888c-104">Tous les messages d'application échangés entre le client et le serveur sont signés et chiffrés.</span><span class="sxs-lookup"><span data-stu-id="2888c-104">All application messages between the client and server are signed and encrypted.</span></span> <span data-ttu-id="2888c-105">Cet exemple est basé sur l’exemple [WSHttpBinding](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2888c-105">This sample is based on the [WSHttpBinding](wshttpbinding.md) sample.</span></span> <span data-ttu-id="2888c-106">Cet exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="2888c-106">This sample consists of a client console program (.exe) and a service library (.dll) hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="2888c-107">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="2888c-107">The service implements a contract that defines a request-reply communication pattern.</span></span>

> [!NOTE]
> <span data-ttu-id="2888c-108">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="2888c-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="2888c-109">Cet exemple ajoute une nouvelle opération à l'interface de calculatrice qui retourne la valeur `True` lorsque le client n'est pas authentifié.</span><span class="sxs-lookup"><span data-stu-id="2888c-109">This sample adds a new operation to the calculator interface that returns `True` if the client was not authenticated.</span></span>

```csharp
public class CalculatorService : ICalculator
{
    public bool IsCallerAnonymous()
    {
        // ServiceSecurityContext.IsAnonymous returns true if the caller is not authenticated.
        return ServiceSecurityContext.Current.IsAnonymous;
    }
    ...
}
```

 <span data-ttu-id="2888c-110">Le service expose un point de terminaison unique de communication avec le service, lequel est défini à l'aide du fichier de configuration Web.config.</span><span class="sxs-lookup"><span data-stu-id="2888c-110">The service exposes a single endpoint for communicating with the service, defined using a configuration file (Web.config).</span></span> <span data-ttu-id="2888c-111">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="2888c-111">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="2888c-112">La liaison est configurée à l’aide de la liaison `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="2888c-112">The binding is configured with a `wsHttpBinding` binding.</span></span> <span data-ttu-id="2888c-113">Le mode de sécurité par défaut pour la liaison `wsHttpBinding` correspond à `Message`.</span><span class="sxs-lookup"><span data-stu-id="2888c-113">The default security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="2888c-114">La valeur de l'attribut `clientCredentialType` est `None`.</span><span class="sxs-lookup"><span data-stu-id="2888c-114">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>

  <protocolMapping>
    <add scheme="http" binding="wsHttpBinding" />
  </protocolMapping>

  <bindings>
    <wsHttpBinding>
     <!-- This configuration defines the security mode as Message and -->
     <!-- the clientCredentialType as None. This mode provides -->
     <!-- server authentication only using the service certificate. -->

     <binding>
       <security mode="Message">
         <message clientCredentialType="None" />
       </security>
     </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="2888c-115">Les informations d’identification à utiliser pour l’authentification du service sont spécifiées dans le [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) .</span><span class="sxs-lookup"><span data-stu-id="2888c-115">The credentials to be used for service authentication are specified in the [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md).</span></span> <span data-ttu-id="2888c-116">Dans le certificat du serveur, la valeur de `SubjectName` doit correspondre à la valeur spécifiée pour l'attribut `findValue`, tel qu'illustré par l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="2888c-116">The server certificate must contain the same value for the `SubjectName` as the value specified for the `findValue` attribute as shown in the following sample code.</span></span>

```xml
<behaviors>
  <serviceBehaviors>
    <behavior>
      <!--
    The serviceCredentials behavior allows you to define a service certificate.
    A service certificate is used by a client to authenticate the service and provide message protection.
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
```

 <span data-ttu-id="2888c-117">La configuration du point de terminaison du client se compose d’une adresse absolue pour le point de terminaison du service, de la liaison et du contrat.</span><span class="sxs-lookup"><span data-stu-id="2888c-117">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="2888c-118">Le mode de sécurité du client pour la liaison `wsHttpBinding` correspond à `Message`.</span><span class="sxs-lookup"><span data-stu-id="2888c-118">The client security mode for the `wsHttpBinding` binding is `Message`.</span></span> <span data-ttu-id="2888c-119">La valeur de l'attribut `clientCredentialType` est `None`.</span><span class="sxs-lookup"><span data-stu-id="2888c-119">The `clientCredentialType` attribute is set to `None`.</span></span>

```xml
<system.serviceModel>
  <client>
    <endpoint name=""
             address="http://localhost/servicemodelsamples/service.svc"
             binding="wsHttpBinding"
             behaviorConfiguration="ClientCredentialsBehavior"
             bindingConfiguration="Binding1"
             contract="Microsoft.ServiceModel.Samples.ICalculator" />
  </client>

  <bindings>
    <wsHttpBinding>
      <!--This configuration defines the security mode as -->
      <!--Message and the clientCredentialType as None. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="None"/>
        </security>
      </binding>
    </wsHttpBinding>
  </bindings>
  ...
</system.serviceModel>
```

 <span data-ttu-id="2888c-120">L'exemple affecte au <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> la valeur <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> pour authentifier le certificat du service.</span><span class="sxs-lookup"><span data-stu-id="2888c-120">The sample sets the <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A> to <xref:System.ServiceModel.Security.X509CertificateValidationMode.PeerOrChainTrust> for authenticating the service's certificate.</span></span> <span data-ttu-id="2888c-121">Cette opération s'effectue dans le fichier App.config du client à la section `behaviors`.</span><span class="sxs-lookup"><span data-stu-id="2888c-121">This is done in the client's App.config file in the `behaviors` section.</span></span> <span data-ttu-id="2888c-122">Cela signifie que si le certificat se trouve dans le magasin de personnes de confiance de l’utilisateur, il est approuvé sans validation de sa chaîne d’émetteur.</span><span class="sxs-lookup"><span data-stu-id="2888c-122">This means that if the certificate is in the user's Trusted People store, then it is trusted without performing a validation of the certificate's issuer chain.</span></span> <span data-ttu-id="2888c-123">Ce paramètre est utilisé ici pour des raisons pratiques afin que l'exemple puisse s'exécuter sans nécessiter que les certificats soient publiés par une autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="2888c-123">This setting is used here for convenience so that the sample can be run without requiring certificates issued by a certification authority (CA).</span></span> <span data-ttu-id="2888c-124">Ce paramètre n'offre pas le même niveau de sécurité que la valeur par défaut, ChainTrust.</span><span class="sxs-lookup"><span data-stu-id="2888c-124">This setting is less secure than the default, ChainTrust.</span></span> <span data-ttu-id="2888c-125">C'est pourquoi, ses conséquences en termes de sécurité doivent être mûrement réfléchies avant d'utiliser `PeerOrChainTrust` dans le code de production.</span><span class="sxs-lookup"><span data-stu-id="2888c-125">The security implications of this setting should be carefully considered before using `PeerOrChainTrust` in production code.</span></span>

 <span data-ttu-id="2888c-126">L’implémentation cliente ajoute un appel à la `IsCallerAnonymous` méthode et ne diffère pas de l’exemple [WSHttpBinding](wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="2888c-126">The client implementation adds a call to the `IsCallerAnonymous` method and otherwise does not differ from the [WSHttpBinding](wshttpbinding.md) sample.</span></span>

```csharp
// Create a client with a client endpoint configuration.
CalculatorClient client = new CalculatorClient();

// Call the GetCallerIdentity operation.
Console.WriteLine("IsCallerAnonymous returned: {0}", client.IsCallerAnonymous());

// Call the Add service operation.
double value1 = 100.00D;
double value2 = 15.99D;
double result = client.Add(value1, value2);
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);

...

//Closing the client gracefully closes the connection and cleans up resources.
client.Close();

Console.WriteLine();
Console.WriteLine("Press <ENTER> to terminate client.");
Console.ReadLine();
```

 <span data-ttu-id="2888c-127">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="2888c-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="2888c-128">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="2888c-128">Press ENTER in the client window to shut down the client.</span></span>

```console
IsCallerAnonymous returned: True
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714
Press <ENTER> to terminate client.
```

 <span data-ttu-id="2888c-129">Le fichier de commandes Setup.bat contenu dans l'exemple Message Security Anonymous vous permet de configurer le serveur à l'aide du certificat nécessaire à l'exécution d'une application hébergée utilisant une sécurité basée sur les certificats.</span><span class="sxs-lookup"><span data-stu-id="2888c-129">The Setup.bat batch file included with the Message Security Anonymous sample enables you to configure the server with a relevant certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="2888c-130">Deux modes d'exécution sont disponibles pour ce fichier.</span><span class="sxs-lookup"><span data-stu-id="2888c-130">The batch file can be run in two modes.</span></span> <span data-ttu-id="2888c-131">Pour exécuter le fichier de commandes en mode ordinateur unique, tapez `setup.bat` dans la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2888c-131">To run the batch file in the single-computer mode, type `setup.bat` at the command line.</span></span> <span data-ttu-id="2888c-132">Pour l'exécuter en mode service, tapez `setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="2888c-132">To run it in service mode, type `setup.bat service`.</span></span> <span data-ttu-id="2888c-133">Utilisez ce mode lorsque l'exemple est exécuté sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2888c-133">Use this mode when running the sample across computers.</span></span> <span data-ttu-id="2888c-134">Pour plus d'informations, consultez la procédure d'installation figurant en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="2888c-134">See the setup procedure at the end of this topic for details.</span></span>

 <span data-ttu-id="2888c-135">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes :</span><span class="sxs-lookup"><span data-stu-id="2888c-135">The following provides a brief overview of the different sections of the batch files:</span></span>

- <span data-ttu-id="2888c-136">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="2888c-136">Creating the server certificate.</span></span>

     <span data-ttu-id="2888c-137">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="2888c-137">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

     <span data-ttu-id="2888c-138">La variable %SERVER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="2888c-138">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="2888c-139">Le certificat est stocké dans le magasin LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2888c-139">The certificate is stored in the LocalMachine store.</span></span> <span data-ttu-id="2888c-140">Si le fichier de commandes d’installation est exécuté à l’aide d’un argument de service (tel que `setup.bat service`), la variable %SERVER_NAME% contient le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2888c-140">If the setup batch file is run with an argument of service (such as `setup.bat service`) the %SERVER_NAME% contains the fully-qualified domain name of the computer.</span></span> <span data-ttu-id="2888c-141">Dans le cas contraire, elle contient la valeur par défaut localhost.</span><span class="sxs-lookup"><span data-stu-id="2888c-141">Otherwise it defaults to localhost.</span></span>

- <span data-ttu-id="2888c-142">Installation du certificat de serveur dans le magasin de certificats approuvés du client.</span><span class="sxs-lookup"><span data-stu-id="2888c-142">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="2888c-143">La ligne suivante copie le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="2888c-143">The following line copies the server certificate into the client trusted people store.</span></span> <span data-ttu-id="2888c-144">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="2888c-144">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="2888c-145">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.</span><span class="sxs-lookup"><span data-stu-id="2888c-145">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```console
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

- <span data-ttu-id="2888c-146">Octroi d'autorisations sur la clé privée du certificat.</span><span class="sxs-lookup"><span data-stu-id="2888c-146">Granting permissions on the certificate's private key.</span></span>

     <span data-ttu-id="2888c-147">Les lignes suivantes du fichier de commandes Setup.bat rendent le certificat de serveur stocké dans le magasin LocalMachine accessible au compte du processus de travail ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="2888c-147">The following lines in the Setup.bat batch file make the server certificate stored in the LocalMachine store accessible to the ASP.NET worker process account.</span></span>

    ```bat
    echo ************
    echo setting privileges on server certificates
    echo ************
    for /F "delims=" %%i in ('"%MSSDK%\bin\FindPrivateKey.exe" My LocalMachine -n CN^=%SERVER_NAME% -a') do set PRIVATE_KEY_FILE=%%i set WP_ACCOUNT=NT AUTHORITY\NETWORK SERVICE
    (ver | findstr "5.1") && set WP_ACCOUNT=%COMPUTERNAME%\ASPNET
    echo Y|cacls.exe "%PRIVATE_KEY_FILE%" /E /G "%WP_ACCOUNT%":R
    iisreset
    ```

> [!NOTE]
> <span data-ttu-id="2888c-148">Si vous utilisez un non-U. S. Édition anglaise de Windows vous devez modifier le fichier Setup.bat et remplacer le `NT AUTHORITY\NETWORK SERVICE` nom du compte par votre équivalent régional.</span><span class="sxs-lookup"><span data-stu-id="2888c-148">If you are using a non-U.S. English edition of Windows you must edit the Setup.bat file and replace the `NT AUTHORITY\NETWORK SERVICE` account name with your regional equivalent.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="2888c-149">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="2888c-149">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="2888c-150">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2888c-150">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="2888c-151">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="2888c-151">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="2888c-152">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="2888c-152">To run the sample on the same computer</span></span>

1. <span data-ttu-id="2888c-153">Assurez-vous que le chemin d’accès contient le dossier dans lequel Makecert.exe et FindPrivateKey.exe se trouvent.</span><span class="sxs-lookup"><span data-stu-id="2888c-153">Ensure that the path includes the folder where Makecert.exe and FindPrivateKey.exe are located.</span></span>

2. <span data-ttu-id="2888c-154">Exécutez Setup.bat à partir du dossier d’installation de l’exemple dans une Invite de commandes développeur pour Visual Studio exécuter avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="2888c-154">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="2888c-155">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="2888c-155">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2888c-156">Le fichier de commandes d’installation est conçu pour être exécuté à partir d’un Invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2888c-156">The setup batch file is designed to be run from a  Developer Command Prompt for Visual Studio.</span></span> <span data-ttu-id="2888c-157">La variable d'environnement PATH doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="2888c-157">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="2888c-158">Cette variable d’environnement est définie automatiquement dans un Invite de commandes développeur pour Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2888c-158">This environment variable is automatically set within a Developer Command Prompt for Visual Studio.</span></span>  
  
3. <span data-ttu-id="2888c-159">Vérifiez l’accès au service à l’aide d’un navigateur en entrant l’adresse `http://localhost/servicemodelsamples/service.svc` .</span><span class="sxs-lookup"><span data-stu-id="2888c-159">Verify access to the service using a browser by entering the address `http://localhost/servicemodelsamples/service.svc`.</span></span>  
  
4. <span data-ttu-id="2888c-160">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="2888c-160">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="2888c-161">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="2888c-161">Client activity is displayed on the client console application.</span></span>  
  
5. <span data-ttu-id="2888c-162">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2888c-162">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="2888c-163">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="2888c-163">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="2888c-164">Créez un répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="2888c-164">Create a directory on the service computer.</span></span> <span data-ttu-id="2888c-165">Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="2888c-165">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="2888c-166">Copiez les fichiers programme du service de \inetpub\wwwroot\servicemodelsamples dans le répertoire virtuel sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="2888c-166">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="2888c-167">Assurez-vous de copier les fichiers dans le sous-répertoire \bin.</span><span class="sxs-lookup"><span data-stu-id="2888c-167">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="2888c-168">Copiez également les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="2888c-168">Also copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="2888c-169">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="2888c-169">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="2888c-170">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="2888c-170">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="2888c-171">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="2888c-171">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="2888c-172">Sur le serveur, exécutez `setup.bat service` dans un invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="2888c-172">On the server, run `setup.bat service` in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="2888c-173">`setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.</span><span class="sxs-lookup"><span data-stu-id="2888c-173">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="2888c-174">Modifiez Web.config pour refléter le nouveau nom de certificat (dans l' `findValue` attribut de [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), qui est le même que le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="2888c-174">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="2888c-175">Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="2888c-175">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="2888c-176">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="2888c-176">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="2888c-177">Sur le client, exécutez ImportServiceCert.bat dans un Invite de commandes développeur pour Visual Studio ouvert avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="2888c-177">On the client, run ImportServiceCert.bat in a Developer Command Prompt for Visual Studio opened with administrator privileges.</span></span> <span data-ttu-id="2888c-178">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="2888c-178">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="2888c-179">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="2888c-179">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="2888c-180">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="2888c-180">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="2888c-181">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="2888c-181">To clean up after the sample</span></span>  
  
- <span data-ttu-id="2888c-182">Exécutez Cleanup.bat dans le dossier exemples une fois que vous avez terminé d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="2888c-182">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2888c-183">Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="2888c-183">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="2888c-184">Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="2888c-184">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="2888c-185">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`.</span><span class="sxs-lookup"><span data-stu-id="2888c-185">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com.`</span></span>
