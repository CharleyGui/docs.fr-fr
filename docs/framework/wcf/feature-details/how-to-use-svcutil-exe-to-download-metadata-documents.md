---
title: 'Procédure : utiliser Svcutil.exe pour télécharger des documents de métadonnées'
description: Découvrez comment utiliser Svcutil.exe pour télécharger des métadonnées à partir de services en cours d’exécution et les enregistrer dans des fichiers locaux.
ms.date: 03/30/2017
ms.assetid: 15524274-3167-4627-b722-d6cedb9fa8c6
ms.openlocfilehash: 449dd3023b5d688ed0de22e3651cccf16bee0c52
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280674"
---
# <a name="how-to-use-svcutilexe-to-download-metadata-documents"></a><span data-ttu-id="c18dc-103">Procédure : utiliser Svcutil.exe pour télécharger des documents de métadonnées</span><span class="sxs-lookup"><span data-stu-id="c18dc-103">How to: Use Svcutil.exe to Download Metadata Documents</span></span>

<span data-ttu-id="c18dc-104">Svcutil.exe vous permet de télécharger des métadonnées à partir de systèmes en cours d'exécution et de les enregistrer dans des fichiers locaux.</span><span class="sxs-lookup"><span data-stu-id="c18dc-104">You can use Svcutil.exe to download metadata from running services and to save the metadata to local files.</span></span> <span data-ttu-id="c18dc-105">Pour les schémas d’URL HTTP et HTTPs, Svcutil.exe tente de récupérer des métadonnées à l’aide de WS-MetadataExchange et de la [découverte de service Web XML](/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="c18dc-105">For HTTP and HTTPS URL schemes, Svcutil.exe attempts to retrieve metadata using WS-MetadataExchange and [XML Web Service Discovery](/previous-versions/dotnet/netframework-4.0/fxx6cfx2(v=vs.100)).</span></span> <span data-ttu-id="c18dc-106">Pour tous les autres schémas d'URL, Svcutil.exe utilise uniquement WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="c18dc-106">For all other URL schemes, Svcutil.exe uses only WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="c18dc-107">Par défaut, Svcutil.exe utilise les liaisons définies dans la classe <xref:System.ServiceModel.Description.MetadataExchangeBindings>.</span><span class="sxs-lookup"><span data-stu-id="c18dc-107">By default, Svcutil.exe uses the bindings defined in the <xref:System.ServiceModel.Description.MetadataExchangeBindings> class.</span></span> <span data-ttu-id="c18dc-108">Pour configurer la liaison utilisée pour WS-MetadataExchange, vous devez définir un point de terminaison client dans le fichier de configuration de Svcutil.exe (svcutil.exe.config) qui utilise le contrat `IMetadataExchange` et qui porte le même nom que le schéma d’URI (Uniform Resource Identifier) de l’adresse du point de terminaison des métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c18dc-108">To configure the binding used for WS-MetadataExchange, you must define a client endpoint in the configuration file for Svcutil.exe (svcutil.exe.config) that uses the `IMetadataExchange` contract and that has the same name as the Uniform Resource Identifier (URI) scheme of the metadata endpoint address.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="c18dc-109">Lors de l’exécution de Svcutil.exe pour obtenir les métadonnées d’un service qui expose deux contrats de service différents qui contiennent chacun une opération du même nom, Svcutil.exe affiche une erreur indiquant « impossible d’obtenir les métadonnées à partir de... ». Par exemple, si vous avez un service qui expose un contrat de service appelé `ICarService` qui a une opération `Get(Car c)` et le même service expose un contrat de service appelé `IBookService` qui a une opération `Get(Book b)` .</span><span class="sxs-lookup"><span data-stu-id="c18dc-109">When running Svcutil.exe to get metadata for a service that exposes two different service contracts that each contain an operation of the same name, Svcutil.exe displays an error saying, "Cannot obtain Metadata from ...." For example, if you have a service that exposes a service contract called `ICarService` that has an operation `Get(Car c)` and the same service exposes a service contract called `IBookService` that has an operation `Get(Book b)`.</span></span> <span data-ttu-id="c18dc-110">Pour contourner ce problème, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="c18dc-110">To work around this issue, do one of the following:</span></span>
>
> - <span data-ttu-id="c18dc-111">Renommez l'une des opérations.</span><span class="sxs-lookup"><span data-stu-id="c18dc-111">Rename one of the operations.</span></span>
> - <span data-ttu-id="c18dc-112">Affectez au <xref:System.ServiceModel.OperationContractAttribute.Name%2A> un nom différent.</span><span class="sxs-lookup"><span data-stu-id="c18dc-112">Set the <xref:System.ServiceModel.OperationContractAttribute.Name%2A> to a different name.</span></span>
> - <span data-ttu-id="c18dc-113">Affectez à l'un des espaces de noms des opérations un espace de noms différent à l'aide de la propriété <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A>.</span><span class="sxs-lookup"><span data-stu-id="c18dc-113">Set one of the operations' namespaces to a different namespace using the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>
  
## <a name="to-download-metadata-using-svcutilexe"></a><span data-ttu-id="c18dc-114">Pour télécharger les métadonnées à l'aide de Svcutil.exe</span><span class="sxs-lookup"><span data-stu-id="c18dc-114">To download metadata using Svcutil.exe</span></span>  
  
1. <span data-ttu-id="c18dc-115">Localisez l'outil Svcutil.exe à l'emplacement suivant :</span><span class="sxs-lookup"><span data-stu-id="c18dc-115">Locate the Svcutil.exe tool at the following location:</span></span>  
  
     <span data-ttu-id="c18dc-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span><span class="sxs-lookup"><span data-stu-id="c18dc-116">C:\Program Files\Microsoft SDKs\Windows\v1.0.\bin</span></span>  
  
2. <span data-ttu-id="c18dc-117">À l'invite de commandes, lancez l'outil en utilisant le format suivant.</span><span class="sxs-lookup"><span data-stu-id="c18dc-117">At the command prompt, launch the tool using the following format.</span></span>  
  
    ```console
    svcutil.exe /t:metadata  <url>* | <epr>  
    ```  
  
     <span data-ttu-id="c18dc-118">Vous devez spécifier l'option `/t:metadata` pour télécharger les métadonnées.</span><span class="sxs-lookup"><span data-stu-id="c18dc-118">You must specify the `/t:metadata` option to download metadata.</span></span> <span data-ttu-id="c18dc-119">Sinon, la configuration et le code client seront générés.</span><span class="sxs-lookup"><span data-stu-id="c18dc-119">Otherwise, client code and configuration are generated.</span></span>  
  
3. <span data-ttu-id="c18dc-120">L' `url` argument <>spécifie l’URL d’un point de terminaison de service qui fournit des métadonnées ou à un document de métadonnées hébergé en ligne.</span><span class="sxs-lookup"><span data-stu-id="c18dc-120">The <`url`>argument specifies the URL to a service endpoint that provides metadata or to a metadata document hosted online.</span></span> <span data-ttu-id="c18dc-121">L' `epr` argument <> spécifie le chemin d’accès à un fichier XML qui contient un WS-Addressing `EndpointAddress` pour un point de terminaison de service qui prend en charge WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="c18dc-121">The <`epr`> argument specifies the path to an XML file that contains a WS-Addressing `EndpointAddress` for a service endpoint that supports WS-MetadataExchange.</span></span>  
  
 <span data-ttu-id="c18dc-122">Pour plus d’options sur l’utilisation de cet outil pour le téléchargement de métadonnées, consultez [outil ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="c18dc-122">For more options about using this tool for metadata download, see [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c18dc-123"> Exemple</span><span class="sxs-lookup"><span data-stu-id="c18dc-123">Example</span></span>  

 <span data-ttu-id="c18dc-124">La commande suivante télécharge des documents de métadonnées à partir d'un service en cours d'exécution.</span><span class="sxs-lookup"><span data-stu-id="c18dc-124">The following command downloads metadata documents from a running service.</span></span>  
  
```console
svcutil /t:metadata http://service/metadataEndpoint  
```  
  
## <a name="see-also"></a><span data-ttu-id="c18dc-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c18dc-125">See also</span></span>

- [<span data-ttu-id="c18dc-126">Outil Service Model Metadata Tool (Svcutil.exe)</span><span class="sxs-lookup"><span data-stu-id="c18dc-126">ServiceModel Metadata Utility Tool (Svcutil.exe)</span></span>](../servicemodel-metadata-utility-tool-svcutil-exe.md)
