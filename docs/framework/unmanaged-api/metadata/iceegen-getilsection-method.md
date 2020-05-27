---
title: ICeeGen::GetIlSection, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetIlSection
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetIlSection
helpviewer_keywords:
- GetIlSection method [.NET Framework metadata]
- ICeeGen::GetIlSection method [.NET Framework metadata]
ms.assetid: 6f2db2ca-203f-4ac3-9530-208642ca385e
topic_type:
- apiref
ms.openlocfilehash: 05f39befa8966046cd71db82da37c44f20992cff
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008805"
---
# <a name="iceegengetilsection-method"></a><span data-ttu-id="fc2a6-102">ICeeGen::GetIlSection, méthode</span><span class="sxs-lookup"><span data-stu-id="fc2a6-102">ICeeGen::GetIlSection Method</span></span>
<span data-ttu-id="fc2a6-103">Obtient la section de la base de code de langage intermédiaire référencée par le handle spécifié.</span><span class="sxs-lookup"><span data-stu-id="fc2a6-103">Gets the section of the intermediate language code base referenced by the specified handle.</span></span>  
  
 <span data-ttu-id="fc2a6-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="fc2a6-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc2a6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc2a6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIlSection (  
    [in] HCEESECTION  *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc2a6-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="fc2a6-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="fc2a6-107">dans Handle de la section à récupérer.</span><span class="sxs-lookup"><span data-stu-id="fc2a6-107">[in] The handle to the section to get.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc2a6-108">Spécifications</span><span class="sxs-lookup"><span data-stu-id="fc2a6-108">Requirements</span></span>  
 <span data-ttu-id="fc2a6-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc2a6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc2a6-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="fc2a6-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fc2a6-111">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="fc2a6-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="fc2a6-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc2a6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2a6-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fc2a6-113">See also</span></span>

- [<span data-ttu-id="fc2a6-114">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="fc2a6-114">ICeeGen Interface</span></span>](iceegen-interface.md)
