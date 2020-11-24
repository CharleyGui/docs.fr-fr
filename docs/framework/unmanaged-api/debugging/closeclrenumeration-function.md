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
ms.openlocfilehash: 575e194cf952f02a3fe4fce9e955e45e1bc3653d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673911"
---
# <a name="closeclrenumeration-function"></a><span data-ttu-id="6b93c-102">Fonction CloseCLREnumeration</span><span class="sxs-lookup"><span data-stu-id="6b93c-102">CloseCLREnumeration Function</span></span>

<span data-ttu-id="6b93c-103">Ferme tous les événements de continuation de common language runtime (CLR) valides situés dans un tableau de handles retournés par la [fonction EnumerateCLRs](enumerateclrs-function.md)et libère la mémoire pour les tableaux de handles et de chemins d’accès aux chaînes.</span><span class="sxs-lookup"><span data-stu-id="6b93c-103">Closes any valid common language runtime (CLR) continue-startup events located in an array of handles returned by the [EnumerateCLRs function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b93c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b93c-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseCLREnumeration (  
    [in]  DWORD      pHandleArray,  
    [in]  LPWSTR**   pStringArray,  
    [in]  DWORD*     dwArrayLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b93c-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6b93c-105">Parameters</span></span>  

 `pHandleArray`  
 <span data-ttu-id="6b93c-106">dans Pointeur vers le tableau de handles d’événement retourné par la [fonction EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="6b93c-106">[in] Pointer to the array of event handles returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `pStringArray`  
 <span data-ttu-id="6b93c-107">dans Pointeur vers le tableau de chemins d’accès aux chaînes CLR retourné par la [fonction EnumerateCLRs](enumerateclrs-function.md).</span><span class="sxs-lookup"><span data-stu-id="6b93c-107">[in] Pointer to the array of CLR string paths returned from the [EnumerateCLRs function](enumerateclrs-function.md).</span></span>  
  
 `dwArrayLength`  
 <span data-ttu-id="6b93c-108">[in] Valeur DWORD contenant la taille (longueur) de `pHandleArray` ou de `pStringArray` (ils sont identiques).</span><span class="sxs-lookup"><span data-stu-id="6b93c-108">[in] DWORD that contains the size (length) of either `pHandleArray` or `pStringArray` (they are the same).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6b93c-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="6b93c-109">Return Value</span></span>  

 <span data-ttu-id="6b93c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6b93c-110">S_OK</span></span>  
 <span data-ttu-id="6b93c-111">Les handles ouverts par la [fonction EnumerateCLRs](enumerateclrs-function.md) sont fermés, et la mémoire allouée pour le handle et les tableaux de chaînes est libérée.</span><span class="sxs-lookup"><span data-stu-id="6b93c-111">Handles opened by the [EnumerateCLRs function](enumerateclrs-function.md) are closed, and memory allocated for the handle and string arrays is freed.</span></span>  
  
 <span data-ttu-id="6b93c-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="6b93c-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="6b93c-113">La longueur de `pHandleArray` ne correspond pas à la longueur passée dans `dwArrayLength`.</span><span class="sxs-lookup"><span data-stu-id="6b93c-113">The length of `pHandleArray` does not match the length that is passed in `dwArrayLength`.</span></span>  
  
 <span data-ttu-id="6b93c-114">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="6b93c-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="6b93c-115">La fonction ne peut pas libérer la mémoire pour `pHandleArray` et `pStringArray`.</span><span class="sxs-lookup"><span data-stu-id="6b93c-115">The function is unable to free the memory for `pHandleArray` and `pStringArray`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b93c-116">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6b93c-116">Requirements</span></span>  

 <span data-ttu-id="6b93c-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b93c-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b93c-118">**En-tête :** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="6b93c-118">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="6b93c-119">**Bibliothèque :** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="6b93c-119">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="6b93c-120">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="6b93c-120">**.NET Framework Versions:** 3.5 SP1</span></span>
