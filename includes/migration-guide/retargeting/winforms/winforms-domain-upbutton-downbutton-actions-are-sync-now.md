---
ms.openlocfilehash: c64431fd651fd7d53fb46231c6acc10c5cb43fff
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606810"
---
### <a name="winforms-domain-upbutton-and-downbutton-actions-are-in-sync-now"></a>Les actions upbutton et downbutton Domain de WinForm sont désormais synchronisées

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.1 et versions antérieures, l’action <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> du contrôle <xref:System.Windows.Forms.DomainUpDown> est ignorée quand le texte du contrôle est présent, obligeant le développeur à utiliser l’action <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> sur le contrôle avant d’utiliser l’action <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>. À compter de .NET Framework 4.7.2, les actions <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType> et <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType> fonctionnent indépendamment dans ce scénario et restent synchronisées.

#### <a name="suggestion"></a>Suggestion

Une application doit s’exécuter sur .NET Framework 4.7.2 ou ultérieur pour tirer parti de ces changements. Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :

- Recompilez-la pour qu’elle cible .NET Framework 4.7.2. Ce changement est activé par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.7.2 ou ultérieur.
- Refusez le comportement de défilement hérité en ajoutant le [commutateur AppContext](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant à la section `<runtime>` du fichier de configuration de l’application et en lui affectant la valeur `false`, comme dans l’exemple suivant.

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Windows.Forms.DomainUpDown.UpButton?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DomainUpDown.DownButton?displayProperty=nameWithType>
