---
title: Membership and Role Provider
ms.date: 03/30/2017
ms.assetid: 0d11a31c-e75f-4fcf-9cf4-b7f26e056bcd
ms.openlocfilehash: e532f35a2c4cd9f53006c088956eadff616d2005
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543587"
---
# <a name="membership-and-role-provider"></a><span data-ttu-id="e7290-102">Membership and Role Provider</span><span class="sxs-lookup"><span data-stu-id="e7290-102">Membership and Role Provider</span></span>
<span data-ttu-id="e7290-103">L’exemple de fournisseur d’appartenances et de rôles montre comment un service peut utiliser les fournisseurs d’appartenances et de rôles ASP.NET pour authentifier et autoriser des clients.</span><span class="sxs-lookup"><span data-stu-id="e7290-103">The Membership and Role Provider sample demonstrates how a service can use the ASP.NET membership and role providers to authenticate and authorize clients.</span></span>  
  
 <span data-ttu-id="e7290-104">Dans cet exemple, le client est une application console (.exe) et le service est hébergé par les services IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="e7290-104">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7290-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="e7290-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e7290-106">L'exemple montre comment :</span><span class="sxs-lookup"><span data-stu-id="e7290-106">The sample demonstrates how:</span></span>  
  
- <span data-ttu-id="e7290-107">Un client peut authentifier des utilisateurs à l'aide de la combinaison nom d'utilisateur et mot de passe.</span><span class="sxs-lookup"><span data-stu-id="e7290-107">A client can authenticate by using the username-password combination.</span></span>  
  
- <span data-ttu-id="e7290-108">Le serveur peut valider les informations d’identification du client par rapport au fournisseur d’appartenances ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e7290-108">The server can validate the client credentials against the ASP.NET membership provider.</span></span>  
  
- <span data-ttu-id="e7290-109">Le serveur peut être authentifié à l'aide du certificat X.509 du serveur.</span><span class="sxs-lookup"><span data-stu-id="e7290-109">The server can be authenticated by using the server's X.509 certificate.</span></span>  
  
- <span data-ttu-id="e7290-110">Le serveur peut mapper le client authentifié à un rôle à l’aide du fournisseur de rôles ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e7290-110">The server can map the authenticated client to a role by using the ASP.NET role provider.</span></span>  
  
- <span data-ttu-id="e7290-111">Le serveur peut utiliser l'`PrincipalPermissionAttribute` pour contrôler l'accès à certaines méthodes exposées par le service.</span><span class="sxs-lookup"><span data-stu-id="e7290-111">The server can use the `PrincipalPermissionAttribute` to control access to certain methods that are exposed by the service.</span></span>  
  
 <span data-ttu-id="e7290-112">Les fournisseurs d'appartenances et de rôles sont configurés pour utiliser un magasin soutenu par SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e7290-112">The membership and role providers are configured to use a store backed by SQL Server.</span></span> <span data-ttu-id="e7290-113">Une chaîne de connexion et différentes options sont spécifiées dans le fichier de configuration du service.</span><span class="sxs-lookup"><span data-stu-id="e7290-113">A connection string and various options are specified in the service configuration file.</span></span> <span data-ttu-id="e7290-114">Le fournisseur d'appartenances reçoit le nom `SqlMembershipProvider` tandis que le fournisseur de rôles reçoit le nom `SqlRoleProvider`.</span><span class="sxs-lookup"><span data-stu-id="e7290-114">The membership provider is given the name `SqlMembershipProvider` while the role provider is given the name `SqlRoleProvider`.</span></span>  
  
```xml  
<!-- Set the connection string for SQL Server -->  
<connectionStrings>  
  <add name="SqlConn"
       connectionString="Data Source=localhost;Integrated Security=SSPI;Initial Catalog=aspnetdb;" />  
</connectionStrings>  
  
<system.web>  
  <!-- Configure the Sql Membership Provider -->  
  <membership defaultProvider="SqlMembershipProvider" userIsOnlineTimeWindow="15">  
    <providers>  
      <clear />  
      <add
        name="SqlMembershipProvider"
        type="System.Web.Security.SqlMembershipProvider"
        connectionStringName="SqlConn"  
        applicationName="MembershipAndRoleProviderSample"  
        enablePasswordRetrieval="false"  
        enablePasswordReset="false"  
        requiresQuestionAndAnswer="false"  
        requiresUniqueEmail="true"  
        passwordFormat="Hashed" />  
    </providers>  
  </membership>  
  
  <!-- Configure the Sql Role Provider -->  
  <roleManager enabled ="true"
               defaultProvider ="SqlRoleProvider" >  
    <providers>  
      <add name ="SqlRoleProvider"
           type="System.Web.Security.SqlRoleProvider"
           connectionStringName="SqlConn"
           applicationName="MembershipAndRoleProviderSample"/>  
    </providers>  
  </roleManager>  
</system.web>  
```  
  
 <span data-ttu-id="e7290-115">Le service expose un point de terminaison unique de communication avec le service, qui est défini à l'aide du fichier de configuration Web.config.</span><span class="sxs-lookup"><span data-stu-id="e7290-115">The service exposes a single endpoint for communicating with the service, which is defined by using the Web.config configuration file.</span></span> <span data-ttu-id="e7290-116">Le point de terminaison se compose d'une adresse, d'une liaison et d'un contrat.</span><span class="sxs-lookup"><span data-stu-id="e7290-116">The endpoint consists of an address, a binding, and a contract.</span></span> <span data-ttu-id="e7290-117">La liaison est configurée avec une `wsHttpBinding`standard, qui utilise par défaut l'authentification Windows.</span><span class="sxs-lookup"><span data-stu-id="e7290-117">The binding is configured with a standard `wsHttpBinding`, which defaults to using Windows authentication.</span></span> <span data-ttu-id="e7290-118">Cet exemple définit la `wsHttpBinding` standard de manière à utiliser l'authentification du nom d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e7290-118">This sample sets the standard `wsHttpBinding` to use username authentication.</span></span> <span data-ttu-id="e7290-119">Le comportement spécifie que le certificat de serveur sera utilisé pour l'authentification du service.</span><span class="sxs-lookup"><span data-stu-id="e7290-119">The behavior specifies that the server certificate is to be used for service authentication.</span></span> <span data-ttu-id="e7290-120">Le certificat de serveur doit contenir la même valeur pour le `SubjectName` en tant qu' `findValue` attribut dans l' [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) élément de configuration.</span><span class="sxs-lookup"><span data-stu-id="e7290-120">The server certificate must contain the same value for the `SubjectName` as the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) configuration element.</span></span> <span data-ttu-id="e7290-121">En outre, le comportement spécifie que l’authentification des paires nom d’utilisateur/mot de passe est effectuée par le fournisseur d’appartenances ASP.NET et que le mappage de rôle est effectué par le fournisseur de rôle ASP.NET en spécifiant les noms définis pour les deux fournisseurs.</span><span class="sxs-lookup"><span data-stu-id="e7290-121">In addition the behavior specifies that authentication of username-password pairs is performed by the ASP.NET membership provider and role mapping is performed by the ASP.NET role provider by specifying the names defined for the two providers.</span></span>  
  
```xml  
<system.serviceModel>  
  
  <protocolMapping>  
    <add scheme="http" binding="wsHttpBinding" />  
  </protocolMapping>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- Set up a binding that uses Username as the client credential type -->  
      <binding>  
        <security mode ="Message">  
          <message clientCredentialType ="UserName"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <serviceBehaviors>  
      <behavior>  
        <!-- Configure role based authorization to use the Role Provider -->  
        <serviceAuthorization principalPermissionMode ="UseAspNetRoles"  
                              roleProviderName ="SqlRoleProvider" />  
        <serviceCredentials>  
          <!-- Configure user name authentication to use the Membership Provider -->  
          <userNameAuthentication userNamePasswordValidationMode ="MembershipProvider"
                                  membershipProviderName ="SqlMembershipProvider"/>  
          <!-- Configure the service certificate -->  
          <serviceCertificate storeLocation ="LocalMachine"
                              storeName ="My"
                              x509FindType ="FindBySubjectName"  
                              findValue ="localhost" />  
        </serviceCredentials>  
        <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
        <serviceDebug includeExceptionDetailInFaults="false" />  
        <serviceMetadata httpGetEnabled="true"/>  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="e7290-122">Lorsque vous exécutez l'exemple, le client appelle plusieurs opérations de service sous trois comptes d'utilisateurs différents : Alice, Bob et Charlie.</span><span class="sxs-lookup"><span data-stu-id="e7290-122">When you run the sample, the client calls the various service operations under three different user accounts: Alice, Bob, and Charlie.</span></span> <span data-ttu-id="e7290-123">Les demandes et réponses de l'opération sont affichées dans la fenêtre de console cliente.</span><span class="sxs-lookup"><span data-stu-id="e7290-123">The operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e7290-124">Les quatre appels passés par l'utilisateur « Alice » doivent réussir.</span><span class="sxs-lookup"><span data-stu-id="e7290-124">All four calls made as user "Alice" should succeed.</span></span> <span data-ttu-id="e7290-125">L'utilisateur « Bob » doit obtenir une erreur d'accès refusé lors de la tentative d'appel de la méthode Divide.</span><span class="sxs-lookup"><span data-stu-id="e7290-125">User "Bob" should get an access denied error when trying to call the Divide method.</span></span> <span data-ttu-id="e7290-126">L'utilisateur  « Charlie » doit obtenir à une erreur d'accès refusé lors de la tentative d'appel de la méthode Multiply.</span><span class="sxs-lookup"><span data-stu-id="e7290-126">User "Charlie" should get an access denied error when trying to call the Multiply method.</span></span> <span data-ttu-id="e7290-127">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="e7290-127">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e7290-128">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="e7290-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e7290-129">Pour générer l’édition C# ou Visual Basic .NET de la solution, suivez les instructions de la procédure d' [exécution des exemples de Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e7290-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
2. <span data-ttu-id="e7290-130">Vérifiez que vous avez configuré la [base de données ASP.NET services d’application](https://go.microsoft.com/fwlink/?LinkId=94997).</span><span class="sxs-lookup"><span data-stu-id="e7290-130">Ensure that you have configured the [ASP.NET Application Services Database](https://go.microsoft.com/fwlink/?LinkId=94997).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e7290-131">Si vous exécutez SQL Server Express Edition, le nom de votre serveur est .\SQLEXPRESS.</span><span class="sxs-lookup"><span data-stu-id="e7290-131">If you are running SQL Server Express Edition, your server name is .\SQLEXPRESS.</span></span> <span data-ttu-id="e7290-132">Ce serveur doit être utilisé lors de la configuration de la base de données ASP.NET Services d’application ainsi que dans la chaîne de connexion Web.config.</span><span class="sxs-lookup"><span data-stu-id="e7290-132">This server should be used when configuring the ASP.NET Application Services Database as well as in the Web.config connection string.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e7290-133">Le compte de processus de travail ASP.NET doit avoir des autorisations sur la base de données créée dans cette étape.</span><span class="sxs-lookup"><span data-stu-id="e7290-133">The ASP.NET worker process account must have permissions on the database that is created in this step.</span></span> <span data-ttu-id="e7290-134">Utilisez l'utilitaire sqlcmd ou SQL Server Management Studio pour ce faire.</span><span class="sxs-lookup"><span data-stu-id="e7290-134">Use the sqlcmd utility or SQL Server Management Studio to do this.</span></span>  
  
3. <span data-ttu-id="e7290-135">Pour exécuter l'exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="e7290-135">To run the sample in a single- or cross-computer configuration, use the following instructions.</span></span>  
  
### <a name="to-run-the-sample-on-the-same-computer"></a><span data-ttu-id="e7290-136">Pour exécuter l'exemple sur le même ordinateur</span><span class="sxs-lookup"><span data-stu-id="e7290-136">To run the sample on the same computer</span></span>  
  
1. <span data-ttu-id="e7290-137">Assurez-vous que le chemin d'accès inclut le dossier dans lequel Makecert.exe se trouve.</span><span class="sxs-lookup"><span data-stu-id="e7290-137">Make sure that the path includes the folder where Makecert.exe is located.</span></span>  
  
2. <span data-ttu-id="e7290-138">Exécutez Setup.bat à partir du dossier d’installation de l’exemple dans une Invite de commandes développeur pour Visual Studio exécuter avec des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="e7290-138">Run Setup.bat from the sample install folder in a Developer Command Prompt for Visual Studio run with administrator privileges.</span></span> <span data-ttu-id="e7290-139">Tous les certificats de service requis pour l'exécution de l'exemple sont ainsi installés.</span><span class="sxs-lookup"><span data-stu-id="e7290-139">This installs the service certificates required for running the sample.</span></span>  
  
3. <span data-ttu-id="e7290-140">Lancez Client.exe à partir de \client\bin.</span><span class="sxs-lookup"><span data-stu-id="e7290-140">Launch Client.exe from \client\bin.</span></span> <span data-ttu-id="e7290-141">L'activité du client s'affiche sur son application de console.</span><span class="sxs-lookup"><span data-stu-id="e7290-141">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="e7290-142">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e7290-142">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="e7290-143">Pour exécuter l'exemple sur plusieurs ordinateurs</span><span class="sxs-lookup"><span data-stu-id="e7290-143">To run the sample across computers</span></span>  
  
1. <span data-ttu-id="e7290-144">Créez un répertoire sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="e7290-144">Create a directory on the service computer.</span></span> <span data-ttu-id="e7290-145">Créez une application virtuelle appelée servicemodelsamples pour ce répertoire à l'aide de l'outil de gestion IIS (Internet Information Services).</span><span class="sxs-lookup"><span data-stu-id="e7290-145">Create a virtual application named servicemodelsamples for this directory by using the Internet Information Services (IIS) management tool.</span></span>  
  
2. <span data-ttu-id="e7290-146">Copiez les fichiers programme du service de \inetpub\wwwroot\servicemodelsamples dans le répertoire virtuel sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="e7290-146">Copy the service program files from \inetpub\wwwroot\servicemodelsamples to the virtual directory on the service computer.</span></span> <span data-ttu-id="e7290-147">Assurez-vous de copier les fichiers dans le sous-répertoire \bin.</span><span class="sxs-lookup"><span data-stu-id="e7290-147">Ensure that you copy the files in the \bin subdirectory.</span></span> <span data-ttu-id="e7290-148">Copiez également les fichiers Setup.bat, GetComputerName.vbs et Cleanup.bat sur l'ordinateur de service.</span><span class="sxs-lookup"><span data-stu-id="e7290-148">Also copy the Setup.bat, GetComputerName.vbs, and Cleanup.bat files to the service computer.</span></span>  
  
3. <span data-ttu-id="e7290-149">Créez un répertoire sur l'ordinateur client pour les fichiers binaires du client.</span><span class="sxs-lookup"><span data-stu-id="e7290-149">Create a directory on the client computer for the client binaries.</span></span>  
  
4. <span data-ttu-id="e7290-150">Copiez les fichiers programme du client dans le répertoire client de l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="e7290-150">Copy the client program files to the client directory on the client computer.</span></span> <span data-ttu-id="e7290-151">Copiez également les fichiers Setup.bat, Cleanup.bat et ImportServiceCert.bat sur le client.</span><span class="sxs-lookup"><span data-stu-id="e7290-151">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="e7290-152">Sur le serveur, ouvrez une Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez `setup.bat service` .</span><span class="sxs-lookup"><span data-stu-id="e7290-152">On the server, open a Developer Command Prompt for Visual Studio with administrative privileges and run `setup.bat service`.</span></span> <span data-ttu-id="e7290-153">`setup.bat`L’exécution avec l' `service` argument crée un certificat de service avec le nom de domaine complet de l’ordinateur et exporte le certificat de service dans un fichier nommé service. cer.</span><span class="sxs-lookup"><span data-stu-id="e7290-153">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the computer and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="e7290-154">Modifiez Web.config pour refléter le nouveau nom de certificat (dans l' `findValue` attribut de [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ), qui est le même que le nom de domaine complet de l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="e7290-154">Edit Web.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)), which is the same as the fully-qualified domain name of the computer.</span></span>  
  
7. <span data-ttu-id="e7290-155">Copiez le fichier Service.cer du répertoire de service vers le répertoire client sur l'ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="e7290-155">Copy the Service.cer file from the service directory to the client directory on the client computer.</span></span>  
  
8. <span data-ttu-id="e7290-156">Dans le fichier Client.exe.config de l'ordinateur client, modifiez la valeur d'adresse du point de terminaison afin qu'elle corresponde à la nouvelle adresse de votre service.</span><span class="sxs-lookup"><span data-stu-id="e7290-156">In the Client.exe.config file on the client computer, change the address value of the endpoint to match the new address of your service.</span></span>  
  
9. <span data-ttu-id="e7290-157">Sur le client, ouvrez une Invite de commandes développeur pour Visual Studio avec des privilèges d’administrateur et exécutez ImportServiceCert.bat.</span><span class="sxs-lookup"><span data-stu-id="e7290-157">On the client, open a Developer Command Prompt for Visual Studio with administrative privileges and run ImportServiceCert.bat.</span></span> <span data-ttu-id="e7290-158">Cette opération importe le certificat de service du fichier Service.cer dans le magasin CurrentUser - TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="e7290-158">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
10. <span data-ttu-id="e7290-159">Sur l'ordinateur client, lancez Client.exe à partir d'une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="e7290-159">On the client computer, launch Client.exe from a command prompt.</span></span> <span data-ttu-id="e7290-160">Si le client et le service ne sont pas en mesure de communiquer, consultez [conseils de dépannage pour les exemples WCF](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="e7290-160">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="e7290-161">Pour procéder au nettoyage après exécution de l'exemple</span><span class="sxs-lookup"><span data-stu-id="e7290-161">To clean up after the sample</span></span>  
  
- <span data-ttu-id="e7290-162">Exécutez Cleanup.bat dans le dossier exemples une fois que vous avez terminé d'exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="e7290-162">Run Cleanup.bat in the samples folder after you have finished running the sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7290-163">Ce script ne supprime pas de certificat de service sur un client lors de l'exécution de cet exemple sur plusieurs ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="e7290-163">This script does not remove service certificates on a client when running this sample across computers.</span></span> <span data-ttu-id="e7290-164">Si vous avez exécuté des exemples de Windows Communication Foundation (WCF) qui utilisent des certificats sur des ordinateurs, veillez à effacer les certificats de service qui ont été installés dans le magasin CurrentUser-TrustedPeople.</span><span class="sxs-lookup"><span data-stu-id="e7290-164">If you have run Windows Communication Foundation (WCF) samples that use certificates across computers, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="e7290-165">Pour ce faire, utilisez la commande suivante : `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>`, par exemple : `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="e7290-165">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`.</span></span>  
  
## <a name="the-setup-batch-file"></a><span data-ttu-id="e7290-166">Le fichier de commandes d'installation</span><span class="sxs-lookup"><span data-stu-id="e7290-166">The Setup Batch File</span></span>  
 <span data-ttu-id="e7290-167">Le fichier de commandes Setup.bat inclus avec cet exemple permet de configurer le serveur avec les certificats pertinents pour exécuter une application auto-hébergée qui requiert une sécurité basée sur le certificat du serveur.</span><span class="sxs-lookup"><span data-stu-id="e7290-167">The Setup.bat batch file included with this sample allows you to configure the server with relevant certificates to run a self-hosted application that requires server certificate-based security.</span></span> <span data-ttu-id="e7290-168">Ce fichier de commandes doit être modifié pour fonctionner sur plusieurs ordinateurs ou sans hébergement.</span><span class="sxs-lookup"><span data-stu-id="e7290-168">This batch file must be modified to work across computers or to work in a non-hosted case.</span></span>  
  
 <span data-ttu-id="e7290-169">Les éléments suivants fournissent une vue d'ensemble des différentes sections des fichiers de commandes afin qu'ils puissent être modifiés pour s'exécuter dans la configuration appropriée.</span><span class="sxs-lookup"><span data-stu-id="e7290-169">The following provides a brief overview of the different sections of the batch files so that they can be modified to run in the appropriate configuration.</span></span>  
  
- <span data-ttu-id="e7290-170">Création du certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="e7290-170">Creating the server certificate.</span></span>  
  
     <span data-ttu-id="e7290-171">Les lignes suivantes du fichier de commandes Setup.bat créent le certificat de serveur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="e7290-171">The following lines from the Setup.bat batch file create the server certificate to be used.</span></span> <span data-ttu-id="e7290-172">La variable %SERVER_NAME% spécifie le nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="e7290-172">The %SERVER_NAME% variable specifies the server name.</span></span> <span data-ttu-id="e7290-173">Modifiez cette variable pour spécifier votre propre nom de serveur.</span><span class="sxs-lookup"><span data-stu-id="e7290-173">Change this variable to specify your own server name.</span></span> <span data-ttu-id="e7290-174">Ce fichier de commandes a comme valeur par défaut « localhost ».</span><span class="sxs-lookup"><span data-stu-id="e7290-174">This batch file defaults it to localhost.</span></span>  
  
     <span data-ttu-id="e7290-175">Le certificat est stocké dans le magasin My (personnel) sous l'emplacement de magasins LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="e7290-175">The certificate is stored in My (Personal) store under the LocalMachine store location.</span></span>  
  
    ```console
    echo ************  
    echo Server cert setup starting  
    echo %SERVER_NAME%  
    echo ************  
    echo making server cert  
    echo ************  
    makecert.exe -sr LocalMachine -ss MY -a sha1 -n CN=%SERVER_NAME% -sky exchange -pe  
    ```  
  
- <span data-ttu-id="e7290-176">Installation du certificat de serveur dans le magasin de certificats approuvés du client.</span><span class="sxs-lookup"><span data-stu-id="e7290-176">Installing the server certificate into the client's trusted certificate store.</span></span>  
  
     <span data-ttu-id="e7290-177">Les lignes suivantes du fichier de commandes Setup.bat copient le certificat de serveur dans le magasin de personnes de confiance du client.</span><span class="sxs-lookup"><span data-stu-id="e7290-177">The following lines in the Setup.bat batch file copy the server certificate into the client trusted people store.</span></span> <span data-ttu-id="e7290-178">Cette étape est requise car les certificats générés par Makecert.exe ne sont pas implicitement approuvés par le système client.</span><span class="sxs-lookup"><span data-stu-id="e7290-178">This step is required because certificates generated by Makecert.exe are not implicitly trusted by the client system.</span></span> <span data-ttu-id="e7290-179">Si vous disposez déjà d'un certificat associé à un certificat racine approuvé du client, par exemple d'un certificat émis par Microsoft, il n'est pas nécessaire d'ajouter le certificat du serveur au magasin de certificats du client.</span><span class="sxs-lookup"><span data-stu-id="e7290-179">If you already have a certificate that is rooted in a client trusted root certificate—for example, a Microsoft-issued certificate—this step of populating the client certificate store with the server certificate is not required.</span></span>  
  
    ```bat  
    certmgr.exe -add -r LocalMachine -s My -c -n %SERVER_NAME% -r CurrentUser -s TrustedPeople  
    ```
