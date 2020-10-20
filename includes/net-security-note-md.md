---
ms.openlocfilehash: 3164233f1ac056de385faa119143d75d3c2dc50c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224339"
---
> [!CAUTION]
> Sécurité d’accès du code (CAS) et code de confiance partielle
>
> Le .NET Framework fournit un mécanisme, appelé « sécurité d'accès du code (CAS) », qui permet de mettre en œuvre différents niveaux de confiance sur différents codes exécutés dans la même application.
>
> **Les autorités de certification ne sont pas prises en charge dans .NET Core, .NET 5 ou versions ultérieures. Les autorités de certification ne sont pas prises en charge par les versions de C# ultérieures à 7,0.**
>
> Dans .NET Framework, les autorités de certification ne doivent pas être utilisées comme mécanisme pour appliquer des limites de sécurité basées sur l’origine du code ou d’autres aspects de l’identité. Le code CAS et Security-Transparent ne sont pas pris en charge comme limite de sécurité avec du code d’un niveau de confiance partiel, en particulier le code d’origine inconnue. Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité. .NET Framework n’émet pas de correctifs de sécurité pour les attaques d’élévation de privilège qui peuvent être découvertes sur le bac à sable (sandbox).
>
> Cette stratégie s'applique à toutes les versions du .NET Framework, mais ne concerne pas le .NET Framework inclus dans Silverlight.
