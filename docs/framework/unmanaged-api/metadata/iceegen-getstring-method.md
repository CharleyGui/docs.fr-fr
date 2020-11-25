---
title: ICeeGen::GetString, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetString
helpviewer_keywords:
- ICeeGen::GetString method [.NET Framework metadata]
- GetString method, ICeeGen interface [.NET Framework metadata]
ms.assetid: 7cc22562-128c-440a-9147-55ff20f173d7
topic_type:
- apiref
ms.openlocfilehash: 9d14ec33128596a148ca3509a49c8c97fafe82d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723101"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="9c3d8-102">ICeeGen::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="9c3d8-102">ICeeGen::GetString Method</span></span>

<span data-ttu-id="9c3d8-103">Obtient la chaîne stockée à l’adresse virtuelle relative spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9c3d8-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="9c3d8-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="9c3d8-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c3d8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9c3d8-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c3d8-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9c3d8-106">Parameters</span></span>  

 `RVA`  
 <span data-ttu-id="9c3d8-107">dans Adresse virtuelle relative de la chaîne à retourner.</span><span class="sxs-lookup"><span data-stu-id="9c3d8-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="9c3d8-108">à Chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="9c3d8-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c3d8-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="9c3d8-109">Requirements</span></span>  

 <span data-ttu-id="9c3d8-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c3d8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c3d8-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="9c3d8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9c3d8-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9c3d8-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9c3d8-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c3d8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c3d8-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c3d8-114">See also</span></span>

- [<span data-ttu-id="9c3d8-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="9c3d8-115">ICeeGen Interface</span></span>](iceegen-interface.md)
