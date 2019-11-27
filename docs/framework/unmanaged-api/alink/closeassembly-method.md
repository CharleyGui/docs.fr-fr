---
title: CloseAssembly, méthode
ms.date: 03/30/2017
api_name:
- IALink.CloseAssembly
- CloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseAssembly
helpviewer_keywords:
- CloseAssembly method
ms.assetid: f66a43bc-a5c5-4190-acbe-63fd27640634
topic_type:
- apiref
ms.openlocfilehash: 70dca19075d8c896408ec78f89549b0c539280de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446579"
---
# <a name="closeassembly-method"></a><span data-ttu-id="d99fb-102">CloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="d99fb-102">CloseAssembly Method</span></span>
<span data-ttu-id="d99fb-103">Finalise les opérations d’assembly.</span><span class="sxs-lookup"><span data-stu-id="d99fb-103">Finalizes assembly operations.</span></span> <span data-ttu-id="d99fb-104">Appelez cette méthode avant de commencer un nouvel assembly ou un module indépendant.</span><span class="sxs-lookup"><span data-stu-id="d99fb-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d99fb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d99fb-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d99fb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d99fb-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="d99fb-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d99fb-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d99fb-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="d99fb-108">Return Value</span></span>  
 <span data-ttu-id="d99fb-109">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="d99fb-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d99fb-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d99fb-110">Requirements</span></span>  
 <span data-ttu-id="d99fb-111">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="d99fb-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d99fb-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d99fb-112">See also</span></span>

- [<span data-ttu-id="d99fb-113">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="d99fb-113">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d99fb-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="d99fb-114">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d99fb-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="d99fb-115">ALink API</span></span>](index.md)
