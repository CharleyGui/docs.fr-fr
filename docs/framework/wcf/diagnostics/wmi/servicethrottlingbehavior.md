---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 3bcf205964a22cdb418d0158e5ee6439169538ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273982"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="30d81-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="30d81-102">ServiceThrottlingBehavior</span></span>

<span data-ttu-id="30d81-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="30d81-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30d81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30d81-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="30d81-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="30d81-105">Methods</span></span>  

 <span data-ttu-id="30d81-106">La classe ServiceThrottlingBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="30d81-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="30d81-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="30d81-107">Properties</span></span>  

 <span data-ttu-id="30d81-108">La classe ServiceThrottlingBehavior a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="30d81-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="30d81-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="30d81-109">MaxConcurrentCalls</span></span>  

 <span data-ttu-id="30d81-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="30d81-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="30d81-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="30d81-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30d81-112">Nombre maximal de messages en cours de traitement actif sur tous les objets de répartiteur dans un ServiceHost.</span><span class="sxs-lookup"><span data-stu-id="30d81-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="30d81-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="30d81-113">MaxConcurrentInstances</span></span>  

 <span data-ttu-id="30d81-114">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="30d81-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="30d81-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="30d81-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30d81-116">Nombre maximal d'objets de service simultanément exécutables.</span><span class="sxs-lookup"><span data-stu-id="30d81-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="30d81-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="30d81-117">MaxConcurrentSessions</span></span>  

 <span data-ttu-id="30d81-118">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="30d81-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="30d81-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="30d81-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30d81-120">Nombre maximal de sessions qu'un hôte peut accepter à la fois.</span><span class="sxs-lookup"><span data-stu-id="30d81-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30d81-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="30d81-121">Requirements</span></span>  
  
|<span data-ttu-id="30d81-122">MOF</span><span class="sxs-lookup"><span data-stu-id="30d81-122">MOF</span></span>|<span data-ttu-id="30d81-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="30d81-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="30d81-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="30d81-124">Namespace</span></span>|<span data-ttu-id="30d81-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="30d81-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30d81-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="30d81-126">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
