---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855662"
---
> [!CAUTION]
> <span data-ttu-id="03d1e-101">Sécurité d’accès du code (CAS) et code de confiance partielle</span><span class="sxs-lookup"><span data-stu-id="03d1e-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="03d1e-102">Le .NET Framework fournit un mécanisme, appelé « sécurité d'accès du code (CAS) », qui permet de mettre en œuvre différents niveaux de confiance sur différents codes exécutés dans la même application.</span><span class="sxs-lookup"><span data-stu-id="03d1e-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="03d1e-103">**Les autorités de certification ne sont pas prises en charge dans .NET Core, .NET 5 ou versions ultérieures. Les autorités de certification ne sont pas prises en charge par les versions de C# ultérieures à 7,0.**</span><span class="sxs-lookup"><span data-stu-id="03d1e-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="03d1e-104">Dans .NET Framework, les autorités de certification ne doivent pas être utilisées comme mécanisme pour appliquer des limites de sécurité basées sur l’origine du code ou d’autres aspects de l’identité.</span><span class="sxs-lookup"><span data-stu-id="03d1e-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="03d1e-105">Les autorités de certification et le code transparent de sécurité ne sont pas pris en charge comme limite de sécurité avec du code d’un niveau de confiance partiel, en particulier le code d’origine inconnue.</span><span class="sxs-lookup"><span data-stu-id="03d1e-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="03d1e-106">Nous vous déconseillons de charger et d'exécuter du code d'origine inconnue sans mettre en place d'autres mesures de sécurité.</span><span class="sxs-lookup"><span data-stu-id="03d1e-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="03d1e-107">Cette stratégie s'applique à toutes les versions du .NET Framework, mais ne concerne pas le .NET Framework inclus dans Silverlight.</span><span class="sxs-lookup"><span data-stu-id="03d1e-107">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
