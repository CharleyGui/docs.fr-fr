---
ms.openlocfilehash: 53860bb867522503c5cb9bd35e25fadd00a116a2
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91609157"
---
### <a name="multi-line-aspnet-textbox-spacing-changed-when-using-antixssencoder"></a>L’espacement de zone de texte ASP.NET sur plusieurs lignes a changé lors de l’utilisation de AntiXSSEncoder

#### <a name="details"></a>Détails

Dans le .NET Framework 4.0, des lignes supplémentaires étaient insérées dans la zone de texte multiligne lors de la publication (postback), quand vous utilisiez <xref:System.Web.Security.AntiXss.AntiXssEncoder?displayProperty=fullName>. Dans .NET Framework 4.5, ces sauts de ligne supplémentaires ne sont pas inclus si l’application web cible .NET Framework 4.5.

#### <a name="suggestion"></a>Suggestion

Notez que les applications web 4.0 reciblées vers .NET Framework 4.5 peuvent avoir des zones de texte multilignes améliorées qui ne comportent plus de sauts de ligne supplémentaires. Si vous ne souhaitez pas ce changement, vous pouvez obtenir l’ancien comportement dans .NET Framework 4.5 en ciblant .NET Framework 4.0.

| Name    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4.5         |
| Type    | Reciblage |
