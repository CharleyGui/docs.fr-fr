---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: a70a4ba40b569acc7893b21d796194224dc4ee78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274047"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="72453-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="72453-102">DeliveryRequirementsAttribute</span></span>

<span data-ttu-id="72453-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="72453-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72453-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72453-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="72453-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="72453-105">Methods</span></span>  

 <span data-ttu-id="72453-106">La classe DeliveryRequirementsAttribute ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="72453-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="72453-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="72453-107">Properties</span></span>  

 <span data-ttu-id="72453-108">La classe DeliveryRequirementsAttribute a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="72453-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="72453-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="72453-109">QueuedDeliveryRequirements</span></span>  

 <span data-ttu-id="72453-110">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="72453-110">Data type: string</span></span>  
  
 <span data-ttu-id="72453-111">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="72453-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72453-112">Spécifie si la liaison pour un service prend en charge des contrats.</span><span class="sxs-lookup"><span data-stu-id="72453-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="72453-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="72453-113">RequireOrderedDelivery</span></span>  

 <span data-ttu-id="72453-114">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="72453-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="72453-115">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="72453-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72453-116">Spécifie si la liaison prend en charge les messages ordonnés.</span><span class="sxs-lookup"><span data-stu-id="72453-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="72453-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="72453-117">TargetContract</span></span>  

 <span data-ttu-id="72453-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="72453-118">Data type: string</span></span>  
  
 <span data-ttu-id="72453-119">Type d'accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="72453-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72453-120">Contrat auquel il s'applique.</span><span class="sxs-lookup"><span data-stu-id="72453-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72453-121">Spécifications</span><span class="sxs-lookup"><span data-stu-id="72453-121">Requirements</span></span>  
  
|<span data-ttu-id="72453-122">MOF</span><span class="sxs-lookup"><span data-stu-id="72453-122">MOF</span></span>|<span data-ttu-id="72453-123">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="72453-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="72453-124">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="72453-124">Namespace</span></span>|<span data-ttu-id="72453-125">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="72453-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72453-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="72453-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
