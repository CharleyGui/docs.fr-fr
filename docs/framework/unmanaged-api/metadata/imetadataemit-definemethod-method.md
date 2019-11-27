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
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431808"
---
# <a name="imetadataemitdefinemethod-method"></a>IMetaDataEmit::DefineMethod, méthode
Crée une définition pour une méthode ou une fonction globale avec la signature spécifiée et retourne un jeton à cette définition de méthode.  
  
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
 dans Jeton `mdTypedef` de la classe parente ou de l’interface parente de la méthode. Définissez `td` sur `mdTokenNil`, si vous définissez une fonction globale.  
  
 `szName`  
 dans Nom du membre au format Unicode.  
  
 `dwMethodFlags`  
 dans Valeur de l’énumération [CorMethodAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) qui spécifie les attributs de la méthode ou de la fonction globale.  
  
 `pvSigBlob`  
 dans Signature de la méthode. La signature est conservée telle qu’elle est fournie. Si vous devez spécifier des informations supplémentaires pour tous les paramètres, utilisez la méthode [IMetaDataEmit :: SetParamProps,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) .  
  
 `cbSigBlob`  
 dans Nombre d’octets dans `pvSigBlob`.  
  
 `ulCodeRVA`  
 dans Adresse du code.  
  
 `dwImplFlags`  
 dans Valeur de l’énumération [CorMethodImpl,](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) qui spécifie les fonctionnalités d’implémentation de la méthode.  
  
 `pmd`  
 à Jeton de membre.  
  
## <a name="remarks"></a>Notes  
 L’API de métadonnées garantit de conserver les méthodes dans le même ordre que celui que l’appelant les émet pour une interface ou une classe englobante donnée, spécifiée dans le paramètre `td`.  
  
 Vous trouverez ci-dessous des informations supplémentaires concernant l’utilisation des `DefineMethod` et des paramètres de paramètres particuliers.  
  
## <a name="slots-in-the-v-table"></a>Emplacements dans le V-table  
 Le runtime utilise les définitions de méthode pour configurer des emplacements v-table. Dans le cas où un ou plusieurs emplacements doivent être ignorés, par exemple pour conserver la parité avec une disposition d’interface COM, une méthode factice est définie pour prendre l’emplacement ou les emplacements dans la v-table ; Affectez à la `dwMethodFlags` la valeur `mdRTSpecialName` de l’énumération [CorMethodAttr,](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) et spécifiez le nom comme suit :  
  
 _VtblGap\< *>* \<\_*CountOfSlots*>
  
 où *numéro* de séquence est le numéro de séquence de la méthode et *CountOfSlots* est le nombre d’emplacements à ignorer dans la table v. Si *CountOfSlots* est omis, 1 est utilisé. Ces méthodes factices ne peuvent pas être appelées à partir de code managé ou non managé et toute tentative de les appeler à partir de code managé ou non managé génère une exception. Leur seul but est d’occuper de l’espace dans la vtable générée par le runtime pour l’intégration COM.  
  
## <a name="duplicate-methods"></a>Méthodes dupliquées  
 Vous ne devez pas définir de méthodes en double. Autrement dit, vous ne devez pas appeler `DefineMethod` avec un ensemble de valeurs en double dans les paramètres `td`, `wzName`et `pvSig`. (Ces trois paramètres définissent ensemble la méthode de manière unique.). Toutefois, vous pouvez utiliser un triple dupliqué fourni qui, pour l’une des définitions de méthode, vous définissez le bit `mdPrivateScope` dans le paramètre `dwMethodFlags`. (Le bit `mdPrivateScope` signifie que le compilateur n’émet pas de référence à cette définition de méthode.)  
  
## <a name="method-implementation-information"></a>Informations d’implémentation de la méthode  
 Les informations sur l’implémentation de la méthode sont souvent inconnues au moment où la méthode est déclarée. Par conséquent, vous n’avez pas besoin de transmettre des valeurs dans les paramètres `ulCodeRVA` et `dwImplFlags` lors de l’appel de `DefineMethod`. Les valeurs peuvent être fournies ultérieurement via [IMetaDataEmit :: SetMethodImplFlags,](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) ou [IMetaDataEmit :: SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), selon le cas.  
  
 Dans certaines situations, telles que l’appel de la plateforme (PInvoke) ou les scénarios de COM Interop, le corps de la méthode n’est pas fourni et `ulCodeRVA` doit être défini sur zéro. Dans ces situations, la méthode ne doit pas être marquée comme abstract, car le runtime localise l’implémentation.  
  
## <a name="defining-a-method-for-pinvoke"></a>Définition d’une méthode pour PInvoke  
 Pour chaque fonction non managée à appeler par le biais de PInvoke, vous devez définir une méthode managée qui représente la fonction non managée cible. Pour définir la méthode managée, utilisez `DefineMethod` avec certains des paramètres définis sur certaines valeurs, en fonction de la façon dont PInvoke est utilisé :  
  
- True PInvoke : implique l’appel d’une méthode non managée externe qui réside dans une DLL non managée.  
  
- PInvoke local : implique l’appel d’une méthode Native non managée qui est incorporée dans le module managé actuel.  
  
 Les paramètres sont indiqués dans le tableau suivant.  
  
|Paramètre|Valeurs pour True PInvoke|Valeurs pour PInvoke local|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||Définir `mdStatic`; Désactivez `mdSynchronized` et `mdAbstract`.|  
|`pvSigBlob`|Signature de méthode common language runtime (CLR) valide avec des paramètres qui sont des types managés valides.|Signature de méthode CLR valide avec des paramètres qui sont des types managés valides.|  
|`ulCodeRVA`||0|  
|`dwImplFlags`|Définissez `miCil` et `miManaged`.|Définissez `miNative` et `miUnmanaged`.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** Cor. h  
  
 **Bibliothèque :** Utilisé en tant que ressource dans MSCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [IMetaDataEmit, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [IMetaDataEmit2, interface](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
