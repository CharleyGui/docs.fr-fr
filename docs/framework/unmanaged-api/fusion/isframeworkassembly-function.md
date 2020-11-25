---
title: IsFrameworkAssembly, fonction
ms.date: 03/30/2017
api_name:
- IsFrameworkAssembly
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IsFrameworkAssembly
helpviewer_keywords:
- IsFrameworkAssembly function [.NET Framework fusion]
ms.assetid: b0c6f19b-d4fd-4971-88f0-12ffb5793da3
topic_type:
- apiref
ms.openlocfilehash: 828c7660d6c006e700302d119ce4caf7d76e5d84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728561"
---
# <a name="isframeworkassembly-function"></a>IsFrameworkAssembly, fonction

Obtient une valeur qui indique si l’assembly spécifié est managé.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsFrameworkAssembly (  
    [in]  LPCWSTR pwzAssemblyReference,  
    [out] LPBOOL  pbIsFrameworkAssembly,  
    [in]  LPWSTR  pwzFrameworkAssemblyIdentity,  
    [in]  LPDWORD pccSize  
 );  
```  
  
## <a name="parameters"></a>Paramètres  

 `pwzAssemblyReference`  
 dans Nom de l’assembly à vérifier.  
  
 `pbIsFrameworkAssembly`  
 à Valeur booléenne qui indique si l’assembly est managé.  
  
 `pwzFrameworkAssemblyIdentity`  
 dans Chaîne non canonique qui contient l’identité unique de l’assembly.  
  
 `pccSize`  
 [in] Taille de `pwzFrameworkAssemblyIdentity`.  
  
## <a name="remarks"></a>Remarques  

 Le `pwzAssemblyReference` paramètre est un pointeur vers une chaîne de caractères qui contient le nom d’un assembly.  
  
 Si cet assembly fait partie du .NET Framework, le `pbIsFrameworkAssembly` paramètre contient une valeur booléenne `true` .  
  
 Si l’assembly nommé ne fait pas partie de la .NET Framework, ou si le `pwzAssemblyReference` paramètre ne nomme pas d’assembly, `pbIsFrameworkAssembly` contient une valeur booléenne `false` .  
  
## <a name="requirements"></a>Configuration requise  

 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de la fusion](fusion-global-static-functions.md)
