---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855662"
---
> [!CAUTION]
> Sécurité d’accès du code (CAS) et code de confiance partielle
>
> Le .NET Framework fournit un mécanisme, appelé « sécurité d'accès du code (CAS) », qui permet de mettre en œuvre différents niveaux de confiance sur différents codes exécutés dans la même application.
>
> **Les autorités de certification ne sont pas prises en charge dans .NET Core, .NET 5 ou versions ultérieures. Les autorités de certification ne sont pas prises en charge par les versions de C# ultérieures à 7,0.**
>
> Dans .NET Framework, les autorités de certification ne doivent pas être utilisées comme mécanisme pour appliquer des limites de sécurité basées sur l’origine du code ou d’autres aspects de l’identité. Les autorités de certification et le code transparent de sécurité ne sont pas pris en charge comme limite de sécurité avec du code d’un niveau de confiance partiel, en particulier le code d’origine inconnue. Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité.
>
> Cette stratégie s'applique à toutes les versions du .NET Framework, mais ne concerne pas le .NET Framework inclus dans Silverlight.
