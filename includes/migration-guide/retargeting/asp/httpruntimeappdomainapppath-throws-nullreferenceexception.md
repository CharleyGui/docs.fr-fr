---
ms.openlocfilehash: 986b647047aaa4a185c1403e96e499ae587bea98
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617529"
---
### <a name="httpruntimeappdomainapppath-throws-a-nullreferenceexception"></a>HttpRuntime.AppDomainAppPath lève une exception NullReferenceException

#### <a name="details"></a>Détails

Dans .NET Framework 4.6.2, le runtime lève un `T:System.NullReferenceException` quand vous récupérez une valeur `P:System.Web.HttpRuntime.AppDomainAppPath` qui inclut des caractères null. Dans .NET Framework 4.6.1 et les versions antérieures, le runtime lève un `T:System.ArgumentNullException`.

#### <a name="suggestion"></a>Suggestion

Vous pouvez effectuer l’une ou l’autre des opérations suivantes pour répondre à ce changement :

- Gérer `T:System.NullReferenceException` si votre application s’exécute sur .NET Framework 4.6.2.
- Effectuer une mise à niveau vers .NET Framework 4.7, qui restaure le comportement précédent et lève un `T:System.ArgumentNullException`.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4.6.2       |
| Type    | Reciblage |

#### <a name="affected-apis"></a>API affectées

- <xref:System.Web.HttpRuntime.AppDomainAppPath?displayProperty=nameWithType>
