---
title: Custom Binding Security
ms.date: 03/30/2017
ms.assetid: a6383dff-4308-46d2-bc6d-acd4e18b4b8d
ms.openlocfilehash: 71bc3d463330b893e8b415892a9bdcc2dae88a2b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64616040"
---
# <a name="custom-binding-security"></a><span data-ttu-id="6c2ec-102">Custom Binding Security</span><span class="sxs-lookup"><span data-stu-id="6c2ec-102">Custom Binding Security</span></span>
<span data-ttu-id="6c2ec-103">L’exemple suivant illustre comment configurer la sécurité à l’aide d’une liaison personnalisée.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-103">This sample demonstrates how to configure security by using a custom binding.</span></span> <span data-ttu-id="6c2ec-104">Il indique également comment utiliser une liaison personnalisée afin d’activer la sécurité de niveau message à l’aide d’un transport sécurisé.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-104">It shows how to use a custom binding to enable message-level security together with a secure transport.</span></span> <span data-ttu-id="6c2ec-105">Cette configuration est utile lorsqu'un transport sécurisé est requis pour la transmission des messages entre le client et le service et que ces messages doivent en même temps bénéficier d'une sécurité de niveau message.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-105">This is useful when a secure transport is required to transmit the messages between client and service and simultaneously the messages must be secure on the message level.</span></span> <span data-ttu-id="6c2ec-106">Cette configuration n’est pas prise en charge par les liaisons fournies par le système.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-106">This configuration is not supported by system-provided bindings.</span></span>

 <span data-ttu-id="6c2ec-107">Cet exemple comporte un programme de console client (EXE) et un programme de console service (EXE).</span><span class="sxs-lookup"><span data-stu-id="6c2ec-107">This sample consists of a client console program (EXE) and a service console program (EXE).</span></span> <span data-ttu-id="6c2ec-108">Le service implémente un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-108">The service implements a duplex contract.</span></span> <span data-ttu-id="6c2ec-109">Le contrat est défini par l'interface `ICalculatorDuplex`, laquelle expose les opérations mathématiques suivantes : addition, soustraction, multiplication et division.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-109">The contract is defined by the `ICalculatorDuplex` interface, which exposes math operations (Add, Subtract, Multiply, and Divide).</span></span> <span data-ttu-id="6c2ec-110">L'interface `ICalculatorDuplex` permet au client d'effectuer des opérations mathématiques, en calculant le résultat de l'exécution sur une session.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-110">The `ICalculatorDuplex` interface allows the client to perform math operations, calculating a running result over a session.</span></span> <span data-ttu-id="6c2ec-111">Indépendamment de l'interface précédente, le service peut retourner ses propres résultats sur l'interface `ICalculatorDuplexCallback`.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-111">Independently, the service may return results on the `ICalculatorDuplexCallback` interface.</span></span> <span data-ttu-id="6c2ec-112">Un contrat duplex requiert une session, un contexte devant être établi pour mettre en relation l'ensemble des messages échangés entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-112">A duplex contract requires a session, because a context must be established to correlate the set of messages being sent between the client and the service.</span></span> <span data-ttu-id="6c2ec-113">Une liaison personnalisée et sécurisée prenant en charge la communication duplex est définie.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-113">A custom binding is defined that supports duplex communication and is secure.</span></span>

> [!NOTE]
>  <span data-ttu-id="6c2ec-114">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="6c2ec-115">La configuration du service définit une liaison personnalisée prenant en charge les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="6c2ec-115">The service configuration defines a custom binding that supports the following:</span></span>

- <span data-ttu-id="6c2ec-116">Communication TCP protégée à l'aide du protocole TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-116">TCP communication protected by using the TLS/SSL protocol.</span></span>

- <span data-ttu-id="6c2ec-117">Sécurité de message Windows.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-117">Windows message security.</span></span>

 <span data-ttu-id="6c2ec-118">La configuration de la liaison personnalisée active le transport sécurisé en activant simultanément la sécurité de niveau message.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-118">The custom binding configuration enables secure transport by simultaneously enabling the message-level security.</span></span> <span data-ttu-id="6c2ec-119">Le classement des éléments de liaison est important pour définir une liaison personnalisée, car chacun représente une couche dans la pile de canaux (consultez [liaisons personnalisées](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span><span class="sxs-lookup"><span data-stu-id="6c2ec-119">The ordering of binding elements is important in defining a custom binding, because each represents a layer in the channel stack (see [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md)).</span></span> <span data-ttu-id="6c2ec-120">La liaison personnalisée est définie dans les fichiers de configuration du service et du client, tel qu'illustré dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-120">The custom binding is defined in the service and client configuration files, as shown in the following sample configuration.</span></span>

```xml
<bindings>
  <!-- Configure a custom binding. -->
  <customBinding>
    <binding name="Binding1">
      <security authenticationMode="SecureConversation"
                 requireSecurityContextCancellation="true">
      </security>
      <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>
      <sslStreamSecurity requireClientCertificate="false"/>
      <tcpTransport/>
    </binding>
  </customBinding>
</bindings>
```

 <span data-ttu-id="6c2ec-121">La liaison personnalisée utilise un certificat de service afin d’authentifier le service au niveau du transport et de protéger les messages pendant leur transmission entre le client et le service.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-121">The custom binding uses a service certificate to authenticate the service on the transport level and to protect the messages during the transmission between client and service.</span></span> <span data-ttu-id="6c2ec-122">Cette tâche est effectuée par l’élément de liaison `sslStreamSecurity`.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-122">This is accomplished by the `sslStreamSecurity` binding element.</span></span> <span data-ttu-id="6c2ec-123">Le certificat du service est configuré à l'aide d'un comportement de service, tel qu'illustré dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-123">The service's certificate is configured using a service behavior as shown in the following sample configuration.</span></span>

```xml
<behaviors>
    <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
        <serviceMetadata />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <serviceCredentials>
        <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName"/>
        </serviceCredentials>
    </behavior>
    </serviceBehaviors>
</behaviors>
```

 <span data-ttu-id="6c2ec-124">En outre, la liaison personnalisée utilise la sécurité de niveau message avec le type d’informations d’identification Windows, c’est-à-dire le type par défaut.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-124">Additionally, the custom binding uses message security with Windows credential type - this is the default credential type.</span></span> <span data-ttu-id="6c2ec-125">Cette tâche est effectuée par l’élément de liaison `security`.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-125">This is accomplished by the `security` binding element.</span></span> <span data-ttu-id="6c2ec-126">Le client et le service sont tous deux authentifiés à l'aide de la sécurité au niveau du message si le mécanisme d'authentification Kerberos est disponible.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-126">Both client and service are authenticated using message-level security if the Kerberos authentication mechanism is available.</span></span> <span data-ttu-id="6c2ec-127">Cela se produit à condition toutefois que l'exemple soit exécuté dans l'environnement Active Directory.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-127">This happens if the sample is run in the Active Directory environment.</span></span> <span data-ttu-id="6c2ec-128">Si le mécanisme d'authentification Kerberos n'est pas disponible, l'authentification NTLM est utilisée.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-128">If the Kerberos authentication mechanism is not available, NTLM authentication is used.</span></span> <span data-ttu-id="6c2ec-129">NTLM authentifie le client au service mais n'authentifie pas le service au client.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-129">NTLM authenticates the client to the service but does not authenticate the service to the client.</span></span> <span data-ttu-id="6c2ec-130">L'élément de liaison `security` est configuré pour utiliser un type `SecureConversation` `authenticationType`, ce qui entraîne la création d'une session de sécurité à la fois au niveau du client et du service.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-130">The `security` binding element is configured to use `SecureConversation` `authenticationType`, which results in the creation of a security session on both the client and the service.</span></span> <span data-ttu-id="6c2ec-131">Ceci est nécessaire pour permettre au contrat duplex du service de fonctionner.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-131">This is required to enable the service's duplex contract to work.</span></span>

 <span data-ttu-id="6c2ec-132">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console cliente.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-132">When you run the sample, the operation requests and responses are displayed in the client's console window.</span></span> <span data-ttu-id="6c2ec-133">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-133">Press ENTER in the client window to shut down the client.</span></span>

```
Press <ENTER> to terminate client.
Result(100)
Result(50)
Result(882.5)
Result(441.25)
Equation(0 + 100 - 50 * 17.65 / 2 = 441.25)
```

 <span data-ttu-id="6c2ec-134">Lorsque vous exécutez l'exemple, vous pouvez consulter les messages retournés au client sur l'interface de rappel envoyée depuis le service.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-134">When you run the sample, you see the messages returned to the client on the callback interface sent from the service.</span></span> <span data-ttu-id="6c2ec-135">Tous les résultats intermédiaires sont affichés, suivis de l'équation en entier une fois toutes les opérations terminées.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-135">Each intermediate result is displayed, followed by the entire equation upon completion of all operations.</span></span> <span data-ttu-id="6c2ec-136">Appuyez sur ENTER pour arrêter le client.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-136">Press ENTER to shut down the client.</span></span>

 <span data-ttu-id="6c2ec-137">Le fichier Setup.bat inclus vous permet de configurer le client et le serveur à l'aide du certificat de service requis pour exécuter les applications hébergées nécessitant une sécurité basée sur les certificats.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-137">The included Setup.bat file enables you to configure the client and server with the relevant service certificate to run a hosted application that requires certificate-based security.</span></span> <span data-ttu-id="6c2ec-138">Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-138">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>

 <span data-ttu-id="6c2ec-139">Les informations suivantes fournissent une vue d'ensemble des différentes sections des fichiers de commandes applicables à cet exemple afin que vous puissiez les modifier en fonction de la configuration requise :</span><span class="sxs-lookup"><span data-stu-id="6c2ec-139">The following provides a brief overview of the different sections of the batch files that apply to this sample so that they can be modified to run in the appropriate configuration:</span></span>

- <span data-ttu-id="6c2ec-140">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="6c2ec-140">Creating the server certificate.</span></span>

     <span data-ttu-id="6c2ec-141">Les lignes suivantes du fichier Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-141">The following lines from the Setup.bat file create the server certificate to be used.</span></span> <span data-ttu-id="6c2ec-142">La variable `%SERVER_NAME%` spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-142">The `%SERVER_NAME%` variable specifies the server name.</span></span> <span data-ttu-id="6c2ec-143">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-143">Change this variable to specify your own server name.</span></span> <span data-ttu-id="6c2ec-144">Ce fichier de commandes affecte par défaut la valeur localhost au nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-144">This batch file defaults the server name to localhost.</span></span>

     <span data-ttu-id="6c2ec-145">Le certificat est stocké dans le magasin CurrentUser pour les services hébergés par le Web.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-145">The certificate is stored in the CurrentUser store for the Web-hosted services.</span></span>

    ```bat
    echo ************
    echo Server cert setup starting
    echo %SERVER_NAME%
    echo ************
    echo making server cert
    echo ************
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe
    ```

- <span data-ttu-id="6c2ec-146">Installation du certificat de serveur dans le magasin de certificats approuvés du client.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-146">Installing the server certificate into the client's trusted certificate store.</span></span>

     <span data-ttu-id="6c2ec-147">Les lignes suivantes du fichier Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-147">The following lines in the Setup.bat file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="6c2ec-148">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-148">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="6c2ec-149">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-149">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>

    ```
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople
    ```

    > [!NOTE]
    >  <span data-ttu-id="6c2ec-150">Le fichier de commandes Setup.bat est conçu pour s'exécuter à partir d'une invite de commandes de Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-150">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="6c2ec-151">La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-151">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="6c2ec-152">Cette variable est définie automatiquement dans une invite de commandes de Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-152">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="6c2ec-153">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="6c2ec-153">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="6c2ec-154">Vérifiez que vous avez effectué la [procédure d’installation unique pour les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6c2ec-154">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="6c2ec-155">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6c2ec-155">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="6c2ec-156">Pour exécuter l’exemple dans une configuration unique ou plusieurs ordinateurs, suivez les instructions de [en cours d’exécution les exemples Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="6c2ec-156">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="6c2ec-157">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="6c2ec-157">To run the sample on the same computer</span></span>

1. <span data-ttu-id="6c2ec-158">Ouvrez une invite de commandes développeur pour la fenêtre Visual Studio avec des privilèges d’administrateur et exécutez Setup.bat à partir du dossier d’installation de l’exemple.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-158">Open a Developer Command Prompt for Visual Studio window with administrator privileges and run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="6c2ec-159">Tous les certificats requis à l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-159">This installs all the certificates required for running the sample.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="6c2ec-160">Le fichier de commandes Setup.bat est conçu pour être exécuté à partir d’un Visual Studio 2012 invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-160">The Setup.bat batch file is designed to be run from a Visual Studio 2012 Command Prompt.</span></span> <span data-ttu-id="6c2ec-161">La variable d’environnement PATH définie dans les points de l’invite de commandes de Visual Studio 2012 sur le répertoire qui contient les exécutables requis par le script Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-161">The PATH environment variable set within the Visual Studio 2012 Command Prompt points to the directory that contains executables required by the Setup.bat script.</span></span>  
  
2. <span data-ttu-id="6c2ec-162">Lancez Service.exe à partir de \service\bin.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-162">Launch Service.exe from \service\bin.</span></span>  
  
3. <span data-ttu-id="6c2ec-163">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-163">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="6c2ec-164">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-164">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="6c2ec-165">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour obtenir des exemples WCF](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="6c2ec-165">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="6c2ec-166">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="6c2ec-166">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="6c2ec-167">Sur l'ordinateur de service :</span><span class="sxs-lookup"><span data-stu-id="6c2ec-167">On the service computer:</span></span>  
  
    1. <span data-ttu-id="6c2ec-168">Créez un répertoire virtuel nommé servicemodelsamples sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-168">Create a virtual directory named servicemodelsamples on the service computer.</span></span>  
  
    2. <span data-ttu-id="6c2ec-169">Copiez les fichiers programme du service de \inetpub\wwwroot\servicemodelsamples dans le répertoire virtuel sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-169">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="6c2ec-170">Assurez-vous de copier les fichiers dans le sous-répertoire \bin.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-170">Ensure that you copy the files in the \bin subdirectory.</span></span>  
  
    3. <span data-ttu-id="6c2ec-171">Copiez les fichiers Setup.bat et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-171">Copy the Setup.bat and Cleanup.bat files to the service computer.</span></span>  
  
    4. <span data-ttu-id="6c2ec-172">Exécutez la commande suivante dans une invite de commandes développeur pour Visual Studio ouverte avec des privilèges d’administrateur : `Setup.bat service`.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-172">Run the following command in a Developer Command Prompt for Visual Studio opened with administrator privileges: `Setup.bat service`.</span></span> <span data-ttu-id="6c2ec-173">L'exécution de cette commande crée un certificat de service dont le nom du sujet correspond au nom de l'ordinateur sur lequel le fichier de commandes a été exécuté.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-173">This creates the service certificate with the subject name matching the name of the computer the batch file was run on.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6c2ec-174">Le fichier de commandes Setup.bat est conçu pour s'exécuter à partir d'une invite de commandes de Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-174">The Setup.bat batch file is designed to be run from a Visual Studio 2010 Command Prompt.</span></span> <span data-ttu-id="6c2ec-175">La variable d'environnement PATH doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-175">It requires that the path environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="6c2ec-176">Cette variable est définie automatiquement dans une invite de commandes de Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-176">This environment variable is automatically set within a Visual Studio 2010 Command Prompt.</span></span>

    5. <span data-ttu-id="6c2ec-177">Modifier le [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) dans le fichier Service.exe.config pour refléter le nom du sujet du certificat généré à l’étape précédente.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-177">Change the [\<serviceCertificate>](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) inside the Service.exe.config file to reflect the subject name of the certificate generated in the previous step.</span></span>

    6. <span data-ttu-id="6c2ec-178">Exécutez Service.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-178">Run Service.exe from a command prompt.</span></span>

2. <span data-ttu-id="6c2ec-179">Sur l'ordinateur client :</span><span class="sxs-lookup"><span data-stu-id="6c2ec-179">On the client computer:</span></span>

    1. <span data-ttu-id="6c2ec-180">Copiez les fichiers programme du client à partir du dossier \client\bin\ sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-180">Copy the client program files from the \client\bin\ folder to the client computer.</span></span> <span data-ttu-id="6c2ec-181">Copiez également le fichier Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-181">Also copy the Cleanup.bat file.</span></span>

    2. <span data-ttu-id="6c2ec-182">Exécutez Cleanup.bat pour supprimer tous les anciens certificats d'exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-182">Run Cleanup.bat to remove any old certificates from previous samples.</span></span>

    3. <span data-ttu-id="6c2ec-183">Exporter le certificat du service en ouvrant une invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et en exécutant la commande suivante sur l’ordinateur de service (remplacez `%SERVER_NAME%` par le nom qualifié complet de l’ordinateur où le service est en cours d’exécution) :</span><span class="sxs-lookup"><span data-stu-id="6c2ec-183">Export the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the service computer (substitute `%SERVER_NAME%` with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr -put -r LocalMachine -s My -c -n %SERVER_NAME% %SERVER_NAME%.cer
        ```

    4. <span data-ttu-id="6c2ec-184">Copiez le fichier % SERVER_NAME%.cer sur l'ordinateur client (remplacez %SERVER_NAME% par le nom complet de l'ordinateur où le service s'exécute).</span><span class="sxs-lookup"><span data-stu-id="6c2ec-184">Copy %SERVER_NAME%.cer to the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running).</span></span>

    5. <span data-ttu-id="6c2ec-185">Importer le certificat du service en ouvrant une invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur, en exécutant la commande suivante sur l’ordinateur client (remplacez % SERVER_NAME % par le nom qualifié complet de l’ordinateur où le service est en cours d’exécution) :</span><span class="sxs-lookup"><span data-stu-id="6c2ec-185">Import the service's certificate by opening a Developer Command Prompt for Visual Studio with administrative privileges, and running the following command on the client computer (substitute %SERVER_NAME% with the fully-qualified name of the computer where the service is running):</span></span>

        ```
        certmgr.exe -add -c %SERVER_NAME%.cer -s -r CurrentUser TrustedPeople
        ```

         <span data-ttu-id="6c2ec-186">Les étapes c, d et e ne sont pas requises lorsque le certificat est publié par un émetteur approuvé.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-186">Steps c, d, and e are not necessary if the certificate is issued by a Trusted Issuer.</span></span>

    6. <span data-ttu-id="6c2ec-187">Modifiez le fichier App.config du client comme suit :</span><span class="sxs-lookup"><span data-stu-id="6c2ec-187">Modify the client’s App.config file as follows:</span></span>

        ```xml
        <client>
            <endpoint name="default"
                address="net.tcp://ReplaceThisWithServiceMachineName:8000/ServiceModelSamples/Service"
                binding="customBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculatorDuplex"
        behaviorConfiguration="CalculatorClientBehavior" />
        </client>
        ```

    7. <span data-ttu-id="6c2ec-188">Si le service s'exécute dans un environnement de domaine sous un compte autre que NetworkService ou LocalSystem, vous devrez peut-être modifier l'identité de son point de terminaison dans le fichier App.config du client afin de lui affecter une identité UPN ou SPN adaptée au compte utilisé pour l'exécuter.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-188">If the service is running under an account other than the NetworkService or LocalSystem account in a domain environment, you might need to modify the endpoint identity for the service endpoint inside the client's App.config file to set the appropriate UPN or SPN based on the account that is used to run the service.</span></span> <span data-ttu-id="6c2ec-189">Pour plus d’informations sur l’identité du point de terminaison, consultez la [identité de Service et d’authentification](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) rubrique.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-189">For more information about endpoint identity, see the [Service Identity and Authentication](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md) topic.</span></span>

    8. <span data-ttu-id="6c2ec-190">Exécutez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-190">Run Client.exe from a command prompt.</span></span>

### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="6c2ec-191">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="6c2ec-191">To clean up after the sample</span></span>

- <span data-ttu-id="6c2ec-192">Exécutez Cleanup.bat dans le dossier exemples une fois que vous avez terminé d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="6c2ec-192">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>
