---
ms.openlocfilehash: 01c0689bbfb102f8f4d9455f9d258e8ea5515d9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859310"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Implémentation incorrecte de MemberDescriptor.Equals

|   |   |
|---|---|
|Détails|L’implémentation d’origine de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> compare deux propriétés de chaîne différentes des objets comparés : le nom de la catégorie et la chaîne de description. La solution consiste à comparer <xref:System.ComponentModel.MemberDescriptor.Category> du premier objet à <xref:System.ComponentModel.MemberDescriptor.Category> du second, et <xref:System.ComponentModel.MemberDescriptor.Description> du premier à <xref:System.ComponentModel.MemberDescriptor.Description> du second.|
|Suggestion|Si votre application dépend de <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> qui retourne parfois <code>false</code> quand les descripteurs sont équivalents et que vous ciblez .NET Framework 4.6.2 ou version ultérieure, plusieurs options s’offrent à vous :<ol><li>Changez le code pour comparer manuellement les champs <xref:System.ComponentModel.MemberDescriptor.Category> et <xref:System.ComponentModel.MemberDescriptor.Description> parallèlement à l’appel de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType>.</li><li>Refusez ce changement en ajoutant la valeur suivante au fichier app.config :</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Si votre application cible .NET Framework 4.6.1 ou version antérieure, qu’elle s’exécute sur .NET Framework 4.6.2 ou version ultérieure et que vous souhaitez activer ce changement, vous pouvez affecter <code>false</code> au commutateur de compatibilité en ajoutant la valeur suivante au fichier app.config :<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4.6.2|
|Type|Reciblage|
|API affectées|<ul><li><xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType></li></ul>|
