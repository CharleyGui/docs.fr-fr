---
ms.openlocfilehash: 7d7424b3ca0d295022999e95ed9862b5226b6220
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90606675"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute est exporté à la fois comme ObsoleteAttribute et comme DeprecatedAttribute dans les scénarios WinMD

#### <a name="details"></a>Détails

Quand vous créez une bibliothèque de métadonnées Windows (fichier .winmd), l’attribut <xref:System.ObsoleteAttribute?displayProperty=fullName> est exporté à la fois comme <xref:System.ObsoleteAttribute?displayProperty=fullName> et comme [Windows.Foundation.DeprecatedAttribute](/uwp/api/windows.foundation.metadata.deprecatedattribute).

#### <a name="suggestion"></a>Suggestion

La recompilation de code source existant qui utilise l’attribut <xref:System.ObsoleteAttribute?displayProperty=fullName> peut générer des avertissements quand ce code est consommé à partir de C++/CX ou de JavaScript. Nous déconseillons d’appliquer à la fois <xref:System.ObsoleteAttribute?displayProperty=fullName> et [Windows.Foundation.DeprecatedAttribute](/uwp/api/windows.foundation.metadata.deprecatedattribute) au code d’assemblys managés, car cela peut produire des avertissements de génération.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.5.1       |
| Type    | Reciblage |
