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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77c88786befb92960f4cfa4a960cbfc624318b26
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771592"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="cf4c0-102">ICorDebugStringValue::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="cf4c0-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="cf4c0-103">Obtient la chaîne référencée par ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="cf4c0-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf4c0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf4c0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]   
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf4c0-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf4c0-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="cf4c0-106">[in] Taille du tableau `szString`.</span><span class="sxs-lookup"><span data-stu-id="cf4c0-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="cf4c0-107">[out] Un pointeur vers le nombre de caractères retournés dans le `szString` tableau.</span><span class="sxs-lookup"><span data-stu-id="cf4c0-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="cf4c0-108">[out] Tableau qui stocke la chaîne récupérée.</span><span class="sxs-lookup"><span data-stu-id="cf4c0-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf4c0-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="cf4c0-109">Requirements</span></span>  
 <span data-ttu-id="cf4c0-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf4c0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf4c0-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf4c0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf4c0-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf4c0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf4c0-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf4c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
