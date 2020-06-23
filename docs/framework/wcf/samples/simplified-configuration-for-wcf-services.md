---
title: Configuration simplifiée pour WCF Services
description: Découvrez comment implémenter et configurer un service et un client standard à l’aide de WCF. Le service communique à l’aide d’un point de terminaison spécifié dans un fichier de configuration.
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 46a0c878b29de34219413a508799ddaddf507dd8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246218"
---
# <a name="simplified-configuration-for-wcf-services"></a><span data-ttu-id="77e84-104">Configuration simplifiée pour WCF Services</span><span class="sxs-lookup"><span data-stu-id="77e84-104">Simplified Configuration for WCF Services</span></span>
<span data-ttu-id="77e84-105">Cet exemple montre comment implémenter et configurer un service et un client standard à l’aide de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="77e84-105">This sample demonstrates how to implement and configure a typical service and client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="77e84-106">Cet exemple constitue la base de tous les autres exemples de technologie de base.</span><span class="sxs-lookup"><span data-stu-id="77e84-106">This sample is the basis for all other basic technology samples.</span></span>  
  
 <span data-ttu-id="77e84-107">Ce service, qui expose un point de terminaison pour communiquer avec le service, utilise la configuration simplifiée dans .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="77e84-107">This service, which exposes an endpoint for communicating with the service, uses the simplified configuration in .NET Framework 4.</span></span> <span data-ttu-id="77e84-108">Avant .NET Framework 4, le point de terminaison est généralement défini dans un fichier de configuration (Web.config), comme indiqué dans l’exemple de code de configuration suivant.</span><span class="sxs-lookup"><span data-stu-id="77e84-108">Prior to .NET Framework 4, the endpoint is typically defined in a configuration file (Web.config), as shown in the following example configuration code.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="77e84-109">Dans .NET Framework 4, l' `<service>` élément est facultatif.</span><span class="sxs-lookup"><span data-stu-id="77e84-109">In .NET Framework 4, the `<service>` element is optional.</span></span> <span data-ttu-id="77e84-110">Lorsqu'un service ne définit pas de points de terminaison, un point de terminaison est ajouté au service pour chaque adresse de base et contrat implémentés.</span><span class="sxs-lookup"><span data-stu-id="77e84-110">When a service does not define any endpoints, an endpoint for each base address and contract implemented are added to the service.</span></span> <span data-ttu-id="77e84-111">L’adresse de base est ajoutée au nom du contrat pour déterminer le point de terminaison et la liaison est déterminée par le schéma d’adresse.</span><span class="sxs-lookup"><span data-stu-id="77e84-111">The base address is appended to the contract name to determine the endpoint and the binding is determined by the address scheme.</span></span> <span data-ttu-id="77e84-112">L'exemple de code suivant montre un fichier de configuration simplifié.</span><span class="sxs-lookup"><span data-stu-id="77e84-112">The following code example demonstrates a simplified configuration file.</span></span> <span data-ttu-id="77e84-113">Comme configuré, le service est accessible à `http://localhost/servicemodelsamples/service.svc` un client sur le même ordinateur.</span><span class="sxs-lookup"><span data-stu-id="77e84-113">As configured, the service can be accessed at `http://localhost/servicemodelsamples/service.svc` by a client on the same computer.</span></span> <span data-ttu-id="77e84-114">Pour que les clients installés sur des ordinateurs distants puissent accéder au service, un nom de domaine complet doit être spécifié au lieu de localhost.</span><span class="sxs-lookup"><span data-stu-id="77e84-114">For clients on remote computers to access the service, a fully-qualified domain name must be specified instead of localhost.</span></span> <span data-ttu-id="77e84-115">Par défaut, le service n'expose pas de métadonnées.</span><span class="sxs-lookup"><span data-stu-id="77e84-115">The service does not expose metadata by default.</span></span> <span data-ttu-id="77e84-116">Comme tel, le service active le comportement <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.</span><span class="sxs-lookup"><span data-stu-id="77e84-116">As such, the service turns on the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> behavior.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="77e84-117">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="77e84-117">To use this sample</span></span>  
  
1. <span data-ttu-id="77e84-118">Assurez-vous d’avoir effectué la [procédure d’installation unique pour les exemples de Windows Communication Foundation](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="77e84-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="77e84-119">Pour générer la solution, suivez les instructions de [la création des exemples de Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="77e84-119">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="77e84-120">Exécutez l'exemple en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="77e84-120">Run the sample by following these steps:</span></span>  
  
    1. <span data-ttu-id="77e84-121">Cliquez avec le bouton droit sur le projet de **service** et sélectionnez **définir comme projet de démarrage**, puis appuyez sur **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="77e84-121">Right click the **Service** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
    2. <span data-ttu-id="77e84-122">Attendez le message de la console confirmant le bon fonctionnement du service.</span><span class="sxs-lookup"><span data-stu-id="77e84-122">Wait for the console output confirming that the service is up and running.</span></span>  
  
    3. <span data-ttu-id="77e84-123">Cliquez avec le bouton droit sur le projet **client** et sélectionnez **définir comme projet de démarrage**, puis appuyez sur **CTRL + F5**.</span><span class="sxs-lookup"><span data-stu-id="77e84-123">Right click the **Client** project and select **Set as StartUp project**, then press **Ctrl+F5**.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="77e84-124">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="77e84-124">The samples may already be installed on your computer.</span></span> <span data-ttu-id="77e84-125">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="77e84-125">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="77e84-126">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="77e84-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="77e84-127">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="77e84-127">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a><span data-ttu-id="77e84-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77e84-128">See also</span></span>

- <span data-ttu-id="77e84-129">[Exemples de gestion AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="77e84-129">[AppFabric Management Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))</span></span>
- [<span data-ttu-id="77e84-130">Configuration simplifiée</span><span class="sxs-lookup"><span data-stu-id="77e84-130">Simplified Configuration</span></span>](../simplified-configuration.md)
