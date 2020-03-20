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
ms.openlocfilehash: 40df78cdf99c2e0f53be9664f3f5c6386b6c6f93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179393"
---
# <a name="getscope2-method"></a><span data-ttu-id="2cfce-102">GetScope2, méthode</span><span class="sxs-lookup"><span data-stu-id="2cfce-102">GetScope2 Method</span></span>
<span data-ttu-id="2cfce-103">Obtient une portée d’importation.</span><span class="sxs-lookup"><span data-stu-id="2cfce-103">Gets an import scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cfce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cfce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScope2(  
    mdAssembly AssemblyID,  
    mdToken FileToken,  
    DWORD dwScope,  
    IMetaDataImport2** ppImportScope  
) PURE;
```  
  
## <a name="parameters"></a><span data-ttu-id="2cfce-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="2cfce-105">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="2cfce-106">ID de l’assemblage cible.</span><span class="sxs-lookup"><span data-stu-id="2cfce-106">ID of target assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="2cfce-107">ID de fichier à partir duquel importer.</span><span class="sxs-lookup"><span data-stu-id="2cfce-107">ID of file from which to import.</span></span>  
  
 `dwScope`  
 <span data-ttu-id="2cfce-108">Portée zéro à importer.</span><span class="sxs-lookup"><span data-stu-id="2cfce-108">Zero-based scope to import.</span></span>  
  
 `ppImportScope`  
 <span data-ttu-id="2cfce-109">Reçoit pointeur à [l’interface interface IMetaDataImport2](../metadata/imetadataimport2-interface.md) pour la portée indiquée.</span><span class="sxs-lookup"><span data-stu-id="2cfce-109">Receives pointer to [IMetaDataImport2 Interface](../metadata/imetadataimport2-interface.md) interface for indicated scope.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cfce-110">Valeur de retour</span><span class="sxs-lookup"><span data-stu-id="2cfce-110">Return Value</span></span>  
 <span data-ttu-id="2cfce-111">Retourne S_OK si la méthode réussit.</span><span class="sxs-lookup"><span data-stu-id="2cfce-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cfce-112">Spécifications</span><span class="sxs-lookup"><span data-stu-id="2cfce-112">Requirements</span></span>  
 <span data-ttu-id="2cfce-113">Nécessite alink.h.</span><span class="sxs-lookup"><span data-stu-id="2cfce-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cfce-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cfce-114">See also</span></span>

- [<span data-ttu-id="2cfce-115">IALink2, interface</span><span class="sxs-lookup"><span data-stu-id="2cfce-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="2cfce-116">IALink, interface</span><span class="sxs-lookup"><span data-stu-id="2cfce-116">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="2cfce-117">API ALink</span><span class="sxs-lookup"><span data-stu-id="2cfce-117">ALink API</span></span>](index.md)
