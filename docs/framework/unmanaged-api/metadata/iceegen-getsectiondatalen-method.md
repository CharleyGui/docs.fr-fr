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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: febf952dbfd80a37017cb165aec4a6b207052d1b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745948"
---
# <a name="iceegengetsectiondatalen-method"></a><span data-ttu-id="04e30-102">ICeeGen::GetSectionDataLen, méthode</span><span class="sxs-lookup"><span data-stu-id="04e30-102">ICeeGen::GetSectionDataLen Method</span></span>
<span data-ttu-id="04e30-103">Obtient la longueur de la section spécifiée.</span><span class="sxs-lookup"><span data-stu-id="04e30-103">Gets the length of the specified section.</span></span>  
  
 <span data-ttu-id="04e30-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="04e30-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e30-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04e30-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionDataLen (  
    [in]  HCEESECTION  section,  
    [out] ULONG        *dataLen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04e30-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="04e30-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="04e30-107">[in] La section de données dont la longueur sera récupérée.</span><span class="sxs-lookup"><span data-stu-id="04e30-107">[in] The data section whose length will be retrieved.</span></span>  
  
 `dataLen`  
 <span data-ttu-id="04e30-108">[out] La longueur retournée de la section spécifiée.</span><span class="sxs-lookup"><span data-stu-id="04e30-108">[out] The returned length of the specified section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="04e30-109">Notes</span><span class="sxs-lookup"><span data-stu-id="04e30-109">Remarks</span></span>  
 <span data-ttu-id="04e30-110">Appelez `GetSectionDataLen` uniquement si vous avez des exigences de section spéciale qui ne sont pas gérées par d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="04e30-110">Call `GetSectionDataLen` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e30-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="04e30-111">Requirements</span></span>  
 <span data-ttu-id="04e30-112">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04e30-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04e30-113">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="04e30-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="04e30-114">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="04e30-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="04e30-115">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04e30-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04e30-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="04e30-116">See also</span></span>

- [<span data-ttu-id="04e30-117">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="04e30-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
