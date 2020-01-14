---
title: IMetaDataTables::GetNextUserString, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
ms.openlocfilehash: 6522dbc8e49d612fc4c0d9597a9b5f12edb2cfe1
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937785"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="d4795-102">IMetaDataTables::GetNextUserString, méthode</span><span class="sxs-lookup"><span data-stu-id="d4795-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="d4795-103">Obtient l’index de la ligne qui contient la chaîne codée en dur suivante dans la colonne de table actuelle.</span><span class="sxs-lookup"><span data-stu-id="d4795-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4795-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4795-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4795-105">Parameters</span><span class="sxs-lookup"><span data-stu-id="d4795-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="d4795-106">dans Valeur d’index de la colonne de chaîne actuelle.</span><span class="sxs-lookup"><span data-stu-id="d4795-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="d4795-107">à Pointeur vers l’index de ligne de la chaîne suivante dans la colonne.</span><span class="sxs-lookup"><span data-stu-id="d4795-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4795-108">Notes</span><span class="sxs-lookup"><span data-stu-id="d4795-108">Remarks</span></span>  
 <span data-ttu-id="d4795-109">Nous déconseillons l’utilisation de cette méthode, car elle ne retourne pas de résultats cohérents.</span><span class="sxs-lookup"><span data-stu-id="d4795-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="d4795-110">Pour plus d’informations sur la table GUID, consultez la documentation de Common Language Infrastructure (CLI), en particulier « Partition II : définition et sémantique des métadonnées ».</span><span class="sxs-lookup"><span data-stu-id="d4795-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="d4795-111">La documentation est disponible en ligne. consultez [les C# normes ECMA et Common Language Infrastructure](../../../standard/components.md#applicable-standards) [standard et ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="d4795-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4795-112">Configuration requise pour</span><span class="sxs-lookup"><span data-stu-id="d4795-112">Requirements</span></span>  
 <span data-ttu-id="d4795-113">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4795-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4795-114">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="d4795-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4795-115">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="d4795-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4795-116">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4795-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4795-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4795-117">See also</span></span>

- [<span data-ttu-id="d4795-118">IMetaDataTables, interface</span><span class="sxs-lookup"><span data-stu-id="d4795-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="d4795-119">IMetaDataTables2, interface</span><span class="sxs-lookup"><span data-stu-id="d4795-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
