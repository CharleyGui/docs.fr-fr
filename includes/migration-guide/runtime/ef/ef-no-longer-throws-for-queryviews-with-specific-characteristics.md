---
ms.openlocfilehash: 705e1a22b8a5791c1103dd374a8bab19356cadfb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67803255"
---
### <a name="ef-no-longer-throws-for-queryviews-with-specific-characteristics"></a>EF ne lève plus d’exception pour des QueryView avec des caractéristiques spécifiques

|   |   |
|---|---|
|Détails|Entity Framework ne lève plus une exception <xref:System.StackOverflowException?displayProperty=name> quand une application exécute une requête qui implique un QueryView avec une propriété de navigation 0..1 qui tente d’inclure les entités associées dans le cadre de la requête, par exemple en appelant <code>.Include(e =&gt; e.RelatedNavProp)</code>.|
|Suggestion|Cette modification affecte uniquement le code qui utilise des QueryView avec des relations 1-0..1 pour exécuter des requêtes qui appellent .Include. Elle permet d'améliorer la fiabilité et doit être transparente pour presque toutes les applications. Toutefois, si elle entraîne un comportement inattendu, vous pouvez la désactiver en ajoutant l'entrée suivante à la section <code>&lt;appSettings&gt;</code> du fichier de configuration de l'application :<pre><code class="lang-xml">&lt;add key=&quot;EntityFramework_SimplifyUserSpecifiedViews&quot; value=&quot;false&quot; /&gt;&#13;&#10;</code></pre>|
|Étendue|Edge|
|Version|4.5.2|
|Type|Runtime|
