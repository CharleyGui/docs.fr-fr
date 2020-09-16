---
title: 'Procédure : héberger un service WCF dans un service Windows managé'
description: Découvrez comment créer un service WCF hébergé par un service Windows. Cette option d'hébergement est disponible dans toutes les versions de Windows.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8e37363b-4dad-4fb6-907f-73c30fac1d9a
ms.openlocfilehash: 21d3dcb05e48154eb3f9f10d8308dc14bd046ae1
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546339"
---
# <a name="how-to-host-a-wcf-service-in-a-managed-windows-service"></a><span data-ttu-id="99c63-104">Procédure : héberger un service WCF dans un service Windows managé</span><span class="sxs-lookup"><span data-stu-id="99c63-104">How to: Host a WCF Service in a Managed Windows Service</span></span>

<span data-ttu-id="99c63-105">Cette rubrique décrit les étapes de base requises pour créer un service Windows Communication Foundation (WCF) qui est hébergé par un service Windows.</span><span class="sxs-lookup"><span data-stu-id="99c63-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted by a Windows Service.</span></span> <span data-ttu-id="99c63-106">Le scénario est activé par l’option d’hébergement du service Windows gérée qui est un service WCF de longue durée hébergé en dehors de Internet Information Services (IIS) dans un environnement sécurisé qui n’est pas activé pour les messages.</span><span class="sxs-lookup"><span data-stu-id="99c63-106">The scenario is enabled by the managed Windows service hosting option that is a long-running WCF service hosted outside of Internet Information Services (IIS) in a secure environment that is not message activated.</span></span> <span data-ttu-id="99c63-107">La durée de vie du service est contrôlée par le système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="99c63-107">The lifetime of the service is controlled instead by the operating system.</span></span> <span data-ttu-id="99c63-108">Cette option d'hébergement est disponible dans toutes les versions de Windows.</span><span class="sxs-lookup"><span data-stu-id="99c63-108">This hosting option is available in all versions of Windows.</span></span>

<span data-ttu-id="99c63-109">Les services Windows peuvent être gérés avec Microsoft.ManagementConsole.SnapIn dans MMC (Microsoft Management Console) et peuvent être configurés pour démarrer automatiquement lorsque le système démarre.</span><span class="sxs-lookup"><span data-stu-id="99c63-109">Windows services can be managed with the Microsoft.ManagementConsole.SnapIn in Microsoft Management Console (MMC) and can be configured to start up automatically when the system boots up.</span></span> <span data-ttu-id="99c63-110">Cette option d’hébergement consiste à inscrire le domaine d’application (AppDomain) qui héberge un service WCF en tant que service Windows géré afin que la durée de vie du processus soit contrôlée par le gestionnaire de contrôle des services (SCM) pour les services Windows.</span><span class="sxs-lookup"><span data-stu-id="99c63-110">This hosting option consists of registering the application domain (AppDomain) that hosts a WCF service as a managed Windows service so that the process lifetime of the service is controlled by the Service Control Manager (SCM) for Windows services.</span></span>

<span data-ttu-id="99c63-111">Le code du service inclut l'implémentation du contrat de service, d'une classe de service Windows et d'une classe Installer.</span><span class="sxs-lookup"><span data-stu-id="99c63-111">The service code includes a service implementation of the service contract, a Windows Service class, and an installer class.</span></span> <span data-ttu-id="99c63-112">La classe d’implémentation de service, `CalculatorService` , est un service WCF.</span><span class="sxs-lookup"><span data-stu-id="99c63-112">The service implementation class, `CalculatorService`, is a WCF service.</span></span> <span data-ttu-id="99c63-113">Le `CalculatorWindowsService` est un service Windows.</span><span class="sxs-lookup"><span data-stu-id="99c63-113">The `CalculatorWindowsService` is a Windows service.</span></span> <span data-ttu-id="99c63-114">Pour prétendre au titre de service Windows, la classe hérite de la `ServiceBase` et implémente les méthodes `OnStart` et `OnStop`.</span><span class="sxs-lookup"><span data-stu-id="99c63-114">To qualify as a Windows service, the class inherits from `ServiceBase` and implements the `OnStart` and `OnStop` methods.</span></span> <span data-ttu-id="99c63-115">Dans la méthode `OnStart`, un objet <xref:System.ServiceModel.ServiceHost> est créé pour le type `CalculatorService` et est ouvert.</span><span class="sxs-lookup"><span data-stu-id="99c63-115">In `OnStart`, a <xref:System.ServiceModel.ServiceHost> is created for the `CalculatorService` type and opened.</span></span> <span data-ttu-id="99c63-116">Dans la méthode `OnStop`, le service est arrêté et éliminé.</span><span class="sxs-lookup"><span data-stu-id="99c63-116">In `OnStop`, the service is stopped and disposed.</span></span> <span data-ttu-id="99c63-117">L'hôte est également chargé de fournir une adresse de base à l'hôte de service, qui a été configuré dans les paramètres d'application.</span><span class="sxs-lookup"><span data-stu-id="99c63-117">The host is also responsible for providing a base address to the service host, which has been configured in application settings.</span></span> <span data-ttu-id="99c63-118">La classe Installer, qui hérite de <xref:System.Configuration.Install.Installer>, permet à l'outil Installutil.exe d'installer le programme comme un service Windows.</span><span class="sxs-lookup"><span data-stu-id="99c63-118">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as a Windows service by the Installutil.exe tool.</span></span>

## <a name="construct-the-service-and-provide-the-hosting-code"></a><span data-ttu-id="99c63-119">Construction du service et ajout du code d'hébergement</span><span class="sxs-lookup"><span data-stu-id="99c63-119">Construct the service and provide the hosting code</span></span>

1. <span data-ttu-id="99c63-120">Créez un nouveau projet d' **application console** Visual Studio appelé **service**.</span><span class="sxs-lookup"><span data-stu-id="99c63-120">Create a new Visual Studio **Console app** project called **Service**.</span></span>

2. <span data-ttu-id="99c63-121">Renommez Program.cs en Service.cs.</span><span class="sxs-lookup"><span data-stu-id="99c63-121">Rename Program.cs to Service.cs.</span></span>

3. <span data-ttu-id="99c63-122">Remplacez l’espace de noms par `Microsoft.ServiceModel.Samples` .</span><span class="sxs-lookup"><span data-stu-id="99c63-122">Change the namespace to `Microsoft.ServiceModel.Samples`.</span></span>

4. <span data-ttu-id="99c63-123">Ajoutez des références aux assemblys suivants :</span><span class="sxs-lookup"><span data-stu-id="99c63-123">Add references to the following assemblies:</span></span>

    - <span data-ttu-id="99c63-124">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="99c63-124">System.ServiceModel.dll</span></span>

    - <span data-ttu-id="99c63-125">System.ServiceProcess.dll</span><span class="sxs-lookup"><span data-stu-id="99c63-125">System.ServiceProcess.dll</span></span>

    - <span data-ttu-id="99c63-126">System.Configuration.Install.dll</span><span class="sxs-lookup"><span data-stu-id="99c63-126">System.Configuration.Install.dll</span></span>

5. <span data-ttu-id="99c63-127">Ajoutez les instructions using suivantes à Service.cs.</span><span class="sxs-lookup"><span data-stu-id="99c63-127">Add the following using statements to Service.cs.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#0)]
     [!code-vb[c_HowTo_HostInNTService#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#0)]

6. <span data-ttu-id="99c63-128">Définissez le contrat de service `ICalculator`, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="99c63-128">Define the `ICalculator` service contract as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#1)]
     [!code-vb[c_HowTo_HostInNTService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#1)]

7. <span data-ttu-id="99c63-129">Implémentez le contrat de service dans une classe appelée `CalculatorService`, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="99c63-129">Implement the service contract in a class called `CalculatorService` as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#2)]
     [!code-vb[c_HowTo_HostInNTService#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#2)]

8. <span data-ttu-id="99c63-130">Créez une classe appelée `CalculatorWindowsService` qui hérite de la classe <xref:System.ServiceProcess.ServiceBase>.</span><span class="sxs-lookup"><span data-stu-id="99c63-130">Create a new class called `CalculatorWindowsService` that inherits from the <xref:System.ServiceProcess.ServiceBase> class.</span></span> <span data-ttu-id="99c63-131">Ajoutez une variable locale appelée `serviceHost` pour faire référence à l'instance <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="99c63-131">Add a local variable called `serviceHost` to reference the <xref:System.ServiceModel.ServiceHost> instance.</span></span> <span data-ttu-id="99c63-132">Définissez la méthode `Main` qui appelle `ServiceBase.Run(new CalculatorWindowsService)`</span><span class="sxs-lookup"><span data-stu-id="99c63-132">Define the `Main` method that calls `ServiceBase.Run(new CalculatorWindowsService)`</span></span>

     [!code-csharp[c_HowTo_HostInNTService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#3)]
     [!code-vb[c_HowTo_HostInNTService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#3)]

9. <span data-ttu-id="99c63-133">Substituez la méthode <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> en créant et en ouvrant une nouvelle instance <xref:System.ServiceModel.ServiceHost>, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="99c63-133">Override the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> method by creating and opening a new <xref:System.ServiceModel.ServiceHost> instance as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#4)]
     [!code-vb[c_HowTo_HostInNTService#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#4)]

10. <span data-ttu-id="99c63-134">Substituez la méthode <xref:System.ServiceProcess.ServiceBase.OnStop%2A> fermant <xref:System.ServiceModel.ServiceHost>, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="99c63-134">Override the <xref:System.ServiceProcess.ServiceBase.OnStop%2A> method closing the <xref:System.ServiceModel.ServiceHost> as shown in the following code.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#5)]
     [!code-vb[c_HowTo_HostInNTService#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#5)]

11. <span data-ttu-id="99c63-135">Créez une classe appelée `ProjectInstaller` qui hérite de <xref:System.Configuration.Install.Installer> et qui est marquée avec <xref:System.ComponentModel.RunInstallerAttribute> défini avec la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="99c63-135">Create a new class called `ProjectInstaller` that inherits from <xref:System.Configuration.Install.Installer> and that is marked with the <xref:System.ComponentModel.RunInstallerAttribute> set to `true`.</span></span> <span data-ttu-id="99c63-136">Cela permet au service Windows d'être installé par l'outil Installutil.exe.</span><span class="sxs-lookup"><span data-stu-id="99c63-136">This allows the Windows service to be installed by the Installutil.exe tool.</span></span>

     [!code-csharp[c_HowTo_HostInNTService#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#6)]
     [!code-vb[c_HowTo_HostInNTService#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#6)]

12. <span data-ttu-id="99c63-137">Supprimez la classe `Service` qui a été générée lors de la création du projet.</span><span class="sxs-lookup"><span data-stu-id="99c63-137">Remove the `Service` class that was generated when you created the project.</span></span>

13. <span data-ttu-id="99c63-138">Ajoutez un fichier de configuration d'application au projet.</span><span class="sxs-lookup"><span data-stu-id="99c63-138">Add an application configuration file to the project.</span></span> <span data-ttu-id="99c63-139">Remplacez le contenu du fichier par le fichier XML de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="99c63-139">Replace the contents of the file with the following configuration XML.</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.serviceModel>    <services>
          <!-- This section is optional with the new configuration model
               introduced in .NET Framework 4. -->
          <service name="Microsoft.ServiceModel.Samples.CalculatorService"
                   behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->
            <endpoint address=""
                      binding="wsHttpBinding"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
            <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
            <endpoint address="mex"
                      binding="mexHttpBinding"
                      contract="IMetadataExchange" />
          </service>
        </services>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceMetadata httpGetEnabled="true"/>
              <serviceDebug includeExceptionDetailInFaults="False"/>
            </behavior>
          </serviceBehaviors>
        </behaviors>
      </system.serviceModel>
    </configuration>
    ```

     <span data-ttu-id="99c63-140">Cliquez avec le bouton droit sur le fichier App.config dans le **Explorateur de solutions** et sélectionnez **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="99c63-140">Right click the App.config file in the **Solution Explorer** and select **Properties**.</span></span> <span data-ttu-id="99c63-141">Sous **copier dans le répertoire de sortie** , sélectionnez **copier si plus récent**.</span><span class="sxs-lookup"><span data-stu-id="99c63-141">Under **Copy to Output Directory** select **Copy if Newer**.</span></span>

     <span data-ttu-id="99c63-142">L'exemple spécifie explicitement les points de terminaison dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="99c63-142">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="99c63-143">Si vous n'ajoutez pas de points de terminaison au service, le runtime ajoute les points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="99c63-143">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="99c63-144">Dans cet exemple, étant donné que le service a un <xref:System.ServiceModel.Description.ServiceMetadataBehavior> défini sur la valeur `true`, la publication des métadonnées est également activée pour votre service.</span><span class="sxs-lookup"><span data-stu-id="99c63-144">In this example, because the service has a <xref:System.ServiceModel.Description.ServiceMetadataBehavior> set to `true`, your service also has publishing metadata enabled.</span></span> <span data-ttu-id="99c63-145">Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [Configuration simplifiée](../simplified-configuration.md) et [Configuration simplifiée pour les services WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="99c63-145">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="install-and-run-the-service"></a><span data-ttu-id="99c63-146">Démarrez et exécutez le service.</span><span class="sxs-lookup"><span data-stu-id="99c63-146">Install and run the service</span></span>

1. <span data-ttu-id="99c63-147">Générez la solution pour créer l'exécutable `Service.exe`.</span><span class="sxs-lookup"><span data-stu-id="99c63-147">Build the solution to create the `Service.exe` executable.</span></span>

2. <span data-ttu-id="99c63-148">Ouvrez Invite de commandes développeur pour Visual Studio et accédez au répertoire du projet.</span><span class="sxs-lookup"><span data-stu-id="99c63-148">Open Developer Command Prompt for Visual Studio and navigate to the project directory.</span></span> <span data-ttu-id="99c63-149">Pour installer le service Windows, tapez `installutil bin\service.exe` à l'invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="99c63-149">Type `installutil bin\service.exe` at the command prompt to install the Windows service.</span></span>

     <span data-ttu-id="99c63-150">Tapez `services.msc` à l'invite de commandes pour accéder au Gestionnaire de contrôle des services (SCM).</span><span class="sxs-lookup"><span data-stu-id="99c63-150">Type `services.msc` at the command prompt to access the Service Control Manager (SCM).</span></span> <span data-ttu-id="99c63-151">Le service Windows doit apparaître dans les services comme « WCFWindowsServiceSample ».</span><span class="sxs-lookup"><span data-stu-id="99c63-151">The Windows service should appear in Services as "WCFWindowsServiceSample".</span></span> <span data-ttu-id="99c63-152">Le service WCF ne peut répondre aux clients que si le service Windows est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="99c63-152">The WCF service can only respond to clients if the Windows service is running.</span></span> <span data-ttu-id="99c63-153">Pour démarrer le service, cliquez avec le bouton droit sur celui-ci dans le SCM et sélectionnez « Démarrer », ou tapez **net start WCFWindowsServiceSample** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="99c63-153">To start the service, right-click it in the SCM and select "Start", or type **net start WCFWindowsServiceSample** at the command prompt.</span></span>

3. <span data-ttu-id="99c63-154">Si vous apportez des modifications au service, vous devez d'abord l'arrêter et le désinstaller.</span><span class="sxs-lookup"><span data-stu-id="99c63-154">If you make changes to the service, you must first stop it and uninstall it.</span></span> <span data-ttu-id="99c63-155">Pour arrêter le service, cliquez avec le bouton droit sur le service dans le SCM et sélectionnez « arrêter », ou **tapez net stop WCFWindowsServiceSample** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="99c63-155">To stop the service, right-click the service in the SCM and select "Stop", or **type net stop WCFWindowsServiceSample** at the command prompt.</span></span> <span data-ttu-id="99c63-156">Notez que si vous arrêtez le service Windows puis exécutez un client, une exception <xref:System.ServiceModel.EndpointNotFoundException> se produit lorsqu'un client tente d'accéder au service.</span><span class="sxs-lookup"><span data-stu-id="99c63-156">Note that if you stop the Windows service and then run a client, an <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="99c63-157">Pour désinstaller le service Windows, tapez **installutil/u bin\service.exe** à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="99c63-157">To uninstall the Windows service type **installutil /u bin\service.exe** at the command prompt.</span></span>

## <a name="example"></a><span data-ttu-id="99c63-158"> Exemple</span><span class="sxs-lookup"><span data-stu-id="99c63-158">Example</span></span>

<span data-ttu-id="99c63-159">Voici une liste complète du code utilisé dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="99c63-159">The following is a complete listing of the code used by this topic:</span></span>

[!code-csharp[c_HowTo_HostInNTService#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostinntservice/cs/service.cs#8)]
[!code-vb[c_HowTo_HostInNTService#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostinntservice/vb/service.vb#8)]

<span data-ttu-id="99c63-160">Comme pour l'option d'auto-hébergement, l'environnement d'hébergement du service Windows requiert que le code d'hébergement soit écrit dans le cadre de l'application.</span><span class="sxs-lookup"><span data-stu-id="99c63-160">Like the "Self-Hosting" option, the Windows service hosting environment requires that some hosting code be written as part of the application.</span></span> <span data-ttu-id="99c63-161">Le service est implémenté en tant qu'application console et contient son propre code d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="99c63-161">The service is implemented as a console application and contains its own hosting code.</span></span> <span data-ttu-id="99c63-162">Dans d'autres environnements d'hébergement, tels que le service d'activation des processus Windows (WAS) dans les services IIS (Internet Information Services), il n'est pas nécessaire que les développeurs écrivent le code d'hébergement.</span><span class="sxs-lookup"><span data-stu-id="99c63-162">In other hosting environments, such as Windows Process Activation Service (WAS) hosting in Internet Information Services (IIS), it is not necessary for developers to write hosting code.</span></span>

## <a name="see-also"></a><span data-ttu-id="99c63-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99c63-163">See also</span></span>

- [<span data-ttu-id="99c63-164">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="99c63-164">Simplified Configuration</span></span>](../simplified-configuration.md)
- [<span data-ttu-id="99c63-165">Hébergement dans une application managée</span><span class="sxs-lookup"><span data-stu-id="99c63-165">Hosting in a Managed Application</span></span>](hosting-in-a-managed-application.md)
- [<span data-ttu-id="99c63-166">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="99c63-166">Hosting Services</span></span>](../hosting-services.md)
- <span data-ttu-id="99c63-167">[Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="99c63-167">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
