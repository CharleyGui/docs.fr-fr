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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de3a9c152f3074339dba330b7827cf795a7e537
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745979"
---
# <a name="iceegengetsectioncreate-method"></a><span data-ttu-id="bdc47-102">ICeeGen::GetSectionCreate, méthode</span><span class="sxs-lookup"><span data-stu-id="bdc47-102">ICeeGen::GetSectionCreate Method</span></span>
<span data-ttu-id="bdc47-103">Génère et obtient une section de code utilisant le nom spécifié et les valeurs d’indicateur.</span><span class="sxs-lookup"><span data-stu-id="bdc47-103">Generates and gets a code section using the specified name and flag values.</span></span>  
  
 <span data-ttu-id="bdc47-104">Cette méthode est obsolète et ne doit pas être utilisée.</span><span class="sxs-lookup"><span data-stu-id="bdc47-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdc47-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bdc47-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSectionCreate (  
    [in]  const char     *name,  
    [in]  DWORD          flags,  
    [out] HCEESECTION    *section  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bdc47-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bdc47-106">Parameters</span></span>  
 `name`  
 <span data-ttu-id="bdc47-107">[in] Un pointeur vers une chaîne qui spécifie le nom de la section doit être créé.</span><span class="sxs-lookup"><span data-stu-id="bdc47-107">[in] A pointer to a string that specifies the name of the section to be created.</span></span>  
  
 `flags`  
 <span data-ttu-id="bdc47-108">[in] Indicateurs qui spécifient des options.</span><span class="sxs-lookup"><span data-stu-id="bdc47-108">[in] Flags that specify options.</span></span>  
  
 `section`  
 <span data-ttu-id="bdc47-109">[out] Pointeur vers la section de code nouvellement créé.</span><span class="sxs-lookup"><span data-stu-id="bdc47-109">[out] A pointer to the newly created code section.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdc47-110">Notes</span><span class="sxs-lookup"><span data-stu-id="bdc47-110">Remarks</span></span>  
 <span data-ttu-id="bdc47-111">Appelez `GetSectionCreate` uniquement si vous avez des exigences de section spéciale qui ne sont pas gérées par d’autres méthodes.</span><span class="sxs-lookup"><span data-stu-id="bdc47-111">Call `GetSectionCreate` only if you have special section requirements that are not handled by other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdc47-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bdc47-112">Requirements</span></span>  
 <span data-ttu-id="bdc47-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdc47-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdc47-114">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bdc47-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bdc47-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bdc47-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bdc47-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdc47-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdc47-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bdc47-117">See also</span></span>

- [<span data-ttu-id="bdc47-118">ICeeGen, interface</span><span class="sxs-lookup"><span data-stu-id="bdc47-118">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
