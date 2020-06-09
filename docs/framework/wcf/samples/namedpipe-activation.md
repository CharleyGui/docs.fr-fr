---
title: NamedPipe Activation
ms.date: 03/30/2017
ms.assetid: f3c0437d-006c-442e-bfb0-6b29216e4e29
ms.openlocfilehash: 8d9a10b94c52514db611144352653b911d109056
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602464"
---
# <a name="namedpipe-activation"></a><span data-ttu-id="c70a2-102">NamedPipe Activation</span><span class="sxs-lookup"><span data-stu-id="c70a2-102">NamedPipe Activation</span></span>

<span data-ttu-id="c70a2-103">Cet exemple illustre l'hébergement d'un service qui utilise le service d'activation des processus Windows (WAS) pour activer un service qui communique sur des canaux nommés.</span><span class="sxs-lookup"><span data-stu-id="c70a2-103">This sample demonstrates hosting a service that uses Windows Process Activation Service (WAS) to activate a service that communicates over names pipes.</span></span> <span data-ttu-id="c70a2-104">Cet exemple est basé sur le [prise en main](getting-started-sample.md) et requiert l’exécution de Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="c70a2-104">This sample is based on the [Getting Started](getting-started-sample.md) and requires Windows Vista to run.</span></span>

> [!NOTE]
> <span data-ttu-id="c70a2-105">La procédure d'installation ainsi que les instructions de génération correspondant à cet exemple figurent en fin de rubrique.</span><span class="sxs-lookup"><span data-stu-id="c70a2-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c70a2-106">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="c70a2-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c70a2-107">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="c70a2-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="c70a2-108">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c70a2-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c70a2-109">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="c70a2-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\NamedPipeActivation`

## <a name="sample-details"></a><span data-ttu-id="c70a2-110">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="c70a2-110">Sample Details</span></span>

<span data-ttu-id="c70a2-111">L'exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergés dans un processus de travail activé par le service d'activation des processus Windows (WAS).</span><span class="sxs-lookup"><span data-stu-id="c70a2-111">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by the Windows Process Activation Services (WAS).</span></span> <span data-ttu-id="c70a2-112">L'activité du client est affichée dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="c70a2-112">Client activity is visible in the console window.</span></span>

<span data-ttu-id="c70a2-113">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="c70a2-113">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="c70a2-114">Le contrat est défini par l'interface `ICalculator`, qui expose des opérations mathématiques (addition, soustraction, multiplication, division) comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c70a2-114">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code.</span></span>

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]
public interface ICalculator
{
    [OperationContract]
    double Add(double n1, double n2);
    [OperationContract]
    double Subtract(double n1, double n2);
    [OperationContract]
    double Multiply(double n1, double n2);
    [OperationContract]
    double Divide(double n1, double n2);
}
```

<span data-ttu-id="c70a2-115">Le client fait des demandes synchrones à une opération mathématique donnée et l’implémentation du service calcule et retourne le résultat approprié.</span><span class="sxs-lookup"><span data-stu-id="c70a2-115">The client makes synchronous requests to a given math operation and the service implementation calculates and returns the appropriate result.</span></span>

```csharp
// Service class that implements the service contract.
public class CalculatorService : ICalculator
{
    public double Add(double n1, double n2)
    {
        return n1 + n2;
    }
    public double Subtract(double n1, double n2)
    {
        return n1 - n2;
    }
    public double Multiply(double n1, double n2)
    {
        return n1 * n2;
    }
    public double Divide(double n1, double n2)
    {
        return n1 / n2;
    }
}
```

<span data-ttu-id="c70a2-116">L'exemple utilise une liaison `netNamedPipeBinding` modifiée sans sécurité.</span><span class="sxs-lookup"><span data-stu-id="c70a2-116">The sample uses a modified `netNamedPipeBinding` binding with no security.</span></span> <span data-ttu-id="c70a2-117">La liaison est spécifiée dans les fichiers de configuration pour le client et le service.</span><span class="sxs-lookup"><span data-stu-id="c70a2-117">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="c70a2-118">Le type de liaison du service est spécifié dans l'attribut `binding` de l'élément du point de terminaison comme illustré dans l'exemple de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="c70a2-118">The binding type for the service is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>

<span data-ttu-id="c70a2-119">Si vous souhaitez utiliser une liaison de canal nommé sécurisée, remplacez le mode de sécurité du serveur par le paramètre de sécurité souhaité et exécutez à nouveau svcutil.exe sur le client pour obtenir un fichier de configuration client mis à jour.</span><span class="sxs-lookup"><span data-stu-id="c70a2-119">If you want use a secured named pipe binding, change the server's security mode to the desired security setting and run svcutil.exe again on the client to obtain an updated client configuration file.</span></span>

```xml
<system.serviceModel>
        <services>
            <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">

        <!-- This endpoint is exposed at the base address provided by host: net.pipe://localhost/servicemodelsamples/service.svc  -->
        <endpoint address=""
                  binding="netNamedPipeBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.pipe://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexNamedPipeBinding"
                  contract="IMetadataExchange" />
      </service>
        </services>
        <bindings>
            <netNamedPipeBinding>
                <binding name="Binding1" >
                    <security mode = "None">
                    </security>
                </binding >
            </netNamedPipeBinding>
        </bindings>

    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>

  </system.serviceModel>
```

<span data-ttu-id="c70a2-120">Les informations sur le point de terminaison du client sont configurées comme illustré dans l'exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="c70a2-120">The client’s endpoint information is configured as shown in the following sample code.</span></span>

```xml
<system.serviceModel>

    <client>
      <endpoint name=""
                          address="net.pipe://localhost/servicemodelsamples/service.svc"
                          binding="netNamedPipeBinding"
                          bindingConfiguration="Binding1"
                          contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>

    <bindings>

      <!--  Following is the expanded configuration section for a NetNamedPipeBinding.
            Each property is configured with the default value. -->

      <netNamedPipeBinding>
        <binding name="Binding1"
                         maxBufferSize="65536"
                         maxConnections="10">
          <security mode = "None">
          </security>
        </binding >

      </netNamedPipeBinding>
    </bindings>

  </system.serviceModel>
```

<span data-ttu-id="c70a2-121">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="c70a2-121">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="c70a2-122">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="c70a2-122">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c70a2-123">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="c70a2-123">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="c70a2-124">Vérifiez qu’IIS 7,0 est installé.</span><span class="sxs-lookup"><span data-stu-id="c70a2-124">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="c70a2-125">IIS 7,0 est requis pour l’activation WAS.</span><span class="sxs-lookup"><span data-stu-id="c70a2-125">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="c70a2-126">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c70a2-126">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="c70a2-127">En outre, vous devez installer les composants d’activation non HTTP WCF :</span><span class="sxs-lookup"><span data-stu-id="c70a2-127">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="c70a2-128">Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="c70a2-128">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="c70a2-129">Sélectionnez **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="c70a2-129">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="c70a2-130">Cliquez sur **activer ou désactiver des composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="c70a2-130">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="c70a2-131">Développez le nœud **Microsoft .NET Framework 3,0** et cochez la Windows Communication Foundation fonctionnalité d' **activation non-http** .</span><span class="sxs-lookup"><span data-stu-id="c70a2-131">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="c70a2-132">Configurez le service d'activation des processus Windows pour prendre en charge l'activation de canal nommé.</span><span class="sxs-lookup"><span data-stu-id="c70a2-132">Configure the Windows Process Activation Service (WAS) to support named pipe activation.</span></span>

    <span data-ttu-id="c70a2-133">Par commodité, les deux étapes suivantes sont implémentées dans un fichier de commandes appelé AddNetPipeSiteBinding.cmd et qui se trouve dans le répertoire d'exemple.</span><span class="sxs-lookup"><span data-stu-id="c70a2-133">As a convenience, the following two steps are implemented in a batch file called AddNetPipeSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="c70a2-134">Pour prendre en charge l’activation net.pipe, le site web par défaut doit d’abord être lié au protocole net.pipe.</span><span class="sxs-lookup"><span data-stu-id="c70a2-134">To support net.pipe activation, the default Web site must first be bound to the net.pipe protocol.</span></span> <span data-ttu-id="c70a2-135">Cela peut être fait à l'aide d'appcmd.exe, installé avec l'ensemble d'outils de gestion d'IIS 7.0.</span><span class="sxs-lookup"><span data-stu-id="c70a2-135">This can be done using appcmd.exe, which is installed with the IIS 7.0 management toolset.</span></span> <span data-ttu-id="c70a2-136">À partir d'une invite de commandes avec élévation de privilèges (administrateur), exécutez la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="c70a2-136">From an elevated (administrator) command prompt, run the following command.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        -+bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="c70a2-137">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="c70a2-137">This command is a single line of text.</span></span>

        <span data-ttu-id="c70a2-138">Cette commande ajoute une liaison de site net.pipe au site web par défaut.</span><span class="sxs-lookup"><span data-stu-id="c70a2-138">This command adds a net.pipe site binding to the default Web site.</span></span>

    2. <span data-ttu-id="c70a2-139">Bien que toutes les applications d’un site partagent une liaison commune net.pipe, chaque application peut activer individuellement la prise en charge net.pipe.</span><span class="sxs-lookup"><span data-stu-id="c70a2-139">Although all applications within a site share a common net.pipe binding, each application can enable net.pipe support individually.</span></span> <span data-ttu-id="c70a2-140">Pour activer net.pipe pour l'application /servicemodelsamples, exécutez la commande suivante à partir d'une invite de commandes avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="c70a2-140">To enable net.pipe for the /servicemodelsamples application, run the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.pipe
        ```

        > [!NOTE]
        > <span data-ttu-id="c70a2-141">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="c70a2-141">This command is a single line of text.</span></span>

        <span data-ttu-id="c70a2-142">Cette commande permet d’accéder à l’application/servicemodelsamples à l’aide de `http://localhost/servicemodelsamples` et de `net.tcp://localhost/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="c70a2-142">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="c70a2-143">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c70a2-143">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>

5. <span data-ttu-id="c70a2-144">Supprimez la liaison du site net.pipe que vous avez ajoutée pour cet exemple.</span><span class="sxs-lookup"><span data-stu-id="c70a2-144">Remove the net.pipe site binding you added for this sample.</span></span>

    <span data-ttu-id="c70a2-145">Par commodité, les deux étapes suivantes sont implémentées dans un fichier de commandes appelé RemoveNetPipeSiteBinding.cmd et qui se trouve dans le répertoire d'exemple :</span><span class="sxs-lookup"><span data-stu-id="c70a2-145">As a convenience, the following two steps are implemented in a batch file called RemoveNetPipeSiteBinding.cmd located in the sample directory:</span></span>

    1. <span data-ttu-id="c70a2-146">Supprimez net.tcp de la liste de protocoles actifs en exécutant la commande suivante à partir d'une invite de commandes avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="c70a2-146">Remove net.tcp from the list of enabled protocols by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="c70a2-147">Cette commande doit être entrée comme une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="c70a2-147">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="c70a2-148">Supprimez la liaison du site net.tcp en exécutant la commande suivante à partir d’une invite de commandes avec élévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="c70a2-148">Remove the net.tcp site binding by running the following command from an elevated command prompt.</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" --bindings.[protocol='net.pipe',bindingInformation='*']
        ```

        > [!NOTE]
        > <span data-ttu-id="c70a2-149">Cette commande doit être tapée comme une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="c70a2-149">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="c70a2-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c70a2-150">See also</span></span>

- <span data-ttu-id="c70a2-151">[Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c70a2-151">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
