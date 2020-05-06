---
title: Fonction CreateDebuggingInterfaceFromVersion Function pour Silverlight
ms.date: 03/30/2017
f1_keywords:
- CreateDebuggingInterfaceFromVersion
helpviewer_keywords:
- CreateDebuggingInterfaceFromVersion function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 35c7a18f-133a-4584-bd25-bb338568b0c6
ms.openlocfilehash: c83bdcca4fab75b4ae94500ceb785b6000cd802a
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860869"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="93c26-102">Fonction CreateDebuggingInterfaceFromVersion Function pour Silverlight</span><span class="sxs-lookup"><span data-stu-id="93c26-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>
<span data-ttu-id="93c26-103">Accepte une chaîne de version common language runtime (CLR) retournée par la [fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md)et retourne une interface de débogueur correspondante (en général, [ICorDebug](icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="93c26-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93c26-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93c26-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93c26-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="93c26-105">Parameters</span></span>  
 `szDebuggeeVersion`  
 <span data-ttu-id="93c26-106">dans Chaîne de version du CLR dans le programme débogué cible, qui est retournée par la [fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="93c26-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="93c26-107">[out] Pointeur vers un autre pointeur vers un objet COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="93c26-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="93c26-108">Cet objet est casté en objet [ICorDebug](icordebug-interface.md) avant d’être retourné.</span><span class="sxs-lookup"><span data-stu-id="93c26-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93c26-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="93c26-109">Return Value</span></span>  
 <span data-ttu-id="93c26-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="93c26-110">S_OK</span></span>  
 <span data-ttu-id="93c26-111">`ppCordb`fait référence à un objet valide qui implémente l’interface d' [interface ICorDebug](icordebug-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="93c26-111">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 <span data-ttu-id="93c26-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="93c26-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="93c26-113">`szDebuggeeVersion` ou `ppCordb` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="93c26-113">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 <span data-ttu-id="93c26-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span><span class="sxs-lookup"><span data-stu-id="93c26-114">CORDBG_E_DEBUG_COMPONENT_MISSING</span></span>  
 <span data-ttu-id="93c26-115">Un composant nécessaire pour le débogage CLR est introuvable.</span><span class="sxs-lookup"><span data-stu-id="93c26-115">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="93c26-116">Cela signifie que mscordbi.dll ou mscordaccore.dll est introuvable dans le répertoire dans lequel figure le fichier CoreCLR.dll cible.</span><span class="sxs-lookup"><span data-stu-id="93c26-116">This means that either mscordbi.dll or mscordaccore.dll was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="93c26-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span><span class="sxs-lookup"><span data-stu-id="93c26-117">CORDBG_E_INCOMPATIBLE_PROTOCOL</span></span>  
 <span data-ttu-id="93c26-118">La version de mscordbi.dll ou de mscordaccore.dll n'est pas la même que celle du fichier CoreCLR.dll cible.</span><span class="sxs-lookup"><span data-stu-id="93c26-118">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="93c26-119">E_FAIL (ou autres codes de retour E_)</span><span class="sxs-lookup"><span data-stu-id="93c26-119">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="93c26-120">Impossible de retourner une [interface ICorDebug](icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="93c26-120">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93c26-121">Notes </span><span class="sxs-lookup"><span data-stu-id="93c26-121">Remarks</span></span>  
 <span data-ttu-id="93c26-122">L'interface retournée fournit les fonctionnalités permettant l'attachement à un CLR dans un processus cible et le débogage du code managé exécuté par le CLR.</span><span class="sxs-lookup"><span data-stu-id="93c26-122">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93c26-123">Spécifications</span><span class="sxs-lookup"><span data-stu-id="93c26-123">Requirements</span></span>  
 <span data-ttu-id="93c26-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93c26-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93c26-125">**En-tête :** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="93c26-125">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="93c26-126">**Bibliothèque :** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="93c26-126">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="93c26-127">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="93c26-127">**.NET Framework Versions:** 3.5 SP1</span></span>
