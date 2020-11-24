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
ms.openlocfilehash: e8c6fd7dca13afe7504e447caca9a217c8136c27
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684523"
---
# <a name="getscope2-method"></a><span data-ttu-id="c97d9-102">GetScope2, méthode</span><span class="sxs-lookup"><span data-stu-id="c97d9-102">GetScope2 Method</span></span>

<span data-ttu-id="c97d9-103">Obtient une étendue d’importation.</span><span class="sxs-lookup"><span data-stu-id="c97d9-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c97d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c97d9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="c97d9-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c97d9-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="c97d9-106">ID de l’assembly cible.</span><span class="sxs-lookup"><span data-stu-id="c97d9-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c97d9-107">ID du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="c97d9-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="c97d9-108">Étendue de base zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="c97d9-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="c97d9-109">Reçoit un pointeur vers l’interface d' [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) pour la portée indiquée.</span><span class="sxs-lookup"><span data-stu-id="c97d9-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c97d9-110">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="c97d9-110">Return Value</span></span>  

 <span data-ttu-id="c97d9-111">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c97d9-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c97d9-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c97d9-112">Requirements</span></span>  

 <span data-ttu-id="c97d9-113">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="c97d9-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c97d9-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c97d9-114">See also</span></span>

- [<span data-ttu-id="c97d9-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="c97d9-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c97d9-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="c97d9-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c97d9-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="c97d9-117">ALink API</span></span>](index.md)
