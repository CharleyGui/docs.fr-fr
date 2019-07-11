---
title: IMetaDataEmit::DefineMethod, méthode
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4297b21970fbca4b5aa53c31680394cab358d255
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67777600"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod, méthode
Crée une définition pour une méthode ou une fonction globale avec la signature spécifiée et retourne un jeton pour cette définition de méthode.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
## <a name="parameters"></a>Paramètres  
 `td`  
 [in] Le `mdTypedef` jeton de la classe parente ou l’interface parente de la méthode. Définissez `td` à `mdTokenNil`, si vous définissez une fonction globale.  
  
 `szName`  
 [in] Le nom de membre au format Unicode.  
  
 `dwMethodFlags`  
 [in] Une valeur de la [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) énumération qui spécifie les attributs de la méthode ou la fonction globale.  
  
 `pvSigBlob`  
 [in] La signature de méthode. La signature est conservée tel que fourni. Si vous devez spécifier des informations supplémentaires pour tous les paramètres, utilisez le [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) (méthode).  
  
 `cbSigBlob`  
 [in] Le nombre d’octets dans `pvSigBlob`.  
  
 `ulCodeRVA`  
 [in] L’adresse du code.  
  
 `dwImplFlags`  
 [in] Une valeur de la [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) énumération qui spécifie les fonctionnalités d’implémentation de la méthode.  
  
 `pmd`  
 [out] Le jeton de membre.  
  
## <a name="remarks"></a>Notes  
 L’API de métadonnées garantit la persistance des méthodes dans le même ordre que l’appelant les émet pour une classe englobante donnée ou une interface, ce qui est spécifié dans le `td` paramètre.  
  
 Des informations supplémentaires concernant l’utilisation de `DefineMethod` et paramètres de paramètre particulier est donné ci-dessous.  
  
## <a name="slots-in-the-v-table"></a>Emplacements dans la V-table  
 Le runtime utilise des définitions de méthode pour configurer les emplacements de v-table. Dans le cas où un ou plusieurs emplacements doivent être ignorés, par exemple pour conserver la parité avec une disposition de l’interface COM, une méthode factice est définie pour accepter l’emplacement ou les emplacements dans la v-table ; définir le `dwMethodFlags` à la `mdRTSpecialName` valeur de la [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) énumération et spécifiez le nom :  
  
 _VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*>
  
 où *SequenceNumber* est le numéro de séquence de la méthode et *NombreEmplacements* est le nombre d’emplacements à ignorer dans la v-table. Si *NombreEmplacements* est omis, 1 est pris en compte. Ces méthodes factices ne peuvent pas être appelés à partir du code managé ou non managé et toute tentative d’appel, à partir du code managé ou non managé, génère une exception. Leur seul but est de l’espace dans la v-table générés par le runtime pour l’intégration de COM.  
  
## <a name="duplicate-methods"></a>Méthodes en double  
 Vous ne devez pas définir des méthodes en double. Autrement dit, vous ne devez pas appeler `DefineMethod` avec un jeu en double des valeurs dans le `td`, `wzName`, et `pvSig` paramètres. (Ces trois paramètres définissent de façon unique la méthode.). Toutefois, vous pouvez utiliser un triple en double à condition que pour une des définitions de méthode, vous définissez le `mdPrivateScope` bit dans le `dwMethodFlags` paramètre. (Le `mdPrivateScope` bits signifie que le compilateur n’émet pas d’une référence à cette définition de méthode.)  
  
## <a name="method-implementation-information"></a>Informations d’implémentation de méthode  
 Plus d’informations sur l’implémentation de méthode ne sont souvent pas connus au moment où que la méthode est déclarée. Par conséquent, vous n’avez pas besoin transmettre des valeurs dans le `ulCodeRVA` et `dwImplFlags` paramètres lors de l’appel `DefineMethod`. Les valeurs peuvent être fournies ultérieurement via [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), le cas échéant.  
  
 Dans certaines situations, telles que l’appel de plate-forme (PInvoke) ou des scénarios COM interop, le corps de méthode n’est pas fourni, et `ulCodeRVA` doit être définie sur zéro. Dans ces situations, la méthode ne doit pas être identifiée comme abstraite, car le runtime utilise pour localiser l’implémentation.  
  
## <a name="defining-a-method-for-pinvoke"></a>Définition d’une méthode pour PInvoke  
 Pour chaque fonction non managée à appeler via PInvoke, vous devez définir une méthode managée qui représente la fonction non managée cible. Pour définir la méthode managée, utilisez `DefineMethod` avec certains des paramètres définis sur certaines valeurs, selon la façon dont PInvoke est utilisé :  
  
- PInvoke true : implique l’appel d’une méthode non managée externe qui réside dans une DLL non managée.  
  
- PInvoke local : implique l’appel d’une méthode non managée native qui est incorporée dans le module managé actuel.  
  
 Les paramètres sont fournis dans le tableau suivant.  
  
|Paramètre|Valeurs pour PInvoke true|Valeurs pour PInvoke local|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Définissez `mdStatic`; désactivez `mdSynchronized` et `mdAbstract`.|  
|`pvSigBlob`|Une signature de méthode du common language runtime (CLR) valide avec des paramètres qui sont valides des types managés.|Une signature de méthode CLR valide avec des paramètres qui sont valides des types managés.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Définissez `miCil` et `miManaged`.|Définissez `miNative` et `miUnmanaged`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor.h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE.dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
