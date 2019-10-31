---
title: CompareAssemblyIdentity, fonction
ms.date: 03/30/2017
api_name:
- CompareAssemblyIdentity
api_location:
- fusion.dll
- clr.dll
api_type:
- COM
f1_keywords:
- CompareAssemblyIdentity
helpviewer_keywords:
- CompareAssemblyIdentity function [.NET Framework fusion]
ms.assetid: 8b364ae1-8efa-4744-a7da-81fd093d84d6
topic_type:
- apiref
ms.openlocfilehash: f6711902fb9d5c5c16084057b731746843cf0230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108924"
---
# <a name="compareassemblyidentity-function"></a>CompareAssemblyIdentity, fonction
Compare deux identités d’assembly pour déterminer si elles sont équivalentes.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
STDAPI CompareAssemblyIdentity (  
    [in]  LPCWSTR                  pwzAssemblyIdentity1,  
    [in]  BOOL                     fUnified1,  
    [in]  LPCWSTR                  pwzAssemblyIdentity2,  
    [in]  BOOL                     fUnified2,  
    [out] BOOL                     *pfEquivalent,  
    [out] AssemblyComparisonResult *pResult  
 );  
```  
  
## <a name="parameters"></a>Paramètres  
 `pwzAssemblyIdentity1`  
 dans Identité textuelle du premier assembly dans la comparaison.  
  
 `fUnified1`  
 dans Indicateur booléen qui indique l’unification spécifiée par l’utilisateur pour `pwzAssemblyIdentity1`.  
  
 `pwzAssemblyIdentity2`  
 dans Identité textuelle du deuxième assembly dans la comparaison.  
  
 `fUnified2`  
 dans Indicateur booléen qui indique l’unification spécifiée par l’utilisateur pour `pwzAssemblyIdentity2`.  
  
 `pfEquivalent`  
 à Indicateur booléen qui indique si les deux assemblys sont équivalents.  
  
 `pResult`  
 à Énumération [AssemblyComparisonResult,](assemblycomparisonresult-enumeration.md) qui contient des informations détaillées sur la comparaison.  
  
## <a name="return-value"></a>Valeur de retour  
 `pfEquivalent` retourne une valeur booléenne qui indique si les deux assemblys sont équivalents. `pResult` renvoie l’une des valeurs de `AssemblyComparisonResult`, afin de fournir une raison plus détaillée de la valeur de `pfEquivalent`.  
  
## <a name="remarks"></a>Notes  
 `CompareAssemblyIdentity` vérifie si `pwzAssemblyIdentity1` et `pwzAssemblyIdentity2` sont équivalents. `pfEquivalent` a la valeur `true` dans une ou plusieurs des conditions suivantes :  
  
- Les deux identités d’assembly sont équivalentes. Pour les assemblys avec nom fort, l’équivalence exige que le nom de l’assembly, la version, le jeton de clé publique et la culture soient identiques. Pour les assemblys simplement nommés, l’équivalence requiert une correspondance sur le nom et la culture de l’assembly.  
  
- Les deux identités d’assembly font référence aux assemblys qui s’exécutent sur le .NET Framework. Cette condition retourne `true` même si les numéros de version de l’assembly ne correspondent pas.  
  
- Les deux assemblys ne sont pas des assemblys managés, mais `fUnified1` ou `fUnified2` a été défini sur `true`.  
  
 L’indicateur de `fUnified` indique que tous les numéros de version jusqu’au numéro de version de l’assembly avec nom fort sont considérés comme équivalents à l’assembly avec nom fort. Par exemple, si la valeur de `pwzAssemblyIndentity1` est « MyAssembly, version = 3.0.0.0, culture = neutral, publicKeyToken =.... » et que la valeur de `fUnified1` est `true`, cela indique que toutes les versions de MyAssembly de la version 0.0.0.0 à 3.0.0.0 doivent être traitées comme identique. Dans ce cas, si `pwzAssemblyIndentity2` fait référence au même assembly que `pwzAssemblyIndentity1`, sauf qu’il a un numéro de version inférieur, `pfEquivalent` est défini sur `true`. Si `pwzAssemblyIdentity2` fait référence à un numéro de version plus élevé, `pfEquivalent` est défini sur `true` uniquement si la valeur de `fUnified2` est `true`.  
  
 Le paramètre `pResult` contient des informations spécifiques sur la raison pour laquelle les deux assemblys sont considérés comme équivalents ou non équivalents. Pour plus d’informations, consultez [énumération AssemblyComparisonResult,](assemblycomparisonresult-enumeration.md).  
  
## <a name="requirements"></a>spécifications  
 **Plateformes :** Consultez [Configuration requise](../../get-started/system-requirements.md).  
  
 **En-tête :** Fusion. h  
  
 **Bibliothèque :** Inclus en tant que ressource dans MsCorEE. dll  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Fonctions statiques globales de fusion](fusion-global-static-functions.md)
- [AssemblyComparisonResult, énumération](assemblycomparisonresult-enumeration.md)
