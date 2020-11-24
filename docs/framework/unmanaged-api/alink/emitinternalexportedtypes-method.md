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
ms.openlocfilehash: faf1438f56cd49b235ffbb18a0154e3e20c202b9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684965"
---
# <a name="emitinternalexportedtypes-method"></a><span data-ttu-id="32baa-102">EmitInternalExportedTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="32baa-102">EmitInternalExportedTypes Method</span></span>

<span data-ttu-id="32baa-103">Émet des types ajoutés à l’assembly.</span><span class="sxs-lookup"><span data-stu-id="32baa-103">Emits types added to the assembly.</span></span> <span data-ttu-id="32baa-104">Appelez cette méthode une fois que des types internes connus ont été ajoutés.</span><span class="sxs-lookup"><span data-stu-id="32baa-104">Call this method after known internal types have been added.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32baa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32baa-105">Syntax</span></span>  
  
```cpp  
HRESULT EmitInternalExportedTypes(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="32baa-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="32baa-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="32baa-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="32baa-107">ID of assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="32baa-108">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="32baa-108">Return Value</span></span>  

 <span data-ttu-id="32baa-109">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="32baa-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32baa-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="32baa-110">Requirements</span></span>  

 <span data-ttu-id="32baa-111">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="32baa-111">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32baa-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32baa-112">See also</span></span>

- [<span data-ttu-id="32baa-113">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="32baa-113">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="32baa-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="32baa-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="32baa-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="32baa-115">ALink API</span></span>](index.md)
