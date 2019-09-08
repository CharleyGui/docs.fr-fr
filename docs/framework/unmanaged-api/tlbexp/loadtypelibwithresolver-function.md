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
ms.openlocfilehash: b78789344050fd5e1cb0ee3492bf330fbf92bc88
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798935"
---
# <a name="loadtypelibwithresolver-function"></a>LoadTypeLibWithResolver, fonction
Charge une bibliothèque de types et utilise l' [interface ITypeLibResolver](itypelibresolver-interface.md) fournie pour résoudre toutes les bibliothèques de types référencées en interne.  
  
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
 dans Chemin d’accès de fichier de la bibliothèque de types.  
  
 `regkind`  
 dans Indicateur d' [énumération REGKIND](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind) qui contrôle la façon dont la bibliothèque de types est inscrite. Les valeurs possibles sont les suivantes :  
  
- `REGKIND_DEFAULT`: Utilisez le comportement d’inscription par défaut.  
  
- `REGKIND_REGISTER`: Inscrire cette bibliothèque de types.  
  
- `REGKIND_NONE`: N’inscrivez pas cette bibliothèque de types.  
  
 `pTlbResolver`  
 dans Pointeur vers l’implémentation de l' [interface ITypeLibResolver](itypelibresolver-interface.md).  
  
 `pptlib`  
 à Référence à la bibliothèque de types en cours de chargement.  
  
## <a name="return-value"></a>Valeur de retour  
 L’une des valeurs HRESULT indiquées dans le tableau suivant.  
  
|Valeur de retour|Signification|  
|------------------|-------------|  
|`S_OK`|Opération réussie.|  
|`E_OUTOFMEMORY`|Mémoire insuffisante.|  
|`E_POINTER`|Un ou plusieurs pointeurs ne sont pas valides.|  
|`E_INVALIDARG`|Un ou plusieurs arguments ne sont pas valides.|  
|`TYPE_E_IOERROR`|La fonction n’a pas pu écrire dans le fichier.|  
|`TYPE_E_REGISTRYACCESS`|Impossible d’ouvrir la base de données d’inscription du système.|  
|`TYPE_E_INVALIDSTATE`|Impossible d’ouvrir la bibliothèque de types.|  
|`TYPE_E_CANTLOADLIBRARY`|La bibliothèque de types ou la DLL n’a pas pu être chargée.|  
  
## <a name="remarks"></a>Notes  
 [Tlbexp. exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md) appelle la `LoadTypeLibWithResolver` fonction pendant le processus de conversion d’assembly en bibliothèque de types.  
  
 Cette fonction charge la bibliothèque de types spécifiée avec un accès minimal au registre. La fonction examine ensuite la bibliothèque de types pour les bibliothèques de types référencées en interne, chacune d’elles devant être chargée et ajoutée à la bibliothèque de types parente.  
  
 Pour pouvoir charger une bibliothèque de types référencée, son chemin d’accès au fichier de référence doit être résolu en chemin d’accès complet au fichier. Pour ce faire, vous devez utiliser la [méthode ResolveTypeLib (](resolvetypelib-method.md) fournie par l' [interface ITypeLibResolver](itypelibresolver-interface.md), qui est transmise `pTlbResolver` dans le paramètre.  
  
 Lorsque le chemin de fichier complet de la bibliothèque de types référencée est connu `LoadTypeLibWithResolver` , la fonction se charge et ajoute la bibliothèque de types référencée à la bibliothèque de types parente, en créant une bibliothèque de types principaux combinée.  
  
 Une fois que la fonction a résolu et chargé toutes les bibliothèques de types référencées en interne, elle retourne une référence à la bibliothèque de types `pptlib` résolue principale dans le paramètre.  
  
 La `LoadTypeLibWithResolver` fonction est généralement appelée par [Tlbexp. exe (exportateur de bibliothèques de types)](../../tools/tlbexp-exe-type-library-exporter.md), qui fournit sa propre implémentation d' [interface ITypeLibResolver](itypelibresolver-interface.md) interne dans le `pTlbResolver` paramètre.  
  
 Si vous appelez `LoadTypeLibWithResolver` directement, vous devez fournir votre propre implémentation d' [interface ITypeLibResolver](itypelibresolver-interface.md) .  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** TlbRef. h  
  
 **Bibliothèque** TlbRef.lib  
  
 **Version de .NET Framework :** 3.5, 3.0, 2.0  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions d’assistance Tlbexp](index.md)
- [LoadTypeLibEx fonction)](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
