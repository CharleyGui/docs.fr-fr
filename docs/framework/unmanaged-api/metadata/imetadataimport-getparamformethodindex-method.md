---
title: IMetaDataImport::GetParamForMethodIndex, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdb3def9574f4442a22b370323dfdf044170542b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778944"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="bf8b4-102">IMetaDataImport::GetParamForMethodIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="bf8b4-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="bf8b4-103">Obtient le jeton qui représente un paramètre spécifié de la méthode représentée par le jeton MethodDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="bf8b4-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf8b4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bf8b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf8b4-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="bf8b4-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="bf8b4-106">[in] Un jeton qui représente la méthode pour retourner le jeton de paramètre.</span><span class="sxs-lookup"><span data-stu-id="bf8b4-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="bf8b4-107">[in] La position ordinale dans la liste de paramètres où le paramètre demandé se produit.</span><span class="sxs-lookup"><span data-stu-id="bf8b4-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="bf8b4-108">Les paramètres sont numérotées à partir de l’autre, avec la valeur de retour dans la position zéro.</span><span class="sxs-lookup"><span data-stu-id="bf8b4-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="bf8b4-109">[out] Pointeur vers un jeton ParamDef qui représente le paramètre demandé.</span><span class="sxs-lookup"><span data-stu-id="bf8b4-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf8b4-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="bf8b4-110">Requirements</span></span>  
 <span data-ttu-id="bf8b4-111">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf8b4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf8b4-112">**En-tête :** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bf8b4-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bf8b4-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bf8b4-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bf8b4-114">**Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf8b4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf8b4-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bf8b4-115">See also</span></span>

- [<span data-ttu-id="bf8b4-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="bf8b4-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bf8b4-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="bf8b4-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
