---
ms.openlocfilehash: 77e231f8ef1dde8a263b8622311099a4a404062d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606376"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost redimensionne correctement le HWND enfant lors de changements DPI

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.2 et versions antérieures, quand WPF était exécuté en mode Par moniteur, les contrôles hébergés dans <xref:System.Windows.Interop.HwndHost> n’étaient pas dimensionnés correctement après des changements DPI, par exemple quand vous passiez des applications d’un écran à un autre. Ce correctif garantit que les contrôles hébergés sont dimensionnés correctement.

#### <a name="suggestion"></a>Suggestion

Pour que l’application tire parti de ces changements, elle doit s’exécuter sur .NET Framework 4.7.2 ou ultérieur et adhérer à ce comportement en définissant le [commutateur AppContext](../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) suivant de la section `<runtime>` du fichier de configuration d’application sur `false`, comme le montre l’exemple suivant.

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Majeure       |
| Version | 4.8         |
| Type    | Reciblage |
