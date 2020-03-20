---
title: 'Atténuation : implémentations IMessageFilter.PreFilterMessage personnalisées'
ms.date: 03/30/2017
ms.assetid: 9cf47c5b-0bb2-45df-9437-61cd7e7c2f4d
ms.openlocfilehash: 7757e8d1fd0258ab2d972b7321082e4afa37f710
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400119"
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

Si cette modification n’est pas souhaitable, les applications qui ciblent le cadre .NET 4.6.1 ou [ \<](../configure-apps/file-schema/runtime/runtime-element.md) une version ultérieure peuvent s’en retirer en ajoutant le paramètre de configuration suivant à la section>de configuration de l’application :

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=true" />
</runtime>
```

En outre, les applications qui ciblent les versions précédentes du cadre .NET mais sont en cours d’exécution sous le cadre .NET 4.6.1 ou une version ultérieure peuvent opter pour ce comportement en ajoutant le paramètre de configuration suivant à [ \<l’heure d’exécution>](../configure-apps/file-schema/runtime/runtime-element.md) section du fichier de configuration de l’application:

```xml
<runtime>
    <AppContextSwitchOverrides value="Switch.System.Windows.Forms.DontSupportReentrantFilterMessage=false" />
</runtime>
```

## <a name="see-also"></a>Voir aussi

- [Compatibilité des applications](application-compatibility.md)
