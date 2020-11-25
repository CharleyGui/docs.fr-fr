---
title: Méthode ICorDebugVariableSymbol::GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: aa3f335516f7fa22a77b786cd870f2a5064aeff5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727625"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="8a0aa-102">Méthode ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="8a0aa-102">ICorDebugVariableSymbol::GetName Method</span></span>

<span data-ttu-id="8a0aa-103">Obtient le nom d'une variable.</span><span class="sxs-lookup"><span data-stu-id="8a0aa-103">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a0aa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a0aa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a0aa-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8a0aa-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="8a0aa-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="8a0aa-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8a0aa-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="8a0aa-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8a0aa-108">Pointeur vers un tableau de caractères qui contient le nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="8a0aa-108">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a0aa-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="8a0aa-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a0aa-110">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8a0aa-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a0aa-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8a0aa-111">Requirements</span></span>  

 <span data-ttu-id="8a0aa-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a0aa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a0aa-113">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a0aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a0aa-114">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a0aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a0aa-115">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a0aa-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a0aa-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a0aa-116">See also</span></span>

- [<span data-ttu-id="8a0aa-117">ICorDebugVariableSymbol, interface</span><span class="sxs-lookup"><span data-stu-id="8a0aa-117">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="8a0aa-118">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="8a0aa-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
