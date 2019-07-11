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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91dc4cb7d64d49d1e95c0c8eb79a29736559d842
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67742084"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="6dfe1-102">EmitManifest, méthode</span><span class="sxs-lookup"><span data-stu-id="6dfe1-102">EmitManifest Method</span></span>
<span data-ttu-id="6dfe1-103">Émet le manifeste final.</span><span class="sxs-lookup"><span data-stu-id="6dfe1-103">Emits the final manifest.</span></span> <span data-ttu-id="6dfe1-104">Appelez cette méthode après l’importation de tous les autres fichiers et la définition de toutes les options.</span><span class="sxs-lookup"><span data-stu-id="6dfe1-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="6dfe1-105">N’appelez pas cette méthode pour les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="6dfe1-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dfe1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dfe1-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="6dfe1-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6dfe1-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6dfe1-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="6dfe1-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="6dfe1-109">Reçoit la taille à réserver dans le fichier d’assembly, récupérée à partir de [StrongNameSignatureSize, fonction](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="6dfe1-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="6dfe1-110">Si vous le souhaitez reçoit le jeton de manifeste d’assembly.</span><span class="sxs-lookup"><span data-stu-id="6dfe1-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6dfe1-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6dfe1-111">Return Value</span></span>  
 <span data-ttu-id="6dfe1-112">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="6dfe1-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dfe1-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6dfe1-113">Requirements</span></span>  
 <span data-ttu-id="6dfe1-114">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="6dfe1-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfe1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dfe1-115">See also</span></span>

- [<span data-ttu-id="6dfe1-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="6dfe1-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6dfe1-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="6dfe1-117">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6dfe1-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="6dfe1-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
