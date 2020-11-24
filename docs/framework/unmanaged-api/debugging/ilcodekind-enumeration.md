---
title: ILCodeKind, énumération
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: 7e9cf760ec609786804a05177349ee2eacd79eaf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692239"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="c963d-102">ILCodeKind, énumération</span><span class="sxs-lookup"><span data-stu-id="c963d-102">ILCodeKind Enumeration</span></span>

<span data-ttu-id="c963d-103">[Pris en charge dans .NET Framework 4.5.2 et ultérieur]</span><span class="sxs-lookup"><span data-stu-id="c963d-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c963d-104">Fournit des valeurs qui spécifient si le débogueur peut accéder aux variables locales ou au code ajoutés dans l'instrumentation ReJIT du profileur.</span><span class="sxs-lookup"><span data-stu-id="c963d-104">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c963d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c963d-105">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="c963d-106">Membres</span><span class="sxs-lookup"><span data-stu-id="c963d-106">Members</span></span>  
  
|<span data-ttu-id="c963d-107">Nom du membre</span><span class="sxs-lookup"><span data-stu-id="c963d-107">Member name</span></span>|<span data-ttu-id="c963d-108">Description</span><span class="sxs-lookup"><span data-stu-id="c963d-108">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="c963d-109">Le débogueur n'a pas accès aux informations de l'instrumentation ReJIT.</span><span class="sxs-lookup"><span data-stu-id="c963d-109">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="c963d-110">Le débogueur a accès aux informations de l'instrumentation ReJIT.</span><span class="sxs-lookup"><span data-stu-id="c963d-110">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c963d-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="c963d-111">Remarks</span></span>  

 <span data-ttu-id="c963d-112">Un membre de l' `ILCodeKind` énumération peut être passé aux méthodes [Enumeratelocalvariablesex,](icordebugilframe4-enumeratelocalvariablesex-method.md) et [getlocalvariableex,](icordebugilframe4-getlocalvariableex-method.md) pour déterminer si le débogueur peut accéder aux variables ajoutées dans l’instrumentation ReJIT du profileur, et à la méthode [getcodeex,](icordebugilframe4-getcodeex-method.md) pour déterminer si le débogueur peut accéder au langage intermédiaire instrumenté.</span><span class="sxs-lookup"><span data-stu-id="c963d-112">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c963d-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c963d-113">Requirements</span></span>  

 <span data-ttu-id="c963d-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c963d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c963d-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c963d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c963d-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c963d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c963d-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c963d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c963d-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c963d-118">See also</span></span>

- [<span data-ttu-id="c963d-119">Énumérations de débogage</span><span class="sxs-lookup"><span data-stu-id="c963d-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="c963d-120">ICorDebugILFrame4, interface</span><span class="sxs-lookup"><span data-stu-id="c963d-120">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="c963d-121">ReJIT : Guide de How-To</span><span class="sxs-lookup"><span data-stu-id="c963d-121">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
