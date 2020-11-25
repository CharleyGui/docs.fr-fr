---
title: ImportTypes2, méthode
ms.date: 03/30/2017
api_name:
- IALink2.ImportTypes2
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes2
helpviewer_keywords:
- ImportTypes2 method
ms.assetid: 32f3ba58-9695-41e9-ba58-fd19e45ed396
topic_type:
- apiref
ms.openlocfilehash: 2ec7708edd86b9f2656d0eee434992c3b73200ca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705044"
---
# <a name="importtypes2-method"></a><span data-ttu-id="77124-102">ImportTypes2, méthode</span><span class="sxs-lookup"><span data-stu-id="77124-102">ImportTypes2 Method</span></span>

<span data-ttu-id="77124-103">Initialise l’importation de types.</span><span class="sxs-lookup"><span data-stu-id="77124-103">Initiates the import of types.</span></span> <span data-ttu-id="77124-104">Appelez cette méthode pour commencer l’importation de types à partir de chaque étendue importée via la [méthode ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="77124-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77124-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77124-105">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport2** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="77124-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="77124-106">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="77124-107">ID de l’assembly dans lequel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="77124-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="77124-108">ID du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="77124-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="77124-109">Étendue de base zéro à partir de laquelle effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="77124-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="77124-110">Reçoit un handle d’énumérateur pour les types dans l’étendue donnée.</span><span class="sxs-lookup"><span data-stu-id="77124-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="77124-111">Reçoit éventuellement l’interface d' [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="77124-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="77124-112">Reçoit éventuellement le nombre de types dans l’étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="77124-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="77124-113">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="77124-113">Return Value</span></span>  

 <span data-ttu-id="77124-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="77124-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77124-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="77124-115">Requirements</span></span>  

 <span data-ttu-id="77124-116">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="77124-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77124-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77124-117">See also</span></span>

- [<span data-ttu-id="77124-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="77124-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="77124-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="77124-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="77124-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="77124-120">ALink API</span></span>](index.md)
