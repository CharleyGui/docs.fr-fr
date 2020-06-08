---
title: IMetaDataImport2, interface
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: fe9e87618291218a41e52f80198ce9068c9c56e2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490392"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="3f28d-102">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="3f28d-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="3f28d-103">Étend l’interface [IMetaDataImport](imetadataimport-interface.md) pour offrir la possibilité d’utiliser des types génériques.</span><span class="sxs-lookup"><span data-stu-id="3f28d-103">Extends the [IMetaDataImport](imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3f28d-104">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3f28d-104">Methods</span></span>  
  
|<span data-ttu-id="3f28d-105">Méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-105">Method</span></span>|<span data-ttu-id="3f28d-106">Description</span><span class="sxs-lookup"><span data-stu-id="3f28d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3f28d-107">EnumGenericParamConstraints, méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-107">EnumGenericParamConstraints Method</span></span>](imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="3f28d-108">Obtient un énumérateur pour un tableau de contraintes de paramètres génériques associées au paramètre générique représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="3f28d-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="3f28d-109">EnumGenericParams, méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-109">EnumGenericParams Method</span></span>](imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="3f28d-110">Obtient un énumérateur pour un tableau de jetons de paramètres génériques associés au jeton TypeDef ou MethodDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="3f28d-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="3f28d-111">EnumMethodSpecs, méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-111">EnumMethodSpecs Method</span></span>](imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="3f28d-112">Obtient un énumérateur pour un tableau de jetons MethodSpec associés au jeton MethodDef ou MemberRef spécifié.</span><span class="sxs-lookup"><span data-stu-id="3f28d-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="3f28d-113">GetGenericParamConstraintProps, méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-113">GetGenericParamConstraintProps Method</span></span>](imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="3f28d-114">Obtient les métadonnées associées à la contrainte de paramètre générique représentée par le jeton de contrainte spécifié.</span><span class="sxs-lookup"><span data-stu-id="3f28d-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="3f28d-115">GetGenericParamProps, méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-115">GetGenericParamProps Method</span></span>](imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="3f28d-116">Obtient les métadonnées associées au paramètre générique représenté par le jeton spécifié.</span><span class="sxs-lookup"><span data-stu-id="3f28d-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="3f28d-117">GetMethodSpecProps, méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-117">GetMethodSpecProps Method</span></span>](imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="3f28d-118">Obtient la signature de métadonnées de la méthode référencée par le jeton MethodSpec spécifié.</span><span class="sxs-lookup"><span data-stu-id="3f28d-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="3f28d-119">GetPEKind, méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-119">GetPEKind Method</span></span>](imetadataimport2-getpekind-method.md)|<span data-ttu-id="3f28d-120">Obtient une valeur identifiant la nature du code dans un fichier exécutable portable (PE), généralement un fichier DLL ou EXE, défini dans la portée des métadonnées actuelle.</span><span class="sxs-lookup"><span data-stu-id="3f28d-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="3f28d-121">GetVersionString, méthode</span><span class="sxs-lookup"><span data-stu-id="3f28d-121">GetVersionString Method</span></span>](imetadataimport2-getversionstring-method.md)|<span data-ttu-id="3f28d-122">Obtient le numéro de version du runtime qui a été utilisé pour générer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="3f28d-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f28d-123">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="3f28d-123">Requirements</span></span>  
 <span data-ttu-id="3f28d-124">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f28d-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f28d-125">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3f28d-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f28d-126">**Bibliothèque :** Utilisé en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3f28d-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f28d-127">**Versions de .NET Framework :**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f28d-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f28d-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f28d-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="3f28d-129">Interfaces de métadonnées</span><span class="sxs-lookup"><span data-stu-id="3f28d-129">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="3f28d-130">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="3f28d-130">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
