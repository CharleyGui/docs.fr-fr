---
title: 3557 - TransactedReceiveScopeEndCommitFailed
ms.date: 03/30/2017
ms.assetid: 079f0188-8146-49ee-b6ae-a08f4e4d2b9b
ms.openlocfilehash: 4a4979047481687ef0d5c9d5891dec8f2826beed
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263657"
---
# <a name="3557---transactedreceivescopeendcommitfailed"></a><span data-ttu-id="5fc03-102">3557 - TransactedReceiveScopeEndCommitFailed</span><span class="sxs-lookup"><span data-stu-id="5fc03-102">3557 - TransactedReceiveScopeEndCommitFailed</span></span>

## <a name="properties"></a><span data-ttu-id="5fc03-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="5fc03-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5fc03-104">id</span><span class="sxs-lookup"><span data-stu-id="5fc03-104">ID</span></span>|<span data-ttu-id="5fc03-105">3557</span><span class="sxs-lookup"><span data-stu-id="5fc03-105">3557</span></span>|  
|<span data-ttu-id="5fc03-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="5fc03-106">Keywords</span></span>|<span data-ttu-id="5fc03-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="5fc03-107">WFServices</span></span>|  
|<span data-ttu-id="5fc03-108">Level</span><span class="sxs-lookup"><span data-stu-id="5fc03-108">Level</span></span>|<span data-ttu-id="5fc03-109">Informations</span><span class="sxs-lookup"><span data-stu-id="5fc03-109">Information</span></span>|  
|<span data-ttu-id="5fc03-110">Channel</span><span class="sxs-lookup"><span data-stu-id="5fc03-110">Channel</span></span>|<span data-ttu-id="5fc03-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="5fc03-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5fc03-112">Description</span><span class="sxs-lookup"><span data-stu-id="5fc03-112">Description</span></span>  

 <span data-ttu-id="5fc03-113">Indique que l'appel à EndCommit sur un CommittableTransaction a levé une exception TransactionException.</span><span class="sxs-lookup"><span data-stu-id="5fc03-113">Indicates the call to EndCommit on a CommittableTransaction threw a TransactionException.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5fc03-114">Message</span><span class="sxs-lookup"><span data-stu-id="5fc03-114">Message</span></span>  

 <span data-ttu-id="5fc03-115">L'appel à EndCommit sur le CommittableTransaction avec l'ID = « %1 » a levé un TransactionException avec le message suivant : « %2 ».</span><span class="sxs-lookup"><span data-stu-id="5fc03-115">The call to EndCommit on the CommittableTransaction with id = '%1' threw a TransactionException with the following message: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5fc03-116">Détails</span><span class="sxs-lookup"><span data-stu-id="5fc03-116">Details</span></span>  
  
|<span data-ttu-id="5fc03-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="5fc03-117">Data Item Name</span></span>|<span data-ttu-id="5fc03-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="5fc03-118">Data Item Type</span></span>|<span data-ttu-id="5fc03-119">Description</span><span class="sxs-lookup"><span data-stu-id="5fc03-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5fc03-120">TransactionId</span><span class="sxs-lookup"><span data-stu-id="5fc03-120">TransactionId</span></span>|<span data-ttu-id="5fc03-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="5fc03-121">xs:string</span></span>|<span data-ttu-id="5fc03-122">ID de CommittableTransaction.</span><span class="sxs-lookup"><span data-stu-id="5fc03-122">The id of the CommittableTransaction.</span></span>|  
|<span data-ttu-id="5fc03-123">Exception</span><span class="sxs-lookup"><span data-stu-id="5fc03-123">Exception</span></span>|<span data-ttu-id="5fc03-124">xs:string</span><span class="sxs-lookup"><span data-stu-id="5fc03-124">xs:string</span></span>|<span data-ttu-id="5fc03-125">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="5fc03-125">The exception details for the exception</span></span>|  
|<span data-ttu-id="5fc03-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5fc03-126">AppDomain</span></span>|<span data-ttu-id="5fc03-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="5fc03-127">xs:string</span></span>|<span data-ttu-id="5fc03-128">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="5fc03-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
