---
title: EmitManifest, méthode
ms.date: 03/30/2017
api_name:
- EmitManifest
- IALink.EmitManifest
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitManifest
helpviewer_keywords:
- EmitManifest method
ms.assetid: fdebc1f3-b62e-4d9e-b775-8ccaa8ecb250
topic_type:
- apiref
ms.openlocfilehash: f3bb978b8358992fd9aa7da922e28efc1ed1a951
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446484"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="e06ae-102">EmitManifest, méthode</span><span class="sxs-lookup"><span data-stu-id="e06ae-102">EmitManifest Method</span></span>
<span data-ttu-id="e06ae-103">Emits the final manifest.</span><span class="sxs-lookup"><span data-stu-id="e06ae-103">Emits the final manifest.</span></span> <span data-ttu-id="e06ae-104">Call this method after importing all other files and setting all options.</span><span class="sxs-lookup"><span data-stu-id="e06ae-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="e06ae-105">Do not call this method for unbound modules.</span><span class="sxs-lookup"><span data-stu-id="e06ae-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e06ae-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e06ae-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="e06ae-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="e06ae-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="e06ae-108">ID of the assembly.</span><span class="sxs-lookup"><span data-stu-id="e06ae-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="e06ae-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="e06ae-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="e06ae-110">Optionally receives the assembly manifest token.</span><span class="sxs-lookup"><span data-stu-id="e06ae-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e06ae-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="e06ae-111">Return Value</span></span>  
 <span data-ttu-id="e06ae-112">Returns S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="e06ae-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e06ae-113">spécifications</span><span class="sxs-lookup"><span data-stu-id="e06ae-113">Requirements</span></span>  
 <span data-ttu-id="e06ae-114">Requires alink.h.</span><span class="sxs-lookup"><span data-stu-id="e06ae-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e06ae-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e06ae-115">See also</span></span>

- [<span data-ttu-id="e06ae-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="e06ae-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="e06ae-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="e06ae-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="e06ae-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="e06ae-118">ALink API</span></span>](index.md)
