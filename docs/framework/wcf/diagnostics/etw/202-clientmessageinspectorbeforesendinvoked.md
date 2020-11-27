---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: f05a0f817b8cb4857a4fa50eada15d3ff9e06855
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266621"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="c211b-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="c211b-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="c211b-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="c211b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c211b-104">id</span><span class="sxs-lookup"><span data-stu-id="c211b-104">ID</span></span>|<span data-ttu-id="c211b-105">202</span><span class="sxs-lookup"><span data-stu-id="c211b-105">202</span></span>|  
|<span data-ttu-id="c211b-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="c211b-106">Keywords</span></span>|<span data-ttu-id="c211b-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c211b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c211b-108">Level</span><span class="sxs-lookup"><span data-stu-id="c211b-108">Level</span></span>|<span data-ttu-id="c211b-109">Informations</span><span class="sxs-lookup"><span data-stu-id="c211b-109">Information</span></span>|  
|<span data-ttu-id="c211b-110">Channel</span><span class="sxs-lookup"><span data-stu-id="c211b-110">Channel</span></span>|<span data-ttu-id="c211b-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="c211b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c211b-112">Description</span><span class="sxs-lookup"><span data-stu-id="c211b-112">Description</span></span>  

 <span data-ttu-id="c211b-113">Cet événement est émis après que le modèle de service a appelé la méthode `BeforeSendRequest` sur un inspecteur de message client.</span><span class="sxs-lookup"><span data-stu-id="c211b-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c211b-114">Message</span><span class="sxs-lookup"><span data-stu-id="c211b-114">Message</span></span>  

 <span data-ttu-id="c211b-115">Le répartiteur a appelé « BeforeSendRequest » sur un ClientMessageInspector de type « %1 ».</span><span class="sxs-lookup"><span data-stu-id="c211b-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c211b-116">Détails</span><span class="sxs-lookup"><span data-stu-id="c211b-116">Details</span></span>  
  
|<span data-ttu-id="c211b-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c211b-117">Data Item Name</span></span>|<span data-ttu-id="c211b-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="c211b-118">Data Item Type</span></span>|<span data-ttu-id="c211b-119">Description</span><span class="sxs-lookup"><span data-stu-id="c211b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c211b-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="c211b-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="c211b-121">CLR FullName du type d'inspecteur appelé.</span><span class="sxs-lookup"><span data-stu-id="c211b-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="c211b-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="c211b-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="c211b-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="c211b-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c211b-124">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="c211b-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c211b-125">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="c211b-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c211b-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c211b-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c211b-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="c211b-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
