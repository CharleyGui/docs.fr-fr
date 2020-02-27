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
* [Chapitre 8. Normes et réglementations fédérales Red Hat Enterprise Linux 7](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/security_guide/chap-federal_standards_and_regulations)
