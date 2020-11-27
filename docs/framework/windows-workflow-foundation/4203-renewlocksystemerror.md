---
title: 4203 - RenewLockSystemError
ms.date: 03/30/2017
ms.assetid: 6ec9ec6f-4ae2-45cf-b99b-02cdb9dc9ec9
ms.openlocfilehash: 17617e25c5cf8cecae608438529e9ce1a7d506f7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251267"
---
# <a name="4203---renewlocksystemerror"></a><span data-ttu-id="f4f96-102">4203 - RenewLockSystemError</span><span class="sxs-lookup"><span data-stu-id="f4f96-102">4203 - RenewLockSystemError</span></span>

## <a name="properties"></a><span data-ttu-id="f4f96-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="f4f96-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4f96-104">id</span><span class="sxs-lookup"><span data-stu-id="f4f96-104">ID</span></span>|<span data-ttu-id="f4f96-105">4203</span><span class="sxs-lookup"><span data-stu-id="f4f96-105">4203</span></span>|  
|<span data-ttu-id="f4f96-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="f4f96-106">Keywords</span></span>|<span data-ttu-id="f4f96-107">WFInstanceStore</span><span class="sxs-lookup"><span data-stu-id="f4f96-107">WFInstanceStore</span></span>|  
|<span data-ttu-id="f4f96-108">Level</span><span class="sxs-lookup"><span data-stu-id="f4f96-108">Level</span></span>|<span data-ttu-id="f4f96-109">Error</span><span class="sxs-lookup"><span data-stu-id="f4f96-109">Error</span></span>|  
|<span data-ttu-id="f4f96-110">Channel</span><span class="sxs-lookup"><span data-stu-id="f4f96-110">Channel</span></span>|<span data-ttu-id="f4f96-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="f4f96-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f4f96-112">Description</span><span class="sxs-lookup"><span data-stu-id="f4f96-112">Description</span></span>  

 <span data-ttu-id="f4f96-113">Indique que le fournisseur SQL n'a pas pu étendre l'expiration du verrou, car l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="f4f96-113">Indicates SQL provider has failed to extend lock expiration due to either lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="f4f96-114">Le SqlWorkflowInstanceStore sera annulé.</span><span class="sxs-lookup"><span data-stu-id="f4f96-114">The SqlWorkflowInstanceStore will be aborted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f4f96-115">Message</span><span class="sxs-lookup"><span data-stu-id="f4f96-115">Message</span></span>  

 <span data-ttu-id="f4f96-116">Échec de l'extension de l'expiration du verrou ; l'expiration du verrou a déjà été passée ou le propriétaire de verrou a été supprimé.</span><span class="sxs-lookup"><span data-stu-id="f4f96-116">Failed to extend lock expiration, lock expiration already passed or the lock owner was deleted.</span></span> <span data-ttu-id="f4f96-117">Abandon de SqlWorkflowInstanceStore.</span><span class="sxs-lookup"><span data-stu-id="f4f96-117">Aborting SqlWorkflowInstanceStore.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f4f96-118">Détails</span><span class="sxs-lookup"><span data-stu-id="f4f96-118">Details</span></span>  
  
|<span data-ttu-id="f4f96-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f4f96-119">Data Item Name</span></span>|<span data-ttu-id="f4f96-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="f4f96-120">Data Item Type</span></span>|<span data-ttu-id="f4f96-121">Description</span><span class="sxs-lookup"><span data-stu-id="f4f96-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f4f96-122">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f4f96-122">AppDomain</span></span>|<span data-ttu-id="f4f96-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="f4f96-123">xs:string</span></span>|<span data-ttu-id="f4f96-124">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="f4f96-124">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
