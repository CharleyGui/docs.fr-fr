---
title: ICorDebugProcess6::MarkDebuggerAttached, méthode
ms.date: 03/30/2017
ms.assetid: bf94f090-5265-4112-8e57-5b4e20e070d0
ms.openlocfilehash: c6543a89a375d4a2887dbe8cff56d66a15650811
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732591"
---
# <a name="icordebugprocess6markdebuggerattached-method"></a><span data-ttu-id="9a135-102">ICorDebugProcess6::MarkDebuggerAttached, méthode</span><span class="sxs-lookup"><span data-stu-id="9a135-102">ICorDebugProcess6::MarkDebuggerAttached Method</span></span>

<span data-ttu-id="9a135-103">Change l'état interne du programme débogué pour que la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> de la bibliothèque de classes du .NET Framework retourne `true`.</span><span class="sxs-lookup"><span data-stu-id="9a135-103">Changes the internal state of the debugee so that the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method in the .NET Framework Class Library returns `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a135-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a135-104">Syntax</span></span>  
  
```cpp  
HRESULT MarkDebuggerAttached(  
    BOOL fIsAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a135-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9a135-105">Parameters</span></span>  

 `fIsAttached`  
 <span data-ttu-id="9a135-106">`true` si la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> doit indiquer qu'un débogueur est attaché ; sinon, `false`.</span><span class="sxs-lookup"><span data-stu-id="9a135-106">`true` if the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method should indicate that a debugger is attached; `false` otherwise.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a135-107">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="9a135-107">Return Value</span></span>  

 <span data-ttu-id="9a135-108">La méthode peut retourner les valeurs répertoriées dans le tableau suivant.</span><span class="sxs-lookup"><span data-stu-id="9a135-108">The method can return the values listed in the following table.</span></span>  
  
|<span data-ttu-id="9a135-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="9a135-109">Return value</span></span>|<span data-ttu-id="9a135-110">Description</span><span class="sxs-lookup"><span data-stu-id="9a135-110">Description</span></span>|  
|------------------|-----------------|  
|`S_OK`|<span data-ttu-id="9a135-111">L’élément débogué a été mis à jour.</span><span class="sxs-lookup"><span data-stu-id="9a135-111">The debuggee was successfully updated.</span></span>|  
|`CORDBG_E_MODULE_NOT_LOADED`|<span data-ttu-id="9a135-112">L'assembly contenant la méthode <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> n'est pas chargé ou il n'a pas pu être reconnu à cause d'une autre erreur (par exemple, métadonnées manquantes).</span><span class="sxs-lookup"><span data-stu-id="9a135-112">The assembly that contains the <xref:System.Diagnostics.Debugger.IsAttached%2A?displayProperty=nameWithType> method is not loaded, or some other error, such as missing metadata, is preventing it from being recognized.</span></span><br /><br /> <span data-ttu-id="9a135-113">Cette erreur courante est sans gravité.</span><span class="sxs-lookup"><span data-stu-id="9a135-113">This error is common and benign.</span></span> <span data-ttu-id="9a135-114">Rappelez la méthode lors du chargement des assemblys supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="9a135-114">You should call the method again when additional assemblies load.</span></span>|  
|<span data-ttu-id="9a135-115">Autres valeurs `HRESULT` indiquant un échec.</span><span class="sxs-lookup"><span data-stu-id="9a135-115">Other failing `HRESULT` values.</span></span>|<span data-ttu-id="9a135-116">Autres valeurs susceptibles d'indiquer un dysfonctionnement des composants du débogueur ou du compilateur.</span><span class="sxs-lookup"><span data-stu-id="9a135-116">Other values likely indicate misbehaving debugger or compiler components.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9a135-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="9a135-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9a135-118">Cette méthode est uniquement disponible avec .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9a135-118">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a135-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9a135-119">Requirements</span></span>  

 <span data-ttu-id="9a135-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a135-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a135-121">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9a135-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9a135-122">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a135-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a135-123">**Versions de .NET Framework :**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a135-123">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a135-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9a135-124">See also</span></span>

- [<span data-ttu-id="9a135-125">ICorDebugProcess6, interface</span><span class="sxs-lookup"><span data-stu-id="9a135-125">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="9a135-126">Interfaces de débogage</span><span class="sxs-lookup"><span data-stu-id="9a135-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
