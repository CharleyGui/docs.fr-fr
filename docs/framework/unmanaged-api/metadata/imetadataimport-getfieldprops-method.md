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
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177246"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="d4563-102">IMetaDataImport::GetFieldProps, méthode</span><span class="sxs-lookup"><span data-stu-id="d4563-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="d4563-103">Obtient les métadonnées associées au champ référencé par le jeton FieldDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="d4563-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4563-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4563-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="d4563-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="d4563-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="d4563-106">[dans] Un jeton FieldDef qui représente le champ pour obtenir des métadonnées associées pour.</span><span class="sxs-lookup"><span data-stu-id="d4563-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="d4563-107">[out] Un pointeur à un jeton TypeDef qui représente le type de la classe que le champ appartient à.</span><span class="sxs-lookup"><span data-stu-id="d4563-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="d4563-108">[out] Le nom du champ.</span><span class="sxs-lookup"><span data-stu-id="d4563-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="d4563-109">[dans] La taille en caractères larges de la mémoire tampon pour *szField*.</span><span class="sxs-lookup"><span data-stu-id="d4563-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="d4563-110">[out] La taille réelle du tampon retourné.</span><span class="sxs-lookup"><span data-stu-id="d4563-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="d4563-111">[out] Drapeaux associés aux métadonnées du terrain.</span><span class="sxs-lookup"><span data-stu-id="d4563-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="d4563-112">[dans] Un pointeur à la valeur des métadonnées binaires qui décrit le champ.</span><span class="sxs-lookup"><span data-stu-id="d4563-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="d4563-113">[out] La taille dans `ppvSigBlob`les octets de .</span><span class="sxs-lookup"><span data-stu-id="d4563-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="d4563-114">[out] Un drapeau qui spécifie le type de valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="d4563-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="d4563-115">[out] Une valeur constante pour le terrain.</span><span class="sxs-lookup"><span data-stu-id="d4563-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="d4563-116">[out] La taille en `ppValue`chars de , ou zéro si aucune chaîne n’existe.</span><span class="sxs-lookup"><span data-stu-id="d4563-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4563-117">Spécifications</span><span class="sxs-lookup"><span data-stu-id="d4563-117">Requirements</span></span>  
 <span data-ttu-id="d4563-118">**Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4563-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4563-119">**En-tête:** Cor.h (en)</span><span class="sxs-lookup"><span data-stu-id="d4563-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d4563-120">**Bibliothèque:** Inclus comme une ressource dans MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d4563-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d4563-121">**.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4563-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4563-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d4563-122">See also</span></span>

- [<span data-ttu-id="d4563-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="d4563-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="d4563-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="d4563-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
