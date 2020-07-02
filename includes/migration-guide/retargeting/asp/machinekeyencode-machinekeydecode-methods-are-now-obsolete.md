---
ms.openlocfilehash: e9d34465970287ed94c0f0373ee4ae94d55aa1ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617176"
---
### <a name="machinekeyencode-and-machinekeydecode-methods-are-now-obsolete"></a>Les méthodes MachineKey.Encode et MachineKey.Decode sont maintenant obsolètes

#### <a name="details"></a>Détails

Ces méthodes sont désormais obsolètes. La compilation du code qui appelle ces méthodes génère un avertissement du compilateur.

#### <a name="suggestion"></a>Suggestion

Les alternatives recommandées sont <xref:System.Web.Security.MachineKey.Protect(System.Byte[],System.String[])> et <xref:System.Web.Security.MachineKey.Unprotect(System.Byte[],System.String[])>. Vous pouvez également supprimer les avertissements de génération, ou les éviter en utilisant un compilateur plus ancien. Ces API sont toujours prises en charge.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4,5         |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.Security.MachineKey.Encode(System.Byte[],System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
- <xref:System.Web.Security.MachineKey.Decode(System.String,System.Web.Security.MachineKeyProtection)?displayProperty=nameWithType>
