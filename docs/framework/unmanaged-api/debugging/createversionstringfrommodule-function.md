---
title: Fonction CreateVersionStringFromModule
ms.date: 03/30/2017
api_name:
- CreateVersionStringFromModule
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- CreateVersionStringFromModule
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
- CreateVersionStringFromModule function
ms.assetid: 3d2fe9bd-75ef-4364-84a6-da1e1994ac1a
topic_type:
- apiref
ms.openlocfilehash: 60b7d77542a5065fb1e09a98e659cac17fb093e9
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860854"
---
# <a name="createversionstringfrommodule-function"></a><span data-ttu-id="7669e-102">Fonction CreateVersionStringFromModule</span><span class="sxs-lookup"><span data-stu-id="7669e-102">CreateVersionStringFromModule Function</span></span>
<span data-ttu-id="7669e-103">Crée une chaîne de version à partir d’un chemin d’accès au Common Language Runtime (CLR) dans un processus cible.</span><span class="sxs-lookup"><span data-stu-id="7669e-103">Creates a version string from a common language runtime (CLR) path in a target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7669e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7669e-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVersionStringFromModule (  
    [in]  DWORD      pidDebuggee,  
    [in]  LPCWSTR    szModuleName,  
    [out, size_is(cchBuffer),  
          length_is(*pdwLength)] LPWSTR Buffer,  
    [in]  DWORD      cchBuffer,  
    [out] DWORD*     pdwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7669e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7669e-105">Parameters</span></span>  
 `pidDebuggee`  
 <span data-ttu-id="7669e-106">[in] Identificateur du processus dans lequel le CLR cible est chargé.</span><span class="sxs-lookup"><span data-stu-id="7669e-106">[in] Identifier of the process in which the target CLR is loaded.</span></span>  
  
 `szModuleName`  
 <span data-ttu-id="7669e-107">[in] Chemin d’accès complet ou relatif au CLR cible chargé dans le processus.</span><span class="sxs-lookup"><span data-stu-id="7669e-107">[in] Full or relative path to the target CLR that is loaded in the process.</span></span>  
  
 `pBuffer`  
 <span data-ttu-id="7669e-108">[out] Mémoire tampon de retour pour stocker la chaîne de version du CLR cible.</span><span class="sxs-lookup"><span data-stu-id="7669e-108">[out] Return buffer for storing the version string for the target CLR.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="7669e-109">[in] Taille de `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7669e-109">[in] Size of `pBuffer`.</span></span>  
  
 `pdwLength`  
 <span data-ttu-id="7669e-110">[out] Longueur de la chaîne de version retournée par `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7669e-110">[out] Length of the version string returned by `pBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7669e-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="7669e-111">Return Value</span></span>  
 <span data-ttu-id="7669e-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="7669e-112">S_OK</span></span>  
 <span data-ttu-id="7669e-113">La chaîne de version du CLR cible a été retournée dans `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7669e-113">The version string for the target CLR was successfully returned in `pBuffer`.</span></span>  
  
 <span data-ttu-id="7669e-114">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7669e-114">E_INVALIDARG</span></span>  
 <span data-ttu-id="7669e-115">`szModuleName` a la valeur null, ou `pBuffer` ou `cchBuffer` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="7669e-115">`szModuleName` is null, or either `pBuffer` or `cchBuffer` is null.</span></span> <span data-ttu-id="7669e-116">`pBuffer` et `cchBuffer` doivent tous deux être null ou non null.</span><span class="sxs-lookup"><span data-stu-id="7669e-116">`pBuffer` and `cchBuffer` must both be null or non-null.</span></span>  
  
 <span data-ttu-id="7669e-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span><span class="sxs-lookup"><span data-stu-id="7669e-117">HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)</span></span>  
 <span data-ttu-id="7669e-118">`pdwLength` est supérieur à `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7669e-118">`pdwLength` is greater than `cchBuffer`.</span></span> <span data-ttu-id="7669e-119">Il peut s'agir d'un résultat attendu si vous avez passé null pour `pBuffer` et `cchBuffer`, et interrogé la taille de la mémoire tampon nécessaire à l'aide de `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="7669e-119">This may be an expected result if you have passed null for both `pBuffer` and `cchBuffer`, and queried the necessary buffer size by using `pdwLength`.</span></span>  
  
 <span data-ttu-id="7669e-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span><span class="sxs-lookup"><span data-stu-id="7669e-120">HRESULT_FROM_WIN32(ERROR_MOD_NOT_FOUND)</span></span>  
 <span data-ttu-id="7669e-121">`szModuleName` ne contient pas un chemin d'accès à un CLR valide dans le processus cible.</span><span class="sxs-lookup"><span data-stu-id="7669e-121">`szModuleName` does not contain a path to a valid CLR in the target process.</span></span>  
  
 <span data-ttu-id="7669e-122">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="7669e-122">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7669e-123">`pidDebuggee` ne fait pas référence à un processus valide ou à tout autre échec.</span><span class="sxs-lookup"><span data-stu-id="7669e-123">`pidDebuggee` does not refer to a valid process, or other failure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7669e-124">Notes </span><span class="sxs-lookup"><span data-stu-id="7669e-124">Remarks</span></span>  
 <span data-ttu-id="7669e-125">Cette fonction accepte un processus CLR identifié par `pidDebuggee` et un chemin d'accès de chaîne spécifié par `szModuleName`.</span><span class="sxs-lookup"><span data-stu-id="7669e-125">This function accepts a CLR process that is identified by `pidDebuggee` and a string path that is specified by `szModuleName`.</span></span> <span data-ttu-id="7669e-126">La chaîne de version est retournée dans la mémoire tampon vers laquelle pointe `pBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7669e-126">The version string is returned in the buffer that `pBuffer` points to.</span></span> <span data-ttu-id="7669e-127">Cette chaîne est opaque à l'utilisateur de la fonction ; autrement dit, il n'y a aucune signification intrinsèque dans la chaîne de version elle-même.</span><span class="sxs-lookup"><span data-stu-id="7669e-127">This string is opaque to the function user; that is, there is no intrinsic meaning in the version string itself.</span></span> <span data-ttu-id="7669e-128">Elle est utilisée uniquement dans le contexte de cette fonction et de la [fonction CreateDebuggingInterfaceFromVersion](createdebugginginterfacefromversion-function-for-silverlight.md).</span><span class="sxs-lookup"><span data-stu-id="7669e-128">It is used solely in the context of this function and the [CreateDebuggingInterfaceFromVersion function](createdebugginginterfacefromversion-function-for-silverlight.md).</span></span>  
  
 <span data-ttu-id="7669e-129">Cette fonction doit être appelée deux fois.</span><span class="sxs-lookup"><span data-stu-id="7669e-129">This function should be called twice.</span></span> <span data-ttu-id="7669e-130">Quand vous appelez pour la première fois, passez la valeur null pour `pBuffer` et `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7669e-130">When you call it the first time, pass null for both `pBuffer` and `cchBuffer`.</span></span> <span data-ttu-id="7669e-131">Quand vous procédez ainsi, la taille de la mémoire tampon nécessaire pour `pBuffer` est retournée dans `pdwLength`.</span><span class="sxs-lookup"><span data-stu-id="7669e-131">When you do this, the size of the buffer necessary for `pBuffer` will be returned in `pdwLength`.</span></span> <span data-ttu-id="7669e-132">Vous pouvez ensuite appeler la fonction une seconde fois et passer la mémoire tampon dans `pBuffer` et sa taille dans `cchBuffer`.</span><span class="sxs-lookup"><span data-stu-id="7669e-132">You can then call the function a second time, and pass the buffer in `pBuffer` and its size in `cchBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7669e-133">Spécifications</span><span class="sxs-lookup"><span data-stu-id="7669e-133">Requirements</span></span>  
 <span data-ttu-id="7669e-134">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7669e-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7669e-135">**En-tête :** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="7669e-135">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="7669e-136">**Bibliothèque :** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="7669e-136">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="7669e-137">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="7669e-137">**.NET Framework Versions:** 3.5 SP1</span></span>
