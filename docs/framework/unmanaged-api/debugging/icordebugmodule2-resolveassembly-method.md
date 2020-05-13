---
title: ICorDebugModule2::ResolveAssembly, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: e64e39d10d20f63430ffe9d2c4df8643e286a677
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210027"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="78c59-102">ICorDebugModule2::ResolveAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="78c59-102">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="78c59-103">Résout l’assembly référencé par le jeton de métadonnées spécifié.</span><span class="sxs-lookup"><span data-stu-id="78c59-103">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="78c59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="78c59-104">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="78c59-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="78c59-105">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="78c59-106">dans `mdToken`Valeur qui référence l’assembly.</span><span class="sxs-lookup"><span data-stu-id="78c59-106">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="78c59-107">à Pointeur vers l’adresse d’un objet ICorDebugAssembly qui représente l’assembly.</span><span class="sxs-lookup"><span data-stu-id="78c59-107">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="78c59-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="78c59-108">Remarks</span></span>

<span data-ttu-id="78c59-109">Si l’assembly n’est pas déjà chargé lorsque `ResolveAssembly` est appelé, une valeur HRESULT de CORDBG_E_CANNOT_RESOLVE_ASSEMBLY est retournée.</span><span class="sxs-lookup"><span data-stu-id="78c59-109">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="78c59-110">Spécifications</span><span class="sxs-lookup"><span data-stu-id="78c59-110">Requirements</span></span>

<span data-ttu-id="78c59-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78c59-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="78c59-112">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78c59-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="78c59-113">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78c59-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="78c59-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78c59-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
