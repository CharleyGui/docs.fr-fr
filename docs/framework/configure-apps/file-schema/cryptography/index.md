---
title: Schéma des paramètres de chiffrement
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: c632a15552c8ba5743aac1309098b7d7ef949bbd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088008"
---
# <a name="cryptography-settings-schema"></a>Schéma des paramètres de chiffrement
Le schéma des paramètres de chiffrement contient des éléments qui spécifient comment mapper des noms d’algorithmes conviviaux à des classes qui implémentent des algorithmes de chiffrement.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<mscorlib>**](mscorlib-element-for-cryptography-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptographySettings>**](cryptographysettings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoNameMapping>**](cryptonamemapping-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClasses>**](cryptoclasses-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cryptoClass>**](cryptoclass-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<nameEntry>**](nameentry-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidMap>**](oidmap-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oidEntry>**](oidentry-element.md)

|Élément|Description|  
|-------------|-----------------|  
|[**\<cryptoClasses**>](cryptoclasses-element.md)|Contient une liste de classes de chiffrement qui ont un mappage à un nom convivial dans l' **\<nameEntry>** élément.|  
|[**\<cryptoClass**>](cryptoclass-element.md)|Contient une classe de chiffrement qui a un mappage à un nom convivial dans l' **\<nameEntry>** élément.|  
|[**\<cryptographySettings**>](cryptographysettings-element.md)|Contient des paramètres de chiffrement.|  
|[**\<cryptoNameMapping**>](cryptonamemapping-element.md)|Contient des mappages de classes à des noms conviviaux.|  
|[**\<mscorlib>**, élément pour les paramètres de chiffrement](mscorlib-element-for-cryptography-settings.md)|Contient l' **\<cryptographySettings>** élément.|  
|[**\<nameEntry>**](nameentry-element.md)|Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.|  
|[**\<oidEntry>**](oidentry-element.md)|Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.|  
|[**\<oidMap>**](oidmap-element.md)|Contient les mappages d’OID ASN.1 aux classes.|  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des fichiers de configuration](../index.md)
- [Services de chiffrement](../../../../standard/security/cryptographic-services.md)
