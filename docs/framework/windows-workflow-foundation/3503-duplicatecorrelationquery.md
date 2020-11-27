---
title: 3503 - DuplicateCorrelationQuery
ms.date: 03/30/2017
ms.assetid: b857f8e6-ce4d-4da4-bc9d-6cd63fa558a4
ms.openlocfilehash: e1e64824ee9a95757ed7c00aa17fa80898219401
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270326"
---
# <a name="3503---duplicatecorrelationquery"></a><span data-ttu-id="aa53c-102">3503 - DuplicateCorrelationQuery</span><span class="sxs-lookup"><span data-stu-id="aa53c-102">3503 - DuplicateCorrelationQuery</span></span>

## <a name="properties"></a><span data-ttu-id="aa53c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="aa53c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa53c-104">id</span><span class="sxs-lookup"><span data-stu-id="aa53c-104">ID</span></span>|<span data-ttu-id="aa53c-105">3503</span><span class="sxs-lookup"><span data-stu-id="aa53c-105">3503</span></span>|  
|<span data-ttu-id="aa53c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="aa53c-106">Keywords</span></span>|<span data-ttu-id="aa53c-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="aa53c-107">WFServices</span></span>|  
|<span data-ttu-id="aa53c-108">Level</span><span class="sxs-lookup"><span data-stu-id="aa53c-108">Level</span></span>|<span data-ttu-id="aa53c-109">Avertissement</span><span class="sxs-lookup"><span data-stu-id="aa53c-109">Warning</span></span>|  
|<span data-ttu-id="aa53c-110">Channel</span><span class="sxs-lookup"><span data-stu-id="aa53c-110">Channel</span></span>|<span data-ttu-id="aa53c-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="aa53c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aa53c-112">Description</span><span class="sxs-lookup"><span data-stu-id="aa53c-112">Description</span></span>  

 <span data-ttu-id="aa53c-113">Indique qu'un CorrelationQuery en double a été trouvé.</span><span class="sxs-lookup"><span data-stu-id="aa53c-113">Indicates a duplicate CorrelationQuery was found.</span></span> <span data-ttu-id="aa53c-114">Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.</span><span class="sxs-lookup"><span data-stu-id="aa53c-114">The duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aa53c-115">Message</span><span class="sxs-lookup"><span data-stu-id="aa53c-115">Message</span></span>  

 <span data-ttu-id="aa53c-116">CorrelationQuery en double trouvé avec Where='%1'.</span><span class="sxs-lookup"><span data-stu-id="aa53c-116">A duplicate CorrelationQuery was found with Where='%1'.</span></span> <span data-ttu-id="aa53c-117">Cette requête en double ne sera pas utilisée lors du calcul de la corrélation.</span><span class="sxs-lookup"><span data-stu-id="aa53c-117">This duplicate query will not be used when calculating correlation.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aa53c-118">Détails</span><span class="sxs-lookup"><span data-stu-id="aa53c-118">Details</span></span>  
  
|<span data-ttu-id="aa53c-119">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="aa53c-119">Data Item Name</span></span>|<span data-ttu-id="aa53c-120">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="aa53c-120">Data Item Type</span></span>|<span data-ttu-id="aa53c-121">Description</span><span class="sxs-lookup"><span data-stu-id="aa53c-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aa53c-122">Where</span><span class="sxs-lookup"><span data-stu-id="aa53c-122">Where</span></span>|<span data-ttu-id="aa53c-123">xs:string</span><span class="sxs-lookup"><span data-stu-id="aa53c-123">xs:string</span></span>|<span data-ttu-id="aa53c-124">Partie Where de la requête de corrélation.</span><span class="sxs-lookup"><span data-stu-id="aa53c-124">The Where portion of the correlation query.</span></span>|  
|<span data-ttu-id="aa53c-125">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aa53c-125">AppDomain</span></span>|<span data-ttu-id="aa53c-126">xs:string</span><span class="sxs-lookup"><span data-stu-id="aa53c-126">xs:string</span></span>|<span data-ttu-id="aa53c-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="aa53c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
