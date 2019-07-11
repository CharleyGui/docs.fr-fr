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
ms.openlocfilehash: 4d4efa7cb3bc98c54be2889855c3b756fdbf2847
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782243"
---
# <a name="icorprofilerinfo2getstringlayout-method"></a><span data-ttu-id="e1578-102">ICorProfilerInfo2::GetStringLayout, méthode</span><span class="sxs-lookup"><span data-stu-id="e1578-102">ICorProfilerInfo2::GetStringLayout Method</span></span>
<span data-ttu-id="e1578-103">Obtient des informations sur la disposition d'un objet string.</span><span class="sxs-lookup"><span data-stu-id="e1578-103">Gets information about the layout of a string object.</span></span> <span data-ttu-id="e1578-104">Cette méthode est déconseillée dans le .NET Framework 4 et est remplacée par la [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) (méthode).</span><span class="sxs-lookup"><span data-stu-id="e1578-104">This method is deprecated in the .NET Framework 4, and is superseded by the [ICorProfilerInfo3::GetStringLayout2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1578-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1578-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStringLayout(  
    [out] ULONG *pBufferLengthOffset,  
    [out] ULONG *pStringLengthOffset,  
    [out] ULONG *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1578-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e1578-106">Parameters</span></span>  
 `pBufferLengthOffset`  
 <span data-ttu-id="e1578-107">[out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e1578-107">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string.</span></span> <span data-ttu-id="e1578-108">La longueur est stockée comme un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e1578-108">The length is stored as a `DWORD`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1578-109">Ce paramètre retourne la longueur de la chaîne elle-même, pas la longueur de la mémoire tampon.</span><span class="sxs-lookup"><span data-stu-id="e1578-109">This parameter returns the length of the string itself, not the length of the buffer.</span></span> <span data-ttu-id="e1578-110">La longueur de la mémoire tampon n’est plus disponible.</span><span class="sxs-lookup"><span data-stu-id="e1578-110">The length of the buffer is no longer available.</span></span>  
  
 `PStringLengthOffset`  
 <span data-ttu-id="e1578-111">[out] Un pointeur vers l’offset de l’emplacement, relatif à la `ObjectID` pointeur, qui stocke la longueur de la chaîne elle-même.</span><span class="sxs-lookup"><span data-stu-id="e1578-111">[out] A pointer to the offset of the location, relative to the `ObjectID` pointer, that stores the length of the string itself.</span></span> <span data-ttu-id="e1578-112">La longueur est stockée comme un `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="e1578-112">The length is stored as a `DWORD`.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="e1578-113">[out] Un pointeur vers l’offset de la mémoire tampon, relative à la `ObjectID` pointeur, qui stocke la chaîne de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="e1578-113">[out] A pointer to the offset of the buffer, relative to the `ObjectID` pointer, that stores the string of wide characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1578-114">Notes</span><span class="sxs-lookup"><span data-stu-id="e1578-114">Remarks</span></span>  
 <span data-ttu-id="e1578-115">Le `GetStringLayout` méthode obtient les offsets, relatif à la `ObjectID` pointeur, des emplacements dans lesquels sont stockés les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="e1578-115">The `GetStringLayout` method gets the offsets, relative to the `ObjectID` pointer, of the locations in which the following are stored:</span></span>  
  
- <span data-ttu-id="e1578-116">La longueur de la mémoire tampon de la chaîne.</span><span class="sxs-lookup"><span data-stu-id="e1578-116">The length of the string's buffer.</span></span>  
  
- <span data-ttu-id="e1578-117">La longueur de la chaîne elle-même.</span><span class="sxs-lookup"><span data-stu-id="e1578-117">The length of the string itself.</span></span>  
  
- <span data-ttu-id="e1578-118">La mémoire tampon qui contient la chaîne réelle de caractères larges.</span><span class="sxs-lookup"><span data-stu-id="e1578-118">The buffer that contains the actual string of wide characters.</span></span>  
  
 <span data-ttu-id="e1578-119">Chaînes peuvent être se terminant par null.</span><span class="sxs-lookup"><span data-stu-id="e1578-119">Strings may be null-terminated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1578-120">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="e1578-120">Requirements</span></span>  
 <span data-ttu-id="e1578-121">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1578-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1578-122">**En-tête :** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1578-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1578-123">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1578-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1578-124">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1578-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1578-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1578-125">See also</span></span>

- [<span data-ttu-id="e1578-126">ICorProfilerInfo, interface</span><span class="sxs-lookup"><span data-stu-id="e1578-126">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="e1578-127">ICorProfilerInfo2, interface</span><span class="sxs-lookup"><span data-stu-id="e1578-127">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
