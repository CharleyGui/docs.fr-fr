---
title: Point de terminaison
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 03c401358839671d750985b95b1aada599931aad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795897"
---
# <a name="endpoint"></a><span data-ttu-id="98eeb-102">Point de terminaison</span><span class="sxs-lookup"><span data-stu-id="98eeb-102">Endpoint</span></span>
<span data-ttu-id="98eeb-103">Point de terminaison</span><span class="sxs-lookup"><span data-stu-id="98eeb-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98eeb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98eeb-104">Syntax</span></span>  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="98eeb-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="98eeb-105">Methods</span></span>  
 <span data-ttu-id="98eeb-106">La classe Endpoint définit la méthode suivante.</span><span class="sxs-lookup"><span data-stu-id="98eeb-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="98eeb-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="98eeb-107">Method</span></span>|<span data-ttu-id="98eeb-108">Description</span><span class="sxs-lookup"><span data-stu-id="98eeb-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98eeb-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="98eeb-109">GetOperationCounterInstanceName</span></span>](getoperationcounterinstancename.md)|<span data-ttu-id="98eeb-110">Récupère le nom d'instance du compteur de performance d'opération</span><span class="sxs-lookup"><span data-stu-id="98eeb-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="98eeb-111">Properties</span><span class="sxs-lookup"><span data-stu-id="98eeb-111">Properties</span></span>  
 <span data-ttu-id="98eeb-112">La classe Endpoint a les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="98eeb-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="98eeb-113">Adresse</span><span class="sxs-lookup"><span data-stu-id="98eeb-113">Address</span></span>  
 <span data-ttu-id="98eeb-114">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98eeb-114">Data type: string</span></span>  
  
 <span data-ttu-id="98eeb-115">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-116">URI qui contient l'adresse du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="98eeb-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="98eeb-117">AddressHeaders</span></span>  
 <span data-ttu-id="98eeb-118">Type de données : tableau de chaînes</span><span class="sxs-lookup"><span data-stu-id="98eeb-118">Data type: string array</span></span>  
  
 <span data-ttu-id="98eeb-119">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-120">Collection d’en-têtes d’adresse jointe à ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="98eeb-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="98eeb-121">AddressIdentity</span></span>  
 <span data-ttu-id="98eeb-122">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98eeb-122">Data type: string</span></span>  
  
 <span data-ttu-id="98eeb-123">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-124">Identité du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="98eeb-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="98eeb-125">AppDomainId</span></span>  
 <span data-ttu-id="98eeb-126">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="98eeb-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="98eeb-127">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-128">ID du domaine d'application qui héberge le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="98eeb-129">comportements</span><span class="sxs-lookup"><span data-stu-id="98eeb-129">Behaviors</span></span>  
 <span data-ttu-id="98eeb-130">Type de données : Tableau de comportements</span><span class="sxs-lookup"><span data-stu-id="98eeb-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="98eeb-131">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-132">Collection de comportements implémentée par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="98eeb-133">Liaison</span><span class="sxs-lookup"><span data-stu-id="98eeb-133">Binding</span></span>  
 <span data-ttu-id="98eeb-134">Type de données : Liaison</span><span class="sxs-lookup"><span data-stu-id="98eeb-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="98eeb-135">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-136">Liaison utilisée par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="98eeb-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="98eeb-137">ContractName</span></span>  
 <span data-ttu-id="98eeb-138">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98eeb-138">Data type: string</span></span>  
  
 <span data-ttu-id="98eeb-139">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-140">Chaîne qui spécifie quel contrat est exposé par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="98eeb-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="98eeb-141">CounterInstanceName</span></span>  
 <span data-ttu-id="98eeb-142">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98eeb-142">Data type: string</span></span>  
  
 <span data-ttu-id="98eeb-143">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-144">Nom de l'instance des compteurs de performance du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="98eeb-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="98eeb-145">ListenUri</span></span>  
 <span data-ttu-id="98eeb-146">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98eeb-146">Data type: string</span></span>  
  
 <span data-ttu-id="98eeb-147">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-148">URI sur lequel le point de terminaison écoute.</span><span class="sxs-lookup"><span data-stu-id="98eeb-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="98eeb-149">Nom</span><span class="sxs-lookup"><span data-stu-id="98eeb-149">Name</span></span>  
 <span data-ttu-id="98eeb-150">Type de données : chaîne</span><span class="sxs-lookup"><span data-stu-id="98eeb-150">Data type: string</span></span>  
  
 <span data-ttu-id="98eeb-151">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-152">Nom unique de ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="98eeb-153">ProcessId</span><span class="sxs-lookup"><span data-stu-id="98eeb-153">ProcessId</span></span>  
 <span data-ttu-id="98eeb-154">Type de données : sint32</span><span class="sxs-lookup"><span data-stu-id="98eeb-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="98eeb-155">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-156">ID du processus qui héberge le point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="98eeb-157">ref</span><span class="sxs-lookup"><span data-stu-id="98eeb-157">ref</span></span>  
 <span data-ttu-id="98eeb-158">Type de données : Contrat</span><span class="sxs-lookup"><span data-stu-id="98eeb-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="98eeb-159">Type d’accès : Lecture seule</span><span class="sxs-lookup"><span data-stu-id="98eeb-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98eeb-160">Le contrat exposé par ce point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="98eeb-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98eeb-161">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="98eeb-161">Requirements</span></span>  
  
|<span data-ttu-id="98eeb-162">MOF</span><span class="sxs-lookup"><span data-stu-id="98eeb-162">MOF</span></span>|<span data-ttu-id="98eeb-163">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="98eeb-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="98eeb-164">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="98eeb-164">Namespace</span></span>|<span data-ttu-id="98eeb-165">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="98eeb-165">Defined in root\ServiceModel</span></span>|
