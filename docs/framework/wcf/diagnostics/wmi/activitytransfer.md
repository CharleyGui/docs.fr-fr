---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: f1978881517fe5010ccc0f5192b21bd6688f063a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291113"
---
# <a name="activitytransfer"></a><span data-ttu-id="683aa-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="683aa-102">ActivityTransfer</span></span>

<span data-ttu-id="683aa-103">Événement du transfert de l'activité</span><span class="sxs-lookup"><span data-stu-id="683aa-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="683aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="683aa-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="683aa-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="683aa-105">Methods</span></span>  

 <span data-ttu-id="683aa-106">La classe ActivityTransfer ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="683aa-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="683aa-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="683aa-107">Properties</span></span>  

 <span data-ttu-id="683aa-108">La classe ActivityTransfer a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="683aa-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="683aa-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="683aa-109">ActivityID</span></span>  
  
- <span data-ttu-id="683aa-110">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="683aa-110">Data type: object</span></span>  
    <span data-ttu-id="683aa-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="683aa-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="683aa-112">ID d’activité</span><span class="sxs-lookup"><span data-stu-id="683aa-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="683aa-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="683aa-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="683aa-114">Type de données : objet</span><span class="sxs-lookup"><span data-stu-id="683aa-114">Data type: object</span></span>  
    <span data-ttu-id="683aa-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="683aa-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="683aa-116">ID d'activité connexe</span><span class="sxs-lookup"><span data-stu-id="683aa-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="683aa-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="683aa-117">Requirements</span></span>  
  
|<span data-ttu-id="683aa-118">MOF</span><span class="sxs-lookup"><span data-stu-id="683aa-118">MOF</span></span>|<span data-ttu-id="683aa-119">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="683aa-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="683aa-120">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="683aa-120">Namespace</span></span>|<span data-ttu-id="683aa-121">Défini dans root\ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="683aa-121">Defined in root\ServiceModel.</span></span>|
