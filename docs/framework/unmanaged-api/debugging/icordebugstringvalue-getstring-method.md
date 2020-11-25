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
ms.openlocfilehash: 9051fa612bef3fbd817ff7bdadbd52c96ade5b7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697088"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="922c9-102">ICorDebugStringValue::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="922c9-102">ICorDebugStringValue::GetString Method</span></span>

<span data-ttu-id="922c9-103">Obtient la chaîne référencée par cet ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="922c9-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="922c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="922c9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="922c9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="922c9-105">Parameters</span></span>  

 `cchString`  
 <span data-ttu-id="922c9-106">[in] Taille du tableau `szString`.</span><span class="sxs-lookup"><span data-stu-id="922c9-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="922c9-107">à Pointeur vers le nombre de caractères retournés dans le `szString` tableau.</span><span class="sxs-lookup"><span data-stu-id="922c9-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="922c9-108">à Tableau qui stocke la chaîne récupérée.</span><span class="sxs-lookup"><span data-stu-id="922c9-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="922c9-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="922c9-109">Requirements</span></span>  

 <span data-ttu-id="922c9-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="922c9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="922c9-111">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="922c9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="922c9-112">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="922c9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="922c9-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="922c9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
