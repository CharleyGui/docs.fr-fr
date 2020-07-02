---
ms.openlocfilehash: 2d0798917b639bc90bf3f78f6fb9f19d0eaf2c71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614542"
---
### <a name="incorrect-implementation-of-memberdescriptorequals"></a>Implémentation incorrecte de MemberDescriptor.Equals

#### <a name="details"></a>Détails

L’implémentation d’origine de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> compare deux propriétés de chaîne différentes des objets comparés : le nom de la catégorie et la chaîne de description. La solution consiste à comparer <xref:System.ComponentModel.MemberDescriptor.Category> du premier objet à <xref:System.ComponentModel.MemberDescriptor.Category> du second, et <xref:System.ComponentModel.MemberDescriptor.Description> du premier à <xref:System.ComponentModel.MemberDescriptor.Description> du second.

#### <a name="suggestion"></a>Suggestion

Si votre application dépend de <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType> qui retourne parfois `false` quand les descripteurs sont équivalents et que vous ciblez .NET Framework 4.6.2 ou version ultérieure, plusieurs options s’offrent à vous :

- Changez le code pour comparer manuellement les champs <xref:System.ComponentModel.MemberDescriptor.Category> et <xref:System.ComponentModel.MemberDescriptor.Description> parallèlement à l’appel de la méthode <xref:System.ComponentModel.MemberDescriptor.Equals%2A?displayProperty=nameWithType>.
- Refusez ce changement en ajoutant la valeur suivante au fichier app.config :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=true" />
</runtime>
```

Si votre application cible .NET Framework 4.6.1 ou version antérieure, qu’elle s’exécute sur .NET Framework 4.6.2 ou version ultérieure et que vous souhaitez activer ce changement, vous pouvez affecter `false` au commutateur de compatibilité en ajoutant la valeur suivante au fichier app.config :

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.MemberDescriptorEqualsReturnsFalseIfEquivalent=false" />
</runtime>
```

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.ComponentModel.MemberDescriptor.Equals(System.Object)?displayProperty=nameWithType>
