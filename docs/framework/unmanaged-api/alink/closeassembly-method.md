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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 18e0b7b3547bb246588f6b255483d4c317e0df88
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742230"
---
# <a name="closeassembly-method"></a><span data-ttu-id="da1ba-102">CloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="da1ba-102">CloseAssembly Method</span></span>
<span data-ttu-id="da1ba-103">Finalise les opérations d’assembly.</span><span class="sxs-lookup"><span data-stu-id="da1ba-103">Finalizes assembly operations.</span></span> <span data-ttu-id="da1ba-104">Appelez cette méthode avant de commencer un nouvel assembly ou un module indépendant.</span><span class="sxs-lookup"><span data-stu-id="da1ba-104">Call this method before beginning a new assembly or unbound module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da1ba-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="da1ba-105">Syntax</span></span>  
  
```cpp  
HRESULT CloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="da1ba-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="da1ba-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="da1ba-107">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="da1ba-107">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da1ba-108">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="da1ba-108">Return Value</span></span>  
 <span data-ttu-id="da1ba-109">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="da1ba-109">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da1ba-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="da1ba-110">Requirements</span></span>  
 <span data-ttu-id="da1ba-111">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="da1ba-111">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da1ba-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da1ba-112">See also</span></span>

- [<span data-ttu-id="da1ba-113">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="da1ba-113">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="da1ba-114">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="da1ba-114">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="da1ba-115">API ALink</span><span class="sxs-lookup"><span data-stu-id="da1ba-115">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
