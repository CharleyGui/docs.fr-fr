---
title: EmitInternalExportedTypes, méthode
ms.date: 03/30/2017
api_name:
- EmitInternalExportedTypes
- IALink2.EmitInternalExportedTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitInternalExportedTypes
helpviewer_keywords:
- EmitInternalExportedTypes method
ms.assetid: 28c8b00d-2c14-40b4-aed5-a1db0e2428eb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 15174480c4345f2514572701a5525f0f192ad120
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742103"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="748db-102">EmitInternalExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="748db-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="748db-103">Émet des types ajoutés à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="748db-103">Emits types added to the assembly.</span></span> <span data-ttu-id="748db-104">Appelez cette méthode une fois connu types internes ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="748db-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="748db-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="748db-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="748db-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="748db-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="748db-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="748db-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="748db-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="748db-108">Return Value</span></span>  
 <span data-ttu-id="748db-109">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="748db-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="748db-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="748db-110">Requirements</span></span>  
 <span data-ttu-id="748db-111">Nécessite alink.h</span><span class="sxs-lookup"><span data-stu-id="748db-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="748db-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="748db-112">See also</span></span>

- [<span data-ttu-id="748db-113">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="748db-113">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="748db-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="748db-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="748db-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="748db-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
