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
# <a name="net-core-federal-information-processing-standard-fips-compliance"></a>Conformité de .NET Core normes FIPS (Federal Information Processing Standard) (FIPS)

La publication de normes FIPS (Federal Information Processing Standard) (FIPS) 140-2 est une norme gouvernementale américaine qui définit les exigences de sécurité minimales pour les modules cryptographiques dans les produits informatiques, tels que définis dans la section 5131 des informations. La réforme de la gestion des technologies 1996.

.NET Core :

* Passe les appels de primitives de chiffrement par le biais des modules standard fournis par le système d’exploitation sous-jacent.
* N’applique **pas** l’utilisation d’algorithmes ou de tailles de clé approuvés par FIPS dans les applications .net core.

L’administrateur système est responsable de la configuration de la conformité FIPS pour un système d’exploitation.

Si le code est écrit pour un environnement conforme aux normes FIPS, le développeur est chargé de s’assurer que les algorithmes FIPS non conformes ne sont pas utilisés.

Pour plus d’informations sur la conformité FIPS, consultez les articles suivants :

* [Conformité Windows FIPS](/windows/security/threat-protection/fips-140-validation)
* [Configuration de Windows pour la conformité FIPS](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing)
* [10,2. FEDERAL INFORMATION PROCESSING STANDARD (FIPS)](https://access.redhat.com/documentation/red_hat_enterprise_linux/6/html/security_guide/sect-security_guide-federal_standards_and_regulations-federal_information_processing_standard)
