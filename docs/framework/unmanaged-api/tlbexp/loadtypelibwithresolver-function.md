---
title: LoadTypeLibWithResolver, fonction
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5d2f5ad2afb2e73acead82369782f142aa10aac3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67782711"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver, fonction
Charge une bibliothèque de types et utilise fourni [ITypeLibResolver, interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) pour résoudre toutes bibliothèques de types référencées en interne.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a>Paramètres  
 `szFile`  
 [in] Le chemin d’accès de fichier de la bibliothèque de types.  
  
 `regkind`  
 [in] Un [énumération de regkind a](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) indicateur qui contrôle comment la bibliothèque de types est enregistrée. Ses valeurs possibles sont :  
  
- `REGKIND_DEFAULT`: Utiliser le comportement de l’inscription par défaut.  
  
- `REGKIND_REGISTER`: Inscrire cette bibliothèque de types.  
  
- `REGKIND_NONE`: N’enregistrez pas cette bibliothèque de types.  
  
 `pTlbResolver`  
 [in] Un pointeur vers l’implémentation de la [ITypeLibResolver, interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).  
  
 `pptlib`  
 [out] Une référence à la bibliothèque de types en cours de chargement.  
  
## <a name="return-value"></a>Valeur de retour  
 Une des valeurs HRESULT répertoriés dans le tableau suivant.  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_OUTOFMEMORY`|Mémoire insuffisante.|  
|`E_POINTER`|Un ou plusieurs des pointeurs ne sont pas valides.|  
|`E_INVALIDARG`|Un ou plusieurs des arguments ne sont pas valides.|  
|`TYPE_E_IOERROR`|La fonction n’a pas pu écrire dans le fichier.|  
|`TYPE_E_REGISTRYACCESS`|La base de données système d’inscription n’a pas pu être ouvert.|  
|`TYPE_E_INVALIDSTATE`|La bibliothèque de types n’a pas pu être ouvert.|  
|`TYPE_E_CANTLOADLIBRARY`|La bibliothèque de types ou de la DLL n’a pas pu être chargé.|  
  
## <a name="remarks"></a>Notes  
 Le [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) appelle le `LoadTypeLibWithResolver` fonction pendant le processus de conversion de l’assembly de bibliothèque de types.  
  
 Cette fonction charge la bibliothèque de types spécifiée avec un accès minimal au Registre. La fonction examine ensuite la bibliothèque de types pour les bibliothèques de types référencées en interne, chacun d’eux doit être chargé et ajouté à la bibliothèque de type parent.  
  
 Avant de la bibliothèque de types référencée peut être chargée, son chemin d’accès du fichier de référence doit être résolu en un chemin d’accès complet du fichier. Ceci est accompli par le [ResolveTypeLib, méthode](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) qui est fourni par le [ITypeLibResolver, interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), qui est transmis dans le `pTlbResolver` paramètre.  
  
 Lorsque le chemin d’accès de fichier complet de la bibliothèque de types référencée est connu, le `LoadTypeLibWithResolver` fonction charge et ajoute la bibliothèque de types référencée à la bibliothèque de type parent, création d’une bibliothèque de types principale combinée.  
  
 Une fois que la fonction et chargement de toutes les bibliothèques de types référencées en interne, elle retourne une référence à la bibliothèque de types résolue principale dans le `pptlib` paramètre.  
  
 Le `LoadTypeLibWithResolver` fonction est généralement appelée par le [Tlbexp.exe (exportateur)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), qui fournit sa propre interne [ITypeLibResolver, interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) mise en œuvre dans le `pTlbResolver` paramètre.  
  
 Si vous appelez `LoadTypeLibWithResolver` directement, vous devez fournir votre propre [ITypeLibResolver, interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implémentation.  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** TlbRef.h  
  
 **Bibliothèque :** TlbRef.lib  
  
 **Version du .NET framework :** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’assistance Tlbexp](../../../../docs/framework/unmanaged-api/tlbexp/index.md)
- [LoadTypeLibEx de le dont (fonction)](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
