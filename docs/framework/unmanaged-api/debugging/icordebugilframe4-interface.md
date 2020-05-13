---
title: ICorDebugILFrame4, interface
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: d0b1c31d45efea4892182c43c801112530361994
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213700"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="090f7-102">ICorDebugILFrame4, interface</span><span class="sxs-lookup"><span data-stu-id="090f7-102">ICorDebugILFrame4 Interface</span></span>
<span data-ttu-id="090f7-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="090f7-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="090f7-104">Fournit des méthodes qui vous permettent d'accéder aux variables locales et au code dans un frame de pile de code de langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="090f7-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="090f7-105">Un paramètre spécifie si le débogueur a accès aux variables et au code ajoutés dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="090f7-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="090f7-106">Méthodes</span><span class="sxs-lookup"><span data-stu-id="090f7-106">Methods</span></span>  
  
|<span data-ttu-id="090f7-107">Méthode</span><span class="sxs-lookup"><span data-stu-id="090f7-107">Method</span></span>|<span data-ttu-id="090f7-108">Description</span><span class="sxs-lookup"><span data-stu-id="090f7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="090f7-109">EnumerateLocalVariablesEx, méthode</span><span class="sxs-lookup"><span data-stu-id="090f7-109">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="090f7-110">Retourne une liste des variables locales disponibles dans le frame actif.</span><span class="sxs-lookup"><span data-stu-id="090f7-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="090f7-111">GetCodeEx, méthode</span><span class="sxs-lookup"><span data-stu-id="090f7-111">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="090f7-112">Retourne le code exécuté par ce frame de pile.</span><span class="sxs-lookup"><span data-stu-id="090f7-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="090f7-113">GetLocalVariableEx, méthode</span><span class="sxs-lookup"><span data-stu-id="090f7-113">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="090f7-114">Retourne la valeur d'une variable locale du frame de langage intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="090f7-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="090f7-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="090f7-115">Remarks</span></span>  
 <span data-ttu-id="090f7-116">Ces méthodes offrent des fonctionnalités en plus de celles fournies par les méthodes [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md)et [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) .</span><span class="sxs-lookup"><span data-stu-id="090f7-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="090f7-117">Chaque méthode comprend un paramètre `flags` qui spécifie si des variables locales ou du code supplémentaires définis par une demande ReJIT du profileur sont visibles.</span><span class="sxs-lookup"><span data-stu-id="090f7-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="090f7-118">Spécifications</span><span class="sxs-lookup"><span data-stu-id="090f7-118">Requirements</span></span>  
 <span data-ttu-id="090f7-119">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="090f7-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="090f7-120">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="090f7-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="090f7-121">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="090f7-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="090f7-122">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="090f7-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="090f7-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="090f7-123">See also</span></span>

- [<span data-ttu-id="090f7-124">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="090f7-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="090f7-125">Débogage</span><span class="sxs-lookup"><span data-stu-id="090f7-125">Debugging</span></span>](index.md)
