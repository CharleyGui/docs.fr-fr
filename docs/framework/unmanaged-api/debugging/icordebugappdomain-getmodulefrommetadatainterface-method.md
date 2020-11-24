---
title: ICorDebugAppDomain::GetModuleFromMetaDataInterface, méthode
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetModuleFromMetaDataInterface
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDataInterface
helpviewer_keywords:
- ICorDebugAppDomain::GetModuleFromMetaDatainterface method [.NET Framework debugging]
- GetModuleFromMetaDatainterface method [.NET Framework debugging]
ms.assetid: f35225b3-5dda-4d5a-913d-b3373e9ab81e
topic_type:
- apiref
ms.openlocfilehash: 5dede67412711736d269386a20446cf45fab1619
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672199"
---
# <a name="icordebugappdomaingetmodulefrommetadatainterface-method"></a><span data-ttu-id="ca361-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface, méthode</span><span class="sxs-lookup"><span data-stu-id="ca361-102">ICorDebugAppDomain::GetModuleFromMetaDataInterface Method</span></span>

<span data-ttu-id="ca361-103">Obtient le module qui correspond à l’interface de métadonnées donnée.</span><span class="sxs-lookup"><span data-stu-id="ca361-103">Gets the module that corresponds to the given metadata interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca361-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ca361-104">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleFromMetaDataInterface (  
    [in] IUnknown           *pIMetaData,  
    [out] ICorDebugModule  **ppModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca361-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ca361-105">Parameters</span></span>  

 `pIMetaData`  
 <span data-ttu-id="ca361-106">dans Pointeur vers un objet qui est l’une des [interfaces de métadonnées](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="ca361-106">[in] A pointer to an object that is one of the [Metadata interfaces](../metadata/metadata-interfaces.md).</span></span>  
  
 `ppModule`  
 <span data-ttu-id="ca361-107">à Pointeur vers l’adresse d’un objet ICorDebugModule qui représente le module correspondant à l’interface de métadonnées donnée.</span><span class="sxs-lookup"><span data-stu-id="ca361-107">[out] A pointer to the address of an ICorDebugModule object that represents the module corresponding to the given metadata interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca361-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="ca361-108">Requirements</span></span>  

 <span data-ttu-id="ca361-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca361-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca361-110">**En-tête :** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ca361-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca361-111">**Bibliothèque :** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ca361-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca361-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca361-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
