---
title: GetResolutionScope, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: f2b78b35db6306c82e389955c4824875bcf25334
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447228"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="21ebd-102">GetResolutionScope, méthode</span><span class="sxs-lookup"><span data-stu-id="21ebd-102">GetResolutionScope Method</span></span>
<span data-ttu-id="21ebd-103">Récupère la portée d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="21ebd-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21ebd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21ebd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="21ebd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="21ebd-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="21ebd-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="21ebd-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="21ebd-107">Fichier qui a besoin d’une référence.</span><span class="sxs-lookup"><span data-stu-id="21ebd-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="21ebd-108">Jeton du fichier dans lequel le type est défini dans, généralement récupéré à l’aide de la [méthode ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="21ebd-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="21ebd-109">Reçoit la référence de l’assembly ou du module.</span><span class="sxs-lookup"><span data-stu-id="21ebd-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21ebd-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="21ebd-110">Return Value</span></span>  
 <span data-ttu-id="21ebd-111">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="21ebd-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21ebd-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="21ebd-112">Requirements</span></span>  
 <span data-ttu-id="21ebd-113">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="21ebd-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ebd-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21ebd-114">See also</span></span>

- [<span data-ttu-id="21ebd-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="21ebd-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="21ebd-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="21ebd-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="21ebd-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="21ebd-117">ALink API</span></span>](index.md)
