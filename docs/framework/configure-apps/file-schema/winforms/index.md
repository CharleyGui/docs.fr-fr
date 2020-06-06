---
title: Section de configuration de Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79151830"
---
# <a name="windows-forms-configuration-section"></a>Section de configuration de Windows Forms
Les paramètres de configuration de Windows Forms permettent à une application Windows Forms de stocker et d’extraire des informations sur les paramètres d’application personnalisés, par exemple la prise en charge de plusieurs écrans, la prise en charge de la haute résolution et d’autres paramètres de configuration prédéfinis.

Les paramètres de configuration de l’application Windows Forms sont stockés dans l’élément `System.Windows.Forms.ApplicationConfigurationSection` d’un fichier de configuration de l’application.

## <a name="syntax"></a>Syntaxe

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a>Attributs et éléments

Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.

### <a name="attributes"></a>Attributs

Aucun.

### <a name="child-elements"></a>Éléments enfants

Élément  |Description |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | Ajoute une clé de paramètre de configuration avec une valeur spécifiée. |

### <a name="parent-elements"></a>Éléments parents

Élément  |Description |
---------|---------|
[\<configuration>](../configuration-element.md) | Élément racine de chaque fichier de configuration utilisé par le common language runtime et les applications Windows Forms. |

## <a name="remarks"></a>Remarques

À compter du .NET Framework 4.7, l’élément `<System.Windows.Forms.ApplicationConfigurationSection>` vous permet de configurer des applications Windows Forms pour tirer parti des fonctionnalités ajoutées dans les dernières versions du .NET Framework.

L' `<System.Windows.Forms.ApplicationConfigurationSection>` élément peut inclure un ou plusieurs [`<add>`](windows-forms-add-configuration-element.md) éléments enfants, chacun d’eux définissant un paramètre de configuration spécifique.

## <a name="see-also"></a>Voir aussi

- [Schéma des fichiers de configuration](../index.md)
- [Prise en charge des résolutions élevées en Windows Forms](../../../winforms/high-dpi-support-in-windows-forms.md)
