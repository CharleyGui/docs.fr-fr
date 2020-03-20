---
title: Exemple Workflow Discovery
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143484"
---
# <a name="workflow-discovery-sample"></a><span data-ttu-id="58700-102">Exemple Workflow Discovery</span><span class="sxs-lookup"><span data-stu-id="58700-102">Workflow Discovery Sample</span></span>
<span data-ttu-id="58700-103">Cet exemple montre comment rendre un service de workflow détectable et comment créer une activité de code personnalisée qui recherche un service particulier.</span><span class="sxs-lookup"><span data-stu-id="58700-103">This sample demonstrates how to make a workflow service discoverable and how to author a custom code activity that searches for a particular service.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="58700-104">Illustre le</span><span class="sxs-lookup"><span data-stu-id="58700-104">Demonstrates</span></span>  
 <span data-ttu-id="58700-105">Activité de recherche de découverte et utilisation de workflow</span><span class="sxs-lookup"><span data-stu-id="58700-105">Discovery Find Activity and Workflow Usage</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="58700-106">Discussions</span><span class="sxs-lookup"><span data-stu-id="58700-106">Discussion</span></span>  
 <span data-ttu-id="58700-107">Dans la première partie de l'exemple, un service de workflow est rendu détectable à l'aide de la configuration.</span><span class="sxs-lookup"><span data-stu-id="58700-107">In the first part of the sample, a workflow service is made discoverable using configuration.</span></span> <span data-ttu-id="58700-108">La configuration peut également être utilisée pour appliquer convenablement le service avec des métadonnées personnalisées (telles que des portées).</span><span class="sxs-lookup"><span data-stu-id="58700-108">Configuration can also be used to apply the service appropriately with custom metadata (such as scopes).</span></span> <span data-ttu-id="58700-109">Sur le client, l'exemple utilise une activité de code personnalisée, qui utilise la découverte pour rechercher un service correspondant à un contrat particulier.</span><span class="sxs-lookup"><span data-stu-id="58700-109">On the client, the sample uses a custom code activity, which uses Discovery to search for a service matching a particular contract.</span></span> <span data-ttu-id="58700-110">L'activité de code produit un URI, utilisé ultérieurement par une activité d'envoi.</span><span class="sxs-lookup"><span data-stu-id="58700-110">The code activity outputs a URI, which is later used by a send activity.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="58700-111">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="58700-111">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="58700-112">Cet exemple utilise des paramètres HTTP, qui doivent avoir des URL appropriées pour s’exécuter (voir [Configuring HTTP et HTTPS](../feature-details/configuring-http-and-https.md) pour plus de détails).</span><span class="sxs-lookup"><span data-stu-id="58700-112">This sample uses HTTP endpoints, which must have proper URL ACLs to run (see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md) for details).</span></span> <span data-ttu-id="58700-113">L'exécution de la commande suivante à partir d'une invite de commandes avec élévation de privilèges doit ajouter les ACL appropriées.</span><span class="sxs-lookup"><span data-stu-id="58700-113">Executing the following command at an elevated command prompt should add the appropriate ACLs.</span></span> <span data-ttu-id="58700-114">Si votre shell ne comprend pas le format variable, remplacez votre Domaine et votre nom d’utilisateur pour les arguments suivants.</span><span class="sxs-lookup"><span data-stu-id="58700-114">If your shell does not understand the variable format, substitute your Domain and Username for the following arguments.</span></span>  
  
     <span data-ttu-id="58700-115">**netsh http ajouter urlacl url 'user '%DOMAIN%http://+:8000/ \\%UserName%**</span><span class="sxs-lookup"><span data-stu-id="58700-115">**netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\\%UserName%**</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="58700-116">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="58700-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="58700-117">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="58700-117">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="58700-118">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="58700-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="58700-119">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="58700-119">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
