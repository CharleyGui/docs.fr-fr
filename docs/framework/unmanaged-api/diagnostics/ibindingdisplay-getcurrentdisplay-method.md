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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d075aeeb904469613999829a1444511d069b9918
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775979"
---
# <a name="ibindingdisplaygetcurrentdisplay-method"></a><span data-ttu-id="7736b-102">IBindingDisplay::GetCurrentDisplay, méthode</span><span class="sxs-lookup"><span data-stu-id="7736b-102">IBindingDisplay::GetCurrentDisplay Method</span></span>
<span data-ttu-id="7736b-103">Retourne les informations d’affichage de liaison actuel.</span><span class="sxs-lookup"><span data-stu-id="7736b-103">Returns the current binding display information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7736b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7736b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentDisplay (  
    [out, retval] SAFEARRAY(struct BindingDisplayTabControl) *display  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7736b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="7736b-105">Parameters</span></span>  
 `display`  
 <span data-ttu-id="7736b-106">[out, retval] Un pointeur vers un safearray qui contient les informations d’affichage de liaison.</span><span class="sxs-lookup"><span data-stu-id="7736b-106">[out, retval] A pointer to a safearray containing the binding display information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7736b-107">Notes</span><span class="sxs-lookup"><span data-stu-id="7736b-107">Remarks</span></span>  
 <span data-ttu-id="7736b-108">Le [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) méthode doit avoir préalablement réussi et le programme doit être arrêté par un débogueur.</span><span class="sxs-lookup"><span data-stu-id="7736b-108">The [IBindingDisplay::InitializeForProcess](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md) method must have previously succeeded, and the program must be stopped by a debugger.</span></span>  
  
 <span data-ttu-id="7736b-109">L’appelant doit libérer retourné `SAFEARRAY` mémoire à l’aide de [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span><span class="sxs-lookup"><span data-stu-id="7736b-109">The caller must deallocate the returned `SAFEARRAY` memory by using [SafeArrayDestroy](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-safearraydestroy).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7736b-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="7736b-110">Requirements</span></span>  
 <span data-ttu-id="7736b-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7736b-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7736b-112">**En-tête :** BindingDisplay.h</span><span class="sxs-lookup"><span data-stu-id="7736b-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="7736b-113">**Bibliothèque :** BindingDisplay.idl</span><span class="sxs-lookup"><span data-stu-id="7736b-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="7736b-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7736b-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7736b-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7736b-115">See also</span></span>

- [<span data-ttu-id="7736b-116">IBindingDisplay, interface</span><span class="sxs-lookup"><span data-stu-id="7736b-116">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)
- [<span data-ttu-id="7736b-117">InitializeForProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="7736b-117">InitializeForProcess Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-initializeforprocess-method.md)
