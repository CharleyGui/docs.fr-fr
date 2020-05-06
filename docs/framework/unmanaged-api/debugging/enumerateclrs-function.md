---
title: Fonction EnumerateCLRs
ms.date: 03/30/2017
api_name:
- EnumerateCLRs
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- EnumerateCLRs
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- EnumerateCLRs function
ms.assetid: f8d50cb3-ec4f-4529-8fe3-bd61fd28e13c
topic_type:
- apiref
ms.openlocfilehash: 1f33fb98712939d1e687798547b784819f164d63
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860723"
---
# <a name="enumerateclrs-function"></a><span data-ttu-id="a2f3a-102">Fonction EnumerateCLRs</span><span class="sxs-lookup"><span data-stu-id="a2f3a-102">EnumerateCLRs Function</span></span>
<span data-ttu-id="a2f3a-103">Fournit un mécanisme pour énumérer les CLR dans un processus.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-103">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2f3a-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateCLRs (  
    [in]  DWORD      debuggeePID,  
    [out] HANDLE**   ppHandleArrayOut,  
    [out] LPWSTR**   ppStringArrayOut,  
    [out] DWORD*     pdwArrayLengthOut  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2f3a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2f3a-105">Parameters</span></span>  
 `debuggeePID`  
 <span data-ttu-id="a2f3a-106">[in] Identificateur du processus à partir duquel les CLR chargés sont énumérés.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-106">[in] Process identifier of the process from which loaded CLRs will be enumerated.</span></span>  
  
 `ppHandleArrayOut`  
 <span data-ttu-id="a2f3a-107">[out] Pointeur vers un tableau contenant les handles d'événements utilisés pour poursuivre un démarrage du CLR.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-107">[out] Pointer to an array containing event handles that are used to continue a CLR startup.</span></span> <span data-ttu-id="a2f3a-108">Chaque handle du tableau n'est pas garanti comme valide.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-108">Each handle in the array is not guaranteed to be valid.</span></span> <span data-ttu-id="a2f3a-109">Si valide, le handle doit être utilisé comme l'événement continue-startup du runtime correspondant situé dans le même index de `ppStringArrayOut`.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-109">If valid, the handle is to be used as the continue-startup event for the corresponding runtime located in the same index of `ppStringArrayOut`.</span></span>  
  
 `ppStringArrayOut`  
 <span data-ttu-id="a2f3a-110">[out] Pointeur vers un tableau de chaînes qui spécifient des chemins d'accès complets aux CLR chargés dans le processus.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-110">[out] Pointer to an array of strings that specify full paths to CLRs loaded in the process.</span></span>  
  
 `pdwArrayLengthOut`  
 <span data-ttu-id="a2f3a-111">[out] Pointeur vers une valeur DWORD qui contient la longueur de `ppHandleArrayOut` et `pdwArrayLengthOut` de taille égale.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-111">[out] Pointer to a DWORD that contains the length of the equally sized `ppHandleArrayOut` and `pdwArrayLengthOut`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2f3a-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a2f3a-112">Return Value</span></span>  
 <span data-ttu-id="a2f3a-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="a2f3a-113">S_OK</span></span>  
 <span data-ttu-id="a2f3a-114">Le nombre de CLR dans le processus a été correctement déterminé, et les tableaux de handles et de chemin d’accès correspondants ont été correctement remplis.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-114">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="a2f3a-115">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a2f3a-115">E_INVALIDARG</span></span>  
 <span data-ttu-id="a2f3a-116">`ppHandleArrayOut` a la valeur null, ou `ppStringArrayOut` ou `pdwArrayLengthOut` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-116">Either `ppHandleArrayOut` or `ppStringArrayOut` is null, or `pdwArrayLengthOut` is null.</span></span>  
  
 <span data-ttu-id="a2f3a-117">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="a2f3a-117">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="a2f3a-118">La fonction ne peut pas allouer suffisamment de mémoire pour les tableaux de handles et de chemins d'accès.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-118">The function is unable to allocate enough memory for the handle and path arrays.</span></span>  
  
 <span data-ttu-id="a2f3a-119">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="a2f3a-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a2f3a-120">Impossible d'énumérer les CLR chargés.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-120">Unable to enumerate loaded CLRs.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2f3a-121">Notes </span><span class="sxs-lookup"><span data-stu-id="a2f3a-121">Remarks</span></span>  
 <span data-ttu-id="a2f3a-122">Pour un processus cible qui est identifié par `debuggeePID`, la fonction retourne un tableau de chemins d’accès, `ppStringArrayOut`, vers les CLR chargés dans le processus ; un tableau de handles d’événement, `ppHandleArrayOut`, qui peut contenir un événement continue-startup pour le CLR au même index ; et la taille des tableaux, `pdwArrayLengthOut`, qui spécifie le nombre de CLR chargés.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-122">For a target process that is identified by `debuggeePID`, the function returns an array of paths, `ppStringArrayOut`, to CLRs loaded in the process; an array of event handles, `ppHandleArrayOut`, which may contain a continue-startup event for the CLR at the same index; and the size of the arrays, `pdwArrayLengthOut`, which specifies the number of CLRs that are loaded.</span></span>  
  
 <span data-ttu-id="a2f3a-123">Sur le système d'exploitation Windows, `debuggeePID` est mappé à un identificateur de processus du système d'exploitation.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-123">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="a2f3a-124">La mémoire pour `ppHandleArrayOut` et `ppStringArrayOut` est allouée par cette fonction.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-124">The memory for `ppHandleArrayOut` and `ppStringArrayOut` are allocated by this function.</span></span> <span data-ttu-id="a2f3a-125">Pour libérer la mémoire allouée, vous devez appeler la [fonction CloseCLREnumeration](closeclrenumeration-function.md).</span><span class="sxs-lookup"><span data-stu-id="a2f3a-125">To free the memory allocated, you must call [CloseCLREnumeration Function](closeclrenumeration-function.md).</span></span>  
  
 <span data-ttu-id="a2f3a-126">Cette fonction peut être appelée en affectant la valeur null aux deux paramètres de tableau afin de retourner le nombre de CLR dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-126">This function can be called with both array parameters set to null in order to return the count of CLRs in the target process.</span></span> <span data-ttu-id="a2f3a-127">Avec ce nombre, un appelant peut déduire la taille de la mémoire tampon qui sera créée : `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span><span class="sxs-lookup"><span data-stu-id="a2f3a-127">From this count, a caller can infer the size of the buffer that will be created: `(sizeof(HANDLE) * count) + (sizeof(LPWSTR) * count) + (sizeof(WCHAR*) * count * MAX_PATH)`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f3a-128">Spécifications</span><span class="sxs-lookup"><span data-stu-id="a2f3a-128">Requirements</span></span>  
 <span data-ttu-id="a2f3a-129">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2f3a-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2f3a-130">**En-tête :** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="a2f3a-130">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="a2f3a-131">**Bibliothèque :** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="a2f3a-131">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="a2f3a-132">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="a2f3a-132">**.NET Framework Versions:** 3.5 SP1</span></span>
