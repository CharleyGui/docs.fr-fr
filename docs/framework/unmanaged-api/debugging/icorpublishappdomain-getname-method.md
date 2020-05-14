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
ms.openlocfilehash: e95f96847c6e069758362fb6febc28dc31911bc9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396299"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="9d220-102">ICorPublishAppDomain::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="9d220-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="9d220-103">Obtient le nom du domaine d’application représenté par ce [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9d220-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d220-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d220-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d220-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="9d220-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="9d220-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="9d220-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9d220-107">à Pointeur vers le nombre de caractères larges, y compris le caractère null, retourné dans le `szName` tableau.</span><span class="sxs-lookup"><span data-stu-id="9d220-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="9d220-108">à Tableau dans lequel stocker le nom.</span><span class="sxs-lookup"><span data-stu-id="9d220-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d220-109">Notes</span><span class="sxs-lookup"><span data-stu-id="9d220-109">Remarks</span></span>  
 <span data-ttu-id="9d220-110">Si `szName` n’a pas la valeur null, la `GetName` méthode copie jusqu’à `cchName` caractères (y compris la marque de fin null) dans `szName` .</span><span class="sxs-lookup"><span data-stu-id="9d220-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="9d220-111">Si une valeur non null est retournée dans `pcchName` , le nombre réel de caractères dans le nom (y compris la marque de fin null) est stocké dans le `szName` tableau.</span><span class="sxs-lookup"><span data-stu-id="9d220-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="9d220-112">La `GetName` méthode retourne un S_OK HRESULT quel que soit le nombre de caractères copiés.</span><span class="sxs-lookup"><span data-stu-id="9d220-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d220-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="9d220-113">Requirements</span></span>  
 <span data-ttu-id="9d220-114">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d220-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d220-115">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="9d220-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9d220-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d220-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d220-117">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d220-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d220-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d220-118">See also</span></span>

- [<span data-ttu-id="9d220-119">ICorPublishAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="9d220-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
