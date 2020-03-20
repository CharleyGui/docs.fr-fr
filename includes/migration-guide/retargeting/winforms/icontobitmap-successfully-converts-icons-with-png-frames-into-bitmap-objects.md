---
ms.openlocfilehash: f4a5911787fa5f72be1dcd15c67b3f132c3f1110
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67804580"
---
### <a name="icontobitmap-successfully-converts-icons-with-png-frames-into-bitmap-objects"></a>Icon.ToBitmap convertit correctement les icônes dotées de cadres PNG en objets Bitmap

|   |   |
|---|---|
|Détails|À compter des applications qui ciblent .NET Framework 4.6, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> convertit correctement en objets Bitmap les icônes comportant des cadres PNG.<p/>Dans les applications qui ciblent .NET Framework 4.5.2 et versions antérieures, la méthode <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> lève une exception <xref:System.ArgumentOutOfRangeException> si l’objet Icon comporte des cadres PNG.<p/>Ce changement affecte les applications qui sont recompilées pour cibler .NET Framework 4.6 et qui implémentent un traitement spécial pour l’exception <xref:System.ArgumentOutOfRangeException> qui est levée quand un objet Icon comporte des cadres PNG. Dans le cadre d’une exécution sous le .NET Framework 4.6, la conversion aboutit, il n’est plus levé d’exception <xref:System.ArgumentOutOfRangeException> et, de ce fait, le gestionnaire d’exceptions n’est plus appelé.|
|Suggestion|Si ce comportement est indésirable, vous pouvez conserver le comportement précédent en ajoutant l’élément suivant à la section <code>&lt;runtime&gt;</code> de votre fichier app.config :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true&quot; /&gt;&#13;&#10;</code></pre>Si le fichier app.config contient déjà l’élément <code>AppContextSwitchOverrides</code>, la nouvelle valeur doit être fusionnée avec l’attribut value comme ceci :<pre><code class="lang-xml">&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Drawing.DontSupportPngFramesInIcons=true;&lt;previous key&gt;=&lt;previous value&gt;&quot; /&gt;&#13;&#10;</code></pre>|
|Étendue|Secondaire|
|Version|4.6|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.Drawing.Icon.ToBitmap?displayProperty=nameWithType></li></ul>|
