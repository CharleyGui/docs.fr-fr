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
ms.openlocfilehash: a5b080443be94d5a298cc67591914d87470e6f48
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447184"
---
# <a name="getscope2-method"></a><span data-ttu-id="4ab6b-102">GetScope2, méthode</span><span class="sxs-lookup"><span data-stu-id="4ab6b-102">GetScope2 Method</span></span>
<span data-ttu-id="4ab6b-103">Obtient une étendue d’importation.</span><span class="sxs-lookup"><span data-stu-id="4ab6b-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ab6b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;   
```  
  
## <a name="parameters"></a><span data-ttu-id="4ab6b-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="4ab6b-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="4ab6b-106">ID de l’assembly cible.</span><span class="sxs-lookup"><span data-stu-id="4ab6b-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="4ab6b-107">ID du fichier à partir duquel effectuer l’importation.</span><span class="sxs-lookup"><span data-stu-id="4ab6b-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="4ab6b-108">Étendue de base zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="4ab6b-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="4ab6b-109">Reçoit un pointeur vers l’interface d' [interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) pour la portée indiquée.</span><span class="sxs-lookup"><span data-stu-id="4ab6b-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ab6b-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="4ab6b-110">Return Value</span></span>  
 <span data-ttu-id="4ab6b-111">Retourne S_OK si la méthode est réussie.</span><span class="sxs-lookup"><span data-stu-id="4ab6b-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ab6b-112">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="4ab6b-112">Requirements</span></span>  
 <span data-ttu-id="4ab6b-113">Requiert ALink. h.</span><span class="sxs-lookup"><span data-stu-id="4ab6b-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab6b-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4ab6b-114">See also</span></span>

- [<span data-ttu-id="4ab6b-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="4ab6b-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="4ab6b-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="4ab6b-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="4ab6b-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="4ab6b-117">ALink API</span></span>](index.md)
