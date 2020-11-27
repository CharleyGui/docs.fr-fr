---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 61605d666911cce277bcebbb0a2f803e9a5dcfeb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261304"
---
# <a name="3550---bufferoutofordermessagenoinstance"></a><span data-ttu-id="3f46c-102">3550 - BufferOutOfOrderMessageNoInstance</span><span class="sxs-lookup"><span data-stu-id="3f46c-102">3550 - BufferOutOfOrderMessageNoInstance</span></span>

## <a name="properties"></a><span data-ttu-id="3f46c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="3f46c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3f46c-104">id</span><span class="sxs-lookup"><span data-stu-id="3f46c-104">ID</span></span>|<span data-ttu-id="3f46c-105">3550</span><span class="sxs-lookup"><span data-stu-id="3f46c-105">3550</span></span>|  
|<span data-ttu-id="3f46c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="3f46c-106">Keywords</span></span>|<span data-ttu-id="3f46c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="3f46c-107">WFServices</span></span>|  
|<span data-ttu-id="3f46c-108">Level</span><span class="sxs-lookup"><span data-stu-id="3f46c-108">Level</span></span>|<span data-ttu-id="3f46c-109">Informations</span><span class="sxs-lookup"><span data-stu-id="3f46c-109">Information</span></span>|  
|<span data-ttu-id="3f46c-110">Channel</span><span class="sxs-lookup"><span data-stu-id="3f46c-110">Channel</span></span>|<span data-ttu-id="3f46c-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="3f46c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3f46c-112">Description</span><span class="sxs-lookup"><span data-stu-id="3f46c-112">Description</span></span>  

 <span data-ttu-id="3f46c-113">Indique qu'une réception mise en mémoire tampon a échoué.</span><span class="sxs-lookup"><span data-stu-id="3f46c-113">Indicates a buffered receive has failed.</span></span> <span data-ttu-id="3f46c-114">Une autre tentative d'opération sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="3f46c-114">The operation will be attempted again when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3f46c-115">Message</span><span class="sxs-lookup"><span data-stu-id="3f46c-115">Message</span></span>  

 <span data-ttu-id="3f46c-116">Impossible d'effectuer l'opération « %1 » actuellement.</span><span class="sxs-lookup"><span data-stu-id="3f46c-116">Operation '%1' cannot be performed at this time.</span></span> <span data-ttu-id="3f46c-117">Une autre tentative sera faite lorsque l'instance de service sera prête à traiter cette opération.</span><span class="sxs-lookup"><span data-stu-id="3f46c-117">Another attempt will be made when the service instance is ready to process this particular operation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3f46c-118">Détails</span><span class="sxs-lookup"><span data-stu-id="3f46c-118">Details</span></span>  
  
|<span data-ttu-id="3f46c-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3f46c-119">Data Item Name</span></span>|<span data-ttu-id="3f46c-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="3f46c-120">Data Item Type</span></span>|<span data-ttu-id="3f46c-121">Description</span><span class="sxs-lookup"><span data-stu-id="3f46c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3f46c-122">NomOpération</span><span class="sxs-lookup"><span data-stu-id="3f46c-122">OperationName</span></span>|<span data-ttu-id="3f46c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f46c-123">xs:string</span></span>|<span data-ttu-id="3f46c-124">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="3f46c-124">The name of the operation.</span></span>|  
|<span data-ttu-id="3f46c-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3f46c-125">AppDomain</span></span>|<span data-ttu-id="3f46c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="3f46c-126">xs:string</span></span>|<span data-ttu-id="3f46c-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="3f46c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
