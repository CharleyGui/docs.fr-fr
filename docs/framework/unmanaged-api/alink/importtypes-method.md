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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f19dd114925ed1fd12bcc0056411c3e3d4181215
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70777098"
---
# <a name="importtypes-method"></a><span data-ttu-id="b2f86-102">ImportTypes, méthode</span><span class="sxs-lookup"><span data-stu-id="b2f86-102">ImportTypes Method</span></span>
<span data-ttu-id="b2f86-103">Lance l’importation de types à partir de chaque étendue importée via la [méthode ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="b2f86-103">Initiates the importing of types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2f86-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2f86-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="b2f86-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="b2f86-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="b2f86-106">ID de l’assembly dans lequel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="b2f86-106">ID of the assembly to import to.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="b2f86-107">ID du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="b2f86-107">ID of the file to import from.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="b2f86-108">Étendue de base zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="b2f86-108">Zero-based scope to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="b2f86-109">Reçoit un handle d’énumérateur pour les types de cette portée.</span><span class="sxs-lookup"><span data-stu-id="b2f86-109">Receives enumerator handle for the types in this scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="b2f86-110">Reçoit éventuellement l’interface d' [interface IMetaDataImport](../metadata/imetadataimport-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="b2f86-110">Optionally receives [IMetaDataImport Interface](../metadata/imetadataimport-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="b2f86-111">Reçoit éventuellement le nombre de types dans l’étendue indiquée.</span><span class="sxs-lookup"><span data-stu-id="b2f86-111">Optionally receives count of types in the indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2f86-112">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="b2f86-112">Return Value</span></span>  
 <span data-ttu-id="b2f86-113">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="b2f86-113">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2f86-114">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="b2f86-114">Requirements</span></span>  
 <span data-ttu-id="b2f86-115">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="b2f86-115">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2f86-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2f86-116">See also</span></span>

- [<span data-ttu-id="b2f86-117">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="b2f86-117">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="b2f86-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="b2f86-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="b2f86-119">API ALink</span><span class="sxs-lookup"><span data-stu-id="b2f86-119">ALink API</span></span>](index.md)
