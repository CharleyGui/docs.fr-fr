---
title: ICorDebugStringValue::GetString, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: e23133176cbd703a58c92f9bf1ead530b0bbb8a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178496"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="9b874-102">ICorDebugStringValue::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="9b874-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="9b874-103">Obtient la chaîne référencée par cette ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="9b874-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b874-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b874-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b874-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9b874-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="9b874-106">[in] Taille du tableau `szString`.</span><span class="sxs-lookup"><span data-stu-id="9b874-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="9b874-107">[out] Un pointeur sur le nombre `szString` de caractères retournés dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="9b874-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="9b874-108">[out] Un tableau qui stocke la ficelle récupérée.</span><span class="sxs-lookup"><span data-stu-id="9b874-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b874-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9b874-109">Requirements</span></span>  
 <span data-ttu-id="9b874-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b874-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b874-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b874-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b874-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b874-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b874-113">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b874-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
