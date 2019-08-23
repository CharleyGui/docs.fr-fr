---
title: ICorProfilerInfo2::GetStringLayout, méthode
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStringLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStringLayout
helpviewer_keywords:
- GetStringLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetStringLayout method [.NET Framework profiling]
ms.assetid: 43189651-a535-4803-a1d1-f1c427ace2ca
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63ad2532240c9f18a00421281fae0d111dbfaec5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963793"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="e0df5-102">ICorProfilerInfo2::GetStringLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="e0df5-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="e0df5-103">Obtient des informations sur la disposition d'un objet string.</span><span class="sxs-lookup"><span data-stu-id="e0df5-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="e0df5-104">Cette méthode est déconseillée dans le .NET Framework 4 et est remplacée par la méthode [ICorProfilerInfo3:: GetStringLayout2,](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="e0df5-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0df5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0df5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0df5-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e0df5-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="e0df5-107">à Pointeur vers le décalage de l’emplacement, relatif au `ObjectID` pointeur, qui stocke la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e0df5-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="e0df5-108">La longueur est stockée sous `DWORD`la forme d’un.</span><span class="sxs-lookup"><span data-stu-id="e0df5-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e0df5-109">Ce paramètre retourne la longueur de la chaîne elle-même, pas la longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="e0df5-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="e0df5-110">La longueur de la mémoire tampon n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="e0df5-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="e0df5-111">à Pointeur vers le décalage de l’emplacement, relatif au `ObjectID` pointeur, qui stocke la longueur de la chaîne elle-même.</span><span class="sxs-lookup"><span data-stu-id="e0df5-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="e0df5-112">La longueur est stockée sous `DWORD`la forme d’un.</span><span class="sxs-lookup"><span data-stu-id="e0df5-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e0df5-113">à Pointeur vers l’offset de la mémoire tampon, relatif au `ObjectID` pointeur, qui stocke la chaîne de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="e0df5-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0df5-114">Notes</span><span class="sxs-lookup"><span data-stu-id="e0df5-114">Remarks</span></span>  
 <span data-ttu-id="e0df5-115">La `GetStringLayout` méthode obtient les offsets, par rapport `ObjectID` au pointeur, des emplacements dans lesquels sont stockés les éléments suivants:</span><span class="sxs-lookup"><span data-stu-id="e0df5-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="e0df5-116">Longueur de la mémoire tampon de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e0df5-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="e0df5-117">Longueur de la chaîne elle-même.</span><span class="sxs-lookup"><span data-stu-id="e0df5-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="e0df5-118">Mémoire tampon qui contient la chaîne réelle de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="e0df5-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="e0df5-119">Les chaînes peuvent se terminer par un caractère null.</span><span class="sxs-lookup"><span data-stu-id="e0df5-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0df5-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e0df5-120">Requirements</span></span>  
 <span data-ttu-id="e0df5-121">**Plateformes** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0df5-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0df5-122">**En-tête :** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e0df5-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0df5-123">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0df5-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0df5-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0df5-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0df5-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e0df5-125">See also</span></span>

- [<span data-ttu-id="e0df5-126">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e0df5-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e0df5-127">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="e0df5-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
