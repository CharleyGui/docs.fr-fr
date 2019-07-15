---
ms.openlocfilehash: db8eb017bdf166b0f1a241f5a8f7db9b9430898a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859131"
---
### <a name="throttle-concurrent-requests-per-session"></a>Restriction des demandes simultanées par session

|   |   |
|---|---|
|Détails|Dans .NET Framework 4.6.2 et les versions antérieures, ASP.NET exécute les requêtes séquentiellement avec le même SessionId et émet toujours SessionId par le biais de cookies par défaut. Si une page met beaucoup de temps à répondre, cela entraînera une dégradation sensible des performances du serveur en appuyant simplement sur F5 dans le navigateur. Dans le correctif, nous avons ajouté un compteur pour effectuer le suivi des requêtes en file d’attente et arrêter les requêtes quand elles dépassent une limite spécifiée. La valeur par défaut est 50. Si la limite est atteinte, un avertissement est journalisé dans le journal des événements et une réponse HTTP 500 peut être enregistrée dans le journal IIS.|
|Suggestion|Pour restaurer l’ancien comportement, vous pouvez ajouter le paramètre suivant à votre fichier web.config pour désactiver le nouveau comportement.<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|Portée|Microsoft Edge|
|Version|4.7|
|Type|Reciblage|

