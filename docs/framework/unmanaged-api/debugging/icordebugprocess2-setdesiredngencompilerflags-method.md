---
title: ICorDebugProcess2::SetDesiredNGENCompilerFlags, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetDesiredNGENCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags
helpviewer_keywords:
- ICorDebugProcess2::SetDesiredNGENCompilerFlags method [.NET Framework debugging]
- SetDesiredNGENCompilerFlags method [.NET Framework debugging]
ms.assetid: 98320175-7c5e-4dbb-8683-86fa82e2641f
topic_type:
- apiref
ms.openlocfilehash: 366a48e5f6abd92f0c6f796f40bdd263181da4a8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213476"
---
# <a name="icordebugprocess2setdesiredngencompilerflags-method"></a><span data-ttu-id="29c8d-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags, méthode</span><span class="sxs-lookup"><span data-stu-id="29c8d-102">ICorDebugProcess2::SetDesiredNGENCompilerFlags Method</span></span>
<span data-ttu-id="29c8d-103">Définit les indicateurs qui doivent être incorporés dans une image précompilée pour permettre au runtime de charger cette image dans le processus en cours.</span><span class="sxs-lookup"><span data-stu-id="29c8d-103">Sets the flags that must be embedded in a precompiled image in order for the runtime to load that image into the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29c8d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29c8d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDesiredNGENCompilerFlags (  
    [in] DWORD    pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29c8d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="29c8d-105">Parameters</span></span>  
 `pdwFlags`  
 <span data-ttu-id="29c8d-106">dans Valeur de l’énumération [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) qui spécifie les indicateurs de compilateur utilisés pour sélectionner l’image précompilée correcte.</span><span class="sxs-lookup"><span data-stu-id="29c8d-106">[in] A value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the compiler flags used to select the correct pre-compiled image.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29c8d-107">Remarks</span><span class="sxs-lookup"><span data-stu-id="29c8d-107">Remarks</span></span>  
 <span data-ttu-id="29c8d-108">La `SetDesiredNGENCompilerFlags` méthode spécifie les indicateurs qui doivent être incorporés dans une image précompilée afin que le runtime charge cette image dans ce processus.</span><span class="sxs-lookup"><span data-stu-id="29c8d-108">The `SetDesiredNGENCompilerFlags` method specifies the flags that must be embedded in a precompiled image so that the runtime will load that image into this process.</span></span> <span data-ttu-id="29c8d-109">Les indicateurs définis par cette méthode sont utilisés uniquement pour sélectionner l’image précompilée correcte.</span><span class="sxs-lookup"><span data-stu-id="29c8d-109">The flags set by this method are used only to select the correct precompiled image.</span></span> <span data-ttu-id="29c8d-110">Si aucune image de ce type n’existe, le runtime chargera à la place l’image MSIL (Microsoft Intermediate Language) et le compilateur juste-à-temps (JIT).</span><span class="sxs-lookup"><span data-stu-id="29c8d-110">If no such image exists, the runtime will load the Microsoft intermediate language (MSIL) image and the just-in-time (JIT) compiler instead.</span></span> <span data-ttu-id="29c8d-111">Dans ce cas, le débogueur doit toujours utiliser la méthode [ICorDebugModule2 :: SetJITCompilerFlags,](icordebugmodule2-setjitcompilerflags-method.md) pour définir les indicateurs comme vous le souhaitez pour la compilation JIT.</span><span class="sxs-lookup"><span data-stu-id="29c8d-111">In that case, the debugger must still use the [ICorDebugModule2::SetJITCompilerFlags](icordebugmodule2-setjitcompilerflags-method.md) method to set the flags as desired for the JIT compilation.</span></span>  
  
 <span data-ttu-id="29c8d-112">Si une image est chargée, mais que certaines compilations JIT doivent avoir lieu pour cette image (ce qui sera le cas si l’image contient des génériques), les indicateurs de compilateur spécifiés par la `SetDesiredNGENCompilerFlags` méthode s’appliqueront à la compilation JIT supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="29c8d-112">If an image is loaded, but some JIT compiling must take place for that image (which will be the case if the image contains generics), the compiler flags specified by the `SetDesiredNGENCompilerFlags` method will apply to the extra JIT compilation.</span></span>  
  
 <span data-ttu-id="29c8d-113">La `SetDesiredNGENCompilerFlags` méthode doit être appelée pendant le rappel [ICorDebugManagedCallback :: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="29c8d-113">The `SetDesiredNGENCompilerFlags` method must be called during the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span> <span data-ttu-id="29c8d-114">Toute tentative d’appel de la `SetDesiredNGENCompilerFlags` méthode échoue.</span><span class="sxs-lookup"><span data-stu-id="29c8d-114">Attempts to call the `SetDesiredNGENCompilerFlags` method afterwards will fail.</span></span> <span data-ttu-id="29c8d-115">En outre, les tentatives de définition d’indicateurs qui ne sont pas définis dans l' `CorDebugJITCompilerFlags` énumération ou qui ne sont pas autorisés pour le processus donné échouent.</span><span class="sxs-lookup"><span data-stu-id="29c8d-115">Also, attempts to set flags that are either not defined in the `CorDebugJITCompilerFlags` enumeration or are not legal for the given process will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29c8d-116">Spécifications</span><span class="sxs-lookup"><span data-stu-id="29c8d-116">Requirements</span></span>  
 <span data-ttu-id="29c8d-117">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29c8d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29c8d-118">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29c8d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29c8d-119">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29c8d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29c8d-120">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29c8d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c8d-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29c8d-121">See also</span></span>

- [<span data-ttu-id="29c8d-122">ICorDebug, interface</span><span class="sxs-lookup"><span data-stu-id="29c8d-122">ICorDebug Interface</span></span>](icordebug-interface.md)
- [<span data-ttu-id="29c8d-123">ICorDebugManagedCallback, interface</span><span class="sxs-lookup"><span data-stu-id="29c8d-123">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
