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
ms.openlocfilehash: 4325d61d12a66b17f88e5e368cbbc7806d0a3ec5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790707"
---
# <a name="icorpublishappdomaingetname-method"></a><span data-ttu-id="dea50-102">ICorPublishAppDomain::GetName, méthode</span><span class="sxs-lookup"><span data-stu-id="dea50-102">ICorPublishAppDomain::GetName Method</span></span>
<span data-ttu-id="dea50-103">Obtient le nom du domaine d’application représenté par ce [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="dea50-103">Gets the name of the application domain that is represented by this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dea50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dea50-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in]  ULONG32   cchName,   
    [out] ULONG32   *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]   
        WCHAR       *szName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dea50-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="dea50-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="dea50-106">[in] Taille du tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="dea50-106">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="dea50-107">à Pointeur vers le nombre de caractères larges, y compris le caractère null, retourné dans le tableau de `szName`.</span><span class="sxs-lookup"><span data-stu-id="dea50-107">[out] A pointer to the number of wide characters, including the null character, returned in the `szName` array.</span></span>  
  
 `szName`  
 <span data-ttu-id="dea50-108">à Tableau dans lequel stocker le nom.</span><span class="sxs-lookup"><span data-stu-id="dea50-108">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dea50-109">Notes</span><span class="sxs-lookup"><span data-stu-id="dea50-109">Remarks</span></span>  
 <span data-ttu-id="dea50-110">Si `szName` n’est pas null, la méthode `GetName` copie jusqu’à `cchName` caractères (y compris la marque de fin null) dans `szName`.</span><span class="sxs-lookup"><span data-stu-id="dea50-110">If `szName` is non-null, the `GetName` method copies up to `cchName` characters (including the null terminator) into `szName`.</span></span> <span data-ttu-id="dea50-111">Si une valeur non null est retournée dans `pcchName`, le nombre réel de caractères dans le nom (y compris la marque de fin null) est stocké dans le tableau `szName`.</span><span class="sxs-lookup"><span data-stu-id="dea50-111">If a non-null is returned in `pcchName`, the actual number of characters in the name (including the null terminator) is stored in the `szName` array.</span></span>  
  
 <span data-ttu-id="dea50-112">La méthode `GetName` retourne un S_OK HRESULT quel que soit le nombre de caractères copiés.</span><span class="sxs-lookup"><span data-stu-id="dea50-112">The `GetName` method returns an S_OK HRESULT regardless of how many characters were copied.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dea50-113">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="dea50-113">Requirements</span></span>  
 <span data-ttu-id="dea50-114">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dea50-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dea50-115">**En-tête :** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="dea50-115">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="dea50-116">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dea50-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dea50-117">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dea50-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea50-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dea50-118">See also</span></span>

- [<span data-ttu-id="dea50-119">ICorPublishAppDomain, interface</span><span class="sxs-lookup"><span data-stu-id="dea50-119">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
