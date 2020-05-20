---
title: IBindingDisplay::GetCurrentDisplay, méthode
ms.date: 03/30/2017
api_name:
- IBindingDisplay.GetCurrentDisplay
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::GetCurrentDisplay
helpviewer_keywords:
- IBindingDisplay::GetCurrentDisplay method [.NET Framework debugging]
- GetCurrentDisplay method [.NET Framework debugging]
ms.assetid: d28eeea4-c4e0-40d4-91de-198d98cfa13c
topic_type:
- apiref
ms.openlocfilehash: 6fe8c3266a8c9a52cd1022589cd68485c4326fd1
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442187"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="fbdd2-102">IBindingDisplay::GetCurrentDisplay, méthode</span><span class="sxs-lookup"><span data-stu-id="fbdd2-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="fbdd2-103">Retourne les informations d’affichage de liaison actuelles.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbdd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fbdd2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbdd2-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fbdd2-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="fbdd2-106">[out, retval] Pointeur vers un SafeArray contenant les informations d’affichage de liaison.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fbdd2-107">Notes</span><span class="sxs-lookup"><span data-stu-id="fbdd2-107">Remarks</span></span>  
 <span data-ttu-id="fbdd2-108">La méthode [IBindingDisplay :: InitializeForProcess,](ibindingdisplay-initializeforprocess-method.md) doit avoir déjà réussi et le programme doit être arrêté par un débogueur.</span><span class="sxs-lookup"><span data-stu-id="fbdd2-108">The [IBindingDisplay::InitializeForProcess](ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="fbdd2-109">L’appelant doit libérer la mémoire retournée `SAFEARRAY` à l’aide de [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="fbdd2-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbdd2-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="fbdd2-110">Requirements</span></span>  
 <span data-ttu-id="fbdd2-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbdd2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbdd2-112">**En-tête :** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="fbdd2-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="fbdd2-113">**Bibliothèque :** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="fbdd2-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="fbdd2-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fbdd2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbdd2-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fbdd2-115">See also</span></span>

- [<span data-ttu-id="fbdd2-116">IBindingDisplay, interface</span><span class="sxs-lookup"><span data-stu-id="fbdd2-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
- [<span data-ttu-id="fbdd2-117">InitializeForProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="fbdd2-117">InitializeForProcess Method</span></span>](ibindingdisplay-initializeforprocess-method.md)
