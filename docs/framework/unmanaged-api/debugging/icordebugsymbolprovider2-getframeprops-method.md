---
title: Méthode ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: ad44c5a7b2d901967ae354f3c30218a8c7f2c2de
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379340"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="c1987-102">Méthode ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="c1987-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="c1987-103">Retourne l'adresse virtuelle relative de départ d'une méthode et le frame parent en fonction d'une adresse virtuelle relative de code.</span><span class="sxs-lookup"><span data-stu-id="c1987-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1987-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1987-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1987-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c1987-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="c1987-106">[in] Adresse virtuelle relative du code.</span><span class="sxs-lookup"><span data-stu-id="c1987-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="c1987-107">[out] Pointeur vers l'adresse virtuelle relative de départ de la méthode.</span><span class="sxs-lookup"><span data-stu-id="c1987-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="c1987-108">[out] Pointeur vers l'adresse virtuelle relative de départ du frame.</span><span class="sxs-lookup"><span data-stu-id="c1987-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1987-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="c1987-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1987-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c1987-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1987-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="c1987-111">Requirements</span></span>  
 <span data-ttu-id="c1987-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1987-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1987-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1987-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1987-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1987-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1987-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1987-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1987-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1987-116">See also</span></span>

- [<span data-ttu-id="c1987-117">ICorDebugSymbolProvider2, interface</span><span class="sxs-lookup"><span data-stu-id="c1987-117">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="c1987-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="c1987-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
