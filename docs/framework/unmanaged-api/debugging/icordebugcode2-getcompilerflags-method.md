---
title: ICorDebugCode2::GetCompilerFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ebed8ea1d4943007f8f18b0baa1c676a78207c2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395506"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="83fd9-102">ICorDebugCode2::GetCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="83fd9-102">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="83fd9-103">Obtient les indicateurs qui spécifient les conditions sous lesquelles cet objet de code a été compilé juste-à-temps (JIT) ou généré à l’aide du générateur d’images natives (Ngen. exe).</span><span class="sxs-lookup"><span data-stu-id="83fd9-103">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="83fd9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83fd9-104">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="83fd9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="83fd9-105">Parameters</span></span>

`pdwFlags`  
<span data-ttu-id="83fd9-106">à Pointeur vers une valeur de l’énumération [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) qui spécifie le comportement du compilateur JIT ou du générateur d’images natives.</span><span class="sxs-lookup"><span data-stu-id="83fd9-106">[out] A pointer to a value of the [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="83fd9-107">spécifications</span><span class="sxs-lookup"><span data-stu-id="83fd9-107">Requirements</span></span>

<span data-ttu-id="83fd9-108">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83fd9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="83fd9-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="83fd9-109">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="83fd9-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83fd9-110">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="83fd9-111">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83fd9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
