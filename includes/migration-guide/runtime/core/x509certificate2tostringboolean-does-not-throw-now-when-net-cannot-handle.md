---
ms.openlocfilehash: 51208762cea2a5688c5d43e5d444d4e014e5f0b4
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621323"
---
### <a name="x509certificate2tostringboolean-does-not-throw-now-when-net-cannot-handle-the-certificate"></a>X509Certificate2.ToString(Boolean) ne lève plus d’exception quand .NET ne peut pas gérer le certificat

#### <a name="details"></a>Détails

Dans .NET Framework 4.5.2 et antérieur, cette méthode levait une exception quand la valeur <code>true</code> était passée au paramètre verbose alors que des certificats non pris en charge par le .NET Framework étaient installés. À présent, la méthode n’échoue plus et retourne une chaîne valide qui omet les parties inaccessibles du certificat.

#### <a name="suggestion"></a>Suggestion

Le code qui dépend de <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType> doit être mis à jour pour s’attendre à ce que la chaîne retournée omette certaines données du certificat (telles que la clé publique, la clé privée et les extensions), ce qui aurait auparavant entraîné la levée d’une exception par l’API.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   |Edge|
|Version|4.6|
|Type|Runtime

#### <a name="affected-apis"></a>API affectées

-<xref:System.Security.Cryptography.X509Certificates.X509Certificate2.ToString(System.Boolean)?displayProperty=nameWithType></li></ul>|
