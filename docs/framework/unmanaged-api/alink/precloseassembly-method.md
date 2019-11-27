---
title: PreCloseAssembly, méthode
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
ms.openlocfilehash: fcfd3e79bbb52837a333b5ffacf5c13ae60f2490
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445613"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="58547-102">PreCloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="58547-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="58547-103">Ferme le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="58547-103">Closes the assembly file.</span></span> <span data-ttu-id="58547-104">Appelez cette méthode après avoir fermé tous les autres fichiers, mais avant de fermer le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="58547-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="58547-105">N’appelez pas cette méthode pour les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="58547-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58547-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="58547-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="58547-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="58547-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="58547-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="58547-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="58547-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="58547-109">Return Value</span></span>  
 <span data-ttu-id="58547-110">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="58547-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58547-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="58547-111">Requirements</span></span>  
 <span data-ttu-id="58547-112">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="58547-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58547-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="58547-113">See also</span></span>

- [<span data-ttu-id="58547-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="58547-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="58547-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="58547-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="58547-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="58547-116">ALink API</span></span>](index.md)
