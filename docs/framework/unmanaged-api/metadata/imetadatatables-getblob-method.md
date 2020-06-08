---
title: IMetaDataTables::GetBlob, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetBlob
helpviewer_keywords:
- GetBlob method [.NET Framework metadata]
- IMetaDataTables::GetBlob method [.NET Framework metadata]
ms.assetid: 94667c1c-6d58-4aa7-b74e-530b11e2a276
topic_type:
- apiref
ms.openlocfilehash: ff97e419c5309fa7cb820cb7e82db96fee34f30c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501272"
---
# <a name="imetadatatablesgetblob-method"></a><span data-ttu-id="c072a-102">IMetaDataTables::GetBlob, méthode</span><span class="sxs-lookup"><span data-stu-id="c072a-102">IMetaDataTables::GetBlob Method</span></span>
<span data-ttu-id="c072a-103">Obtient un pointeur vers l’objet BLOB (Binary Large Object) situé à l’index de colonne spécifié.</span><span class="sxs-lookup"><span data-stu-id="c072a-103">Gets a pointer to the binary large object (BLOB) at the specified column index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c072a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c072a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBlob (  
    [in]  ULONG          ixBlob,  
    [out] ULONG          *pcbData,  
    [out] const void     **ppData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c072a-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c072a-105">Parameters</span></span>  
 `ixBlob`  
 <span data-ttu-id="c072a-106">dans Adresse mémoire à partir de laquelle effectuer l’extraction `ppData` .</span><span class="sxs-lookup"><span data-stu-id="c072a-106">[in] The memory address from which to get `ppData`.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="c072a-107">à Pointeur vers la taille, en octets, de `ppData` .</span><span class="sxs-lookup"><span data-stu-id="c072a-107">[out] A pointer to the size, in bytes, of `ppData`.</span></span>  
  
 `ppData`  
 <span data-ttu-id="c072a-108">à Pointeur vers un pointeur vers les données binaires récupérées.</span><span class="sxs-lookup"><span data-stu-id="c072a-108">[out] A pointer to a pointer to the binary data retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c072a-109">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c072a-109">Requirements</span></span>  
 <span data-ttu-id="c072a-110">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c072a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c072a-111">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="c072a-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c072a-112">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c072a-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c072a-113">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c072a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c072a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c072a-114">See also</span></span>

- [<span data-ttu-id="c072a-115">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="c072a-115">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="c072a-116">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="c072a-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
