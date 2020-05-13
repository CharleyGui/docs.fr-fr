---
title: ICorDebugMergedAssemblyRecord::GetSimpleName, méthode
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: f6c6682c8bb23143d308aa4f1a6887b28ea82fcd
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209706"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="3008f-102">ICorDebugMergedAssemblyRecord::GetSimpleName, méthode</span><span class="sxs-lookup"><span data-stu-id="3008f-102">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>
<span data-ttu-id="3008f-103">Obtient le nom simple de l'assembly.</span><span class="sxs-lookup"><span data-stu-id="3008f-103">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3008f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3008f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3008f-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3008f-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3008f-106">[in] Nombre de caractères dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="3008f-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3008f-107">[out] Pointeur vers le nombre de caractères réellement écrits dans la mémoire tampon `szName`.</span><span class="sxs-lookup"><span data-stu-id="3008f-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="3008f-108">Pointeur vers un tableau de caractères.</span><span class="sxs-lookup"><span data-stu-id="3008f-108">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3008f-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="3008f-109">Remarks</span></span>  
 <span data-ttu-id="3008f-110">Cette méthode récupère le nom simple d'un assembly (par exemple, « System.Collections »), sans extension de fichier, version, culture ni jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="3008f-110">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="3008f-111">Elle correspond à la propriété <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> dans le code managé.</span><span class="sxs-lookup"><span data-stu-id="3008f-111">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3008f-112">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3008f-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3008f-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="3008f-113">Requirements</span></span>  
 <span data-ttu-id="3008f-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3008f-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3008f-115">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3008f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3008f-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3008f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3008f-117">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3008f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3008f-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3008f-118">See also</span></span>

- [<span data-ttu-id="3008f-119">ICorDebugMergedAssemblyRecord, interface</span><span class="sxs-lookup"><span data-stu-id="3008f-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="3008f-120">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="3008f-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
