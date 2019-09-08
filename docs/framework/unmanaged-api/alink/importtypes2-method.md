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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce09eca30e1edb9e1afc02216a07955a5fed4fd2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70787252"
---
# <a name="importtypes2-method"></a><span data-ttu-id="c3835-102">ImportTypes2, méthode</span><span class="sxs-lookup"><span data-stu-id="c3835-102">ImportTypes2 Method</span></span>
<span data-ttu-id="c3835-103">Initialise l’importation de types.</span><span class="sxs-lookup"><span data-stu-id="c3835-103">Initiates the import of types.</span></span> <span data-ttu-id="c3835-104">Appelez cette méthode pour commencer l’importation de types à partir de chaque étendue importée via la [méthode ImportFile](importfile-method.md).</span><span class="sxs-lookup"><span data-stu-id="c3835-104">Call this method to begin importing types from each scope imported via [ImportFile Method](importfile-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3835-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3835-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="c3835-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c3835-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="c3835-107">ID de l’assembly dans lequel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="c3835-107">ID of assembly into which to import.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="c3835-108">ID du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="c3835-108">ID of file to from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="c3835-109">Étendue de base zéro à partir de laquelle effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="c3835-109">Zero-based scope from which to import.</span></span>  
  
 `phEnum`  
 <span data-ttu-id="c3835-110">Reçoit un handle d’énumérateur pour les types dans l’étendue donnée.</span><span class="sxs-lookup"><span data-stu-id="c3835-110">Receives enumerator handle for the types in the given scope.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="c3835-111">Reçoit éventuellement l’interface d' [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="c3835-111">Optionally receives [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface.</span></span>  
  
 `pdwCountOfTypes`  
 <span data-ttu-id="c3835-112">Reçoit éventuellement le nombre de types dans l’étendue spécifiée.</span><span class="sxs-lookup"><span data-stu-id="c3835-112">Optionally receives count of types in the specified scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3835-113">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c3835-113">Return Value</span></span>  
 <span data-ttu-id="c3835-114">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="c3835-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3835-115">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="c3835-115">Requirements</span></span>  
 <span data-ttu-id="c3835-116">Requiert ALink. h</span><span class="sxs-lookup"><span data-stu-id="c3835-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3835-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c3835-117">See also</span></span>

- [<span data-ttu-id="c3835-118">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="c3835-118">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="c3835-119">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="c3835-119">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="c3835-120">API ALink</span><span class="sxs-lookup"><span data-stu-id="c3835-120">ALink API</span></span>](index.md)
