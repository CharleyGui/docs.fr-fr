---
title: EmitAssembly, méthode
ms.date: 03/30/2017
api_name:
- IALink2.EmitAssembly
- EmitAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- EmitAssembly
helpviewer_keywords:
- EmitAssembly method
ms.assetid: 605ff39e-e5cc-4bff-8196-e8d68a9715b9
topic_type:
- apiref
ms.openlocfilehash: b85b2576660f77eb901c504d398e8bc7909882f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676372"
---
# <a name="emitassembly-method"></a><span data-ttu-id="d24b9-102">EmitAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="d24b9-102">EmitAssembly Method</span></span>

<span data-ttu-id="d24b9-103">Crée l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d24b9-103">Creates the assembly.</span></span> <span data-ttu-id="d24b9-104">Appelez cette méthode une fois que tous les autres fichiers sont fermés, à l’exception du fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="d24b9-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="d24b9-105">N’appelez pas cette méthode lors de la génération de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="d24b9-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d24b9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d24b9-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="d24b9-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d24b9-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="d24b9-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="d24b9-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d24b9-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="d24b9-109">Return Value</span></span>  

 <span data-ttu-id="d24b9-110">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="d24b9-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d24b9-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="d24b9-111">Requirements</span></span>  

 <span data-ttu-id="d24b9-112">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="d24b9-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d24b9-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d24b9-113">See also</span></span>

- [<span data-ttu-id="d24b9-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="d24b9-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="d24b9-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="d24b9-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="d24b9-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="d24b9-116">ALink API</span></span>](index.md)
