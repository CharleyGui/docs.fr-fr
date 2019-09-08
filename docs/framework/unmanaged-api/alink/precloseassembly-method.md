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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d4cf862ae3676b85a7fc3f09a4f5794e01284737
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787236"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="c2bdc-102">PreCloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="c2bdc-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="c2bdc-103">Ferme le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="c2bdc-103">Closes the assembly file.</span></span> <span data-ttu-id="c2bdc-104">Appelez cette méthode après avoir fermé tous les autres fichiers, mais avant de fermer le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="c2bdc-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="c2bdc-105">N’appelez pas cette méthode pour les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="c2bdc-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2bdc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2bdc-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2bdc-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c2bdc-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c2bdc-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c2bdc-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c2bdc-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c2bdc-109">Return Value</span></span>  
 <span data-ttu-id="c2bdc-110">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c2bdc-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2bdc-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c2bdc-111">Requirements</span></span>  
 <span data-ttu-id="c2bdc-112">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c2bdc-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2bdc-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2bdc-113">See also</span></span>

- [<span data-ttu-id="c2bdc-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="c2bdc-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c2bdc-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="c2bdc-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c2bdc-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="c2bdc-116">ALink API</span></span>](index.md)
