---
ms.openlocfilehash: 3164233f1ac056de385faa119143d75d3c2dc50c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224339"
---
> [!CAUTION]
> <span data-ttu-id="a8d3e-101">Sécurité d’accès du code (CAS) et code de confiance partielle</span><span class="sxs-lookup"><span data-stu-id="a8d3e-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="a8d3e-102">Le .NET Framework fournit un mécanisme, appelé « sécurité d'accès du code (CAS) », qui permet de mettre en œuvre différents niveaux de confiance sur différents codes exécutés dans la même application.</span><span class="sxs-lookup"><span data-stu-id="a8d3e-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="a8d3e-103">**Les autorités de certification ne sont pas prises en charge dans .NET Core, .NET 5 ou versions ultérieures. Les autorités de certification ne sont pas prises en charge par les versions de C# ultérieures à 7,0.**</span><span class="sxs-lookup"><span data-stu-id="a8d3e-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="a8d3e-104">Dans .NET Framework, les autorités de certification ne doivent pas être utilisées comme mécanisme pour appliquer des limites de sécurité basées sur l’origine du code ou d’autres aspects de l’identité.</span><span class="sxs-lookup"><span data-stu-id="a8d3e-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="a8d3e-105">Le code CAS et Security-Transparent ne sont pas pris en charge comme limite de sécurité avec du code d’un niveau de confiance partiel, en particulier le code d’origine inconnue.</span><span class="sxs-lookup"><span data-stu-id="a8d3e-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="a8d3e-106">Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité.</span><span class="sxs-lookup"><span data-stu-id="a8d3e-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="a8d3e-107">.NET Framework n’émet pas de correctifs de sécurité pour les attaques d’élévation de privilège qui peuvent être découvertes sur le bac à sable (sandbox).</span><span class="sxs-lookup"><span data-stu-id="a8d3e-107">.NET Framework will not issue security patches for any elevation-of-privilege exploits that might be discovered against the CAS sandbox.</span></span>
>
> <span data-ttu-id="a8d3e-108">Cette stratégie s'applique à toutes les versions du .NET Framework, mais ne concerne pas le .NET Framework inclus dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a8d3e-108">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
