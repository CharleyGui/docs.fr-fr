---
title: Activation de TCP
ms.date: 03/30/2017
ms.assetid: bf8c215c-0228-4f4f-85c2-e33794ec09a7
ms.openlocfilehash: 3487d84a63b2838dc1b55fdf3f41b410fcfc2e63
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094876"
---
# <a name="tcp-activation"></a><span data-ttu-id="30c55-102">Activation de TCP</span><span class="sxs-lookup"><span data-stu-id="30c55-102">TCP Activation</span></span>

<span data-ttu-id="30c55-103">Cet exemple illustre l'hébergement d'un service utilisant les services d'activation des processus Windows (WAS, Windows Process Activation Services) afin d'activer un service qui communique à l'aide du protocole net.tcp.</span><span class="sxs-lookup"><span data-stu-id="30c55-103">This sample demonstrates hosting a service that uses Windows Process Activation Services (WAS) to activate a service that communicates over the net.tcp protocol.</span></span> <span data-ttu-id="30c55-104">Cet exemple est basé sur le [prise en main](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="30c55-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>

> [!NOTE]
> <span data-ttu-id="30c55-105">La procédure d'installation ainsi que les instructions de génération relatives à cet exemple figurent à la fin de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="30c55-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30c55-106">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="30c55-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="30c55-107">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="30c55-107">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="30c55-108">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="30c55-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="30c55-109">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="30c55-109">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WASHost\TCPActivation`

<span data-ttu-id="30c55-110">L'exemple se compose d'un programme de console client (.exe) et d'une bibliothèque de service (.dll) hébergée dans un processus de traitement activé par le service WAS.</span><span class="sxs-lookup"><span data-stu-id="30c55-110">The sample consists of a client console program (.exe) and a service library (.dll) hosted in a worker process activated by WAS.</span></span> <span data-ttu-id="30c55-111">L'activité du client est affichée dans la fenêtre de console.</span><span class="sxs-lookup"><span data-stu-id="30c55-111">Client activity is visible in the console window.</span></span>

<span data-ttu-id="30c55-112">Le service implémente un contrat qui définit un modèle de communication demande-réponse.</span><span class="sxs-lookup"><span data-stu-id="30c55-112">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="30c55-113">Le contrat est défini par l'interface `ICalculator`, laquelle expose des opérations mathématiques (addition, soustraction, multiplication et division), tel qu'illustré dans l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="30c55-113">The contract is defined by the `ICalculator` interface, which exposes math operations (Add, Subtract, Multiply, and Divide), as shown in the following sample code:</span></span>

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

<span data-ttu-id="30c55-114">L'implémentation de service calcule, puis retourne le résultat approprié :</span><span class="sxs-lookup"><span data-stu-id="30c55-114">The service implementation calculates and returns the appropriate result:</span></span>

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

<span data-ttu-id="30c55-115">Dans la version de liaison net.tcp utilisée par l'exemple, le partage de port TCP est activé et la sécurité est désactivée.</span><span class="sxs-lookup"><span data-stu-id="30c55-115">The sample uses a variant of the net.tcp binding with TCP port sharing enabled and security turned off.</span></span> <span data-ttu-id="30c55-116">Si vous souhaitez utiliser une liaison TCP sécurisée, modifiez le mode de sécurité du serveur en fonction du paramètre souhaité, puis exécutez de nouveau l'outil Svcutil.exe sur le client afin de générer un fichier de configuration à jour pour ce dernier.</span><span class="sxs-lookup"><span data-stu-id="30c55-116">If you want to use a secured TCP binding, change the server's security mode to the desired setting and re-run Svcutil.exe on the client to generate an update client configuration file.</span></span>

<span data-ttu-id="30c55-117">L'exemple suivant contient la configuration du service :</span><span class="sxs-lookup"><span data-stu-id="30c55-117">The following sample shows the configuration for the service:</span></span>

```xml
<system.serviceModel>

    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: net.tcp://localhost/servicemodelsamples/service.svc  -->
        <endpoint binding="netTcpBinding" bindingConfiguration="PortSharingBinding"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at net.tcp://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexTcpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netTcpBinding>
        <binding name="PortSharingBinding" portSharingEnabled="true">
          <security mode="None" />
        </binding>
      </netTcpBinding>
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

<span data-ttu-id="30c55-118">Le point de terminaison du client est configuré tel qu'illustré dans l'exemple de code suivant :</span><span class="sxs-lookup"><span data-stu-id="30c55-118">The client's endpoint is configured as shown in the following sample code:</span></span>

```xml
<system.serviceModel>
    <bindings>
        <netTcpBinding>
          <binding name="NetTcpBinding_ICalculator">
            <security mode="None"/>
          </binding>
        </netTcpBinding>
    </bindings>
    <client>
        <endpoint address="net.tcp://localhost/servicemodelsamples/service.svc"
            binding="netTcpBinding" bindingConfiguration="NetTcpBinding_ICalculator"
            contract="Microsoft.ServiceModel.Samples.ICalculator" name="NetTcpBinding_ICalculator" />
    </client>
</system.serviceModel>
```

<span data-ttu-id="30c55-119">Lorsque vous exécutez l'exemple, les demandes et réponses d'opération s'affichent dans la fenêtre de console du client.</span><span class="sxs-lookup"><span data-stu-id="30c55-119">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="30c55-120">Appuyez sur Entrée dans la fenêtre du client pour l'arrêter.</span><span class="sxs-lookup"><span data-stu-id="30c55-120">Press ENTER in the client window to shut down the client.</span></span>

```console
Add(100,15.99) = 115.99
Subtract(145,76.54) = 68.46
Multiply(9,81.25) = 731.25
Divide(22,7) = 3.14285714285714

Press <ENTER> to terminate client.
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="30c55-121">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="30c55-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="30c55-122">Vérifiez qu’IIS 7,0 est installé.</span><span class="sxs-lookup"><span data-stu-id="30c55-122">Ensure that IIS 7.0 is installed.</span></span> <span data-ttu-id="30c55-123">IIS 7,0 est requis pour l’activation WAS.</span><span class="sxs-lookup"><span data-stu-id="30c55-123">IIS 7.0 is required for WAS activation.</span></span>

2. <span data-ttu-id="30c55-124">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30c55-124">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

    <span data-ttu-id="30c55-125">En outre, vous devez installer les composants d’activation non HTTP WCF :</span><span class="sxs-lookup"><span data-stu-id="30c55-125">In addition, you must install the WCF non-HTTP activation components:</span></span>

    1. <span data-ttu-id="30c55-126">Dans le menu **Démarrer**, cliquez sur **Panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="30c55-126">From the **Start** menu, choose **Control Panel**.</span></span>

    2. <span data-ttu-id="30c55-127">Sélectionnez **programmes et fonctionnalités**.</span><span class="sxs-lookup"><span data-stu-id="30c55-127">Select **Programs and Features**.</span></span>

    3. <span data-ttu-id="30c55-128">Cliquez sur **activer ou désactiver des composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="30c55-128">Click **Turn Windows Components on or Off**.</span></span>

    4. <span data-ttu-id="30c55-129">Développez le nœud **Microsoft .NET Framework 3,0** et cochez la Windows Communication Foundation fonctionnalité d' **activation non-http** .</span><span class="sxs-lookup"><span data-stu-id="30c55-129">Expand the **Microsoft .NET Framework 3.0** node and check the **Windows Communication Foundation Non-HTTP Activation** feature.</span></span>

3. <span data-ttu-id="30c55-130">Configurez le servie WAS afin d'assurer la prise en charge de l'activation TCP.</span><span class="sxs-lookup"><span data-stu-id="30c55-130">Configure WAS to support TCP activation.</span></span>

    <span data-ttu-id="30c55-131">Pour des raisons pratiques, les deux étapes suivantes sont implémentées dans le fichier de commandes AddNetTcpSiteBinding.cmd se trouvant dans le répertoire de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="30c55-131">As a convenience, the following two steps are implemented in a batch file called AddNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="30c55-132">Pour assurer la prise en charge de l'activation de net.tcp, le site Web par défaut doit d'abord être lié à un port net.tcp.</span><span class="sxs-lookup"><span data-stu-id="30c55-132">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="30c55-133">Vous pouvez utiliser Appcmd.exe, installé avec les outils de gestion des services IIS 7.0, à cette fin.</span><span class="sxs-lookup"><span data-stu-id="30c55-133">This can be done using Appcmd.exe, which is installed with the Internet Information Services 7.0 (IIS) management toolset.</span></span> <span data-ttu-id="30c55-134">Sous un compte d'administrateur, exécutez la commande suivante à partir d'une invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="30c55-134">From an administrator-level command prompt, run the following command:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!TIP]
        > <span data-ttu-id="30c55-135">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="30c55-135">This command is a single line of text.</span></span> <span data-ttu-id="30c55-136">Cette commande ajoute une liaison de site net.tcp au site Web par défaut qui écoute sur le port TCP 808, quel que soit le nom d’hôte.</span><span class="sxs-lookup"><span data-stu-id="30c55-136">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any hostname.</span></span>

    2. <span data-ttu-id="30c55-137">Bien que toutes les applications d'un site partagent la même liaison net.tcp, chacune d'elle peut activer de manière individuelle la prise en charge net.pipe.</span><span class="sxs-lookup"><span data-stu-id="30c55-137">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="30c55-138">Afin d'activer le net.tcp pour l'application /servicemodelsamples, exécutez la commande suivante à partir d'une invite de commandes, sous un compte d'administrateur :</span><span class="sxs-lookup"><span data-stu-id="30c55-138">To enable net.tcp for the /servicemodelsamples application, run the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http,net.tcp
        ```

        > [!NOTE]
        > <span data-ttu-id="30c55-139">Cette commande est une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="30c55-139">This command is a single line of text.</span></span> <span data-ttu-id="30c55-140">Cette commande permet d’accéder à l’application/servicemodelsamples à l’aide de `http://localhost/servicemodelsamples` et `net.tcp://localhost/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="30c55-140">This command enables the /servicemodelsamples application to be accessed using both `http://localhost/servicemodelsamples` and `net.tcp://localhost/servicemodelsamples`.</span></span>

4. <span data-ttu-id="30c55-141">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30c55-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

5. <span data-ttu-id="30c55-142">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="30c55-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

    <span data-ttu-id="30c55-143">Supprimez la liaison de site net.tcp que vous avez ajoutée dans le cadre de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="30c55-143">Remove the net.tcp site binding you added for this sample.</span></span>

    <span data-ttu-id="30c55-144">Pour des raisons pratiques, les deux étapes suivantes sont implémentées dans le fichier de commandes RemoveNetTcpSiteBinding.cmd situé dans le répertoire de l'exemple.</span><span class="sxs-lookup"><span data-stu-id="30c55-144">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>

    1. <span data-ttu-id="30c55-145">Supprimez le protocole net.tcp de la liste des protocoles activés en exécutant la commande suivante à partir d'une invite de commandes en tant qu'administrateur :</span><span class="sxs-lookup"><span data-stu-id="30c55-145">Remove net.tcp from the list of enabled protocols by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples" /enabledProtocols:http
        ```

        > [!NOTE]
        > <span data-ttu-id="30c55-146">Cette commande doit être entrée comme une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="30c55-146">This command must be entered as a single line of text.</span></span>

    2. <span data-ttu-id="30c55-147">Supprimez la liaison de site net.tcp en exécutant la commande suivante à partir d'une invite de commandes en tant qu'administrateur :</span><span class="sxs-lookup"><span data-stu-id="30c55-147">Remove the net.tcp site binding by running the following command from an administrator-level command prompt:</span></span>

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > <span data-ttu-id="30c55-148">Cette commande doit être tapée comme une ligne unique de texte.</span><span class="sxs-lookup"><span data-stu-id="30c55-148">This command must be typed in as a single line of text.</span></span>

## <a name="see-also"></a><span data-ttu-id="30c55-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30c55-149">See also</span></span>

- <span data-ttu-id="30c55-150">[Hébergement AppFabric et exemples de persistance](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="30c55-150">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
