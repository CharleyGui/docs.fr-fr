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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2adf53d1e29fda077cdcf7b79891f6271993109
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787584"
---
# <a name="emitassembly-method"></a><span data-ttu-id="5e65e-102">EmitAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="5e65e-102">EmitAssembly Method</span></span>
<span data-ttu-id="5e65e-103">Crée l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5e65e-103">Creates the assembly.</span></span> <span data-ttu-id="5e65e-104">Appelez cette méthode une fois que tous les autres fichiers sont fermés, à l’exception du fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="5e65e-104">Call this method after all other files are closed except for the assembly file.</span></span> <span data-ttu-id="5e65e-105">N’appelez pas cette méthode lors de la génération de modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="5e65e-105">Do not call this method when producing unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e65e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5e65e-106">Syntax</span></span>  
  
```cpp  
HRESULT EmitAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e65e-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5e65e-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="5e65e-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="5e65e-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e65e-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="5e65e-109">Return Value</span></span>  
 <span data-ttu-id="5e65e-110">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="5e65e-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e65e-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="5e65e-111">Requirements</span></span>  
 <span data-ttu-id="5e65e-112">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="5e65e-112">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e65e-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5e65e-113">See also</span></span>

- [<span data-ttu-id="5e65e-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="5e65e-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="5e65e-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="5e65e-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="5e65e-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="5e65e-116">ALink API</span></span>](index.md)
