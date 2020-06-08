---
title: IMetaDataImport::GetNestedClassProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 82cf5e14520f0e677c2d274cf013d8a0020e8fa2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503534"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="8c92d-102">IMetaDataImport::GetNestedClassProps, méthode</span><span class="sxs-lookup"><span data-stu-id="8c92d-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="8c92d-103">Obtient le jeton TypeDef pour le parent <xref:System.Type> du type imbriqué spécifié.</span><span class="sxs-lookup"><span data-stu-id="8c92d-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c92d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8c92d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c92d-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="8c92d-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="8c92d-106">dans Jeton TypeDef représentant le <xref:System.Type> pour lequel retourner le jeton de la classe parente.</span><span class="sxs-lookup"><span data-stu-id="8c92d-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="8c92d-107">à Pointeur vers le jeton TypeDef pour le <xref:System.Type> qui `tdNestedClass` est imbriqué dans.</span><span class="sxs-lookup"><span data-stu-id="8c92d-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c92d-108">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="8c92d-108">Requirements</span></span>  
 <span data-ttu-id="8c92d-109">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c92d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c92d-110">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="8c92d-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="8c92d-111">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="8c92d-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="8c92d-112">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c92d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c92d-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8c92d-113">See also</span></span>

- [<span data-ttu-id="8c92d-114">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="8c92d-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="8c92d-115">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="8c92d-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
