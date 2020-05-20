---
title: ICLRAssemblyIdentityManager, interface
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: f06c8228d5eb850c0d5ff94d12be03d7fb75023b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615915"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="ede29-102">ICLRAssemblyIdentityManager, interface</span><span class="sxs-lookup"><span data-stu-id="ede29-102">ICLRAssemblyIdentityManager Interface</span></span>
<span data-ttu-id="ede29-103">Fournit des méthodes qui prennent en charge la communication entre l’hôte et le common language runtime (CLR) à propos des assemblys.</span><span class="sxs-lookup"><span data-stu-id="ede29-103">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ede29-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ede29-104">Methods</span></span>  
  
|<span data-ttu-id="ede29-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="ede29-105">Method</span></span>|<span data-ttu-id="ede29-106">Description</span><span class="sxs-lookup"><span data-stu-id="ede29-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ede29-107">GetBindingIdentityFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="ede29-107">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="ede29-108">Obtient les données de liaison de l’identité de l’assembly pour l’assembly dans le chemin d’accès au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ede29-108">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="ede29-109">GetBindingIdentityFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="ede29-109">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="ede29-110">Obtient les données d’identité d’assembly canoniques pour l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="ede29-110">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="ede29-111">GetCLRAssemblyReferenceList, méthode</span><span class="sxs-lookup"><span data-stu-id="ede29-111">GetCLRAssemblyReferenceList Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="ede29-112">Obtient une instance [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) à partir de la liste d’identités d’assembly partielle fournie.</span><span class="sxs-lookup"><span data-stu-id="ede29-112">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="ede29-113">GetProbingAssembliesFromReference, méthode</span><span class="sxs-lookup"><span data-stu-id="ede29-113">GetProbingAssembliesFromReference Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="ede29-114">Obtient un énumérateur [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) pour les identités d’assembly référencées par l’assembly avec l’identité spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ede29-114">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="ede29-115">GetReferencedAssembliesFromFile, méthode</span><span class="sxs-lookup"><span data-stu-id="ede29-115">GetReferencedAssembliesFromFile Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="ede29-116">Obtient une instance [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) qui contient une liste d’assemblys référencés par l’assembly dans le chemin d’accès au fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ede29-116">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="ede29-117">GetReferencedAssembliesFromStream, méthode</span><span class="sxs-lookup"><span data-stu-id="ede29-117">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="ede29-118">Obtient un pointeur vers un `ICLRReferenceAssemblyEnum` objet qui contient les données d’identité de l’assembly pour les assemblys référencés par l’assembly dans le flux spécifié.</span><span class="sxs-lookup"><span data-stu-id="ede29-118">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="ede29-119">IsStronglyNamed, méthode</span><span class="sxs-lookup"><span data-stu-id="ede29-119">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="ede29-120">Obtient une valeur qui indique si l’assembly spécifié porte un nom fort.</span><span class="sxs-lookup"><span data-stu-id="ede29-120">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ede29-121">Notes</span><span class="sxs-lookup"><span data-stu-id="ede29-121">Remarks</span></span>  
 <span data-ttu-id="ede29-122">Utilisez `ICLRAssemblyIdentityManager` pour récupérer des instances de `ICLRAssemblyReferenceList` et pour énumérer les identités d’assembly.</span><span class="sxs-lookup"><span data-stu-id="ede29-122">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ede29-123">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="ede29-123">Requirements</span></span>  
 <span data-ttu-id="ede29-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ede29-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ede29-125">**En-tête :** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ede29-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ede29-126">**Bibliothèque :** Inclus en tant que ressource dans MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ede29-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ede29-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ede29-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ede29-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ede29-128">See also</span></span>

- [<span data-ttu-id="ede29-129">ICLRAssemblyReferenceList, interface</span><span class="sxs-lookup"><span data-stu-id="ede29-129">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="ede29-130">ICLRProbingAssemblyEnum, interface</span><span class="sxs-lookup"><span data-stu-id="ede29-130">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="ede29-131">Interfaces d'hébergement</span><span class="sxs-lookup"><span data-stu-id="ede29-131">Hosting Interfaces</span></span>](hosting-interfaces.md)
