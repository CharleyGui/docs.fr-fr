---
title: <requiredRuntime>, élément
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697488"
---
# <a name="requiredruntime-element"></a>élément @no__t 0requiredRuntime >

Spécifie que l’application prend en charge uniquement la version 1.0 du common language runtime. Cet élément est déconseillé et ne doit plus être utilisé. L’élément [`supportedRuntime`](supportedruntime-element.md) doit être utilisé à la place.

[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<startup >** ](startup-element.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requiredRuntime >**  

## <a name="syntax"></a>Syntaxe

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`version`|Attribut facultatif.<br /><br /> Valeur de chaîne qui spécifie la version du .NET Framework que cette application prend en charge. La valeur de chaîne doit correspondre au nom de répertoire trouvé sous la racine d’installation .NET Framework. Le contenu de la valeur de chaîne n’est pas analysé.|
|`safemode`|Attribut facultatif.<br /><br /> Spécifie si le code de démarrage du runtime effectue une recherche dans le registre pour déterminer la version du Runtime.|

## <a name="safemode-attribute"></a>safemode (attribut)

|Value|Description|
|-----------|-----------------|
|`false`|Le code de démarrage du runtime recherche dans le registre. Valeur par défaut.|
|`true`|Le code de démarrage du runtime n’examine pas le registre.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`startup`|Contient l' `<requiredRuntime>` élément.|

## <a name="remarks"></a>Notes
 Les applications générées pour prendre en charge uniquement la version 1,0 du Runtime doivent utiliser l’élément `<requiredRuntime>`. Les applications générées à l’aide de la version 1,1 ou ultérieure du Runtime doivent utiliser l’élément `<supportedRuntime>`.

> [!NOTE]
> Si vous utilisez la fonction [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) pour spécifier le fichier de configuration, vous devez utiliser l’élément `<requiredRuntime>` pour toutes les versions du Runtime. L’élément `<supportedRuntime>` est ignoré lorsque vous utilisez [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).

 La chaîne d’attribut `version` doit correspondre au nom du dossier d’installation pour la version spécifiée du .NET Framework. Cette chaîne n’est pas interprétée. Si le code de démarrage du runtime ne trouve pas de dossier correspondant, le runtime n’est pas chargé ; le code de démarrage affiche un message d’erreur et se ferme.

> [!NOTE]
> Le code de démarrage d’une application hébergée dans Microsoft Internet Explorer ignore l’élément `<requiredRuntime>`.

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier la version du runtime dans un fichier de configuration.

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres de démarrage](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Guide pratique pour configurer une application en vue de prendre en charge le .NET Framework 4 ou versions ultérieures](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
