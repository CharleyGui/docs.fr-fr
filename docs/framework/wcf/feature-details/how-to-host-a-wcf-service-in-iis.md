---
title: 'Procédure : héberger un service WCF dans IIS'
description: Découvrez comment créer un service WCF hébergé dans Internet Information Services (IIS). Vous pouvez utiliser l'hébergement IIS uniquement avec un transport HTTP.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b044b1c9-c1e5-4c9f-84d8-0f02f4537f8b
ms.openlocfilehash: e0eb61e56b20eda6627030700b823042e07d10c9
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244442"
---
# <a name="how-to-host-a-wcf-service-in-iis"></a><span data-ttu-id="ea4d7-104">Procédure : héberger un service WCF dans IIS</span><span class="sxs-lookup"><span data-stu-id="ea4d7-104">How to: Host a WCF Service in IIS</span></span>

<span data-ttu-id="ea4d7-105">Cette rubrique décrit les étapes de base requises pour créer un service Windows Communication Foundation (WCF) hébergé dans Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="ea4d7-105">This topic outlines the basic steps required to create a Windows Communication Foundation (WCF) service that is hosted in Internet Information Services (IIS).</span></span> <span data-ttu-id="ea4d7-106">Dans cette rubrique, on suppose que vous connaissez IIS et que vous comprenez la manière d'utiliser l'outil d'administration IIS pour créer et gérer des applications IIS.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-106">This topic assumes you are familiar with IIS and understand how to use the IIS management tool to create and manage IIS applications.</span></span> <span data-ttu-id="ea4d7-107">Pour plus d’informations sur IIS, consultez [Internet Information Services](https://www.iis.net/).</span><span class="sxs-lookup"><span data-stu-id="ea4d7-107">For more information about IIS see [Internet Information Services](https://www.iis.net/).</span></span> <span data-ttu-id="ea4d7-108">Un service WCF qui s’exécute dans l’environnement IIS tire pleinement parti des fonctionnalités d’IIS, telles que le recyclage de processus, l’arrêt inactif, le contrôle d’intégrité des processus et l’activation basée sur des messages.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-108">A WCF service that runs in the IIS environment takes full advantage of IIS features, such as process recycling, idle shutdown, process health monitoring, and message-based activation.</span></span> <span data-ttu-id="ea4d7-109">Cette option d'hébergement requiert que les services IIS soient configurés correctement, mais n'exige pas l'écriture d'un code d'hébergement dans le cadre de l'application.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-109">This hosting option requires that IIS be properly configured, but it does not require that any hosting code be written as part of the application.</span></span> <span data-ttu-id="ea4d7-110">Vous pouvez utiliser l'hébergement IIS uniquement avec un transport HTTP.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-110">You can use IIS hosting only with an HTTP transport.</span></span>  
  
 <span data-ttu-id="ea4d7-111">Pour plus d’informations sur la façon dont WCF et ASP.NET interagissent, consultez [services WCF et ASP.net](wcf-services-and-aspnet.md).</span><span class="sxs-lookup"><span data-stu-id="ea4d7-111">For more information about how WCF and ASP.NET interact, see [WCF Services and ASP.NET](wcf-services-and-aspnet.md).</span></span> <span data-ttu-id="ea4d7-112">Pour plus d’informations sur la configuration de la sécurité, consultez [sécurité](security.md).</span><span class="sxs-lookup"><span data-stu-id="ea4d7-112">For more information about configuring security, see [Security](security.md).</span></span>  
  
 <span data-ttu-id="ea4d7-113">Pour obtenir la copie source de cet exemple, consultez [l’hébergement IIS à l’aide du code inline](../samples/iis-hosting-using-inline-code.md).</span><span class="sxs-lookup"><span data-stu-id="ea4d7-113">For the source copy of this example, see [IIS Hosting Using Inline Code](../samples/iis-hosting-using-inline-code.md).</span></span>  
  
### <a name="to-create-a-service-hosted-by-iis"></a><span data-ttu-id="ea4d7-114">Pour créer un service hébergé par IIS</span><span class="sxs-lookup"><span data-stu-id="ea4d7-114">To create a service hosted by IIS</span></span>  
  
1. <span data-ttu-id="ea4d7-115">Vérifiez que les services IIS sont installés et s'exécutent sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-115">Confirm that IIS is installed and running on your computer.</span></span> <span data-ttu-id="ea4d7-116">Pour plus d’informations sur l’installation et la configuration d’IIS, consultez [installation et configuration d’iis 7,0](/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span><span class="sxs-lookup"><span data-stu-id="ea4d7-116">For more information about installing and configuring IIS see [Installing and Configuring IIS 7.0](/iis/install/installing-iis-7/installing-necessary-iis-components-on-windows-vista)</span></span>  
  
2. <span data-ttu-id="ea4d7-117">Créez un nouveau dossier pour vos fichiers d’application appelé « IISHostedCalcService », vérifiez que ASP.NET a accès au contenu du dossier et utilisez l’outil de gestion IIS pour créer une application IIS qui se trouve physiquement dans ce répertoire d’application.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-117">Create a new folder for your application files called "IISHostedCalcService", ensure that ASP.NET has access to the contents of the folder, and use the IIS management tool to create a new IIS application that is physically located in this application directory.</span></span> <span data-ttu-id="ea4d7-118">Lors de la création d'un alias pour le répertoire de l'application, utilisez « IISHostedCalc ».</span><span class="sxs-lookup"><span data-stu-id="ea4d7-118">When creating an alias for the application directory use "IISHostedCalc".</span></span>  
  
3. <span data-ttu-id="ea4d7-119">Créez un fichier appelé « service.svc » dans le répertoire de l'application.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-119">Create a new file named "service.svc" in the application directory.</span></span> <span data-ttu-id="ea4d7-120">Modifiez ce fichier en ajoutant l' @ServiceHost élément suivant.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-120">Edit this file by adding the following @ServiceHost element.</span></span>  
  
   ```aspx-csharp
   <%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService"%>
   ```  
  
4. <span data-ttu-id="ea4d7-121">Créez un sous-répertoire App_Code dans le répertoire de l'application.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-121">Create an App_Code subdirectory within the application directory.</span></span>  
  
5. <span data-ttu-id="ea4d7-122">Créez un fichier de code nommé Service.cs dans le sous-répertoire App_Code.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-122">Create a code file named Service.cs in the App_Code subdirectory.</span></span>  
  
6. <span data-ttu-id="ea4d7-123">Ajoutez les instructions using suivantes en tête du fichier Service.cs.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-123">Add the following using statements to the top of the Service.cs file.</span></span>  
  
    ```csharp  
    using System;  
    using System.ServiceModel;  
    ```  
  
7. <span data-ttu-id="ea4d7-124">Ajoutez la déclaration d'espace de noms suivante à la suite des instructions using.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-124">Add the following namespace declaration after the using statements.</span></span>  
  
    ```csharp  
    namespace Microsoft.ServiceModel.Samples  
    {  
    }  
    ```  
  
8. <span data-ttu-id="ea4d7-125">Définissez le contrat de service à l'intérieur de la déclaration d'espace de noms, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-125">Define the service contract inside the namespace declaration as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#11)]
     [!code-vb[c_HowTo_HostInIIS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#11)]  
  
9. <span data-ttu-id="ea4d7-126">Implémentez le contrat de service après la définition du contrat de service, tel qu'indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-126">Implement the service contract after the service contract definition as shown in the following code.</span></span>  
  
     [!code-csharp[c_HowTo_HostInIIS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#12)]
     [!code-vb[c_HowTo_HostInIIS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#12)]  
  
10. <span data-ttu-id="ea4d7-127">Créez un fichier nommé « Web.config » dans le répertoire de l'application et ajoutez le code de configuration suivant dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-127">Create a file named "Web.config" in the application directory and add the following configuration code into the file.</span></span> <span data-ttu-id="ea4d7-128">Lors de l’exécution, l’infrastructure WCF utilise les informations pour construire un point de terminaison avec lequel les applications clientes peuvent communiquer.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-128">At runtime, the WCF infrastructure uses the information to construct an endpoint that client applications can communicate with.</span></span>  
  
     [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]
  
     <span data-ttu-id="ea4d7-129">L'exemple spécifie explicitement les points de terminaison dans le fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-129">This example explicitly specifies endpoints in the configuration file.</span></span> <span data-ttu-id="ea4d7-130">Si vous n'ajoutez pas de points de terminaison au service, le runtime ajoute les points de terminaison par défaut.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-130">If you do not add any endpoints to the service, the runtime adds default endpoints for you.</span></span> <span data-ttu-id="ea4d7-131">Pour plus d’informations sur les points de terminaison, les liaisons et les comportements par défaut, consultez [configuration simplifiée](../simplified-configuration.md) et [configuration simplifiée pour les services WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="ea4d7-131">For more information about default endpoints, bindings, and behaviors see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
11. <span data-ttu-id="ea4d7-132">Pour vous assurer que le service est hébergé correctement, ouvrez une instance d'Internet Explorer et naviguez jusqu'à l'URL du service : `http://localhost/IISHostedCalc/Service.svc`</span><span class="sxs-lookup"><span data-stu-id="ea4d7-132">To make sure the service is hosted correctly, open an instance of Internet Explorer and browse to the service's URL: `http://localhost/IISHostedCalc/Service.svc`</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea4d7-133"> Exemple</span><span class="sxs-lookup"><span data-stu-id="ea4d7-133">Example</span></span>  

 <span data-ttu-id="ea4d7-134">L'intégralité du code pour le service de calculatrice hébergé IIS est présentée ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="ea4d7-134">The following is a complete listing of the code for the IIS hosted calculator service.</span></span>  
  
 [!code-csharp[C_HowTo_HostInIIS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/cs/source.cs#1)]
 [!code-vb[C_HowTo_HostInIIS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_hostiniis/vb/source.vb#1)]
 [!code-xml[c_HowTo_HostInIIS#100](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_hostiniis/common/web.config#100)]  
  
## <a name="see-also"></a><span data-ttu-id="ea4d7-135">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea4d7-135">See also</span></span>

- [<span data-ttu-id="ea4d7-136">Hébergement dans les services IIS (Internet Information Services)</span><span class="sxs-lookup"><span data-stu-id="ea4d7-136">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="ea4d7-137">Hébergement de services</span><span class="sxs-lookup"><span data-stu-id="ea4d7-137">Hosting Services</span></span>](../hosting-services.md)
- [<span data-ttu-id="ea4d7-138">Services WCF et ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ea4d7-138">WCF Services and ASP.NET</span></span>](wcf-services-and-aspnet.md)
- [<span data-ttu-id="ea4d7-139">Sécurité</span><span class="sxs-lookup"><span data-stu-id="ea4d7-139">Security</span></span>](security.md)
- <span data-ttu-id="ea4d7-140">[Fonctionnalités d’hébergement de Windows Server AppFabric](/previous-versions/appfabric/ee677189(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="ea4d7-140">[Windows Server App Fabric Hosting Features](/previous-versions/appfabric/ee677189(v=azure.10))</span></span>
