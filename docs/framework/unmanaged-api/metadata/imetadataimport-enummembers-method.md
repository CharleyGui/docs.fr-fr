---
title: IMetaDataImport::EnumMembers, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumMembers
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumMembers
helpviewer_keywords:
- IMetaDataImport::EnumMembers method [.NET Framework metadata]
- EnumMembers method [.NET Framework metadata]
ms.assetid: 3fb8e178-342b-4c89-9bcf-f7f834e6cb77
topic_type:
- apiref
ms.openlocfilehash: cc3bc5140da0634b5172f6253de3de37bff487f1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84492032"
---
# <a name="imetadataimportenummembers-method"></a><span data-ttu-id="3d969-102">IMetaDataImport::EnumMembers, méthode</span><span class="sxs-lookup"><span data-stu-id="3d969-102">IMetaDataImport::EnumMembers Method</span></span>
<span data-ttu-id="3d969-103">Énumère les jetons MemberRef représentant les membres du type spécifié.</span><span class="sxs-lookup"><span data-stu-id="3d969-103">Enumerates MemberDef tokens representing members of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d969-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d969-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumMembers (
   [in, out]  HCORENUM    *phEnum,
   [in]  mdTypeDef   cl,
   [out] mdToken     rMembers[],
   [in]  ULONG       cMax,
   [out] ULONG       *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d969-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3d969-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="3d969-106">[in, out] Pointeur vers l’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="3d969-106">[in, out] A pointer to the enumerator.</span></span>  
  
 `cl`  
 <span data-ttu-id="3d969-107">dans Jeton TypeDef représentant le type dont les membres doivent être énumérés.</span><span class="sxs-lookup"><span data-stu-id="3d969-107">[in] A TypeDef token representing the type whose members are to be enumerated.</span></span>  
  
 `rMembers`  
 <span data-ttu-id="3d969-108">à Tableau utilisé pour contenir les jetons MemberDef.</span><span class="sxs-lookup"><span data-stu-id="3d969-108">[out] The array used to hold the MemberDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3d969-109">[in] Taille maximale du tableau `rMembers`.</span><span class="sxs-lookup"><span data-stu-id="3d969-109">[in] The maximum size of the `rMembers` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="3d969-110">à Nombre réel de jetons MemberDef retournés dans `rMembers` .</span><span class="sxs-lookup"><span data-stu-id="3d969-110">[out] The actual number of MemberDef tokens returned in `rMembers`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d969-111">Valeur renvoyée</span><span class="sxs-lookup"><span data-stu-id="3d969-111">Return Value</span></span>  
  
|<span data-ttu-id="3d969-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3d969-112">HRESULT</span></span>|<span data-ttu-id="3d969-113">Description</span><span class="sxs-lookup"><span data-stu-id="3d969-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="3d969-114">`EnumMembers`retourné avec succès.</span><span class="sxs-lookup"><span data-stu-id="3d969-114">`EnumMembers` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="3d969-115">Il n’y a aucun jeton MemberDef à énumérer.</span><span class="sxs-lookup"><span data-stu-id="3d969-115">There are no MemberDef tokens to enumerate.</span></span> <span data-ttu-id="3d969-116">Dans ce cas, `pcTokens` est égal à zéro.</span><span class="sxs-lookup"><span data-stu-id="3d969-116">In that case, `pcTokens` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d969-117">Remarques</span><span class="sxs-lookup"><span data-stu-id="3d969-117">Remarks</span></span>  
 <span data-ttu-id="3d969-118">Lors de l’énumération des collections de membres pour une classe, `EnumMembers` retourne uniquement les membres (champs et méthodes, mais **pas** les propriétés ou les événements) définis directement sur la classe.</span><span class="sxs-lookup"><span data-stu-id="3d969-118">When enumerating collections of members for a class, `EnumMembers` returns only members (fields and methods, but **not** properties or events) defined directly on the class.</span></span> <span data-ttu-id="3d969-119">Elle ne retourne pas les membres que la classe hérite, même si la classe fournit une implémentation pour ces membres hérités.</span><span class="sxs-lookup"><span data-stu-id="3d969-119">It does not return any members that the class inherits, even if the class provides an implementation for those inherited members.</span></span> <span data-ttu-id="3d969-120">Pour énumérer les membres hérités, l’appelant doit parcourir explicitement la chaîne d’héritage.</span><span class="sxs-lookup"><span data-stu-id="3d969-120">To enumerate inherited members, the caller must explicitly walk the inheritance chain.</span></span> <span data-ttu-id="3d969-121">Notez que les règles de la chaîne d’héritage peuvent varier selon le langage ou le compilateur qui a émis les métadonnées d’origine.</span><span class="sxs-lookup"><span data-stu-id="3d969-121">Note that the rules for the inheritance chain may vary depending on the language or compiler that emitted the original metadata.</span></span>

 <span data-ttu-id="3d969-122">Les propriétés et les événements ne sont pas énumérés par `EnumMembers` .</span><span class="sxs-lookup"><span data-stu-id="3d969-122">Properties and events are not enumerated by `EnumMembers`.</span></span> <span data-ttu-id="3d969-123">Pour les énumérer, utilisez [EnumProperties,](imetadataimport-enumproperties-method.md) ou [EnumEvents,](imetadataimport-enumevents-method.md).</span><span class="sxs-lookup"><span data-stu-id="3d969-123">To enumerate those, use [EnumProperties](imetadataimport-enumproperties-method.md) or [EnumEvents](imetadataimport-enumevents-method.md).</span></span>
  
## <a name="requirements"></a><span data-ttu-id="3d969-124">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3d969-124">Requirements</span></span>  
 <span data-ttu-id="3d969-125">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d969-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d969-126">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3d969-126">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d969-127">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3d969-127">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d969-128">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d969-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d969-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d969-129">See also</span></span>

- [<span data-ttu-id="3d969-130">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="3d969-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3d969-131">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="3d969-131">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
