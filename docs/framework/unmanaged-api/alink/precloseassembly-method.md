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
ms.openlocfilehash: 31c0c5e23d1a985c2005693e25ca91379037482a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728678"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="16237-102">PreCloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="16237-102">PreCloseAssembly Method</span></span>

<span data-ttu-id="16237-103">Ferme le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="16237-103">Closes the assembly file.</span></span> <span data-ttu-id="16237-104">Appelez cette méthode après avoir fermé tous les autres fichiers, mais avant de fermer le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="16237-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="16237-105">N’appelez pas cette méthode pour les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="16237-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16237-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="16237-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="16237-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="16237-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="16237-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="16237-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="16237-109">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="16237-109">Return Value</span></span>  

 <span data-ttu-id="16237-110">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="16237-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16237-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="16237-111">Requirements</span></span>  

 <span data-ttu-id="16237-112">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="16237-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16237-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="16237-113">See also</span></span>

- [<span data-ttu-id="16237-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="16237-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="16237-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="16237-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="16237-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="16237-116">ALink API</span></span>](index.md)
