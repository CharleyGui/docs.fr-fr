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
ms.openlocfilehash: bdab1fd10be8fd245f4348798232964721b4487a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777340"
---
# <a name="emitmanifest-method"></a><span data-ttu-id="c65ad-102">EmitManifest, méthode</span><span class="sxs-lookup"><span data-stu-id="c65ad-102">EmitManifest Method</span></span>
<span data-ttu-id="c65ad-103">Émet le manifeste final.</span><span class="sxs-lookup"><span data-stu-id="c65ad-103">Emits the final manifest.</span></span> <span data-ttu-id="c65ad-104">Appelez cette méthode après l’importation de tous les autres fichiers et la définition de toutes les options.</span><span class="sxs-lookup"><span data-stu-id="c65ad-104">Call this method after importing all other files and setting all options.</span></span> <span data-ttu-id="c65ad-105">N’appelez pas cette méthode pour les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="c65ad-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c65ad-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c65ad-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitManifest(  
    mdAssembly   AssemblyID,  
    DWORD*       pdwReserveSize,  
    mdAssembly*  ptkManifest  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c65ad-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c65ad-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c65ad-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c65ad-108">ID of the assembly.</span></span>  
  
 `pdwReserveSize`  
 <span data-ttu-id="c65ad-109">Reçoit la taille à réserver dans le fichier d’assembly, récupérée à partir de la [fonction StrongNameSignatureSize (](../strong-naming/strongnamesignaturesize-function.md).</span><span class="sxs-lookup"><span data-stu-id="c65ad-109">Receives the size to reserve in the assembly file, retrieved from [StrongNameSignatureSize Function](../strong-naming/strongnamesignaturesize-function.md).</span></span>  
  
 `ptkManifest`  
 <span data-ttu-id="c65ad-110">Reçoit éventuellement le jeton du manifeste de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c65ad-110">Optionally receives the assembly manifest token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c65ad-111">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c65ad-111">Return Value</span></span>  
 <span data-ttu-id="c65ad-112">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c65ad-112">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c65ad-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c65ad-113">Requirements</span></span>  
 <span data-ttu-id="c65ad-114">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c65ad-114">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c65ad-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c65ad-115">See also</span></span>

- [<span data-ttu-id="c65ad-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="c65ad-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c65ad-117">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="c65ad-117">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c65ad-118">API ALink</span><span class="sxs-lookup"><span data-stu-id="c65ad-118">ALink API</span></span>](index.md)
