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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3adc29f73a3ab4a43a399b024a6c0187f02b5851
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750616"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="b2f92-102">ICeeGen::EmitString, méthode</span><span class="sxs-lookup"><span data-stu-id="b2f92-102">ICeeGen::EmitString Method</span></span>
<span data-ttu-id="b2f92-103">Émet la chaîne spécifiée dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="b2f92-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="b2f92-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="b2f92-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f92-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2f92-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2f92-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2f92-106">Parameters</span></span>  
 `lpString`  
 <span data-ttu-id="b2f92-107">[in] Chaîne à émettre.</span><span class="sxs-lookup"><span data-stu-id="b2f92-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="b2f92-108">[out] L’adresse virtuelle relative de la chaîne émise.</span><span class="sxs-lookup"><span data-stu-id="b2f92-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2f92-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b2f92-109">Requirements</span></span>  
 <span data-ttu-id="b2f92-110">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2f92-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2f92-111">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="b2f92-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b2f92-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b2f92-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b2f92-113">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2f92-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f92-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2f92-114">See also</span></span>

- [<span data-ttu-id="b2f92-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="b2f92-115">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
