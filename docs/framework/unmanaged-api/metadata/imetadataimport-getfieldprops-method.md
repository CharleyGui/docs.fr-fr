---
title: IMetaDataImport::GetFieldProps, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 458a90bc47711d9f831805faa8468a49f3e0d305
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703994"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="43f90-102">IMetaDataImport::GetFieldProps, méthode</span><span class="sxs-lookup"><span data-stu-id="43f90-102">IMetaDataImport::GetFieldProps Method</span></span>

<span data-ttu-id="43f90-103">Obtient les métadonnées associées au champ référencé par le jeton FieldDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="43f90-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f90-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43f90-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43f90-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="43f90-105">Parameters</span></span>  

 `mb`  
 <span data-ttu-id="43f90-106">dans Jeton FieldDef qui représente le champ pour lequel obtenir les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="43f90-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="43f90-107">à Pointeur vers un jeton TypeDef qui représente le type de la classe à laquelle le champ appartient.</span><span class="sxs-lookup"><span data-stu-id="43f90-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="43f90-108">à Nom du champ.</span><span class="sxs-lookup"><span data-stu-id="43f90-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="43f90-109">dans Taille en caractères larges de la mémoire tampon pour *szField*.</span><span class="sxs-lookup"><span data-stu-id="43f90-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="43f90-110">à Taille réelle de la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="43f90-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="43f90-111">à Indicateurs associés aux métadonnées du champ.</span><span class="sxs-lookup"><span data-stu-id="43f90-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="43f90-112">dans Pointeur vers la valeur de métadonnées binaires qui décrit le champ.</span><span class="sxs-lookup"><span data-stu-id="43f90-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="43f90-113">à Taille en octets de `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="43f90-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="43f90-114">à Indicateur qui spécifie le type de valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="43f90-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="43f90-115">à Valeur constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="43f90-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="43f90-116">à Taille en caractères de `ppValue` , ou zéro si aucune chaîne n’existe.</span><span class="sxs-lookup"><span data-stu-id="43f90-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43f90-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="43f90-117">Requirements</span></span>  

 <span data-ttu-id="43f90-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43f90-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43f90-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="43f90-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43f90-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43f90-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43f90-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43f90-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f90-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="43f90-122">See also</span></span>

- [<span data-ttu-id="43f90-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="43f90-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="43f90-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="43f90-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
