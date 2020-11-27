---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 4aa0f41b0b772551d9257920e5c15051961b7332
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267817"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="71a9c-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="71a9c-102">208 - MessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="71a9c-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="71a9c-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="71a9c-104">id</span><span class="sxs-lookup"><span data-stu-id="71a9c-104">ID</span></span>|<span data-ttu-id="71a9c-105">208</span><span class="sxs-lookup"><span data-stu-id="71a9c-105">208</span></span>|  
|<span data-ttu-id="71a9c-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="71a9c-106">Keywords</span></span>|<span data-ttu-id="71a9c-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="71a9c-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="71a9c-108">Level</span><span class="sxs-lookup"><span data-stu-id="71a9c-108">Level</span></span>|<span data-ttu-id="71a9c-109">Informations</span><span class="sxs-lookup"><span data-stu-id="71a9c-109">Information</span></span>|  
|<span data-ttu-id="71a9c-110">Channel</span><span class="sxs-lookup"><span data-stu-id="71a9c-110">Channel</span></span>|<span data-ttu-id="71a9c-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="71a9c-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="71a9c-112">Description</span><span class="sxs-lookup"><span data-stu-id="71a9c-112">Description</span></span>  

 <span data-ttu-id="71a9c-113">Cet événement est émis après que le modèle de service a appelé la méthode `AfterReceive` sur un inspecteur de message.</span><span class="sxs-lookup"><span data-stu-id="71a9c-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="71a9c-114">Message</span><span class="sxs-lookup"><span data-stu-id="71a9c-114">Message</span></span>  

 <span data-ttu-id="71a9c-115">Le répartiteur a appelé 'AfterReceiveReply' sur un MessageInspector de type '%1'.</span><span class="sxs-lookup"><span data-stu-id="71a9c-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="71a9c-116">Détails</span><span class="sxs-lookup"><span data-stu-id="71a9c-116">Details</span></span>  
  
|<span data-ttu-id="71a9c-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="71a9c-117">Data Item Name</span></span>|<span data-ttu-id="71a9c-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="71a9c-118">Data Item Type</span></span>|<span data-ttu-id="71a9c-119">Description</span><span class="sxs-lookup"><span data-stu-id="71a9c-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="71a9c-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="71a9c-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="71a9c-121">CLR FullName du type de `MessageInspector` appelé.</span><span class="sxs-lookup"><span data-stu-id="71a9c-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="71a9c-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="71a9c-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="71a9c-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="71a9c-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="71a9c-124">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="71a9c-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="71a9c-125">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="71a9c-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="71a9c-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="71a9c-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="71a9c-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="71a9c-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
