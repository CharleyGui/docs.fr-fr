---
title: 'Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3ac43b574c4382c4aec5070acde0fa77516727d
ms.sourcegitcommit: 26f4a7697c32978f6a328c89dc4ea87034065989
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66251148"
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

## <a name="mitigation"></a>Atténuation

Si ce changement n’est pas souhaitable, les applications qui ciblent .NET Framework 4.6.1 ou versions ultérieures peuvent ne pas y adhérer en ajoutant le paramètre de configuration suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

De plus, les applications qui ciblent des versions antérieures du .NET Framework, mais qui s’exécutent sous .NET Framework 4.6.1 ou versions ultérieures peuvent adhérer à ce comportement en ajoutant le paramètre de configuration suivant à la section [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) du fichier de configuration de l’application :

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Voir aussi

- [Modifications de reciblage](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6-1.md)
