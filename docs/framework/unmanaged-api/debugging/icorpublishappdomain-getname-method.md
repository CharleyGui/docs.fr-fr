---
title: ICorPublishAppDomain::GetName, méthode
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetName
helpviewer_keywords:
- GetName method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetName method [.NET Framework debugging]
ms.assetid: 6ef8ac9b-9803-4b65-8b13-25f3e0b1bc6b
topic_type:
- apiref
ms.openlocfilehash: 762c637696fdf79ccab6702918b5bf962ea55903
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178415"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="2b530-102">ICorPublishAppDomain::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="2b530-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="2b530-103">Obtient le nom du domaine d’application qui est représenté par cet [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="2b530-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b530-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b530-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b530-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2b530-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="2b530-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="2b530-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="2b530-107">[out] Un pointeur sur le nombre de personnages larges, y compris le caractère nul, retourné dans le `szName` tableau.</span><span class="sxs-lookup"><span data-stu-id="2b530-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="2b530-108">[out] Un tableau dans lequel stocker le nom.</span><span class="sxs-lookup"><span data-stu-id="2b530-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b530-109">Notes </span><span class="sxs-lookup"><span data-stu-id="2b530-109">Remarks</span></span>  
 <span data-ttu-id="2b530-110">Si `szName` elle n’est `GetName` pas nulle, la méthode s’insère jusqu’à `cchName` des caractères (y compris le terminateur nul) en `szName`.</span><span class="sxs-lookup"><span data-stu-id="2b530-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="2b530-111">Si un non-null `pcchName`est retourné dans , le nombre réel de caractères `szName` dans le nom (y compris le terminateur nul) est stocké dans le tableau.</span><span class="sxs-lookup"><span data-stu-id="2b530-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="2b530-112">La `GetName` méthode renvoie un S_OK HRESULT quel que soit le nombre de caractères copiés.</span><span class="sxs-lookup"><span data-stu-id="2b530-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b530-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2b530-113">Requirements</span></span>  
 <span data-ttu-id="2b530-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b530-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b530-115">**En-tête:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="2b530-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="2b530-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b530-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b530-117">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b530-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b530-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2b530-118">See also</span></span>

- [<span data-ttu-id="2b530-119">ICorPublishAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="2b530-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
