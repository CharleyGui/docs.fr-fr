---
title: GetScope, méthode
ms.date: 03/30/2017
api_name:
- IALink.GetScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope
helpviewer_keywords:
- GetScope method
ms.assetid: e1555328-2c71-4ece-b357-9eb6d3a8efc4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f3c3142ca12789b086bcd8b5a9c00c943264ae7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741857"
---
# <a name="getscope-method"></a><span data-ttu-id="b9c28-102">GetScope, méthode</span><span class="sxs-lookup"><span data-stu-id="b9c28-102">GetScope Method</span></span>
<span data-ttu-id="b9c28-103">Obtient une portée d’importation.</span><span class="sxs-lookup"><span data-stu-id="b9c28-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9c28-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9c28-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport** ppImportScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9c28-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b9c28-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b9c28-106">ID unique de l’assembly dans lequel importer.</span><span class="sxs-lookup"><span data-stu-id="b9c28-106">Unique ID of assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b9c28-107">ID unique du fichier à importer à partir de.</span><span class="sxs-lookup"><span data-stu-id="b9c28-107">Unique ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="b9c28-108">Portée de base zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="b9c28-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="b9c28-109">Reçoit [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface pour l’étendue.</span><span class="sxs-lookup"><span data-stu-id="b9c28-109">Receives [IMetaDataImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface for the scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9c28-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b9c28-110">Return Value</span></span>  
 <span data-ttu-id="b9c28-111">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="b9c28-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9c28-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b9c28-112">Requirements</span></span>  
 <span data-ttu-id="b9c28-113">Nécessite alink.h</span><span class="sxs-lookup"><span data-stu-id="b9c28-113">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c28-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b9c28-114">See also</span></span>

- [<span data-ttu-id="b9c28-115">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="b9c28-115">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="b9c28-116">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="b9c28-116">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="b9c28-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="b9c28-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
