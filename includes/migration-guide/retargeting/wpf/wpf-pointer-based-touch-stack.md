---
ms.openlocfilehash: eb89cbc72d8b09fd1aa5bc775a6c539eb208fa70
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614575"
---
### <a name="wpf-pointer-based-touch-stack"></a>Pile tactile basée sur un pointeur WPF

#### <a name="details"></a>Détails

Ce changement ajoute la possibilité d’activer une pile facultative tactile/de stylet WPF basée sur WM_POINTER.  Les développeurs qui n’activent pas ceci explicitement ne devraient voir aucun changement de comportement tactile/du stylet dans WPF. Problèmes connus actuels avec la pile facultative tactile/de stylet basée sur WM_POINTER :

- Pas de prise en charge de l’écriture manuscrite en temps réel.
- Bien que les plug-ins pour l’écriture manuscrite et le stylet fonctionnent toujours, ils sont traités sur le thread d’interface utilisateur, ce qui peut entraîner une baisse des performances.
- Changements de comportement en raison de changements dans la promotion d’événements tactiles/de stylet en événements de souris
- La manipulation peut se comporter différemment
- Le glisser-déplacer ne réagit pas correctement à l’entrée tactile
- Cela n’affecte pas l’entrée du stylet
- Le glisser-déplacer ne peut plus être lancé par des événements tactiles/du stylet
- Cela peut éventuellement bloquer l’application jusqu'à ce que l’entrée de la souris soit détectée.
- Au lieu de cela, les développeurs doivent lancer le glisser-déplacer à partir des événements de souris.

#### <a name="suggestion"></a>Suggestion

Les développeurs qui souhaitent activer cette pile peuvent ajouter/fusionner les éléments suivants dans le fichier App.config de l’application :

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Input.Stylus.EnablePointerSupport=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

La suppression de cette entrée ou l’affectation de la valeur false désactive cette pile facultative. Notez que cette pile est uniquement disponible sur Windows 10 Creators Update et ultérieur.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Edge        |
| Version | 4,7         |
| Type    | Reciblage |
