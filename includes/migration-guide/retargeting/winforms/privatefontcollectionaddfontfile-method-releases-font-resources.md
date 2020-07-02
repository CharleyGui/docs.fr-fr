---
ms.openlocfilehash: 53ded5ae6e5a025fc7992da099c3481587bb6f31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614579"
---
### <a name="privatefontcollectionaddfontfile-method-releases-font-resources"></a>La méthode PrivateFontCollection.AddFontFile libère les ressources de police

#### <a name="details"></a>Détails

Dans .NET Framework 4.7.1 et versions antérieures, une fois le <xref:System.Drawing.Text.PrivateFontCollection> supprimé pour les objets <xref:System.Drawing.Font>, la classe <xref:System.Drawing.Text.PrivateFontCollection?displayProperty=nameWithType> ne libère pas les ressources de police GDI+ qui sont ajoutées à cette collection à l’aide de la méthode <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)>. Dans .NET Framework 4.7.2 et versions ultérieures, <xref:System.Drawing.Text.FontCollection.Dispose%2A> libère les polices GDI+ qui ont été ajoutées à la collection en tant que fichiers.

#### <a name="suggestion"></a>Suggestion

**Comment accepter ou refuser ces modifications** Pour qu’une application tire parti de ces modifications, elle doit s’exécuter sur le .NET Framework 4.7.2 ou version ultérieure. Pour que l’application bénéficie de ces changements, procédez de l’une des manières suivantes :

- Recompilez-la pour qu’elle cible .NET Framework 4.7.2. Ce changement est activé par défaut sur les applications Windows Forms qui ciblent .NET Framework 4.7.2 ou ultérieur.
- Faites-lui cibler .NET Framework version 4.7.1 ou antérieure et refusez les comportements d’accessibilité hérités en ajoutant le [commutateur AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) suivant à la section `<runtime>` du fichier app.config et en lui affectant la valeur `false`, comme dans l’exemple suivant.

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Drawing.Text.DoNotRemoveGdiFontsResourcesFromFontCollection=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

Si votre application cible .NET Framework 4.7.2 ou une version ultérieure et que vous souhaitez conserver le comportement hérité, choisissez de ne pas libérer les ressources de police en affectant explicitement à ce commutateur AppContext la valeur `true`.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.7.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Drawing.Text.PrivateFontCollection.AddFontFile(System.String)?displayProperty=nameWithType>
- <xref:System.Drawing.Text.FontCollection.Dispose?displayProperty=nameWithType>
