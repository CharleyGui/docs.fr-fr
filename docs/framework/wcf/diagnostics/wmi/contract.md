---
title: Contrat
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868430"
---
# <a name="contract"></a><span data-ttu-id="520dd-102">Contrat</span><span class="sxs-lookup"><span data-stu-id="520dd-102">Contract</span></span>
<span data-ttu-id="520dd-103">Contrat</span><span class="sxs-lookup"><span data-stu-id="520dd-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="520dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="520dd-104">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="520dd-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="520dd-105">Methods</span></span>  
 <span data-ttu-id="520dd-106">La classe Contract ne définit pas de méthodes.</span><span class="sxs-lookup"><span data-stu-id="520dd-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="520dd-107">Properties</span><span class="sxs-lookup"><span data-stu-id="520dd-107">Properties</span></span>  
 <span data-ttu-id="520dd-108">La classe Contract a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="520dd-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="520dd-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="520dd-109">AppDomainId</span></span>  
 <span data-ttu-id="520dd-110">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="520dd-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="520dd-111">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-112">ID du domaine d'application qui héberge le contrat.</span><span class="sxs-lookup"><span data-stu-id="520dd-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="520dd-113">comportements</span><span class="sxs-lookup"><span data-stu-id="520dd-113">Behaviors</span></span>  
 <span data-ttu-id="520dd-114">Type de données: Tableau de comportements</span><span class="sxs-lookup"><span data-stu-id="520dd-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="520dd-115">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-116">Comportements associés à ce contrat.</span><span class="sxs-lookup"><span data-stu-id="520dd-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="520dd-117">Name</span><span class="sxs-lookup"><span data-stu-id="520dd-117">Name</span></span>  
 <span data-ttu-id="520dd-118">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="520dd-118">Data type: string</span></span>  
  
 <span data-ttu-id="520dd-119">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-120">Nom du contrat dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="520dd-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="520dd-121">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="520dd-121">Namespace</span></span>  
 <span data-ttu-id="520dd-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="520dd-122">Data type: string</span></span>  
  
 <span data-ttu-id="520dd-123">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-124">Espace de noms de l'élément `portType` dans WSDL.</span><span class="sxs-lookup"><span data-stu-id="520dd-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="520dd-125">Opérations</span><span class="sxs-lookup"><span data-stu-id="520dd-125">Operations</span></span>  
 <span data-ttu-id="520dd-126">Type de données: Tableau d’opérations</span><span class="sxs-lookup"><span data-stu-id="520dd-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="520dd-127">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-128">Opérations de ce contrat.</span><span class="sxs-lookup"><span data-stu-id="520dd-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="520dd-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="520dd-129">ProcessId</span></span>  
 <span data-ttu-id="520dd-130">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="520dd-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="520dd-131">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-132">ID du processus qui héberge le contrat.</span><span class="sxs-lookup"><span data-stu-id="520dd-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="520dd-133">ref</span><span class="sxs-lookup"><span data-stu-id="520dd-133">ref</span></span>  
 <span data-ttu-id="520dd-134">Type de données: Contrat</span><span class="sxs-lookup"><span data-stu-id="520dd-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="520dd-135">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-136">Type de rappel lorsque le contrat est un contrat duplex.</span><span class="sxs-lookup"><span data-stu-id="520dd-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="520dd-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="520dd-137">SessionMode</span></span>  
 <span data-ttu-id="520dd-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="520dd-138">Data type: string</span></span>  
  
 <span data-ttu-id="520dd-139">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-140">Indique si le contrat nécessite que la liaison associée à ce contrat utilise les sessions de canal.</span><span class="sxs-lookup"><span data-stu-id="520dd-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="520dd-141">Type</span><span class="sxs-lookup"><span data-stu-id="520dd-141">Type</span></span>  
 <span data-ttu-id="520dd-142">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="520dd-142">Data type: string</span></span>  
  
 <span data-ttu-id="520dd-143">Type d’accès: Lecture seule</span><span class="sxs-lookup"><span data-stu-id="520dd-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520dd-144">Type du contrat.</span><span class="sxs-lookup"><span data-stu-id="520dd-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="520dd-145">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="520dd-145">Requirements</span></span>  
  
|<span data-ttu-id="520dd-146">MOF</span><span class="sxs-lookup"><span data-stu-id="520dd-146">MOF</span></span>|<span data-ttu-id="520dd-147">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="520dd-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="520dd-148">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="520dd-148">Namespace</span></span>|<span data-ttu-id="520dd-149">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="520dd-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="520dd-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="520dd-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
