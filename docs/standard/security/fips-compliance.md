---
title: Compatibilité FIPS-.NET Core
description: Explique la conformité à la norme FIPS (.NET Core normes FIPS (Federal Information Processing Standard)).
ms.date: 11/20/2019
author: Rick-Anderson
ms.author: riande
ms.openlocfilehash: cf640c857e79ae811dd38d57a0e5301b7bc96572
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74205065"
---
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a><span data-ttu-id="e854e-103">Conformité de .NET Core normes FIPS (Federal Information Processing Standard) (FIPS)</span><span class="sxs-lookup"><span data-stu-id="e854e-103">.NET Core Federal Information Processing Standard (FIPS) compliance</span></span>

<span data-ttu-id="e854e-104">La publication de normes FIPS (Federal Information Processing Standard) (FIPS) 140-2 est une norme gouvernementale américaine qui définit les exigences de sécurité minimales pour les modules cryptographiques dans les produits informatiques, tels que définis dans la section 5131 des informations. La réforme de la gestion des technologies 1996.</span><span class="sxs-lookup"><span data-stu-id="e854e-104">The Federal Information Processing Standard (FIPS) Publication 140-2 is a U.S. government standard that defines minimum security requirements for cryptographic modules in information technology products, as defined in Section 5131 of the Information Technology Management Reform Act of 1996.</span></span>

<span data-ttu-id="e854e-105">.NET Core :</span><span class="sxs-lookup"><span data-stu-id="e854e-105">.NET Core:</span></span>

* <span data-ttu-id="e854e-106">Passe les appels de primitives de chiffrement par le biais des modules standard fournis par le système d’exploitation sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="e854e-106">Passes cryptographic primitives calls through to the standard modules the underlying operating system provides.</span></span>
* <span data-ttu-id="e854e-107">N’applique **pas** l’utilisation d’algorithmes ou de tailles de clé approuvés par FIPS dans les applications .net core.</span><span class="sxs-lookup"><span data-stu-id="e854e-107">Does **not** enforce the use of FIPS Approved algorithms or key sizes in .NET Core apps.</span></span>

<span data-ttu-id="e854e-108">L’administrateur système est responsable de la configuration de la conformité FIPS pour un système d’exploitation.</span><span class="sxs-lookup"><span data-stu-id="e854e-108">The system administrator is responsible for configuring the FIPS compliance for an operating system.</span></span>

<span data-ttu-id="e854e-109">Si le code est écrit pour un environnement conforme aux normes FIPS, le développeur est chargé de s’assurer que les algorithmes FIPS non conformes ne sont pas utilisés.</span><span class="sxs-lookup"><span data-stu-id="e854e-109">If code is written for a FIPS-compliant environment, the developer is responsible for ensuring that non-compliant FIPS algorithms aren't used.</span></span>

<span data-ttu-id="e854e-110">Pour plus d’informations sur la conformité FIPS, consultez les articles suivants :</span><span class="sxs-lookup"><span data-stu-id="e854e-110">For more information on FIPS compliance, see the following articles:</span></span>

* [<span data-ttu-id="e854e-111">Conformité Windows FIPS</span><span class="sxs-lookup"><span data-stu-id="e854e-111">Windows FIPS Compliance</span></span>](/windows/security/threat-protection/fips-140-validation)
* [<span data-ttu-id="e854e-112">Configuration de Windows pour la conformité FIPS</span><span class="sxs-lookup"><span data-stu-id="e854e-112">Configuring Windows for FIPS Compliance</span></span>](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [<span data-ttu-id="e854e-113">10,2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)</span><span class="sxs-lookup"><span data-stu-id="e854e-113">10.2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)</span></span>](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
