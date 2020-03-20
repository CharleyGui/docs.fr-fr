---
title: UriTemplate Table Dispatcher, exemple
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: aa4259f8c823bebf38b9689df92c45992cb55723
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143679"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="f82aa-102">UriTemplate Table Dispatcher, exemple</span><span class="sxs-lookup"><span data-stu-id="f82aa-102">UriTemplate Table Dispatcher Sample</span></span>
<span data-ttu-id="f82aa-103">La classe <xref:System.UriTemplateTable> fournit une structure de table associative de type dictionnaire permettant d'utiliser un ensemble d'instances d'<xref:System.UriTemplate>.</span><span class="sxs-lookup"><span data-stu-id="f82aa-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="f82aa-104">Cet exemple illustre un moteur de distribution de base construit à l'aide d'`UriTemplateTable`, un scénario d'utilisation commun pour la classe `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="f82aa-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="f82aa-105">Cet exemple illustre les concepts clés suivants pour la classe `UriTemplateTable` :</span><span class="sxs-lookup"><span data-stu-id="f82aa-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="f82aa-106">Association de délégués à des `UriTemplates` dans une `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="f82aa-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="f82aa-107">Utilisation de <xref:System.UriTemplateTable.MatchSingle%2A> pour obtenir le délégué de gestionnaire correct pour un URI particulier.</span><span class="sxs-lookup"><span data-stu-id="f82aa-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="f82aa-108">Appel du délégué de gestionnaire pour traiter la requête.</span><span class="sxs-lookup"><span data-stu-id="f82aa-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f82aa-109">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="f82aa-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f82aa-110">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f82aa-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="f82aa-111">Pour exécuter l’échantillon dans une configuration mono-ou cross-machine, suivez les instructions dans [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f82aa-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f82aa-112">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f82aa-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f82aa-113">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f82aa-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f82aa-114">Si ce répertoire n’existe pas, rendez-vous sur [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) Samples pour .NET Framework 4 pour](https://www.microsoft.com/download/details.aspx?id=21459) télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] des échantillons.</span><span class="sxs-lookup"><span data-stu-id="f82aa-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f82aa-115">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f82aa-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="f82aa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f82aa-116">See also</span></span>

- [<span data-ttu-id="f82aa-117">Table UriTemplate</span><span class="sxs-lookup"><span data-stu-id="f82aa-117">UriTemplate Table</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-sample.md)
- [<span data-ttu-id="f82aa-118">Uritemplate</span><span class="sxs-lookup"><span data-stu-id="f82aa-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
