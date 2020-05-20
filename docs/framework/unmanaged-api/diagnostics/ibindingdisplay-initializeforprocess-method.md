---
title: IBindingDisplay::InitializeForProcess, méthode
ms.date: 03/30/2017
api_name:
- IBindingDisplay.InitializeForProcess
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- IBindingDisplay::InitializeForProcess
helpviewer_keywords:
- IBindingDisplay::InitializeForProcess method [.NET Framework debugging]
- InitializeForProcess method [.NET Framework debugging]
ms.assetid: 59417acb-4e59-46ad-acfe-d827e6ab6078
topic_type:
- apiref
ms.openlocfilehash: 8645878132359b6218cd62b1ff707208de53704b
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83442148"
---
# <a name="ibindingdisplayinitializeforprocess-method"></a><span data-ttu-id="3bd09-102">IBindingDisplay::InitializeForProcess, méthode</span><span class="sxs-lookup"><span data-stu-id="3bd09-102">IBindingDisplay::InitializeForProcess Method</span></span>
<span data-ttu-id="3bd09-103">Initialise l’objet [IBindingDisplay](ibindingdisplay-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3bd09-103">Initializes the [IBindingDisplay](ibindingdisplay-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bd09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3bd09-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeForProcess (  
    [in] ULONG32   pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bd09-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3bd09-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="3bd09-106">dans Identificateur du processus.</span><span class="sxs-lookup"><span data-stu-id="3bd09-106">[in] The process identifier.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bd09-107">Notes</span><span class="sxs-lookup"><span data-stu-id="3bd09-107">Remarks</span></span>  
 <span data-ttu-id="3bd09-108">Le débogueur appelle la `InitializeForProcess` méthode au moment de la création pour initialiser l’affichage de liaison.</span><span class="sxs-lookup"><span data-stu-id="3bd09-108">The debugger calls the `InitializeForProcess` method at creation time to initialize the binding display.</span></span> <span data-ttu-id="3bd09-109">`InitializeForProcess`doit être appelé au moment de la création avant que toute autre méthode sur `IBindingDisplay` ne soit appelée.</span><span class="sxs-lookup"><span data-stu-id="3bd09-109">`InitializeForProcess` must be called at creation time before any other method on `IBindingDisplay` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bd09-110">Conditions requises</span><span class="sxs-lookup"><span data-stu-id="3bd09-110">Requirements</span></span>  
 <span data-ttu-id="3bd09-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bd09-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bd09-112">**En-tête :** BindingDisplay. h</span><span class="sxs-lookup"><span data-stu-id="3bd09-112">**Header:** BindingDisplay.h</span></span>  
  
 <span data-ttu-id="3bd09-113">**Bibliothèque :** BindingDisplay. idl</span><span class="sxs-lookup"><span data-stu-id="3bd09-113">**Library:** BindingDisplay.idl</span></span>  
  
 <span data-ttu-id="3bd09-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bd09-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bd09-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3bd09-115">See also</span></span>

- [<span data-ttu-id="3bd09-116">IBindingDisplay, interface</span><span class="sxs-lookup"><span data-stu-id="3bd09-116">IBindingDisplay Interface</span></span>](ibindingdisplay-interface.md)
