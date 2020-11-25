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
ms.openlocfilehash: d4d3ba5713398876b55c072f0cda7eb5d599c4d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729280"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="0efd6-102">IMetaDataImport::GetParamForMethodIndex, méthode</span><span class="sxs-lookup"><span data-stu-id="0efd6-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>

<span data-ttu-id="0efd6-103">Obtient le jeton qui représente un paramètre spécifié de la méthode représentée par le jeton MethodDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="0efd6-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0efd6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0efd6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0efd6-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="0efd6-105">Parameters</span></span>  

 `md`  
 <span data-ttu-id="0efd6-106">dans Jeton qui représente la méthode pour laquelle retourner le jeton de paramètre.</span><span class="sxs-lookup"><span data-stu-id="0efd6-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="0efd6-107">dans Position ordinale dans la liste de paramètres où le paramètre demandé se produit.</span><span class="sxs-lookup"><span data-stu-id="0efd6-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="0efd6-108">Les paramètres sont numérotés à partir de un, avec la valeur de retour de la méthode dans la position zéro.</span><span class="sxs-lookup"><span data-stu-id="0efd6-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="0efd6-109">à Pointeur vers un jeton ParamDef qui représente le paramètre demandé.</span><span class="sxs-lookup"><span data-stu-id="0efd6-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0efd6-110">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="0efd6-110">Requirements</span></span>  

 <span data-ttu-id="0efd6-111">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0efd6-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0efd6-112">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0efd6-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0efd6-113">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0efd6-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0efd6-114">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0efd6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0efd6-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0efd6-115">See also</span></span>

- [<span data-ttu-id="0efd6-116">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="0efd6-116">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0efd6-117">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="0efd6-117">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
