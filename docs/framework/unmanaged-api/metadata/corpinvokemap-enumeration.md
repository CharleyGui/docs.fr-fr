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
ms.openlocfilehash: 17b7af7016cf88fd3ae263dd952502d515b0c833
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441560"
---
# <a name="corpinvokemap-enumeration"></a>CorPinvokeMap, énumération
Spécifie les options d’un appel PInvoke.  
  
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
|`pmNoMangle`|Utilisez chaque nom de membre comme spécifié.|  
|`pmCharSetMask`|Réservé.|  
|`pmCharSetNotSpec`|Réservé.|  
|`pmCharSetAnsi`|Marshalez les chaînes en tant que chaînes de caractères codés sur plusieurs octets.|  
|`pmCharSetUnicode`|Marshalez les chaînes en tant que caractères Unicode sur 2 octets.|  
|`pmCharSetAuto`|Marshalez automatiquement les chaînes de manière appropriée pour le système d’exploitation cible. La valeur par défaut est Unicode sur Windows NT, Windows 2000, Windows XP et la famille Windows Server 2003. la valeur par défaut est ANSI sur Windows 98 et Windows Me.|  
|`pmBestFitUseAssem`|Réservé.|  
|`pmBestFitEnabled`|Effectuez le mappage le mieux adapté des caractères Unicode qui n’ont pas de correspondance exacte dans le jeu de caractères ANSI.|  
|`pmBestFitDisabled`|N’effectuez pas le mappage le mieux adapté des caractères Unicode. Dans ce cas, tous les caractères non mappables seront remplacés par un «  ? ».|  
|`pmBestFitMask`|Réservé.|  
|`pmThrowOnUnmappableCharUseAssem`|Réservé.|  
|`pmThrowOnUnmappableCharEnabled`|Levez une exception lorsque le marshaleur d’interopérabilité rencontre un caractère non mappable.|  
|`pmThrowOnUnmappableCharDisabled`|Ne levez pas d’exception lorsque le marshaleur d’interopérabilité rencontre un caractère non mappable.|  
|`pmThrowOnUnmappableCharMask`|Réservée|  
|`pmSupportsLastError`|Autorisez l’appelé à appeler la fonction de `SetLastError` Win32 avant de retourner la méthode avec attributs.|  
|`pmCallConvMask`|Réservée|  
|`pmCallConvWinapi`|Utilisez la Convention d’appel de la plateforme par défaut. Par exemple, sur Windows, la valeur par défaut est `StdCall` et sur Windows CE .NET il est `Cdecl`.|  
|`pmCallConvCdecl`|Utilisez la Convention d’appel `Cdecl`. Dans ce cas, l’appelant nettoie la pile. Cela permet d’appeler des fonctions avec `varargs` (c’est-à-dire des fonctions qui acceptent un nombre variable de paramètres).|  
|`pmCallConvStdcall`|Utilisez la Convention d’appel `StdCall`. Dans ce cas, l’appelé nettoie la pile. Il s’agit de la Convention par défaut pour appeler des fonctions non managées avec l’appel de code non managé.|  
|`pmCallConvThiscall`|Utilisez la Convention d’appel `ThisCall`. Dans ce cas, le premier paramètre est le pointeur `this` et il est stocké dans le registre ECX. D’autres paramètres font l’objet d’un push sur la pile. La Convention d’appel `ThisCall` est utilisée pour appeler des méthodes sur des classes exportées à partir d’une DLL non managée.|  
|`pmCallConvFastcall`|Réservé.|  
|`pmMaxValue`|Réservé.|  
  
## <a name="requirements"></a>Configuration requise  
 **Plateformes :** Consultez [Configuration requise](../../../../docs/framework/get-started/system-requirements.md).  
  
 **En-tête :** CorHdr. h  
  
 **Versions du .NET Framework :** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Voir aussi

- [Énumérations de métadonnées](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
