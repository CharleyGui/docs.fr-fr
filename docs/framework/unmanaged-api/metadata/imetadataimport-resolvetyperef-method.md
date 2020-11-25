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
ms.openlocfilehash: 76c5519a6cd1b8994e2f869281f13d8269e89fde
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702821"
---
# <a name="imetadataimportresolvetyperef-method"></a>IMetaDataImport::ResolveTypeRef, méthode

Résout une <xref:System.Type> référence représentée par le jeton TypeRef spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ResolveTypeRef (  
   [in]  mdTypeRef       tr,  
   [in]  REFIID          riid,  
   [out] IUnknown        **ppIScope,  
   [out] mdTypeDef       *ptd  
);  
```  
  
## <a name="parameters"></a>Paramètres  

 `tr`  
 dans Jeton de métadonnées TypeRef pour lequel retourner les informations de type référencées.  
  
 `riid`  
 dans IID de l’interface à retourner `ppIScope` . En général, il s’agit de IID_IMetaDataImport.  
  
 `ppIScope`  
 à Interface avec la portée de module dans laquelle le type référencé est défini.  
  
 `ptd`  
 à Pointeur vers un jeton TypeDef qui représente le type référencé.  
  
## <a name="remarks"></a>Remarques  
  
> [!IMPORTANT]
> N’utilisez pas cette méthode si plusieurs domaines d’application sont chargés. La méthode ne respecte pas les limites du domaine d’application. Si plusieurs versions d’un assembly sont chargées et qu’elles contiennent le même type avec le même espace de noms, la méthode retourne la portée de module du premier type qu’elle trouve.  
  
 La `ResolveTypeRef` méthode recherche la définition de type dans d’autres modules. Si la définition de type est trouvée, `ResolveTypeRef` retourne une interface à cette portée de module, ainsi que le jeton typedef pour le type.  
  
 Si la référence de type à résoudre a une portée de résolution de AssemblyRef, la `ResolveTypeRef` méthode recherche une correspondance uniquement dans les portées de métadonnées qui ont déjà été ouvertes avec des appels à la méthode [IMetaDataDispenser :: OpenScope](imetadatadispenser-openscope-method.md) ou à la méthode [IMetaDataDispenser :: OpenScopeOnMemory](imetadatadispenser-openscopeonmemory-method.md) . Cela est dû au fait que `ResolveTypeRef` ne peut pas déterminer à partir de la portée AssemblyRef sur le disque ou dans le global assembly cache l’assembly est stocké.  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions de .NET Framework :**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](imetadataimport-interface.md)
- [IMetaDataImport2, interface](imetadataimport2-interface.md)
