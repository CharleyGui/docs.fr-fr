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
ms.openlocfilehash: 2bd05b49c3d51ac13865997910c99cc0cd5ca2d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491242"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="019fd-102">IMetaDataImport::GetFieldProps, méthode</span><span class="sxs-lookup"><span data-stu-id="019fd-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="019fd-103">Obtient les métadonnées associées au champ référencé par le jeton FieldDef spécifié.</span><span class="sxs-lookup"><span data-stu-id="019fd-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="019fd-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="019fd-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="019fd-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="019fd-106">dans Jeton FieldDef qui représente le champ pour lequel obtenir les métadonnées associées.</span><span class="sxs-lookup"><span data-stu-id="019fd-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="019fd-107">à Pointeur vers un jeton TypeDef qui représente le type de la classe à laquelle le champ appartient.</span><span class="sxs-lookup"><span data-stu-id="019fd-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="019fd-108">à Nom du champ.</span><span class="sxs-lookup"><span data-stu-id="019fd-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="019fd-109">dans Taille en caractères larges de la mémoire tampon pour *szField*.</span><span class="sxs-lookup"><span data-stu-id="019fd-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="019fd-110">à Taille réelle de la mémoire tampon retournée.</span><span class="sxs-lookup"><span data-stu-id="019fd-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="019fd-111">à Indicateurs associés aux métadonnées du champ.</span><span class="sxs-lookup"><span data-stu-id="019fd-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="019fd-112">dans Pointeur vers la valeur de métadonnées binaires qui décrit le champ.</span><span class="sxs-lookup"><span data-stu-id="019fd-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="019fd-113">à Taille en octets de `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="019fd-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="019fd-114">à Indicateur qui spécifie le type de valeur du champ.</span><span class="sxs-lookup"><span data-stu-id="019fd-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="019fd-115">à Valeur constante pour le champ.</span><span class="sxs-lookup"><span data-stu-id="019fd-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="019fd-116">à Taille en caractères de `ppValue` , ou zéro si aucune chaîne n’existe.</span><span class="sxs-lookup"><span data-stu-id="019fd-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="019fd-117">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="019fd-117">Requirements</span></span>  
 <span data-ttu-id="019fd-118">**Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="019fd-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="019fd-119">**En-tête :** Cor. h</span><span class="sxs-lookup"><span data-stu-id="019fd-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="019fd-120">**Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="019fd-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="019fd-121">**Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="019fd-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="019fd-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="019fd-122">See also</span></span>

- [<span data-ttu-id="019fd-123">IMetaDataImport, interface</span><span class="sxs-lookup"><span data-stu-id="019fd-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="019fd-124">IMetaDataImport2, interface</span><span class="sxs-lookup"><span data-stu-id="019fd-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
