---
title: ICorDebugThread2::GetActiveFunctions, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetActiveFunctions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetActiveFunctions
helpviewer_keywords:
- GetActiveFunctions method [.NET Framework debugging]
- ICorDebugThread2::GetActiveFunctions method [.NET Framework debugging]
ms.assetid: 27fae01a-ecec-423a-973e-24f8de55826c
topic_type:
- apiref
ms.openlocfilehash: e064a7db131a671adc4d0b6df522f3456e3a31d5
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377150"
---
# <a name="icordebugthread2getactivefunctions-method"></a><span data-ttu-id="53873-102">ICorDebugThread2::GetActiveFunctions, méthode</span><span class="sxs-lookup"><span data-stu-id="53873-102">ICorDebugThread2::GetActiveFunctions Method</span></span>
<span data-ttu-id="53873-103">Obtient des informations sur la fonction active dans chacun des frames de ce thread.</span><span class="sxs-lookup"><span data-stu-id="53873-103">Gets information about the active function in each of this thread's frames.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53873-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53873-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFunctions (  
    [in]   ULONG32             cFunctions,  
    [out]  ULONG32             *pcFunctions,  
    [in, out, size_is(cFunctions), length_is(*pcFunctions)]  
        COR_ACTIVE_FUNCTION    pFunctions[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53873-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="53873-105">Parameters</span></span>  
 `cFunctions`  
 <span data-ttu-id="53873-106">[in] Taille du tableau `pFunctions`.</span><span class="sxs-lookup"><span data-stu-id="53873-106">[in] The size of the `pFunctions` array.</span></span>  
  
 `pcFunctions`  
 <span data-ttu-id="53873-107">à Pointeur vers le nombre d’objets retournés dans le `pFunctions` tableau.</span><span class="sxs-lookup"><span data-stu-id="53873-107">[out] A pointer to the number of objects returned in the `pFunctions` array.</span></span> <span data-ttu-id="53873-108">Le nombre d’objets retournés sera égal au nombre de frames managés sur la pile.</span><span class="sxs-lookup"><span data-stu-id="53873-108">The number of objects returned will be equal to the number of managed frames on the stack.</span></span>  
  
 `pFunctions`  
 <span data-ttu-id="53873-109">[in, out] Tableau d’objets COR_ACTIVE_FUNCTION, chacun contenant des informations sur les fonctions actives dans les frames de ce thread.</span><span class="sxs-lookup"><span data-stu-id="53873-109">[in, out] An array of COR_ACTIVE_FUNCTION objects, each of which contains information about the active functions in this thread's frames.</span></span>  
  
 <span data-ttu-id="53873-110">Le premier élément sera utilisé pour le frame de feuille, et ainsi de suite jusqu’à la racine de la pile.</span><span class="sxs-lookup"><span data-stu-id="53873-110">The first element will be used for the leaf frame, and so on back to the root of the stack.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53873-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="53873-111">Remarks</span></span>  
 <span data-ttu-id="53873-112">Si `pFunctions` a la valeur null en entrée, `GetActiveFunctions` retourne uniquement le nombre de fonctions qui se trouvent sur la pile.</span><span class="sxs-lookup"><span data-stu-id="53873-112">If `pFunctions` is null on input, `GetActiveFunctions` returns only the number of functions that are on the stack.</span></span> <span data-ttu-id="53873-113">Autrement dit, si `pFunctions` a la valeur null en entrée, `GetActiveFunctions` retourne une valeur uniquement dans `pcFunctions` .</span><span class="sxs-lookup"><span data-stu-id="53873-113">That is, If `pFunctions` is null on input, `GetActiveFunctions` returns a value only in `pcFunctions`.</span></span>  
  
 <span data-ttu-id="53873-114">La `GetActiveFunctions` méthode est conçue comme une optimisation pour obtenir les mêmes informations à partir de frames dans une trace de la pile, et comprend uniquement les frames qui auraient eu un objet ICorDebugILFrame pour eux dans la trace de la pile complète.</span><span class="sxs-lookup"><span data-stu-id="53873-114">The `GetActiveFunctions` method is intended as an optimization over getting the same information from frames in a stack trace, and includes only frames that would have had an ICorDebugILFrame object for them in the full stack trace.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53873-115">Spécifications</span><span class="sxs-lookup"><span data-stu-id="53873-115">Requirements</span></span>  
 <span data-ttu-id="53873-116">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53873-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53873-117">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53873-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53873-118">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53873-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53873-119">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53873-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
