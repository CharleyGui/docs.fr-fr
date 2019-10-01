---
title: ICorDebugCode2::GetCodeChunks, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCodeChunks
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCodeChunks
helpviewer_keywords:
- GetCodeChunks method [.NET Framework debugging]
- ICorDebugCode2::GetCodeChunks method [.NET Framework debugging]
ms.assetid: 210a2f02-2678-4555-bc4a-78a0408764c8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bdaf6391ca5c19f073708d6258ad5775bec9824
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700729"
---
# <a name="icordebugcode2getcodechunks-method"></a><span data-ttu-id="3a5ab-102">ICorDebugCode2::GetCodeChunks, méthode</span><span class="sxs-lookup"><span data-stu-id="3a5ab-102">ICorDebugCode2::GetCodeChunks Method</span></span>

<span data-ttu-id="3a5ab-103">Obtient les blocs de code composés de cet objet de code.</span><span class="sxs-lookup"><span data-stu-id="3a5ab-103">Gets the chunks of code that this code object is composed of.</span></span>

## <a name="syntax"></a><span data-ttu-id="3a5ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a5ab-104">Syntax</span></span>

```cpp
HRESULT GetCodeChunks (
    [in]  ULONG32     cbufSize,
    [out] ULONG32     *pcnumChunks,
    [out, size_is(cbufSize), length_is(*pcnumChunks)]
        CodeChunkInfo chunks[]
);
```

## <a name="parameters"></a><span data-ttu-id="3a5ab-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3a5ab-105">Parameters</span></span>

 `cbufSize`  
 <span data-ttu-id="3a5ab-106">dans Taille du tableau `chunks`.</span><span class="sxs-lookup"><span data-stu-id="3a5ab-106">[in] Size of the `chunks` array.</span></span>

 `pcnumChunks`  
 <span data-ttu-id="3a5ab-107">à Nombre de segments retournés dans le tableau `chunks`.</span><span class="sxs-lookup"><span data-stu-id="3a5ab-107">[out] The number of chunks returned in the `chunks` array.</span></span>

 `chunks`  
 <span data-ttu-id="3a5ab-108">à Tableau de structures « CodeChunkInfo », chacune représentant un segment de code unique.</span><span class="sxs-lookup"><span data-stu-id="3a5ab-108">[out] An array of "CodeChunkInfo" structures, each of which represents a single chunk of code.</span></span> <span data-ttu-id="3a5ab-109">Si la valeur de `cbufSize` est égale à 0, ce paramètre peut avoir la valeur null.</span><span class="sxs-lookup"><span data-stu-id="3a5ab-109">If the value of `cbufSize` is 0, this parameter can be null.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a5ab-110">Notes</span><span class="sxs-lookup"><span data-stu-id="3a5ab-110">Remarks</span></span>

 <span data-ttu-id="3a5ab-111">Les segments de code ne se chevauchent jamais et suivent l’ordre dans lequel ils ont été concaténés par [ICorDebugCode :: GetCode](icordebugcode-getcode-method.md).</span><span class="sxs-lookup"><span data-stu-id="3a5ab-111">The code chunks will never overlap, and they will follow the order in which they would have been concatenated by [ICorDebugCode::GetCode](icordebugcode-getcode-method.md).</span></span> <span data-ttu-id="3a5ab-112">Un objet de code MSIL (Microsoft Intermediate Language) dans le .NET Framework version 2,0 comprendra un seul segment de code.</span><span class="sxs-lookup"><span data-stu-id="3a5ab-112">A Microsoft intermediate language (MSIL) code object in the .NET Framework version 2.0 will comprise a single code chunk.</span></span>

## <a name="requirements"></a><span data-ttu-id="3a5ab-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3a5ab-113">Requirements</span></span>

 <span data-ttu-id="3a5ab-114">**Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a5ab-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="3a5ab-115">**En-tête :** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a5ab-115">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="3a5ab-116">**Bibliothèque** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a5ab-116">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="3a5ab-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a5ab-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
 
