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
ms.openlocfilehash: 474c3274bfba6803ebb17289f138251d755250e4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699802"
---
# <a name="cryptography-settings-schema"></a>Schéma des paramètres de chiffrement
Le schéma des paramètres de chiffrement contient des éléments qui spécifient comment mapper des noms d’algorithmes conviviaux à des classes qui implémentent des algorithmes de chiffrement.  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<mscorlib >** ](mscorlib-element-for-cryptography-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<cryptographySettings >** ](cryptographysettings-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<cryptoNameMapping >** ](cryptonamemapping-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0cryptoClasses >** ](cryptoclasses-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7 @ no__t-8 @ no__t-9[ **&nbsp;2cryptoClass >** ](cryptoclass-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6 @ no__t-7[ **&nbsp;0nameEntry >** ](nameentry-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5[ **\<oidMap >** ](oidmap-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 @ no__t-6[ **\<oidEntry >** ](oidentry-element.md)  
  
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
- [Cryptographic Services](../../../../standard/security/cryptographic-services.md)
