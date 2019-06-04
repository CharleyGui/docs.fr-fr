---
title: <NetFx40_PInvokeStackResilience>, élément
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7a1cf34f63b1ba0dfced8ff23c252f3363723c6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489407"
---
# <a name="netfx40pinvokestackresilience-element"></a>\<NetFx40_PInvokeStackResilience > élément
Indique si le runtime corrige automatiquement les déclarations incorrectes d’appel de code non managé à l’exécution, au prix de transitions plus lentes entre le code managé et le code non managé.  
  
 \<configuration>  
\<runtime>  
<NetFx40_PInvokeStackResilience>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
  
|Attribut|Description|  
|---------------|-----------------|  
|`enabled`|Attribut requis.<br /><br /> Spécifie si le runtime détecte plateforme incorrecte les déclarations d’appel et résout automatiquement la pile en cours d’exécution sur les plateformes 32 bits.|  
  
## <a name="enabled-attribute"></a>Attribut enabled  
  
|Value|Description|  
|-----------|-----------------|  
|`0`|Le runtime utilise l’architecture introduite dans .NET Framework 4 ne détecte pas de marshaling d’interopérabilité plus rapide et les déclarations d’appel de plateforme incorrect de correctif. Il s'agit de la valeur par défaut.|  
|`1`|Les runtime utilise des transitions plus lentes pour détecter et corriger la plateforme incorrecte les déclarations d’appel.|  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|  
|`runtime`|Contient des informations sur les options d'initialisation du runtime.|  
  
## <a name="remarks"></a>Notes  
 Cet élément vous permet aux échanges plus rapidement le marshaling d’interopérabilité pour les déclarations d’appel de résilience d’exécution par rapport à la plateforme incorrecte.  
  
 À compter de .NET Framework 4, une architecture simplifiée de marshaling interop fournit une amélioration significative des performances pour les transitions du code managé au code non managé. Dans les versions antérieures du .NET Framework, la plateforme incorrecte détectée de couche marshaling sur les plateformes 32 bits, les déclarations d’appel et corrigés automatiquement la pile. La nouvelle architecture de marshaling élimine cette étape. Par conséquent, les transitions sont très rapides, mais une déclaration non managé incorrectes peuvent provoquer un échec du programme.  
  
 Pour faciliter la détection des déclarations incorrectes pendant le développement, l’expérience de débogage Visual Studio a été améliorée. Le [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) assistant débogage managé (MDA) vous notifie de plateforme incorrect appel déclarations lorsque votre application s’exécute avec le débogueur attaché.  
  
 Pour répondre aux scénarios où votre application utilise les composants que vous ne pouvez pas recompiler et qu’avez incorrect non managé déclarations, vous pouvez utiliser le `NetFx40_PInvokeStackResilience` élément. Ajout de cet élément au fichier de configuration de votre application avec `enabled="1"` opte pour un mode de compatibilité avec le comportement des versions antérieures du .NET Framework, au prix de transitions plus lentes. Les assemblys qui ont été compilés sur des versions antérieures du .NET Framework sont automatiquement accepté d’utiliser ce mode de compatibilité et n’avez pas besoin de cet élément.  
  
## <a name="configuration-file"></a>Fichier de configuration  
 Cet élément peut être utilisé uniquement dans le fichier de configuration d’application.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment à opter pour une meilleure résilience contre incorrect plateforme déclarations d’appel pour une application, au prix de transitions plus lentes entre code managé et.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Schéma des fichiers de configuration](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
