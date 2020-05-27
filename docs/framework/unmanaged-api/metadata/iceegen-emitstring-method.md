---
title: ICeeGen::EmitString, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.EmitString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::EmitString
helpviewer_keywords:
- EmitString method [.NET Framework metadata]
- ICeeGen::EmitString method [.NET Framework metadata]
ms.assetid: ad2710a7-edb8-4493-8619-3fce235e3334
topic_type:
- apiref
ms.openlocfilehash: e7c58e6cdbe0d3c8513721a40eaa3fdfcec6ce2e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008857"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="4634c-102">ICeeGen::EmitString, méthode</span><span class="sxs-lookup"><span data-stu-id="4634c-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="4634c-103">Émet la chaîne spécifiée dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="4634c-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="4634c-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="4634c-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4634c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4634c-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4634c-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4634c-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="4634c-107">dans Chaîne à émettre.</span><span class="sxs-lookup"><span data-stu-id="4634c-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="4634c-108">à Adresse virtuelle relative de la chaîne émise.</span><span class="sxs-lookup"><span data-stu-id="4634c-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4634c-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="4634c-109">Requirements</span></span>  
 <span data-ttu-id="4634c-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4634c-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4634c-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="4634c-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4634c-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4634c-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4634c-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4634c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4634c-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4634c-114">See also</span></span>

- [<span data-ttu-id="4634c-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="4634c-115">ICeeGen Interface</span></span>](iceegen-interface.md)
