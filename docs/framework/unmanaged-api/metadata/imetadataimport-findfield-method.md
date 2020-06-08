---
title: IMetaDataImport::FindField, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindField
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindField
helpviewer_keywords:
- IMetaDataImport::FindField method [.NET Framework metadata]
- FindField method [.NET Framework metadata]
ms.assetid: 38cd4e16-fbb2-471c-aa73-ac51a1931ad2
topic_type:
- apiref
ms.openlocfilehash: 11ea6e468909ea42e38bdc7b76c60c460c98025e
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503664"
---
# <a name="imetadataimportfindfield-method"></a><span data-ttu-id="8cbba-102">IMetaDataImport::FindField, méthode</span><span class="sxs-lookup"><span data-stu-id="8cbba-102">IMetaDataImport::FindField Method</span></span>
<span data-ttu-id="8cbba-103">Obtient un pointeur vers le jeton FieldDef pour le champ qui est entouré par le spécifié <xref:System.Type> et qui a le nom et la signature de métadonnées spécifiés.</span><span class="sxs-lookup"><span data-stu-id="8cbba-103">Gets a pointer to the FieldDef token for the field that is enclosed by the specified <xref:System.Type> and that has the specified name and metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cbba-104">Syntax</span></span>  
  
```cpp  
HRESULT FindField (  
   [in]  mdTypeDef         td,  
   [in]  LPCWSTR           szName,  
   [in]  PCCOR_SIGNATURE   pvSigBlob,  
   [in]  ULONG             cbSigBlob,  
   [out] mdFieldDef        *pmb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cbba-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8cbba-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="8cbba-106">dans Jeton TypeDef pour la classe ou l’interface qui englobe le champ à rechercher.</span><span class="sxs-lookup"><span data-stu-id="8cbba-106">[in] The TypeDef token for the class or interface that encloses the field to search for.</span></span> <span data-ttu-id="8cbba-107">Si cette valeur est `mdTokenNil` , la recherche est effectuée pour une variable globale.</span><span class="sxs-lookup"><span data-stu-id="8cbba-107">If this value is `mdTokenNil`, the lookup is done for a global variable.</span></span>  
  
 `szName`  
 <span data-ttu-id="8cbba-108">dans Nom du champ à rechercher.</span><span class="sxs-lookup"><span data-stu-id="8cbba-108">[in] The name of the field to search for.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="8cbba-109">dans Pointeur vers la signature de métadonnées binaires du champ.</span><span class="sxs-lookup"><span data-stu-id="8cbba-109">[in] A pointer to the binary metadata signature of the field.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="8cbba-110">dans Taille en octets de `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="8cbba-110">[in] The size in bytes of `pvSigBlob`.</span></span>  
  
 `pmb`  
 <span data-ttu-id="8cbba-111">à Pointeur vers le jeton FieldDef correspondant.</span><span class="sxs-lookup"><span data-stu-id="8cbba-111">[out] A pointer to the matching FieldDef token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cbba-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="8cbba-112">Remarks</span></span>  
 <span data-ttu-id="8cbba-113">Vous spécifiez le champ à l’aide de sa classe englobante ou de son interface ( `td` ), son nom ( `szName` ) et éventuellement sa signature ( `pvSigBlob` ).</span><span class="sxs-lookup"><span data-stu-id="8cbba-113">You specify the field using its enclosing class or interface (`td`), its name (`szName`), and optionally its signature (`pvSigBlob`).</span></span>  
  
 <span data-ttu-id="8cbba-114">La signature transmise à `FindField` doit avoir été générée dans l’étendue actuelle, car les signatures sont liées à une portée particulière.</span><span class="sxs-lookup"><span data-stu-id="8cbba-114">The signature passed to `FindField` must have been generated in the current scope, because signatures are bound to a particular scope.</span></span> <span data-ttu-id="8cbba-115">Une signature peut incorporer un jeton qui identifie la classe englobante ou le type valeur.</span><span class="sxs-lookup"><span data-stu-id="8cbba-115">A signature can embed a token that identifies the enclosing class or value type.</span></span> <span data-ttu-id="8cbba-116">(Le jeton est un index dans la table TypeDef locale).</span><span class="sxs-lookup"><span data-stu-id="8cbba-116">(The token is an index into the local TypeDef table).</span></span> <span data-ttu-id="8cbba-117">Vous ne pouvez pas générer une signature au moment de l’exécution en dehors du contexte de la portée actuelle et utiliser cette signature comme entrée pour `FindField` .</span><span class="sxs-lookup"><span data-stu-id="8cbba-117">You cannot build a run-time signature outside the context of the current scope and use that signature as input to `FindField`.</span></span>  
  
 <span data-ttu-id="8cbba-118">`FindField`recherche uniquement les champs qui ont été définis directement dans la classe ou l’interface ; il ne trouve pas les champs hérités.</span><span class="sxs-lookup"><span data-stu-id="8cbba-118">`FindField` finds only fields that were defined directly in the class or interface; it does not find inherited fields.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cbba-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8cbba-119">Requirements</span></span>  
 <span data-ttu-id="8cbba-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cbba-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cbba-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8cbba-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8cbba-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8cbba-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8cbba-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cbba-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbba-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8cbba-124">See also</span></span>

- [<span data-ttu-id="8cbba-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8cbba-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8cbba-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="8cbba-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
