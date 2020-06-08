---
title: IMetaDataImport::ResolveTypeRef, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.ResolveTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::ResolveTypeRef
helpviewer_keywords:
- ResolveTypeRef method [.NET Framework metadata]
- IMetaDataImport::ResolveTypeRef method [.NET Framework metadata]
ms.assetid: 556bccfb-61bc-4761-b1d5-de4b1c18a38f
topic_type:
- apiref
ms.openlocfilehash: f55af87e21b48430807166cb03e1d41271e830a1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503430"
---
# <a name="imetadataimportresolvetyperef-method"></a><span data-ttu-id="df510-102">IMetaDataImport::ResolveTypeRef, méthode</span><span class="sxs-lookup"><span data-stu-id="df510-102">IMetaDataImport::ResolveTypeRef Method</span></span>
<span data-ttu-id="df510-103">Résout une <xref:System.Type> référence représentée par le jeton TypeRef spécifié.</span><span class="sxs-lookup"><span data-stu-id="df510-103">Resolves a <xref:System.Type> reference represented by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df510-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df510-104">Syntax</span></span>  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df510-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="df510-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="df510-106">dans Jeton de métadonnées TypeRef pour lequel retourner les informations de type référencées.</span><span class="sxs-lookup"><span data-stu-id="df510-106">[in] The TypeRef metadata token to return the referenced type information for.</span></span>  
  
 `riid`  
 <span data-ttu-id="df510-107">dans IID de l’interface à retourner `ppIScope` .</span><span class="sxs-lookup"><span data-stu-id="df510-107">[in] The IID of the interface to return in `ppIScope`.</span></span> <span data-ttu-id="df510-108">En général, il s’agit de IID_IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="df510-108">Typically, this would be IID_IMetaDataImport.</span></span>  
  
 `ppIScope`  
 <span data-ttu-id="df510-109">à Interface avec la portée de module dans laquelle le type référencé est défini.</span><span class="sxs-lookup"><span data-stu-id="df510-109">[out] An interface to the module scope in which the referenced type is defined.</span></span>  
  
 `ptd`  
 <span data-ttu-id="df510-110">à Pointeur vers un jeton TypeDef qui représente le type référencé.</span><span class="sxs-lookup"><span data-stu-id="df510-110">[out] A pointer to a TypeDef token that represents the referenced type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df510-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="df510-111">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="df510-112">N’utilisez pas cette méthode si plusieurs domaines d’application sont chargés.</span><span class="sxs-lookup"><span data-stu-id="df510-112">Do not use this method if multiple application domains are loaded.</span></span> <span data-ttu-id="df510-113">La méthode ne respecte pas les limites du domaine d’application.</span><span class="sxs-lookup"><span data-stu-id="df510-113">The method does not respect application domain boundaries.</span></span> <span data-ttu-id="df510-114">Si plusieurs versions d’un assembly sont chargées et qu’elles contiennent le même type avec le même espace de noms, la méthode retourne la portée de module du premier type qu’elle trouve.</span><span class="sxs-lookup"><span data-stu-id="df510-114">If multiple versions of an assembly are loaded, and they contain the same type with the same namespace, the method returns the module scope of the first type it finds.</span></span>  
  
 <span data-ttu-id="df510-115">La `ResolveTypeRef` méthode recherche la définition de type dans d’autres modules.</span><span class="sxs-lookup"><span data-stu-id="df510-115">The `ResolveTypeRef` method searches for the type definition in other modules.</span></span> <span data-ttu-id="df510-116">Si la définition de type est trouvée, `ResolveTypeRef` retourne une interface à cette portée de module, ainsi que le jeton typedef pour le type.</span><span class="sxs-lookup"><span data-stu-id="df510-116">If the type definition is found, `ResolveTypeRef` returns an interface to that module scope as well as the TypeDef token for the type.</span></span>  
  
 <span data-ttu-id="df510-117">Si la référence de type à résoudre a une portée de résolution de AssemblyRef, la `ResolveTypeRef` méthode recherche une correspondance uniquement dans les portées de métadonnées qui ont déjà été ouvertes avec des appels à la méthode [IMetaDataDispenser :: OpenScope](imetadatadispenser-openscope-method.md) ou à la méthode [IMetaDataDispenser :: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="df510-117">If the type reference to be resolved has a resolution scope of AssemblyRef, the `ResolveTypeRef` method searches for a match only in the metadata scopes that have already been opened with calls to either the [IMetaDataDispenser::OpenScope](imetadatadispenser-openscope-method.md) method or the [IMetaDataDispenser::OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) method.</span></span> <span data-ttu-id="df510-118">Cela est dû au fait que `ResolveTypeRef` ne peut pas déterminer à partir de la portée AssemblyRef sur le disque ou dans le global assembly cache l’assembly est stocké.</span><span class="sxs-lookup"><span data-stu-id="df510-118">This is because `ResolveTypeRef` cannot determine from only the AssemblyRef scope where on disk or in the global assembly cache the assembly is stored.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df510-119">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df510-119">Requirements</span></span>  
 <span data-ttu-id="df510-120">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df510-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df510-121">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="df510-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="df510-122">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="df510-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="df510-123">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df510-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df510-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df510-124">See also</span></span>

- [<span data-ttu-id="df510-125">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="df510-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="df510-126">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="df510-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
