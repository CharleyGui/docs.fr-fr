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
ms.openlocfilehash: 04103ad305e0ae97669f3e07e06f03c2cdb4dfbd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787519"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="66315-102">EmitInternalExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="66315-102">EmitInternalExportedTypes Method</span></span>
<span data-ttu-id="66315-103">Émet des types ajoutés à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="66315-103">Emits types added to the assembly.</span></span> <span data-ttu-id="66315-104">Appelez cette méthode une fois que des types internes connus ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="66315-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66315-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66315-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="66315-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="66315-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="66315-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="66315-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66315-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="66315-108">Return Value</span></span>  
 <span data-ttu-id="66315-109">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="66315-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66315-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="66315-110">Requirements</span></span>  
 <span data-ttu-id="66315-111">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="66315-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66315-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66315-112">See also</span></span>

- [<span data-ttu-id="66315-113">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="66315-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="66315-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="66315-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="66315-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="66315-115">ALink API</span></span>](index.md)
