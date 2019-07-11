---
title: IMetaDataImport::GetInterfaceImplProps, méthode
ms.date: 02/25/2019
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2a4305b94d785a764671a2d73f43facefd0da0e6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782374"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a>IMetaDataImport::GetInterfaceImplProps, méthode
Obtient un pointeur vers les jetons de métadonnées pour le <xref:System.Type> qui implémente la méthode spécifiée, et pour l’interface qui déclare cette méthode.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `iiImpl`  
 [in] Représentant la méthode pour renvoyer les jetons de classe et d’interface pour le jeton de métadonnées.  
  
 `pClass`  
 [out] Le jeton de métadonnées représentant la classe qui implémente la méthode.  
  
 `ptkIface`  
 [out] Le jeton de métadonnées qui représente l’interface qui définit la méthode implémentée.  

## <a name="remarks"></a>Notes

 Vous obtenez la valeur de `iImpl` en appelant le [EnumInterfaceImpls](imetadataimport-enuminterfaceimpls-method.md) (méthode).
 
 Par exemple, supposons qu’une classe a un `mdTypeDef` jeton la valeur de 0 x 02000007 et qu’elle implémente trois interfaces dont les types ont des jetons : 

- 0x02000003 (TypeDef)
- 0x0100000A (TypeRef)
- 0x0200001C (TypeDef)

Conceptuellement, ces informations sont stockées dans une table de mise en œuvre d’interface en tant que :

| Numéro de ligne | Jeton de classe | Jeton de l’interface |
|------------|-------------|-----------------|
| 4          |             |                 |
| 5\.          | 02000007    | 02000003        |
| 6\.          | 02000007    | 0100000A        |
| 7          |             |                 |
| 8          | 02000007    | 0200001C        |

Rappelez-vous, le jeton est une valeur de 4 octets :

- Les 3 octets contenant le nombre de lignes ou RID.
- L’octet de poids fort conserve le type de jeton : 0 x 09 pour `mdtInterfaceImpl`.

`GetInterfaceImplProps` Retourne les informations contenues dans la ligne dont le jeton que vous fournissez dans le `iImpl` argument. 
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataImport, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [IMetaDataImport2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
