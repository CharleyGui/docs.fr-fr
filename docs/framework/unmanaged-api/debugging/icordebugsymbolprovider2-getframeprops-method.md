---
title: Méthode ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: ba1fd104c35b6e6dfdfd771f71eb19f8d532a1d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672009"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="5ac37-102">Méthode ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="5ac37-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>

<span data-ttu-id="5ac37-103">Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.</span><span class="sxs-lookup"><span data-stu-id="5ac37-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ac37-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ac37-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5ac37-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5ac37-105">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="5ac37-106">[in] Adresse virtuelle relative du code.</span><span class="sxs-lookup"><span data-stu-id="5ac37-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="5ac37-107">[out] Pointeur vers l'adresse virtuelle relative de départ de la méthode.</span><span class="sxs-lookup"><span data-stu-id="5ac37-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="5ac37-108">[out] Pointeur vers l'adresse virtuelle relative de départ du frame.</span><span class="sxs-lookup"><span data-stu-id="5ac37-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ac37-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="5ac37-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5ac37-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5ac37-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ac37-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5ac37-111">Requirements</span></span>  

 <span data-ttu-id="5ac37-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ac37-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ac37-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5ac37-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5ac37-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5ac37-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ac37-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ac37-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ac37-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5ac37-116">See also</span></span>

- [<span data-ttu-id="5ac37-117">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="5ac37-117">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="5ac37-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="5ac37-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
