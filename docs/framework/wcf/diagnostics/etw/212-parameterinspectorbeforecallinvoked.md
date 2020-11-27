---
title: 212 - ParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 063fc8d2-ceac-4c18-8368-de84f2c78035
ms.openlocfilehash: 28c2aca4555d2e4ff498e450deae55ad6a87743c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279036"
---
# <a name="212---parameterinspectorbeforecallinvoked"></a><span data-ttu-id="999ac-102">212 - ParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="999ac-102">212 - ParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="999ac-103">Propriétés</span><span class="sxs-lookup"><span data-stu-id="999ac-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="999ac-104">id</span><span class="sxs-lookup"><span data-stu-id="999ac-104">ID</span></span>|<span data-ttu-id="999ac-105">212</span><span class="sxs-lookup"><span data-stu-id="999ac-105">212</span></span>|  
|<span data-ttu-id="999ac-106">Mots clés</span><span class="sxs-lookup"><span data-stu-id="999ac-106">Keywords</span></span>|<span data-ttu-id="999ac-107">Dépannage, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="999ac-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="999ac-108">Level</span><span class="sxs-lookup"><span data-stu-id="999ac-108">Level</span></span>|<span data-ttu-id="999ac-109">Informations</span><span class="sxs-lookup"><span data-stu-id="999ac-109">Information</span></span>|  
|<span data-ttu-id="999ac-110">Channel</span><span class="sxs-lookup"><span data-stu-id="999ac-110">Channel</span></span>|<span data-ttu-id="999ac-111">Microsoft-Windows-Application Server-Applications/Analyse</span><span class="sxs-lookup"><span data-stu-id="999ac-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="999ac-112">Description</span><span class="sxs-lookup"><span data-stu-id="999ac-112">Description</span></span>  

 <span data-ttu-id="999ac-113">Cet événement est émis après que le modèle de service a appelé la méthode `BeforeCall` sur un `ParameterInspector`.</span><span class="sxs-lookup"><span data-stu-id="999ac-113">This event is emitted after the Service Model has invoked the `BeforeCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="999ac-114">Message</span><span class="sxs-lookup"><span data-stu-id="999ac-114">Message</span></span>  

 <span data-ttu-id="999ac-115">Le répartiteur a appelé 'BeforeCall' sur un ParameterInspector de type '%1.'</span><span class="sxs-lookup"><span data-stu-id="999ac-115">The Dispatcher invoked 'BeforeCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="999ac-116">Détails</span><span class="sxs-lookup"><span data-stu-id="999ac-116">Details</span></span>  
  
|<span data-ttu-id="999ac-117">Nom d'élément de données</span><span class="sxs-lookup"><span data-stu-id="999ac-117">Data Item Name</span></span>|<span data-ttu-id="999ac-118">Type d'élément de données</span><span class="sxs-lookup"><span data-stu-id="999ac-118">Data Item Type</span></span>|<span data-ttu-id="999ac-119">Description</span><span class="sxs-lookup"><span data-stu-id="999ac-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="999ac-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="999ac-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="999ac-121">CLR FullName du type d'inspecteur appelé.</span><span class="sxs-lookup"><span data-stu-id="999ac-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="999ac-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="999ac-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="999ac-123">Pour les services hébergés par le Web, ce champ identifie de manière unique le service dans la hiérarchie Web.</span><span class="sxs-lookup"><span data-stu-id="999ac-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="999ac-124">Son format est défini en tant que « chemin d’accès virtuel de l’application nom du site Web&#124;chemin d’accès virtuel du service&#124;ServiceName ».</span><span class="sxs-lookup"><span data-stu-id="999ac-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="999ac-125">Exemple : « Default Web site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService ».</span><span class="sxs-lookup"><span data-stu-id="999ac-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="999ac-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="999ac-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="999ac-127">Chaîne retournée par AppDomain.CurrentDomain.FriendlyName.</span><span class="sxs-lookup"><span data-stu-id="999ac-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
