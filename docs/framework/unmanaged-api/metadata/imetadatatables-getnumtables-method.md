---
title: IMetaDataTables::GetNumTables, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNumTables
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNumTables
helpviewer_keywords:
- GetNumTables method [.NET Framework metadata]
- IMetaDataTables::GetNumTables method [.NET Framework metadata]
ms.assetid: 8196f2a3-bbf2-45d3-a6cd-74502c356644
topic_type:
- apiref
ms.openlocfilehash: 7e1ea16e7954f21b1349e88d43d7e3b271a57ed7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95680289"
---
# <a name="imetadatatablesgetnumtables-method"></a><span data-ttu-id="d95b6-102">IMetaDataTables::GetNumTables, méthode</span><span class="sxs-lookup"><span data-stu-id="d95b6-102">IMetaDataTables::GetNumTables Method</span></span>

<span data-ttu-id="d95b6-103">Obtient le nombre de tables dans la portée de l' `IMetaDataTables` instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="d95b6-103">Gets the number of tables in the scope of the current `IMetaDataTables` instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d95b6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d95b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNumTables (  
    [out]  ULONG   *pcTables  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d95b6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d95b6-105">Parameters</span></span>  

 `pcTables`  
 <span data-ttu-id="d95b6-106">à Pointeur vers le nombre de tables dans la portée de l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="d95b6-106">[out] A pointer to the number of tables in the current instance scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d95b6-107">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d95b6-107">Requirements</span></span>  

 <span data-ttu-id="d95b6-108">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d95b6-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d95b6-109">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d95b6-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d95b6-110">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d95b6-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d95b6-111">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d95b6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d95b6-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d95b6-112">See also</span></span>

- [<span data-ttu-id="d95b6-113">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="d95b6-113">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="d95b6-114">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="d95b6-114">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
