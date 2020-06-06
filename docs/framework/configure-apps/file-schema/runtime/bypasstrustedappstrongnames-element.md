---
title: Élément <bypassTrustedAppStrongNames>
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- bypassTrustedAppStrongNames element
- strong-named assemblies, loading into trusted application domains
- <bypassTrustedAppStrongNames> element
ms.assetid: 71b2ebf6-3843-41e2-ad52-ffa5cd083a40
ms.openlocfilehash: 96361a6742d1d2f76cb237344189d3277d7c8069
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739084"
---
# <a name="bypasstrustedappstrongnames-element"></a>Élément \<bypassTrustedAppStrongNames>

Spécifie s’il faut ignorer la validation des noms forts sur les assemblys de confiance totale qui sont chargés dans un niveau de confiance totale <xref:System.AppDomain> .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<bypassTrustedAppStrongNames>**

## <a name="syntax"></a>Syntaxe

```xml
<bypassTrustedAppStrongNames
   enabled="true|false"/>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

|Attribut|Description|
|---------------|-----------------|
|`enabled`|Attribut requis.<br /><br /> Spécifie si la fonctionnalité de contournement qui évite de valider des noms forts pour les assemblys de confiance totale est activée. Lorsque cette fonctionnalité est activée, les noms forts ne sont pas validés pour être corrects lorsque l’assembly est chargé. Par défaut, il s’agit de `true`.|

## <a name="enabled-attribute"></a>Attribut enabled

|Valeur|Description|
|-----------|-----------------|
|`true`|Les signatures avec nom fort sur les assemblys de confiance totale ne sont pas validées lorsque les assemblys sont chargés dans un niveau de confiance totale <xref:System.AppDomain> . Il s'agit de la valeur par défaut.|
|`false`|Les signatures avec nom fort sur les assemblys de confiance totale sont validées lorsque les assemblys sont chargés dans un niveau de confiance totale <xref:System.AppDomain> . La signature de nom fort est vérifiée uniquement pour l’exactitude de la signature ; elle n’est pas comparée à un autre nom fort pour une correspondance.|

### <a name="child-elements"></a>Éléments enfants

Aucun.

### <a name="parent-elements"></a>Éléments parents

|Élément|Description|
|-------------|-----------------|
|`configuration`|Élément racine de chaque fichier de configuration utilisé par le Common Language Runtime et les applications .NET Framework.|
|`runtime`|Contient des informations sur les liaisons d’assembly et l’opération garbage collection.|

## <a name="remarks"></a>Remarques

La fonctionnalité de contournement de nom fort évite la surcharge liée à la vérification de signature de nom fort des assemblys de confiance totale.

Cette fonctionnalité s’applique à tout assembly signé avec un nom fort qui présente les caractéristiques suivantes :

- Confiance totale sans <xref:System.Security.Policy.StrongName> preuve (par exemple, a une `MyComputer` preuve de zone).

- Chargé dans un <xref:System.AppDomain> de confiance totale.

- Chargé à partir d'un emplacement sous la propriété <xref:System.AppDomainSetup.ApplicationBase%2A> de cet <xref:System.AppDomain>.

- Sans signature différée.

> [!NOTE]
> Si la fonctionnalité de contournement a été désactivée pour toutes les applications sur l’ordinateur à l’aide d’une clé de Registre, ce paramètre de fichier de configuration n’a aucun effet. Pour plus d’informations, consultez [Comment : désactiver la fonctionnalité de contournement de nom fort](../../../../standard/assembly/disable-strong-name-bypass-feature.md).

## <a name="example"></a>Exemple

L’exemple suivant montre comment spécifier le comportement qui valide la signature de nom fort sur les assemblys de confiance totale.

```xml
<configuration>
   <runtime>
      <bypassTrustedAppStrongNames enabled="false"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>Voir aussi

- [Schéma des paramètres d’exécution](index.md)
- [Schéma des fichiers de configuration](../index.md)
- [Comment : désactiver la fonctionnalité de contournement de nom fort](../../../../standard/assembly/disable-strong-name-bypass-feature.md)
