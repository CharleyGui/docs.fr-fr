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
ms.openlocfilehash: 8dae903ab76ab83ac0818c4bc4a76e81094bdf65
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445666"
---
# <a name="importtypes2-method"></a><span data-ttu-id="a1ed8-102">ImportTypes2, méthode</span><span class="sxs-lookup"><span data-stu-id="a1ed8-102">ImportTypes2 Method</span></span>
<span data-ttu-id="a1ed8-103">Initialise l’importation de types.</span><span class="sxs-lookup"><span data-stu-id="a1ed8-103">Initiates the import of types.</span></span> <span data-ttu-id="a1ed8-104">Appelez cette méthode pour commencer l’importation de types à partir de chaque étendue importée via la [méthode ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="a1ed8-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ed8-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1ed8-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a1ed8-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="a1ed8-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a1ed8-107">ID de l’assembly dans lequel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="a1ed8-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a1ed8-108">ID du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="a1ed8-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="a1ed8-109">Étendue de base zéro à partir de laquelle effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="a1ed8-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="a1ed8-110">Reçoit un handle d’énumérateur pour les types dans l’étendue donnée.</span><span class="sxs-lookup"><span data-stu-id="a1ed8-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="a1ed8-111">Reçoit éventuellement l’interface d' [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a1ed8-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="a1ed8-112">Reçoit éventuellement le nombre de types dans l’étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a1ed8-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1ed8-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="a1ed8-113">Return Value</span></span>  
 <span data-ttu-id="a1ed8-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="a1ed8-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ed8-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="a1ed8-115">Requirements</span></span>  
 <span data-ttu-id="a1ed8-116">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="a1ed8-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1ed8-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1ed8-117">See also</span></span>

- [<span data-ttu-id="a1ed8-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="a1ed8-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a1ed8-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="a1ed8-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a1ed8-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="a1ed8-120">ALink API</span></span>](index.md)
