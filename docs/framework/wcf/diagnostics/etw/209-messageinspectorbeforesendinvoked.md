---
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 50a9424f445781cac70d7d7fde58beea10231cfa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267752"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="08730-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="08730-102">209 - MessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="08730-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="08730-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08730-104">id</span><span class="sxs-lookup"><span data-stu-id="08730-104">ID</span></span>|<span data-ttu-id="08730-105">209</span><span class="sxs-lookup"><span data-stu-id="08730-105">209</span></span>|  
|<span data-ttu-id="08730-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="08730-106">Keywords</span></span>|<span data-ttu-id="08730-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="08730-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="08730-108">Level</span><span class="sxs-lookup"><span data-stu-id="08730-108">Level</span></span>|<span data-ttu-id="08730-109">Informations</span><span class="sxs-lookup"><span data-stu-id="08730-109">Information</span></span>|  
|<span data-ttu-id="08730-110">Channel</span><span class="sxs-lookup"><span data-stu-id="08730-110">Channel</span></span>|<span data-ttu-id="08730-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="08730-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="08730-112">Description</span><span class="sxs-lookup"><span data-stu-id="08730-112">Description</span></span>  

 <span data-ttu-id="08730-113">Cet événement est émis après que le modèle de service a appelé la méthode `BeforeSend` sur un inspecteur de message.</span><span class="sxs-lookup"><span data-stu-id="08730-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="08730-114">Message</span><span class="sxs-lookup"><span data-stu-id="08730-114">Message</span></span>  

 <span data-ttu-id="08730-115">Le répartiteur a appelé 'BeforeSendRequest' sur un MessageInspector de type '%1'.</span><span class="sxs-lookup"><span data-stu-id="08730-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="08730-116">Détails</span><span class="sxs-lookup"><span data-stu-id="08730-116">Details</span></span>  
  
|<span data-ttu-id="08730-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="08730-117">Data Item Name</span></span>|<span data-ttu-id="08730-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="08730-118">Data Item Type</span></span>|<span data-ttu-id="08730-119">Description</span><span class="sxs-lookup"><span data-stu-id="08730-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="08730-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="08730-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="08730-121">CLR FullName du type de `MessageInspector` appelé.</span><span class="sxs-lookup"><span data-stu-id="08730-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="08730-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="08730-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="08730-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="08730-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="08730-124">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="08730-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="08730-125">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="08730-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="08730-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="08730-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="08730-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="08730-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
