---
title: 3551 - BufferOutOfOrderMessageNoBookmark
ms.date: 03/30/2017
ms.assetid: 7930d6c4-c843-4a83-933a-cecd71b80d1e
ms.openlocfilehash: 5e6a5f9d21435fee8309bd222443407e50ec2cee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263605"
---
# <a name="3551---bufferoutofordermessagenobookmark"></a><span data-ttu-id="18d68-102">3551 - BufferOutOfOrderMessageNoBookmark</span><span class="sxs-lookup"><span data-stu-id="18d68-102">3551 - BufferOutOfOrderMessageNoBookmark</span></span>

## <a name="properties"></a><span data-ttu-id="18d68-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="18d68-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="18d68-104">id</span><span class="sxs-lookup"><span data-stu-id="18d68-104">ID</span></span>|<span data-ttu-id="18d68-105">3551</span><span class="sxs-lookup"><span data-stu-id="18d68-105">3551</span></span>|  
|<span data-ttu-id="18d68-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="18d68-106">Keywords</span></span>|<span data-ttu-id="18d68-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="18d68-107">WFServices</span></span>|  
|<span data-ttu-id="18d68-108">Level</span><span class="sxs-lookup"><span data-stu-id="18d68-108">Level</span></span>|<span data-ttu-id="18d68-109">Informations</span><span class="sxs-lookup"><span data-stu-id="18d68-109">Information</span></span>|  
|<span data-ttu-id="18d68-110">Channel</span><span class="sxs-lookup"><span data-stu-id="18d68-110">Channel</span></span>|<span data-ttu-id="18d68-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="18d68-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="18d68-112">Description</span><span class="sxs-lookup"><span data-stu-id="18d68-112">Description</span></span>  

 <span data-ttu-id="18d68-113">Indique qu'une reprise de signet a échoué.</span><span class="sxs-lookup"><span data-stu-id="18d68-113">Indicates a bookmark resumption has failed.</span></span> <span data-ttu-id="18d68-114">Une autre tentative d'opération de réception en mémoire tampon sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="18d68-114">The buffered receive operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="18d68-115">Message</span><span class="sxs-lookup"><span data-stu-id="18d68-115">Message</span></span>  

 <span data-ttu-id="18d68-116">Impossible d'effectuer actuellement l'opération « %2 » sur l'instance de service « %1 ».</span><span class="sxs-lookup"><span data-stu-id="18d68-116">Operation '%2' on service instance '%1' cannot be performed at this time.</span></span> <span data-ttu-id="18d68-117">Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="18d68-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="18d68-118">Détails</span><span class="sxs-lookup"><span data-stu-id="18d68-118">Details</span></span>  
  
|<span data-ttu-id="18d68-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="18d68-119">Data Item Name</span></span>|<span data-ttu-id="18d68-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="18d68-120">Data Item Type</span></span>|<span data-ttu-id="18d68-121">Description</span><span class="sxs-lookup"><span data-stu-id="18d68-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="18d68-122">NomOpération</span><span class="sxs-lookup"><span data-stu-id="18d68-122">OperationName</span></span>|<span data-ttu-id="18d68-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="18d68-123">xs:string</span></span>|<span data-ttu-id="18d68-124">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="18d68-124">The name of the operation.</span></span>|  
|<span data-ttu-id="18d68-125">ServiceInstanceId</span><span class="sxs-lookup"><span data-stu-id="18d68-125">ServiceInstanceId</span></span>|<span data-ttu-id="18d68-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="18d68-126">xs:string</span></span>|<span data-ttu-id="18d68-127">ID de l'instance du service.</span><span class="sxs-lookup"><span data-stu-id="18d68-127">The id of the service instance.</span></span>|  
|<span data-ttu-id="18d68-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="18d68-128">AppDomain</span></span>|<span data-ttu-id="18d68-129">xs:string</span><span class="sxs-lookup"><span data-stu-id="18d68-129">xs:string</span></span>|<span data-ttu-id="18d68-130">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="18d68-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
