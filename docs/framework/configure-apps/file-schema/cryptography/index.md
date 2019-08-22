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
ms.openlocfilehash: a2aa56f8b2a92f906293adfae9d23ed8959336fb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664294"
---
# <a name="cryptography-settings-schema"></a>Schéma des paramètres de chiffrement
Le schéma des paramètres de chiffrement contient des éléments qui spécifient comment mapper des noms d’algorithmes conviviaux à des classes qui implémentent des algorithmes de chiffrement.  
  
 [ **\<configuration>** ](../configuration-element.md)  
  
 [ **\<mscorlib>** ](mscorlib-element-for-cryptography-settings.md)  
  
 [ **\<cryptographySettings>** ](cryptographysettings-element.md)  
  
 [ **\<cryptoNameMapping>** ](cryptonamemapping-element.md)  
  
 [ **\<cryptoClasses>** ](cryptoclasses-element.md)  
  
 [ **\<cryptoClass>** ](cryptoclass-element.md)  
  
 [ **\<nameEntry>** ](nameentry-element.md)  
  
 [ **\<oidMap>** ](oidmap-element.md)  
  
 [ **\<oidEntry>** ](oidentry-element.md)  
  
|Élément|Description|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|Contient la liste des classes de chiffrement qui ont un mappage à un nom convivial dans l’élément **\<nameEntry>** .|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|Contient une classe de chiffrement qui a un mappage à un nom convivial dans l’élément **\<nameEntry>** .|  
|[ **\<cryptographySettings**>](cryptographysettings-element.md)|Contient des paramètres de chiffrement.|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|Contient des mappages de classes à des noms conviviaux.|  
|[ **\<mscorlib>** , élément pour les paramètres de chiffrement](mscorlib-element-for-cryptography-settings.md)|Contient l’élément **\<cryptographySettings>** .|  
|[ **\<nameEntry>** ](nameentry-element.md)|Mappe un nom de classe à un nom d’algorithme convivial, ce qui permet à une classe d’avoir plusieurs noms conviviaux.|  
|[ **\<oidEntry>** ](oidentry-element.md)|Mappe un identificateur d’objet (OID) ASN.1 à un nom convivial.|  
|[ **\<oidMap>** ](oidmap-element.md)|Contient les mappages d’OID ASN.1 aux classes.|  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des fichiers de configuration](../index.md)
- [Cryptographic Services](../../../../../docs/standard/security/cryptographic-services.md)
