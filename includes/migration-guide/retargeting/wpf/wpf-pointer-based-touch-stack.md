---
ms.openlocfilehash: 3463b6c45952aab0023e40921739e84eb51ca001
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859174"
---
### <a name="wpf-pointer-based-touch-stack"></a>Pile tactile basée sur un pointeur WPF

|   |   |
|---|---|
|Détails|Ce changement ajoute la possibilité d’activer une pile facultative tactile/de stylet WPF basée sur WM_POINTER.  Les développeurs qui n’activent pas ceci explicitement ne devraient voir aucun changement de comportement tactile/du stylet dans WPF. Problèmes connus actuels avec la pile facultative tactile/de stylet basée sur WM_POINTER :<ul><li>Pas de prise en charge de l’écriture manuscrite en temps réel.</li><li>Bien que les plug-ins pour l’écriture manuscrite et le stylet fonctionnent toujours, ils sont traités sur le thread d’interface utilisateur, ce qui peut entraîner une baisse des performances.</li><li>Changements de comportement en raison de changements dans la promotion d’événements tactiles/de stylet en événements de souris</li><li>La manipulation peut se comporter différemment</li><li>Le glisser-déplacer ne réagit pas correctement à l’entrée tactile</li><li>Cela n’affecte pas l’entrée du stylet</li><li>Le glisser-déplacer ne peut plus être lancé par des événements tactiles/du stylet</li><li>Cela peut éventuellement bloquer l’application jusqu'à ce que l’entrée de la souris soit détectée.</li><li>Au lieu de cela, les développeurs doivent lancer le glisser-déplacer à partir des événements de souris.</li></ul>|
|Suggestion|Les développeurs qui souhaitent activer cette pile peuvent ajouter/fusionner les éléments suivants dans le fichier App.config de l’application :<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>La suppression de cette entrée ou l’affectation de la valeur false désactive cette pile facultative. Notez que cette pile est uniquement disponible sur Windows 10 Creators Update et ultérieur.|
|Étendue|Edge|
|Version|4,7|
|Type|Reciblage|
