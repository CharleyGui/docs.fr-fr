---
title: ICeeGen::GetSectionDataLen, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionDataLen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionDataLen
helpviewer_keywords:
- ICeeGen::GetSectionDataLen method [.NET Framework metadata]
- GetSectionDataLen method [.NET Framework metadata]
ms.assetid: e2a06ee4-b8ee-49c7-935a-c1031a29eef2
topic_type:
- apiref
ms.openlocfilehash: 1855c73849c35bf709b0af261a88e6cd7a40abfb
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008298"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="46d66-102">ICeeGen::GetSectionDataLen, méthode</span><span class="sxs-lookup"><span data-stu-id="46d66-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="46d66-103">Obtient la longueur de la section spécifiée.</span><span class="sxs-lookup"><span data-stu-id="46d66-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="46d66-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="46d66-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d66-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46d66-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="46d66-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="46d66-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="46d66-107">dans Section de données dont la longueur sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="46d66-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="46d66-108">à Longueur retournée de la section spécifiée.</span><span class="sxs-lookup"><span data-stu-id="46d66-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="46d66-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="46d66-109">Remarks</span></span>  
 <span data-ttu-id="46d66-110">Appelez `GetSectionDataLen` uniquement si vous avez des exigences de section spéciales qui ne sont pas gérées par d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="46d66-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46d66-111">Spécifications</span><span class="sxs-lookup"><span data-stu-id="46d66-111">Requirements</span></span>  
 <span data-ttu-id="46d66-112">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46d66-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46d66-113">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="46d66-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="46d66-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="46d66-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="46d66-115">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46d66-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d66-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="46d66-116">See also</span></span>

- [<span data-ttu-id="46d66-117">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="46d66-117">ICeeGen Interface</span></span>](iceegen-interface.md)
