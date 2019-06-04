---
title: Agilité de chiffrement dans sécurité WCF
ms.date: 03/30/2017
ms.assetid: c2c549e5-ac19-40c5-b686-8f67f52b6dbf
ms.openlocfilehash: b8e3b6dc62baf31901520d7f5edac0529e937016
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490940"
---
# <a name="cryptographic-agility-in-wcf-security"></a><span data-ttu-id="f2b18-102">Agilité de chiffrement dans sécurité WCF</span><span class="sxs-lookup"><span data-stu-id="f2b18-102">Cryptographic agility in WCF security</span></span>

<span data-ttu-id="f2b18-103">Cet exemple montre comment spécifier dans un algorithme standard ou personnalisé pour fournir une implémentation de chiffrement agile dans un client Windows Communication Foundation (WCF) et le service.</span><span class="sxs-lookup"><span data-stu-id="f2b18-103">This sample shows how to specify in a standard/custom algorithm to provide a cryptographic agile implementation in a Windows Communication Foundation (WCF) client and service.</span></span> <span data-ttu-id="f2b18-104">Cet exemple est composé des projets suivants :</span><span class="sxs-lookup"><span data-stu-id="f2b18-104">The sample is composed of the following projects:</span></span>

<span data-ttu-id="f2b18-105">**Service**</span><span class="sxs-lookup"><span data-stu-id="f2b18-105">**Service**</span></span>

<span data-ttu-id="f2b18-106">Il s’agit d’un service WCF auto-hébergé qui implémente le `ICalculator` interface et sécurise le point de terminaison en utilisant la <xref:System.ServiceModel.WSHttpBinding> avec la session sécurisée et la session fiable désactivée.</span><span class="sxs-lookup"><span data-stu-id="f2b18-106">This is a self-hosted WCF service that implements the `ICalculator` interface and secures the endpoint using the <xref:System.ServiceModel.WSHttpBinding> with secure session and reliable session disabled.</span></span> <span data-ttu-id="f2b18-107">Le service définit une classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.</span><span class="sxs-lookup"><span data-stu-id="f2b18-107">The service defines a custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

<span data-ttu-id="f2b18-108">**Client**</span><span class="sxs-lookup"><span data-stu-id="f2b18-108">**Client**</span></span>

<span data-ttu-id="f2b18-109">Il s’agit d’un client WCF qui accède au service après une authentification réussie.</span><span class="sxs-lookup"><span data-stu-id="f2b18-109">This is a WCF client that accesses the service after successful authentication.</span></span> <span data-ttu-id="f2b18-110">Il appelle les opérations exposées par l'interface `ICalculator` et implémentées par le service.</span><span class="sxs-lookup"><span data-stu-id="f2b18-110">It invokes the operations exposed by the `ICalculator` interface and implemented by the service.</span></span> <span data-ttu-id="f2b18-111">Le client définit également la même classe `SecurityAlgorithmSuite` personnalisée pour spécifier les algorithmes de chiffrement à utiliser pour la sécurité du message.</span><span class="sxs-lookup"><span data-stu-id="f2b18-111">The client also defines the same custom `SecurityAlgorithmSuite` class to specify the cryptographic algorithms to be used for message security.</span></span>

## <a name="to-use-this-sample"></a><span data-ttu-id="f2b18-112">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="f2b18-112">To use this sample</span></span>

1. <span data-ttu-id="f2b18-113">Ouvrez la solution CryptoAgility.sln dans Visual Studio 2012.</span><span class="sxs-lookup"><span data-stu-id="f2b18-113">Open the CryptoAgility.sln solution in Visual Studio 2012.</span></span>

2. <span data-ttu-id="f2b18-114">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="f2b18-114">Press CTRL+SHIFT+B to build the solution.</span></span>

3. <span data-ttu-id="f2b18-115">Ouvrez l’Explorateur de fichiers et accédez au répertoire \WCF\Basic\Security\CryptoAgility\Service\bin et exécutez le fichier service.exe avec des privilèges d’administrateur en double-cliquant sur service.exe et en sélectionnant **exécuter en tant qu’administrateur**.</span><span class="sxs-lookup"><span data-stu-id="f2b18-115">Open File Explorer and navigate to the \WCF\Basic\Security\CryptoAgility\Service\bin directory and run the service.exe file with administrator privileges by right-clicking service.exe and selecting **Run as administrator**.</span></span>

4. <span data-ttu-id="f2b18-116">Accédez au répertoire \WCF\Basic\Security\CryptoAgility\Client\bin et exécutez le fichier client.exe normalement.</span><span class="sxs-lookup"><span data-stu-id="f2b18-116">Navigate to \WCF\Basic\Security\CryptoAgility\Client\bin directory and run the client.exe file normally.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2b18-117">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="f2b18-117">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2b18-118">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="f2b18-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="f2b18-119">Si ce répertoire n’existe pas, accédez à [Windows Communication Foundation (WCF) et des exemples de Windows Workflow Foundation (WF) pour .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les Windows Communication Foundation (WCF) et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemples.</span><span class="sxs-lookup"><span data-stu-id="f2b18-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2b18-120">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="f2b18-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Security\CryptoAgility`

## <a name="see-also"></a><span data-ttu-id="f2b18-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2b18-121">See also</span></span>

- [<span data-ttu-id="f2b18-122">Sécurité dans Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f2b18-122">Windows Communication Foundation Security</span></span>](../feature-details/security.md)
