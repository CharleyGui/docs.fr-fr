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
ms.openlocfilehash: f40345b09cae164660711b987f62130518736518
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208622"
---
# <a name="createdebugginginterfacefromversion-function-for-silverlight"></a><span data-ttu-id="c6520-102">Fonction CreateDebuggingInterfaceFromVersion Function pour Silverlight</span><span class="sxs-lookup"><span data-stu-id="c6520-102">CreateDebuggingInterfaceFromVersion Function for Silverlight</span></span>

<span data-ttu-id="c6520-103">Accepte une chaîne de version common language runtime (CLR) retournée par la [fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md)et retourne une interface de débogueur correspondante (en général, [ICorDebug](icordebug-interface.md)).</span><span class="sxs-lookup"><span data-stu-id="c6520-103">Accepts a common language runtime (CLR) version string that is returned from the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md), and returns a corresponding debugger interface (typically, [ICorDebug](icordebug-interface.md)).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6520-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6520-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateDebuggingInterfaceFromVersion (  
    [in]  LPCWSTR      szDebuggeeVersion,  
    [out] IUnknown**   ppCordb,  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6520-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c6520-105">Parameters</span></span>  

 `szDebuggeeVersion`\
 <span data-ttu-id="c6520-106">dans Chaîne de version du CLR dans le programme débogué cible, qui est retournée par la [fonction CreateVersionStringFromModule](createversionstringfrommodule-function.md).</span><span class="sxs-lookup"><span data-stu-id="c6520-106">[in] Version string of the CLR in the target debuggee, which is returned by the [CreateVersionStringFromModule function](createversionstringfrommodule-function.md).</span></span>  
  
 `ppCordb`\
 <span data-ttu-id="c6520-107">[out] Pointeur vers un autre pointeur vers un objet COM (`IUnknown`).</span><span class="sxs-lookup"><span data-stu-id="c6520-107">[out] Pointer to a pointer to a COM object (`IUnknown`).</span></span> <span data-ttu-id="c6520-108">Cet objet est casté en objet [ICorDebug](icordebug-interface.md) avant d’être retourné.</span><span class="sxs-lookup"><span data-stu-id="c6520-108">This object will be cast to an [ICorDebug](icordebug-interface.md) object before it is returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6520-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c6520-109">Return Value</span></span>

 `S_OK`\
 <span data-ttu-id="c6520-110">`ppCordb`fait référence à un objet valide qui implémente l’interface d' [interface ICorDebug](icordebug-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c6520-110">`ppCordb` references a valid object that implements the [ICorDebug interface](icordebug-interface.md) interface.</span></span>  
  
 `E_INVALIDARG`\
 <span data-ttu-id="c6520-111">`szDebuggeeVersion` ou `ppCordb` a la valeur null.</span><span class="sxs-lookup"><span data-stu-id="c6520-111">Either `szDebuggeeVersion` or `ppCordb` is null.</span></span>  
  
 `CORDBG_E_DEBUG_COMPONENT_MISSING`\
 <span data-ttu-id="c6520-112">Un composant nécessaire pour le débogage CLR est introuvable.</span><span class="sxs-lookup"><span data-stu-id="c6520-112">A component that is necessary for CLR debugging cannot be located.</span></span> <span data-ttu-id="c6520-113">_Mscordbi. dll_ ou _mscordaccore. dll_ est introuvable dans le même répertoire que la cible CoreCLR. dll.</span><span class="sxs-lookup"><span data-stu-id="c6520-113">Either _mscordbi.dll_ or _mscordaccore.dll_ was not found in the same directory as the target CoreCLR.dll.</span></span>  
  
 `CORDBG_E_INCOMPATIBLE_PROTOCOL`\
 <span data-ttu-id="c6520-114">La version de mscordbi.dll ou de mscordaccore.dll n'est pas la même que celle du fichier CoreCLR.dll cible.</span><span class="sxs-lookup"><span data-stu-id="c6520-114">Either mscordbi.dll or mscordaccore.dll is not the same version as the target CoreCLR.dll.</span></span>  
  
 <span data-ttu-id="c6520-115">`E_FAIL`(ou autres `E_` codes de retour) </span><span class="sxs-lookup"><span data-stu-id="c6520-115">`E_FAIL` (or other `E_` return codes)</span></span>\
 <span data-ttu-id="c6520-116">Impossible de retourner une [interface ICorDebug](icordebug-interface.md).</span><span class="sxs-lookup"><span data-stu-id="c6520-116">Unable to return an [ICorDebug interface](icordebug-interface.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6520-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="c6520-117">Remarks</span></span>

 <span data-ttu-id="c6520-118">L'interface retournée fournit les fonctionnalités permettant l'attachement à un CLR dans un processus cible et le débogage du code managé exécuté par le CLR.</span><span class="sxs-lookup"><span data-stu-id="c6520-118">The interface that is returned provides the facilities for attaching to a CLR in a target process and debugging the managed code that the CLR is running.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6520-119">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c6520-119">Requirements</span></span>

 <span data-ttu-id="c6520-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6520-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6520-121">**En-tête :** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="c6520-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="c6520-122">**Bibliothèque :** dbgshim. dll</span><span class="sxs-lookup"><span data-stu-id="c6520-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="c6520-123">**Versions de .NET Framework :** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="c6520-123">**.NET Framework Versions:** 3.5 SP1</span></span>
