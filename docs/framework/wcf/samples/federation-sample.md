---
title: Federation, exemple
ms.date: 03/30/2017
ms.assetid: 7e9da0ca-e925-4644-aa96-8bfaf649d4bb
ms.openlocfilehash: 22d405620a77285ebe7a68fc151a8e8611df9b4d
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283274"
---
# <a name="federation-sample"></a><span data-ttu-id="8b4b1-102">Federation, exemple</span><span class="sxs-lookup"><span data-stu-id="8b4b1-102">Federation Sample</span></span>

<span data-ttu-id="8b4b1-103">Cet exemple présente la sécurité fédérée :</span><span class="sxs-lookup"><span data-stu-id="8b4b1-103">This sample demonstrates federated security.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="8b4b1-104">Détails de l'exemple</span><span class="sxs-lookup"><span data-stu-id="8b4b1-104">Sample Details</span></span>  

 <span data-ttu-id="8b4b1-105">Windows Communication Foundation (WCF) prend en charge le déploiement d’architectures de sécurité fédérée via le `wsFederationHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="8b4b1-105">Windows Communication Foundation (WCF) provides support for deploying federated security architectures through the `wsFederationHttpBinding`.</span></span> <span data-ttu-id="8b4b1-106">`wsFederationHttpBinding` fournit une liaison sécurisée, fiable et interopérable qui implique l'utilisation de HTTP comme mécanisme de transport sous-jacent pour la communication demande/réponse, le format de câble d'encodage étant Text/XML.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-106">The `wsFederationHttpBinding` provides a secure, reliable, and interoperable binding that involves the use of HTTP as the underlying transport mechanism for request/reply communication, and Text/XML as the wire format for encoding.</span></span> <span data-ttu-id="8b4b1-107">Pour plus d’informations sur la Fédération dans WCF, consultez [Federation](../feature-details/federation.md).</span><span class="sxs-lookup"><span data-stu-id="8b4b1-107">For more information about Federation in WCF, see [Federation](../feature-details/federation.md).</span></span>  
  
 <span data-ttu-id="8b4b1-108">Le scénario comporte 4 parties :</span><span class="sxs-lookup"><span data-stu-id="8b4b1-108">The scenario is made up of 4 pieces:</span></span>  
  
- <span data-ttu-id="8b4b1-109">Service BookStore</span><span class="sxs-lookup"><span data-stu-id="8b4b1-109">BookStore service</span></span>  
  
- <span data-ttu-id="8b4b1-110">STS BookStore</span><span class="sxs-lookup"><span data-stu-id="8b4b1-110">BookStore STS</span></span>  
  
- <span data-ttu-id="8b4b1-111">STS HomeRealm</span><span class="sxs-lookup"><span data-stu-id="8b4b1-111">HomeRealm STS</span></span>  
  
- <span data-ttu-id="8b4b1-112">Client BookStore</span><span class="sxs-lookup"><span data-stu-id="8b4b1-112">BookStore Client</span></span>  
  
 <span data-ttu-id="8b4b1-113">Le service BookStore prend en charge deux opérations : `BrowseBooks` et `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-113">The BookStore service supports two operations, `BrowseBooks` and `BuyBook`.</span></span> <span data-ttu-id="8b4b1-114">Il autorise l'accès anonyme à l'opération `BrowseBooks`, mais requiert l'authentification pour accéder à l'opération `BuyBooks`.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-114">It allows anonymous access to the `BrowseBooks` operation, but requires authenticated access to access the `BuyBooks` operation.</span></span> <span data-ttu-id="8b4b1-115">L'authentification prend la forme d'un jeton émis par le STS BookStore.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-115">The authentication takes the form of a token issued by the BookStore STS.</span></span> <span data-ttu-id="8b4b1-116">Le fichier de configuration du service BookStore pointe des clients sur le STS BookStore à l'aide de `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-116">The configuration file for the BookStore Service points clients to the BookStore STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
<!-- This is the Service binding for the BuyBooks endpoint. It redirects clients to the BookStore STS -->  
    <binding name='BuyBookBinding'>  
        <security mode="Message">  
            <message>  
                <issuerMetadata  
  address='http://localhost/FederationSample/BookStoreSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='BookStoreSTS.com'/>  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="8b4b1-117">Le STS BookStore impose ensuite aux clients de s'authentifier à l'aide d'un jeton émis par le STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-117">The BookStore STS then requires that clients authenticate using a token issued by the HomeRealm STS.</span></span> <span data-ttu-id="8b4b1-118">Une fois encore, le fichier de configuration du STS BookStore pointe des clients sur le STS HomeRealm à l'aide de `wsFederationHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-118">Again, the configuration file for the BookStore STS points clients to the HomeRealm STS using the `wsFederationHttpBinding`.</span></span>  
  
```xml  
<wsFederationHttpBinding>  
 <!-- This is the binding for the clients requesting tokens from this STS. It redirects clients to the HomeRealm STS -->  
    <binding name='BookStoreSTSBinding'>  
        <security mode='Message'>  
            <message>  
                <issuerMetadata  
 address='http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex' >  
                    <identity>  
                        <dns value ='HomeRealmSTS.com' />  
                    </identity>  
                </issuerMetadata>  
            </message>  
        </security>  
    </binding>  
</wsFederationHttpBinding>  
```  
  
 <span data-ttu-id="8b4b1-119">La séquence des événements lors de l'accès à l'opération `BuyBook` est la suivante :</span><span class="sxs-lookup"><span data-stu-id="8b4b1-119">The sequence of events when accessing the `BuyBook` operation is as follows:</span></span>  
  
1. <span data-ttu-id="8b4b1-120">Le client s'authentifie auprès du STS HomeRealm à l'aide d'informations d'identification Windows.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-120">The client authenticates to the HomeRealm STS using Windows credentials.</span></span>  
  
2. <span data-ttu-id="8b4b1-121">Le STS HomeRealm émet un jeton qui peut être utilisé pour s'authentifier auprès du STS BookStore.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-121">The HomeRealm STS issues a token that can be used to authenticate to the BookStore STS.</span></span>  
  
3. <span data-ttu-id="8b4b1-122">Le client s'authentifie auprès du STS BookStore à l'aide du jeton émis par le STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-122">The client authenticates to the BookStore STS using the token issued by the HomeRealm STS.</span></span>  
  
4. <span data-ttu-id="8b4b1-123">Le STS BookStore émet un jeton qui peut être utilisé pour s'authentifier auprès du service BookStore.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-123">The BookStore STS issues a token that can be used to authenticate to the BookStore Service.</span></span>  
  
5. <span data-ttu-id="8b4b1-124">Le client s'authentifie auprès du service BookStore à l'aide du jeton émis par le STS BookStore.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-124">The client authenticates to the BookStore service using the token issued by the BookStore STS.</span></span>  
  
6. <span data-ttu-id="8b4b1-125">Le client accède à l'opération `BuyBook`.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-125">The client accesses the `BuyBook` operation.</span></span>  
  
 <span data-ttu-id="8b4b1-126">Suivez les instructions suivantes sur la configuration et l'exécution de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-126">See the following instructions about how to set up and run this sample.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8b4b1-127">Pour exécuter cet exemple, vous devez disposer d’autorisations en écriture sur le répertoire **wwwroot** .</span><span class="sxs-lookup"><span data-stu-id="8b4b1-127">You must have Write permissions to the **wwwroot** directory to run this sample.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8b4b1-128">Pour configurer, générer et exécuter l'exemple</span><span class="sxs-lookup"><span data-stu-id="8b4b1-128">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="8b4b1-129">Ouvrez la fenêtre de commande de Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-129">Open the SDK command window.</span></span> <span data-ttu-id="8b4b1-130">Dans le chemin d’accès de l’exemple, exécutez Setup.bat.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-130">In the sample path, run Setup.bat.</span></span> <span data-ttu-id="8b4b1-131">Cette opération crée les répertoires virtuels requis pour l'exemple et installe les certificats requis avec les autorisations appropriées.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-131">This creates the virtual directories required for the sample and installs the required certificates with appropriate permissions.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8b4b1-132">Le fichier de commandes Setup.bat est conçu pour s'exécuter à partir d'une invite de commandes du Kit de développement Windows SDK.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-132">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="8b4b1-133">La variable d'environnement du Kit de développement MS SDK doit pointer vers le répertoire d'installation du Kit de développement SDK.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-133">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="8b4b1-134">Cette variable est définie automatiquement dans une invite de commandes du Kit de développement logiciel Windows.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-134">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span> <span data-ttu-id="8b4b1-135">Sur Windows Vista, vous devez vous assurer que la compatibilité avec la gestion IIS 6,0 est installée, car la configuration utilise des scripts d’administrateur IIS.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-135">On Windows Vista, you must ensure that IIS 6.0 Management Compatibility is installed because the set up uses IIS administrator scripts.</span></span> <span data-ttu-id="8b4b1-136">L’exécution du script d’installation sur Windows Vista nécessite des privilèges d’administrateur.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-136">Running the set-up script on Windows Vista requires administrator privileges.</span></span>  
  
2. <span data-ttu-id="8b4b1-137">Ouvrez FederationSample. sln dans Visual Studio et sélectionnez **générer la solution** dans le menu **générer** .</span><span class="sxs-lookup"><span data-stu-id="8b4b1-137">Open FederationSample.sln in Visual Studio and select **Build Solution** from the **Build** menu.</span></span> <span data-ttu-id="8b4b1-138">Cette opération génère les fichiers de projet communs, le service Bookstore, le STS Bookstore, le STS HomeRealm, et les déploie dans IIS.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-138">This builds the common project files, Bookstore service, Bookstore STS, HomeRealm STS, and deploys them in IIS.</span></span> <span data-ttu-id="8b4b1-139">Elle génère également l’application cliente Bookstore et place le fichier exécutable BookStoreClient.exe dans le dossier FederationSample\BookStoreClient\bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-139">This also builds the Bookstore client application and places the executable BookStoreClient.exe in the FederationSample\BookStoreClient\bin\Debug folder.</span></span>  
  
3. <span data-ttu-id="8b4b1-140">Double-cliquez sur BookStoreClient.exe.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-140">Double-click BookStoreClient.exe.</span></span> <span data-ttu-id="8b4b1-141">La fenêtre BookStoreClient s'affiche.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-141">The BookStoreClient window is displayed.</span></span>  
  
4. <span data-ttu-id="8b4b1-142">Vous pouvez parcourir les livres disponibles dans la librairie en cliquant sur **Parcourir les livres**.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-142">You can browse the books available in the bookstore by clicking **Browse Books**.</span></span>  
  
5. <span data-ttu-id="8b4b1-143">Pour acheter un livre particulier, sélectionnez le livre dans la liste et cliquez sur **acheter un livre**.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-143">To purchase a particular book, select the book in the list and click **Buy Book**.</span></span> <span data-ttu-id="8b4b1-144">L'application démarre et s'authentifie à l'aide de l'authentification Windows avec le STS HomeRealm.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-144">The application starts up and authenticates using Windows authentication with the HomeRealm Security Token Service.</span></span>  
  
     <span data-ttu-id="8b4b1-145">L'exemple est configuré pour permettre aux utilisateurs d'acheter des livres pour un montant égal ou inférieur à 15 dollars.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-145">The sample is configured to allow users to purchase books that cost $15 or less.</span></span> <span data-ttu-id="8b4b1-146">Si un client tente d'acheter des livres pour un montant supérieur à 15 dollars, il reçoit un message du service BookStore indiquant que l'accès est refusé.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-146">Attempting to buy books that cost more than $15 results in the client getting an Access Denied message from the Book Store Service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="8b4b1-147">L'exemple ne met pas à jour la limite de crédit de l'utilisateur après un achat.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-147">The sample does not update the user’s credit limit after a purchase.</span></span> <span data-ttu-id="8b4b1-148">Vous pouvez acheter des livres à plusieurs reprises dans la limite de crédit (fixée) de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-148">You can repeatedly purchase books within the user’s (fixed) credit limit.</span></span>  
  
#### <a name="to-clean-up"></a><span data-ttu-id="8b4b1-149">Pour nettoyer</span><span class="sxs-lookup"><span data-stu-id="8b4b1-149">To clean up</span></span>  
  
1. <span data-ttu-id="8b4b1-150">Exécutez Cleanup.bat.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-150">Run Cleanup.bat.</span></span> <span data-ttu-id="8b4b1-151">Cette opération supprime les répertoires virtuels créés pendant l'installation ainsi que les certificats installés pendant l'installation.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-151">This deletes the virtual directories that were created during set up and also removes the certificates installed during setup.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8b4b1-152">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-152">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8b4b1-153">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-153">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="8b4b1-154">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et Windows Workflow Foundation (WF) exemples pour .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) pour télécharger tous les exemples Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="8b4b1-154">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8b4b1-155">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="8b4b1-155">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\Federation`  
