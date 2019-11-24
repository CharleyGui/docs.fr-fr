---
title: IMetaDataTables::GetString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetString
helpviewer_keywords:
- IMetaDataTables::GetString method [.NET Framework metadata]
- GetString method, IMetaDataTables interface [.NET Framework metadata]
ms.assetid: 895c35cf-b95d-4e3b-93b5-cfc1cf9044fc
topic_type:
- apiref
ms.openlocfilehash: 055499230f500cb7249746e1acbf46b4548d25bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426797"
---
# <a name="imetadatatablesgetstring-method"></a><span data-ttu-id="c148e-102">IMetaDataTables::GetString, méthode</span><span class="sxs-lookup"><span data-stu-id="c148e-102">IMetaDataTables::GetString Method</span></span>
<span data-ttu-id="c148e-103">Gets the string at the specified index from the table column in the current reference scope.</span><span class="sxs-lookup"><span data-stu-id="c148e-103">Gets the string at the specified index from the table column in the current reference scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c148e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c148e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (   
    [in]  ULONG       ixString,  
    [out] const char  **ppString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c148e-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c148e-105">Parameters</span></span>  
 `ixString`  
 <span data-ttu-id="c148e-106">[in] The index at which to start to search for the next value.</span><span class="sxs-lookup"><span data-stu-id="c148e-106">[in] The index at which to start to search for the next value.</span></span>  
  
 `ppString`  
 <span data-ttu-id="c148e-107">[out] A pointer to a pointer to the returned string value.</span><span class="sxs-lookup"><span data-stu-id="c148e-107">[out] A pointer to a pointer to the returned string value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c148e-108">spécifications</span><span class="sxs-lookup"><span data-stu-id="c148e-108">Requirements</span></span>  
 <span data-ttu-id="c148e-109">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c148e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c148e-110">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c148e-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c148e-111">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c148e-111">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c148e-112">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c148e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c148e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c148e-113">See also</span></span>

- [<span data-ttu-id="c148e-114">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="c148e-114">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="c148e-115">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="c148e-115">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
