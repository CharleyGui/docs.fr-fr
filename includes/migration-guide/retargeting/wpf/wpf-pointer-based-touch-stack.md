---
ms.openlocfilehash: bb3d7c1afa9e506ffc7c6d068c48428d1e66ccb6
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66379456"
---
### <a name="wpf-pointer-based-touch-stack"></a>Pile tactile basée sur un pointeur WPF

|   |   |
|---|---|
|Détails|Ce changement ajoute la possibilité d’activer une pile facultative tactile/de stylet WPF basée sur WM_POINTER.  Les développeurs qui n’activent pas ceci explicitement ne devraient voir aucun changement de comportement tactile/du stylet dans WPF. Problèmes connus actuels avec la pile facultative tactile/de stylet basée sur WM_POINTER :<ul><li>Pas de prise en charge de l’écriture manuscrite en temps réel.</li><li>Bien que les plug-ins pour l’écriture manuscrite et le stylet fonctionnent toujours, ils sont traités sur le thread d’interface utilisateur, ce qui peut entraîner une baisse des performances.</li><li>Changements de comportement en raison de changements dans la promotion d’événements tactiles/de stylet en événements de souris</li><li>La manipulation peut se comporter différemment</li><li>Le glisser-déplacer ne réagit pas correctement à l’entrée tactile</li><li>Cela n’affecte pas l’entrée du stylet</li><li>Le glisser-déplacer ne peut plus être lancé par des événements tactiles/du stylet</li><li>Cela peut éventuellement entraîner une absence de réponse de la part de l’application jusqu’à ce que l’entrée de la souris soit détectée.</li><li>Au lieu de cela, les développeurs doivent lancer le glisser-déplacer à partir des événements de souris.</li></ul>|
|Suggestion|Les développeurs qui souhaitent activer cette pile peuvent ajouter/fusionner les éléments suivants dans le fichier App.config de l’application :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>La suppression de cette entrée ou l’affectation de la valeur false désactive cette pile facultative. Notez que cette pile est uniquement disponible sur Windows 10 Creators Update et ultérieur.|
|Portée|Microsoft Edge|
|Version|4.7|
|Type|Reciblage|
