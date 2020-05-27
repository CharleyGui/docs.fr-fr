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
ms.openlocfilehash: b7b15261d825c1bd5f217c4cecd82ed36a716d0e
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008259"
---
# <a name="iceegengetstring-method"></a><span data-ttu-id="0f675-102">ICeeGen::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="0f675-102">ICeeGen::GetString Method</span></span>
<span data-ttu-id="0f675-103">Obtient la chaîne stockée à l’adresse virtuelle relative spécifiée.</span><span class="sxs-lookup"><span data-stu-id="0f675-103">Gets the string stored at the specified relative virtual address.</span></span>  
  
 <span data-ttu-id="0f675-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="0f675-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f675-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f675-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in]  ULONG      RVA,
    [out] LPWSTR     *lpString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f675-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0f675-106">Parameters</span></span>  
 `RVA`  
 <span data-ttu-id="0f675-107">dans Adresse virtuelle relative de la chaîne à retourner.</span><span class="sxs-lookup"><span data-stu-id="0f675-107">[in] The relative virtual address of the string to return.</span></span>  
  
 `lpString`  
 <span data-ttu-id="0f675-108">à Chaîne retournée.</span><span class="sxs-lookup"><span data-stu-id="0f675-108">[out] The returned string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f675-109">Spécifications</span><span class="sxs-lookup"><span data-stu-id="0f675-109">Requirements</span></span>  
 <span data-ttu-id="0f675-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f675-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f675-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0f675-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f675-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0f675-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f675-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f675-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f675-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0f675-114">See also</span></span>

- [<span data-ttu-id="0f675-115">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="0f675-115">ICeeGen Interface</span></span>](iceegen-interface.md)
