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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c6c2e741df594e265fdef51a602a9a4927733b7c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741862"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="a2199-102">GetResolutionScope, méthode</span><span class="sxs-lookup"><span data-stu-id="a2199-102">GetResolutionScope Method</span></span>
<span data-ttu-id="a2199-103">Récupère l’étendue d’un type donné.</span><span class="sxs-lookup"><span data-stu-id="a2199-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2199-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a2199-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2199-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a2199-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a2199-106">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="a2199-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a2199-107">Fichier qui a besoin d’une référence.</span><span class="sxs-lookup"><span data-stu-id="a2199-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="a2199-108">Jeton du fichier dans lequel le type est défini, généralement récupéré avec [ImportFile, méthode](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a2199-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="a2199-109">Reçoit la référence d’assembly ou module.</span><span class="sxs-lookup"><span data-stu-id="a2199-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2199-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a2199-110">Return Value</span></span>  
 <span data-ttu-id="a2199-111">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="a2199-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2199-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a2199-112">Requirements</span></span>  
 <span data-ttu-id="a2199-113">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="a2199-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2199-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2199-114">See also</span></span>

- [<span data-ttu-id="a2199-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="a2199-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="a2199-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="a2199-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="a2199-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="a2199-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
