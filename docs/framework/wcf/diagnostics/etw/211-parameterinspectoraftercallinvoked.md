---
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: 7027b6557520a9ccb587f8d383d3598571da5838
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279062"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="a7794-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="a7794-102">211 - ParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="a7794-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="a7794-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a7794-104">id</span><span class="sxs-lookup"><span data-stu-id="a7794-104">ID</span></span>|<span data-ttu-id="a7794-105">211</span><span class="sxs-lookup"><span data-stu-id="a7794-105">211</span></span>|  
|<span data-ttu-id="a7794-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="a7794-106">Keywords</span></span>|<span data-ttu-id="a7794-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a7794-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="a7794-108">Level</span><span class="sxs-lookup"><span data-stu-id="a7794-108">Level</span></span>|<span data-ttu-id="a7794-109">Informations</span><span class="sxs-lookup"><span data-stu-id="a7794-109">Information</span></span>|  
|<span data-ttu-id="a7794-110">Channel</span><span class="sxs-lookup"><span data-stu-id="a7794-110">Channel</span></span>|<span data-ttu-id="a7794-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="a7794-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a7794-112">Description</span><span class="sxs-lookup"><span data-stu-id="a7794-112">Description</span></span>  

 <span data-ttu-id="a7794-113">Cet événement est émis après que le modèle de service a appelé la méthode `AfterCall` sur un `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="a7794-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a7794-114">Message</span><span class="sxs-lookup"><span data-stu-id="a7794-114">Message</span></span>  

 <span data-ttu-id="a7794-115">Le répartiteur a appelé 'AfterCall' sur un ParameterInspector de type '%1'.</span><span class="sxs-lookup"><span data-stu-id="a7794-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="a7794-116">Détails</span><span class="sxs-lookup"><span data-stu-id="a7794-116">Details</span></span>  
  
|<span data-ttu-id="a7794-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a7794-117">Data Item Name</span></span>|<span data-ttu-id="a7794-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="a7794-118">Data Item Type</span></span>|<span data-ttu-id="a7794-119">Description</span><span class="sxs-lookup"><span data-stu-id="a7794-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a7794-120">Nom de type</span><span class="sxs-lookup"><span data-stu-id="a7794-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="a7794-121">CLR FullName du type de `ParameterInspector` appelé.</span><span class="sxs-lookup"><span data-stu-id="a7794-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="a7794-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="a7794-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="a7794-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="a7794-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a7794-124">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="a7794-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a7794-125">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="a7794-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a7794-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="a7794-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="a7794-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="a7794-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
