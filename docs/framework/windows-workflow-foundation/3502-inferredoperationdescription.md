---
title: 3502 - InferredOperationDescription
ms.date: 03/30/2017
ms.assetid: 6aebb614-3c72-4537-ba11-3cc7200ef1f1
ms.openlocfilehash: 05278067e3f86612ee4aafbe7d5eb66dc934cb85
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242108"
---
# <a name="3502---inferredoperationdescription"></a><span data-ttu-id="1a389-102">3502 - InferredOperationDescription</span><span class="sxs-lookup"><span data-stu-id="1a389-102">3502 - InferredOperationDescription</span></span>

## <a name="properties"></a><span data-ttu-id="1a389-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="1a389-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1a389-104">id</span><span class="sxs-lookup"><span data-stu-id="1a389-104">ID</span></span>|<span data-ttu-id="1a389-105">3502</span><span class="sxs-lookup"><span data-stu-id="1a389-105">3502</span></span>|  
|<span data-ttu-id="1a389-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="1a389-106">Keywords</span></span>|<span data-ttu-id="1a389-107">WFServices</span><span class="sxs-lookup"><span data-stu-id="1a389-107">WFServices</span></span>|  
|<span data-ttu-id="1a389-108">Level</span><span class="sxs-lookup"><span data-stu-id="1a389-108">Level</span></span>|<span data-ttu-id="1a389-109">Informations</span><span class="sxs-lookup"><span data-stu-id="1a389-109">Information</span></span>|  
|<span data-ttu-id="1a389-110">Channel</span><span class="sxs-lookup"><span data-stu-id="1a389-110">Channel</span></span>|<span data-ttu-id="1a389-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="1a389-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1a389-112">Description</span><span class="sxs-lookup"><span data-stu-id="1a389-112">Description</span></span>  

 <span data-ttu-id="1a389-113">Indique qu'un OperationDescription a été déduit de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="1a389-113">Indicates an OperationDescription has been inferred from WorkflowService.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1a389-114">Message</span><span class="sxs-lookup"><span data-stu-id="1a389-114">Message</span></span>  

 <span data-ttu-id="1a389-115">OperationDescription avec Name='%1' dans le contrat « %2 » a été déduit de WorkflowService.</span><span class="sxs-lookup"><span data-stu-id="1a389-115">OperationDescription with Name='%1' in contract '%2' has been inferred from WorkflowService.</span></span> <span data-ttu-id="1a389-116">IsOneWay=%3.</span><span class="sxs-lookup"><span data-stu-id="1a389-116">IsOneWay=%3.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1a389-117">Détails</span><span class="sxs-lookup"><span data-stu-id="1a389-117">Details</span></span>  
  
|<span data-ttu-id="1a389-118">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1a389-118">Data Item Name</span></span>|<span data-ttu-id="1a389-119">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="1a389-119">Data Item Type</span></span>|<span data-ttu-id="1a389-120">Description</span><span class="sxs-lookup"><span data-stu-id="1a389-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1a389-121">NomOpération</span><span class="sxs-lookup"><span data-stu-id="1a389-121">OperationName</span></span>|<span data-ttu-id="1a389-122">xs:string</span><span class="sxs-lookup"><span data-stu-id="1a389-122">xs:string</span></span>|<span data-ttu-id="1a389-123">Nom de l'opération.</span><span class="sxs-lookup"><span data-stu-id="1a389-123">The name of the operation.</span></span>|  
|<span data-ttu-id="1a389-124">ContractName</span><span class="sxs-lookup"><span data-stu-id="1a389-124">ContractName</span></span>|<span data-ttu-id="1a389-125">xs:string</span><span class="sxs-lookup"><span data-stu-id="1a389-125">xs:string</span></span>|<span data-ttu-id="1a389-126">Nom du contrat.</span><span class="sxs-lookup"><span data-stu-id="1a389-126">The name of the contract.</span></span>|  
|<span data-ttu-id="1a389-127">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="1a389-127">IsOneWay</span></span>|<span data-ttu-id="1a389-128">xs:string</span><span class="sxs-lookup"><span data-stu-id="1a389-128">xs:string</span></span>|<span data-ttu-id="1a389-129">True ou False indiquant si le contrat est unidirectionnel.</span><span class="sxs-lookup"><span data-stu-id="1a389-129">True or False indicating if the contract is one-way.</span></span>|  
|<span data-ttu-id="1a389-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1a389-130">AppDomain</span></span>|<span data-ttu-id="1a389-131">xs:string</span><span class="sxs-lookup"><span data-stu-id="1a389-131">xs:string</span></span>|<span data-ttu-id="1a389-132">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="1a389-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
