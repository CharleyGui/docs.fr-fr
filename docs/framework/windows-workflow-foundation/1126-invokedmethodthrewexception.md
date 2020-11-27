---
title: 1126 - InvokedMethodThrewException
ms.date: 03/30/2017
ms.assetid: 0d3cff1a-97e6-4b6c-be18-108c6881bfc0
ms.openlocfilehash: 7caaebe42f49a62fec61ba17a4d3fe3a538e2ab4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262838"
---
# <a name="1126---invokedmethodthrewexception"></a><span data-ttu-id="eabbf-102">1126 - InvokedMethodThrewException</span><span class="sxs-lookup"><span data-stu-id="eabbf-102">1126 - InvokedMethodThrewException</span></span>

## <a name="properties"></a><span data-ttu-id="eabbf-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="eabbf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="eabbf-104">id</span><span class="sxs-lookup"><span data-stu-id="eabbf-104">ID</span></span>|<span data-ttu-id="eabbf-105">1126</span><span class="sxs-lookup"><span data-stu-id="eabbf-105">1126</span></span>|  
|<span data-ttu-id="eabbf-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="eabbf-106">Keywords</span></span>|<span data-ttu-id="eabbf-107">WFRuntime</span><span class="sxs-lookup"><span data-stu-id="eabbf-107">WFRuntime</span></span>|  
|<span data-ttu-id="eabbf-108">Level</span><span class="sxs-lookup"><span data-stu-id="eabbf-108">Level</span></span>|<span data-ttu-id="eabbf-109">Informations</span><span class="sxs-lookup"><span data-stu-id="eabbf-109">Information</span></span>|  
|<span data-ttu-id="eabbf-110">Channel</span><span class="sxs-lookup"><span data-stu-id="eabbf-110">Channel</span></span>|<span data-ttu-id="eabbf-111">Microsoft-Windows-Application Server-Applications/Débogage</span><span class="sxs-lookup"><span data-stu-id="eabbf-111">Microsoft-Windows-Application Server-Applications/Debug</span></span>|  
  
## <a name="description"></a><span data-ttu-id="eabbf-112">Description</span><span class="sxs-lookup"><span data-stu-id="eabbf-112">Description</span></span>  

 <span data-ttu-id="eabbf-113">Indique qu'une exception a été levée par la méthode appelée par l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="eabbf-113">Indicates an exception was thrown by the method called by the InvokeMethod activity.</span></span>  
  
## <a name="message"></a><span data-ttu-id="eabbf-114">Message</span><span class="sxs-lookup"><span data-stu-id="eabbf-114">Message</span></span>  

 <span data-ttu-id="eabbf-115">Une exception a été levée dans la méthode appelée par l'activité « %1 ».</span><span class="sxs-lookup"><span data-stu-id="eabbf-115">An exception was thrown in the method called by the activity '%1'.</span></span> <span data-ttu-id="eabbf-116">%2</span><span class="sxs-lookup"><span data-stu-id="eabbf-116">%2</span></span>  
  
## <a name="details"></a><span data-ttu-id="eabbf-117">Détails</span><span class="sxs-lookup"><span data-stu-id="eabbf-117">Details</span></span>  
  
|<span data-ttu-id="eabbf-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="eabbf-118">Data Item Name</span></span>|<span data-ttu-id="eabbf-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="eabbf-119">Data Item Type</span></span>|<span data-ttu-id="eabbf-120">Description</span><span class="sxs-lookup"><span data-stu-id="eabbf-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="eabbf-121">InvokeMethod</span><span class="sxs-lookup"><span data-stu-id="eabbf-121">InvokeMethod</span></span>|<span data-ttu-id="eabbf-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="eabbf-122">xs:string</span></span>|<span data-ttu-id="eabbf-123">Nom complet de l'activité InvokeMethod.</span><span class="sxs-lookup"><span data-stu-id="eabbf-123">The display name of the InvokeMethod activity.</span></span>|  
|<span data-ttu-id="eabbf-124">Exception</span><span class="sxs-lookup"><span data-stu-id="eabbf-124">Exception</span></span>|<span data-ttu-id="eabbf-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="eabbf-125">xs:string</span></span>|<span data-ttu-id="eabbf-126">Détails de l'exception</span><span class="sxs-lookup"><span data-stu-id="eabbf-126">The exception details for the exception</span></span>|  
|<span data-ttu-id="eabbf-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="eabbf-127">AppDomain</span></span>|<span data-ttu-id="eabbf-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="eabbf-128">xs:string</span></span>|<span data-ttu-id="eabbf-129">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="eabbf-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
