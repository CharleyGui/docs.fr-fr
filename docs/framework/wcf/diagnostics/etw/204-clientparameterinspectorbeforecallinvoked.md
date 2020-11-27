---
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: a7db8c9fa87518c59969f3089ff033fa8c912577
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96275786"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="9a4b2-102">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="9a4b2-102">204 - ClientParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="9a4b2-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="9a4b2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9a4b2-104">id</span><span class="sxs-lookup"><span data-stu-id="9a4b2-104">ID</span></span>|<span data-ttu-id="9a4b2-105">204</span><span class="sxs-lookup"><span data-stu-id="9a4b2-105">204</span></span>|  
|<span data-ttu-id="9a4b2-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="9a4b2-106">Keywords</span></span>|<span data-ttu-id="9a4b2-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9a4b2-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9a4b2-108">Level</span><span class="sxs-lookup"><span data-stu-id="9a4b2-108">Level</span></span>|<span data-ttu-id="9a4b2-109">Informations</span><span class="sxs-lookup"><span data-stu-id="9a4b2-109">Information</span></span>|  
|<span data-ttu-id="9a4b2-110">Channel</span><span class="sxs-lookup"><span data-stu-id="9a4b2-110">Channel</span></span>|<span data-ttu-id="9a4b2-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="9a4b2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9a4b2-112">Description</span><span class="sxs-lookup"><span data-stu-id="9a4b2-112">Description</span></span>  

 <span data-ttu-id="9a4b2-113">Cet événement est émis après que le modèle de service a appelé la méthode `BeforeCall` sur un inspecteur de paramètre client.</span><span class="sxs-lookup"><span data-stu-id="9a4b2-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9a4b2-114">Message</span><span class="sxs-lookup"><span data-stu-id="9a4b2-114">Message</span></span>  

 <span data-ttu-id="9a4b2-115">Le répartiteur a appelé 'BeforeCall' sur un ClientParameterInspector de type '%1.'</span><span class="sxs-lookup"><span data-stu-id="9a4b2-115">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9a4b2-116">Détails</span><span class="sxs-lookup"><span data-stu-id="9a4b2-116">Details</span></span>  
  
|<span data-ttu-id="9a4b2-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9a4b2-117">Data Item Name</span></span>|<span data-ttu-id="9a4b2-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="9a4b2-118">Data Item Type</span></span>|<span data-ttu-id="9a4b2-119">Description</span><span class="sxs-lookup"><span data-stu-id="9a4b2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9a4b2-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="9a4b2-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="9a4b2-121">CLR FullName du type d'inspecteur appelé.</span><span class="sxs-lookup"><span data-stu-id="9a4b2-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="9a4b2-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="9a4b2-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="9a4b2-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="9a4b2-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9a4b2-124">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="9a4b2-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9a4b2-125">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="9a4b2-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9a4b2-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9a4b2-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9a4b2-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="9a4b2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
