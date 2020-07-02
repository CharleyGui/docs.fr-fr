---
ms.openlocfilehash: 3709b9e694011666cebcb0ae09fbc838f65967af
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614563"
---
### <a name="wpf-grid-allocation-of-space-to-star-columns"></a>Allocation par Grid de l’espace aux colonnes * dans WPF

#### <a name="details"></a>Détails

À compter de .NET Framework 4.7, WPF remplace l’algorithme utilisé par <xref:System.Windows.Controls.Grid> pour allouer de l’espace aux colonnes \*, ce qui a pour effet de modifier la largeur réelle affectée aux colonnes \* dans différents cas :

- Quand une ou plusieurs \* colonnes ont également une largeur minimale ou maximale qui remplace l’allocation proportionnelle pour cette colonne. (La largeur minimale peut dériver d’une déclaration MinWidth explicite, ou d’un minimum implicite obtenu à partir du contenu de la colonne. La largeur maximale ne peut être définie qu’explicitement, à partir d’une déclaration MaxWidth.)
- Lorsqu’une ou plusieurs colonnes \* déclarent un très grand poids \*, supérieur à 10 ^ 298.
- Lorsque les poids \* sont suffisamment différents pour rencontrer une instabilité du calcul en virgule flottante (dépassement de capacité positif ou négatif, perte de précision).
- Lorsque l’arrondi de disposition est activé, et que la résolution d’affichage efficace en PPP est suffisamment élevée.
Dans les deux premiers cas, les largeurs produites par le nouvel algorithme peuvent être considérablement différentes de celles générées par l’ancien algorithme ; dans le dernier cas, la différence sera au plus de un ou deux pixels.<p/>Le nouvel algorithme résout plusieurs bogues présents dans l’ancien algorithme :

- L’allocation totale à des colonnes peut dépasser la largeur de la grille. Cela peut se produire lors de l’allocation d’espace pour une colonne dont la part proportionnelle est inférieure à sa taille minimale. L’algorithme alloue la taille minimale, ce qui réduit l’espace disponible pour les autres colonnes. S’il ne reste aucune colonne \* à allouer, l’allocation totale est trop grande.
- L’allocation totale peut être inférieure à la largeur de la grille. C’est le double problème pour #1, survenant lors de l’affectation à une colonne dont la part proportionnelle est supérieure à sa taille maximale, sans colonnes \* restantes pour combler.
- Deux colonnes \* peuvent recevoir des allocations non proportionnelles à leurs poids \*. Il s’agit d’une version atténuée de 1 et 2, qui survient lors de l’allocation aux colonnes \* A, B et C (dans cet ordre), si la part proportionnelle de B ne respecte pas la contrainte minimale (ou maximale). Comme ci-dessus, cela modifie l’espace disponible pour la colonne C, qui obtient une allocation proportionnelle inférieure (ou supérieure) à A,
- Les colonnes avec des poids extrêmement volumineux (&gt; 10^298) sont traitées comme si elles avaient un poids de 10^298. Les différences proportionnelles entre elles (et entre les colonnes avec des poids légèrement inférieurs) ne sont pas respectées.
- Les colonnes avec des poids infinis ne sont pas gérées correctement. [Il est en fait impossible de définir un poids infini, mais il s’agit d’une restriction artificielle. Le code d’allocation essayait de le gérer, sans succès.]
- Plusieurs problèmes mineurs en évitant le dépassement de capacité positif ou négatif, la perte de précision et autres problèmes liées aux nombres à virgule flottante.
- Les ajustements d’arrondi de disposition sont incorrects à un niveau de PPP suffisamment élevé.
Le nouvel algorithme produit des résultats qui répondent aux critères suivants :<p/>A. La largeur réelle affectée à une colonne * n’est jamais inférieure à sa largeur minimale ni supérieure à sa largeur maximale.<br/>B. Chaque <em>colonne qui n’est pas affectée de sa largeur minimale ou maximale est assignée à une largeur proportionnelle à son <em>poids. Pour être précis, si deux colonnes sont déclarées respectivement avec les valeurs Width x</em> et y</em> , et si aucune colonne ne reçoit sa largeur minimale ou maximale, les largeurs réelles v et w affectées aux colonnes sont dans la même proportion : v/w = = x/y.<br/>C. La largeur totale allouée aux &quot; colonnes proportionnelles &quot; \* est égale à l’espace disponible après l’allocation aux colonnes avec restriction (Fixed, auto et \* -Columns allouées à leur largeur minimale ou maximale). Cela peut être égal à zéro, par exemple si la somme des largeurs minimales dépasse la largeur disponible de la grille.<br/>D. Toutes ces instructions doivent être interprétées en considérant la disposition &quot;idéale&quot;. Lorsque l’arrondi de disposition est activé, la largeur réelle peut différer de la largeur idéale jusqu’à un pixel.<br/>L’ancien algorithme respectait (A), sans pouvoir en faire autant pour les autres critères dans les cas présentés ci-dessus.<p/>Tout ce que qui a été évoqué sur les colonnes et les largeurs dans cet article s’applique également aux lignes et leurs hauteurs.

#### <a name="suggestion"></a>Suggestion

Par défaut, les applications qui ciblent les versions du .NET Framework à partir de .NET Framework 4.7 voient le nouvel algorithme, tandis que les applications qui ciblent .NET Framework 4.6.2 ou antérieur voient l’ancien algorithme.<p/>Pour remplacer la valeur par défaut, utilisez les paramètres de configuration suivants :

<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Controls.Grid.StarDefinitionsCanExceedAvailableSpace=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>

La valeur `true` sélectionne l’ancien algorithme, et `false` le nouvel algorithme.

| Nom    | Valeur       |
|:--------|:------------|
| Étendue   | Secondaire       |
| Version | 4,7         |
| Type    | Reciblage |
