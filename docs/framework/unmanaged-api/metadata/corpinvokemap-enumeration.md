---
title: CorPinvokeMap, énumération
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 8216dc3030b18428ab52fbf8385d392f81057aa0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176147"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap, énumération
Spécifie les options pour un appel PInvoke.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a>Membres  
  
|Membre|Description|  
|------------|-----------------|  
|`pmNoMangle`|Utilisez chaque nom de membre tel que spécifié.|  
|`pmCharSetMask`|Réservé.|  
|`pmCharSetNotSpec`|Réservé.|  
|`pmCharSetAnsi`|Les chaînes sont marshalées sous forme de chaînes de caractères à plusieurs octets.|  
|`pmCharSetUnicode`|Les chaînes sont marshalées sous forme de caractères Unicode de 2 octets.|  
|`pmCharSetAuto`|Les chaînes sont automatiquement marshalées, comme requis par le système d'exploitation cible. La valeur par défaut est Unicode sur Windows NT, Windows 2000, Windows XP, et la famille Windows Server 2003; la valeur par défaut est ANSI sur Windows 98 et Windows Me.|  
|`pmBestFitUseAssem`|Réservé.|  
|`pmBestFitEnabled`|Effectuez la cartographie la mieux adaptée des caractères Unicode qui n’ont pas de correspondance exacte dans l’ensemble de caractères ANSI.|  
|`pmBestFitDisabled`|N’effectuez pas la cartographie la mieux adaptée des caractères Unicode. Dans ce cas, tous les caractères inapprables seront remplacés par un «?».|  
|`pmBestFitMask`|Réservé.|  
|`pmThrowOnUnmappableCharUseAssem`|Réservé.|  
|`pmThrowOnUnmappableCharEnabled`|Jetez une exception lorsque le maréchal interop rencontre un caractère inapprable.|  
|`pmThrowOnUnmappableCharDisabled`|Ne jetez pas une exception lorsque le maréchal interop rencontre un caractère inapprable.|  
|`pmThrowOnUnmappableCharMask`|Réservé|  
|`pmSupportsLastError`|Permettez à l’appelant d’appeler la fonction Win32 `SetLastError` avant de revenir de la méthode attribuée.|  
|`pmCallConvMask`|Réservé|  
|`pmCallConvWinapi`|Utilisez la convention d’appel de la plate-forme par défaut. Par exemple, sur Windows `StdCall` la valeur par défaut `Cdecl`est et sur Windows CE .NET il est .|  
|`pmCallConvCdecl`|Utilisez `Cdecl` la convention d’appel. Dans ce cas, l’appelant nettoie la pile. Cela permet d’appeler des fonctions avec `varargs` (c’est-à-dire des fonctions qui acceptent un nombre variable de paramètres).|  
|`pmCallConvStdcall`|Utilisez `StdCall` la convention d’appel. Dans ce cas, le callee nettoie la pile. Il s'agit de la convention par défaut pour appeler les fonctions non managées avec appel de code non managé.|  
|`pmCallConvThiscall`|Utilisez `ThisCall` la convention d’appel. Dans ce cas, le `this` premier paramètre est le pointeur et est stocké dans le registre ECX. D'autres paramètres font l'objet d'un push sur la pile. La `ThisCall` convention d’appel est utilisée pour appeler des méthodes sur les classes exportées d’un DLL non gestion.|  
|`pmCallConvFastcall`|Réservé.|  
|`pmMaxValue`|Réservé.|  
  
## <a name="requirements"></a>Spécifications  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête:** CorHdr.h  
  
 **.NET Versions-cadre:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
