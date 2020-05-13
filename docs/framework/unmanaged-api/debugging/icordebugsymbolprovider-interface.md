---
title: ICorDebugSymbolProvider, interface
ms.date: 03/30/2017
ms.assetid: 85b24196-b6c6-4bda-9de3-47180bd6ff96
ms.openlocfilehash: 25faad4f4bc67b57c339bc63d1a18ab4d275cd71
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379349"
---
# <a name="icordebugsymbolprovider-interface"></a><span data-ttu-id="9de8e-102">ICorDebugSymbolProvider, interface</span><span class="sxs-lookup"><span data-stu-id="9de8e-102">ICorDebugSymbolProvider Interface</span></span>
<span data-ttu-id="9de8e-103">Fournit des méthodes pouvant être utilisées pour récupérer des informations sur les symboles de débogage.</span><span class="sxs-lookup"><span data-stu-id="9de8e-103">Provides methods that can be used to retrieve debug symbol information.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9de8e-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="9de8e-104">Methods</span></span>  
  
|<span data-ttu-id="9de8e-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-105">Method</span></span>|<span data-ttu-id="9de8e-106">Description</span><span class="sxs-lookup"><span data-stu-id="9de8e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9de8e-107">GetAssemblyImageBytes, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-107">GetAssemblyImageBytes Method</span></span>](icordebugsymbolprovider-getassemblyimagebytes-method.md)|<span data-ttu-id="9de8e-108">Lit les données d’un assembly fusionné pour une adresse virtuelle relative (RVA) donnée dans l’assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="9de8e-108">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>|  
|[<span data-ttu-id="9de8e-109">GetAssemblyImageMetadata, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-109">GetAssemblyImageMetadata Method</span></span>](icordebugsymbolprovider-getassemblyimagemetadata-method.md)|<span data-ttu-id="9de8e-110">Retourne les métadonnées d'un assembly fusionné.</span><span class="sxs-lookup"><span data-stu-id="9de8e-110">Returns the metadata from a merged assembly.</span></span>|  
|[<span data-ttu-id="9de8e-111">GetCodeRange, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-111">GetCodeRange Method</span></span>](icordebugsymbolprovider-getcoderange-method.md)|<span data-ttu-id="9de8e-112">Obtient l'adresse de début et la taille de la méthode pour une adresse virtuelle relative (RVA) donnée dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="9de8e-112">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>|  
|[<span data-ttu-id="9de8e-113">GetInstanceFieldSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-113">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)|<span data-ttu-id="9de8e-114">Obtient les symboles de champ d'instance qui correspondent à une signature typespec.</span><span class="sxs-lookup"><span data-stu-id="9de8e-114">Gets the instance field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="9de8e-115">GetMergedAssemblyRecords, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-115">GetMergedAssemblyRecords Method</span></span>](icordebugsymbolprovider-getmergedassemblyrecords-method.md)|<span data-ttu-id="9de8e-116">Obtient les enregistrements de symbole de tous les assemblys fusionnés.</span><span class="sxs-lookup"><span data-stu-id="9de8e-116">Gets the symbol records for all the merged assemblies.</span></span>|  
|[<span data-ttu-id="9de8e-117">GetMethodLocalSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-117">GetMethodLocalSymbols Method</span></span>](icordebugsymbolprovider-getmethodlocalsymbols-method.md)|<span data-ttu-id="9de8e-118">Obtient les symboles locaux d'une méthode selon l'adresse virtuelle relative (RVA) de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9de8e-118">Gets a method's local symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="9de8e-119">GetMethodParameterSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-119">GetMethodParameterSymbols Method</span></span>](icordebugsymbolprovider-getmethodparametersymbols-method.md)|<span data-ttu-id="9de8e-120">Obtient les symboles de paramètre d'une méthode en fonction de l'adresse virtuelle relative (RVA) de cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9de8e-120">Gets a method's parameter symbols given the relative virtual address (RVA) of that method.</span></span>|  
|[<span data-ttu-id="9de8e-121">GetMethodProps, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)|<span data-ttu-id="9de8e-122">Retourne des informations sur les propriétés de la méthode, telles que le jeton de métadonnées de la méthode et des informations sur ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans cette méthode.</span><span class="sxs-lookup"><span data-stu-id="9de8e-122">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>|  
|[<span data-ttu-id="9de8e-123">GetObjectSize, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-123">GetObjectSize Method</span></span>](icordebugsymbolprovider-getobjectsize-method.md)|<span data-ttu-id="9de8e-124">Retourne la taille d'un objet en fonction de sa signature typespec.</span><span class="sxs-lookup"><span data-stu-id="9de8e-124">Returns the object size for an object based on its typespec signature.</span></span>|  
|[<span data-ttu-id="9de8e-125">GetStaticFieldSymbols, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-125">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)|<span data-ttu-id="9de8e-126">Obtient les symboles de champ statique qui correspondent à une signature typespec.</span><span class="sxs-lookup"><span data-stu-id="9de8e-126">Gets the static field symbols that correspond to a typespec signature.</span></span>|  
|[<span data-ttu-id="9de8e-127">GetTypeProps, méthode</span><span class="sxs-lookup"><span data-stu-id="9de8e-127">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)|<span data-ttu-id="9de8e-128">Retourne des informations sur les propriétés d'un type, comme le nombre de signature de ses paramètres génériques, en fonction d'une adresse virtuelle relative (RVA) dans une vtable.</span><span class="sxs-lookup"><span data-stu-id="9de8e-128">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9de8e-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="9de8e-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9de8e-130">Cette interface est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9de8e-130">This interface is available with .NET Native only.</span></span> <span data-ttu-id="9de8e-131">Si vous implémentez cette interface pour des scénarios ICorDebug en dehors de .NET Native, le Common Language Runtime ignore cette interface.</span><span class="sxs-lookup"><span data-stu-id="9de8e-131">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9de8e-132">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9de8e-132">Requirements</span></span>  
 <span data-ttu-id="9de8e-133">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9de8e-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9de8e-134">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9de8e-134">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9de8e-135">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9de8e-135">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9de8e-136">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9de8e-136">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9de8e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9de8e-137">See also</span></span>

- [<span data-ttu-id="9de8e-138">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9de8e-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9de8e-139">Débogage</span><span class="sxs-lookup"><span data-stu-id="9de8e-139">Debugging</span></span>](index.md)
