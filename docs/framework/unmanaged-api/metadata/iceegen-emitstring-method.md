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
ms.openlocfilehash: b9c907868df31da8d995c6a6b86db258d395335d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715444"
---
# <a name="iceegenemitstring-method"></a><span data-ttu-id="36ca9-102">ICeeGen::EmitString, méthode</span><span class="sxs-lookup"><span data-stu-id="36ca9-102">ICeeGen::EmitString Method</span></span>

<span data-ttu-id="36ca9-103">Émet la chaîne spécifiée dans la base de code.</span><span class="sxs-lookup"><span data-stu-id="36ca9-103">Emits the specified string into the code base.</span></span>  
  
 <span data-ttu-id="36ca9-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="36ca9-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36ca9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36ca9-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitString (  
    [in]  LPWSTR    lpString,  
    [out] ULONG     *RVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36ca9-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="36ca9-106">Parameters</span></span>  

 `lpString`  
 <span data-ttu-id="36ca9-107">dans Chaîne à émettre.</span><span class="sxs-lookup"><span data-stu-id="36ca9-107">[in] The string to emit.</span></span>  
  
 `RVA`  
 <span data-ttu-id="36ca9-108">à Adresse virtuelle relative de la chaîne émise.</span><span class="sxs-lookup"><span data-stu-id="36ca9-108">[out] The relative virtual address of the emitted string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36ca9-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="36ca9-109">Requirements</span></span>  

 <span data-ttu-id="36ca9-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36ca9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36ca9-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="36ca9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="36ca9-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36ca9-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="36ca9-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36ca9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36ca9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36ca9-114">See also</span></span>

- [<span data-ttu-id="36ca9-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="36ca9-115">ICeeGen Interface</span></span>](iceegen-interface.md)
