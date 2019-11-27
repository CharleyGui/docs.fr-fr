---
title: ImportTypes, méthode
ms.date: 03/30/2017
api_name:
- IALink.ImportTypes
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- ImportTypes
helpviewer_keywords:
- ImportTypes method
ms.assetid: 351d4b4c-c939-486d-9471-51914a55f471
topic_type:
- apiref
ms.openlocfilehash: 76d2b163f959111923bffb1348890f6fbb29828e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445681"
---
# <a name="importtypes-method"></a><span data-ttu-id="56c66-102">ImportTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="56c66-102">ImportTypes Method</span></span>
<span data-ttu-id="56c66-103">Lance l’importation de types à partir de chaque étendue importée via la [méthode ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="56c66-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56c66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56c66-104">Syntax</span></span>  
  
```cpp  
HRESULT ImportTypes(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    HALINKENUM* phEnum,  
    IMetaDataImport** ppImportScope,  
    DWORD* pdwCountOfTypes  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="56c66-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="56c66-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="56c66-106">ID de l’assembly dans lequel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="56c66-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="56c66-107">ID du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="56c66-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="56c66-108">Étendue de base zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="56c66-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="56c66-109">Reçoit un handle d’énumérateur pour les types de cette portée.</span><span class="sxs-lookup"><span data-stu-id="56c66-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="56c66-110">Reçoit éventuellement l’interface d' [interface IMetaDataImport](../metadata/imetadataimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="56c66-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="56c66-111">Reçoit éventuellement le nombre de types dans l’étendue indiquée.</span><span class="sxs-lookup"><span data-stu-id="56c66-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56c66-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="56c66-112">Return Value</span></span>  
 <span data-ttu-id="56c66-113">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="56c66-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56c66-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="56c66-114">Requirements</span></span>  
 <span data-ttu-id="56c66-115">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="56c66-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c66-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="56c66-116">See also</span></span>

- [<span data-ttu-id="56c66-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="56c66-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="56c66-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="56c66-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="56c66-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="56c66-119">ALink API</span></span>](index.md)
