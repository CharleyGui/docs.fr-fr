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
ms.openlocfilehash: 9c154d4ad561e0bd9d82adaca77d2e30f11a5237
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379665"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="cf887-102">ICorDebugStringValue::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="cf887-102">ICorDebugStringValue::GetString Method</span></span>
<span data-ttu-id="cf887-103">Obtient la chaîne référencée par cet ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="cf887-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf887-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf887-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf887-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="cf887-105">Parameters</span></span>  
 `cchString`  
 <span data-ttu-id="cf887-106">[in] Taille du tableau `szString`.</span><span class="sxs-lookup"><span data-stu-id="cf887-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="cf887-107">à Pointeur vers le nombre de caractères retournés dans le `szString` tableau.</span><span class="sxs-lookup"><span data-stu-id="cf887-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="cf887-108">à Tableau qui stocke la chaîne récupérée.</span><span class="sxs-lookup"><span data-stu-id="cf887-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf887-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="cf887-109">Requirements</span></span>  
 <span data-ttu-id="cf887-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf887-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf887-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf887-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf887-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf887-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf887-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf887-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
