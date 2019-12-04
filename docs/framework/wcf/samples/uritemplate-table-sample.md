---
title: UriTemplate Table, exemple
ms.date: 03/30/2017
ms.assetid: 5dd1d38f-1989-4c64-820d-821f5a02216a
ms.openlocfilehash: fb5932acce60e2da45f99730580237d31130d918
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715407"
---
# <a name="uritemplate-table-sample"></a><span data-ttu-id="8a40a-102">UriTemplate Table, exemple</span><span class="sxs-lookup"><span data-stu-id="8a40a-102">UriTemplate Table Sample</span></span>
<span data-ttu-id="8a40a-103">La classe <xref:System.UriTemplateTable> fournit une structure de table associative de type dictionnaire permettant d'utiliser un ensemble d'instances d'`UriTemplate`.</span><span class="sxs-lookup"><span data-stu-id="8a40a-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of `UriTemplate` instances.</span></span> <span data-ttu-id="8a40a-104">Les URI (Uniform Resource Identifier) spécifiques peuvent être mis en correspondance avec tous les modèles de la table de manière efficace, et les données associées au modèle mis en correspondance peuvent être récupérées.</span><span class="sxs-lookup"><span data-stu-id="8a40a-104">Specific Uniform Resource Identifiers (URIs) can be matched efficiently against all templates in the table, and data associated with the matched template can be retrieved.</span></span>  
  
 <span data-ttu-id="8a40a-105">Cet exemple présente les concepts clés suivants relatifs à la classe `UriTemplateTable` :</span><span class="sxs-lookup"><span data-stu-id="8a40a-105">This sample demonstrates the following key concepts related to the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="8a40a-106">Syntaxe d'instanciation de `UriTemplateTable`.</span><span class="sxs-lookup"><span data-stu-id="8a40a-106">Syntax for instantiating a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="8a40a-107">Remplissage de `UriTemplateTable` avec un jeu de paires clé/valeur.</span><span class="sxs-lookup"><span data-stu-id="8a40a-107">Populating a `UriTemplateTable` with a set of key/value pairs.</span></span>  
  
- <span data-ttu-id="8a40a-108">Mise en correspondance d'un URI candidat avec la table à l'aide de <xref:System.UriTemplateTable.MatchSingle%2A>.</span><span class="sxs-lookup"><span data-stu-id="8a40a-108">Matching a candidate URI against the table using <xref:System.UriTemplateTable.MatchSingle%2A>.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8a40a-109">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="8a40a-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8a40a-110">Pour générer l’édition C# ou Visual Basic .NET de la solution, conformez-vous aux instructions figurant dans [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a40a-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="8a40a-111">Pour exécuter l’exemple dans une configuration à un ou plusieurs ordinateurs, suivez les instructions de [la section exécution des exemples de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="8a40a-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8a40a-112">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8a40a-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8a40a-113">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="8a40a-113">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="8a40a-114">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8a40a-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a40a-115">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="8a40a-115">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateTable`  
  
## <a name="see-also"></a><span data-ttu-id="8a40a-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a40a-116">See also</span></span>

- [<span data-ttu-id="8a40a-117">Répartiteur de table UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8a40a-117">UriTemplate Table Dispatcher</span></span>](../../../../docs/framework/wcf/samples/uritemplate-table-dispatcher-sample.md)
- [<span data-ttu-id="8a40a-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="8a40a-118">UriTemplate</span></span>](../../../../docs/framework/wcf/samples/uritemplate-sample.md)
