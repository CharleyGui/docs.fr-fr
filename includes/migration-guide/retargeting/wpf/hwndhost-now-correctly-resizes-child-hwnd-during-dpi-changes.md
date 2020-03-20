---
ms.openlocfilehash: b92086c8ccf7592ce70b75bd31d4ea255c35b543
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803453"
---
### <a name="hwndhost-now-correctly-resizes-child-hwnd-during-dpi-changes"></a>HwndHost redimensionne correctement le HWND enfant lors de changements DPI

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.7.2 et versions antérieures, quand WPF était exécuté en mode Par moniteur, les contrôles hébergés dans <xref:System.Windows.Interop.HwndHost> n’étaient pas dimensionnés correctement après des changements DPI, par exemple quand vous passiez des applications d’un écran à un autre. Ce correctif garantit que les contrôles hébergés sont dimensionnés correctement.|
|Suggestion|Pour que l’application tire parti de ces changements, elle doit s’exécuter sur .NET Framework 4.7.2 ou ultérieur et adhérer à ce comportement en définissant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant de la section <code>&lt;runtime&gt;</code> du fichier de configuration d’application sur <code>false</code>, comme le montre l’exemple suivant.<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Étendue|Majeure|
|Version|4.8|
|Type|Reciblage|
