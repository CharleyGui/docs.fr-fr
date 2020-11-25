---
title: ICorDebugStringValue::GetLength, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
ms.openlocfilehash: 74a4b42be09c577cc80f1a73e077694e5a4a8d5f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697114"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="a0e91-102">ICorDebugStringValue::GetLength, méthode</span><span class="sxs-lookup"><span data-stu-id="a0e91-102">ICorDebugStringValue::GetLength Method</span></span>

<span data-ttu-id="a0e91-103">Obtient le nombre de caractères de la chaîne référencés par cet ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="a0e91-103">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0e91-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a0e91-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0e91-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a0e91-105">Parameters</span></span>  

 `pcchString`  
 <span data-ttu-id="a0e91-106">à Pointeur vers une valeur qui spécifie la longueur de la chaîne référencée par cet `ICorDebugStringValue` objet.</span><span class="sxs-lookup"><span data-stu-id="a0e91-106">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0e91-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a0e91-107">Requirements</span></span>  

 <span data-ttu-id="a0e91-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0e91-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0e91-109">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0e91-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0e91-110">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0e91-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0e91-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0e91-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
