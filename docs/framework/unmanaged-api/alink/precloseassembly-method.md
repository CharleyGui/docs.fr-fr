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
ms.openlocfilehash: a820d5d742c722b495a5a4b3952450a0434110fd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741552"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="71571-102">PreCloseAssembly, méthode</span><span class="sxs-lookup"><span data-stu-id="71571-102">PreCloseAssembly Method</span></span>
<span data-ttu-id="71571-103">Ferme le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="71571-103">Closes the assembly file.</span></span> <span data-ttu-id="71571-104">Appelez cette méthode après la fermeture de tous les autres fichiers, mais avant de fermer le fichier d’assembly.</span><span class="sxs-lookup"><span data-stu-id="71571-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="71571-105">N’appelez pas cette méthode pour les modules indépendants.</span><span class="sxs-lookup"><span data-stu-id="71571-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71571-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71571-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="71571-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="71571-107">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="71571-108">ID de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="71571-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71571-109">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="71571-109">Return Value</span></span>  
 <span data-ttu-id="71571-110">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="71571-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71571-111">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="71571-111">Requirements</span></span>  
 <span data-ttu-id="71571-112">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="71571-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71571-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="71571-113">See also</span></span>

- [<span data-ttu-id="71571-114">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="71571-114">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="71571-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="71571-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="71571-116">API ALink</span><span class="sxs-lookup"><span data-stu-id="71571-116">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
