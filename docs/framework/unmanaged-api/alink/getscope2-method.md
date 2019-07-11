---
title: GetScope2, méthode
ms.date: 03/30/2017
api_name:
- IALink2.GetScope2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetScope2
helpviewer_keywords:
- GetScope2 method
ms.assetid: 49435665-6f5a-4acd-9034-8c9244a04a63
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0c0abc63610f3f1ed6e8a556c44ee15edc1ea20b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741844"
---
# <a name="getscope2-method"></a><span data-ttu-id="6d309-102">GetScope2, méthode</span><span class="sxs-lookup"><span data-stu-id="6d309-102">GetScope2 Method</span></span>
<span data-ttu-id="6d309-103">Obtient une portée d’importation.</span><span class="sxs-lookup"><span data-stu-id="6d309-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d309-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d309-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="6d309-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="6d309-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="6d309-106">ID de l’assembly cible.</span><span class="sxs-lookup"><span data-stu-id="6d309-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="6d309-107">ID du fichier à partir duquel importer.</span><span class="sxs-lookup"><span data-stu-id="6d309-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="6d309-108">Portée de base zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="6d309-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="6d309-109">Reçoit le pointeur vers [IMetaDataImport2, Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface pour la portée indiquée.</span><span class="sxs-lookup"><span data-stu-id="6d309-109">Receives pointer to [IMetaDataImport2 Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d309-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="6d309-110">Return Value</span></span>  
 <span data-ttu-id="6d309-111">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="6d309-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d309-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="6d309-112">Requirements</span></span>  
 <span data-ttu-id="6d309-113">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="6d309-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d309-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d309-114">See also</span></span>

- [<span data-ttu-id="6d309-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="6d309-115">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="6d309-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="6d309-116">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="6d309-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="6d309-117">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
