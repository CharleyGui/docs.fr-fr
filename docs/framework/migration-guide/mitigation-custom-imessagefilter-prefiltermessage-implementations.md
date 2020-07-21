---
title: 'Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées'
description: En savoir plus sur le implémentation personnalisé IMessageFilter. PreFilterMessage personnalisées inclus dans les applications Windows Forms qui ciblent .NET Framework 4.6.1 et versions ultérieures.
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 5fe7500d3ed6ff293514495df150a747e7946dda
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475253"
---
# <a name="mitigation-custom-imessagefilterprefiltermessage-implementations"></a>Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées

Dans les applications Windows Forms qui ciblent des versions du .NET Framework à partir de .NET Framework 4.6.1, une implémentation personnalisée de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> peut en toute sécurité filtrer les messages quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée si l’implémentation de <xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A?displayProperty=nameWithType> :

- Effectue l’une des actions suivantes ou les deux :

  - Ajout d’un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.AddMessageFilter%2A>.

  - Suppression d’un filtre de message en appelant la méthode <xref:System.Windows.Forms.Application.RemoveMessageFilter%2A>. .

- **Et** pompe des messages en appelant la méthode <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType>.

## <a name="impact"></a>Impact

Ce changement affecte uniquement les applications Windows Forms qui ciblent .NET Framework 4.6.1 et versions ultérieures.

Pour les applications Windows Forms qui ciblent des versions antérieures du .NET Framework, de telles implémentations lèvent dans certains cas une exception <xref:System.IndexOutOfRangeException> quand la méthode <xref:System.Windows.Forms.Application.FilterMessage%2A?displayProperty=nameWithType> est appelée.

## <a name="mitigation"></a>Limitation des risques

Si cette modification n’est pas souhaitable, les applications qui ciblent le .NET Framework 4.6.1 ou une version ultérieure peuvent la refuser en ajoutant le paramètre de configuration suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

En outre, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sous le .NET Framework 4.6.1 ou une version ultérieure, peuvent accepter ce comportement en ajoutant le paramètre de configuration suivant à la [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application :

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
