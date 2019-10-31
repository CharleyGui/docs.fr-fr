---
title: Fonction CloseCLREnumeration
ms.date: 03/30/2017
api_name:
- CloseCLREnumeration
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CloseCLREnumeration
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CloseCLR Enumeration function
ms.assetid: 5e3c3958-80bb-43b1-a96b-dd3e6dbd9cd7
topic_type:
- apiref
ms.openlocfilehash: 1d42292705dae03e9bf1a1555508dfb69cebde82
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132436"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="e6d88-102">Fonction CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="e6d88-102">CloseCLREnumeration Function</span></span>
<span data-ttu-id="e6d88-103">Ferme tous les événements de continuation de common language runtime (CLR) valides situés dans un tableau de handles retournés par la [fonction EnumerateCLRs](enumerateclrs-function.md)et libère la mémoire pour les tableaux de handles et de chemins d’accès aux chaînes.</span><span class="sxs-lookup"><span data-stu-id="e6d88-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6d88-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6d88-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e6d88-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e6d88-105">Parameters</span></span>  
 `pHandleArray`  
 <span data-ttu-id="e6d88-106">dans Pointeur vers le tableau de handles d’événement retourné par la [fonction EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="e6d88-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="e6d88-107">dans Pointeur vers le tableau de chemins d’accès aux chaînes CLR retourné par la [fonction EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="e6d88-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="e6d88-108">[in] Valeur DWORD contenant la taille (longueur) de `pHandleArray` ou de `pStringArray` (ils sont identiques).</span><span class="sxs-lookup"><span data-stu-id="e6d88-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e6d88-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e6d88-109">Return Value</span></span>  
 <span data-ttu-id="e6d88-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e6d88-110">S_OK</span></span>  
 <span data-ttu-id="e6d88-111">Les handles ouverts par la [fonction EnumerateCLRs](enumerateclrs-function.md) sont fermés, et la mémoire allouée pour le handle et les tableaux de chaînes est libérée.</span><span class="sxs-lookup"><span data-stu-id="e6d88-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="e6d88-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="e6d88-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="e6d88-113">La longueur de `pHandleArray` ne correspond pas à la longueur passée dans `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="e6d88-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="e6d88-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="e6d88-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="e6d88-115">La fonction ne peut pas libérer la mémoire pour `pHandleArray` et `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="e6d88-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6d88-116">spécifications</span><span class="sxs-lookup"><span data-stu-id="e6d88-116">Requirements</span></span>  
 <span data-ttu-id="e6d88-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6d88-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6d88-118">**En-tête :** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="e6d88-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="e6d88-119">**Bibliothèque :** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="e6d88-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="e6d88-120">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e6d88-120">**.NET Framework Versions:** 3.5 SP1</span></span>
