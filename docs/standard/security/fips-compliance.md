---
title: Compatibilité FIPS-.NET Core
description: Explique la conformité à la norme FIPS (.NET Core normes FIPS (Federal Information Processing Standard)).
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: 84d6edc6975af0484bb67999ad5891eaf4db057d
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626956"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="27d4e-103">Conformité de .NET Core normes FIPS (Federal Information Processing Standard) (FIPS)</span><span class="sxs-lookup"><span data-stu-id="27d4e-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="27d4e-104">La publication de normes FIPS (Federal Information Processing Standard) (FIPS) 140-2 est une norme gouvernementale américaine qui définit les exigences de sécurité minimales pour les modules cryptographiques dans les produits informatiques, tels que définis dans la section 5131 des informations. La réforme de la gestion des technologies 1996.</span><span class="sxs-lookup"><span data-stu-id="27d4e-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="27d4e-105">.NET Core :</span><span class="sxs-lookup"><span data-stu-id="27d4e-105">.NET Core:</span></span>

* <span data-ttu-id="27d4e-106">Passe les appels de primitives de chiffrement par le biais des modules standard fournis par le système d’exploitation sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="27d4e-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="27d4e-107">N’applique **pas** l’utilisation d’algorithmes ou de tailles de clé approuvés par FIPS dans les applications .net core.</span><span class="sxs-lookup"><span data-stu-id="27d4e-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="27d4e-108">L’administrateur système est responsable de la configuration de la conformité FIPS pour un système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="27d4e-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="27d4e-109">Si le code est écrit pour un environnement conforme aux normes FIPS, le développeur est chargé de s’assurer que les algorithmes FIPS non conformes ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="27d4e-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="27d4e-110">Pour plus d’informations sur la conformité FIPS, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="27d4e-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="27d4e-111">Conformité Windows FIPS</span><span class="sxs-lookup"><span data-stu-id="27d4e-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="27d4e-112">Configuration de Windows pour la conformité FIPS</span><span class="sxs-lookup"><span data-stu-id="27d4e-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="27d4e-113">Chapitre 8. Normes et réglementations fédérales Red Hat Enterprise Linux 7</span><span class="sxs-lookup"><span data-stu-id="27d4e-113">Chapter 8. Federal Standards and Regulations Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
