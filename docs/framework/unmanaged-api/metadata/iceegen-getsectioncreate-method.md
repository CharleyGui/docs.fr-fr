---
title: ICeeGen::GetSectionCreate, méthode
ms.date: 03/30/2017
api_name:
- ICeeGen.GetSectionCreate
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetSectionCreate
helpviewer_keywords:
- ICeeGen::GetSectionCreate method [.NET Framework metadata]
- GetSectionCreate method [.NET Framework metadata]
ms.assetid: 154b2460-59ce-4874-a9f2-1b3353486ac5
topic_type:
- apiref
ms.openlocfilehash: 4ef3992d840f539ca07c411c2d740fa32b14edbc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722945"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="af70b-102">ICeeGen::GetSectionCreate, méthode</span><span class="sxs-lookup"><span data-stu-id="af70b-102">ICeeGen::GetSectionCreate Method</span></span>

<span data-ttu-id="af70b-103">Génère et obtient une section de code à l’aide du nom et des valeurs d’indicateur spécifiés.</span><span class="sxs-lookup"><span data-stu-id="af70b-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="af70b-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="af70b-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af70b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af70b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af70b-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="af70b-106">Parameters</span></span>  

 `name`  
 <span data-ttu-id="af70b-107">dans Pointeur vers une chaîne qui spécifie le nom de la section à créer.</span><span class="sxs-lookup"><span data-stu-id="af70b-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="af70b-108">dans Indicateurs qui spécifient des options.</span><span class="sxs-lookup"><span data-stu-id="af70b-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="af70b-109">à Pointeur vers la section de code nouvellement créée.</span><span class="sxs-lookup"><span data-stu-id="af70b-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af70b-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="af70b-110">Remarks</span></span>  

 <span data-ttu-id="af70b-111">Appelez `GetSectionCreate` uniquement si vous avez des exigences de section spéciales qui ne sont pas gérées par d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="af70b-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af70b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="af70b-112">Requirements</span></span>  

 <span data-ttu-id="af70b-113">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af70b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af70b-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="af70b-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="af70b-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="af70b-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="af70b-116">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af70b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af70b-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af70b-117">See also</span></span>

- [<span data-ttu-id="af70b-118">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="af70b-118">ICeeGen Interface</span></span>](iceegen-interface.md)
